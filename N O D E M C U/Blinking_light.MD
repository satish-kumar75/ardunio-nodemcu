# this is blinking light program in nodemcu

---

## first we have to go to simulator and connect all the component

---

```c++


void setup() {
  // put your setup code here, to run once:
  // Serial.begin(115200);
  // Serial.println("Hello, ESP32!");
  pinMode(5, OUTPUT);
  pinMode(4, OUTPUT);
  pinMode(2 , OUTPUT);
  Serial.begin(9600);

}

void loop() {
  // put your main code here, to run repeatedly:
  // this speeds up the simulation
  digitalWrite(5,HIGH);
  delay(50);
   digitalWrite(5,LOW);
   delay(50);
    Serial.println("stop");
   digitalWrite(4,HIGH);
  delay(50);
   digitalWrite(4,LOW);
   delay(50);
    Serial.println("stop");
   digitalWrite(2,HIGH);
  delay(50);
   digitalWrite(2,LOW);
   delay(50);
    Serial.println("stop");
}

```

[live simulation -https://wokwi.com/projects/372034180029504513](https://wokwi.com/projects/372034180029504513 "https://wokwi.com/projects/372034180029504513")
