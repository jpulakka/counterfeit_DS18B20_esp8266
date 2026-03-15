Fork of https://github.com/cpetrich/counterfeit_DS18B20 for my personal purposes.

I wanted to study my AliExpress "DS18B20"s, but I only had ESP8266 hardware at hand.

A couple of things needed to be done:
* Disabling WiFi, because OneWire uses bit-banging, and ESP's WiFi interrupts ruin the timing.
* Changing default pin assignments to be appropriate for typical ESP8266 boards.

Usage:
1. Install https://github.com/esp8266/Arduino?tab=readme-ov-file#installing-with-boards-manager
2. Install OneWire https://www.pjrc.com/teensy/td_libs_OneWire.html
3. Check the pins. By default, D4 a.k.a. pin 2 for LED (as it is on WEMOS D1 mini at least), and D2 a.k.a. pin 4 a.k.a. SDA for OneWire.
4. Compile and Upload the sketch, and use Serial Monitor for operating it.
