#include <LiquidCrystal.h>          //lcd kütüphanesi
LiquidCrystal lcd(12,11,5,4,3,2);   //lcd baglantı pinleri 
int analogInput = 0;
float vout = 0.0;
float vin = 0.0;
float R1 = 10000.0; // 10K ohm direnç
float R2 = 1000.0; // 1K ohm direnç
int value = 0;
void setup(){
   pinMode(analogInput, INPUT);
   lcd.begin(16, 2);
   lcd.setCursor(1, 0);
   lcd.print("VOLTMETRE");
}
void loop(){
   
   value = analogRead(analogInput);
   vout = (value * 5.0) / 1024.0; 
   vin = vout / (R2/(R1+R2)); 
   if (vin<0.09) {
   vin=0.0;
} 
lcd.setCursor(1, 1);
lcd.print("VOLTAJ V= ");
lcd.print(vin);
delay(1000);
}
