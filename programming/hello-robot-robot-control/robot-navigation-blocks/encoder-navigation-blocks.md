# Encoder Navigation - Blocks

In the previous section you learned about how to use Elapsed Time to allow your robot to navigate the world around it autonomously. When starting out many of the robot actions can be accomplished by turning on a motor for a specific amount of time. Eventually, these time-based actions may not be accurate or repeatable enough. Environmental factors, such as the state of battery charge during operation and mechanisms wearing in through use, can all affect time-based actions. Fortunately, there is a way to give feedback to the robot about how it is operating by using sensors; devices that are used to collect information about the robot and the environment around it. &#x20;

With Elapsed Time, in order to get the robot to move to a specific distance, you had to estimate the amount of time and the percentage of duty cycle needed to get from point a to point b. However, the REV motors come with built in encoders, which provide feedback in the form of ticks ( or counts) per revolution of the motor. The information provided by the encoders can be used to move the motor to a target position, or a target distance.&#x20;

Moving the motors to a specific position, using the encoders, removes any potential inaccuracies or inconsistencies from using Elapsed Time. The focus of this section is to move the robot to a target position using encoders.&#x20;

{% hint style="warning" %}
There are two articles in that go through the basics of Encoders. [Using Encoders](../../using-encoders.md) goes through the basics of the different types of motor modes, as well as a few application examples of using these modes in code. In this section we will focus on using `RUN_TO_POSITION`.

The other article, [Encoders](../../../sensors/encoders/), focuses on the general functionality of an encoder.&#x20;

It is recommended that you review both articles before moving on with this guide.&#x20;
{% endhint %}

## Basics of Programming with Encoders

Start by creating a basic op mode called HelloRobot\_EncoderAuton.&#x20;

{% hint style="warning" %}
When creating an op mode a decision needs to be made on whether or not to set it to autonomous mode. For applications under 30 seconds, typically required for competitive game play changing the op mode type to autonomous is recommended. For applications over 30 seconds, setting the code to the autonomous op mode type will limit your autonomous code to 30 seconds of run time. If you plan on exceeding the 30 seconds built into the SDK, keeping the code as a teleoperated op mode type is recommended.&#x20;

