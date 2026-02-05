# AIRMOUSE-PROJECT
🖱️ Air Mouse Using MPU6050 and Arduino / ESP32
📌 Project Description

This project implements an Air Mouse system that allows the user to control the computer cursor using hand movements in the air. The system uses an MPU6050 (Accelerometer + Gyroscope) sensor to detect motion and orientation. The motion data is processed by a microcontroller (Arduino/ESP32) and sent to the computer, where it is converted into mouse cursor movements and click actions.

This project demonstrates the application of embedded systems, sensor interfacing, and human–computer interaction.



🎯 Objectives

To design a wireless/USB air mouse using motion sensors
To control mouse cursor using hand gestures
To implement left click, right click, and scroll functions
To reduce dependency on physical mouse devices
To understand IMU sensors and real-time data processing



🛠️ Components Used

Arduino / ESP32
MPU6050 (Accelerometer + Gyroscope)
Push buttons (for left/right click)
Connecting wires
Breadboard
USB cable / Bluetooth connection



⚙️ Software Used

Arduino IDE
C programing (for PC-side cursor control, if used)
Serial / Bluetooth communication library



🧠 Working Principle

The MPU6050 sensor measures the tilt and movement of the user’s hand using accelerometer and gyroscope data.
This data is read by the microcontroller and processed to calculate cursor movement in X and Y directions.
The processed data is then sent to the computer via USB serial or Bluetooth.
On the computer side, the received data is mapped to mouse cursor movements and click actions.
Thus, moving the hand in air moves the cursor on the screen, acting as an Air Mouse.



🔌 Block Diagram 

MPU6050 → Microcontroller (Arduino/ESP32) → PC (via USB/Bluetooth) → Cursor Control



🖥️ Features

Cursor movement using hand tilt
Left click and right click using buttons / gestures
Scroll using wrist rotation
Smooth and real-time response
Portable and low-cost design




🚀 How to Run the Project

Connect the MPU6050 to Arduino/ESP32
Upload the Arduino code using Arduino IDE
Connect the board to PC using USB / Bluetooth
Run the Python receiver program (if used)
Move your hand to control the cursor
Use buttons/gestures for clicking and scrolling



📊 Results

The cursor moves smoothly based on hand motion
Click and scroll functions work as expected
The system successfully replaces a traditional mouse for basic operations




🔮 Future Improvements

Add gesture recognition using Machine Learning
Improve accuracy using Kalman/Complementary filter
Add multi-gesture support (zoom, rotate, drag)
Make it fully wireless and compact
Develop a mobile app interface
