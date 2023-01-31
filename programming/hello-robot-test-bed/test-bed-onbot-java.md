# Test Bed - OnBot Java

OnBot Java is a text-based programming tool that lets programmers use a web browser to create, edit and save their Java op modes. In this section users can learn how to create an op mode, as wells as the basics of programming the actuators and sensors featured on the test bed.&#x20;

Follow the guide in order to get an in depth understanding of working with OnBot Java or navigate to the section that fits your needs:

| Section                                                                  | Goals of Section                                                                                                                                           |
| ------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Creating an Op Mode](test-bed-onbot-java.md#creating-an-op-mode)        | Focuses on how to navigate the OnBot Java interface and create an op mode.                                                                                 |
| [Programming Essentials ](test-bed-onbot-java.md#programming-essentials) | Breaks down the structure and key elelments needed for an op mode, as well as some of the essential components of Java.                                    |
| [Programming Actuators ](test-bed-onbot-java.md#programming-actuators)   | How to code servos and motors. This section walks through the basic logic of coding actuators, controlling actuators with a gamepad, and using telemetry.  |
| [Programming Sensors ](test-bed-onbot-java.md#programming-sensors)       | How to code a digital device. The section focuses on the basic logic of coding a digital device, like a REV Touch Sensor.                                  |

## Creating an Op Mode&#x20;

Before diving in and creating your first op mode, you should consider the concept of [**naming conventions**](https://en.wikipedia.org/wiki/Naming\_convention\_\(programming\)). When writing code the goal is to be as clear as possible about what is happening within the code. This is where the concept of naming conventions comes into play. Common naming conventions have been established by the programming world to denote variables, classes, functions, etc. Op modes share some similarities to [**classes**](https://en.wikipedia.org/wiki/Class\_\(computer\_programming\))**.** Thus the naming convention for op modes tends to follow that naming convention for classes; where the first letter of every word is capitalized.&#x20;

{% hint style="info" %}
This section assumes that you have already accessed the OnBot Java platform during the [Hello Robot - Introduction to Programming](../hello-robot-introduction-to-programming.md#accessing-onbot-java). If you are unsure how to access OnBot Java please revisit this section before proceeding.&#x20;
{% endhint %}

To start, access the Robot Controller Console and go to the OnBot Java page. There are a few key things to take note of on the main Onbot Java page.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MO1sU9pAYKqKYP4W09g%2F-MO3EovLwi7VQLDCRl2t%2Fonbot%20-%20main%20screen.svg?alt=media\&token=58e61a2c-291c-42f8-a0d3-95e7dedb29c5)

1. **Create New Op Mode** - The plus sign button opens up a window to create a new op more.
2. **Project Browser Pane** - This pane shows all the java project files on the Robot Controller.&#x20;
3. **Source Code Editing Pane** - This pane is the main code editing area.
4. **Message Pane** - This pane provides messages on the success or failure of code builds.
5. **Build Everything** - Builds all of the .java files on a Robot Controller.&#x20;

{% hint style="info" %}
When an op mode is created or edited the OnBot Java editor will auto-save the .java file to the file of system of the Robot Controller. However, in order to execute the code on the Robot Controller the .java text file needs to be converted to a binary that can be loaded dynamically onto the FTC Robot Controller app. This conversion is done by building the op modes.&#x20;
{% endhint %}

Select the _**Create New Op Mode**_ button. This will open the _**New File**_** ** window. This window allows users to choose settings like: naming their op modes, selecting a sample code to build off of, or choosing op mode type.

For this guide select the following sections:

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MO1sU9pAYKqKYP4W09g%2F-MO78GrErEg-pO9RgUJ3%2Fonbot%20-%20create%20new%20op%20mode.svg?alt=media\&token=80537f16-9138-4e6b-aa77-6dc8842291a8)

* File Name: HelloRobot\_TeleOp
* Sample: BlankLinearOpMode
* Op Mode Type: TeleOp
* Setup for Configured Hardware: on

Once the proper settings have been choose, select "OK" to create the op mode. The new file will populate the Project Browser Pane.

## Programming Essentials

During the process of creating an op mode the Onbot Java tool had several options to choose from. Those options define what information is already included in the op mode, which can simplify what a programmer has to do on their end. For instance, an option was given to select a sample. In OnBot Java these samples act as templates; providing statements, logical structure, and syntax for different robotics use cases.&#x20;

In the previous section the following settings were selected: the _Setup Code for Configured Hardware_ option, the _TeleOp_ option, and a sample code called **BlankLinearOpMode.** These options combined setup the shell of code needed to have a functional op mode.&#x20;

An op mode is considered a set of instructions for a robot to follow in order to understand the world around it. Even though the SDK provides readily available op mode structures, understanding what concepts the template is utilizing, and why, helps increase programming knowledge. Follow through this section to learn more about the op mode template and the programming concepts that make up its structure.  &#x20;

```java
package org.firstinspires.ftc.teamcode;

import com.qualcomm.robotcore.eventloop.opmode.LinearOpMode;
import com.qualcomm.robotcore.hardware.Blinker;
import com.qualcomm.robotcore.hardware.Gyroscope;
import com.qualcomm.robotcore.hardware.ColorSensor;
import com.qualcomm.robotcore.hardware.Servo;
import com.qualcomm.robotcore.hardware.DigitalChannel;
import com.qualcomm.robotcore.eventloop.opmode.TeleOp;
import com.qualcomm.robotcore.eventloop.opmode.Disabled;
import com.qualcomm.robotcore.hardware.DcMotor;
import com.qualcomm.robotcore.hardware.DcMotorSimple;
import com.qualcomm.robotcore.util.ElapsedTime;

@TeleOp

public class HelloWorld_TeleOp extends LinearOpMode {
    private Gyroscope imu;
    private ColorSensor test_color;
    private DcMotor test_motor;
    private Servo test_servo;
    private DigitalChannel test_touch;


    @Override
    public void runOpMode() {
        imu = hardwareMap.get(Gyroscope.class, "imu");
        test_color = hardwareMap.get(ColorSensor.class, "test_color");
        test_motor = hardwareMap.get(DcMotor.class, "test_motor");
        test_servo = hardwareMap.get(Servo.class, "test_servo");
        test_touch = hardwareMap.get(DigitalChannel.class, "test_touch");

        telemetry.addData("Status", "Initialized");
        telemetry.update();
        // Wait for the game to start (driver presses PLAY)
        waitForStart();

        // run until the end of the match (driver presses STOP)
        while (opModeIsActive()) {
            telemetry.addData("Status", "Running");
            telemetry.update();

        }
    }

```

{% hint style="warning" %}
The code block provides the structure of the template op mode based on the Hello Robot Configuration and with some comments missing. If another configuration is being used the code will be slightly different but many of the underlying concepts are the same.&#x20;
{% endhint %}

### Programming Concepts&#x20;

At the start of the op mode there is an [**annotation**](https://en.wikipedia.org/wiki/Java\_annotation) that occurs before the class definition. This annotation states that this is a tele-operated (i.e., driver controlled) op mode:

```java
@TeleOp
```

In Java annotations are metadata, or descriptive information about the code. In this case the annotation is being used to tell the system that this op mode is tele-operated. Changing the annotation from `@TeleOp` to `@Autonomous` will change the code to an autonomous op mode.&#x20;

```java
public class HelloWorld_TeleOp extends LinearOpMode {
```

You can also see that the OnBot Java editor created five **** [**private member** ](https://en.wikipedia.org/wiki/Class\_\(computer\_programming\)#Member\_accessibility)**variables** for this op mode. These variables will hold references to the five configured devices that the OnBot Java editor detected in the active configuration.

```
    private Gyroscope imu;
    private ColorSensor test_color;
    private DcMotor test_motor;
    private Servo test_servo;
    private DigitalChannel test_touch;
```

Next, there is an **overridden method** called `runOpMode`. Every op mode of type `LinearOpMode` must implement this method. This method gets called when a user selects and runs the op mode.

```
    @Override
    public void runOpMode() {
```

Hardware mapping was introduced in the configuration section, as a two part process. The first part of the process was creating a configuration file. The second part of the process is retrieving references to hardware devices from the `hardwareMap` **** [**object**](https://en.wikipedia.org/wiki/Object\_\(computer\_science\)).&#x20;

{% hint style="info" %}
&#x20;The`hardwareMap` object is available to use in the `runOpMode` method. It is an object of type `hardwareMap` class.
{% endhint %}

At the start of the `runOpMode` method, the op mode uses the `hardwareMap` object to get references to the hardware devices that are listed in the Robot Controller’s configuration file:

```
        imu = hardwareMap.get(Gyroscope.class, "imu");
        test_color = hardwareMap.get(ColorSensor.class, "test_color");
        test_motor = hardwareMap.get(DcMotor.class, "test_motor");
        test_servo = hardwareMap.get(Servo.class, "test_servo");
        test_touch = hardwareMap.get(DigitalChannel.class, "test_touch");

```

The `hardwareMap.get()` **method call** is used to retrieve the hardware devices and assign them to variables. The method call accepts two **arguments**: a reference to the particular class of hardware devices the device belongs to and the name of the hardware device in the configuration file. The name in the `hardwareMap.get()` needs to match the name of the device in the configuration file. If the names do not match, the op mode will throw a runtime error indicating that it can not find the device.&#x20;

{% hint style="info" %}
For more information on the runtime error check out the [Common Errors in Hardware Mapping ](../hello-robot-configuration.md#common-errors-in-hardware-mapping)section.&#x20;
{% endhint %}

In the next few statements of the example, the op mode prompts the user to push the start button to continue. It uses another object that is available in the `runOpMode` method. This object is called **telemetry** and the op mode uses the `addData` method to add a message to be sent to the Driver Station. The op mode then calls the update method to send the message to the Driver Station. Then it calls the `waitForStart` method, to wait until the user pushes the start button on the driver station to begin the op mode run.

{% hint style="info" %}
**Telemetry** is the process of collecting and transmitting data.  In Robotics telemetry is often used to output internal data from actuators and sensors to the Driver Station. This data can then be analyzed by users to make decisions that can improve code.&#x20;
{% endhint %}

```
        telemetry.addData("Status", "Initialized");
        telemetry.update();
        // Wait for the game to start (driver presses PLAY)
        waitForStart();
```

{% hint style="info" %}
&#x20;All linear op modes should have a `waitForStart` statement to ensure that the robot will not begin executing the op mode until the driver pushes the start button.
{% endhint %}

After a start command has been received, the op mode enters a **while loop** and keeps iterating in this loop until the op mode is no longer active (i.e., until the user pushes the stop button on the Driver Station):

```
        // run until the end of the match (driver presses STOP)
        while (opModeIsActive()) {
            telemetry.addData("Status", "Running");
            telemetry.update();

        }
```

As the op mode iterates in the while loop, it will continue to send telemetry messages with the index of “Status” and the message of “Running” to be displayed on the Driver Station.&#x20;

#### Syntax

Programming languages, much like any language, have a set of guiding rules and principals that allow statements to be universally understood. Things like punctuation, word structure, and formatting all play a part in how a line of code is interpreted. In linguistics and computer science the rules that govern the structure of a sentence are known as [syntax](https://en.wikipedia.org/wiki/Java\_syntax).&#x20;

It is important to understand the syntax for Java, as syntax errors will be common and hard to track without a basic level of understanding.&#x20;

#### Object Oriented Programming&#x20;

This section dropped a lot of references to methods, object, and classes. These are all intermediate to advance programming topics often centered around the concept of object oriented programming. The purpose of the Hello Robot guide is to act as a introductory course to robotics programming rather than deep dive into programming concepts.&#x20;

However, keep object oriented programming in mind as your skills grow. For now the most important thing to know is that occasionally methods within the SDK libraries will need to be called in order to perform a certain task. For instance, the line __ `HelloRobot_TeleOp.opModeIsActive()` line calls the method `opModeIsActive`, which is the procedure in the SDK that is able to tell when the op mode has been activate by the driver station phone.&#x20;

Going forward many of the motor, servo, or sensor specific code will deal with calls to other methods or classes.&#x20;

{% hint style="info" %}
For more information on classes and methods in the SDK check out the [Java Doc](https://ftctechnh.github.io/ftc\_app/doc/javadoc/index.html).&#x20;
{% endhint %}

## Programming Actuators

### Servo Basics

The goal of this section is to cover some of the basics of programming a servo within OnBot Java. By the end of this section users should be able to control a servo with a gamepad, as well as understand some of the key programming needs of the servo.&#x20;

{% hint style="info" %}
This section is considering the Smart Robot Servo in its default mode. If your servo has been changed to function in continuous mode or with angular limits it will not behave the same using the code examples below. You can learn more about the[ Smart Robot Servo](https://docs.revrobotics.com/duo-build/actuators/servos/smart-robot-servo) or changing the Servo's mode via the [SRS Programmer](https://docs.revrobotics.com/duo-build/actuators/servos/srs-programmer) by clicking the hyperlinks.&#x20;
{% endhint %}

With a typical servo, you can specify a target position for the servo. The servo will turn its motor shaft to move to the target position, and then maintain that position, even if moderate forces are applied to try and disturb its position.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MBtA\_rAKndrhw3UEHOy%2F-MBtffLxjwr8kU4I5jjV%2Fimage.png?alt=media\&token=08c50111-d056-48fc-86ec-1bd85b1b7f57)

For both Blocks and OnBot Java, you can specify a target position that ranges from 0 to 1 for a servo. For a servo with a 270° range, if the input range was from 0 to 1 then a signal input of 0 would cause the servo to turn to point -135°. For a signal input of 1, the servo would turn to +135°. Inputs between the minimum and maximum have corresponding angles evenly distributed between the minimum and maximum servo angle. This is important to keep in mind as you learn how to code servos.&#x20;

#### Programming a Servo

Add the line `test_servo.setPosition(1);` __ to the op mode while loop.&#x20;

```java
        while (opModeIsActive()) {
            test_servo.setPosition(1);
            telemetry.addData("Status", "Running");
            telemetry.update();

        }
```

Select **Build Everything** to build the code.&#x20;

{% hint style="success" %}
Try running this op mode on the test bed two times and consider the following questions:

* Did the servo move during the first run?
* Did the servo move during the second run?

If the servo did not move switch the `test_servo.setPosition(1);`to `test_servo.setPosition(0);` __ and try again.&#x20;
{% endhint %}

The intent of the`test_servo.setPosition();`is to set the position of the servo. If the servo is already in the set position when a code is run, it will not change positions. Lets try adding the line `test_servo.setPosition(0);` __ to the code in the initialization section.

```java
public void runOpMode() {
        imu = hardwareMap.get(Gyroscope.class, "imu");
        test_color = hardwareMap.get(ColorSensor.class, "test_color");
        test_motor = hardwareMap.get(DcMotor.class, "test_motor");
        test_servo = hardwareMap.get(Servo.class, "test_servo");
        test_touch = hardwareMap.get(DigitalChannel.class, "test_touch");
        
        test_servo.setPosition(0);

        telemetry.addData("Status", "Initialized");
        telemetry.update();
        // Wait for the game to start (driver presses PLAY)
        waitForStart();

        // run until the end of the match (driver presses STOP)
        while (opModeIsActive()) {
            test_servo.setPosition(1);
            telemetry.addData("Status", "Running");
            telemetry.update();

        }
    }
}

```

{% hint style="success" %}
Try running this op mode on the test bed. Give some time between hitting init and hitting play and consider the following question:

* What is different from the previous run?
{% endhint %}

The `test_servo.setPosition(0);` that was added in the step above changes the servo position to 0 during the initialization phase, so when the op mode is run the servo will always move to position 1. For some applications starting the servo in a **known state**, like at position zero, is beneficial to the operation of a mechanism. Setting the servo to the known state in the initialization ensures it is in the correct position when the op mode runs.&#x20;

#### Programming a Servo with a Gamepad

The focus of this example is to assign certain servo positions to buttons on the gamepad. For this example the known state will stay at position 0, so that after initialization the servo will be a the -135 degree position of the servo range. The following list shows what buttons correspond with which servo position.&#x20;

| **Button** | Degree Position | Code Position |
| ---------- | --------------- | ------------- |
| Y          | -135            | 0             |
| X          | 0               | 0.5           |
| B          | 0               | 0.5           |
| A          | 135             | 1             |

The best way to switch the servo position will be to use a conditional __ `if/ else if`statement. An if statement considers whether a conditional statement is true or false. If the conditional statement is true a defined action (like the servo moving) is performed. If the conditional statement is false the action is not performed.&#x20;

An `if/else if` statement takes in multiple different conditional statements. If the first conditional statement is found to be false then the second conditional state is analyzed. To better understand this concept consider the following code:

```java
if (gamepad1.y){
    //move to -135 degrees
    test_servo.setPosition(0);
    
} else if (gamepad1.x || gamepad1.b) {
    //move to 0 degrees
    test_servo.setPosition(0.5);

} else if (gamepad1.a) {
    //move to 135 degrees 
    test_servo.setPosition(1);
    
}
```

There are three different paths in this `if/else if` statement. If the first conditional statement is true (the Y button is pressed) the servo moves to code position 0 and the other conditional statements are ignored. If the first condition is false (the Y button is not pressed) the second condition is analyzed. This behavior repeats until a condition is met or all conditions have been tested and found false.&#x20;

{% hint style="info" %}
**`||` ** is a logical operator in Java. This symbol is the Java equivalent of "or." Using this in a conditional statement says that either button x or button b can be pressed for this condition to be considered true.&#x20;
{% endhint %}

```java
public void runOpMode() {
        imu = hardwareMap.get(Gyroscope.class, "imu");
        test_color = hardwareMap.get(ColorSensor.class, "test_color");
        test_motor = hardwareMap.get(DcMotor.class, "test_motor");
        test_servo = hardwareMap.get(Servo.class, "test_servo");
        test_touch = hardwareMap.get(DigitalChannel.class, "test_touch");
        
        test_servo.setPosition(0);

        telemetry.addData("Status", "Initialized");
        telemetry.update();
        // Wait for the game to start (driver presses PLAY)
        waitForStart();

        // run until the end of the match (driver presses STOP)
        while (opModeIsActive()) {
            if (gamepad1.y){
                //move to -135 degrees
                test_servo.setPosition(0);
    
            } else if (gamepad1.x || gamepad1.b) {
                //move to 0 degrees
                test_servo.setPosition(0.5);

            } else if (gamepad1.a) {
                //move to 135 degrees 
                test_servo.setPosition(1);
                        }
                        
            telemetry.addData("Status", "Running");
            telemetry.update();

        }
    }
}
```

#### Servos and Telemetry&#x20;

Recall that **telemetry** is the process of collecting and transmitting data.  In Robotics telemetry is used to output internal data from actuators and sensors to the Driver Station. This data can then be analyzed by users to make decisions that can improve code.

The most useful telemetry from the servo is the the position of the servo along its 270 degree range. In order to get that information the following line needs to be used.&#x20;

```java
test_servo.getPosition();
```

In the[ programming essentials ](test-bed-onbot-java.md#programming-essentials)section the __ `telemetry.addData();` __ line was briefly discussed. This method call takes in a key and variable parameter and outputs the information to the Driver Station. The key is a string, or a line of text, that should define the variable. In this case the __ `telemetry.addData();`is being used to output the position of the servo as it is changed so the key can be "Servo Position" The parameter however will be the the `test_servo.getPosition();`method call.

```java
double motorPower = 0; 
while (opModeIsActive()) {
           if (gamepad1.y){
                //move to -135 degrees
                test_servo.setPosition(0);
    
            } else if (gamepad1.x || gamepad1.b) {
                //move to 0 degrees
                test_servo.setPosition(0.5);

            } else if (gamepad1.a) {
                //move to 135 degrees 
                test_servo.setPosition(1);
            
            telemetry.addData("Servo Position", test_servo.getPosition());
            telemetry.addData("Status", "Running");
            telemetry.update();

        }
```

### Motor Basics

{% hint style="warning" %}
Modify your op mode to add the motor related code. This can be done by clearing out your current code modifications or adding the motor related code to your current op mode.&#x20;
{% endhint %}

The goal of this section is to cover some of the basics of programming a motor within OnBot Java. By the end of this section users should be able to control a motor using a gamepad, as well as understand some of the basics of working with motor encoders.&#x20;

#### Driving Motors&#x20;

Add the line `test_motor.setPower(1);` to the op mode while loop.&#x20;

```java
        while (opModeIsActive()) {
            test_motor.setPower(1);
            
            telemetry.addData("Status", "Running");
            telemetry.update();

        }
```

Select **Build Everything** to build the code.&#x20;

{% hint style="success" %}
Try running this op mode on the test bed and consider the following questions:

* How fast is the motor running?&#x20;
* What happens if you change the power from **1** to **0.3**?
* What happens if you change the power to **-1**?
{% endhint %}

The level of power sent to the motor is dependent on the numerical number assigned to the motor. The change from 1 to 0.3 decreased the motors speed from 100% of duty cycle to 30% of duty cycle. Meanwhile, the change to -1 allowed the motor to rotate at 100% duty cycle in the opposite direction. So, power can be fluctuated to drive a motor _forward_ or _backwards_.&#x20;

However, the `test_motor.setPower(1);` line will run the motor in the assigned direction until something in the code stops the motor or causes a change in direction.&#x20;

#### Driving Motors with the Gamepad&#x20;

In the previous section you learned how to set the motor to run at a specific power level in a specific direction. However, in some applications, it may be necessary to control the motor with a gamepad, to easily change the direction or power level of a mechanism.&#x20;

For this section lets create a double variable `motorPower`. This variable will be created within the op mode but outside of the while loop.&#x20;

```java
public void runOpMode() {
        imu = hardwareMap.get(Gyroscope.class, "imu");
        test_color = hardwareMap.get(ColorSensor.class, "test_color");
        test_motor = hardwareMap.get(DcMotor.class, "test_motor");
        test_servo = hardwareMap.get(Servo.class, "test_servo");
        test_touch = hardwareMap.get(DigitalChannel.class, "test_touch");
        
        double motorPower = 0; 

        telemetry.addData("Status", "Initialized");
        telemetry.update();
        // Wait for the game to start (driver presses PLAY)
        waitForStart();
        // run until the end of the match (driver presses STOP)
        while (opModeIsActive()) {
            
            telemetry.addData("Status", "Running");
            telemetry.update();

        }
    }
}
```

A **double** is numerical data type that can store numbers with decimal points. Since the power, or duty cycle, of the motor runs on a scale between 1 to -1; the `motorPower` variable will need to be able to hold numerical data with decimal points.&#x20;

Consider the following lines of code:

```java
  motorPower = - this.gamepad1.left_stick_y;
  test_motor.setPower(motorPower);
```

The line `motorPower  = - this.gamepad1.left_stick_y;` takes an numerical input that corresponds with the position of the gamepad joystick as it moves along the y-axis and assigns it as the `motorPower` variable. The next line `test_motor.setPower(motorPower);` sets the motor power equal to the `motorPower` variable.

{% hint style="info" %}
Note that for the Logitech F310 gamepads, the Y value of a joystick ranges from -1, when a joystick is in its topmost position, to +1, when a joystick is in its bottommost position. In order to change the directional relationship between the motor and the joystick, so that the topmost position of the joystick correlates with the forward direction of the motor, a **negative symbol**, or negation operator needs to be used.&#x20;
{% endhint %}

```java
// run until the end of the match (driver presses STOP)
double motorPower = 0; 
while (opModeIsActive()) {
            motorPower = - this.gamepad1.left_stick_y;
            test_motor.setPower(motorPower);
            
            telemetry.addData("Status", "Running");
            telemetry.update();

        }
```

#### Motors and Telemetry&#x20;

Recall that **telemetry** is the process of collecting and transmitting data.  In Robotics telemetry is used to output internal data from actuators and sensors to the Driver Station. This data can then be analyzed by users to make decisions that can improve code.&#x20;

One of the most common forms of telemetry data from motors is the data pulled from the motor encoder. REV DC Motors, like the Core Hex Motor, are equipped with internal encoders that relays positional information in the form of counts. In order to get information from the encoders the following line needs to be used:&#x20;

```java
test_motor.getCurrentPosition();
```

In the[ programming essentials ](broken-reference)section the __ `telemetry.addData();`line was briefly discussed. This method call takes in a key and variable parameter and outputs the information to the Driver Station. The key is a string, or a line of text, that should define the variable. In this case the __ `telemetry.addData();`is being used to output the position of the motor in the form of encoder counts so the key can be "Encoder Value." The parameter however will be the the `test_motor.getCurrentPosition();` method call.&#x20;

```java
double motorPower = 0; 
while (opModeIsActive()) {
            motorPower = - this.gamepad1.left_stick_y;
            test_motor.setPower(motorPower);
            
            telemetry.addData("Encoder Value", test_motor.getCurrentPosition());
            telemetry.addData("Status", "Running");
            telemetry.update();

        }
```

{% hint style="info" %}
For more information on programming encoders check out the [Using Encoders](../using-encoders.md) page. For more information the counts per revolution metric and how to use it check out the[ Encoders ](../../sensors/encoders/)page.&#x20;
{% endhint %}

## Programming Sensors&#x20;

### Touch Sensor Basics

The goal of this section is to cover some of the basics of programming a digital device, or Touch Sensor, within Blocks.&#x20;

{% hint style="danger" %}
Before programming with a Touch Sensor or other digital device it is important to understand what a digital device is and what the common applications for digital devices are. Visit the [Digital Sensors ](../../sensors/digital.md)page for more info.&#x20;
{% endhint %}

#### Programming a Digital Device

{% hint style="warning" %}
Modify your op mode to add the digital device related code. This can be done by clearing out your current code modifications or adding the digital device code to your op mode.&#x20;
{% endhint %}

The information from digital devices comes in two states, also known as binary states. The most common way to utilize this information is to use a conditional statement like an `if/else` statement. The line `test_touch.getState();` collects the binary `FALSE/TRUE` state from the touch sensor and acts as the condition for the `if/else` statement.&#x20;

```java
if (test_touch.getState()){
    //Touch Sensor is not pressed 
} else {
    //Touch Sensor is pressed 
        }
```

The code above highlights the basics structure of the __ `if/else`_s_tatement for a digital device. The `FALSE/TRUE` state of a REV Touch Sensor corresponds with whether or not the button on the Touch Sensor is pressed. When the button is not pressed the state of the Touch Sensor is true. When the button is pressed the state of the Touch Sensor is false. This status is reflected by the comments in the code.&#x20;

The most basic way to use a digital device is to use telemetry to output information, like the status of the Touch Sensor button. To do this, lets create a **string** variable called __ `touchStatus`. This variable will be created within the op mode.&#x20;

{% hint style="info" %}
[String](https://en.wikipedia.org/wiki/String\_\(computer\_science\)#String\_datatypes) refers to data that consists of a sequence of characters. String datatypes are indicated in code by a set of quotation marks. For instance, "Hello Robot" is a string but Hello Robot is not.
{% endhint %}

```java
public void runOpMode() {
        imu = hardwareMap.get(Gyroscope.class, "imu");
        test_color = hardwareMap.get(ColorSensor.class, "test_color");
        test_motor = hardwareMap.get(DcMotor.class, "test_motor");
        test_servo = hardwareMap.get(Servo.class, "test_servo");
        test_touch = hardwareMap.get(DigitalChannel.class, "test_touch");
        
        String touchStatus = "";

```

The line `String touchStatus = "";` __ declares that the variable touchStatus is an empty string variable. Which means that `touchStatus` is currently holding a string with zero characters in it.&#x20;

Add the __ `if/else` statement to the while loop.&#x20;

```java
public void runOpMode() {
        imu = hardwareMap.get(Gyroscope.class, "imu");
        test_color = hardwareMap.get(ColorSensor.class, "test_color");
        test_motor = hardwareMap.get(DcMotor.class, "test_motor");
        test_servo = hardwareMap.get(Servo.class, "test_servo");
        test_touch = hardwareMap.get(DigitalChannel.class, "test_touch");
        
        String touchStatus = "";
        
        telemetry.addData("Status", "Initialized");
        telemetry.update();
        
        // Wait for the game to start (driver presses PLAY)
        waitForStart();
        
        // run until the end of the match (driver presses STOP)
        while (opModeIsActive()) {
        
            if (test_touch.getState()){
                //Touch Sensor is not pressed 
            } else {
                //Touch Sensor is pressed 
                        }
            telemetry.addData("Status", "Running");
            telemetry.update();

        }
    }
}
```

Right now the variable __ `touchStatus` is empty, but for this example it should change to reflect the status of the touch sensor. To do this `touchStatus` __ should be set to either `"Not Pressed"` or `"Pressed"`.

```java
 if (test_touch.getState()){
    //Touch Sensor is not pressed  
    touchStatus = "Not Pressed";
    
 } else {
    //Touch Sensor is pressed 
    touchStatus = "Pressed";
                        }
```

To display in the information assigned to `touchStatus`, telemetry needs to be used. In the[ programming essentials ](test-bed-onbot-java.md#programming-essentials)section the __ `telemetry.addData()` __ line was briefly discussed. This method call takes in a key and variable parameter and outputs the information to the Driver Station. The key is a string, or a line of text, that should define the variable. In this case the __ `telemetry.addData();` __ is being used to output changes in the __ `touchStatus` variable so `"Touch Status"` would be a good key. The parameter will be the`touchStatus` variable. Add this line above the __ `telemetry.update();`line in the while loop.

```java
telemetry.addData("Touch Sensor", touchStatus);
```

#### Digital Devices as Limit Switches&#x20;

One of the most common uses for a digital device like a touch sensor is to use it as a [limit switch](../../sensors/digital.md#applications). The intent of a limit switch is to stop a mechanism, like an arm or lift, before it exceeds its physical limitations. In this application power needs to be cut from the motor when the limit is met.&#x20;

Programming a limit switch requires the same _if/else_ logic applied in the previous section. If the touch sensor state is true (it is not pressed) the motor will have power. Else (it is pressed) the motor will not have power.

```java
 if (test_touch.getState()){
    //Touch Sensor is not pressed  
     test_motor.setPower(0.3);
    
} else {
    //Touch Sensor is pressed 
    test_motor.setPower(0);
                        }
```

The code block above introduces the basics of a limit switch. Like with most sensors, its good to have telemetry that updates the Driver Station on the status of the sensor. Consider the following code:

```java
public void runOpMode() {
        imu = hardwareMap.get(Gyroscope.class, "imu");
        test_color = hardwareMap.get(ColorSensor.class, "test_color");
        test_motor = hardwareMap.get(DcMotor.class, "test_motor");
        test_servo = hardwareMap.get(Servo.class, "test_servo");
        test_touch = hardwareMap.get(DigitalChannel.class, "test_touch");
        
        String touchStatus = "";
        
        telemetry.addData("Status", "Initialized");
        telemetry.update();
        
        // Wait for the game to start (driver presses PLAY)
        waitForStart();
        
        // run until the end of the match (driver presses STOP)
        while (opModeIsActive()) {
        
         if (test_touch.getState()){
            //Touch Sensor is not pressed  
           test_motor.setPower(0.3);
           touchStatus = "Not Pressed";
    
          } else {
            //Touch Sensor is pressed 
            test_motor.setPower(0);
            touchStatus = "Pressed";
                        }
                        
            telemetry.addData("Touch Sensor:", touchStatus);
            telemetry.addData("Status", "Running");
            telemetry.update();

        }
    }
}
```
