# Arduino Radar Model for Distance and Angle Finding using Ultrasonic Sensor and Servo Motor

## Components used / Material
* Arduino uno
* Ultrasonic sensor
* Servo Motor


## Circuit Diagram of Arduino Radar Model

![image](https://github.com/ashiksarker2018000000125/Emabbded-SystemLab-Final-Project/blob/main/radar_circuit_diagram.png)


## Code of the project
```
#include <Servo.h>. 
const int trigPin = 10;
const int echoPin = 11;
long duration;
int distance;
Servo myServo;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT); 
  Serial.begin(9600);
  myServo.attach(12); 
}
void loop() {
  for(int i=15;i<=165;i++){  
    myServo.write(i);
    delay(30);
    distance = calculateDistance();
    Serial.print(i);
    Serial.print(","); 
    Serial.print(distance); 
    Serial.print("."); 
  }


  for(int i=165;i>15;i--){  
    myServo.write(i);
    delay(30);
    distance = calculateDistance();
    Serial.print(i);
    Serial.print(",");
    Serial.print(distance);
    Serial.print(".");
  }
}

int calculateDistance(){ 
  
  digitalWrite(trigPin, LOW); 
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH); 
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH); 
  distance= duration*0.034/2;
  return distance;
}
```
