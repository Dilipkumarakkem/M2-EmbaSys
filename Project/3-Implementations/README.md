#include <LiquidCrystal.h>
const int trig_pin = 13;
const int echo_pin = 12;

long distance, duration;

const int rs = 7, en = 6, d4 = 3, d5 = 2, d6 = 1, d7 = 0;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);

void setup()
{
lcd.begin(16, 2);
lcd.print("Dilip");
pinMode(trig_pin, OUTPUT);
pinMode(echo_pin, INPUT);
}

void loop()
{
digitalWrite(trig_pin,HIGH);
delayMicroseconds(20);
digitalWrite(trig_pin,LOW);
delayMicroseconds(20);

duration = pulseIn(echo_pin, HIGH); //To receive the reflected signal.
distance= duration*0.034/2;

lcd.setCursor(0,1); //set the cursor to column 0 and line 1
lcd.print(distance);
lcd.print("cm");
delay(100);
}