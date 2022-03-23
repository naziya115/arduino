* ~~rfid scanner connect with your card~~
* how to track state of multile buttons
* connect rfid to the project


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



### Rfid scanner with buttons
```#include <Servo.h> 
#include <SPI.h> // подключаем библиотеки 
#include <MFRC522.h> 

#define RST_PIN 9 
#define SS_PIN 10 
int piezoPin = 5; 

MFRC522 mfrc522(SS_PIN, RST_PIN); 
  
unsigned long uidDec, uidDecTemp;  // для храниения номера метки в десятичном формате 

const int  btnstop = 5;    
const int  btnprev = 6;   
const int  btnnext = 7;   

int btnstop_state = 0;         
int btnstop_lstate = 0;    

int btnprev_state = 0;         
int btnprev_lstate = 0;  

int btnnext_state = 0;         
int btnnext_lstate = 0; 

void setup() {
  // initialize the button pin as a input:
  pinMode(btnstop, INPUT);
  pinMode(btnprev, INPUT);
  pinMode(btnnext, INPUT);
  // initialize serial communication:
  Serial.begin(9600);
  Serial.println("Waiting for card..."); 
  SPI.begin(); // инициализация SPI / Init SPI bus. 
  mfrc522.PCD_Init(); // инициализация MFRC522 / Init MFRC522 
}


void loop() {
  btnstop_state = digitalRead(btnstop);
  btnprev_state = digitalRead(btnprev);
  if (btnstop_state != btnstop_lstate) {
    if (btnstop_state == HIGH) {
      Serial.println("stopped");
    } else {
      Serial.println("played");
    }
  }
  btnstop_lstate = btnstop_state;

//  btnnext_state = digitalRead(btnnext);
   if (btnprev_state != btnprev_lstate) {
    if (btnprev_state == HIGH) {
      Serial.println("prev");
    } else {
      Serial.println("off");
    }
  }
  btnprev_lstate = btnprev_state;


  


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
  if (uidDec == 2249957616) // Сравниваем Uid метки, если он равен заданному, то загорается зеленый светодиод, иначе красный 
  { 
    Serial.println("music 1 plays");
    delay(1000);
  } 
  if (uidDec == 637102311) // Сравниваем Uid метки, если он равен заданному, то загорается зеленый светодиод, иначе красный 
  { 
    Serial.println("music 2 plays");
    delay(1000);
  }  
}
```
