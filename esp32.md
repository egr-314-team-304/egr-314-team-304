for esp32 code
//
import machine
import time

# UART
uart = machine.UART(1, baudrate=9600, tx=17, rx=16)

# Motor control pins
motor_pin = machine.Pin(5, machine.Pin.OUT)

def rotate_motor(direction):
    if direction == "clockwise":
        # Logic to rotate motor clockwise
        motor_pin.value(1)
    else:
        # Logic to rotate motor counter-clockwise
        motor_pin.value(0)
    time.sleep(1)  # Adjust delay as needed for 90-degree rotation
    motor_pin.value(0)  # Stop the motor

while True:
    if uart.any():
        data = uart.read().decode().strip()
        if data:
            print("Received data:", data)
            # Assuming data is either 'clockwise' or 'counter-clockwise'
            rotate_motor(data)
    time.sleep(0.1)
    
[Home Page](index.md)
