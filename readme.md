# Digital Voltmeter Project

## Overview
This project demonstrates how to create a digital voltmeter using an Arduino, an LCD display, and various electronic components. The voltmeter reads an input voltage and displays it on the LCD screen.

## Components Used
1. Arduino Board
2. LED
3. Resistors
4. Potentiometer
5. LCD Display
6. Breadboard
7. Jumper Wires

## Arduino Code
The `voltmeter.ino` file contains the Arduino code for the digital voltmeter. It includes the necessary setup for the LCD, reading analog input, and displaying the voltage.

```cpp
#include "LiquidCrystal.h"

LiquidCrystal lcd(8, 9, 4, 5, 6, 7);

float input_voltage = 0.0;
float temp=0.0;
float r1=90900.0;
float r2=10000.0;

void setup()
{
   Serial.begin(9600);     // opens serial port, sets data rate to 9600 bps
   lcd.begin(16, 2);       // set up the LCD's number of columns and rows
   lcd.print("DIGITAL VOLTMETER");
}

void loop()
{
   // Conversion formula
   int analog_value = analogRead(A0);
   temp = (analog_value * 5.0) / 1024.0; 
   input_voltage = temp / (r2/(r1+r2));
   
   if (input_voltage < 0.1) 
   {
     input_voltage=0.0;
   } 

   Serial.print("v= ");
   Serial.println(input_voltage);
   lcd.setCursor(0, 1);
   lcd.print("Voltage= ");
   lcd.print(input_voltage);
   delay(300);
}
```
## Project Simulation
The project can be simulated using Tinkercad. Visit [Tinkercad](https://www.tinkercad.com/) and use the simulator to visualize and test the digital voltmeter.

## Setup Instructions
1. Connect the components as per the circuit diagram.
2. Upload the `voltmeter.ino` code to the Arduino board.
3. Power up the circuit and observe the voltage readings on the LCD display.
```