### DS18B20-Temperature-Sensor-with-Arduino
##Introducing DS18B20 Temperature Sensor

The DS18B20 temperature sensor is a one-wire digital temperature sensor. This means that it just requires one data line (and GND) to communicate with the Arduino.

It can be powered by an external power supply or it can derive power from the data line (called “parasite mode”), which eliminates the need for an external power supply

###Upload Code – Single DS18B20

To interface with the DS18B20 temperature sensor, you need to install the One Wire library by Paul Stoffregen and the Dallas Temperature library. Follow the next steps to install those libraries.

Installing Libraries
1. Open your Arduino IDE and go to Sketch > Include Library > Manage Libraries. The Library Manager should open.

2. Type “OneWire” in the search box and install the OneWire library by Paul Stoffregen.
