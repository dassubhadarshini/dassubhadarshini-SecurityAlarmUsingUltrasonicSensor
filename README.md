# Security Alarm Using Ultrasonic Sensor

## Project Overview

This project implements a simple and effective security alarm system using an ultrasonic sensor. The system detects objects or intruders within a specified range and triggers an alarm when motion is detected. Ultrasonic sensors are capable of measuring the distance between an object and the sensor, making them ideal for intrusion detection systems.

The project is ideal for beginners in electronics and IoT, and can be extended for home automation, office security, or other purposes requiring motion detection.

## Materials Required

- Ultrasonic Sensor (HC-SR04)
- Microcontroller (Arduino Uno or similar)
- Buzzer or Alarm
- Jumper Wires
- Breadboard
- 9V Battery or USB Power Supply
- Resistors (if needed)
- LED (optional, for visual alerts)
- Connecting cables

## How It Works

The system operates by sending out ultrasonic waves using the ultrasonic sensor. The sensor measures the time taken for the waves to bounce back from an object, calculating the distance based on the time difference. If the measured distance falls below a defined threshold (indicating the presence of an object or person within range), an alarm is triggered.

### Working Principle:

1. **Ultrasonic Sensor**: The HC-SR04 sensor emits ultrasonic sound waves at a frequency of 40kHz. When these waves hit an object, they are reflected back to the sensor. The sensor calculates the distance to the object based on the time taken for the echo to return.
   
2. **Microcontroller**: The Arduino (or any other microcontroller) processes the input from the sensor, continuously monitoring the distance. When the distance is below a specified limit (e.g., 20 cm), the alarm is triggered.

3. **Alarm Triggering**: When an object is detected within the defined range, the microcontroller activates the buzzer or alarm, alerting the user of potential intrusion.


## Code

const int trig = 12;
const int echo = 13;
const int Buzz = 8;
const int LED2 = 7;
const int LED3 = 6;
const int LED4 = 5;
const int LED5 = 4;
const int LED6 = 3;
const int LED7 = 2;
int duration = 0;
int distance = 0;
int offTimeDelay=125;
int onTimeDelay=150;

void setup() 
{
Serial.begin(9600);
  pinMode(trig , OUTPUT);

  pinMode(echo , INPUT);

  pinMode(Buzz , OUTPUT);
  pinMode(LED2 , OUTPUT);
  pinMode(LED3 , OUTPUT);
  pinMode(LED4 , OUTPUT);
  pinMode(LED5 , OUTPUT);
  pinMode(LED6 , OUTPUT);
  pinMode(LED7 , OUTPUT);

}
void loop()
{
  digitalWrite(trig , HIGH);
  delayMicroseconds(1000);
  digitalWrite(trig , LOW);

  duration = pulseIn(echo , HIGH);

  distance = (duration/2) / 28.5 ;

  Serial.println(distance);

  if ( distance <= 7 )
  {
    digitalWrite(Buzz, HIGH);
    
    digitalWrite(Buzz, HIGH);
    digitalWrite(LED2,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED3,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED4,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED5,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED6,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED7,HIGH);
    delay(onTimeDelay);
    digitalWrite(Buzz,LOW);
    delay(onTimeDelay);

    digitalWrite(Buzz, HIGH);
    digitalWrite(LED2,HIGH);
    delay(offTimeDelay);
    digitalWrite(LED3,LOW);
    delay(onTimeDelay);
    digitalWrite(LED4,HIGH);
    delay(offTimeDelay);
    digitalWrite(LED5,LOW);
    delay(onTimeDelay);
    digitalWrite(LED6,HIGH);
    delay(offTimeDelay);
    digitalWrite(LED7,LOW);
    delay(onTimeDelay);
    digitalWrite(Buzz,LOW);
    delay(onTimeDelay);

    digitalWrite(Buzz, HIGH);
    digitalWrite(LED2,LOW);
    delay(offTimeDelay);
    digitalWrite(LED3,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED4,LOW);
    delay(offTimeDelay);
    digitalWrite(LED5,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED6,LOW);
    delay(offTimeDelay);
    digitalWrite(LED7,HIGH);
    delay(onTimeDelay);
    digitalWrite(Buzz,LOW);
    delay(onTimeDelay);

    digitalWrite(Buzz, HIGH);
    digitalWrite(LED2,LOW);
    delay(offTimeDelay);
    digitalWrite(LED7,LOW);
    delay(offTimeDelay);
    digitalWrite(LED3,LOW);
    delay(offTimeDelay);
    digitalWrite(LED6,LOW);
    delay(offTimeDelay);
    digitalWrite(LED4,LOW);
    delay(offTimeDelay);
    digitalWrite(LED5,LOW);
    delay(offTimeDelay);


    digitalWrite(Buzz, HIGH);
    digitalWrite(LED2,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED7,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED3,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED6,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED5,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED6,HIGH);
    delay(onTimeDelay);


    
    digitalWrite(Buzz, HIGH);
    digitalWrite(LED2,LOW);
    delay(offTimeDelay);
    digitalWrite(LED2,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED3,LOW);
    delay(offTimeDelay);
    digitalWrite(LED3,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED4,LOW);
    delay(offTimeDelay);
    digitalWrite(LED4,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED5,LOW);
    delay(offTimeDelay);
    digitalWrite(LED5,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED6,LOW);
    delay(offTimeDelay);
    digitalWrite(LED6,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED7,LOW);
    delay(offTimeDelay);
    digitalWrite(LED7,HIGH);
    delay(onTimeDelay);
    digitalWrite(Buzz,LOW);
    delay(offTimeDelay);


    digitalWrite(Buzz, HIGH);
    digitalWrite(LED2,LOW);
    digitalWrite(LED3,LOW);
    delay(offTimeDelay);
    digitalWrite(LED4,LOW);
    digitalWrite(LED5,LOW);
    delay(offTimeDelay);
    digitalWrite(LED6,LOW);
    digitalWrite(LED7,LOW);
    delay(offTimeDelay);
    digitalWrite(Buzz,LOW);
    delay(offTimeDelay);

    digitalWrite(Buzz, HIGH);
    digitalWrite(LED2,HIGH);
    digitalWrite(LED3,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED4,HIGH);
    digitalWrite(LED5,HIGH);
    delay(onTimeDelay);
    digitalWrite(LED6,HIGH);
    digitalWrite(LED7,HIGH);
    delay(onTimeDelay);
    digitalWrite(Buzz,LOW);
    delay(onTimeDelay);


     
  }
  else
  {
    digitalWrite(Buzz, LOW);
  }
  

  if ( distance <= 14 )
  {
    digitalWrite(LED2, HIGH);
  }
  else
  {
    digitalWrite(LED2, LOW);
  }

  
  if ( distance <= 21 )
  {
    digitalWrite(LED3, HIGH);
  }
  else
  {
    digitalWrite(LED3, LOW);
  }



  if ( distance <= 28 )
  {
    digitalWrite(LED4, HIGH);
  }
  else
  {
    digitalWrite(LED4, LOW);

  }

  
  if ( distance <= 35 )
  {
    digitalWrite(LED5, HIGH);
  }
  else
  {
    digitalWrite(LED5, LOW);
  }

  
  if ( distance <= 42 )
  {
    digitalWrite(LED6, HIGH);
  }
  else
  {
    digitalWrite(LED6, LOW);
  }

  
  if ( distance <= 49 )
  {
    digitalWrite(LED7, HIGH); 
  }
  else
  {
     digitalWrite(LED7, LOW);
  }
}
