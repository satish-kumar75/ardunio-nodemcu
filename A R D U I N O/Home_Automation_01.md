# Home Automation Using servo motor and Ultra Sonic Sensor
_____

## Circuit Snapshot
![CPT2310090820-858x461 (1)](https://github.com/SatishKumar75/ardunio-nodemcu/assets/106571472/ac8a875c-72ea-49d3-9e4e-9f06ece63a36)

------

[Live Simulation](https://www.tinkercad.com/things/dNrWDXxohIY "https://www.tinkercad.com/things/dNrWDXxohIY")

-----

## Code
```c++
#include <Servo.h>
#include <LiquidCrystal.h>
const int trgpin = 11;
const int echopin = 2;

LiquidCrystal lcd (8, 7, 6, 5, 4, 3);

int pos = 0;

Servo servo_9;
Servo servo_10;

#define SOUND_SPEED 0.034
long duration;
float distance;

void setup()
{
  servo_9.attach(9, 500, 2500);
  servo_10.attach(10, 500, 2500);
  pinMode(13,OUTPUT);
  pinMode(12, OUTPUT);
  pinMode(trgpin, OUTPUT);
  pinMode(echopin, INPUT);
  lcd.begin(16, 2);
  
   servo_9.write(0);
  servo_10.write(0);
  
	
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
    lcd.setCursor(10, 0);
    lcd.print(distance);
  
  if(distance <= 40){
    servo_9.write(0);
    servo_10.write(0);
    lcd.setCursor(0,1);
    lcd.print("Door is Open ");
    digitalWrite(12,HIGH);
    digitalWrite(13,HIGH);
  }else{
    servo_9.write(90);
    servo_10.write(90);
    lcd.setCursor(0,1);
    lcd.print("Door is Close");
    digitalWrite(12,LOW);
    digitalWrite(13,LOW);
  }
}
```
------

## Circuit
![image](https://github.com/SatishKumar75/ardunio-nodemcu/assets/106571472/b90b86db-16c0-40cd-af26-1d10c6a93675)
