# Demonstration of Servo Motor (How can we contorl the movement of the servo motor using push button)

-------

## This is the sanpshot of the circuit

---------
![image](https://github.com/SatishKumar75/ardunio-nodemcu/assets/106571472/92f42d16-ff7b-44b8-97c3-601c7e043f1e)

[Live Simulation](https://wokwi.com/projects/374300472186701825 "https://wokwi.com/projects/374300472186701825")

## Here is the code of the Servo Motor

```c++
#include<ESP32Servo.h>
Servo myservo;
int pos = 0;
void setup() {
  myservo.attach(21);
  pinMode(5, INPUT_PULLUP);
  pinMode(18, INPUT_PULLUP);
  Serial.begin(9600);
}

void loop() {
  if(digitalRead(5) == LOW)
  {
    pos++;
    Serial.println(pos);
    myservo.write(pos);
    delay(15);
    if(pos>=180){
      pos=180;
    }
  }
  if(digitalRead(18) == LOW){
    pos--;
    Serial.println(pos);
    myservo.write(pos);
    delay(15);
    if(pos<=0){
      pos=0;
    }
  }
}

```
### Note: - If you are getting the libaray "ESP32Servo.h" not found then you can manually add by clicking on "Library Manager and then click on + icon then search for the ESP32Servo"  
