# Distance Measurement with HC-SR04 Ultrasonic Sensor

This Arduino script demonstrates how to use the HC-SR04 ultrasonic sensor to measure distance. The sensor's distance measurements are printed to the Serial Monitor in centimeters.

## Components Required

- Arduino board (e.g., Arduino Uno)
- HC-SR04 Ultrasonic Sensor
- Jumper wires

## Wiring

- **HC-SR04 Pinout**:
  - **Trig** to Arduino pin D7
  - **Echo** to Arduino pin D6
  - **VCC** to Arduino 5V
  - **GND** to Arduino GND

## Code

```cpp
#define echoPin D6
#define trigPin D7

long duration, distance;

void setup() {
  Serial.begin(115200);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
}

void loop() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(3);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(12);
  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH);
  distance = (duration / 2) / 29.1;
  Serial.print("Distance= ");
  Serial.print(distance);
  Serial.println("cm");
  delay(1000);
}
```

## Usage:

1. Connect the HC-SR04 sensor to the Arduino as per the wiring instructions.
2. Upload the code to your Arduino board.
3. Open the Serial Monitor (set to 115200 baud rate) to view the distance measurements.
