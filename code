# AMD

  // 05/11/17
// AUTO MEDICINE DISPENSER 

#include <Servo.h>
#include <LiquidCrystal.h>

const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);
int servoPin = 9;
Servo Servo1;
int led = 13;
int irpin = 7;

void setup()
{
  Servo1.attach(servoPin);
  lcd.begin(16, 2);
  lcd.setCursor(0,0);
  lcd.print("    AMD PLUS   ");
  pinMode(led, OUTPUT);
  pinMode(irpin, INPUT);
 //Serial.begin(9600);
  Servo1.write(0); // added on 30/10/17

}

void loop()
{
  Servo1.write(0);
  delay(1000);

  
  for (int i = 0; i <= 180; i +=1)
  {
    
    //Serial.println(i);
    delay(250); // to change the timing of each slot changed 1000 to 300 on 01/11/17
    
    if ( i == 0 | i == 60 | i == 120 | i == 180)
    {
      Servo1.write(i);
      if ( i == 0)
      {     lcd.setCursor(0,1);
            lcd.print( " LOAD MEDICINE");
      }
      else
      {   lcd.setCursor(0,1);
          lcd.print( "COLLECT MEDICINE  ");
      }
      while (digitalRead(irpin) == LOW)
      {

        if ( i == 0)
        {

          digitalWrite(led, HIGH);
          delay(1000);
          digitalWrite(led, LOW);
          delay(1000);
        }


        else
        {
          digitalWrite(led, HIGH);
          delay(100);
          digitalWrite(led,LOW);
          delay(500);
        }
      }
      digitalWrite(led, LOW);
     
    }
    
  // when tray opened timer stops till tray  closes. added on 5/11/17
  
   if(digitalRead(irpin) == HIGH)
    { 
      lcd.setCursor(0,1);
      lcd.print(" PUT TRAY BACK  ");
    }
    
    else
    {
      lcd.setCursor(0,1);
      lcd.print("                ");
    }
    
   // when tray opened timmer stops till tray  closes. added on 2/11/17   
   
   while(digitalRead(irpin) == HIGH) 
   
    { 
          digitalWrite(led, HIGH);
          delay(100);
          digitalWrite(led,LOW);
          delay(2000);
      
    }
  
   // added on 1/11/17  this is bring the servo to "0" position after 180 degree
    
   if ( i == 180 )
      {                   
        Servo1.write(0);
        delay(200);
      }
  }


}

