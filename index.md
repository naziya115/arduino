# 05.03.22. Arduino lesson
## lcd  
- SDA — AREF
- SCL — to the first one (before AREF)
- UCC — to 5V
- GND — to GND
```
#define _LCD_TYPE 1 
#include <LCD_1602_RUS_ALL.h> // Подключение библиотеки 
LCD_1602_RUS <LiquidCrystal_I2C> lcd(0x27, 16, 2);

//ӨСКЕМЕН

byte g[] = {
  B11111,
  B10001,
  B10001,
  B11111,
  B10001,
  B10001,
  B11111,
  B00000
};
byte k[] = {
  B10001,
  B10010,
  B10100,
  B11000,
  B10100,
  B10010,
  B10011,
  B10011
};

void setup() {
  lcd.init(); 
  lcd.backlight();
  lcd.createChar(2, g);
  lcd.setCursor(0,0); 
  lcd.print("\2СКЕМЕН");
 
}

void loop() { }
```

``` 
//НАҒЫЗ ҚАЗАҚ
#define _LCD_TYPE 1 
#include <LCD_1602_RUS_ALL.h> // Подключение библиотеки 
LCD_1602_RUS <LiquidCrystal_I2C> lcd(0x27, 16, 2);

byte g[] = {
  B11111,
  B10000,
  B10000,
  B11110,
  B10000,
  B10000,
  B10000,
  B10000
};
byte k[] = {
  B10001,
  B10010,
  B10100,
  B11000,
  B10100,
  B10010,
  B10011,
  B10011
};

void setup() {
  lcd.init(); 
  lcd.backlight();
  lcd.createChar(3, k);
  lcd.createChar(2, g);
  lcd.setCursor(0,0); 
  lcd.print("НА\2ЫЗ");
  lcd.setCursor(0,1); 
  lcd.print("\3A3A\3"); 
 
}

void loop() { }
```
