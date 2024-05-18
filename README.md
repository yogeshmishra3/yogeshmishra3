#include <TM1637Display.h>

// Define CLK and DIO pins for each display module
#define CLK_PIN_1 13
#define DIO_PIN_1 12
#define CLK_PIN_2 7
#define DIO_PIN_2 6
#define CLK_PIN_3 9
#define DIO_PIN_3 8
#define CLK_PIN_4 11
#define DIO_PIN_4 10

// Create instances for each TM1637 display
TM1637Display display1(CLK_PIN_1, DIO_PIN_1);
TM1637Display display2(CLK_PIN_2, DIO_PIN_2);
TM1637Display display3(CLK_PIN_3, DIO_PIN_3);
TM1637Display display4(CLK_PIN_4, DIO_PIN_4);

#define R1 29
#define Y1 25
#define G1 27
#define R2 32
#define Y2 28
#define G2 30
#define R3 22
#define Y3 26
#define G3 24
#define R4 5
#define Y4 3
#define G4 4
 
#define sensor1 A3
#define sensor2 A6
#define sensor3 A9
#define sensor4 A0
#define sensor5 A4
#define sensor6 A7
#define sensor7 A10
#define sensor8 A1
#define sensor9 A5
#define sensor10 A8
#define sensor11 A11
#define sensor12 A2

float IR1=0;
float IR2=0;
float IR3=0;
float IR4=0;
float IR5=0;
float IR6=0;
float IR7=0;
float IR8=0;
float IR9=0;
float IR10=0;
float IR11=0;
float IR12=0;

void setup() {
   Serial.begin(9600);
   // Initialize all displays
  display1.setBrightness(7); // Set brightness level (0x00 to 0x0f)
  display2.setBrightness(7);
  display3.setBrightness(7);
  display4.setBrightness(7);

pinMode(R1,OUTPUT);
pinMode(Y1,OUTPUT);
pinMode(G1,OUTPUT);

pinMode(R2,OUTPUT);
pinMode(Y2,OUTPUT);
pinMode(G2,OUTPUT);

pinMode(R3,OUTPUT);
pinMode(Y3,OUTPUT);
pinMode(G3,OUTPUT);

pinMode(R4,OUTPUT);
pinMode(Y4,OUTPUT);
pinMode(G4,OUTPUT);

pinMode(sensor1,INPUT);
pinMode(sensor2,INPUT);
pinMode(sensor3,INPUT);
pinMode(sensor4,INPUT);
pinMode(sensor5,INPUT);
pinMode(sensor6,INPUT);
pinMode(sensor7,INPUT);
pinMode(sensor8,INPUT);
pinMode(sensor9,INPUT);
pinMode(sensor10,INPUT);
pinMode(sensor11,INPUT);
pinMode(sensor12,INPUT);
}

