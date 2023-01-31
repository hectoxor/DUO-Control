# Arm Control - OnBot Java

## Introduction to Arm Control&#x20;

Robot control comes in many different forms. Now that you have walked through programming a drivetrain, we can apply those concepts to controlling other mechanisms. Since this guide utilizes the Class Bot the focus will be on the basics of controlling it's main mechanism, a single jointed arm. &#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Mbh\_La74HLHjHtArkSm%2F-Mbh\_RZjnHpZbvvDsZ8H%2FClass%20Bot%20side%20view.svg?alt=media\&token=1bfb2c2c-c01c-42c1-87cc-801a1bc2da2b)

Controlling an arm requires a different thought process than the one you used to control the drivetrain. While the drivetrain uses the rotation motion of the motors to drive along a linear distance, an arm rotates along a central point, or joint. When working with an arm you will have to head caution to the physical limitations of the robot this includes load bearing, range of motion, and other forces that may apply.

In this section you will learn how to use the gamepad `Dpad` controls and the installed Touch Sensor to control the arm. However, the focus of this section is using code to limit the range of motion of the arm.&#x20;

| Sections                                                                                                     | Goals of Section                                                                                                      |
| ------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------- |
| [Basics of Programming an Arm](arm-control-onbot-java.md#basics-of-programming-an-arm)                       | Introduction to coding an arm for teleoperated control and working with a limit switch                                |
| [Programming an Arm to a Position](arm-control-onbot-java.md#programming-an-arm-to-a-position)               | Using motor encoders to move an arm to a specific position, such as from 45 degrees to 90 degrees.                    |
| [Using Limits to Control Range of Motion](arm-control-onbot-java.md#using-limits-to-control-range-of-motion) | Working with the basics of arm control, motor encoder, and limit switches to control the range of motion for an arm.  |

## Basics of Programming an Arm&#x20;

Start by creating a basic op mode called `HelloRobot_ArmControl`.&#x20;

{% hint style="warning" %}
For more information on how to create an op mode check out the [Test Bed - Onbot Java ](../hello-robot-test-bed/test-bed-onbot-java.md)section. &#x20;
{% endhint %}

Unlike the joystick, which sends values corresponding to the position of the joystick, the `Dpad` on the gamepad inputs **Boolean** `FALSE/TRUE`. In order to dictate how the arm moves when you press `DpadUp` **** or  `DpadDown`; an`if/else if` statement needs to be used. Create an `if/else if` statement like the one below.&#x20;

```java
while (opModeIsActive()) {
   if(gamepad1.dpad_up){
                
                }
   else if (gamepad1.dpad_down){
            
                } 
     }            
```

Now that the basic structure is in place, we can add the necessary blocks to dictate the direction of the arm. The best practice is to have the arm move up when `DpadUp` is selected and down with `DpadDown`is selected. To do this lets add`arm.SetPower();` to each of the actionable parts of the `if/else if`statement.&#x20;

{% hint style="info" %}
Recall that the value assigned to `setPower` dictates the [direction and speed](robot-navigation-blocks/#basics-of-programming-drivetrains) of the motor. Between the motor and the gearing on the class bot the positive value will move the arm the arm upwards and a negative value will move the arm downwards.&#x20;

If you are unsure which direction your motor will move create the following code and test to ensure that your motor is behaving as expected.&#x20;
{% endhint %}

```java
if(gamepad1.dpad_up){
       arm.setPower(0.2);         
            }
else if (gamepad1.dpad_down){
       arm.setPower(-0.2); 
            }   
```

{% hint style="info" %}
Starting with a lower duty cycle percentage such as the 0.2 exhibited in the code above, will allow for easier testing when making decisions for the arm. We will change to a higher duty cycle later on in this guide.
{% endhint %}

{% hint style="success" %}
Save the op mode and try running the code. Consider the following questions.&#x20;

* What happens if you press up on the `Dpad`?
* What happens if you press down on the `Dpad`?
{% endhint %}

Right now the logic of the `if/else if`statement declares that when  `gamepad1.dpad_up` is true (has been pressed) the motor will run in the forward ( or in this case upwards) direction at 20% duty cycle. If `gamepad1.dpad_down` is true the motor will run in reverse at 20% duty cycle. If you ran the code at this stage you may have noticed that even when you released the`Dpad` the motor continued to run in the selected direction. The current `if/else if`statement tells the robot when the motor should move and in what direction, but nothing tells the motor to stop, thus the arm continues to run without limits.&#x20;

To fix this edit the`if/else if` statement to include and action to perform if neither gamepad conditions are true. Since we want the arm to stop moving if neither gamepad conditions are met lets use `arm.setPower(0);` to stop the motor .

```java
if(gamepad1.dpad_up){
       arm.setPower(0.2);         
            }
else if (gamepad1.dpad_down){
       arm.setPower(-0.2); 
            }   
else { 
       arm.setPower(0); 
            }    
```

{% hint style="success" %}
Try saving and running the op mode again. Pay attention to the speed of the arm going up versus going down. Does the speed seem the same?
{% endhint %}

Working with an arm introduces different factors for consideration than what you have seen previously with drivetrains. For instance, did you notice a difference in speeds when moving the arm up or down? Unlike the drivetrain, where the effect of gravity impacts the motors consistently across either direction, gravity plays a significant role in the speed of the arm motor.&#x20;

### Adding a Limit Switch&#x20;

Another consideration to make is the physical limitations of your arm mechanism. Certain mechanisms may have a physical limitation, that when exceeded runs the risk of damaging the mechanism or another component of the robot. There are a few ways to limit the mechanism with sensors that will help reduce the potential of a mechanism exceeding its physical limitations. In this section we will focus on using a limit switch to limit the motion range of the arm.

{% hint style="info" %}
This section assumes that you have a basic knowledge of limit switches form the[ Test Bed](../hello-robot-test-bed/test-bed-onbot-java.md#programming-a-digital-device) section and the [Digital Sensors](../../sensors/digital.md#applications) article.&#x20;
{% endhint %}

As you may recall from the Test Bed section limit switches use Boolean logic to dictate when a limit has been met. Limit switches typically come in the form of digital sensors, like the Touch Sensor, as digital sensors report a **Boolean** on/off to the system, much like a light switch.&#x20;

If you are using a Class Bot your robot should have a Touch Sensor mounted to the front of your robot chassis. You also have a[ Limit Switch Bumper](https://docs.revrobotics.com/15mm/ftc-starter-kit-class-bot/skv3-arm-assemblies#limit-switch-bumper-assembly) installed. Together these items create a limit switch system. By utilizing the limit switch system you can keep your Class Bot arm from exceeding the lower physical limit, or what will be known as our starting position. Lets go ahead and start coding!&#x20;

{% hint style="warning" %}
Before proceeding with code please make sure that your mechanism is interfacing with, and pressing the Touch Sensor. If you have the Class Bot this entails making sure your bumper is actively pressing the Touch Sensor when the arm comes down.&#x20;
{% endhint %}

In the [Test Bed - Onbot Java](../hello-robot-test-bed/test-bed-onbot-java.md#digital-devices-as-limit-switches) section, you learned how to create a basic limit switch program, similar to the one below.

{% code title="Limit Switch if/else" %}
```java
 if (touch.getState()){
    //Touch Sensor is not pressed  
     arm.setPower(0.2);
    
} else {
    //Touch Sensor is pressed 
    arm.setPower(0);
                        }
```
{% endcode %}

If you recall from the initial Limit Switch section, the Touch Sensor operates on a `FALSE/TRUE`binary. When the touch sensors is not pressed `touch.getState()`reports `true`; when the touch sensor is pressed `touch.getState()`reports `false`. The logic of the code states that when touch sensor is not pressed, the motor runs at 20% duty cycle.&#x20;

Rather than have the motor run at 20% of duty cycle when the Touch Sensor isn't pressed and stop when the sensor is pressed, we want to control the arm using the gamepad still. To do this we can nest the `Gamepad if/else if`statement within the `Limit Switch if/else` statement.&#x20;

{% hint style="warning" %}
For this next portion we will be utilizing the `if/else if` statement create in the Basics of Programming and Arm. From here on out this basic code logic will be refereed to as the `Gamepad if/else if`. The limit switch code will be know as the `Limit Switch if/else`. Both pieces of code will be referenced again.

{% code title="Gamepad if/else if " %}
```java
if(gamepad1.dpad_up){
       arm.setPower(0.2);         
            }
else if (gamepad1.dpad_down){
       arm.setPower(-0.2); 
            }   
else { 
       arm.setPower(0); 
            } 
```
{% endcode %}
{% endhint %}

```java
if(touch.getState()){
      if(gamepad1.dpad_up){
            arm.setPower(0.2);         
                 }
      else if (gamepad1.dpad_down){
            arm.setPower(-0.2); 
                 }   
      else { 
            arm.setPower(0); 
                 }  
       }
  else {
      arm.setPower(0);
       } 
```

{% hint style="success" %}
Save the op mode and run it.&#x20;

What happens when the Touch Sensor is pressed?
{% endhint %}

One of the common features of a limit switch, like the touch sensor,  is the ability to reset to its default state. If you press the Touch Sensor with your finger, you may notice that as soon as you release the pressure you are applying the Touch Sensor will return to its default "not pressed" state. However, you have to release the pressure in order to accomplish this.&#x20;

{% hint style="warning" %}
Make sure that the mechanism is actually interfacing with the Touch Sensor. For the Class Bot, you may need to adjust the Touch Sensor so that the Limit Switch Bumper is interfacing with it more consistently.&#x20;
{% endhint %}

The code in the info block above dictates that when the Touch Sensor is pressed the arm motor is set to zero. This would work in a mechanism where the Touch Sensor is allowed to return to its default state on its own. However, once the arm presses the Touch Sensor, the weight of the mechanism will keep the Touch Sensor from returning to its default state. The combination of the weight of the mechanism and the logic of the info block code means that once the arm meets its limit it will not be able to move again.&#x20;

To remedy this, an action to move the arm in the opposite direction of of the limit needs to be added to the `else` statement.  Since the Touch Sensor is a lower limit for the arm, the arm will need to move up (or the motor in the forward direction) to move away from the touch sensor. To do this we can create an `if/else` statement similar to our gamepad `Gamepad if/else if`statement. Instead of having the normal gamepad operations, when the Touch Sensor and`DpadUp` are pressed the arm moves away from the Touch Sensor. Once the Touch Sensor no longer reports false the normal gamepad operations return and the arm can move in either direction again.

```java
if(touch.getState()){
      if(gamepad1.dpad_up){
            arm.setPower(0.2);         
                 }
      else if (gamepad1.dpad_down){
            arm.setPower(-0.2); 
                 }   
      else { 
            arm.setPower(0); 
                 }  
       }
  else {
       if(gamepad1.dpad_up){
            arm.setPower(0.2);         
                 }
       else{
            arm.setPower(0);
       } 
```

## Programming an Arm to a Position

In the [Encoder Navigation](robot-navigation-onbot-java/encoder-navigation-onbot.md#basics-of-programming-with-encoders) section the concept of moving the motor to a specific position based on encoder ticks was introduced. The process highlighted in _Encoder Navigation_ focused on how to convert from encoder ticks to rotations to a linear distance. A similar procedure can be utilized to move the arm to a particular position. However, unlike the drivetrain, the arm does not follow a linear path. Rather than convert to a linear distance it makes more sense to convert the encoder ticks into an angle measured in degrees.&#x20;

In the image below two potential positions are showcased for the ClassBot arm. One of the positions - highlighted in blue below - is the position where the arm meets the limit of the touch sensor. Due to the limit, this position will be our default or starting position. From the Class Bot build guide, it is known that the Extrusion supporting the battery sits a 45 degree angle. Since the arm is roughly parallel to these extrusion when it is in the starting position, we can estimate that the default angle of the arm is roughly 45 degrees.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MaZOjYoShzpGpEUjqNv%2F-Ma\_\_OatEnD88azc\_Zie%2Fdifferent%20positions.svg?alt=media\&token=f19ee578-4d9b-4708-adda-c99a62259f90)

The goal of this section is to determine the amount of encoder ticks it will take to move the arm from its starting position to a position around 90 degrees.  There are a few different ways this can be accomplished. An estimation can be done by moving the arm to the desired position and recording the telemetry feedback from the Driver Station. Another option is to do to the math calculations to find the amount of encoder ticks occur per degree moved. Follow through this section to walk through both options and determine which is the best for your team.&#x20;

### Estimating the Position of the Arm&#x20;

To estimate the position of the arm using telemetry and testing, lets start with the `Gamepad if/else if`code.

{% code title="Gamepad if/else if " %}
```java
if(gamepad1.dpad_up){
       arm.setPower(0.2);         
            }
else if (gamepad1.dpad_down){
       arm.setPower(-0.2); 
            }   
else { 
       arm.setPower(0); 
            } 
```
{% endcode %}

{% hint style="warning" %}
For now you can comment out the limit switch related code.&#x20;
{% endhint %}

Within the while loop add the lines`telemetry.addData("Arm Test", arm.getCurrentPosition());` and `telemetry.update();`&#x20;

```java
while(opModeIsActive){
    if(gamepad1.dpad_up){
       arm.setPower(0.2);         
            }
     else if (gamepad1.dpad_down){
       arm.setPower(-0.2); 
            }   
     else { 
       arm.setPower(0); 
            } 
     telemetry.addData("Arm Test", arm.getCurrentPosition());
     telemetry.update();
          
 }
```

Save the op mode and run it. Use the gamepad commands to move the arm to the 90 degree position. Once you have the arm properly positioned read the telemetry off the Driver Station to determine the encoder count relative to the position of the arm.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MadRPzxQDwEcPdg\_MX-%2F-Mae0pJn3Pk9zTlgBL5x%2FClass%20Bot%20side%20view%20arm%20at%2090%20-%20with%20DS%20telemetry.svg?alt=media\&token=6bbd1870-e17a-407a-b7d3-77be74c46e2b)

{% hint style="warning" %}
Recall from the[ Basic Encoder Concepts](../using-encoders.md#basic-encoder-concepts) section that the encoder position is set to 0 each time the Control Hub is turned on. This means that if your arm is in a position other than the starting position when the Control Hub is turned on, that position becomes zero instead of the starting position.&#x20;

The number given in the image above is not necessarily an accurate encoder count for the 90 degree position. To get the most accurate encoder reading for your robot make sure that your starting position reads as 0 encoder counts. To further increase accuracy consider doing several testing runs before deciding on the number of counts.&#x20;
{% endhint %}

Recall that in order to execute `RUN_TO_POSITION` the following three lines of cod need to be added to both sections of the Gamepad `if/else if` block.

```java
arm.setTargetPosition(0);
arm.setMode(DcMotor.RunMode.RUN_TO_POSITION);
arm.setPower(0);
```

When `DpadUp` is pressed, the arm should move to the the 90 degree position. When`DpadDown` is pressed the arm should move back to the starting position. To do this set the first`arm.setTargetPosition(0);` equal to the number of ticks it took your arm to get to 90 degrees, for this example we will use 83 ticks.&#x20;

Since we want `DpadDown` **** to return the arm to the starting position, keeping the  `arm.setTargetPosition(0);` set to 0 will allow us to accomplish this. Set both `arm.setPower(0);` equal to 0.5.&#x20;

{% code title="Target Position if/else if " %}
```java
if(gamepad1.dpad_up){
     arm.setTargetPosition(83);
     arm.setMode(DcMotor.RunMode.RUN_TO_POSITION);
     arm.setPower(0.5);
            }
else if (gamepad1.dpad_down){
      arm.setTargetPosition(0);
      arm.setMode(DcMotor.RunMode.RUN_TO_POSITION);
      arm.setPower(0.5);
            } 
```
{% endcode %}

{% hint style="warning" %}
Note: the code above was given a file name `Target Position if/else if` this code will be referenced again.&#x20;
{% endhint %}

{% hint style="info" %}
Recall that the target position dictates which direction the motor moves, taking over the directionality control from `arm.setPower();` so both blocks can be set to a positive value since they will control the speed.&#x20;
{% endhint %}

If you try running this code you may notice that the arm oscillates in the 90 degree position. When this behavior is present you should also notice the telemetry output for the encoder counts fluctuating. `RUN_TO_POSITION` is a **Closed Loop Control**, which means that if the arm does not perfectly reach the target position, the motor will continue to fluctuate until it does. When motors continue to oscillate and never quite reach the target position this may be a sign that the factors determining tolerances and other aspects of the closed loop are not tuned to this particular motor or mechanism. There are ways to tune the motor, but for now we want to focus on working with the arm and expanding on how limits and positions work with regards to the mechanism.&#x20;

### Calculating Target Position

In the initial introduction to run to position, you worked through the calculations needed to convert the ticks per rotation of a motor into ticks per mm moved. Now we want to focus on how to convert ticks per rotation of the motor to ticks per degree moved. From the previous section you should have a rough estimate of the amount of ticks you need to get to the 90 degree position. The goal of this section is to work through how to get a more exact position.&#x20;

To start you will need some of the same variables we used in [Encoder Navigation](robot-navigation-onbot-java/encoder-navigation-onbot.md#converting-encoder-ticks-to-a-distance):

#### Ticks per Revolution

Recall, that ticks per revolution of the encoder shaft is different than the ticks per revolution of the shaft that is controlling a mechanism. We saw this in the [Encoder Navigation](robot-navigation-blocks/encoder-navigation-blocks.md#basics-of-programming-with-encoders) section when the ticks per revolution at the motor was different from the ticks per revolution of the wheel. As motion is transmitted from a motor to a mechanism, the resolution of the encoder ticks changes.&#x20;

{% hint style="info" %}
For more information on the effect of motion transmission across a mechanism check out the [Compound Gearing](https://docs.revrobotics.com/duo-build/actuators/gears/gears-advanced#compound-gearing) section.
{% endhint %}

The amount of ticks per revolution of the encoder shaft is dependent on the motor and encoder. Manufacturers of motors with built-in encoders will have information on the amount of ticks per revolution.

{% hint style="info" %}
Visit the manufacturers website for your motor or encoders for more information on encoder counts. For HD Hex Motors or Core Hex Motors visit the [Motor](https://docs.revrobotics.com/duo-build/actuators/motors) documentation.&#x20;
{% endhint %}

In the [Core Hex Motor specifications ](https://docs.revrobotics.com/duo-build/actuators/motors/core-hex-motor#product-specs)there are two different Encoder Counts per Revolution numbers:

* At the motor - 4 counts/revolution
* At the output - 288 counts/revolution

At the motor is the number of encoder counts on the shaft that encoder is on. This number is equivalent to the 28 counts per revolution we used for the HD Hex Motor.  The 288 counts "at the output" accounts for the change in resolution after the motion is transmitted from the motor to the built in 72:1 gearbox. Lets use the 288 as ticks per revolution so that we do not have to account for the gearbox in our total gear reduction variable.&#x20;

#### Total Gear Reduction

Since we built the the gear reduction from the motor gearbox into the ticks per revolution the main focus of this section is calculating the gear reduction of the arm joint. The motor shaft drives a 45 tooth gear that transmits motion to a 125 tooth gear. The total gear ratio is 125T:45T. To calculate the gear reduction for this gear train, we can simply divide 125 by 45.&#x20;

$$
\frac{125}{45} = 2.777778
$$

To summarize, for the Class Bot V2 the following information is true:&#x20;

|                      |           |
| -------------------- | --------- |
| Ticks per revolution | 288 ticks |
| Total gear reduction | 2.777778  |

Now that we have this information lets create two constant variables:&#x20;

* `COUNTS_PER_MOTOR_REV`
* `GEAR_REDUCTION`

{% hint style="info" %}
The common naming convention for constant variables is known as CONSTANT\_CASE, where the variable name is in all caps and words are separated by and underscore.&#x20;
{% endhint %}

Add the `COUNTS_PER_MOTOR_REV` and `GEAR_REDUCTION`variables to the op mode beneath where the hardware variables are created.&#x20;

```java
public class HelloRobot_ArmControl extends LinearOpMode {
    private DcMotor arm;
    
    static final double     COUNTS_PER_MOTOR_REV    = 288; 
    static final double     GEAR_REDUCTION    = 2.7778;   
```

Now that these two variables have been defined, we can use them to calculate two other variables: the amount of encoder counts per rotation of the 125T driven gear and the number of counts per degree moved.

Calculating counts per revolution of the 125T gear (or `COUNTS_PER_GEAR_REV`)is the same formula used in [Encoder Navigation](robot-navigation-onbot-java/encoder-navigation-onbot.md#circumference-of-the-wheel) for our`COUNTS_PER_WHEEL_REV`variable. So to get this variable we can multiple`COUNTS_PER_MOTOR_REV` by `GEAR_REDUCTION`.

```java
static final double  COUNTS_PER_GEAR_REV    = COUNTS_PER_MOTOR_REV * GEAR_REDUCTION;
```

To calculate the number of counts per degree or moved or `COUNTS_PER_DEGREE`divide the `COUNTS_PER_GEAR_REV`variable by 360.&#x20;

```java
static final double     COUNTS_PER_DEGREE    = COUNTS_PER_GEAR_REV/360;
```

Add both these variables to the op mode.

```java
public class HelloRobot_ArmControl extends LinearOpMode {
    private DcMotor arm;
    
    static final double     COUNTS_PER_MOTOR_REV    = 288; 
    static final double     GEAR_REDUCTION    = 2.7778;   
    static final double     COUNTS_PER_GEAR_REV    = COUNTS_PER_MOTOR_REV * GEAR_REDUCTION;
    static final double     COUNTS_PER_DEGREE    = COUNTS_PER_GEAR_REV/360;
```

Finally we need to create a non-constant variable that will act as our position. Create a variable called `armPosition` above the `waitForStart();` command.

```java
public void runOpMode() {
        arm = hardwareMap.get(DcMotor.class, "arm");
        
        int armPosition;
        
        waitForStart();
```

Add this variable to the `if(gaempad1.dpad_up)` section of the `Target Position if/else if`statement, as this section dictates the 90 degree position. To get to the 90 degree position, the arm needs to move roughly 45 degrees. Set arm position equal to `COUNTS_PER_DEGREE`times 45.&#x20;

{% hint style="info" %}
Recall that `setTargetPosition()`requires an integer to be its parameter. When defining `armPosition` remember to add the line `(int)` in front of the double variable. However, you need to be cautious of potential rounding errors. Since `COUNTS_PER_MM`is part of an equation it is recommended that you convert to an integer after the result of the equation is found.&#x20;

```java
armPosition = (int)(COUNTS_PER_DEGREE * 45);
```
{% endhint %}

```java
while (opModeIsActive()) {

   if(gamepad1.dpad_up){
         armPosition = (int)(COUNTS_PER_DEGREE * 45);
         arm.setTargetPosition(83);
         arm.setMode(DcMotor.RunMode.RUN_TO_POSITION);
         arm.setPower(0.4);
                 }
```

Set target position to `armPostion`.

```java
if(gamepad1.dpad_up){
     armPosition = (int)(COUNTS_PER_DEGREE * 45);
     arm.setTargetPosition(armPosition);
     arm.setMode(DcMotor.RunMode.RUN_TO_POSITION);
     arm.setPower(0.4);
            }
else if (gamepad1.dpad_down){
      arm.setTargetPosition(0);
      arm.setMode(DcMotor.RunMode.RUN_TO_POSITION);
      arm.setPower(0.4);
            } 
```

{% hint style="warning" %}
We could change what `armPosition` is equal to in the `gamepad1.dpad_down` portion of the `if/else if` statement such as:&#x20;

```java
else if (gamepad1.dpad_down){
      armPosition = (int)(COUNTS_PER_DEGREE * 0);
      arm.setTargetPosition(armPosition);
      arm.setMode(DcMotorEx.RunMode.RUN_TO_POSITION);
      arm.setPower(0.4);
            } 
```

In this case we would consistently redefine `armPosition` to match the needs of whatever positions we want to create. Since our only two positions at the moment are our starting position and our 90 degree position it isn't necessary However, it is a good practice to create a variable in situations like this. If we want to add another position later, we can easily edit the variable to fit our needs.
{% endhint %}

## Using Limits to Control Range of Motion&#x20;

In the previous sections you worked on some of the building blocks for restricting an arms range of motion. From those sections you should have the foundation you need to perform basic arm control. However, there are some other creative ways you can use encoder positions and limits to expand the control you have over your arm.&#x20;

This section will cover two additional types of control. The first type of control we will explore is the idea of **soft limits**. In the [Adding a Limit Switch](arm-control-onbot-java.md#adding-a-limit-switch) section we discuss the concept of physical limits of a mechanism however, there may be times you need to limit the range of motion of an arm without installing a physical limit. To do this position based code can be used to create a range for the arm.&#x20;

Once you have a basic idea of how to create soft limits, we will explore how to use a limit switch (like a touch sensor) to reset the range of motion. This type of control reduces the risk of getting stuck outside of your intended range of motion, which can affect the expected behavior of your robot.&#x20;

To set the soft limits we will use some of the basic logic we established in previous sections, with some edited changes. Start with a `Basic Op Mode` and add the constant variables from the [Calculating Target Position](arm-control-onbot-java.md#calculating-target-position) section to the op mode.&#x20;

```java
@TeleOp

public class Basic extends LinearOpMode {
    private DcMotor  arm;

    static final double     COUNTS_PER_MOTOR_REV    = 288; 
    static final double     GEAR_REDUCTION    = 2.7778;   
    static final double     COUNTS_PER_GEAR_REV    = COUNTS_PER_MOTOR_REV * GEAR_REDUCTION;
    static final double     COUNTS_PER_DEGREE    = COUNTS_PER_GEAR_REV/360;
    
    @Override
    public void runOpMode() {
        arm = hardwareMap.get(DcMotor.class, "arm");
        
        
        waitForStart();
    
        while (opModeIsActive()) {
            telemetry.addData("Status", "Running");
            telemetry.update();

        }
    }
}
```

Next we need to create our upper and lower limits. Create two new integer variables one called `minPosition` and one called `maxPosition`. Add both of these to the in the initialization section of the op mode above the `waitForStart()`; command.&#x20;

```java
public void runOpMode() {
        arm = hardwareMap.get(DcMotor.class, "arm");
        
        int minPostion;
        int maxPosition;
        waitForStart();
    
```

For now we want the `minPosition` set as our starting position and the `maxPosition` set to our 90 degree position. Set `minPosition`equal to 0 and set `maxPosition`equal to`COUNTS_PER_DEGREE` times 45 .&#x20;

{% hint style="info" %}
Remember you need to make a data type conversion!
{% endhint %}

```java
int minPostion = 0;
int maxPosition = (int)(COUNTS_PER_DEGREE *45);
```

An `if/else if` statement needs to be added to control the arm, for this we can use the same basic logic we use in the [Basics of Programming and Arm](arm-control-onbot-java.md#basics-of-programming-an-arm).&#x20;

```java
while(opModeIsActive()){
     if(gamepad1.dpad_up){
            arm.setPower(0.5);         
            }
     else if (gamepad1.dpad_down){
            arm.setPower(-0.5); 
            }   
     else { 
            arm.setPower(0); 
            }   
     } 
```

To set the limit we need to edit our `if/else if`statement so that the limits are built in. If **** `DpadUp`is selected and the position of the arm is less than the `maxPosition` then the arm will move to the `maxPosition`. If **** `DpadDown` is selected and the position of the is greater that the `minPosition` then the arm will move towards the `minPosition`.&#x20;

```java
while (opModeIsActive()) {
    if (gamepad1.dpad_up && arm.getCurrentPosition() < maxPosition) {
            arm.setPower(0.5);
            } 
    else if (gamepad1.dpad_down && arm.getCurrentPosition() > minPosition) {
            arm.setPower(-0.5);
            } 
    else {
            arm.setPower(0);
            }
    }
```

{% hint style="success" %}
The current code configuration will stop the motor at any point that the conditions to power the motor are not met. Depending to factors like the weight of the mechanism and any load that it is bearing, when the motor stops the arm may drop below the `maxPosition`.  Take time to test out the code and confirm that it behaves in the way you expect it to.&#x20;
{% endhint %}

#### Overriding Limits

One of the benefits of having a soft limit is being able to exceed that limit. Since encoders zero tick position is determined by the position of the arm when the Control Hub powers on; if attention is not payed to what position the arm is on power up the range of motion of the arm is affected. For instance, if we have to reset the Control Hub while the arm is in the 90 degree position, the 90 degree position is equal to 0 encoder ticks. One way around this is to create an override for the range of motion.&#x20;

There are a few different ways an override of sorts can be created, in our case we are going to use the a button and touch sensor to help reset our range.&#x20;

Start by editing the `if/else if` statement  to add another `else if`  condition. Use the line `gamepad1.a` as the condition. Add a the line `arm.setPower(-0.5);` as the action item.

```java
while (opModeIsActive()) {
    if (gamepad1.dpad_up && arm.getCurrentPosition() < maxPosition) {
            arm.setPower(0.5);
            } 
    else if (gamepad1.dpad_down && arm.getCurrentPosition() > minPosition) {
            arm.setPower(-0.5);
            } 
    else if(gamepad1.a){
            arm.setPower(-0.5);
    else {
            arm.setPower(0);
            }
    }
```

Now that we have this change in place, when the `a` button is pressed the arm will move toward the starting position. When the arm reaches and presses the touch sensor we want to`STOP_AND_RESET_ENCODER` .

We can create another `if` statement that focuses on performing this stop and reset when the Touch Sensor is pressed. Since the Touch Sensor reports `true` when its not pressed and `false` when it is, we will need to use the **logical not operator** `!`.

{% hint style="info" %}
The **not operator** `!` can be used in conditional binary statements when you need inverse whether something is `true` of `false`. For instance, an `if` statement activates when something is true, but when `touch.getState();` reports `true` it is not pressed. In our case we want this if statement to activate when the Touch Sensor is pressed thus we need to use the not operator.&#x20;
{% endhint %}

```java
if (!touch.getState()) {
          arm.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
        }
```

So, if the Touch Sensor returns `false` (or is pressed) the motor run mode `STOP_AND_RESET_ENCODER`will be activated causing the motor encoder to reset to 0 ticks.&#x20;

Now that this code is done, try testing it!&#x20;

```java
@TeleOp

public class HelloRobot_ArmControl extends LinearOpMode {
    private DcMotor arm;
    private Servo claw;
    private Gyroscope imu;
    private DcMotor leftmotor;
    private DcMotor rightmotor;
    private DigitalChannel touch;
    
    static final double     COUNTS_PER_MOTOR_REV    = 288; 
    static final double     GEAR_REDUCTION    = 2.7778;   
    static final double     COUNTS_PER_GEAR_REV    = COUNTS_PER_MOTOR_REV * GEAR_REDUCTION;
    static final double     COUNTS_PER_DEGREE    = COUNTS_PER_GEAR_REV/360;

    

    @Override
    public void runOpMode() {
        arm = hardwareMap.get(DcMotor.class, "arm");
        claw = hardwareMap.get(Servo.class, "claw");
        imu = hardwareMap.get(Gyroscope.class, "imu");
        leftmotor = hardwareMap.get(DcMotor.class, "leftmotor");
        rightmotor = hardwareMap.get(DcMotor.class, "rightmotor");
        touch = hardwareMap.get(DigitalChannel.class, "touch");
        
        int minPostion = 0;
        int maxPosition = (int)(COUNTS_PER_DEGREE *45);
        
        waitForStart();
            
        // run until the end of the match (driver presses STOP)
        while (opModeIsActive()) {
            if (gamepad1.dpad_up && arm.getCurrentPosition() < maxPosition) {
                arm.setPower(0.5);
                    } 
            else if (gamepad1.dpad_down && arm.getCurrentPosition() > minPosition) {
                arm.setPower(-0.5);
                    } 
            else if (gamepad1.a) {
                arm.setPower(-0.5);
                    } 
            else {
                arm.setPower(0);
                }
            if (!touch.getState()) {
              arm.setMode(DcMotor.RunMode.STOP_AND_RESET_ENCODER);
                    }
        telemetry.addData("Arm Test", arm.getCurrentPosition());
        telemetry.update(); 
        }
    }
}
```
