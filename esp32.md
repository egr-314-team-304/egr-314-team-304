Python script for Thonny that communicates with the ESP32 and controls the IFX9201SGAUMA1 motor driver, based on sensor inputs and in coordination with a PIC32MX250F128B microcontroller

```python
import machine
import time

# UART configuration for receiving sensor data
uart = machine.UART(1, baudrate=9600, tx=17, rx=16)

# SPI configuration for motor driver communication
spi = machine.SPI(1, baudrate=10000000, polarity=0, phase=0)
cs = machine.Pin(15, machine.Pin.OUT)  # Chip select for SPI

def send_spi_data(data):
    """ Send data to the motor driver over SPI. """
    cs.value(0)  # Begin SPI communication
    spi.write(data)
    cs.value(1)  # End SPI communication

def rotate_motor_90_degrees(direction):
    """ Rotate the motor 90 degrees in the specified direction. """
    rotation_time = 0.5  # Adjust this based on your motor's speed
    if direction == "clockwise":
        send_spi_data(b'\x01')  # Command for clockwise rotation
    else:
        send_spi_data(b'\x02')  # Command for counter-clockwise rotation
    time.sleep(rotation_time)  # Wait for the motor to rotate 90 degrees
    send_spi_data(b'\x00')  # Stop the motor

def get_motor_direction(sensor_data):
    """ Determine motor direction from sensor data. """
    # Placeholder for sensor data processing logic
    # Replace with actual logic based on your sensor
    if sensor_data == "condition_for_clockwise":
        return "clockwise"
    else:
        return "counter-clockwise"

while True:
    if uart.any():
        data = uart.read().decode().strip()
        if data:
            print("Sensor data received:", data)
            motor_direction = get_motor_direction(data)
            rotate_motor_90_degrees(motor_direction)
    time.sleep(0.1)

//-------------------------------------
//print to Oled Screen

from machine import Pin, SoftI2C
import ssd1306
import gfx
from time import sleep

i2c = SoftI2C(scl=Pin(22), sda=Pin(21))

oled_width = 128
oled_height = 64
oled = ssd1306.SSD1306_I2C(oled_width, oled_height, i2c)
graphics = gfx.GFX(oled_width, oled_height, oled.pixel)

oled.text('Temp: 20.0F', 20, 20)  # 'Hello' at position (0,0)
# Display the message
oled.text('Temp: 40.0C', 20, 40)

oled.show()

//-------------------------------------
//MQTT connection

# Derived from: 
# * https://github.com/peterhinch/micropython-async/blob/master/v3/as_demos/auart.py
# * https://github.com/tve/mqboard/blob/master/mqtt_async/hello-world.py


from mqtt_async import MQTTClient, config
import uasyncio as asyncio
import time
from machine import UART
import my_oled
import logging
logging.basicConfig(level=logging.DEBUG)

MAXTX = 4

# Change the following configs to suit your environment
TOPIC_PUB = 'EGR314/Team304/KML'
TOPIC_SUB = 'EGR314/Instructor'
config.server = 'egr3x4.ddns.net' # can also be a hostname
config.ssid     = 'Particle'
config.wifi_pw  = 'greatstreet595'

uart = UART(2, 9600,tx=17,rx=16)
uart.init(9600, bits=8, parity=None, stop=1,flow=0) # init with given parameters

async def receiver():
    b = b''
    sreader = asyncio.StreamReader(uart)
    while True:
        res = await sreader.read(1)
        if res==b'\r':
            await client.publish(TOPIC_PUB, b, qos=1)
            print('published', b)
            b = b''
        else:
            b+=res

def callback(topic, msg, retained, qos):
    print('callback',topic, msg, retained, qos)
    my_oled.print_data(msg)
  #  my_oled.plot_data(msg)
    while (not not msg):
        
        uart.write(msg[:MAXTX])
        time.sleep(.01)
        msg = msg[MAXTX:]

    uart.write('\r\n')
    time.sleep(.01)
  
async def conn_callback(client): await client.subscribe(TOPIC_SUB, 1)

async def main(client):
    await client.connect()
    asyncio.create_task(receiver())
    while True:
        await asyncio.sleep(1)

config.subs_cb = callback
config.connect_coro = conn_callback

client = MQTTClient(config)
loop = asyncio.get_event_loop()
loop.run_until_complete(main(client))




```
This Python script is for interfacing an ESP32 microcontroller with the IFX9201SGAUMA1 motor driver, while receiving input from a PIC32MX250F128B microcontroller. In this setup, the ESP32 utilizes UART communication to receive sensor data from the PIC32MX250F128B. Once the data is received, the ESP32 processes it to determine the motor's rotation direction. The motor control is executed via SPI communication, which sends commands to the IFX9201SGAUMA1 motor driver. This script is designed to rotate the motor 90 degrees in either a clockwise or counter-clockwise direction, based on the sensor input. The rotation is time-controlled, offering a straightforward yet effective way to manage motor movement, especially in basic automation or robotic applications where precise angular control is needed.

[Home Page](index.md)