void loop() {
unsigned long startTime = millis();  // Get the current time in milliseconds

 IR1=analogRead(sensor1);
 IR2=analogRead(sensor2);
 IR3=analogRead(sensor3);
 IR4=analogRead(sensor4);
 IR5=analogRead(sensor5);
 IR6=analogRead(sensor6);
 IR7=analogRead(sensor7);
 IR8=analogRead(sensor8);
 IR9=analogRead(sensor9);
 IR10=analogRead(sensor10);
 IR11=analogRead(sensor11);
 IR12=analogRead(sensor12);

  // Print sensor values to the serial monitor
  Serial.print("Sensor 1: ");
  Serial.print(IR1);
  Serial.print("\t Sensor 2: ");
  Serial.print(IR2);
  Serial.print("\t Sensor 3: ");
  Serial.print(IR3);
  Serial.print("\t Sensor 4: ");
  Serial.println(IR4);
  Serial.print("\t Sensor 5: ");
  Serial.print(IR5);
  Serial.print("\t Sensor 6: ");
  Serial.print(IR6);
  Serial.print("\t Sensor 7: ");
  Serial.print(IR7);
  Serial.print("\t Sensor 8: ");
  Serial.println(IR8);
  Serial.print("\t Sensor 9: ");
  Serial.print(IR9);
  Serial.print("\t Sensor 10: ");
  Serial.print(IR10);
  Serial.print("\t Sensor 11: ");
  Serial.print(IR11);
  Serial.print("\t Sensor 12: ");
  Serial.println(IR12);
delay(1000);

if(IR1>500&&IR2>500&&IR3>500&&IR4<500||
   IR5>500&&IR6>500&&IR7>500&&IR8<500
   ||IR9>500&&IR10>500&&IR11>500&&IR12<500)
 {digitalWrite(R1,HIGH);//g4 high
 digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,HIGH);
  digitalWrite(Y1,LOW);
   digitalWrite(G2,LOW);
   
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
   digitalWrite(G3,LOW);
   
  digitalWrite(R4,LOW);
 digitalWrite(Y4,LOW);
  digitalWrite(G4,HIGH);
   
  }
 //L L H L
 else if(IR1>500&&IR2>500&&IR3<500&&IR4>500
        || IR5>500&&IR6>500&&IR7<500&&IR8>500
        || IR9>500&&IR10>500&&IR11<500&&IR12>500)
  {digitalWrite(R1,HIGH);//g3 high
digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,HIGH);
 digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,LOW);
 digitalWrite(Y3,LOW);
  digitalWrite(G3,HIGH);
  
  digitalWrite(R4,HIGH);
 digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
}
//L L H H 
else if(IR1>500&&IR2>500&&IR3<500&&IR4>500
     ||   IR5>500&&IR6>500&&IR7<500&&IR8>500
      || IR9>500&&IR10>500&&IR11<500&&IR12>500)
 { digitalWrite(R1,HIGH);//G3 high
digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,HIGH);
digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,LOW);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,HIGH);
 
  digitalWrite(R4,HIGH);
 digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(5000);

  digitalWrite(R1,HIGH);//y3 and y4 high
digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);

  digitalWrite(R2,HIGH);
 digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
 
  digitalWrite(R3,LOW);
    digitalWrite(Y3,HIGH);
 digitalWrite(G3,LOW);
 
  digitalWrite(Y4,HIGH);
 digitalWrite(R4,LOW);
  digitalWrite(G4,LOW);
delay(1000);
 
  digitalWrite(R1,HIGH);//g4 high
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);

  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  
  digitalWrite(R4,LOW);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,HIGH);
  delay(5000);}
 //L H L L 
 else if(IR1>500&&IR2<500&&IR3>500&&IR4>500
        || IR5>500&&IR6<500&&IR7>500&&IR8>500||
         IR9>500&&IR10<500&&IR11>500&&IR12>500)
  {digitalWrite(R1,HIGH);//g2 high
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,LOW);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,HIGH);
 
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  }
//L H L H
 else if(IR1>500&&IR2<500&&IR3>500&&IR4>500||
         IR5>500&&IR6<500&&IR7>500&&IR8>500||
        IR9>500&&IR10<500&&IR11>500&&IR12>500)
  {digitalWrite(R1,HIGH);//g2 high
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,LOW);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,HIGH);
 
  digitalWrite(R3,HIGH);
 digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
 
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(5000);

  digitalWrite(R1,HIGH);//y2 y4 high
digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);

  digitalWrite(R2,LOW);
  digitalWrite(Y2,HIGH);
  digitalWrite(G2,LOW);

  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
 
  digitalWrite(Y4,HIGH);
 digitalWrite(R4,LOW);
  digitalWrite(G4,LOW);
  delay(1000);
  
   digitalWrite(R1,HIGH);//g4 high
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);

  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
 
  digitalWrite(R4,LOW);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,HIGH);
  delay(5000);}
