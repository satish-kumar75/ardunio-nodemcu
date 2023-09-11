# Demonstration of Servo Motor (How can we contorl the movement of the servo motor)

-------

## This is the sanpshot of the circuit

---------

![image](https://github.com/SatishKumar75/ardunio-nodemcu/assets/106571472/bc51c32f-dcb3-450d-bec1-e727ddf9ed99)

--------

[Live Simulation](https://wokwi.com/projects/375550305086751745 "https://wokwi.com/projects/375550305086751745")

## Here is the code of the Servo Motor

```c++
#include <ESP32Servo.h>

Servo myservo;  // Create a servo object

void setup() {
  myservo.attach(21);  // Attach the servo to digital pin 9
}

void loop() {
  // Sweep the servo from 0 to 180 degrees
  for (int pos = 0; pos <= 180; pos += 1) {
    myservo.write(pos);
    delay(15);  // Adjust the delay for servo speed
  }

  // Delay at 180 degrees
  delay(1000);

  // Sweep the servo back from 180 to 0 degrees
  for (int pos = 180; pos >= 0; pos -= 1) {
    myservo.write(pos);
    delay(15);  // Adjust the delay for servo speed
  }

  // Delay at 0 degrees
  delay(1000);
}

```
