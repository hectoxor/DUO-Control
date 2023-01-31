# Encoder Navigation - OnBot

In the previous section you learned about how to use Elapsed Time to allow your robot to navigate the world around it autonomously. When starting out many of the robot actions can be accomplished by turning on a motor for a specific amount of time. Eventually, these time-based actions may not be accurate or repeatable enough. Environmental factors, such as the state of battery charge during operation and mechanisms wearing in through use, can all affect time-based actions. Fortunately, there is a way to give feedback to the robot about how it is operating by using sensors; devices that are used to collect information about the robot and the environment around it. &#x20;

With Elapsed Time, in order to get the robot to move to a specific distance, you had to estimate the amount of time and the percentage of duty cycle needed to get from point a to point b. However, the REV motors come with built in encoders, which provide feedback in the form of ticks ( or counts) per revolution of the motor. The information provided by the encoders can be used to move the motor to a target position, or a target distance.&#x20;

Moving the motors to a specific position, using the encoders, removes any potential inaccuracies or inconsistencies from using Elapsed Time. The focus of this section is to move the robot to a target position using encoders.&#x20;

{% hint style="warning" %}
There are two articles in that go through the basics of Encoders. [Using Encoders](../../using-encoders.md) goes through the basics of the different types of motor modes, as well as a few application examples of using these modes in code. In this section we will focus on using `RUN_TO_POSITION`.

The other article, [Encoders](../../../sensors/encoders/), focuses on the general functionality of an encoder.&#x20;

It is recommended that you review both articles before moving on with this guide.&#x20;
{% endhint %}

## Basics of Programming with Encoders

Start by creating a basic op mode called`HelloRobot_EncoderAuton`.&#x20;

{% hint style="warning" %}
When creating an op mode a decision needs to be made on whether or not to set it to autonomous mode. For applications under 30 seconds, typically required for competitive game play changing the op mode type to autonomous is recommended. For applications over 30 seconds, setting the code to the autonomous op mode type will limit your autonomous code to 30 seconds of run time. If you plan on exceeding the 30 seconds built into the SDK, keeping the code as a teleoperated op mode type is recommended.&#x20;

