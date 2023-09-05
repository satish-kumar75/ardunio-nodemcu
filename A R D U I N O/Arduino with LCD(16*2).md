# Demonstration of working of LCD with Arduino 
_____

## Circuit Snapshot
![image](https://github.com/SatishKumar75/ardunio-nodemcu/assets/106571472/2fde9a5f-53fa-4826-9bd3-6ef237132993)

------

[Live Simulation](https://www.tinkercad.com/things/66shgoBClfo "https://www.tinkercad.com/things/66shgoBClfo")

-----

## This is the code of the Printing the ASCAII Values of all the Small letters
```c++
#include <LiquidCrystal.h>

LiquidCrystal lcd (2, 3, 4, 5, 6, 7);

void setup() {
  lcd.begin(16, 2);
}

void loop() { 
   lcd.setCursor(0, 0);
   lcd.print("ASCII Values:");
   delay(1000);
  
  for (char letter = 'a'; letter <= 'z'; letter++) {
    lcd.setCursor(0, 1);
    lcd.print(letter);
    lcd.print(": ");
    lcd.print((int)letter);
    delay(500);
    lcd.clear();
  }

  delay(5000);
}

```

