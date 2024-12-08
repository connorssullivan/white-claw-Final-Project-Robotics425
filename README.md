# Robot Arm Control System

This project is a robotic arm control system that allows for precise movement of multiple joints using servo motors. The arm can be controlled via Bluetooth commands, enabling remote operation through a serial interface. The system includes features for initializing the arm's positions, precise joint control, and custom behaviors like "waving hello."

## Features

- **Bluetooth Control**: The system uses an HC-05 Bluetooth module to receive input commands remotely.
- **Precise Joint Movement**: Each joint of the robotic arm can be moved in small increments for precise positioning.
- **Servo Initialization**: Automatically sets all servos to their default positions on startup or reset.
- **Custom Behaviors**: Includes a predefined "say hello" action where the arm waves up and down.
- **Collision Prevention**: Prevents out-of-bound movements by limiting the joint's range based on predefined positions.

## Components Used

- **Adafruit PWM Servo Driver**: For controlling up to 16 servo motors with precise PWM signals.
- **HC-05 Bluetooth Module**: To receive commands from a remote device via a serial interface.
- **Servo Motors**: Used to control each joint of the robotic arm.
- **Arduino Board**: The central microcontroller for processing input and controlling the arm.

## File Overview

### `RobotArmControl.ino`
This is the main code file that includes:
- Servo initialization and default positions.
- Joint movement functions.
- Command handling for Bluetooth input.
- Custom behaviors (e.g., waving hello).

### Key Functions

#### `initializeServos()`
Sets all servo motors to their default positions.

#### `moveJoint(int &currentPos, int step, int channel, const char *jointName)`
Moves a specific joint by a given step size, ensuring the movement stays within valid bounds.

#### `moveShoulder(int step)`
Specialized function to control the shoulder joints with synchronized movement.

#### `handleInput(char input)`
Parses Bluetooth commands and executes the appropriate joint movement or action.

#### `sayHello()`
Makes the robotic arm wave by moving the forearm up and down three times.

## Command List

Commands are sent via Bluetooth and interpreted by the `handleInput()` function:

| Command | Action                          |
|---------|---------------------------------|
| `0`     | Move shoulder down              |
| `1`     | Move shoulder up                |
| `2`     | Move elbow up                   |
| `3`     | Move elbow down                 |
| `4`     | Move forearm up                 |
| `5`     | Move forearm down               |
| `6`     | Move wrist up                   |
| `7`     | Move wrist down                 |
| `8`     | Open claw                       |
| `9`     | Close claw                      |
| `h`     | Make the arm wave ("say hello") |
| `s`     | Reset all servos to default positions |

## System Setup

1. **Hardware Connections**:
   - Connect the servo motors to the Adafruit PWM Servo Driver.
   - Connect the HC-05 Bluetooth module to the designated RX and TX pins on the Arduino.
   - Ensure the power supply matches the requirements of the servos and the Arduino board.

2. **Software Setup**:
   - Install the required libraries: `Wire.h`, `Adafruit_PWMServoDriver`, and `SoftwareSerial`.
   - Upload the code to the Arduino using the Arduino IDE.

3. **Testing**:
   - Open the serial monitor or connect a Bluetooth-enabled device to send commands.
   - Use the provided command list to test joint movements and custom actions.

## Future Improvements

- **Grip Strength**: Enhance the claw's grip to handle heavier objects.
- **Collision Detection**: Add sensors to prevent accidental collisions during movement.
- **Position Feedback**: Integrate encoders for real-time feedback on joint positions.

## License

This project is open-source and licensed under the MIT License.

---

Happy building!
