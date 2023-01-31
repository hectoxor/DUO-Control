# Robot Navigation - OnBot Java

## Introduction to Robot Navigation

As alluded to in the Hello Robot - Robot Control section, robot control comes in many different forms. One of the control types to consider for robots with drivetrains, is robot navigation. &#x20;

Robot navigation as a concept is dependent on the type of drivetrain and the type of operation mode. For instance, the code to control a mecanum drivetrain differs from the code used to control a differential drivetrain. There is also a difference between coding for teleoperated driving, with a gamepad, or coding for autonomous, where each movement of the robot must be defined within code.&#x20;

The following section goes through some of the basics of programming for a differential drivetrain, as well as how to set up a teleoperated arcade style drivetrain code. The concepts and logic highlighted in this section will be applicable the autonomous control section Elapsed Time.&#x20;

| Sections                                                                  | Goals of Section                                                                                                                                                                                |
| ------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Basics of Programming Drivetrains](./#basics-of-programming-drivetrains) | What to consider when [programming drivetrain motors](./#programming-drivetrain-motors) and how to apply this to an [arcade style teleoperated control](./#teleoperated-driving-arcade-style).  |

## Basics of Programming Drivetrains

### Programming Drivetrain Motors

Start by creating a basic op mode called `DualDrive`.&#x20;

{% hint style="info" %}
Visit the [Test Bed - OnBot Java](../../hello-robot-test-bed/test-bed-onbot-java.md) section for more information on creating an op mode. The op mode below focuses on hardware mapping only the relevant drivetrain motors. &#x20;
{% endhint %}

```java
package org.firstinspires.ftc.teamcode;

import com.qualcomm.robotcore.eventloop.opmode.LinearOpMode;
import com.qualcomm.robotcore.eventloop.opmode.TeleOp;
import com.qualcomm.robotcore.hardware.DcMotor;
import com.qualcomm.robotcore.hardware.DcMotorSimple;

@TeleOp
public class DualDrive extends LinearOpMode {
  private DcMotor rightmotor;
  private DcMotor leftmotor;

  @Override
  public void runOpMode() {

        rightmotor = hardwareMap.get(DcMotor.class, "rightmotor");
        leftmotor = hardwareMap.get(DcMotor.class, "leftmotor");
        
        waitForStart();

        while (opModeIsActive()) {

        }
    }
}
```

Since the focus of this section is creating a functional drivetrain in code, lets started by adding `rightmotor.setPower(1);` and `leftmotor.setPower(1);` to the op more while loop.

```java
while (opModeIsActive()) {
        rightmotor.setPower(1);
        leftmotor.setPower(1);
        }
```

{% hint style="success" %}
Before moving on try running the code as is and consider the following questions:&#x20;

* What behavior is the robot exhibiting?&#x20;
* What direction is the robot spinning in?

When motors run at different speeds they spin along their center pivot point. But the motors are both set to a power (or duty cycle) of 1?
{% endhint %}

DC Motors are capable of spinning in two different directions depending on the current flow: clockwise and counter clockwise. When using a positive power value the Control Hub sends current to the motor for it to spin in a clockwise direction.

With the Class Bot and current code, both motors are currently set to run in the clockwise direction. If you set the robot on blocks and run the code again though, you can see that the motors run in opposing directions. With the mirrored way the motors mount to the drivetrain, one motor is naturally the inverse of the other.&#x20;

Why would the inverse motor cause the robot to spin in a circle? Both speed and direction of rotation of the **wheels** impact the overall direction the robot moves in. In this case, both **motors** were assigned to have the same power and direction but how the motors transfer motion to the **wheels**, causes the robot to spin instead of moving forward.&#x20;

{% hint style="info" %}
Check the [Introduction to Motion](https://docs.revrobotics.com/duo-build/actuators/introduction-to-motion) section for more information on the mechanics of transferring motion and power.
{% endhint %}

In the info block above you were asked to determine which direction the robot spun in. The robot pivots in the direction of the inversed motor. For instance, when the right motor is the inversed motor the robot will pivot to the right. If the left motor is the inversed motor the robot will pivot to the left.&#x20;

#### The Affect of Drivetrain Motors on Drivetrain Movement

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MVrZYOdMO43YdZ0zxXy%2F-MVrsHYT6qr4y1KLl-RD%2FDrivetrains-%20motors%20relation%20to%20turning.svg?alt=media\&token=bdddd2dd-dbbd-4204-a772-16dbca06832f)

For the Class Bot, the robot pivots to the right, so the right motor will be reversed. Add the line `rightmotor.setDirection(DcMotorSimple.Direction.REVERSE);` to the op mode under the variable declarations.

```java
public void runOpMode() {
        float x;
        double y;

        rightmotor = hardwareMap.get(DcMotor.class, "rightmotor");
        leftmotor = hardwareMap.get(DcMotor.class, "leftmotor");

        rightmotor.setDirection(DcMotorSimple.Direction.REVERSE);
        
        waitForStart();

        while (opModeIsActive()) {
              rightmotor.setPower(1);
              leftmotor.setPower(1);
            }
   }
```

Adding the `rightmotor.setDirection(DcMotorSimple.Direction.REVERSE);` code line reverses (or inverses) the direction of the right motor. Both motors now consider the same direction forward an

### Teleoperated Driving - Arcade Style

Recall that when the motors were running in opposing directions the robot spun in circles. This same logic will be used to control the robot using the arcade style of control mentioned in the Hello Robot - Autonomous Robot section.&#x20;

#### Programming with gamepads

To start, create two variables$$x$$and $$y$$. Both variables will be doubles.&#x20;

```java
public void runOpMode() {
        double x;
        double y;

        rightmotor = hardwareMap.get(DcMotor.class, "rightmotor");
        leftmotor = hardwareMap.get(DcMotor.class, "leftmotor");

        rightmotor.setDirection(DcMotorSimple.Direction.REVERSE);
        
        waitForStart();
```

&#x20;Assign $$y$$  as `y = -gamepad1.right_stick_y;` , which is the y-axis of the right joystick.&#x20;

{% hint style="info" %}
Remember positive/negative values inputted by the gamepad's y-axis are inverse of the positive/negative values of the motor.&#x20;
{% endhint %}

Assign the $$x$$ as the `x = gamepad1.right_stick_x;`, which is the x axis of the right gamepad joystick. The x-axis of the joystick does not need to be inverted.&#x20;

```java
while (opModeIsActive()) {
        x = gamepad1.right_stick_x;
        y = -gamepad1.right_stick_y;
        
        rightmotor.setPower(1);
        leftmotor.setPower(1);
        }
```

Setting `x = gamepad1.right_stick_x;` and `y = -gamepad1.right_stick_y;` assigns values from the gamepad joystick to $$x$$ and $$y$$. As previously mentioned, the joystick gives values along a two dimension coordinate system. $$y$$ receives the value from the y- axis and $$x$$ receives the value from the x-axis. Both axis output values between -1 and 1.&#x20;

To better understand consider the following table. The table shows the expected value generated from moving the joystick all the way in one direction, along the axis. For instance, when the joystick is pushed all the way in the upwards direction the coordinate values are (0,1).&#x20;

{% hint style="info" %}
The table below assumes that the the $$y$$values from the gamepad have been inverted in code when assigned to the variable $$y$$.
{% endhint %}

|                                                                                                                                      Joystick Direction                                                                                                                                     | $$x$$  | $$y$$  |
| :-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :----: | :----: |
|  <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mefge4HnWzFYZVV8De2%2F-Mefhx7EWkkmadU6LW8V%2FGamepad%20-%20forward%20simple.svg?alt=media&#x26;token=ea9e8593-204d-4c38-b370-52f1450bd996" alt="" data-size="original"> |    0   |    1   |
| <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mefge4HnWzFYZVV8De2%2F-MefhzwimOC2m68IoDSE%2FGamepad%20-%20reverse%20simple.svg?alt=media&#x26;token=9ff3f6ce-370a-47b4-9928-b5c475aa0d66" alt="" data-size="original">  |    0   |   -1   |
|   <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mefge4HnWzFYZVV8De2%2F-Mefi1rcj_EIfo6ZRW2u%2FGamepad%20-%20left%20simple.svg?alt=media&#x26;token=79ed0be9-83f2-41b4-988f-4b78b2474a22" alt="" data-size="original">   |   -1   |    0   |
|  <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mefge4HnWzFYZVV8De2%2F-Mefi4IQJxLAupAhBq8Y%2FGamepad%20-%20right%20simple.svg?alt=media&#x26;token=c0141307-dc28-46f2-8097-bd7b719b0968" alt="" data-size="original">   |    1   |    0   |

Now that you have a better understanding of how the physical movement of the gamepad affects the numerical inputs given to your Control System; its time to consider how to control the drivetrain using the joystick.&#x20;

{% hint style="info" %}
Recall, from the [Programming Drivetrain Motors](./#programming-drivetrain-motors) section, that the speed and direction of a motor plays a large part in how the drivetrain moves.
{% endhint %}

The numerical outputs for `setPower`determine the speed and direction of the motors. For instance, when both motors are set to 1 they move in the forward direction at full speed (or 100% of duty cycle).  Much like the gamepads, the numerical value for `setPower`is in a range of -1 to 1. The absolute value of the assigned number determines percentage of duty cycle. As an example, 0.3 and -0.3 both indicate that the motor is operating at a duty cycle of 30%. The sign of the number indicates the direction the motor is rotating in. To better understand, consider the following graphic.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MVwkCFYYAPlJ0cAmhBB%2F-MW-yY4NTAgAYNayqDF2%2FMotor%20-%20SetMotor%20relationship.svg?alt=media\&token=b2fce6df-9b82-47b3-8f34-83021b904a6f)

When a motor is assigned a `setPower` value between -1 and 0, the motor will rotate in the direction it considers to be reverse. When a motor is assigned a value between 0 and 1, it will rotate forward.&#x20;

In the [Programming Drivetrain Motors](./#programming-drivetrain-motors) section, it was discussed that a robot rotates when the motors are moving in opposing directions. However, this has more to do with both speed and direction. To think of it numerically, a differential drivetrain will turn to the right when the `setPower`value for the right motor is less than that of the left motor. This is exhibited in the following example.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MVwkCFYYAPlJ0cAmhBB%2F-MW-wFdz5WlegTXYg9GA%2FMotor%20-%20SetPower%20results%20-%20Blocks.svg?alt=media\&token=bf906b42-2a7c-45cc-a537-99823a08b54d)

When both motors are `rightmotor.setPower(1); leftmotor.setPower(1);`the robot will run at full speed in a mostly straight line. However, when the rightmotor is running in the same direction but at a lower speed, such as `rightmotor.setPower(0.3); leftmotor.setPower(1);` the robot will turn or rotate to the right. This is likely to be an arching movement that is not as sharp as a full pivot. In contrast when the `rightmotor` is set to full speed but in the opposite direction of the `leftmotor`, the robot pivots to the right. So, mathematically the following is considered to be true:&#x20;

|                                            |                    |
| ------------------------------------------ | ------------------ |
| `rightmotor.setPower = leftmotor.setPower` | Forward or Reverse |
| `rightmotor.setPower > leftmotor.setPower` | Left Turn          |
| `rightmotor.setPower < leftmotor.setPower` | Right Turn         |

As previously implied, `gamepad1.right_stick_y` and `gamepad1.right_stick_x`send values to the Control System from the game pad joystick. In contrast, the `setPower` function interprets numerical information set in the code and sends the appropriate current to the motors to dictate how the motors behave.&#x20;

In an arcade drive, the following joy stick inputs (directions) need to correspond with the following outputs (motor power values).&#x20;

| Joystick Direction                                                                                                                                                                                                                                                                          | (X,Y)  | rightmotor | leftmotor |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ | ---------- | --------- |
| <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mefge4HnWzFYZVV8De2%2F-Mefhx7EWkkmadU6LW8V%2FGamepad%20-%20forward%20simple.svg?alt=media&#x26;token=ea9e8593-204d-4c38-b370-52f1450bd996" alt="" data-size="original">  | (0,1)  | 1          | 1         |
| <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mefge4HnWzFYZVV8De2%2F-MefhzwimOC2m68IoDSE%2FGamepad%20-%20reverse%20simple.svg?alt=media&#x26;token=9ff3f6ce-370a-47b4-9928-b5c475aa0d66" alt="" data-size="original">  | (0,-1) | -1         | -1        |
| <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mefge4HnWzFYZVV8De2%2F-Mefi1rcj_EIfo6ZRW2u%2FGamepad%20-%20left%20simple.svg?alt=media&#x26;token=79ed0be9-83f2-41b4-988f-4b78b2474a22" alt="" data-size="original">     | (-1,0) | 1          | -1        |
| <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mefge4HnWzFYZVV8De2%2F-Mefi4IQJxLAupAhBq8Y%2FGamepad%20-%20right%20simple.svg?alt=media&#x26;token=c0141307-dc28-46f2-8097-bd7b719b0968" alt="" data-size="original">    | (1,0)  | -1         | 1         |

To get the outputs expressed in the table above, the gamepad values must be assigned to each motor in a meaningful way, where. Algebraic principles can be used to determine the two formulas needed to get the values. However, the formulas are provided below.&#x20;

$$
rightmotor = y-x \\
leftmotor = y+x
$$

Rather than `setPower(1);` both the motors can be set to the above formulas. For instance, the right motor can be set as `rightmotor.setPower(y-x);`.

```java
while (opModeIsActive()) {
        x = gamepad1.right_stick_x;
        y = -gamepad1.right_stick_y;
        
        rightmotor.setPower(y-x);
        leftmotor.setPower(y+x);
        }
```

With this you now have a functional teleoperated arcade drive. From here you can start adding hardware mapping for the other pieces of robot hardware. Below is an outline of the expected code for the Class Bot with full hardware mapping.&#x20;

```java
package org.firstinspires.ftc.teamcode;

import com.qualcomm.robotcore.eventloop.opmode.LinearOpMode;
import com.qualcomm.robotcore.hardware.Blinker;
import com.qualcomm.robotcore.hardware.Servo;
import com.qualcomm.robotcore.hardware.Gyroscope;
import com.qualcomm.robotcore.hardware.DigitalChannel;
import com.qualcomm.robotcore.eventloop.opmode.TeleOp;
import com.qualcomm.robotcore.eventloop.opmode.Disabled;
import com.qualcomm.robotcore.hardware.DcMotor;
import com.qualcomm.robotcore.hardware.DcMotorSimple;
import com.qualcomm.robotcore.util.ElapsedTime;

@TeleOp

public class DualDrive extends LinearOpMode {
    private Blinker control_Hub;
    private DcMotor arm;
    private Servo claw;
    private Gyroscope imu;
    private DcMotor leftmotor;
    private DcMotor rightmotor;
    private DigitalChannel touch;


    @Override
    public void runOpMode() {
        double x;
        double y;

        control_Hub = hardwareMap.get(Blinker.class, "Control Hub");
        arm = hardwareMap.get(DcMotor.class, "arm");
        claw = hardwareMap.get(Servo.class, "claw");
        imu = hardwareMap.get(Gyroscope.class, "imu");
        leftmotor = hardwareMap.get(DcMotor.class, "leftmotor");
        rightmotor = hardwareMap.get(DcMotor.class, "rightmotor");
        touch = hardwareMap.get(DigitalChannel.class, "touch");
        
        rightmotor.setDirection(DcMotorSimple.Direction.REVERSE);

        telemetry.addData("Status", "Initialized");
        telemetry.update();
        
        // Wait for the game to start (driver presses PLAY)
        waitForStart();

        // run until the end of the match (driver presses STOP)
        while (opModeIsActive()) {
              x = gamepad1.right_stick_x;
              y = -gamepad1.right_stick_y;
              
              rightmotor.setPower(y-x);
              leftmotor.setPower(y+x);
        
            telemetry.addData("Status", "Running");
            telemetry.update();

        }
    }
```
