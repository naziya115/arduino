* ~~rfid scanner connect with your card~~
* build the same thing with buttons
* connect rfid to the project
* when one button clicked rfid scanner switch


```
#include <Servo.h> 
#include <SPI.h> // подключаем библиотеки 
#include <MFRC522.h> 
 
  
#define RST_PIN 9 
#define SS_PIN 10 
int piezoPin = 5; 
  
MFRC522 mfrc522(SS_PIN, RST_PIN); 
  
unsigned long uidDec, uidDecTemp;  // для храниения номера метки в десятичном формате 
 
Servo servo; 
 
void setup() { 
  Serial.begin(9600); 
  Serial.println("Waiting for card..."); 
  SPI.begin(); // инициализация SPI / Init SPI bus. 
  mfrc522.PCD_Init(); // инициализация MFRC522 / Init MFRC522 
  servo.attach(7); 
} 
  
void loop() {   
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
  if (uidDec == 3321693555) // Сравниваем Uid метки, если он равен заданному, то загорается зеленый светодиод, иначе красный 
  { 
    Serial.println("correct");
    delay(1000);
  } 
  else { 
      Serial.println("incorrect");
      delay(1000);
  }  
 /* delay(1500); 
  noTone(piezoPin); */
}
```
