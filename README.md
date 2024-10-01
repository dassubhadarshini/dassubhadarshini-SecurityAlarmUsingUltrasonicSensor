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

## Circuit Diagram

![Ultrasonic Security Alarm Circuit](https://example.com/path/to/circuit-diagram.png) *(Replace this link with an actual image link)*

## Code

```cpp
// Define pins for ultrasonic sensor
const int trigPin = 9;
const int echoPin = 10;
const int buzzerPin = 11; // Pin for the buzzer

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(buzzerPin, OUTPUT);
  Serial.begin(9600); // Start the serial communication
}

void loop() {
  // Send ultrasonic pulse
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  // Measure the pulse width of echoPin
  long duration = pulseIn(echoPin, HIGH);
  
  // Calculate the distance
  int distance = duration * 0.034 / 2; // Distance in cm

  if (distance < 20) { // Trigger the alarm if object is closer than 20 cm
    digitalWrite(buzzerPin, HIGH);
  } else {
    digitalWrite(buzzerPin, LOW);
  }

  // Print distance to the Serial Monitor
  Serial.print("Distance: ");
  Serial.println(distance);

  delay(100); // Small delay to avoid overwhelming the sensor
}
