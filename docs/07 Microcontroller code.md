**Overview**


The microcontroller code establishes both the input pins for door sensor detection and the output pins which operate the H bridge driver. The program uses the configured pins to monitor sensor states which determine motor operation. The program sends appropriate logic signals to the H bridge for motor rotation when the door status changes. The program includes a brief delay to enhance reading stability while maintaining continuous operation for immediate microcontroller responses. The system operates as a basic control mechanism which monitors sensor data to activate motor movement through real-time input detection.







#include "mcc_generated_files/system/system.h"

/*
    Main application
*/

// Simple DC motor demo for PIC18F57Q43 and DRV8871
// IN1 on RF6
// IN2 on RF5

#include <xc.h>

#define _XTAL_FREQ 64000000U

void init_pins(void)
{
    // make RF5 and RF6 digital
    ANSELFbits.ANSELF5 = 0;
    ANSELFbits.ANSELF6 = 0;

    // set RF5 and RF6 as outputs
    TRISFbits.TRISF5 = 0;
    TRISFbits.TRISF6 = 0;

    // motor off at start
    LATFbits.LATF5 = 0;
    LATFbits.LATF6 = 0;
}

void forward(void)
{
    // IN1 high, IN2 low
    LATFbits.LATF6 = 1;
    LATFbits.LATF5 = 0;
}

void reverse(void)
{
    // IN1 low, IN2 high
    LATFbits.LATF6 = 0;
    LATFbits.LATF5 = 1;
}

void brake(void)
{
    // both low
    LATFbits.LATF6 = 0;
    LATFbits.LATF5 = 0;
}

void main(void)
{
    init_pins();

    while(1)
    {
        forward();         // run forward
        __delay_ms(3000);  // three seconds

        brake();           // stop
        __delay_ms(1000);  // one second

        reverse();         // run reverse
        __delay_ms(3000);

        brake();           // stop
        __delay_ms(1000);
    }
}

Here is the zip file with the code can be downloaded[here](https://github.com/user-attachments/files/24045241/PCB.zip)
