/*******************************************************************************
  Main Source File

  Company:
    Microchip Technology Inc.

  File Name:
    main.c

  Summary:
    This file contains the "main" function for a project.

  Description:
    This file contains the "main" function for a project.  The
    "main" function calls the "SYS_Initialize" function to initialize the state
    machines of all modules in the system
 *******************************************************************************/

// *****************************************************************************
// *****************************************************************************
// Section: Included Files
// *****************************************************************************
// *****************************************************************************

#include <xc.h>
#include <plib_i2c1_master.h>
#include <plib_i2c2_master.h>
#include <plib_spi2_master.h>
#include <plib_uart1.h>

// Constants for sensor addresses
#define OPT3001_I2C_ADDRESS 0x44
#define TMP100_I2C_ADDRESS  0x48
#define SHT41_I2C_ADDRESS   0x44

// Motor control pins
#define MOTOR_PWM_PIN       21
#define MOTOR_DIRECTION_PIN 24
#define MOTOR_DISTANCE_PIN  18

// ESP32 UART communication pins
#define ESP32_UART_TX_PIN   2
#define ESP32_UART_RX_PIN   3

//ESP32 OLED pins
#define OLED_SDA_PIN        3
#define OLED_SCL_PIN        4

void main(void) {
    // Initialize I/O
    TRISBbits.TRISB10 = 0;  // Set RB10 as output for PWM
    TRISBbits.TRISB13 = 0;  // Set RB13 as output for DIR
    TRISBbits.TRISB9 = 0;  // Set RB9 as output for DIS

    // Initialize PWM on CCP1 (RC2)
    CCP1CON = 0x8C;  // PWM mode
    CCPR1 = 0x00;    // Start with 0 duty cycle
    T2CON = 0x04;    // Timer2 ON, Prescaler 1:1
    PR2 = 0xFF;      // PWM period

    // Enable the motor (Assuming active LOW disable)
    MOTOR_DISTANCE_PIN = 0;     // Enable the motor

    // Main loop
    while (1) {
        // Increase speed from 0 to maximum
        for (int speed = 0; speed < 256; speed++) {
            CCPR1 = speed;  // Set speed
            MOTOR_DIRECTION_PIN = 0;    // Set direction forward
            __delay_ms(10); // Adjust delay as needed
        }

        // Decrease speed to 0
        for (int speed = 255; speed >= 0; speed--) {
            CCPR1 = speed;  // Set speed
            MOTOR_DIRECTION_PIN = 1;    // Set direction reverse
            __delay_ms(10); // Adjust delay as needed
        }
    }
}

//Function prototypes
void initI2C(void);
uint16_t readOPT4001(void);
float readTMP100(void);
// Add SHT41 functions as needed

void initMotorControl(void);
void moveMotorToPosition(int position);

void initUART(void);
void sendToESP32(float temperature, uint16_t lightIntensity);
void printToOLED(float temperature, uint16_t lightIntensity);

int main(void) {
    // Configure I/O pins
    TRISBCLR = (1 << 6); // Clear RB2 (SDA) as output
    TRISBSET = (1 << 9); // Set RA2 (SCL) as input
    // Configure other I/O pins as needed

    // Initialize peripherals
    initI2C();
    initMotorControl();
    initUART();

float readTemperatureFromTMP100(void) {
    uint8_t readBuffer[2];
    float temperature;
    I2C_ERROR status;

    // Start the I2C read transaction
    I2C2_Read(0x48, readBuffer, 2, &status);

    // Check if the read operation was successful
    if (status != I2C_ERROR_NONE) {
        // Handle error (e.g., sensor not responding)
        return -1; // Indicate an error
    }

    // Convert the read data to temperature
    int16_t rawTemp = (readBuffer[0] << 8) | readBuffer[1];
    temperature = convertRawToTemperature(rawTemp);

    return temperature;
}
float convertRawToTemperature(int16_t rawTemp) {
    // Each LSB might represent 0.0625 degrees Celsius
    return rawTemp * 0.0625;
}

int main(void) {
    SYS_Initialize(NULL);

    while (true) {
        float temperature = readTemperatureFromTMP100();
        if (temperature >= 0) {
            // Valid temperature read, process or display it
        } else {
            // Handle read error
        }
    }

    return 0;
}    
    while (1) {
        // Read data from sensors
        uint16_t lightIntensity = readOPT4001();
        float temperature = readTMP100();

        // Check light intensity and control motor accordingly
        if (lightIntensity > / 3000 ) {
            moveMotorToPosition(180);
        } else {
            moveMotorToPosition(0);
        }

        // Send data to ESP32 over UART
        sendToESP32(temperature, lightIntensity);

        // Print data to OLED on ESP32
        printToOLED(temperature, lightIntensity);

        // Add delay or other logic as needed
    }

    return 0;
}

// Implement the functions as per previous responses
/*******************************************************************************
 End of File
*/

---

[Home Page](index.md)
