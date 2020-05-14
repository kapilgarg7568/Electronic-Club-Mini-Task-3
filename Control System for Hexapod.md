# Control System for Hexapod
## Data from multiple IMU to microcontroller
**Problem**:Reading Multiple IMU on the same 12C Bus on Arduino Uno is not easy as all sensors (MPU-6050) have the same address of 0x68.This is important for Arduoino to select which of the conneccted I2C devices it want to talk to so we cant use more than one sensor at a time with I2C protocol.

 **Sensors**:
 - Here I am using **MPU-6050** sensor based on MEMS (micro electro mechanical systems) technology.
 - MPU6050 sensor module is complete 6-axis Motion Tracking Device. It combines 3-axis Gyroscope, 3-axis Accelerometer and Digital Motion Processor all in small package.
 - it has additional feature of on-chip Temperature sensor. 
 - It has I2C bus interface to communicate with the microcontrollers.
 - [ MPU-6050 Datasheet ](https://github.com/kapilgarg7568/Electronic-Club-Mini-Task-3/files/4626004/MPU-6000-Datasheet1.pdf)
 - ![Sensor image](https://user-images.githubusercontent.com/64272528/81891946-8031cf80-95c7-11ea-9e7e-08b2abaf57c5.jpeg)

 
 **Microcontroller**:
 - Here i have choosen **Arduino UNO board** as our microcontroller as it is easy to use and cheap.
 - It supports I2C protocol hence its is compatible with our MPU-6050 sensor.
 
 **I2C Protocol**:
 - I2C is a serial protocol for two-wire interface to connect low-speed devices like microcontrollers, EEPROMs, A/D and D/A converters, I/O interfaces and other similar peripherals in embedded systems.
 - The way I2C protocol works one thing it needs is that each of the conected I2C module shold have a unique address.
 - More information on [ I2C protocol ](https://en.m.wikipedia.org/wiki/I%C2%B2C)
 - ![I2C protocol](https://user-images.githubusercontent.com/64272528/81895580-37324900-95d0-11ea-9557-a0a5af38fb60.jpeg)


 


**Solution**:
- But its possible using ADO pin (on MPU-6050) and TCA9548A multiplexer breakout.
 - **TCA9548A multiplexer breakout**:
 - TCA9548A is an eight-channel (bidirectional) I2C multiplexer which allows eight separate I2C devices to be controlled by a single host I2C bus. You just need to wire up the I2C sensors to the SCn / SDn multiplexed buses.The Multiplexer connects to VIN, GND, SDA and SCL lines of the micro-controller.
 - It is capable of aquiring data from nultiple senors which hold the same address.
 - it comes with a reset pin so that if there is any bus conflict or improper operation it can be reset by asserting a low to reset pin. 
- The trick is if ADO of any MPU-6050 is made HIGH, its 12C address changes to 0x69. Now if you want many accelerometers working on the same channel, use the sesnsor address as 0x69 (this will only work when the relevant MPU-6050 ADO is HIGH). When this happens, all the other sensors are transmitting using 0x68 and arduino is not going to read them. Then the arduinocan only read that particular sensor whose ADO is made HIGH using a Pin of TCA9548A multiplexer.
- But we can send or recieve data to maximum 8 same address I2C devices and here we are using 19 IMU so we need 3 such TCA9548A multiplexer to set a proper communication between microcontroller and all 19 MPU-6050 sensors.
- [ TCA9548A Multiplexer Datasheet ](https://github.com/kapilgarg7568/Electronic-Club-Mini-Task-3/files/4626276/adafruit-tca9548a-1-to-8-i2c-multiplexer-breakout.pdf)
- [User Guide to TCA9548A Multiplexer ](https://github.com/kapilgarg7568/Electronic-Club-Mini-Task-3/files/4626279/TCA9548A-Q1.PDF)

- ![sensor](https://user-images.githubusercontent.com/64272528/81896778-eff98780-95d2-11ea-9e2c-5a4068bc3573.jpeg)


- Circuit of Two same address I2C devices connected with arduino through TCA9548A multiplexer
![arduino wiht](https://user-images.githubusercontent.com/64272528/81896785-f1c34b00-95d2-11ea-936d-50959ef4db75.jpeg)


