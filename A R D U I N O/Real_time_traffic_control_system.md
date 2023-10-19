# Real time traffic control system with UltraSonic sensor
_____

## Circuit Snapshot
![Animation](https://github.com/SatishKumar75/ardunio-nodemcu/assets/106571472/4236d295-21a1-4d5c-8153-a529a10cca9a)

------

[Live Simulation](https://www.tinkercad.com/things/bxjKkaKTisk "https://www.tinkercad.com/things/bxjKkaKTisk")

-----

## Code
```c++
const int sensor1_trig = 2;
const int sensor1_echo = 3;
const int sensor2_trig = 4;
const int sensor2_echo = 5;
const int sensor3_trig = 6;
const int sensor3_echo = 7;
const int sensor4_trig = 8;
const int sensor4_echo = 9;

const int led1 = 10;
const int redled1 = A0;
const int led2 = 11;
const int redled2 = A1;
const int led3 = 12;
const int redled3 = A2;
const int led4 = 13;
const int redled4 = A3;

int distances[4] = {0};                                // Store distances from all sensors
int ledPins[4] = {redled1, redled2, redled3, redled4}; // Red LEDs
int greenPins[4] = {led1, led2, led3, led4};           // Green LEDs

void calculateDistance(int sensor_trig, int sensor_echo, int sensorIndex)
{
    digitalWrite(sensor_trig, LOW);
    delayMicroseconds(2);
    digitalWrite(sensor_trig, HIGH);
    delayMicroseconds(10);
    digitalWrite(sensor_trig, LOW);
    long duration = pulseIn(sensor_echo, HIGH);
    int distance = duration * 0.034 / 2;
    distances[sensorIndex] = distance;
}

void setup()
{
    pinMode(sensor1_trig, OUTPUT);
    pinMode(sensor1_echo, INPUT);
    pinMode(sensor2_trig, OUTPUT);
    pinMode(sensor2_echo, INPUT);
    pinMode(sensor3_trig, OUTPUT);
    pinMode(sensor3_echo, INPUT);
    pinMode(sensor4_trig, OUTPUT);
    pinMode(sensor4_echo, INPUT);

    pinMode(led1, OUTPUT);
    pinMode(redled1, OUTPUT);
    pinMode(led2, OUTPUT);
    pinMode(redled2, OUTPUT);
    pinMode(led3, OUTPUT);
    pinMode(redled3, OUTPUT);
    pinMode(led4, OUTPUT);
    pinMode(redled4, OUTPUT);

    Serial.begin(9600);
}

void loop()
{
    // Measure distances for all sensors
    calculateDistance(sensor1_trig, sensor1_echo, 0);
    calculateDistance(sensor2_trig, sensor2_echo, 1);
    calculateDistance(sensor3_trig, sensor3_echo, 2);
    calculateDistance(sensor4_trig, sensor4_echo, 3);

    // Print distances to Serial Monitor
    for (int i = 0; i < 4; i++)
    {
        Serial.print("Distance from Sensor ");
        Serial.print(i + 1);
        Serial.print(": ");
        Serial.print(distances[i]);
        Serial.println(" cm");
    }
  Serial.println();

    // Find the sensor with the shortest distance
    int closestSensor = 0;
    int shortestDistance = distances[0];
    for (int i = 1; i < 4; i++)
    {
        if (distances[i] < shortestDistance)
        {
            closestSensor = i;
            shortestDistance = distances[i];
        }
    }

    // Control the LEDs based on the closest sensor
    for (int i = 0; i < 4; i++)
    {
        if (i == closestSensor)
        {
            digitalWrite(greenPins[i], HIGH);
            digitalWrite(ledPins[i], LOW);
        }
        else
        {
            digitalWrite(greenPins[i], LOW);
            digitalWrite(ledPins[i], HIGH);
        }
    }

    delay(1000);
}
```
