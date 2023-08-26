# This is the demonstration of how we can make a counter program using 7 Segment Display.

------

## This is the snapshot of the circuit: -
![image](https://github.com/SatishKumar75/ardunio-nodemcu/assets/106571472/7b402a92-194d-46b2-8843-1b406998cfef)

-----

## By clicking on the given link you can view the simulation of TinkerCad
[Live Simulation](https://www.tinkercad.com/things/1InDPX7o1Xu "https://www.tinkercad.com/things/1InDPX7o1Xu")

## Here is the code for the same: 
```c++

void setup()
{
pinMode(0,OUTPUT);//dp
pinMode(1,OUTPUT); //a
pinMode(2,OUTPUT);//b
pinMode(3,OUTPUT);//c
pinMode(4,OUTPUT);//d
pinMode(5,OUTPUT);//e
pinMode(6,OUTPUT);//f
pinMode(7,OUTPUT);//g

}

void loop()
{

num(1,1,1,1,1,1,1,0);//0
delay(1000);
num(1,0,1,1,0,0,0,0);//1
delay(1000);
num(1,1,1,0,1,1,0,1);//2
delay(1000);
num(1,1,1,1,1,0,0,1);//3
delay(1000);
num(1,0,1,1,0,0,1,1);//4
delay(1000);
num(1,1,0,1,1,0,1,1);//5
delay(1000);
num(1,1,0,1,1,1,1,1);//6
delay(1000);
num(1,1,1,1,0,0,0,0);//7
delay(1000);
num(1,1,1,1,1,1,1,1);//8
delay(1000);
num(1,1,1,1,1,0,1,1);//9
delay(1000);
num(1,1,1,1,1,1,1,1);//8
delay(1000);
num(1,1,1,1,0,0,0,0);//7
delay(1000);
num(1,1,0,1,1,1,1,1);//6
delay(1000);
num(1,1,0,1,1,0,1,1);//5
delay(1000);
num(1,0,1,1,0,0,1,1);//4
delay(1000);
num(1,1,1,1,1,0,0,1);//3
delay(1000);
num(1,1,1,0,1,1,0,1);//2
delay(1000);
num(1,0,1,1,0,0,0,0);//1
delay(1000);
num(1,1,1,1,1,1,1,0);//0
delay(1000);

}

void num(int dp, int a, int b, int c, int d, int e, int f, int g) {
digitalWrite(0,dp);
digitalWrite(1,a);
digitalWrite(2,b);
digitalWrite(3,c);
digitalWrite(4,d);
digitalWrite(5,e);
digitalWrite(6,f);
digitalWrite(7,g);
}
```
