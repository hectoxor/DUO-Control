# Robot Navigation - Blocks

## Introduction to Robot Navigation

As alluded to in the Hello Robot - Robot Control section, robot control comes in many different forms. One of the control types to consider for robots with drivetrains, is robot navigation. &#x20;

Robot navigation as a concept is dependent on the type of drivetrain and the type of operation mode. For instance, the code to control a mecanum drivetrain differs from the code used to control a differential drivetrain. There is also a difference between coding for teleoperated driving, with a gamepad, or coding for autonomous, where each movement of the robot must be defined within code.&#x20;

The following section goes through some of the basics of programming for a differential drivetrain, as well as how to set up a teleoperated arcade style drivetrain code. The concepts and logic highlighted in this section are applicable to autonomous control, including the section [Elapsed Time](elapsed-time-blocks.md).&#x20;

| Sections                                                                  | Goals of Section                                                                                                                                                                                |
| ------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Basics of Programming Drivetrains](./#basics-of-programming-drivetrains) | What to consider when [programming drivetrain motors](./#programming-drivetrain-motors) and how to apply this to an[ arcade style teleoperated control](./#teleoperated-driving-arcade-style).  |

## Basics of Programming Drivetrains

For controlling the Class Bot V2 drivetrain, being able to control two motors simultaneously is important. This is done through the **dual** motor block within Blocks. To access the **dual** motor block, at the top of the Categorize Blocks section there is a drop down menu for **Actuators**. Selecting DcMotor will drop down the options **Dual** and another drop down menu **Extended**. Select Dual to access the dual motor blocks.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MQr5KcDA2dA-neXLDAW%2F-MQrS9SWLBweIiOsJWXO%2FBlocks%20-%20where%20to%20find%20dual%20motor%20blocks.svg?alt=media\&token=f3d6572c-e3c4-49aa-9eba-0df1e930735a)

### Programming Drivetrain Motors

Add the __ <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVNpboWEAOhTj8EGLe4%2FDual%20Motor%20-%20Arm%20and%20Left%20(inline).svg?alt=media&#x26;token=fae3f82c-5dd1-4e3b-9590-138cbe778e47" alt="" data-size="original"> block to op mode while loop.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVNjzguHO1BvGxNnawG%2FDual%20Motor%20-%20Add%20dual%20motor%20block%20to%20loop.svg?alt=media\&token=5ed744f0-9f43-41e2-9774-64fa2f1b94e1)

{% hint style="info" %}
When there are multiple of the same type of variable (such as multiple Dc Motor variables) the variable specific blocks will choose a default variable based on alphabetical order. For this example Op Mode Dc Motor blocks will default to the arm variable.&#x20;
{% endhint %}

Use the variable drop down menu on the block to change from arm to rightmotor.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVNdPNK1aoHjru6tzHV%2FDual%20Motor%20-%20Variable%20Drop%20Down%20Menu.svg?alt=media\&token=3cb22ad9-52e4-42e1-8e29-95650ac60e79)

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVRvnMZQuYQpBKRkzD6%2FDual%20Motor%20-%20variable%20adjustment.svg?alt=media\&token=2ee3c108-2a1c-45ca-8ea0-9dbf6808a701)

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



For the Class Bot, the robot pivots to the right, so the right motor will be reversed. Add <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVOBZ-rzSPjT4Aje-Ub%2FMotor%20-%20rightmotorDirection.svg?alt=media&#x26;token=82cbecae-83d2-41a4-b7ee-eda7a029ed9c" alt="" data-size="original"> to the op mode class, under the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVRzzz2RWu0i_oNzqo3%2FComment%20-%20Put%20intialization%20blocks.svg?alt=media&#x26;token=5b100e29-9c67-4bb3-be74-0d35d452cb76" alt="" data-size="original"> comment block.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVRqXPMgd43HMRJPC1Y%2FDual%20Motor%20-%20Add%20motor%20direction.svg?alt=media\&token=dd43039c-2605-4a0c-9e38-830ff0aa2f2d)

Adding the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVOBZ-rzSPjT4Aje-Ub%2FMotor%20-%20rightmotorDirection.svg?alt=media&#x26;token=82cbecae-83d2-41a4-b7ee-eda7a029ed9c" alt="" data-size="line"> block changes the direction of the right motor so that both motors will run in the same direction when power is set to one.&#x20;