//L H H L 
else if(IR1>500&&IR2<500&&IR3>500&&IR4>500
       || IR5>500&&IR6<500&&IR7>500&&IR8>500
       || IR9>500&&IR10<500&&IR11>500&&IR12>500)
  {digitalWrite(R1,HIGH);//g2 high
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,LOW);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,HIGH);
 
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  
  digitalWrite(R4,HIGH);
  digitalWrite(R4,LOW);
  digitalWrite(G4,LOW);
  delay(5000);

digitalWrite(R1,HIGH);//y2 y3 high
 digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);

  digitalWrite(R1,LOW);
  digitalWrite(Y2,HIGH);
  digitalWrite(G2,LOW);

  digitalWrite(R3,LOW);
    digitalWrite(Y3,HIGH);
 digitalWrite(G3,LOW);
 
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(1000);
  digitalWrite(R1,HIGH);//g3 high
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,LOW);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,HIGH);
  
  digitalWrite(R4,HIGH);
 digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(5000);}
 //L H H H 
else if(IR1>500&&IR2<500&&IR3>500&&IR4>500
       || IR5>500&&IR6<500&&IR7>500&&IR8>500
       || IR9>500&&IR10<500&&IR11>500&&IR12>500)//g2 high
{digitalWrite(R1,HIGH);
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,LOW);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,HIGH);
  
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(5000);

  digitalWrite(R1,HIGH);//y2 y3 high
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);

  digitalWrite(R1,LOW);
  digitalWrite(Y2,HIGH);
    digitalWrite(G2,LOW);
 
  digitalWrite(R3,LOW);
   digitalWrite(Y3,HIGH);
 digitalWrite(G3,LOW);
  
  digitalWrite(R4,HIGH);
 digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(1000);
//g3 high
  digitalWrite(R1,HIGH);
 digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,LOW);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,HIGH);
  
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(5000);

  digitalWrite(R1,HIGH);//y3 y4 high
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
 digitalWrite(R3,LOW);
  digitalWrite(Y3,HIGH);
  digitalWrite(G3,LOW);

  digitalWrite(R4,LOW);
  digitalWrite(Y4,HIGH);
   digitalWrite(G4,LOW);
  delay(1000);
//g4 high
   digitalWrite(R1,HIGH);
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  
  digitalWrite(R4,LOW);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,HIGH);
  delay(5000);}
//H L L L
else if(IR1<500&&IR2>500&&IR3>500&&IR4>500
     ||  IR5<500&&IR6>500&&IR7>500&&IR8>500
     ||  IR9<500&&IR10>500&&IR11>500&&IR12>500)
  {digitalWrite(R1,LOW);//g1 high
  digitalWrite(Y1,LOW);
  digitalWrite(G1,HIGH);
  
  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  }
//H L L H
else if(IR1<500&&IR2>500&&IR3>500&&IR4>500
      ||  IR5<500&&IR6>500&&IR7>500&&IR8>500
     ||  IR9<500&&IR10>500&&IR11>500&&IR12>500)
 { digitalWrite(R1,LOW);//g1 high
  digitalWrite(Y1,LOW);
  digitalWrite(G1,HIGH);
  
  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(5000);

  digitalWrite(Y1,HIGH);//y1 y4 high
  digitalWrite(R1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  
  digitalWrite(Y4,HIGH);
  digitalWrite(R4,LOW);
  digitalWrite(G4,LOW);
delay(1000);

   digitalWrite(R1,HIGH);//g4 high
 digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  
  digitalWrite(R4,LOW);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,HIGH);
  delay(5000);}
