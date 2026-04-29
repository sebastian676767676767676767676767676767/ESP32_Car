# ESP32 IR Remote Controlled Car

This project uses an ESP32, an IR remote, a DC motor driver, and a servo motor to control a small vehicle.
You can move the car forward, reverse, steer left/right, and stop using an IR remote.

---

## Features

* IR remote control input
* Smooth motor speed control (PWM)
* Forward and reverse with acceleration ramp
* Servo-based steering
* Instant stop command
* Repeat signal handling for continuous input

---

## Hardware Requirements

* ESP32 board
* IR receiver module
* IR remote
* Servo motor (e.g., SG90)
* DC motor + motor driver (L298N or similar)
* Power supply (battery pack recommended)
* Jumper wires

---

## Pin Configuration

| Component     | ESP32 Pin |
| ------------- | --------- |
| IR Receiver   | 19        |
| Servo Signal  | 25        |
| Motor Input 1 | 13        |
| Motor Input 2 | 14        |
| Motor Enable  | 27        |

---

## Libraries Used

Make sure to install these libraries in Arduino IDE:

* IRremoteESP8266
* ESP32Servo

---

## Getting Started

1. Clone this repository:

   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   ```

2. Open the project in Arduino IDE

3. Install required libraries (via Library Manager)

4. Select your board:

   ```
   ESP32 Dev Module
   ```

5. Upload the code to your ESP32

6. Open Serial Monitor (115200 baud)

---

## Controls (IR Remote)

| Button | Action     |
| ------ | ---------- |
| Up     | Forward    |
| Down   | Reverse    |
| Left   | Turn Left  |
| Right  | Turn Right |
| OK     | Stop       |

Note: IR codes may vary depending on your remote.

---

## How It Works

### Motor Control

* Uses PWM (ledcWrite) for speed control
* Gradually increases speed for smoother acceleration
* Ensures minimum speed threshold to prevent stalling

### Steering

* Servo rotates between defined angles:

  * Left: 117
  * Center: 133
  * Right: 150

### IR Handling

* Decodes signals using IRrecv
* Supports repeat codes for holding buttons
* Prevents command flooding with timing control

---

## Customization

You can tweak these values in the code:

```cpp
const int minSpeed = 200;
const int maxLeft = 117;
const int maxRight = 150;
const int center = 133;

int turnStep = 1;
int speedStep = 1;
```

---

## Notes

* Servo is initialized before PWM motor setup to avoid timer conflicts
* If the servo fails to attach, check:

  * Power supply
  * Correct pin wiring
* Use external power for motors — do NOT power directly from ESP32

---

## Credits

Based on IR remote concepts from:
https://docs.sunfounder.com/projects/esp32-starter-kit/en/latest/arduino/basic_projects/ar_irremote.html

---

## License

This project is open-source. Feel free to use and modify it.

---
## Video
![](images/IMG_6779-ezgif.com-video-to-gif-converter.gif)
