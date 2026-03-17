Fork of https://github.com/cpetrich/counterfeit_DS18B20 for my personal purposes.

I wanted to study my AliExpress "DS18B20"s, but the .ino sketch is for Arduino and I only had ESP8266 hardware at hand. Miraculously, 
https://github.com/esp8266/Arduino supports ESP8266 on Arduino environment!

Just a couple of adjustments were needed:
* Disabling WiFi. OneWire uses bit-banging, and ESP's non-maskable WiFi interrupts ruin the timing.[^1]
* Changing default pin assignments to be appropriate for typical ESP8266 boards.

Usage:
1. Install https://github.com/esp8266/Arduino?tab=readme-ov-file#installing-with-boards-manager
2. Install OneWire https://www.pjrc.com/teensy/td_libs_OneWire.html
3. Check the pins. By default, D4 a.k.a. GPIO 2 for LED (as it is on WEMOS D1 mini at least), and D2 a.k.a. GPIO 4 a.k.a. SDA for OneWire.
4. Compile and Upload the sketch, and use Serial Monitor for operating it.

Example output in [./results_for_aliexpress_probe.txt](results_for_aliexpress_probe.txt). My DS18B20s turned out to be "Family A3 (Clone)", which is "okay" among fakes.
The important point is to avoid "Family D" or "Family F" garbage.

[^1]: OneWire on ESP is good enough for normal "just read the temperature" use with DS18B20s,
  but a DS2482-100 hardware I2C to 1-Wire bridge would be a good idea for critical applications.
