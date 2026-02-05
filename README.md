# AIRMOUSE-PROJECT
This project implements an Air Mouse using an MPU6050 sensor and a microcontroller to control the computer cursor through hand movements. The system detects tilt and motion and converts them into real-time cursor movement and click actions, providing a portable and low-cost alternative to a traditional mouse.

    #include <Wire.h>
    #include <Adafruit_MPU6050.h>
    #include <Adafruit_Sensor.h>
    #include <BleMouse.h>

    #define LEFTBUTTON 19
    #define RIGHTBUTTON 18
    #define SPEED 10   // Pointer speed multiplier

    Adafruit_MPU6050 mpu;
    BleMouse bleMouse;

    void setup() {
    Serial.begin(115200);

    pinMode(LEFTBUTTON, INPUT_PULLUP);
    pinMode(RIGHTBUTTON, INPUT_PULLUP);

    if (!mpu.begin()) {
    Serial.println("Failed to find MPU6050 chip!");
    while (1) { delay(10); }
    }
     Serial.println("MPU6050 Found!");

    mpu.setAccelerometerRange(MPU6050_RANGE_2_G);
    mpu.setGyroRange(MPU6050_RANGE_250_DEG);
    mpu.setFilterBandwidth(MPU6050_BAND_5_HZ);

    bleMouse.begin();

    delay(2000); // Wait for BLE to connect
    }

     void loop() {
    if (bleMouse.isConnected()) {
    sensors_event_t a, g, temp;
    mpu.getEvent(&a, &g, &temp);

    // Use gyroscope data for movement
    int dx = (int)(g.gyro.y * SPEED); // Rotate wrist left/right → X movement
    int dy = (int)(-g.gyro.x * SPEED); // Rotate wrist up/down → Y movement

     bleMouse.move(dx, dy);

    // Left click
    if (digitalRead(LEFTBUTTON) == LOW) {
      if (!bleMouse.isPressed(MOUSE_LEFT)) {
        bleMouse.press(MOUSE_LEFT);
      }
    } else {
      if (bleMouse.isPressed(MOUSE_LEFT)) {
        bleMouse.release(MOUSE_LEFT);
      }
    }

    // Right click
    if (digitalRead(RIGHTBUTTON) == LOW) {
      if (!bleMouse.isPressed(MOUSE_RIGHT)) {
        bleMouse.press(MOUSE_RIGHT);
      }
    } else {
      if (bleMouse.isPressed(MOUSE_RIGHT)) {
        bleMouse.release(MOUSE_RIGHT);
      }
    }
    }
    }
