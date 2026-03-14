#define BLYNK_TEMPLATE_ID ",,,,,,,," 
#define BLYNK_TEMPLATE_NAME "Robo car" 
#define BLYNK_AUTH_TOKEN "..............."

#include <WiFi.h> 
#include <BlynkSimpleEsp32.h>

// Replace these with your actual network and Blynk credentials 
char auth[] = "....................";  

// Blynk Auth Token from the app 
char ssid[] = "...............";     // Wi-Fi SSID 
char pass[] = "...............";     // Wi-Fi Password

// Motor control pins 
#define ENA 35 
#define ENB 27 
#define IN1 32 
#define IN2 33 
#define IN3 25 
#define IN4 26

int speedA = 255; // Default speed for motor A (left side) 
int speedB = 255; // Default speed for motor B (right side)


BLYNK_WRITE(V0) {
  if (param.asInt()) { 
    moveForward();  // Button pressed 
  } else { stopMotors();   // Button released 
  } 
}

BLYNK_WRITE(V1) {
  if (param.asInt()) { 
    moveBackward();  // Button pressed 
    } else { stopMotors();   // Button released 
    } 
} 

BLYNK_WRITE(V2) {
  if (param.asInt()) { 
    turnLeft();  // Button pressed 
    } else { stopMotors();   // Button released 
    } 
} 

BLYNK_WRITE(V3) {
  if (param.asInt()) { 
    turnRight();  // Button pressed 
    } else { stopMotors();   // Button released 
    } 
} 

BLYNK_WRITE(V4) {
  if (param.asInt()) { 
    stopMotors();  // Button pressed 
  } else { stopMotors();   // Button released 
  } 
} 

// Speed sliders 
BLYNK_WRITE(V5) { 
  speedA = param.asInt(); 
  Serial.print("Speed A: "); Serial.println(speedA); 
  } 

BLYNK_WRITE(V6) { 
  speedA = param.asInt(); 
  Serial.print("Speed B: "); Serial.println(speedA); 
  } 


void setup() { 
  
  Serial.begin(115200);
// Motor pins 
pinMode(ENA, OUTPUT); 
pinMode(ENB, OUTPUT); 
pinMode(IN1, OUTPUT); 
pinMode(IN2, OUTPUT); 
pinMode(IN3, OUTPUT); 
pinMode(IN4, OUTPUT);

// Start Blynk 
Blynk.begin(auth, ssid, pass); }

void loop() { 
  Blynk.run(); }

// Movement functions 
void moveForward() { 
  Serial.println("Moving Forward"); 
  digitalWrite(IN1, HIGH); digitalWrite(IN2, LOW); 
  digitalWrite(IN3, HIGH); digitalWrite(IN4, LOW); 
  analogWrite(ENA, speedA); analogWrite(ENB, speedB); 
  }
void moveBackward() { 
  Serial.println("Moving Backward"); 
  digitalWrite(IN1, LOW); digitalWrite(IN2, HIGH); 
  digitalWrite(IN3, LOW); digitalWrite(IN4, HIGH); 
  analogWrite(ENA, speedA); analogWrite(ENB, speedB); 
  }
void turnLeft() { 
  Serial.println("Turning Left"); 
  digitalWrite(IN1, LOW); digitalWrite(IN2, HIGH); 
  digitalWrite(IN3, HIGH); digitalWrite(IN4, LOW); 
  analogWrite(ENA, speedA); analogWrite(ENB, speedB); 
  }
void turnRight() { 
  Serial.println("Turning Right"); 
  digitalWrite(IN1, HIGH); digitalWrite(IN2, LOW); 
  digitalWrite(IN3, LOW); digitalWrite(IN4, HIGH); 
  analogWrite(ENA, speedA); analogWrite(ENB, speedB);
  }
void stopMotors() { 
  Serial.println("Stopping Motors"); 
  digitalWrite(IN1, LOW); digitalWrite(IN2, LOW); 
  digitalWrite(IN3, LOW); digitalWrite(IN4, LOW);
}
