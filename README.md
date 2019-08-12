# Esp8266_stand_alone
This code is among the first steps in making your system transmit data online using ESP8266-01 module. 
This module is simple to use but can be a bit of stress if not well informed.
The first step is to flash the module with a new firmware 
I will not cover that here as there a plenty of tutorials
Here is the code you input after the version control to use serial communication to send data btn arduino and ESP module.

PINOUTS
         Esp8266-Arduino
          VCC-3.3V
          TX-TX
          RX-RX
          CH_PD-3.3V
          RST-RESET Button
          GPIO0-FLASH Button

Steps
1. Connect FLASH Button (This is connecting GPIO0 to the button then to the ground)
2. Connect RESET Button (This is connecting the RST pin to button then to the ground)
3.Press and hold FLASH button
4. While holding FLASH button, Press and Release RESET button
5. Release FLash Button

Change the Arduino Board Setting to Generic ESP8266
Select the right port 
upload the code below



