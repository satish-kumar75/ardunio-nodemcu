# Demonstration of Humidity Sensor

-------

## This is the sanpshot of the circuit

---------
![image](https://github.com/SatishKumar75/ardunio-nodemcu/assets/106571472/86dfbdcc-eff5-4ff9-ad19-16eb324a48e5)

------

[Live Simulation](https://wokwi.com/projects/375558556367699969 "https://wokwi.com/projects/375558556367699969")

------

# Code: 
```c++
#include "DHT.h"
#define DHTTYPE DHT11
#define dht_dpin 2
DHT dht(dht_dpin, DHTTYPE);

void setup(void) {
  // put your setup code here, to run once:
  dht.begin();
  Serial.begin(9600);
  Serial.println("Humidity and Temprature\n\n");
  delay(700);
}

void loop() {
  // put your main code here, to run repeatedly:
  float h =dht.readHumidity();
  float t =dht.readTemperature();
  Serial.print("Current humidity= ");
  Serial.print(h);
  Serial.println("%  ");
  Serial.print("Temprature =");
  Serial.print(t);
  Serial.println("C  ");
  delay(800); // this speeds up the simulation
}

```

# Note: Include the "DHT22" Library in Library Manager
