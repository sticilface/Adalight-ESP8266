# Adalight-ESP8266
Adalight for the Arduino ESP


Needs to be compiled on the arduin-ESP IDE.
https://github.com/esp8266/Arduino.git


This sketch will take GRB pixels over serial sent by hyperion and push them out to WS2812 LEDs.  The reason I wrote this is that it is non-blocking, and can be run alonside the wifi, mqtt, HTTP server or anything else your ESP is doing.  Each pass through the loop takes anything in the serial FIFO buffer and adds it to the pixel buffer and moves on, next pass continues until the right number of LEDs has been reached, then the latch to show the pixels is triggered.  It falls back to header search after a timeout.  Using 200 LEDs, at a baud rate of 2,000,000 takes 9915uS to complete which works out at 101 Hrz.  So it is pretty quick on the ESP!

I've run this on a fairly complicated ESP sketch, with all the other features running at the same time. 

Must define PIN, number of LEDs, baud rate.  
Tested to work at a baud rate of 2,000,000. 

