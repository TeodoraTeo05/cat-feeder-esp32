# Cat Feeder ESP32

This project represents an automated cat feeding system built using an ESP32 board. The device allows dispensing food and water either through physical buttons or via a web interface accessible from any phone or laptop connected to the ESP32 network.

## Functionality

- The ESP32 creates its own Wi-Fi network named `CatFeeder_AP`.
- The user connects to this network and accesses the web control page via a browser (e.g., `http://192.168.4.1`).
- The web interface contains two buttons:
  - **Give Food** – activates the servo motor to open the food compartment.
  - **Give Water** – activates another servo motor to dispense water.
- In parallel, the system allows triggering the two functions via two physical buttons.
- Each action is confirmed by:
  - a message on the LCD (`Eat well, my kittens` or `Drink well, my kittens`)
  - a sound emitted by the buzzer.

## Hardware Components Used

- ESP32 Development Board
- 2 x SG90 Micro Servo
- 1602 LCD with I2C interface
- Passive buzzer
- 2 x Physical buttons (pushbuttons)
- Jumper wires and breadboard

## Libraries Used

- `WiFi.h` – for creating the local Wi-Fi network (Access Point)
- `WebServer.h` – for implementing the HTML web interface
- `ESP32Servo.h` – for precise control of the servo motors
- `LiquidCrystal_I2C.h` – for the LCD display with I2C interface

All libraries are compatible with the ESP32 platform and offer easy integration within the Arduino IDE.

## Operating Mode

1. On startup, the LCD displays the message "Cat Feeder Ready".
2. The ESP32 initializes the Wi-Fi network and the web server.
3. When an HTTP request is received (`/food` or `/water`) or a physical button is pressed:
   - The corresponding servo motor is activated.
   - The relevant message is displayed on the LCD.
   - The buzzer emits a short beep.

## Validation

The functionalities were tested individually and in combination:
- The web interface was verified on a phone and PC.
- The physical buttons were tested with `INPUT_PULLUP` and respond correctly.
- The servo motors move between the 0° and 90° positions with a 1s `delay`.
- The LCD messages and the audio signal are correctly synchronized.

## Demo video

https://youtu.be/CCG9btgEeA4
