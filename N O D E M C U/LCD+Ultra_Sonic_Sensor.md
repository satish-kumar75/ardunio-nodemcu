# Calculating the distance with Ultra Sonic Sensor and displaying it on LCD using NODE-MCU ESP32

-------

## Snapshot

-----
![CPT2309120937-768x423](https://github.com/SatishKumar75/ardunio-nodemcu/assets/106571472/5d36907f-2cc6-4cc6-8260-ded0ef785f8d)

-----

[Live Simulation](https://wokwi.com/projects/374665572014111745 "https://wokwi.com/projects/374665572014111745")

------

## Sample Code
```c++
#include <LiquidCrystal.h>
LiquidCrystal lcd(22, 21, 13, 12, 14, 27);
const int trgpin = 5;
const int echopin = 18;

#define SOUND_SPEED 0.034
long duration;
float distance;
void setup()
{
    lcd.begin(16, 2);
    pinMode(trgpin, OUTPUT);
    pinMode(echopin, INPUT);
}

void loop()
{
    digitalWrite(trgpin, LOW);
    delayMicroseconds(2);
    digitalWrite(trgpin, HIGH);
    delayMicroseconds(10);
    digitalWrite(trgpin, LOW);

    duration = pulseIn(echopin, HIGH);

    distance = duration * SOUND_SPEED / 2;

    lcd.setCursor(0, 0);
    lcd.print("Distance: ");
    lcd.setCursor(1, 1);
    lcd.print(distance);
}

```
