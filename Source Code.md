#define trigPin1 6 
#define echoPin1 5 
#define trigPin2 10 
#define echoPin2 9 
 
 
long duration, distance1,distance2, RightSensor,BackSensor,FrontSensor,LeftSensor; 
 
 void setup() 
{ 
Serial.begin 	(9600); pinMode(trigPin1, OUTPUT); pinMode(echoPin1, INPUT); pinMode(trigPin2, OUTPUT); pinMode(echoPin2, INPUT); 
} 
 
 void loop() { 
SonarSensor(trigPin1, echoPin1); RightSensor = distance1; if(distance1<10) 
{ 
 
digitalWrite(7,HIGH); 
delay(10); digitalWrite(4,HIGH); delay(10); digitalWrite(3,HIGH); 
} 
SonarSensor(trigPin2, echoPin2); LeftSensor = distance1; if(distance1<10) 
{ 
digitalWrite(7,LOW); 
delay(10); digitalWrite(4,LOW); delay(10); digitalWrite(3,LOW); 
} 
Serial.print(LeftSensor); 
Serial.print(" - "); 
Serial.println(RightSensor); 
 
}  
 void SonarSensor(int trigPin,int echoPin) 
{ 
digitalWrite(trigPin, LOW); delayMicroseconds(2); digitalWrite(trigPin, HIGH); delayMicroseconds(10); digitalWrite(trigPin, LOW); duration = pulseIn(echoPin, HIGH); distance1 = (duration/2) / 29.1; 
  
}
