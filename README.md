# LED Blink Using Timer0 in PIC Microcontroller

###### Implemented an LED blinking system using Timer0 in the PIC16F877A microcontroller with Proteus simulation. The project demonstrates timer-based delay generation for periodic LED control without relying on software delays, showcasing efficient use of hardware timers in embedded systems.
---
## Here is the references...

Circuit Connections :-

<img src=https://github.com/lingeshkumarkamaraj/LED-Blink-Using-Timer0/blob/main/1.png> 
<img src=https://github.com/lingeshkumarkamaraj/LED-Blink-Using-Timer0/blob/main/3.png> 
<img src=https://github.com/lingeshkumarkamaraj/LED-Blink-Using-Timer0/blob/main/2.png> 

Working :- 

[<img width="300" height="300" src="https://img.icons8.com/color/96/start.png" alt="video"/>](https://youtu.be/BsKQYUnHONE)


---
Code :-

Main file:

```
// main.c file


#include <xc.h>
#include "xc8_header.h"
#define XTAL_FREQ 20000000

#include <stdbool.h>
#define LEDT TRISBbits.TRISB1
#define LEDP PORTBbits.RB1

volatile unsigned int overflowcount = 0;
volatile bool timeflag = 0;

void __interrupt()ISR(void){
    
    if(INTCONbits.T0IF == 1){
        TMR0 = 0;
        INTCONbits.T0IF = 0;
        overflowcount++;
        
        if(overflowcount >= 782){
            overflowcount = 0;
            timeflag = 1;
        }

    }
}

void Timer0_Init(){
    
    OPTION_REG = 0b00000100;
    TMR0 = 0;
    INTCONbits.T0IF = 0;
    INTCONbits.GIE = 1;
    INTCONbits.T0IE = 1;
    
}

void main(void) {
    
    LEDT = 0;
    Timer0_Init();
    while(1){
        if(timeflag == 1){
            LEDP ^= 1;
            timeflag = 0;
        }
    }
}



```

Header file:

```
//xc8_header.h file

#ifndef XC_HEADER_H
#define	XC_HEADER_H

#include <xc.h> // include processor files - each processor file is guarded.  

// CONFIG
#pragma config FOSC = EXTRC     // Oscillator Selection bits (RC oscillator)
#pragma config WDTE = OFF       // Watchdog Timer Enable bit (WDT disabled)
#pragma config PWRTE = OFF      // Power-up Timer Enable bit (PWRT disabled)
#pragma config BOREN = OFF      // Brown-out Reset Enable bit (BOR disabled)
#pragma config LVP = OFF        // Low-Voltage (Single-Supply) In-Circuit Serial Programming Enable bit (RB3 is digital I/O, HV on MCLR must be used for programming)
#pragma config CPD = OFF        // Data EEPROM Memory Code Protection bit (Data EEPROM code protection off)
#pragma config WRT = OFF        // Flash Program Memory Write Enable bits (Write protection off; all program memory may be written to by EECON control)
#pragma config CP = OFF         // Flash Program Memory Code Protection bit (Code protection off)


#endif	


```
---
[PROTEUS FILE LINK](https://github.com/lingeshkumarkamaraj/LED-Blink-Using-Timer0/blob/main/PIC%20timer0.pdsprj)
---
