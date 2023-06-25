# mearm_esp32_cam
 esp32 cam for mearm
In this project, I connect an esp32-cam to a mearm robotic arm, so I can control the arm from a web interface. I use I2C to connect the esp32-cam to a pca9685 PWM driver, and use the driver to control the robot arm. I also add an OLED screen to the I2C bus.

__video link__ <br>
https://youtu.be/ukeri1_q-RQ

__Equipment__
1. MEARM robot kit: https://shop.mearm.com/
2. ESP32-CAM AI thinker: Available on amazon or similar.
3. PCA9685 servo driver: Available on amazon or aliexpress.
4. OLED 0.96": Available on amazon or aliexpress or similar.
5. FTDI to flash esp32 cam: https://www.amazon.com.au/gp/product/B00IJXZQ7C/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1


__Links__ <br>
Random Nerds esp32 rc car:
https://randomnerdtutorials.com/esp32-cam-car-robot-web-server/ <br>
Random Nerds I2C additional bus:
https://randomnerdtutorials.com/esp32-i2c-communication-arduino-ide/ <br>
Robojax PCA9685 tutorial:
http://robojax.com/learn/arduino/?vid=robojax_PCA9685-V2


__Adafruit PWM servo library update__ <br>
I have made the following change to the Adafruit_PWMServoDriver.h file <br>
From:
```c
Adafruit_PWMServoDriver(const uint8_t addr, TwoWire &i2c);
```
To:
```c
Adafruit_PWMServoDriver(const uint8_t addr, TwoWire *i2c);
```

And the  Adafruit_PWMServoDriver.cpp file <br>
From:
```c
Adafruit_PWMServoDriver::Adafruit_PWMServoDriver(const uint8_t addr,
                                                 TwoWire &i2c)
    : _i2caddr(addr), _i2c(&i2c) {}
```
To:
```c
Adafruit_PWMServoDriver::Adafruit_PWMServoDriver(const uint8_t addr,
                                                 TwoWire *i2c)
    : _i2caddr(addr), _i2c(i2c) {}
```

