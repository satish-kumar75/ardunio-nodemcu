# Home automation uisng Ultara Sonic Sensor and Temperature Sensor
_____

## Simulation

https://github.com/SatishKumar75/ardunio-nodemcu/assets/106571472/3714335b-97b0-44d1-bbe1-ee13e3d1a4f2

------

[Live Simulation](https://www.tinkercad.com/things/8fcdSN8fdRb "https://www.tinkercad.com/things/8fcdSN8fdRb")

-----

# Code
```c++
#include <Servo.h>
#include <LiquidCrystal.h>
const int trgpin = 11;
const int echopin = 2;
const int temp = A1;
float celsius;

LiquidCrystal lcd (8, 7, 6, 5, 4, 3);

int pos = 0;

Servo servo_9;
Servo servo_10;

#define SOUND_SPEED 0.034
long duration;
float distance;

void setup()
{
  pinMode(temp,INPUT);
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
  	celsius = analogRead(temp)*0.004882814;
  	celsius = (celsius - 0.5) * 100.0;
  
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
  	lcd.setCursor(14,1);
    lcd.print(celsius);
	lcd.print(" C");
  
  if(distance <= 40){
    servo_9.write(0);
    servo_10.write(0);
    lcd.setCursor(0,1);
    lcd.print("Door is Open ");
    digitalWrite(13,HIGH);
  }else{
    servo_9.write(90);
    servo_10.write(90);
    lcd.setCursor(0,1);
    lcd.print("Door is Close");
     digitalWrite(13,LOW);
  }
  if(celsius >= 20){
     digitalWrite(12,HIGH);
    
  }else{
    digitalWrite(12,LOW);
   
  }
}
```
------

## Circuit

![image](https://github.com/SatishKumar75/ardunio-nodemcu/assets/106571472/73093533-470d-4aea-8d21-5202387ed5c5)