//H L H L 
else if(IR1>500&&IR2<500&&IR3>500&&IR4<500
      || IR5>500&&IR6<500&&IR7>500&&IR8<500
     ||  IR9>500&&IR10<500&&IR11>500&&IR12<500)
  {digitalWrite(R1,LOW);//g1 high
  digitalWrite(Y1,LOW);
  digitalWrite(G1,HIGH);
  
  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(5000);

 digitalWrite(Y1,HIGH);//y1 y3 high
digitalWrite(R1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,HIGH);
 digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
 
  digitalWrite(R3,LOW);
    digitalWrite(Y3,HIGH);
    digitalWrite(G3,LOW);
    
  digitalWrite(R4,HIGH);
 digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(1000);
  
   digitalWrite(R1,HIGH);//g3 high
   digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,HIGH);
 digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,LOW);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,HIGH);
  
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(5000);}
//H L H H 
else if(IR1<500&&IR2>500&&IR3>500&&IR4>500
      ||  IR5<500&&IR6>500&&IR7>500&&IR8>500
     ||  IR9<500&&IR10>500&&IR11>500&&IR12>500)//g1 high
{digitalWrite(R1,LOW);
  digitalWrite(Y1,LOW);
  digitalWrite(G1,HIGH);
  
  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(5000);
 
  digitalWrite(Y1,HIGH);//y1 y3 high
  digitalWrite(R1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
 digitalWrite(G2,LOW);
  
  digitalWrite(R3,LOW);
  digitalWrite(Y3,HIGH);
  digitalWrite(G3,LOW);
 
  digitalWrite(R4,HIGH);
 digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(1000);
//g3 high
  digitalWrite(R1,HIGH);
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);

  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,LOW);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,HIGH);
 
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(5000);

  digitalWrite(R1,HIGH);//y3 y4 high
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);

  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,LOW);
    digitalWrite(Y3,HIGH);
    digitalWrite(G3,LOW);
    
digitalWrite(R4,LOW);
  digitalWrite(Y4,HIGH);
  digitalWrite(G4,LOW);
  delay(1000);
//g4 high
   digitalWrite(R1,HIGH);
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,HIGH);
 digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,HIGH);
 digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  
  digitalWrite(R4,LOW);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,HIGH);
  delay(5000);}
//H H L L 
else if(IR1<500&&IR2>500&&IR3<500&&IR4<500
        ||IR5<500&&IR6>500&&IR7<500&&IR8<500
       || IR9<500&&IR10>500&&IR11<500&&IR12<500)
//g1 high
{digitalWrite(R1,LOW);
  digitalWrite(Y1,LOW);
  digitalWrite(G1,HIGH);
  
  digitalWrite(R2,HIGH);
 digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
    digitalWrite(G3,LOW);
    
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(5000);
 
  digitalWrite(Y1,HIGH);//y1 y2 high
  digitalWrite(R1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R1,LOW);
  digitalWrite(Y2,HIGH);
   digitalWrite(G2,LOW);
   
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(1000);
//g2 high
  digitalWrite(R1,HIGH);
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,LOW);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,HIGH);
  
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(5000);}
//H H H L
else if (IR1>500&&IR2>500&&IR3>500&&IR4<500
        ||IR5>500&&IR6>500&&IR7>500&&IR8<500
      || IR9>500&&IR10>500&&IR11>500&&IR12<500)
//g1 high

{  digitalWrite(R1,LOW);
   digitalWrite(Y1,LOW);
  digitalWrite(G1,HIGH);
  
  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,HIGH);
 digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(5000);

 
  digitalWrite(Y1,HIGH);//y1 y2 high
  digitalWrite(R1,LOW);
  digitalWrite(G1,LOW);

  digitalWrite(R2,LOW);
  digitalWrite(Y2,HIGH);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  
  digitalWrite(R4,HIGH);
 digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(1000);
//g2 high
 digitalWrite(R1,HIGH);
 digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,LOW);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,HIGH);
  
  digitalWrite(R3,HIGH);
 digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  
  digitalWrite(R4,HIGH);
 digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(5000);

  digitalWrite(R1,HIGH);//y2 y3 high
digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);

  digitalWrite(R2,LOW);
  digitalWrite(Y2,HIGH);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,LOW);
  digitalWrite(Y3,HIGH);
  digitalWrite(G3,LOW);
  
  digitalWrite(R4,HIGH);
 digitalWrite(Y4,LOW);
 digitalWrite(G4,LOW);
  delay(1000);
