# 🤖 4-Servo Motor Control — Arduino Uno Tinkercad

## 📋 Overview
This project programs an Arduino Uno to control 4 servo motors simultaneously. Each servo performs a sweep motion for a fixed duration, then holds at a neutral position.

## 🎯 Task
1. Run all 4 servos using sweep motion (0°→180°→0°) for **2 seconds**.
2. After 2 seconds, stop and hold all servos at **90°**.

## 🔧 Hardware
| Component     | Quantity |
|----------------|----------|
| Arduino Uno R3 | 1        |
| Servo motor    | 4        |

## 🔌 Wiring

| Servo | Signal (orange) | Power (red) | Ground (black) |
|-------|------------------|-------------|-----------------|
| 1     | Pin 9            | 5V          | GND             |
| 2     | Pin 10           | 5V          | GND             |
| 3     | Pin 11           | 5V          | GND             |
| 4     | Pin 12           | 5V          | GND             |

All 4 servos share the Arduino's **5V** and **GND** pins; each has its own dedicated signal pin.

## 💻 Code
```cpp
#include <Servo.h>

Servo servo1;
Servo servo2;
Servo servo3;
Servo servo4;

void setup() {
  servo1.attach(9);
  servo2.attach(10);
  servo3.attach(11);
  servo4.attach(12);

  unsigned long startTime = millis();

  // Sweep motion for 2 seconds
  while (millis() - startTime < 2000) {
    for (int pos = 0; pos <= 180; pos += 1) {
      servo1.write(pos);
      servo2.write(pos);
      servo3.write(pos);
      servo4.write(pos);
      delay(15);
    }
    for (int pos = 180; pos >= 0; pos -= 1) {
      servo1.write(pos);
      servo2.write(pos);
      servo3.write(pos);
      servo4.write(pos);
      delay(15);
    }
  }

  // Hold all servos at 90 degrees
  servo1.write(90);
  servo2.write(90);
  servo3.write(90);
  servo4.write(90);
}

void loop() {
  // Nothing to repeat — servos remain at 90°
}
```

## 🖼️ Circuit
![Circuit diagram](circuit.png)

## 🎬 Demo
A short simulation video demonstrating the sweep-then-hold behavior is included: [`demo.mp4`](demo.mp4)

## ▶️ How to Run (Tinkercad)
1. Open [Tinkercad Circuits](https://www.tinkercad.com/) → **Create** → **Circuits**.
2. Add an **Arduino Uno R3** and **4 servo motors**.
3. Wire each servo according to the table above.
4. Open the **Code** editor, switch to **Text** mode, and paste the code above.
5. Click **Start Simulation**.

## ✅ Expected Result
- ✅ All 4 servos sweep back and forth for 2 seconds.
- ✅ After 2 seconds, all servos stop and hold steady at 90°.

## 👤 Author
Prepared as part of a servo motor control exercise using Arduino and Tinkercad.