### Teleoperated Driving - Arcade Style

Recall that when the motors were running in opposing directions the robot spun in circles. This same logic will be used to control the robot using the arcade style of control mentioned in the Hello Robot - Autonomous Robot section.&#x20;

#### Programming with gamepads

To start, create two variables $$x$$ and $$y$$ . Add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVS6vr4fOLI02xyBjhL%2FVariable%20-%20Set%20x%20to.svg?alt=media&#x26;token=99679c61-b207-4053-bfdc-b1f6c973fcc1" alt="" data-size="original">and<img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVS14nu9_ZE4QKp6Yn5%2FVariable%20-%20Set%20y%20to.svg?alt=media&#x26;token=87f18baa-067c-4059-8ac2-7c20cd45ca55" alt="" data-size="original">blocks to the while loop.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVST80N7utfTN7C8nn4%2FDual%20Motor%20-%20Add%20x%20and%20y%20variables.svg?alt=media\&token=1720da94-ada1-4dee-aae5-558f8254a88a)

$$y$$ will be assigned as <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVY90hzKehu4L9uGscf%2FGamepad%20-%20Joytstick%20y%20axis.svg?alt=media&#x26;token=b47cfd05-1252-45b8-a1f9-03662db45d62" alt="" data-size="original">, which is the y-axis of the right joystick.&#x20;

{% hint style="info" %}
Remember positive/negative values inputted by the gamepad's y-axis are inverse of the positive/negative values of the motor.&#x20;
{% endhint %}

Assign $$x$$ as the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVY92VNjdfeFbgTDbty%2FGamepad%20-%20Joytstick%20x%20axis.svg?alt=media&#x26;token=1cc6c4e0-fee2-42a7-b8ba-66aad22b12a3" alt="" data-size="original">, which is the x axis of the right gamepad joystick. The x-axis of the joystick does not need to be inverted.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVY64X-T5DxuDnc36ML%2FDual%20Motor%20-%20Adding%20joystick%20components.svg?alt=media\&token=d2a678fd-2f8a-44f6-9b63-b0b3fc2a0255)

The <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVYECjmC5fNog4tq9u5%2FVariable%20-%20set%20x%20equal%20to%20rightstickX.svg?alt=media&#x26;token=8f75536d-d3f5-4900-a0d3-db209c1e3c88" alt="" data-size="original"> and <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVYEFfkG_JRA7Cf0cUT%2FVariable%20-%20set%20y%20equal%20to%20rightstickY.svg?alt=media&#x26;token=16029543-fced-498e-a765-ce119e36d11b" alt="" data-size="original"> block sets assign values from the gamepad joystick to $$x$$ and $$y$$ . As previously mentioned, the joystick gives values along a two dimension coordinate system. $$y$$ receives the value from the y- axis and $$x$$ receives the value from the x-axis. Both axis output values between -1 and 1.&#x20;

To better understand consider the following table. The table shows the expected value generated from moving the joystick all the way in one direction, along the axis. For instance, when the joystick is pushed all the way in the upwards direction the coordinate values are (0,1).&#x20;

{% hint style="info" %}
The table below assumes that the the $$y$$values from the gamepad have been inverted in code when assigned to the variable $$y$$ .
{% endhint %}

|                                                                                                                                      Joystick Direction                                                                                                                                     | $$x$$  | $$y$$  |
| :-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :----: | :----: |
|  <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mefge4HnWzFYZVV8De2%2F-Mefhx7EWkkmadU6LW8V%2FGamepad%20-%20forward%20simple.svg?alt=media&#x26;token=ea9e8593-204d-4c38-b370-52f1450bd996" alt="" data-size="original"> |    0   |    1   |
| <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mefge4HnWzFYZVV8De2%2F-MefhzwimOC2m68IoDSE%2FGamepad%20-%20reverse%20simple.svg?alt=media&#x26;token=9ff3f6ce-370a-47b4-9928-b5c475aa0d66" alt="" data-size="original">  |    0   |   -1   |
|   <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mefge4HnWzFYZVV8De2%2F-Mefi1rcj_EIfo6ZRW2u%2FGamepad%20-%20left%20simple.svg?alt=media&#x26;token=79ed0be9-83f2-41b4-988f-4b78b2474a22" alt="" data-size="original">   |   -1   |    0   |
|  <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mefge4HnWzFYZVV8De2%2F-Mefi4IQJxLAupAhBq8Y%2FGamepad%20-%20right%20simple.svg?alt=media&#x26;token=c0141307-dc28-46f2-8097-bd7b719b0968" alt="" data-size="original">   |    1   |    0   |

