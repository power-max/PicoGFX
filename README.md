# PicoGFX

This is my port of the Adafruit SSD1306 graphics library to the Pi Pico C SDK.
The port required also porting the Adafruit_GFX library. The port is not perfect, since the Arduino Serial library was not ported as it has a large number of dependences which result in half of the Arduino API needing to be ported (and at that point you might as well use Arduino framework)

## Known limitations:
* only basic string support and print function
* only I2C working at the moment (I don't have an SPI screen to test)
* only SSD1306


