# Rfid module
### Link to RFID-module code + connection: https://ampermarket.kz/base/ex22-rfid/

```
#include <Servo.h> 
#include <SPI.h> // подключаем библиотеки 
#include <MFRC522.h> 
 
  
#define RST_PIN 9 
#define SS_PIN 10 
#define RED_LED 2 
#define GREEN_LED 3 
int piezoPin = 5; 
  
MFRC522 mfrc522(SS_PIN, RST_PIN); 
  
unsigned long uidDec, uidDecTemp;  // для храниения номера метки в десятичном формате 
 
Servo servo; 
 
void setup() { 
  Serial.begin(9600); 
  Serial.println("Waiting for card..."); 
  SPI.begin(); // инициализация SPI / Init SPI bus. 
  mfrc522.PCD_Init(); // инициализация MFRC522 / Init MFRC522 
  pinMode(RED_LED, OUTPUT); // красный светодиод 
  pinMode(GREEN_LED, OUTPUT); // зеленый светодиод 
  servo.attach(7); 
} 
  
void loop() { 
  // по умолчанию светодиоды не горят 
  digitalWrite(RED_LED, LOW);   
  digitalWrite(GREEN_LED, LOW);  
  // Поиск новой метки 
  if ( ! mfrc522.PICC_IsNewCardPresent()) { 
    return; 
  } 
  // Выбор метки 
  if ( ! mfrc522.PICC_ReadCardSerial()) { 
    return; 
  } 
  uidDec = 0; 
  // Выдача серийного номера метки. 
  for (byte i = 0; i < mfrc522.uid.size; i++) 
  { 
    uidDecTemp = mfrc522.uid.uidByte[i]; 
    uidDec = uidDec * 256 + uidDecTemp; 
  } 
  Serial.println("Card UID: "); 
  Serial.println(uidDec); // Выводим UID метки в монитор порта 
  if (uidDec == 2510910695) // Сравниваем Uid метки, если он равен заданному, то загорается зеленый светодиод, иначе красный 
  { 
     digitalWrite(GREEN_LED, HIGH);  
     digitalWrite(RED_LED, LOW); 
     servo.write(0); 
     delay(3000);  
     servo.write(90);  
     tone(piezoPin, 1000);     
  } 
  else { 
     digitalWrite(RED_LED, HIGH);   
     digitalWrite(GREEN_LED, LOW); 
     tone(piezoPin, 1000); 
  }  
 /* delay(1500); 
  noTone(piezoPin); */
}
```
