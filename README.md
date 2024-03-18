# Arduino-Newping

### Distance 수정 전
#include <NewPing.h>

#define TRIGGER_PIN  2  
#define ECHO_PIN     3  
#define MAX_DISTANCE 100 

NewPing sonar(TRIGGER_PIN, ECHO_PIN, MAX_DISTANCE); 

void setup() {
  Serial.begin(115200); 
}

void loop() {
  delay(50);                    
  Serial.print("Ping: ");
  Serial.print(sonar.ping_cm()); 
  Serial.println("cm");
}

### Distance 수정 후 

#include <NewPing.h>

#define TRIGGER_PIN  2
#define ECHO_PIN     3 
#define MAX_DISTANCE 100

NewPing sonar(TRIGGER_PIN, ECHO_PIN, MAX_DISTANCE);

void setup() {
  Serial.begin(115200);
}

void loop() {
  float distance = 0.0;
  delay(50);                   
  distance = sonar.ping_cm();
  if (distance ==0) distance = MAX_DISTANCE;
  Serial.print("Ping: ");
  Serial.print(distance); 
  Serial.println("cm");
}