For information on how op modes work please visit the [Introduction to Programming ](../../hello-robot-introduction-to-programming.md#op-modes)section.&#x20;

For more information on how to change the op mode type check out the[ Test Bed - Blocks ](../../hello-robot-test-bed/test-bed-blocks.md#creating-an-op-mode)section. &#x20;
{% endhint %}

Add the __ <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW6L1g4Y8GSBICwwFHF%2FMotor%20-%20rightmotorDirection.svg?alt=media&#x26;token=67d93d39-a4fd-441f-ae5d-6d323d657c6c" alt="" data-size="original"> block to the op mode under the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVRzzz2RWu0i_oNzqo3%2FComment%20-%20Put%20intialization%20blocks.svg?alt=media&#x26;token=5b100e29-9c67-4bb3-be74-0d35d452cb76" alt="" data-size="original">.This will change the direction of the rotation of the right motor to be the same direction as the left motor.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYCCC1UjXUUSq0ujDmk%2F-MYGTZudXy9wP6X\_lX0B%2FEncoder%20-%20adding%20reverse.svg?alt=media\&token=bb44ea59-7115-49e1-915b-cc8b451f03c0)

{% hint style="info" %}
For more information on the directionality of motor check out the [Basics of Programming Drivetrains](./#basics-of-programming-drivetrains) section.&#x20;
{% endhint %}

Recall from [Using Encoders](../../using-encoders.md) that using `RUN_TO_POSITION` mode requires a three step process. The first step is setting target position. To set target position, grab the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYCCC1UjXUUSq0ujDmk%2F-MYGpj87ESnvB0Mbaqbo%2FDual%20Motoer%20-%20set%20position.svg?alt=media&#x26;token=8e0a9be7-426d-4d85-8a69-cc1682dd1d44" alt="" data-size="original">  block and add it to the op mode under the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWPfpmWuWVqh1EweC06%2FComment%20-%20Put%20loop%20blocks.svg?alt=media&#x26;token=f8741193-0083-4e16-8d7c-0ca7277c2dde" alt="" data-size="original"> comment. To get a target position that equates to a target distance requires so calculations, which will be covered later.  For now, set target position to 1000 ticks.&#x20;

{% hint style="info" %}
When there are multiple of the same type of variable (such as multiple Dc Motor variables) the variable specific blocks will choose a default variable based on alphabetical order. For this example Op Mode Dc Motor blocks will default to the arm variable. Click the arrow next to the motor name to change the arm motor variable to the rightmotor variable. Use the variable drop down menu on the block to change from arm to rightmotor.![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVNdPNK1aoHjru6tzHV%2FDual%20Motor%20-%20Variable%20Drop%20Down%20Menu.svg?alt=media\&token=3cb22ad9-52e4-42e1-8e29-95650ac60e79)
{% endhint %}

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYCCC1UjXUUSq0ujDmk%2F-MYGfhk2fqH-\_OQYxyxd%2FEncoder%20-%20First%20Target%20Position.svg?alt=media\&token=e19ee14c-466a-4663-b995-4ace25da974b)

The next step is to set both motors to the `RUN_TO_POSITION` mode. Place the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYCCC1UjXUUSq0ujDmk%2F-MYGpV5c0A6R6UP0YKgC%2FDual%20Motor%20-%20set%20mode%20to%20RUNTO.svg?alt=media&#x26;token=d69c8c3e-35f2-4f64-8698-2fccba89ee01" alt="" data-size="original"> block beneath the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYCCC1UjXUUSq0ujDmk%2F-MYGq13GHps2CyeLWbZt%2FDual%20Motor%20-%20target%20position%20to%201000.svg?alt=media&#x26;token=6c977583-8da8-43a2-848e-0b09583f63d4" alt="" data-size="original"> block.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYCCC1UjXUUSq0ujDmk%2F-MYGqJNRD6CEONRGPj\_d%2FEncoder%20-%20add%20run%20to%20position.svg?alt=media\&token=9398cfbc-00b5-4456-8d96-96752a7db26a)

The main focus of the three step process is to set a target, tell the robot to move to that target, and at what speed (or velocity) the robot should get to that target. Normally, the recommended next step is to calculate velocity and set a target velocity based on ticks. However, this requires quite a bit of math to find the appropriate velocity. For testing purposes, its more important to make sure that the main part of the code is working before getting too deep into the creation of the code. Since the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVrZYOdMO43YdZ0zxXy%2F-MVwMw5ZpQkhFNu3fZwH%2FDual%20Motor%20-%20set%20to%20positive.svg?alt=media&#x26;token=bec685f7-b263-4268-a87e-d2b24ac24bbe" alt="" data-size="original"> function was covered in previous sections and will communicate to the system what relative speed (or in this case duty cycle) is needed to get to the target, this can be used in the place of velocity for now.&#x20;

&#x20;Add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVrZYOdMO43YdZ0zxXy%2F-MVwRA9auYOOqnGmzAX7%2FDual%20Motor%20-%20set%20to%20positive.svg?alt=media&#x26;token=ed171c16-63c4-4531-89f3-ed93ce36dbae" alt="" data-size="original"> block to the op mode beneath the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYCCC1UjXUUSq0ujDmk%2F-MYGpV5c0A6R6UP0YKgC%2FDual%20Motor%20-%20set%20mode%20to%20RUNTO.svg?alt=media&#x26;token=d69c8c3e-35f2-4f64-8698-2fccba89ee01" alt="" data-size="original"> block. Change the duty cycle (or power) of both motors to 0.8, instead of 1.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYCCC1UjXUUSq0ujDmk%2F-MYHEQz4PuZ4H60Qmc8-%2FEncoder%20-%20add%20set%20power%20for%20now.svg?alt=media\&token=0b2e2da0-20d5-4d5f-8ad4-6980e9c76fc5)

Now that all three `RUN_TO_POSITION` steps have been added to the code the code can be tested. However, if you want to wait for the motor to reach its target position before continuing in your program, you can use a while loop that checks if the motor is busy (not yet at its target).  For this program lets edit the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYCCC1UjXUUSq0ujDmk%2F-MYLc6c3oNSncufi2_U_%2FLoops%20-%20While%20(opModeIsActive)%20encoder%20opmode.svg?alt=media&#x26;token=8e16a84b-8ef9-467a-8c15-8089d4bd584f" alt="" data-size="original"> block.&#x20;

{% hint style="info" %}
Recall that, within a linear op mode, a while loop must always have the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYCCC1UjXUUSq0ujDmk%2F-MYLoJ7socGKL3TYebta%2FClasses%20-%20Call%20Op%20mode%20active%20(encoder).svg?alt=media&#x26;token=5b6ddd85-d9f8-45f4-8378-90dacac89e53" alt="" data-size="line"> Boolean as a condition. This condition ensures that the while loop will terminate when the stop button is pressed.&#x20;
{% endhint %}

&#x20;Grab an <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW9yJdVdzRolyWei1gK%2FLogic%20-%20and.svg?alt=media&#x26;token=129d69e5-1d08-4d91-8eb6-77ee65a3458b" alt="" data-size="original"> block from the logic menu and add it to the while loop. On the left side of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW9yJdVdzRolyWei1gK%2FLogic%20-%20and.svg?alt=media&#x26;token=129d69e5-1d08-4d91-8eb6-77ee65a3458b" alt="" data-size="original"> block add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYCCC1UjXUUSq0ujDmk%2F-MYLqJ0o25l0qXexhQAN%2FMotor%20-%20is%20busy.svg?alt=media&#x26;token=711996ba-e85c-428c-8661-c63dff1b3bde" alt="" data-size="original">block. On the right side add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYpSPN_7dbYCVxvOxEL%2F-MYprDjxWilLiLPAqPut%2FMotor%20-%20roghtmotor%20is%20busy.svg?alt=media&#x26;token=fb46f071-0f9c-4447-9ef9-af50dd1e4182" alt="" data-size="original"> block.&#x20;

Embed the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYpSPN_7dbYCVxvOxEL%2F-MYprs4f0C8BmAp0-ukL%2FCombo%20-%20left%20and%20right%20are%20busy.svg?alt=media&#x26;token=04d747f4-c4f7-40e9-a4bb-da9e574ebb6f" alt="" data-size="original"> in another <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW9yJdVdzRolyWei1gK%2FLogic%20-%20and.svg?alt=media&#x26;token=129d69e5-1d08-4d91-8eb6-77ee65a3458b" alt="" data-size="original"> block. Place the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYpSPN_7dbYCVxvOxEL%2F-MYprs4f0C8BmAp0-ukL%2FCombo%20-%20left%20and%20right%20are%20busy.svg?alt=media&#x26;token=04d747f4-c4f7-40e9-a4bb-da9e574ebb6f" alt="" data-size="original"> on the right side of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW9yJdVdzRolyWei1gK%2FLogic%20-%20and.svg?alt=media&#x26;token=129d69e5-1d08-4d91-8eb6-77ee65a3458b" alt="" data-size="original"> block. On the left side add the<img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYCCC1UjXUUSq0ujDmk%2F-MYLoJ7socGKL3TYebta%2FClasses%20-%20Call%20Op%20mode%20active%20(encoder).svg?alt=media&#x26;token=5b6ddd85-d9f8-45f4-8378-90dacac89e53" alt="" data-size="line"> block.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYpSPN\_7dbYCVxvOxEL%2F-MYppB5XKKHCxlnzxMd6%2FEncoder%20-%20changing%20while%20loop.svg?alt=media\&token=0b6bdd36-9bfa-4b9b-b1cb-a42f2ad09a43)

{% hint style="info" %}
Right now the while loop is waiting for the right and left motors to reach their respective targets. There may be occasions when you want to wait for both motors to reach their target position, in this case the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWB9-FbRpvUKsRz3Tbi%2Flogic%20-%20or%20block.svg?alt=media&#x26;token=28de91ba-b844-4003-9c38-0a19d6e70e17" alt="" data-size="original"> can be used.

&#x20;<img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYpSPN_7dbYCVxvOxEL%2F-MYpwslGYPymyht-7Rwu%2Fcombo%20-%20right%20left%20are%20busy.svg?alt=media&#x26;token=14b6604f-c1c3-4857-a711-1cd7e24bdf75" alt="" data-size="original">
{% endhint %}

{% hint style="success" %}
Save and run the op mode two times in a row. Does the robot move as expected the second time?

Try turning the Control Hub off and then back on. How does the robot move?
{% endhint %}

In the [Basic Encoder Concepts ](../../using-encoders.md#basic-encoder-concepts)section, it is clarified that ell encoder ports start at 0 ticks when the Control Hub is turned on. Since you did not turn off the Control Hub in between runs, the second time you ran the op mode the motors were already at, or around, the target position. When you run a code, you want to ensure that certain variables start in a known state. For the encoder ticks, this can be achieved by setting the mode to <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYCCC1UjXUUSq0ujDmk%2F-MYLu6oXY0GtRH6-WlwJ%2FDual%20Motor%20-%20stop%20and%20reset%20encoder.svg?alt=media&#x26;token=b3fadb6e-e1a9-4b50-8ca1-7ab052a2b2fa" alt="" data-size="original"> . Add this block to the op mode in the initialization section. Each time the op mode is initialized, the encoder ticks will be reset to zero.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYpSPN\_7dbYCVxvOxEL%2F-MYq-JRMtJ4GgcDvmoiF%2FEncoder%20-%20add%20stop%20and%20reset.svg?alt=media\&token=05aa57b0-66b0-439e-9bdb-46c7e8cecbbc)

{% hint style="info" %}
For more information on the motor mode `STOP_AND_RESET_ENCODERS`check out the [STOP\_AND\_RESET\_ENCODERS](../../using-encoders.md#stop\_and\_reset\_encoder-mode) section of the Using Encoders guide.&#x20;
{% endhint %}

### Converting Encoder Ticks to a Distance&#x20;

In the previous section, the basic structure needed to use `RUN_TO_POSITION`was created. The placement of<img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYCCC1UjXUUSq0ujDmk%2F-MYGq13GHps2CyeLWbZt%2FDual%20Motor%20-%20target%20position%20to%201000.svg?alt=media&#x26;token=6c977583-8da8-43a2-848e-0b09583f63d4" alt="" data-size="original">within the code, set the target position to 1000 ticks. What is the distance from the starting point of the robot and the point the robot moves to after running this code?&#x20;

Rather than attempt to measure, or estimate, the distance the robot moves, the encoder ticks can be converted from amount of ticks per revolution of the encoder to how many encoder ticks it takes to move the robot a unit of distance, like a millimeter or inch. Knowing the amount of ticks per a unit of measure allows you to set a specific distance. For instance, if you work through the conversion process and find out that a drivetrain takes 700 ticks to move an inch, this can be used to find the total number of ticks need to move the robot 24 inches.&#x20;

{% hint style="warning" %}
Reminder that the basis for this guide is the [Class Bot V2](https://docs.revrobotics.com/duo-build/ftc-starter-kit-class-bot). The REV DUO Build System is a metric system. Since part of the conversion process references the diameter of the wheels, this section will convert to ticks per mm.
{% endhint %}

When using encoders built into motors, converting from ticks per revolution to ticks per unit of measure moved requires the following information:

* Ticks per revolution of the encoder shaft
* Total gear reduction on the motor
  * Including gearboxes and motion transmission components like gears, sprockets and chain, or belts and pulleys
* Circumference of the driven wheels

#### Ticks per Revolution

The amount of ticks per revolution of the encoder shaft is dependent on the motor and encoder. Manufacturers of motors with built-in encoders will have information on the amount of ticks per revolution. For HD Hex Motors the encoder counts 28 ticks per revolution of the motor shaft.&#x20;

{% hint style="info" %}
Visit the manufacturers website for your motor or encoders for more information on encoder counts. For HD Hex Motors or Core Hex Motors visit the [Motor](https://docs.revrobotics.com/duo-build/actuators/motors) documentation.&#x20;
{% endhint %}

#### Total Gear Reduction

Since ticks per revolution of the encoder shaft is before any gear reduction calculating the total gear reduction is needed. This includes the gearbox and any addition reduction from motion transmission components. To find the total gear reduction use the [Compound Gearing formula](https://docs.revrobotics.com/duo-build/actuators/gears/gears-advanced#compound-gearing).&#x20;

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

Add the variables to the initialization section of the op mode.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYpSPN\_7dbYCVxvOxEL%2F-MYq2kD-rv3X1dFg6GCD%2FEncoder%20-%20add%20first%20three%20constant%20variables.svg?alt=media\&token=b5a4eb09-1d5a-46ef-ac1e-2d4fed43b126)

Once the variables are created and added to the op mode, use the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYQpFaVyN6OAN2wLm6r%2F-MYRB7rWtI2jshN4W7LJ%2FMath%20-%200.svg?alt=media&#x26;token=99ad04a5-2f5e-4c97-a3f1-aa6471df73b2" alt="" data-size="original"> blocks to set the variables to the respective values. For `WHEEL_CIRCUMFERENCE_MM`  a combination of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYQpFaVyN6OAN2wLm6r%2F-MYRS32ax0_5fhPWNou9%2FMath%20-%20multiplication.svg?alt=media&#x26;token=76bfe431-53f9-4310-9164-47faeef5a26b" alt="" data-size="original"> , <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYQpFaVyN6OAN2wLm6r%2F-MYRB7rWtI2jshN4W7LJ%2FMath%20-%200.svg?alt=media&#x26;token=99ad04a5-2f5e-4c97-a3f1-aa6471df73b2" alt="" data-size="original"> , and<img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYQpFaVyN6OAN2wLm6r%2F-MYRSB17mEeOLwbUp2y2%2FMath%20-%20pi%20block.svg?alt=media&#x26;token=4cb365a7-a4b0-4fe7-a0cb-d1727929b12e" alt="" data-size="original"> blocks to get the circumference of the wheel. The&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYQpFaVyN6OAN2wLm6r%2F-MYRP6ZUXJNSFde2UzFX%2FEncoder%20-%20adding%20numbers%20to%20the%20first%20three.svg?alt=media\&token=c2901d94-6d68-4db3-a5b5-1ae1a15d30ef)

Now that these three variables have been defined, we can use them to calculate two other variables: the amount of encoder counts per rotation of the wheel and the number of counts per mm that the wheel moves.&#x20;

To calculate counts per wheel revolution multiple`COUNTS_PER_MOTOR_REV` by `DRIVE_GEAR_REDUCTION` Use the following formula:

$$
y = a
*b
$$

Where,&#x20;

* $$a$$ = `COUNTS_PER_MOTOR_REV`
* $$b$$ = `DRIVE_GEAR_REDUCTION`&#x20;
* $$y$$ = `COUNTS_PER_WHEEL_REV`

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

{% hint style="warning" %}
`COUNTS_PER_WHEEL_REV`will be created as a separate variable from`COUNTS_PER_MM` as it is used in calculating a target velocity.&#x20;
{% endhint %}

Create these variables in Blocks and add then to the op mode under the other constant variables.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYpSPN\_7dbYCVxvOxEL%2F-MYq5Zopxu3g4mMRcRrf%2FEncoders%20-%20adding%20next%20two%20variables.svg?alt=media\&token=adddf546-58c8-4618-ba74-9af4c551e626)

Again math blocks need to be used to define these variables. Lets start with the `COUNTS_PER_WHEEL_REV`  variable. Add a <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYQpFaVyN6OAN2wLm6r%2F-MYRS32ax0_5fhPWNou9%2FMath%20-%20multiplication.svg?alt=media&#x26;token=76bfe431-53f9-4310-9164-47faeef5a26b" alt="" data-size="original"> to the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYQpFaVyN6OAN2wLm6r%2F-MYRfuLihTonvd67Sk4b%2FVariavble%20-%20COUNT_PER%20WHEEL%20REV.svg?alt=media&#x26;token=c0e85fc9-8dc2-4fe0-a0e4-8d32e1f311ad" alt="" data-size="original"> block. Add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYRgR43ABOUSGb1f8WZ%2F-MYeigphTtcNkGuZlxOg%2FVariable%20-%20counts%20per%20motor%20rev.svg?alt=media&#x26;token=72582836-0ff4-4093-819a-0cc7718025d4" alt="" data-size="original"> and <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYRgR43ABOUSGb1f8WZ%2F-MYeikxKcR2ab3l-siE2%2FVariable%20-%20drive%20gear%20reduction.svg?alt=media&#x26;token=c52353c7-2a92-48ea-92a2-4e407170b421" alt="" data-size="original">blocks to either side of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYQpFaVyN6OAN2wLm6r%2F-MYRS32ax0_5fhPWNou9%2FMath%20-%20multiplication.svg?alt=media&#x26;token=76bfe431-53f9-4310-9164-47faeef5a26b" alt="" data-size="original"> block.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYRgR43ABOUSGb1f8WZ%2F-MYek67Gj5FUmCoaeaUn%2FVariable%20-%20setting%20wheel%20rev.svg?alt=media\&token=fd34a44b-5229-48a9-b5e3-866aeeb6ea6f)

Since `COUNTS_PER_WHEEL_REV`  has been calculated it can be used to calculate `COUNTS_PER_MM` add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYRgR43ABOUSGb1f8WZ%2F-MYepPimZMwCPPARot8P%2FMath%20-%20division.svg?alt=media&#x26;token=53cb0fdc-cdf6-4ce0-abbd-cd3ab3f9d30d" alt="" data-size="original"> to the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYRgR43ABOUSGb1f8WZ%2F-MYeqNUzRqrbAl-CypnS%2FVariable%20-%20set%20counts%20per%20mm.svg?alt=media&#x26;token=c0e14153-93f2-4781-8583-840f4527bc70" alt="" data-size="original">. On the left side of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYRgR43ABOUSGb1f8WZ%2F-MYepPimZMwCPPARot8P%2FMath%20-%20division.svg?alt=media&#x26;token=53cb0fdc-cdf6-4ce0-abbd-cd3ab3f9d30d" alt="" data-size="original"> add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYRgR43ABOUSGb1f8WZ%2F-MYey5fLzndMDfYs7HdW%2FVariable%20-counts%20per%20wheel.svg?alt=media&#x26;token=1ff59bbd-6e23-404f-a0bd-15b37501cec6" alt="" data-size="original"> block. On the right side of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYRgR43ABOUSGb1f8WZ%2F-MYepPimZMwCPPARot8P%2FMath%20-%20division.svg?alt=media&#x26;token=53cb0fdc-cdf6-4ce0-abbd-cd3ab3f9d30d" alt="" data-size="original"> add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYeyIdN23s6PuxYRjxx%2F-MYf-5tkdwxOZ7wRXrM-%2FVariable%20-circumferenc.svg?alt=media&#x26;token=296ae9f7-5119-475f-b9a3-7eeba4fe8aeb" alt="" data-size="original"> .

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYeyIdN23s6PuxYRjxx%2F-MYf7Q7ov7Ll3ETClAK\_%2FVariable%20-%20set%20counts%20per%20mm%20to%20vairables.svg?alt=media\&token=8198265a-2ddd-4cb8-b48e-6476ebc1aecb)

Once`COUNTS_PER_WHEEL_MM` is set, this completes the conversion process, and all constant variables are set.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYeyIdN23s6PuxYRjxx%2F-MYf8yipdms5gf\_BovI0%2FEncoder%20-%20Constant%20Variables%20Complete.svg?alt=media\&token=fe259b31-7ce6-4c14-ba09-ae911f9d6faa)

### Moving to a Target Distance&#x20;

Now that you have created the constant variables needed to calculate the amount of ticks per mm moved, you can use this to set a target distance. For instance, if you would like to have the robot move forward two feet, converting from feet to millimeters and multiplying by the `COUNTS_PER_MM`will give you the amount of counts (or ticks) needed to reach that distance.&#x20;

Create two more variables called `leftTarget` and`rightTarget`. Add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYeyIdN23s6PuxYRjxx%2F-MYfarkmXxKPyNxDquzZ%2FVariables%20-%20set%20leftTarget.svg?alt=media&#x26;token=c6637dac-56cf-46cd-bdc4-fadcf7e216d3" alt="" data-size="original">and <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYeyIdN23s6PuxYRjxx%2F-MYfauhcXmBRK_CtexwM%2FVariables%20-%20set%20rightTarget.svg?alt=media&#x26;token=c3b16a3d-1f9c-4545-bd5c-486f5b242146" alt="" data-size="original"> blocks to the op mode above the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYCCC1UjXUUSq0ujDmk%2F-MYGq13GHps2CyeLWbZt%2FDual%20Motor%20-%20target%20position%20to%201000.svg?alt=media&#x26;token=6c977583-8da8-43a2-848e-0b09583f63d4" alt="" data-size="original">block.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYpSPN\_7dbYCVxvOxEL%2F-MYq8SkmxAYvBtog6emN%2FEncoder%20-%20adding%20target.svg?alt=media\&token=d99eb7b7-a21a-4b55-83c4-c11a407b4b45)

Right now the main distance factor is `COUNTS_PER_MM` , however you may want to go a distance that is in the imperial system, such as 2 feet (or 24 inches). The target distance in this case will need to be converted to mm. To convert from feet to millimeters use the following formula:

$$
d_{(mm)} = d_{(ft)} × 304.8
$$

If you convert 2 feet to millimeters, it comes out the be 609.6 millimeters. For the purpose of this guide, lets go ahead an round this to be 610 millimeters. Multiply 610 millimeters by the`COUNTS_PER_MM` variable to get the number of ticks needed to move the robot 2 feet. Since the intent is to have the robot move in a straight line, set both the `leftTarget` and `rightTarget`, to be equal to 610 \*  `COUNTS_PER_MM`

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYeyIdN23s6PuxYRjxx%2F-MYfgx\_HDJauUNJaLMqD%2FVariable%20-%20set%20target%20to.svg?alt=media\&token=2a8b9b96-e0cb-4244-9eff-579c59317ed4)

Edit the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYCCC1UjXUUSq0ujDmk%2F-MYGq13GHps2CyeLWbZt%2FDual%20Motor%20-%20target%20position%20to%201000.svg?alt=media&#x26;token=6c977583-8da8-43a2-848e-0b09583f63d4" alt="" data-size="original"> so that both motors are set to the appropriate target position. To do this add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYeyIdN23s6PuxYRjxx%2F-MYfkdJjHrXQM9Phg8gz%2FVariable%20-%20left%20target.svg?alt=media&#x26;token=a74c319c-7899-4316-b980-7faf93a1327b" alt="" data-size="original"> and <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYeyIdN23s6PuxYRjxx%2F-MYfkhOc5yahjvtzUAq2%2FVariable%20-%20right%20target.svg?alt=media&#x26;token=5b5a09bb-1a64-4829-9151-afe48cbebf32" alt="" data-size="original"> blocks to their respective motor.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYpSPN\_7dbYCVxvOxEL%2F-MYqA7DGJlthxBNbAKGy%2FEncoder%20-%20finalizing%20target.svg?alt=media\&token=2c24b98a-8f32-4fbc-8ac2-228c317ca57a)

### Setting Velocity&#x20;

Velocity is a closed loop control within the SDK that uses the encoder counts to determine the approximate power/speed the motors need to go in order to meet the set velocity. When working with encoder setting a velocity is recommended over setting a power level, as it offers a higher level of control. &#x20;

To set a velocity, its important to understand the maximum velocity in RPM your motor is capable of. For the Class Bot V2 the motors are capable of a maximum RPM of 300. With a drivetrain, you are likely to get better control by setting velocity lower than the maximum. In this case, lets set the velocity to 175 RPM&#x20;

{% hint style="info" %}
Recall that `setVelocity` is measure in ticks per second.&#x20;
{% endhint %}

Since RPM is the amount of revolutions per minute a conversion needs to be made from RPM to ticks per second. To do this divide the RPM by 60, to get the amount of rotations per second. Rotations per second can the be multiplied by `COUNTS_PER_WHEEL_REV`, to get the amount of ticks per second.&#x20;

$$
TPS = \frac{175}{60} * CPWR
$$

Create a new variable called TPS. Add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYeyIdN23s6PuxYRjxx%2F-MYfxnoZpHQV4V7dyiqS%2FVariable%20-%20set%20TPS%20to.svg?alt=media&#x26;token=49523bae-8ad5-4b97-8af8-b20edd5d61b4" alt="" data-size="original"> to the op mode under the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MWACAqNiP66tvS4fGxc%2FComment%20-%20Put%20run%20blocks%20here.svg?alt=media&#x26;token=a002379b-48fb-4d1f-a08c-e2568d142683" alt="" data-size="original"> comment block.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYpSPN\_7dbYCVxvOxEL%2F-MYqDFhpzVI9awH-haz-%2FEncoder%20-%20add%20TPS.svg?alt=media\&token=b5961ca7-856f-43b2-8a1c-4c53908b0b4c)

Add a <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYQpFaVyN6OAN2wLm6r%2F-MYRS32ax0_5fhPWNou9%2FMath%20-%20multiplication.svg?alt=media&#x26;token=76bfe431-53f9-4310-9164-47faeef5a26b" alt="" data-size="original"> block to the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYeyIdN23s6PuxYRjxx%2F-MYfxnoZpHQV4V7dyiqS%2FVariable%20-%20set%20TPS%20to.svg?alt=media&#x26;token=49523bae-8ad5-4b97-8af8-b20edd5d61b4" alt="" data-size="original"> block. On the right side of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYQpFaVyN6OAN2wLm6r%2F-MYRS32ax0_5fhPWNou9%2FMath%20-%20multiplication.svg?alt=media&#x26;token=76bfe431-53f9-4310-9164-47faeef5a26b" alt="" data-size="original"> block add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYRgR43ABOUSGb1f8WZ%2F-MYey5fLzndMDfYs7HdW%2FVariable%20-counts%20per%20wheel.svg?alt=media&#x26;token=1ff59bbd-6e23-404f-a0bd-15b37501cec6" alt="" data-size="original">. One the left side of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYQpFaVyN6OAN2wLm6r%2F-MYRS32ax0_5fhPWNou9%2FMath%20-%20multiplication.svg?alt=media&#x26;token=76bfe431-53f9-4310-9164-47faeef5a26b" alt="" data-size="original"> add the<img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYRgR43ABOUSGb1f8WZ%2F-MYepPimZMwCPPARot8P%2FMath%20-%20division.svg?alt=media&#x26;token=53cb0fdc-cdf6-4ce0-abbd-cd3ab3f9d30d" alt="" data-size="original"> block. Add the chosen RPM to the left side of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYRgR43ABOUSGb1f8WZ%2F-MYepPimZMwCPPARot8P%2FMath%20-%20division.svg?alt=media&#x26;token=53cb0fdc-cdf6-4ce0-abbd-cd3ab3f9d30d" alt="" data-size="original"> block and 60 to the right side.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYeyIdN23s6PuxYRjxx%2F-MYfzugs\_ZuQcMfIRTGE%2FCombo%20block%20-%20setting%20TPS%20to.svg?alt=media\&token=e0e406a4-a2b8-48e8-9f83-87a714af1b02)

Now that the target ticks per second has been set, swap the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYeyIdN23s6PuxYRjxx%2F-MYg1RLiF3aIU-PaJgah%2FEncoder%20-%20setpower%20.08.svg?alt=media&#x26;token=5de07247-352c-4727-bb52-966146c861a0" alt="" data-size="original">block for a <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYeyIdN23s6PuxYRjxx%2F-MYg1WJmbeYlb5XsxdAI%2FDual%20Motor%20-%20setVelocity.svg?alt=media&#x26;token=8a44a6b2-f60f-4a37-8291-d3bdf2049504" alt="" data-size="original"> block. Add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYeyIdN23s6PuxYRjxx%2F-MYg2807btHlLi-Ew5MN%2FVariable%20-%20TPS.svg?alt=media&#x26;token=311503ee-e5fe-47e7-b374-20b7b0b3ef24" alt="" data-size="original"> to both motors.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYpSPN\_7dbYCVxvOxEL%2F-MYqF1DFayHRsKHOVEVN%2FEncoder%20-%20add%20velocity%20blocks.svg?alt=media\&token=37d09c98-2ef0-4ef4-9b8b-eb74e125cda3)

With the velocity set, this is the final thing needed to complete the objective of driving in a straight line. Consider adding telemetry and other hardware components as you begin fleshing out your full autonomous code.&#x20;

### Turning the Drivetrain Using RUN\_TO\_POSITION

In the [Robot Navigation - Blocks ](./#teleoperated-driving-arcade-style)section, the mechanism of <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVrZYOdMO43YdZ0zxXy%2F-MVwRA9auYOOqnGmzAX7%2FDual%20Motor%20-%20set%20to%20positive.svg?alt=media&#x26;token=ed171c16-63c4-4531-89f3-ed93ce36dbae" alt="" data-size="original"> was discussed. <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVrZYOdMO43YdZ0zxXy%2F-MVwRA9auYOOqnGmzAX7%2FDual%20Motor%20-%20set%20to%20positive.svg?alt=media&#x26;token=ed171c16-63c4-4531-89f3-ed93ce36dbae" alt="" data-size="original"> dictates what direction and speed a motor moves in. On a drivetrain the combined direction and speed of the motors dictates whether the robot moves in forward, backwards, or turns.

In `RUN_TO_POSITION`mode the encoder counts are used instead <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVrZYOdMO43YdZ0zxXy%2F-MVwRA9auYOOqnGmzAX7%2FDual%20Motor%20-%20set%20to%20positive.svg?alt=media&#x26;token=ed171c16-63c4-4531-89f3-ed93ce36dbae" alt="" data-size="original"> of to dictate directionality of the motor. If a target position value is greater than the current position of the encoder, the motor moves forward. If the target position value is less than the current position of the encoder, the motor moves backwards

Since speed an directionality impacts how a robot turns, target position and velocity need to be edited to get the robot to turn. Consider the following code:&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MYpSPN\_7dbYCVxvOxEL%2F-MYqF6LgjPjdJZep0YBh%2FEncoder%20-%20turning%20the%20robot.svg?alt=media\&token=86aa2038-d5b1-488c-8043-5c0a11c86842)

The `rightTarget` has been changed to be a negative target position. Assuming that the encoder starts at zero due to `STOP_AND_RESET_ENCODER` this causes the robot to turn to the right. Velocity is the same for both motors. If you try running this code, you may notice that the robot pivots along its center of rotation. To get a wider turn changing the velocity so that the right motor is running at a lower velocity than the left motor. Adjust the velocity and target position as needed to get the turn you need.

{% hint style="info" %}
For more information on how direction and speed impact the movement of a robot please refer to the explanation of <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVrZYOdMO43YdZ0zxXy%2F-MVwRA9auYOOqnGmzAX7%2FDual%20Motor%20-%20set%20to%20positive.svg?alt=media&#x26;token=ed171c16-63c4-4531-89f3-ed93ce36dbae" alt="" data-size="original"> in the [Robot Navigation ](./#teleoperated-driving-arcade-style)section.
{% endhint %}
