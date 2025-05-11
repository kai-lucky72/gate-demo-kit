🚦 Smart Ultrasonic Gate System with Servo, LEDs, and Buzzer
Overview
This Arduino project implements a smart gate system using an ultrasonic sensor, servo motor, LED indicators, and a buzzer. The gate automatically opens when an object (e.g., a person or vehicle) is detected within a certain distance and closes after a specified time. Audio and visual feedback are provided during gate operation.

🧰 Hardware Components
Arduino UNO (or compatible board)

Ultrasonic Sensor (HC-SR04)

Servo Motor (e.g., SG90)

Red LED (Gate Closed Indicator)

Blue LED (Gate Open Indicator)

Piezo Buzzer

Jumper Wires

Breadboard or PCB

Resistors (for LEDs, typically 220Ω)

🔌 Pin Configuration
Component	Arduino Pin
Ultrasonic Trigger	D2
Ultrasonic Echo	D3
Red LED (Closed)	D4
Blue LED (Open)	D5
Servo Motor	D6 (PWM)
Ground (Extra)	D7, D8
Piezo Buzzer	D12

Note: Pins D7 and D8 are used as software-configured GND lines. They are set LOW to serve as grounding points in the absence of physical GND rails.

🔄 System Behavior
Idle State (Default):

Gate is closed (Servo at 0°).

Red LED is ON.

Blue LED and buzzer are OFF.

Object Detection (within 15 cm):

Gate opens (Servo to 80°).

Red LED turns OFF; Blue LED turns ON.

Buzzer beeps repeatedly in timed intervals (tick-tock sound pattern).

After 5 Seconds:

Gate closes automatically.

LEDs return to default (Red ON, Blue OFF).

Buzzer turns OFF.

📏 Distance Measurement
The system uses the HC-SR04 ultrasonic sensor to calculate the distance between the sensor and the approaching object:


distance = duration * 0.034 / 2;
Where duration is the pulse travel time, and 0.034 cm/µs is the speed of sound in air.

🛠️ Setup & Usage
Upload the code to your Arduino using the Arduino IDE.

Connect components according to the pin configuration above.

Power the system via USB or external 5V source.

Observe the gate behavior based on object detection.

📎 Additional Notes
Adjust Distance Threshold: You can change if (distance < 15) to a different value depending on the desired trigger range.

Servo Angle: Modify gateServo.write(80) if your servo requires a different angle to open fully.

Buzzer Pattern: Timing can be tweaked in the buzzerInterval, delay(800), and delay(400) values.

📚 Serial Monitor Output
For debugging or monitoring purposes, the serial output displays the real-time distance measured:


Distance: 12 cm
Distance: 17 cm
...
📦 Future Improvements (Optional)
Add an LCD/OLED display to show gate status.

Implement RFID or keypad-based override.

Log events with a timestamp to an SD card.