Now that you have a better understanding of how the physical movement of the gamepad affects the numerical inputs given to your Control System; its time to consider how to control the drivetrain using the joystick. Recall, from the Programming Drivetrain Motors section, that the speed and direction of a motor plays a large part in how the drivetrain moves. The numerical outputs for  <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVrZYOdMO43YdZ0zxXy%2F-MVwRA9auYOOqnGmzAX7%2FDual%20Motor%20-%20set%20to%20positive.svg?alt=media&#x26;token=ed171c16-63c4-4531-89f3-ed93ce36dbae" alt="" data-size="original">determine the speed and direction of the motors. For instance, when both motors are set to 1 they move in the forward direction at full speed (or 100% of duty cycle). &#x20;

Much like the gamepads, the numerical value for `setPower` is in a range of -1 to 1. The absolute value of the assigned number determines percentage of duty cycle. As an example, 0.3 and -0.3 both indicate that the motor is operating at a duty cycle of 30%. The sign of the number indicates the direction the motor is rotating in. To better understand, consider the following graphic.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MVwkCFYYAPlJ0cAmhBB%2F-MW-yY4NTAgAYNayqDF2%2FMotor%20-%20SetMotor%20relationship.svg?alt=media\&token=b2fce6df-9b82-47b3-8f34-83021b904a6f)

When a motor is assigned a `setPower`value between -1 and 0, the motor will rotate in the direction it considers to be reverse. When a motor is assigned a value between 0 and 1, it will rotate forward.&#x20;

In the Programming Drivetrain Motors section, it was discussed that a robot rotates when the motors are moving in opposing directions. However, this has more to do with both speed and direction. To think of it numerically, a differential drivetrain will turn to the right when the `setPower` value for the right motor is less than that of the left motor. This is exhibited in the following example.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MVwkCFYYAPlJ0cAmhBB%2F-MW-wFdz5WlegTXYg9GA%2FMotor%20-%20SetPower%20results%20-%20Blocks.svg?alt=media\&token=bf906b42-2a7c-45cc-a537-99823a08b54d)

When both motors are <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVrZYOdMO43YdZ0zxXy%2F-MVwRA9auYOOqnGmzAX7%2FDual%20Motor%20-%20set%20to%20positive.svg?alt=media&#x26;token=ed171c16-63c4-4531-89f3-ed93ce36dbae" alt="" data-size="original"> the robot will run at full speed in a mostly straight line. However, when the rightmotor is running in the same direction but at a lower speed, such as <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVrZYOdMO43YdZ0zxXy%2F-MVwQEtvE9_UNoH5UBSh%2FDual%20Motor%20-%20right%20turn.svg?alt=media&#x26;token=273a84b8-9fb4-42e3-a740-ff30cdfd8819" alt="" data-size="original"> the robot will turn or rotate to the right. This is likely to be an arching movement that is not as sharp as a full pivot. In contrast when the rightmotor is set to full speed but in the opposite direction of the leftmotor, the robot pivots to the right. So, mathematically the following is considered to be true:&#x20;

|                        |                    |
| ---------------------- | ------------------ |
| rightMotor = leftMotor | Forward or Reverse |
| rightMotor > leftMotor | Left Turn          |
| rightMotor < leftMotor | Right Turn         |

As previously implied, <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVY92VNjdfeFbgTDbty%2FGamepad%20-%20Joytstick%20x%20axis.svg?alt=media&#x26;token=1cc6c4e0-fee2-42a7-b8ba-66aad22b12a3" alt="" data-size="original"> and <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVY90hzKehu4L9uGscf%2FGamepad%20-%20Joytstick%20y%20axis.svg?alt=media&#x26;token=b47cfd05-1252-45b8-a1f9-03662db45d62" alt="" data-size="original"> send values to the Control System from the game pad joystick. In contrast, <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVrZYOdMO43YdZ0zxXy%2F-MVwRA9auYOOqnGmzAX7%2FDual%20Motor%20-%20set%20to%20positive.svg?alt=media&#x26;token=ed171c16-63c4-4531-89f3-ed93ce36dbae" alt="" data-size="original"> interprets numerical information set in the code and sends the appropriate current to the motors to dictate how the motors behave.&#x20;