//g3 high
   
  digitalWrite(R1,HIGH);
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  
  digitalWrite(R2,HIGH);
digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  
  digitalWrite(R3,LOW);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,HIGH);
  
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(5000);}

else 
{//G1 high for 3000 delay 
  digitalWrite(G4,LOW);
  digitalWrite(R1,LOW);
  digitalWrite(Y1,LOW);

  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G1,HIGH);
  digitalWrite(R4,HIGH);
  for (int i = 20; i > 0; i--) {
     display1.showNumberDec(i, false);
    delay(1000);
  }
   
 // delay(10000);
//G1 and Y2 high for 1000 delay
  digitalWrite(R1,LOW);
  digitalWrite(Y1,LOW);
  digitalWrite(G1,HIGH);
  digitalWrite(R2,LOW);
  digitalWrite(Y2,HIGH);
  digitalWrite(G2,LOW);
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(1000);
//Y1 and G2 high for 1000 delay 
  digitalWrite(R1,LOW);
  digitalWrite(Y1,HIGH);
  digitalWrite(G1,LOW);
  digitalWrite(R2,LOW);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,HIGH);
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(1000);
//G2 high for 2000 delay 
  digitalWrite(R1,HIGH);
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  digitalWrite(R2,LOW);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,HIGH);
   for (int i = 20; i > 0; i--) {
     display2.showNumberDec(i, false);
    delay(1000);
  }
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  // delay(10000); // Check if pin R3 is HIGH
//G2 and Y3 high for 1000 delay 
  digitalWrite(R1,HIGH);
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  digitalWrite(R2,LOW);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,HIGH);
  digitalWrite(R3,LOW);
  digitalWrite(Y3,HIGH);
  digitalWrite(G3,LOW);
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(1000);
//G3 and Y2 high for 1000 delay 
  digitalWrite(R1,HIGH);
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  digitalWrite(R2,LOW);
  digitalWrite(Y2,HIGH);
  digitalWrite(G2,LOW);
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  digitalWrite(R4,HIGH);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
  delay(1000);
//G3 high for 2000 delay 
  digitalWrite(R1,HIGH);
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  digitalWrite(R3,LOW);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,HIGH);
   for (int i = 20; i > 0; i--) {
     display3.showNumberDec(i, false);
    delay(1000);
  }
  digitalWrite(R4,LOW);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,LOW);
 // delay(10000);
//G3 and Y4 for 1000 delay 
  digitalWrite(R1,HIGH);
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  digitalWrite(R3,LOW);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,HIGH);
  digitalWrite(R4,LOW);
  digitalWrite(Y4,HIGH);
  digitalWrite(G4,LOW);
  delay(1000);
//G4 and Y3 HIGH for 1000 delay
  digitalWrite(R1,HIGH);
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  digitalWrite(R3,LOW);
  digitalWrite(Y3,HIGH);
  digitalWrite(G3,LOW);
  digitalWrite(R4,LOW);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,HIGH); 
  delay(1000);
//G4 high for 200 delay 
  digitalWrite(R1,HIGH);
  digitalWrite(Y1,LOW);
  digitalWrite(G1,LOW);
  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  digitalWrite(R4,LOW);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,HIGH);
   for (int i = 20; i > 0; i--) {
     display4.showNumberDec(i, false);
    delay(1000);
  }
 // delay(10000);
//G4 and Y1 high for 1000 delay 
  digitalWrite(R1,LOW);
  digitalWrite(Y1,HIGH);
  digitalWrite(G1,LOW);
  digitalWrite(R2,HIGH);
  digitalWrite(Y2,LOW);
  digitalWrite(G2,LOW);
  digitalWrite(R3,HIGH);
  digitalWrite(Y3,LOW);
  digitalWrite(G3,LOW);
  digitalWrite(R4,LOW);
  digitalWrite(Y4,LOW);
  digitalWrite(G4,HIGH);
  delay(1000);
}}
