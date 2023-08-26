# This is the demonstration of the how we can use the PWN pin to read the analog signals.

----

## Here is the Sanpshot of the circuit connection of this: 
![image](https://github.com/SatishKumar75/ardunio-nodemcu/assets/106571472/20bb2649-ea61-4223-b151-96972874ca82)

## You can view the simulation for this by clicking on the given link
[Live Simulation](https://www.tinkercad.com/things/1X3ImeVh8eN "https://www.tinkercad.com/things/1X3ImeVh8eN")

## Here I am attaching the code for the same
```c++
void setup()
{
  pinMode(9, OUTPUT);
  pinMode(10, OUTPUT);
  pinMode(11, OUTPUT);
}

void loop()
{
  analogWrite(9, 255);
  delay(3000);
  analogWrite(10, 44);
  delay(3000);
  analogWrite(9,0);
  delay(3000);
  analogWrite(10,90);
  delay(3000);
   analogWrite(11, 220);
  delay(3000);
  analogWrite(10,0);
  delay(3000);
  analogWrite(11,0);
  delay(3000);
}
```

