- š Hi, Iām @maininkaew
- š Iām interested in ...
- š± Iām currently learning ...
- šļø Iām looking to collaborate on ...
- š« How to reach me ...

<!---
maininkaew/maininkaew is a āØ special āØ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

//start




#include<LiquidCrystal.h>
LiquidCrystal lcd(13,12,11,10,9,8) ;
float value=0 ;
float rev=0 ;
int rpm ;
int oldtime ;
int time ;

void isr()
{
 rev++;
}

void setup() {
  lcd.begin(16,2) ;
  attachInterrupt(0,isr,RISING) ;
}

void loop() {
  
  delay(1000) ;
  detachInterrupt(0) ;
  time=millis()-oldtime ;
  rpm=(rev/time)*60000/3 ;
  oldtime=millis();
  rev=0;
  lcd.clear() ;
  lcd.setCursor(3,0) ;
  lcd.print("TACHOMETER") ;
  lcd.setCursor(4,1) ;
  lcd.print(     rpm) ;
  lcd.print("  RPM" ) ;
  lcd.print("   ") ;
  attachInterrupt(0,isr,RISING);
  
  
 
   
  
}
