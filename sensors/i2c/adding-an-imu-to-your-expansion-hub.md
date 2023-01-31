# Adding an IMU to your Expansion Hub

{% hint style="info" %}
**If your Expansion Hub was purchased **_**BEFORE**_** December 2021, it already has an internal IMU installed and you do not need to follow these steps.**&#x20;
{% endhint %}

## **Compatible External IMUs**

There are a few options that will work for giving your Expansion Hub Gyro/IMU function.

1. Intergrating Gyro with our Logic Level Converter ans Sensor Cable Adapter - This is directly supported in the FTC Programing environment but is just a single-axis gyro, not a full IMU.

{% hint style="info" %}
**If your Expansion Hub was purchased **_**BEFORE**_** December 2021, it already has an internal IMU installed and you do not need to follow these steps.**&#x20;
{% endhint %}

## **Compatible External IMUs**

There are a few options that will work for giving your Expansion Hub Gyro/IMU function.

1. [Integrating Gyro](https://modernroboticsinc.com/product/integrating-gyro/) with our [Logic Level Converter](https://www.revrobotics.com/rev-31-1389/) and [Sensor Cable Adapter](https://www.revrobotics.com/rev-31-1384/) - This is directly supported in the FTC Programing environment but is just a single-axis gyro, not a full IMU.
2. [navX2 Sensor Bundle](https://www.andymark.com/products/navx2-micro-navigation-sensor-bundle) - Also supported in the FTC programming environment. Code examples are listed on AndyMark's page, and this product includes the correct cables to use within FTC. &#x20;
3. [Adafruit 9-DOF Absolute Orientation IMU](https://www.adafruit.com/product/4646) - This is the same IMU as in the Control Hub, but will require you to either create an adapter cable or solder a cut [sensor cable](https://www.revrobotics.com/jst-ph-4-pin-sensor-cable-4-pack/) to the board. Plugging this in and configuring the IMU on I2C port zero will allow you to use and program the same as an internal IMU.
