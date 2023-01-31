# Elapsed Time - OnBot Java

## Introduction to Elapsed Time

One way to create an autonomous code is to use a timer to define which actions should occur when. Within the SDK actions can be set to a timer by using **ElapsedTime.**&#x20;

Timers consist of two main categories: count up and count down. In most applications a timer is considered to be a device that counts down from a specified time interval. For instance, the timer on a phone or a microwave. However, some timers, like stopwatches, count upwards from zero. These types of timers measure the amount of time that has elapsed.&#x20;

ElapsedTime is a count up timer. Registering the amount of time elapsed from the start of a set event, like the starting of a stopwatch. In this case, it is the amount of time elapsed from when the timer is instantiated or reset within the code.&#x20;

The ElapsedTime timer starts counting the amount of time elapsed from the point of its creation within a code. For instance, in this section ElapsedTime will be created (or instantiated) in the section of code that occurs when the op mode is initialized. There is no option to stop the ElapsedTime timer. Instead, the reset() function can be used within your code to reset the timer at various intervals.&#x20;

One the timer has been reset, the amount of time that has elapsed can be queried by calling methods like time(), seconds(), or milliseconds(). The time given by the queried methods can be used in loops to dictate how long a specific action should take place.&#x20;

{% hint style="info" %}
For more information on the ElapsedTime object check out the [Java Docs](https://ftctechnh.github.io/ftc\_app/doc/javadoc/index.html).&#x20;
{% endhint %}

| Sections                                                                                            | Goals of Section                                                       |
| --------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| [Basics of programming with Elapsed Time](elapsed-time-onbot-java.md#programming-with-elapsed-time) | Learning the logic needed to use elapsed time for autonomous control.  |

## Programming with Elapsed Time

Start by creating a new op mode called `HelloWorld_ElapsedTime` using the `BasicOpMode_Linear` sample. There are other feature you can select that may make things easier as you begin to develop your autonomous op modes. For instance, as you may recall, selecting **Setup Code for Configured Hardware** creates the necessary references to the hardware map. Another selection you can make is for the code to be setup as an autonomous op mode. This adds the `@Autonomous` annotation that distinguishes the code as an autonomous op mode in the Driver Station Application.

{% hint style="warning" %}
When creating an op mode a decision needs to be made on whether or not to set it to autonomous mode. For applications under 30 seconds, typically required for competitive game play changing the op mode type to autonomous is recommended. For applications over 30 seconds, setting the code to the autonomous op mode type will limit your autonomous code to 30 seconds of run time. If you plan on exceeding the 30 seconds built into the SDK, keeping the code as a teleoperated op mode type is recommended.&#x20;

For information on how op modes work please visit the [Introduction to Programming ](../../hello-robot-introduction-to-programming.md#op-modes)section.&#x20;
{% endhint %}

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MScjVyG-yFVd-BeDPcb%2F-MSi3AjZpUOOBUTDePq8%2FElapsed%20Time%20\_%20creating%20new%20op%20mode.svg?alt=media\&token=ce004662-8774-4e6e-ae77-797e72faa6b5)

Selecting the features discussed above will allow you to start with the following code.&#x20;

```java
package org.firstinspires.ftc.teamcode;

import com.qualcomm.robotcore.eventloop.opmode.LinearOpMode;
import com.qualcomm.robotcore.hardware.AnalogInput;
import com.qualcomm.robotcore.hardware.Gyroscope;
import com.qualcomm.robotcore.hardware.ColorSensor;
import com.qualcomm.robotcore.hardware.Servo;
import com.qualcomm.robotcore.hardware.DigitalChannel;
import com.qualcomm.robotcore.eventloop.opmode.Autonomous;
import com.qualcomm.robotcore.eventloop.opmode.TeleOp;
import com.qualcomm.robotcore.eventloop.opmode.Disabled;
import com.qualcomm.robotcore.hardware.DcMotor;
import com.qualcomm.robotcore.hardware.DcMotorSimple;


@Autonomous

public class HelloWorld_ElapsedTime extends LinearOpMode {
    private DcMotor leftMotor;
    private DcMotor rightMotor;
    private DcMotor arm;
    private Servo claw;
    private DigitalChannel touch;
    private Gyroscope imu; 

    @Override
    public void runOpMode() {
        imu = hardwareMap.get(Gyroscope.class, "imu");
        leftMotor = hardwareMap.get(DcMotor.class, "leftmotor");
        rightMotor = hardwareMap.get(DcMotor.class, "rightmotor");
        arm = hardwareMap.get(DcMotor.class, "arm");
        claw = hardwareMap.get(Servo.class, "claw");
        touch = hardwareMap.get(DigitalChannel.class, "touch");
        
        telemetry.addData("Status", "Initialized");
        telemetry.update();
        
        // Wait for the game to start (driver presses PLAY)
        waitForStart();

        // run until the end of the match (driver presses STOP)
        while (opModeIsActive()){
            telemetry.addData("Status", "Running");
            telemetry.update();
        }
    }
}

```

Since the focus of this section is Elapsed Time, a variable of `ElapsedTime`and an instance of `ElapsedTime` needs to be created. To do this the following line is needed

```java
private ElapsedTime     runtime = new ElapsedTime();
```

The above line performs two actions. A private `ElapsedTime` variable called `runtime` is created. Once `runtime` is created and defined as an `ElapsedTime` variable, it can hold the relevant time information and data. The other part of the line `runtime = new ElapsedTime();` creates an instance of the `ElapsedTime` timer object and assigns it to the runtime variable.&#x20;

Add this line to the op mode with the other private variables.&#x20;

```java
public class HelloWorld_ElapsedTime extends LinearOpMode {
    private DcMotor leftMotor;
    private DcMotor rightMotor;
    private DcMotor arm;
    private Servo claw;
    private DigitalChannel touch;
    private Gyroscope imu; 
    private ElapsedTime     runtime = new ElapsedTime();
```

The goal for this example is to have a series of actions performed on timed intervals, like driving forward for three seconds. Another way to think about it is that the robot drives forward while the `ElapsedTime` timer is less than or equal to three seconds or `runtime.seconds() <= 3.0`. For this particular example the best way to achieve this goal is to use a while loop. Replace the default op mode while loop with the following loop.

```java
       waitForStart();
       while (runtime.seconds() <= 3.0) {

        }
```

{% hint style="info" %}
It is important to know that, within a linear op mode, a while loop must always have the `opModeIsActive()` Boolean as a condition. This condition ensures that the while loop will terminate when the stop button is pressed.&#x20;
{% endhint %}

While loops run when the condition is true and stop when the condition is false. In this case, the while loop should only start if both conditions (`opModeIsActive()` and `runtime.seconds() <= 3.0`) are true. The while loop should terminate when the`runtime.seconds() > 3` is greater than three seconds or the stop button on the driver station is pressed. To accomplish this the logical operator `&&` needs to be used.

{% hint style="info" %}
`&&` **** is a logical operator in Java. This symbol is the Java equivalent of "and." Using this in a conditional statement requires that both statements need to be true in order for the overall condition to be true.&#x20;
{% endhint %}

```java
       waitForStart();
       while (opModeIsActive() && (runtime.seconds() <= 3.0)) {

        }
```

Recall that the `ElapsedTime` timer starts when it is instantiated or reset. Since the timer is being instantiated when the runtime variable is being created, and the variable creations are happening before the `waitForStart();` command is written; the timer will start when the op mode is initialized rather than when the op mode is started. This can cause issues on consistency in the robots performance, depending on the delay between initialization and start.&#x20;

{% hint style="success" %}
**Consider the following scenario:**

In a competition setting, teams are often required to initialize their robot prior to the start of a match. This means that a robot can sit in initialization anywhere from a few seconds to a few minutes. If an autonomous code is centered around using an `ElapsedTime` timer that begins upon instantiation, the longer a robot is sitting in initialization the less likely it is to run as expected.
{% endhint %}

In order to avoid issues from a time delay between initialization and start, a timer reset can be added to the code. Add the line `runtime.reset()`; between the `waitForStart();` command and the while loop.

```java
       waitForStart();
       runtime.reset();
       while (opModeIsActive() && (runtime.seconds() <= 3.0)) {

        }
```

Now the timer is reset , lets go ahead and add the motor related code. If you recall from [Programming Drivetrain Motors](./#programming-drivetrain-motors) article; the motors on the drivetrain mirror each other. The mirrored nature of the motor mounting causes the motors to rotate in opposing directions. In order to remedy this discrepancy the direction of the right motor needs to be reversed. Add the following lines of code to the op mode above the `waitForStart();` command.&#x20;

```java
rightMotor.setDirection(DcMotor.Direction.REVERSE);
```

Now, within the while loop add the lines`leftmotor.setPower(1);` and `rightmotor.setPower(1);` to set both motors to run at full speed in the forward direction.

```java
package org.firstinspires.ftc.teamcode;

import com.qualcomm.robotcore.eventloop.opmode.LinearOpMode;
import com.qualcomm.robotcore.hardware.AnalogInput;
import com.qualcomm.robotcore.hardware.Gyroscope;
import com.qualcomm.robotcore.hardware.ColorSensor;
import com.qualcomm.robotcore.hardware.Servo;
import com.qualcomm.robotcore.hardware.DigitalChannel;
import com.qualcomm.robotcore.eventloop.opmode.Autonomous;
import com.qualcomm.robotcore.eventloop.opmode.TeleOp;
import com.qualcomm.robotcore.eventloop.opmode.Disabled;
import com.qualcomm.robotcore.hardware.DcMotor;
import com.qualcomm.robotcore.hardware.DcMotorSimple;
import com.qualcomm.robotcore.util.ElapsedTime;


@Autonomous

public class HelloWorld_ElapsedTime extends LinearOpMode {
    private DcMotor leftMotor;
    private DcMotor rightMotor;
    private DcMotor arm;
    private Servo claw;
    private DigitalChannel touch;
    private Gyroscope imu; 
    private ElapsedTime     runtime = new ElapsedTime();

    @Override
    public void runOpMode() {
        imu = hardwareMap.get(Gyroscope.class, "imu");
        leftMotor = hardwareMap.get(DcMotor.class, "leftmotor");
        rightMotor = hardwareMap.get(DcMotor.class, "rightmotor");
        arm = hardwareMap.get(DcMotor.class, "arm");
        claw = hardwareMap.get(Servo.class, "claw");
        touch = hardwareMap.get(DigitalChannel.class, "touch");
        
        rightMotor.setDirection(DcMotor.Direction.REVERSE);
        
        telemetry.addData("Status", "Initialized");
        telemetry.update();
        // Wait for the game to start (driver presses PLAY)
        
        waitForStart();
        // run until the end of the match (driver presses STOP)
  
        runtime.reset();
        while (opModeIsActive() && (runtime.seconds() <= 3.0)) {
            leftMotor.setPower(1);
            rightMotor.setPower(1);
        }
```

You now have the basic code you need to have your robot drive forward for three seconds. This should give you a basic sense of coding with `ElapsedTime`. Other actions like opening and closing a claw, or lifting an arm can be coded into your autonomous program.&#x20;

As advised in previous sections, it is beneficial to add telemetry to certain code to get the feedback data you want or need. For this example, the telemetry will display how many seconds have elapsed for each leg of the robots journey.&#x20;

```java
while (opModeIsActive() && (runtime.seconds() <= 3.0)) {
    leftMotor.setPower(1);
    rightMotor.setPower(1);
    telemetry.addData("Leg 1", runtime.seconds());
    telemetry.update();
        }
```

For this particular guide, the end goal is to test the accuracy of a robot driving forward from point a to point b and then driving backwards back to point a. In order to do that another section of code based off the timer needs to be written. One way to do this is to to copy the while loop that you already made and make the necessary edits like switching the direction of power to the motors.&#x20;

```java
runtime.reset();
while (opModeIsActive() && (runtime.seconds() <= 3.0)) {
    leftMotor.setPower(1);
    rightMotor.setPower(1);
    telemetry.addData("Leg 1", runtime.seconds());
    telemetry.update();
        }

runtime.reset();
while (opModeIsActive() && (runtime.seconds() <= 3.0)) {
    leftMotor.setPower(-1);
    rightMotor.setPower(-1);
    telemetry.addData("Leg 2", runtime.seconds());
    telemetry.update();
        }
```

{% hint style="info" %}
Notice that an additional `runtime.reset();` was added to the code above. The other option for a second while loop would have involved adding an additional condition to the while loop. Such as:

`while(opModeIsActive() && (runtime.seconds() > 3.0)  && runtime.seconds() <=6.0)`&#x20;

The choice to reset the timer before starting a new leg of the robots journey was made to reduce the amount of code changes that may need to be made while testing the code.&#x20;
{% endhint %}

### Full Code Example

```java
package org.firstinspires.ftc.teamcode;

import com.qualcomm.robotcore.eventloop.opmode.LinearOpMode;
import com.qualcomm.robotcore.hardware.AnalogInput;
import com.qualcomm.robotcore.hardware.Gyroscope;
import com.qualcomm.robotcore.hardware.ColorSensor;
import com.qualcomm.robotcore.hardware.Servo;
import com.qualcomm.robotcore.hardware.DigitalChannel;
import com.qualcomm.robotcore.eventloop.opmode.Autonomous;
import com.qualcomm.robotcore.eventloop.opmode.TeleOp;
import com.qualcomm.robotcore.eventloop.opmode.Disabled;
import com.qualcomm.robotcore.hardware.DcMotor;
import com.qualcomm.robotcore.hardware.DcMotorSimple;
import com.qualcomm.robotcore.util.ElapsedTime;


@Autonomous

public class HelloWorld_ElapsedTime extends LinearOpMode {
    private DcMotor leftMotor;
    private DcMotor rightMotor;
    private DcMotor arm;
    private Servo claw;
    private DigitalChannel touch;
    private Gyroscope imu; 
    private ElapsedTime     runtime = new ElapsedTime();

    @Override
    public void runOpMode() {
        imu = hardwareMap.get(Gyroscope.class, "imu");
        leftMotor = hardwareMap.get(DcMotor.class, "leftmotor");
        rightMotor = hardwareMap.get(DcMotor.class, "rightmotor");
        arm = hardwareMap.get(DcMotor.class, "arm");
        claw = hardwareMap.get(Servo.class, "claw");
        touch = hardwareMap.get(DigitalChannel.class, "touch");
        leftMotor.setDirection(DcMotor.Direction.FORWARD); // Set to REVERSE if using AndyMark motors
        rightMotor.setDirection(DcMotor.Direction.REVERSE);
        
        telemetry.addData("Status", "Initialized");
        telemetry.update();
        // Wait for the game to start (driver presses PLAY)
        waitForStart();

        // run until the end of the match (driver presses STOP)
  
        runtime.reset();
        while (opModeIsActive() && (runtime.seconds() <= 3.0)) {
            leftMotor.setPower(1);
            rightMotor.setPower(1);
            telemetry.addData("Leg 1", runtime.seconds());
            telemetry.update();
        }

        runtime.reset();
        while (opModeIsActive() && (runtime.seconds() <= 3.0)) {
            leftMotor.setPower(-1);
            rightMotor.setPower(-1);
            telemetry.addData("Leg 2", runtime.seconds());
            telemetry.update();
        }

        }
    }
```