In an arcade drive, the following joy stick inputs (directions) need to correspond with the following outputs (motor power values).&#x20;

| Joystick Direction                                                                                                                                                                                                                                                                          | ( $$x$$ , $$y$$ ) | rightmotor | leftmotor |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- | ---------- | --------- |
| <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mefge4HnWzFYZVV8De2%2F-Mefhx7EWkkmadU6LW8V%2FGamepad%20-%20forward%20simple.svg?alt=media&#x26;token=ea9e8593-204d-4c38-b370-52f1450bd996" alt="" data-size="original">  | (0,1)             | 1          | 1         |
| <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mefge4HnWzFYZVV8De2%2F-MefhzwimOC2m68IoDSE%2FGamepad%20-%20reverse%20simple.svg?alt=media&#x26;token=9ff3f6ce-370a-47b4-9928-b5c475aa0d66" alt="" data-size="original">  | (0,-1)            | -1         | -1        |
| <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mefge4HnWzFYZVV8De2%2F-Mefi1rcj_EIfo6ZRW2u%2FGamepad%20-%20left%20simple.svg?alt=media&#x26;token=79ed0be9-83f2-41b4-988f-4b78b2474a22" alt="" data-size="original">     | (-1,0)            | 1          | -1        |
| <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mefge4HnWzFYZVV8De2%2F-Mefi4IQJxLAupAhBq8Y%2FGamepad%20-%20right%20simple.svg?alt=media&#x26;token=c0141307-dc28-46f2-8097-bd7b719b0968" alt="" data-size="original">    | (1,0)             | -1         | 1         |

To get the outputs expressed in the table above, the gamepad values must be assigned to each motor in a meaningful way, where. Algebraic principles can be used to determine the two formulas needed to get the values. However, the formulas are provided below.&#x20;

$$
rightmotor = y-x \\
leftmotor = y+x
$$

From the **math** menu grab the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW0myHWtFzHImnlIb8X%2F-MW0x3wm9ShSr87RKGmE%2Fmath%20-%20minus%20block.svg?alt=media&#x26;token=75f4a567-e432-407c-9e86-48c478664703" alt="" data-size="original">and <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW0myHWtFzHImnlIb8X%2F-MW0xADWQomF1x9ui--7%2Fmath%20-%20plus%20block.svg?alt=media&#x26;token=a5a38958-1100-4297-928b-4c1ea1e0a0a4" alt="" data-size="original"> blocks and add them to the respective motor in the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVrZYOdMO43YdZ0zxXy%2F-MVwRA9auYOOqnGmzAX7%2FDual%20Motor%20-%20set%20to%20positive.svg?alt=media&#x26;token=ed171c16-63c4-4531-89f3-ed93ce36dbae" alt="" data-size="original"> block.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MW0myHWtFzHImnlIb8X%2F-MW0xIkxGnrAqLyC1NDq%2FDual%20Motor%20-%20Adding%20%2B%20and%20-.svg?alt=media\&token=6579a5c8-95a0-4fc6-aed0-ef117a229734)

Next add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW0myHWtFzHImnlIb8X%2F-MW1GN0AKTXtbG-4RSvt%2FVariable%20-%20x.svg?alt=media&#x26;token=ae7966dc-9e41-4db4-8d86-2ea27b667c81" alt="" data-size="original"> and <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW0myHWtFzHImnlIb8X%2F-MW1GPqHF3_v0S-vEmE3%2FVariable%20-%20y.svg?alt=media&#x26;token=b984f4b9-020c-4c02-9f3c-4a45805bbbbf" alt="" data-size="original"> to the formula blocks. &#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MW0myHWtFzHImnlIb8X%2F-MW1Gi3Vryjay8wqmyFH%2FDual%20Motor%20-%20Add%20variables%20to%20formulas.svg?alt=media\&token=77822ccf-e3bf-40cc-bb98-6045ea37d24d)

With this you now have a functional teleoperated arcade drive!
