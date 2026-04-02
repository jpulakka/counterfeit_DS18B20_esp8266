Fork of https://github.com/cpetrich/counterfeit_DS18B20 for my personal purposes.

I wanted to study some DS18B20 temperature sensors from AliExpress[^1], but the .ino sketch is for Arduino, and I only had an ESP8266 at hand. Miraculously, 
https://github.com/esp8266/Arduino supports ESP8266 on the Arduino environment!

Just a couple of adjustments were needed:
* Disabling WiFi. OneWire uses bit-banging, and ESP's non-maskable WiFi interrupts ruin the timing.[^2]
* Changing default pin assignments to be appropriate for typical ESP8266 boards.

Usage:
1. Install Arduino IDE.
2. Install https://github.com/esp8266/Arduino?tab=readme-ov-file#installing-with-boards-manager
3. Install OneWire https://www.pjrc.com/teensy/td_libs_OneWire.html
4. Select the right board in the IDE and check the pins in the sketch. By default, D4 a.k.a. GPIO 2 for LED (as it is on WEMOS D1 mini at least), and D2 a.k.a. GPIO 4 a.k.a. SDA for OneWire.
5. Compile and Upload the sketch, and use the Serial Monitor to operate it.

[^1]: Example output in [results_for_aliexpress_probe.txt](./results_for_aliexpress_probe.txt). My DS18B20s turned out to be "Family A3 (Clone)", which is "okay" among fakes.
The important point is to avoid "Family D" or "Family F" garbage.
[^2]: OneWire on ESP is good enough for normal "just read the temperature" use with DS18B20s, even when using WiFi,
  but a DS2484 hardware I2C to 1-Wire bridge would be a good idea for critical applications.
