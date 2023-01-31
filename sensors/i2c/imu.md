# IMU

## IMU Basics&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MACurZIeya0T0PmIrds%2F-MACxSFVQFnWa9fkbKDx%2Fimage.png?alt=media\&token=9f403e21-750c-4d75-a89f-bd85214ab8f8)

Each REV Robotics Control Hub ([REV-31-1595](https://www.revrobotics.com/rev-31-1595/)), and Expansion Hubs ([REV-31-1153](https://www.revrobotics.com/rev-31-1153/)) purchased before December 2021, **** has a built in IMU, or inertial measurement unit. The IMU combines measurements from multiple internal sensors to compute its current orientation. It can also provide the angular velocity (how fast the IMU is rotating along each axis).

{% hint style="info" %}
**Expansion Hubs shipped AFTER December 1st, 2021 no longer include an internal IMU**
{% endhint %}

The data used by the IMU to track the orientation includes the rotation along each axis, and the forces of acceleration along each axis. Using the acceleration forces allows the IMU to detect the direction of gravity, preventing drift in the pitch and roll readings. Only the heading will drift slowly, as small inaccuracies build up over time.

### Product Specifications&#x20;

* I2C Address: 0x28
* Port: 0&#x20;

## How to Use

Originally, Control Hubs and Expansion Hubs came with the Bosch BNO055 IMU. Control Hubs containing the alternative Bosch BHI260AP IMU started shipping in September 2022. To see which IMU your Control Hub has, go to the Manage page within the Program & Manage web interface, either from the Driver Station, the REV Hardware Client, or at `http://192.168.43.1:8080` in a web browser on a laptop connected to the Control Hub's Wi-Fi network.

When you create a new configuration file, the correct IMU type will be automatically detected, and added to the configuration.

Version 8.1 of the FTC Robot Controller app adds a new universal `IMU` interface for Blocks and Java programming, which supports both the BNO055 IMU and the BHI260AP IMU. The BNO055 IMU can also be used from the legacy `BNO055IMU` interface.

### The universal `IMU` interface

The new universal `IMU` interface added in version 8.1 of the FTC Robot Controller app provides robot-centric orientation and angular velocity values. You can specify the exact orientation of the Control or Expansion Hub on your robot, and the interface will convert the raw values from the IMU into robot-centric values. This simplifies how you use the IMU's values, and prevents problems when the hub is not mounted with the REV Robotics logo facing upwards.

All values from the`IMU` interface are in the Robot Coordinate System, in which the origin is inside your robot, the Z axis points towards the ceiling, the Y axis points straight ahead through the front of your robot (whatever you define the front to be), and the X axis points out the right side of your robot. This coordinate system is right-handed, which means that if you point a typical right thumb in the same direction as the axis, rotation in the same direction that the fingers curl is considered positive.

The `IMU.getRobotYawPItchRollAngles()`method on the `IMU` interface provides the robot's orientation in a simplified format of yaw, pitch, and roll angles. Most teams should use this method to get the robot's orientation.

* **Yaw** (also known as heading) is the measure of rotation along the robot's Z axis, or the side-to-side lateral rotation of the robot.
* **Pitch** is the measure of rotation along the robot's X axis, or the front-to-back rotation of the robot.
* **Roll** is the measure along the robot's Y axis, or the side-to-side tilt of the robot.

### The legacy `BNO055IMU` interface

The `BNO055IMU` interface has several disavantages compared to the universal `IMU` interface.

* It can only be used with Control Hubs and Expansion Hubs that contain the original BNO055 IMU.
* It only works reliably when the Hub is mounted flat, with the REV Robotics logo pointed upwards.
* The values it provides are relative to the Hub, not the Robot.
* You have to manually specify the axes order for the orientation angles (ZXY is recommended for typical use cases).

The coordinate system used for the `BNO055IMU` interface is defined like this:

* The X axis  runs from the bottom of the hub, near the servo ports, to the top of the hub, where the USB ports are.
* The Y axis runs from the sensor ports on the right to the motor ports on the left.&#x20;
* The Z axis points upwards through the REV Robotics logo.

### Applications&#x20;

There are a multitude of applications for the IMU within autonomous op modes:

* Use the heading to drive in straight lines and turn during autonomous
* Use the IMU with motor encoders to track and determine robot placement on a field&#x20;

{% hint style="info" %}
_To learn more on how to configure the IMU check out the_[ _I2C_ ](./)_introduction page._
{% endhint %}
