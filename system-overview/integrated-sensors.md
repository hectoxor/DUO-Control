# Integrated Sensors

The REV Robotics Control Hub ([REV-31-1595](https://www.revrobotics.com/rev-31-1595/)) **** and Expansion Hub ([REV-31-1153](https://www.revrobotics.com/rev-31-1153/)) integrate a number of feedback sensors. Some of these are user accessible in the latest FTC Android Studio SDK, but others are not yet directly user accessible. These sensors are in some cases also used by the Control Hub and Expansion Hub for internal safety monitoring.&#x20;

* Battery Voltage Monitoring \[**Accessible**]
* Integrated 9-axis IMU \[**Accessible**]
  * Bosch BNO055 9-axis absolute orientation sensor
  * Internally connected to I2C port 0 and configured to address 0x28
* Current Monitoring
  * Battery \[**Accessible**]
  * I2C Bus \[**Accessible**]
  * Digital Power Bus \[**Accessible**]
  * Servo Power Bus \[Not Accessible]
* Per Motor Channel Current Monitoring \[**Accessible**]
