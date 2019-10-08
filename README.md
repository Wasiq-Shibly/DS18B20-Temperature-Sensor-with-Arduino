### DS18B20-Temperature-Sensor-with-Arduino
##Introducing DS18B20 Temperature Sensor

The DS18B20 temperature sensor is a one-wire digital temperature sensor. This means that it just requires one data line (and GND) to communicate with the Arduino.

It can be powered by an external power supply or it can derive power from the data line (called “parasite mode”), which eliminates the need for an external power supply

###Circuit Diagram
![circuit](https://user-images.githubusercontent.com/55593937/66380140-9dbb0d00-e9d8-11e9-8824-a93945119518.PNG)

###Upload Code – Single DS18B20

To interface with the DS18B20 temperature sensor, you need to install the One Wire library by Paul Stoffregen and the Dallas Temperature library. Follow the next steps to install those libraries.

Installing Libraries
1. Open your Arduino IDE and go to Sketch > Include Library > Manage Libraries. The Library Manager should open.

2. Type “OneWire” in the search box and install the OneWire library by Paul Stoffregen.
![l2](https://user-images.githubusercontent.com/55593937/66379972-4f0d7300-e9d8-11e9-9724-8a751da95362.PNG)
![l2](https://user-images.githubusercontent.com/55593937/66379978-52086380-e9d8-11e9-9a7c-51f66c26976e.PNG)

code:

#include <OneWire.h>
#include <DallasTemperature.h>

// Data wire is conntec to the Arduino digital pin 4
#define ONE_WIRE_BUS 4

// Setup a oneWire instance to communicate with any OneWire devices
OneWire oneWire(ONE_WIRE_BUS);

// Pass our oneWire reference to Dallas Temperature sensor 
DallasTemperature sensors(&oneWire);

void setup(void)
{
  // Start serial communication for debugging purposes
  Serial.begin(9600);
  // Start up the library
  sensors.begin();
}

void loop(void){ 
  // Call sensors.requestTemperatures() to issue a global temperature and Requests to all devices on the bus
  sensors.requestTemperatures(); 
  
  Serial.print("Celsius temperature: ");
  // Why "byIndex"? You can have more than one IC on the same bus. 0 refers to the first IC on the wire
  Serial.print(sensors.getTempCByIndex(0)); 
  Serial.print(" - Fahrenheit temperature: ");
  Serial.println(sensors.getTempFByIndex(0));
  delay(1000);
}



