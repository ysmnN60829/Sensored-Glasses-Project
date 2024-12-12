
Details
 // eazytronic.com
 #include <Servo.h> // servo library
Servo s1;
const int trigPin = 9;     // ultrasoni sensor pin
const int echoPin = 10;    // ultrasoni sensor pin
long duration;
int distanceCm, distanceInch;
void setup()
{
Serial.begin(9600); 
s1.attach(3);
pinMode(trigPin, OUTPUT);
pinMode(echoPin, INPUT);

}
void loop() {
digitalWrite(trigPin, LOW);
delayMicroseconds(2);
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);
duration = pulseIn(echoPin, HIGH);
distanceCm= duration*0.034/2;
distanceInch = duration*0.0133/2;
Serial.println("Distance: ");
Serial.println(distanceCm);

if(distanceCm < 25)
{
  s1.write(90);
  delay(2000);
}
else 
{
  s1.write(0);
  delay(500);
}
}