For information on how op modes work please visit the [Introduction to Programming ](../../hello-robot-introduction-to-programming.md#op-modes)section.&#x20;

For more information on how to change the op mode type check out the [Test Bed - OnBot Java ](../../hello-robot-test-bed/test-bed-onbot-java.md#creating-an-op-mode)section.&#x20;
{% endhint %}

{% hint style="info" %}
The op mode structure below is simplified and only includes the necessary components needed to create the encoder based code.&#x20;
{% endhint %}

```java
package org.firstinspires.ftc.teamcode;

import com.qualcomm.robotcore.eventloop.opmode.LinearOpMode;
import com.qualcomm.robotcore.eventloop.opmode.Autonomous;
import com.qualcomm.robotcore.eventloop.opmode.TeleOp;
import com.qualcomm.robotcore.eventloop.opmode.Disabled;
import com.qualcomm.robotcore.hardware.DcMotor;
import com.qualcomm.robotcore.hardware.DcMotorSimple;

@Autonomous //sets the op mode as an autonomous op mode 

public class HelloWorld_EncoderAuton extends LinearOpMode {
    private DcMotor leftmotor;
    private DcMotor rightmotor;
    
    @Override
    public void runOpMode() {
        leftmotor = hardwareMap.get(DcMotor.class, "leftmotor");
        rightmotor = hardwareMap.get(DcMotor.class, "rightmotor");
        
        // Wait for the game to start (driver presses PLAY)
        waitForStart();

        // run until the end of the match (driver presses STOP)
        while (opModeIsActive()){
        
        }
    }
}

```

As with all drivetrain related navigation, the directionality of one of the motors needs to be reversed in order for both motors to move in the same direction. Since the Class Bot V2 is still being used add the line `rightmotor.setDirection(DcMotor.Direction.REVERSE);` to the code beneath the `rightmotor = hardwareMap.get(DcMotor.class, "rightmotor");` code line.&#x20;

```java
public void runOpMode() {
        leftmotor = hardwareMap.get(DcMotor.class, "leftmotor");
        rightmotor = hardwareMap.get(DcMotor.class, "rightmotor");
        
        rightmotor.setDirection(DcMotor.Direction.REVERSE);
        
        waitForStart();
```

{% hint style="info" %}
For more information on the directionality of motor check out the [Basics of Programming Drivetrains](../robot-navigation-blocks/#basics-of-programming-drivetrains) section.&#x20;
{% endhint %}

Recall from [Using Encoders](../../using-encoders.md) that using `RUN_TO_POSITION` mode requires a three step process. The first step is setting target position. To set target position add the lines `leftmotor.setTargetPosition(1000);` and `rightmotor.setTargetPosition(1000);` to the op mode after the `waitForStart();` command. To get a target position that equates to a target distance requires so calculations, which will be covered later. For now, set target position to 1000 ticks.&#x20;

```java
waitForStart();

leftmotor.setTargetPosition(1000);
rightmotor.setTargetPosition(1000);

while (opModeIsActive()){
        
        }
```

The next step is to set both motors to the `RUN_TO_POSITION`mode. Add the lines `leftmotor.setMode(DcMotor.RunMode.RUN_TO_POSITION);`and `rightmotor.setMode(DcMotor.RunMode.RUN_TO_POSITION);`to your code, beneath the `setTargetPosition` code lines.&#x20;

```java
waitForStart();

leftmotor.setTargetPosition(1000);
rightmotor.setTargetPosition(1000);

leftmotor.setMode(DcMotor.RunMode.RUN_TO_POSITION);
rightmotor.setMode(DcMotor.RunMode.RUN_TO_POSITION);

while (opModeIsActive()){
        
        }
```

The main focus of the three step process is to set a target, tell the robot to move to that target, and at what speed (or velocity) the robot should get to that target. Normally, the recommended next step is to calculate velocity and set a target velocity based on ticks. However, this requires quite a bit of math to find the appropriate velocity. For testing purposes, its more important to make sure that the main part of the code is working before getting too deep into the creation of the code. Since the `setPower` function was covered in previous sections and will communicate to the system what relative speed (or in this case duty cycle) is needed to get to the target, this can be used in the place of `setVelocity` for now.&#x20;

Add the lines to set the power of both motors to 80% of duty cycle.&#x20;

```java
waitForStart();

leftmotor.setTargetPosition(1000);
rightmotor.setTargetPosition(1000);

leftmotor.setMode(DcMotor.RunMode.RUN_TO_POSITION);
rightmotor.setMode(DcMotor.RunMode.RUN_TO_POSITION);

leftmotor.setPower(0.8);
rightmotor.setPower(0.8);

while (opModeIsActive()){
        
        }
```

Now that all three `RUN_TO_POSITION` steps have been added to the code the code can be tested. However, if you want to wait for the motor to reach its target position before continuing in your program, you can use a while loop that checks if the motor is busy (not yet at its target). For this program lets edit the `while (opModeIsActive()){}`&#x20;

{% hint style="info" %}
Recall that, within a linear op mode, a while loop must always have the `opModeIsActive()`  Boolean as a condition. This condition ensures that the while loop will terminate when the stop button is pressed.&#x20;
{% endhint %}

Edit the while loop to include the  `leftmotor.isBusy()` and `righmotor.isBusy()`functions. This will check if the left motor and right motor are busy running to a target position. The while loop will stop when either motor reaches the target position.&#x20;

```java
while (opModeIsActive() && (leftmotor.isBusy() && rightmotor.isBusy())) {

}
```

{% hint style="info" %}
Right now the while loop is waiting for the either motor to reach the target. There may be occasions when you want to wait for both motors to reach their target position, in this case the following loop can be used.&#x20;

`while (opModeIsActive() && (leftmotor.isBusy() || rightmotor.isBusy()))`
{% endhint %}

{% hint style="success" %}
Save and run the op mode two times in a row. Does the robot move as expected the second time?

Try turning the Control Hub off and then back on. How does the robot move?
{% endhint %}

In the [Basic Encoder Concepts ](../../using-encoders.md#basic-encoder-concepts)section, it is clarified that all encoder ports start at 0 ticks when the Control Hub is turned on. Since you did not turn off the Control Hub in between runs, the second time you ran the op mode the motors were already at, or around, the target position. When you run a code, you want to ensure that certain variables start in a known state. For the encoder ticks, this can be achieved by setting the mode to `STOP_AND_RESET_ENCODER` . Add this block to the op mode in the initialization section. Each time the op mode is initialized, the encoder ticks will be reset to zero.&#x20;

```java
public void runOpMode() {
        leftmotor = hardwareMap.get(DcMotor.class, "leftmotor");
        rightmotor = hardwareMap.get(DcMotor.class, "rightmotor");
        
        rightmotor.setDirection(DcMotor.Direction.REVERSE);
        
        leftmotor.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        rightmotor.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        
        waitForStart();
```

{% hint style="info" %}
For more information on the motor mode `STOP_AND_RESET_ENCODERS`check out the [STOP\_AND\_RESET\_ENCODERS](../../using-encoders.md#stop\_and\_reset\_encoder-mode) section of the Using Encoders guide.&#x20;
{% endhint %}

### Converting Encoder Ticks to a Distance&#x20;

In the previous section, the basic structure needed to use `RUN_TO_POSITION`was created. The placement of `leftmotor.setTargetPosition(1000);` and `rightmotor.setTargetPosition(1000);` within the code, set the target position to 1000 ticks. What is the distance from the starting point of the robot and the point the robot moves to after running this code?&#x20;

Rather than attempt to measure, or estimate, the distance the robot moves, the encoder ticks can be converted from amount of ticks per revolution of the encoder to how many encoder ticks it takes to move the robot a unit of distance, like a millimeter or inch. Knowing the amount of ticks per a unit of measure allows you to set a specific distance. For instance, if you work through the conversion process and find out that a drivetrain takes 700 ticks to move an inch, this can be used to find the total number of ticks need to move the robot 24 inches.&#x20;

{% hint style="warning" %}
Reminder that the basis for this guide is the [Class Bot V2](https://docs.revrobotics.com/duo-build/ftc-starter-kit-class-bot). The REV DUO Build System is a metric system. Since part of the conversion process references the diameter of the wheels, this section will convert to ticks per mm.
{% endhint %}

For the conversion process the following information is needed:&#x20;

* Ticks per revolution of the encoder
* Total gear reduction on the motor
  * Including gearboxes and motion transmission components like gears, sprockets and chain, or belts and pulleys
* Circumference of the driven wheels

#### Ticks per Revolution

The amount of ticks per revolution of the encoder shaft is dependent on the motor and encoder. Manufacturers of motors with built-in encoders will have information on the amount of ticks per revolution. For HD Hex Motors the encoder counts 28 ticks per revolution of the motor shaft.&#x20;

{% hint style="info" %}
Visit the manufacturers website for your motor or encoders for more information on encoder counts. For HD Hex Motors or Core Hex Motors visit our [Motor](https://docs.revrobotics.com/duo-build/actuators/motors) documentation.&#x20;
{% endhint %}

#### Total Gear Reduction

Since ticks per revolution of the encoder shaft is before any gear reduction calculating the total gear reduction is needed. This includes the gearbox and any addition reduction from motion transmission components. To find the total gear reduction use the [Compound Gearing formula](https://docs.revrobotics.com/duo-build/actuators/gears/gears-advanced#compound-gearing).

For the Class Bot V2 there are two UltraPlanetary Cartridges, 4:1 and 5:1, and an additional gear reduction from the UltraPlanetary Output to the wheels, 72T:45T ratio.

{% hint style="info" %}
The UltraPlanetary Cartridges use the nominal gear ratio as a descriptor. The actual gear ratios can be found in the [UltraPlanetary Users Manual's Cartridge Details](https://docs.revrobotics.com/ultraplanetary/cartridge-details#actual-cartridge-gear-ratios).&#x20;
{% endhint %}

Using the compound gearing formula for the Class Bot V2 the total gear reduction is:

$$
\frac{3.61}{1} * \frac{5.23}{1} * \frac{72}{45} = 30.21
$$

{% hint style="info" %}
Unlike the the spur gears used to transfer motion to the wheels, the UltraPlanetary Gearbox Cartridges are planetary gear systems. To make calculations easier the gear ratios for the Cartridges are already reduced.&#x20;
{% endhint %}

#### Circumference of the Wheel

The Class Bot V2 uses the 90mm Traction Wheels. 90mm is the diameter of the wheel. To get the appropriate circumference use the following formula&#x20;

$$
circumference = diameter * \pi
$$

You can calculate this by hand, but for the purpose of this guide, this can be calculated within the code.&#x20;

{% hint style="info" %}
Due to wear and manufacturing tolerances, the diameter of some wheels may be nominally different. For the most accurate results consider measuring your wheel to confirm that the diameter is accurate.&#x20;
{% endhint %}

To summarize, for the Class Bot V2 the following information is true:&#x20;

|                            |                 |
| -------------------------- | --------------- |
| Ticks per revolution       | 28 ticks        |
| Total gear reduction       | 30.21           |
| Circumference of the wheel | $$90mm * \pi$$  |

Each of these pieces of information will be used to find the number of encoder ticks (or counts) per mm that the wheel moves. Rather than worry about calculating this information by hand, these values can be added to the code as constant variables. To do this create three variables:

* `COUNTS_PER_MOTOR_REV`
* `DRIVE_GEAR_REDUCTION`
* `WHEEL_CIRCUMFERENCE_MM`

{% hint style="info" %}
The common naming convention for constant variables is known as CONSTANT\_CASE, where the variable name is in all caps and words are separated by and underscore.&#x20;
{% endhint %}

Add the variables to op mode class, where the hardware variables are defined. Defining the variables within the bounds of the class but outside of the op mode, allows them to be referenced in other methods of functions within the class. To ensure variables are referenceable they are set as `static final double` variables. Static allows references to the variables anywhere within the class and final dictates that these variables are constant and unchanged elsewhere within the code. Since these variables are not integers they are classified as double variables.&#x20;

```java
public class HelloWorld_EncoderAuton extends LinearOpMode {
    private DcMotor leftmotor;
    private DcMotor rightmotor;
    
    static final double     COUNTS_PER_MOTOR_REV    = 28.0; 
    static final double     DRIVE_GEAR_REDUCTION    = 30.21;   
    static final double     WHEEL_CIRCUMFERENCE_MM  = 90.0 * Math.PI;
```

Now that these three variables have been defined, they can be used to calculate two other variables: the amount of encoder counts per rotation of the wheel and the number of counts per mm that the wheel moves.&#x20;

To calculate counts per wheel revolution multiple`COUNTS_PER_MOTOR_REV` by `DRIVE_GEAR_REDUCTION` Use the following formula:

$$
y = a
*b
$$

Where,&#x20;

* $$a$$ = `COUNTS_PER_MOTOR_REV`
* $$b$$ = `DRIVE_GEAR_REDUCTION`&#x20;
* $$y$$ = `COUNTS_PER_WHEEL_REV`

Create the `COUNTS_PER_WHEEL_REV`variable within the code. This will also be a `static final double` variable.&#x20;

```java
public class HelloWorld_EncoderAuton extends LinearOpMode {
    private DcMotor leftmotor;
    private DcMotor rightmotor;
    
    static final double     COUNTS_PER_MOTOR_REV    = 28.0; 
    static final double     DRIVE_GEAR_REDUCTION    = 30.24;   
    static final double     WHEEL_CIRCUMFERENCE_MM  = 90.0 * 3.14;
    
    static final double     COUNTS_PER_WHEEL_REV    = COUNTS_PER_MOTOR_REV * DRIVE_GEAR_REDUCTION;
```

Once `COUNTS_PER_WHEEL_REV` is calculated, use it to calculate the counts per mm that the wheel moves. To do this divide the`COUNTS_PER_WHEEL_REV` by the `WHEEL_CIRCUMFERENCE_MM`. Use the following formula.

$$
x = \frac{(a*b)}{c} = \frac{y}{c}
$$

Where,

* $$a$$ = `COUNTS_PER_MOTOR_REV`
* $$b$$ = `DRIVE_GEAR_REDUCTION`
* $$c$$ = `WHEEL_CIRCUMFERENCE_MM`
* $$y$$ = `COUNTS_PER_WHEEL_REV`
* $$x$$ = `COUNTS_PER_MM`

Create the `COUNTS_PER_MM`variable within the code. This will also be a `static final double` variable.&#x20;

```java
public class HelloWorld_EncoderAuton extends LinearOpMode {
    private DcMotor leftmotor;
    private DcMotor rightmotor;
    
    static final double     COUNTS_PER_MOTOR_REV    = 28.0; 
    static final double     DRIVE_GEAR_REDUCTION    = 30.24;   
    static final double     WHEEL_CIRCUMFERENCE_MM  = 90.0 * 3.14;
    
    static final double     COUNTS_PER_WHEEL_REV    = COUNTS_PER_MOTOR_REV * DRIVE_GEAR_REDUCTION;
    static final double     COUNTS_PER_MM           = COUNTS_PER_WHEEL_REV / WHEEL_CIRCUMFERENCE_MM;
```

{% hint style="warning" %}
`COUNTS_PER_WHEEL_REV`will be created as a separate variable from`COUNTS_PER_MM` as it is used in calculating a target velocity.&#x20;
{% endhint %}

### Moving to a Target Distance&#x20;

Now that you have created the constant variables needed to calculate the amount of ticks per mm moved, you can use this to set a target distance. For instance, if you would like to have the robot move forward two feet, converting from feet to millimeters and multiplying by the `COUNTS_PER_MM`will give you the amount of counts (or ticks) needed to reach that distance.&#x20;

Create two more variables called `leftTarget` and`rightTarget`. These variables can be fluctuated and edited in your code to tell the motors what positions to go to, rather than place them with the constant variables, create these variables within the op mode but above the `waitForStart();` command.&#x20;

{% hint style="info" %}
The `setTargetPosition();`function takes in a integer (or int) data type as its parameter, rather than a double. Since both the `leftTarget` and `rightTarget`will be used to set the target position, create both variables as int variables.&#x20;
{% endhint %}

```java
public void runOpMode() {
        leftmotor = hardwareMap.get(DcMotor.class, "leftmotor");
        rightmotor = hardwareMap.get(DcMotor.class, "rightmotor");
        
        rightmotor.setDirection(DcMotor.Direction.REVERSE);
        
        leftmotor.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        rightmotor.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        
        int leftTarget;
        int rightTarget;
        
        waitForStart();
```

Right now the main distance factor is `COUNTS_PER_MM` , however you may want to go a distance that is in the imperial system, such as 2 feet (or 24 inches). The target distance in this case will need to be converted to mm. To convert from feet to millimeters use the following formula:

$$
d_{(mm)} = d_{(ft)} × 304.8
$$

If you convert 2 feet to millimeters, it comes out the be 609.6 millimeters. For the purpose of this guide, lets go ahead an round this to be 610 millimeters. Multiply 610 millimeters by the`COUNTS_PER_MM` variable to get the number of ticks needed to move the robot 2 feet. Since the intent is to have the robot move in a straight line, set both the `leftTarget` and `rightTarget`, to be equal to 610 \*  `COUNTS_PER_MM`

{% hint style="info" %}
As previously mentioned the `setTargetPosition();` function requires that its parameter must be an integer data type. The `leftTarget`and `rightTarget`variables have been set to be integers, however the`COUNTS_PER_MM` variable is a double. Since these are two different data types, a conversion of data types needs to be done.&#x20;

In this case the`COUNTS_PER_MM`needs to be converted to an integer. This is as simple as adding the line (int) in front of the double variable. However, you need to be cautious of potential rounding errors. Since `COUNTS_PER_MM`is part of an equation it is recommended that you convert to an integer after the result of the equation is found. The example of how to do this is exhibited below.&#x20;
{% endhint %}

```java
int leftTarget = (int)(610 * COUNTS_PER_MM);
int rightTarget = (int)(610 * COUNTS_PER_MM);
```

Edit the `setTargetPosition();` lines so that both motors are set to the appropriate target position. To do this add the `leftTarget`and `rightTarget` variables to their respective motor.&#x20;

```java
leftmotor.setTargetPosition(leftTarget);
rightmotor.setTargetPosition(rightTarget);
```

{% hint style="success" %}
Try running the code and observing the behavior of the robot. Consider some of the following &#x20;

* Is the robot moving forward by two feet?
* Does the robot seem to be moving in straight line?&#x20;
* Is the code running without error?
{% endhint %}

### Setting Velocity&#x20;

Velocity is a closed loop control within the SDK that uses the encoder counts to determine the approximate power/speed the motors need to go in order to meet the set velocity. When working with encoder setting a velocity is recommended over setting a power level, as it offers a higher level of control.&#x20;

To set a velocity, its important to understand the maximum velocity in RPM your motor is capable of. For the Class Bot V2 the motors are capable of a maximum RPM of 300. With a drivetrain, you are likely to get better control by setting velocity lower than the maximum. In this case, lets set the velocity to 175 RPM&#x20;

{% hint style="info" %}
Recall that `setVelocity` is measure in ticks per second.&#x20;
{% endhint %}

Create a new double variable called `TPS`. Add `TPS` the to the op mode under where `rightTarget` is defined. &#x20;

```java
public void runOpMode() {
        leftmotor = hardwareMap.get(DcMotor.class, "leftmotor");
        rightmotor = hardwareMap.get(DcMotor.class, "rightmotor");
        
        rightmotor.setDirection(DcMotor.Direction.REVERSE);
        
        leftmotor.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        rightmotor.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        
        int leftTarget = (int)(610 * COUNTS_PER_MM);
        int rightTarget = (int)(610 * COUNTS_PER_MM);
        double TPS;
        
        waitForStart();
```

Since RPM is the amount of revolutions per minute a conversion needs to be made from RPM to ticks per second. To do this divide the RPM by 60, to get the amount of rotations per second. Rotations per second can the be multiplied by `COUNTS_PER_WHEEL_REV`, to get the amount of ticks per second.&#x20;

$$
TPS = \frac{175}{60} * CPWR
$$

```java
double TPS = (175/60) * COUNTS_PER_WHEEL_REV
```

Exchange the `setPower();`functions for `setVelocity();`. Add`TPS` as the parameter for `setVelocity();`.

```java
waitForStart();

leftmotor.setTargetPosition(leftTarget);
rightmotor.setTargetPosition(rightTarget);

leftmotor.setMode(DcMotor.RunMode.RUN_TO_POSITION);
rightmotor.setMode(DcMotor.RunMode.RUN_TO_POSITION);

leftmotor.setVelocity(TPS);
rightmotor.setVelocity(TPS);

while (opModeIsActive() && (leftmotor.isBusy() && rightmotor.isBusy())){
        
        }
```

{% hint style="success" %}
Try to build the code. Do you get errors?&#x20;
{% endhint %}

With the current state of the code you are likely to get errors similar to the ones pictured below:

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYg8Ye7SaX4Ko7AR-5W%2F-MYkwkfQkLpwvRZ6d221%2Fmotor%20ex%20error.svg?alt=media\&token=a42e1af9-8986-4338-a0f6-cdd18038fc1e)

This is because the `setVelocity();`function is a function of the`DcMotorEx` Interface. The `DcMotorEx` Interface is an extension of the `DcMotor` Interface, that provides enhanced motor functionality, such as access to closed loop control functions. To use `setVelocity();` the motor variables need to be changed to `DcMotorEx` . To do this both the private variable creation of the motors, and the hardware mapping need to be changed to `DcMotorEx`.&#x20;

```java
public class HelloWorld_EncoderAuton extends LinearOpMode {
    private DcMotorEx leftmotor;
    private DcMotorEx rightmotor;
```

```java
public void runOpMode() {
        leftmotor = hardwareMap.get(DcMotorEx.class, "leftmotor");
        rightmotor = hardwareMap.get(DcMotorEx.class, "rightmotor");
```

{% hint style="info" %}
Since `DcMotorEx` is an extension of `DcMotor`, `DcMotor` specific functions can be used by variables defined as `DcMotorEx`.&#x20;
{% endhint %}

Once you have made these changes the basic, drive two feet code is done! The code below is the finalized version of the code. In this the other hardware components and telemetry have been added.&#x20;

```java
@Autonomous

public class HelloWorld_EncoderAuton extends LinearOpMode {
    private DcMotorEx leftmotor;
    private DcMotorEx rightmotor;
    private DcMotor arm;
    private Servo claw;
    private DigitalChannel touch;
    private Gyroscope imu; 
    
    static final double     COUNTS_PER_MOTOR_REV    = 28.0; 
    static final double     DRIVE_GEAR_REDUCTION    = 30.24;   
    static final double     WHEEL_CIRCUMFERENCE_MM  = 90.0 * 3.14;
    
    static final double     COUNTS_PER_WHEEL_REV    = COUNTS_PER_MOTOR_REV * DRIVE_GEAR_REDUCTION;
    static final double     COUNTS_PER_MM           = COUNTS_PER_WHEEL_REV / WHEEL_CIRCUMFERENCE_MM;
    
    @Override
    public void runOpMode() {
        imu = hardwareMap.get(Gyroscope.class, "imu");
        leftmotor = hardwareMap.get(DcMotorEx.class, "leftmotor");
        rightmotor = hardwareMap.get(DcMotorEx.class, "rightmotor");
        arm = hardwareMap.get(DcMotor.class, "arm");
        claw = hardwareMap.get(Servo.class, "claw");
        touch = hardwareMap.get(DigitalChannel.class, "touch");
        
        rightmotor.setDirection(DcMotor.Direction.REVERSE);

        leftmotor.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        rightmotor.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        
        
        int leftTarget = (int)(610 * COUNTS_PER_MM);
        int rightTarget = (int)(610 * COUNTS_PER_MM);
        double TPS = (175/ 60) * COUNTS_PER_WHEEL_REV;
        
        waitForStart();
        
        
        leftmotor.setTargetPosition(leftTarget);
        rightmotor.setTargetPosition(rightTarget);
        
        leftmotor.setMode(DcMotor.RunMode.RUN_TO_POSITION);
        rightmotor.setMode(DcMotor.RunMode.RUN_TO_POSITION);
        
        leftmotor.setVelocity(TPS);
        rightmotor.setVelocity(TPS);
        
        while (opModeIsActive() && (leftmotor.isBusy() && rightmotor.isBusy())) {
            telemetry.addData("left", leftmotor.getCurrentPosition());
            telemetry.addData("right", rightmotor.getCurrentPosition());
            telemetry.update();
        }
    }
}
```

### Turning the Drivetrain Using RUN\_TO\_POSITION

In the [Robot Navigation - OnBot Java ](broken-reference)section, the mechanism of `setPower();` was discussed. `setPower();`dictates what direction and speed a motor moves in. On a drivetrain this dictates whether the robot moves in forward, reverse, or turns.

In `RUN_TO_POSITION`mode  the encoder counts ( or `setTargetPosition();`) are used instead of `setPower();` to dictate directionality of the motor. If a target position value is greater than the current position of the encoder, the motor moves forward. If the target position value is less than the current position of the encoder, the motor moves backwards

Since speed an directionality impacts how a robot turns, `setTargetPostion();` and `setVelocity();`need to be edited to get the robot to turn. Consider the following code:&#x20;

```java
int leftTarget = (int)(610 * COUNTS_PER_MM);
int rightTarget = (int)(-610 * COUNTS_PER_MM);
double TPS = (100/ 60) * COUNTS_PER_WHEEL_REV;
       
        
waitForStart();
        
        
leftmotor.setTargetPosition(leftTarget);
rightmotor.setTargetPosition(rightTarget);
        
leftmotor.setMode(DcMotor.RunMode.RUN_TO_POSITION);
rightmotor.setMode(DcMotor.RunMode.RUN_TO_POSITION);
        
leftmotor.setVelocity(TPS);
rightmotor.setVelocity(TPS);
```

The `rightTarget` has been changed to be a negative target position. Assuming that the encoder starts at zero due to `STOP_AND_RESET_ENCODER` this causes the robot to turn to the right. Velocity remains the same for both motors. If you try running this code, you may notice that the robot pivots along its center of rotation. To get a wider turn changing the velocity so that the right motor is running at a lower velocity than the left motor. Adjust the velocity and target position as needed to get the turn you need.

{% hint style="info" %}
For more information on how direction and speed impact the movement of a robot please refer to the explanation of `setPower();` in the [Robot Navigation ](../robot-navigation-blocks/#teleoperated-driving-arcade-style)section.
{% endhint %}

The following code walks through adding a turn to the program, after the robot moves forward for 2 feet. After the robot reaches the 2 foot goal, there is a call to `STOP_AND_RESET_ENCODERS` this will reduce the need to calculate what position to go to after a position has been reached.&#x20;

```java
@Autonomous

public class HelloWorld_EncoderAuton extends LinearOpMode {
    private DcMotorEx leftmotor;
    private DcMotorEx rightmotor;
    private DcMotor arm;
    private Servo claw;
    private DigitalChannel touch;
    private Gyroscope imu; 
    
    static final double     COUNTS_PER_MOTOR_REV    = 28.0; 
    static final double     DRIVE_GEAR_REDUCTION    = 30.24;   
    static final double     WHEEL_CIRCUMFERENCE_MM  = 90.0 * 3.14;
    
    static final double     COUNTS_PER_WHEEL_REV    = COUNTS_PER_MOTOR_REV * DRIVE_GEAR_REDUCTION;
    static final double     COUNTS_PER_MM           = COUNTS_PER_WHEEL_REV / WHEEL_CIRCUMFERENCE_MM;
    
    @Override
    public void runOpMode() {
        imu = hardwareMap.get(Gyroscope.class, "imu");
        leftmotor = hardwareMap.get(DcMotorEx.class, "leftmotor");
        rightmotor = hardwareMap.get(DcMotorEx.class, "rightmotor");
        arm = hardwareMap.get(DcMotor.class, "arm");
        claw = hardwareMap.get(Servo.class, "claw");
        touch = hardwareMap.get(DigitalChannel.class, "touch");

        rightmotor.setDirection(DcMotor.Direction.REVERSE);

        leftmotor.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        rightmotor.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        
        // TPS variable split to change velocity for each motor when necessary
        
        int leftTarget = (int)(610 * COUNTS_PER_MM);
        int rightTarget = (int)(610 * COUNTS_PER_MM);
        double LTPS = (175/ 60) * COUNTS_PER_WHEEL_REV;         
        double RTPS = (175/ 60) * COUNTS_PER_WHEEL_REV;
        
        waitForStart();
        
        
        leftmotor.setTargetPosition(leftTarget);
        rightmotor.setTargetPosition(rightTarget);
        
        leftmotor.setMode(DcMotor.RunMode.RUN_TO_POSITION);
        rightmotor.setMode(DcMotor.RunMode.RUN_TO_POSITION);
        
        leftmotor.setVelocity(LTPS);
        rightmotor.setVelocity(RTPS);
        
        //wait for motor to reach position before moving on 
        while (opModeIsActive() && (leftmotor.isBusy() && rightmotor.isBusy())) {
            telemetry.addData("left", leftmotor.getCurrentPosition());
            telemetry.addData("right", rightmotor.getCurrentPosition());
            telemetry.update();
        }
        // Reset encoders to zero 
        leftmotor.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        rightmotor.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        
        // changing variables to match new needs 
        
        leftTarget = (int)(300 * COUNTS_PER_MM);
        rightTarget = (int)( -300 * COUNTS_PER_MM);
        LTPS = (100/ 60) * COUNTS_PER_WHEEL_REV;         
        RTPS = (70/ 60) * COUNTS_PER_WHEEL_REV;
        
        leftmotor.setTargetPosition(leftTarget);
        rightmotor.setTargetPosition(rightTarget);
        
        leftmotor.setMode(DcMotor.RunMode.RUN_TO_POSITION);
        rightmotor.setMode(DcMotor.RunMode.RUN_TO_POSITION);
        
        leftmotor.setVelocity(LTPS);
        rightmotor.setVelocity(RTPS);
        
        //wait for motor to reach position before moving on 
        while (opModeIsActive() && (leftmotor.isBusy() && rightmotor.isBusy())) {
            telemetry.addData("left", leftmotor.getCurrentPosition());
            telemetry.addData("right", rightmotor.getCurrentPosition());
            telemetry.update();
        }
    }
}
```
