# Arm Control - Blocks

## Introduction to Arm Control&#x20;

Robot control comes in many different forms. Now that you have walked through programming a drivetrain, we can apply those concepts to controlling other mechanisms. Since this guide utilizes the Class Bot the focus will be on the basics of controlling it's main mechanism, a single jointed arm. &#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Mbh\_La74HLHjHtArkSm%2F-Mbh\_RZjnHpZbvvDsZ8H%2FClass%20Bot%20side%20view.svg?alt=media\&token=1bfb2c2c-c01c-42c1-87cc-801a1bc2da2b)

Controlling an arm requires a different thought process than the one you used to control the drivetrain. While the drivetrain uses the rotation motion of the motors to drive along a linear distance, an arm rotates along a central point, or joint. When working with an arm you will have to head caution to the physical limitations of the robot this includes load bearing, range of motion, and other forces that may apply.

In this section you will learn how to use the gamepad `Dpad` controls and the installed Touch Sensor to control the arm. However, the focus of this section is using code to limit the range of motion of the arm.&#x20;

| Sections                                                                                                 | Goals of Section                                                                                                      |
| -------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| [Basics of Programming an Arm](arm-control-blocks.md#basics-of-programming-an-arm)                       | Introduction to coding an arm for teleoperated control and working with a limit switch                                |
| [Programming an Arm to a Position](arm-control-blocks.md#programming-an-arm-to-a-position)               | Using motor encoders to move an arm to a specific position, such as from 45 degrees to 90 degrees.                    |
| [Using Limits to Control Range of Motion](arm-control-blocks.md#using-limits-to-control-range-of-motion) | Working with the basics of arm control, motor encoder, and limit switches to control the range of motion for an arm.  |

## Basics of Programming an Arm

Start by creating a basic op mode called `HelloRobot_ArmControl`.&#x20;

{% hint style="warning" %}
For more information on how to create an op mode type check out the[ Test Bed - Blocks ](../hello-robot-test-bed/test-bed-blocks.md#creating-an-op-mode)section. &#x20;
{% endhint %}

Unlike the joystick, which sends values corresponding to the position of the joystick, the `Dpad`on the gamepad inputs **Boolean** `FALSE/TRUE`. In order to tell the arm to move when `Dpad Up`or `Dpad Down` are selected, an`if/else if` statement needs to be used. Select an <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBUDlUpVQmk7Y7zght%2FLogic%20-%20if%20else.svg?alt=media&#x26;token=d48d4eec-5bcf-4086-aa74-b080fbb0527b" alt="" data-size="original"> block. Use the settings drop down to change the block to an <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_76Lu914wbfp2TPuaG%2FLogic%20-%20if%20elif.svg?alt=media&#x26;token=15492f0a-0762-4bdb-867c-c9d910f15775" alt="" data-size="original"> block. Do this by switching the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_7ooP0-O2TTvg1kCNI%2F-M_7pUSPlhlQbpyFqiHc%2Flogic%20-%20else.svg?alt=media&#x26;token=3a041334-1689-435d-ab9d-7bece7a05230" alt="" data-size="original"> out for an<img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAnBZGxGoi9TO3k6FC%2FLogic%20-%20else%20if.svg?alt=media&#x26;token=33006b12-eb23-4836-928f-9c7bcd57d0e5" alt="" data-size="original">.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_2CE63M33f73tG7c96%2F-M\_7-FqCBac6olINNE2x%2Flogic%20-%20swapping%20to%20elif.svg?alt=media\&token=2bc5dd95-9e8d-4e9f-ae8a-f5da6174bd34)

Add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_76Lu914wbfp2TPuaG%2FLogic%20-%20if%20elif.svg?alt=media&#x26;token=15492f0a-0762-4bdb-867c-c9d910f15775" alt="" data-size="original"> block to the op mode while loop.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_2CE63M33f73tG7c96%2F-M\_7K8m6Fb2RNq4isXUp%2FArm%20-%20add%20if%20else%20if%20else.svg?alt=media\&token=443055f1-2656-44af-ad64-b080de3786ba)

Add the  <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_6pst95i16Ri14yZ4b%2FGamepad%20-%20d%20pad%20blocks.svg?alt=media&#x26;token=82f3553f-3e78-4940-a8b7-375a566b8ae6" alt="" data-size="original"> and <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_6pxul-r5EMNjjKUza%2FGamepad%20-%20d%20pad%20down.svg?alt=media&#x26;token=29aa6ba0-6ed0-406a-aec7-2ece45c2f701" alt="" data-size="original"> blocks to the condition statements of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_76Lu914wbfp2TPuaG%2FLogic%20-%20if%20elif.svg?alt=media&#x26;token=15492f0a-0762-4bdb-867c-c9d910f15775" alt="" data-size="original">block.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_2CE63M33f73tG7c96%2F-M\_7SXNq7poj15LVdIbC%2FArm%20-%20add%20dpad%20blocks%20to%20if.svg?alt=media\&token=d2ee9267-a16b-4dea-af7c-6a150f333358)

One of the purposes of using the `Dpad` is to help delineate which direction the arm needs to move in. In this case, should <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_6pst95i16Ri14yZ4b%2FGamepad%20-%20d%20pad%20blocks.svg?alt=media&#x26;token=82f3553f-3e78-4940-a8b7-375a566b8ae6" alt="" data-size="original"> correspond with the arm moving upwards. Add a <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_7Vk_DJnc0QG4TNlgA%2Fmotor%20-%20arm%20set%20power%20to%201.svg?alt=media&#x26;token=106ab893-7912-41e6-b1bd-4f57d0e8a132" alt="" data-size="original"> block to the do portion of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_76Lu914wbfp2TPuaG%2FLogic%20-%20if%20elif.svg?alt=media&#x26;token=15492f0a-0762-4bdb-867c-c9d910f15775" alt="" data-size="original"> block below the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_6pst95i16Ri14yZ4b%2FGamepad%20-%20d%20pad%20blocks.svg?alt=media&#x26;token=82f3553f-3e78-4940-a8b7-375a566b8ae6" alt="" data-size="original"> block. Change the power from 1 to 0.2.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_2CE63M33f73tG7c96%2F-M\_7VAL0rQiDRzNpK0RW%2FArm%20-%20add%20first%20motor%20block.svg?alt=media\&token=a8ca8d73-4c2e-4227-bc3a-1bb53c15b880)

Add another<img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_7Vk_DJnc0QG4TNlgA%2Fmotor%20-%20arm%20set%20power%20to%201.svg?alt=media&#x26;token=106ab893-7912-41e6-b1bd-4f57d0e8a132" alt="" data-size="original"> block to the do portion of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_76Lu914wbfp2TPuaG%2FLogic%20-%20if%20elif.svg?alt=media&#x26;token=15492f0a-0762-4bdb-867c-c9d910f15775" alt="" data-size="original"> block below the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_6pxul-r5EMNjjKUza%2FGamepad%20-%20d%20pad%20down.svg?alt=media&#x26;token=29aa6ba0-6ed0-406a-aec7-2ece45c2f701" alt="" data-size="original"> block. Change the power from 1 to -0.2.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_2CE63M33f73tG7c96%2F-M\_7kP-c-lQmc4VuTWk4%2FArm%20-%20add%20second%20motor%20block.svg?alt=media\&token=70e97cf3-776f-486e-9312-9b42417dc049)

{% hint style="success" %}
Save the op mode and try running the code. Consider the following questions.&#x20;

* What happens if you press up on the `Dpad`?
* What happens if you press down on the `Dpad`?
{% endhint %}

Right now the logic of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_76Lu914wbfp2TPuaG%2FLogic%20-%20if%20elif.svg?alt=media&#x26;token=15492f0a-0762-4bdb-867c-c9d910f15775" alt="" data-size="original"> statement declares that when <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_6pst95i16Ri14yZ4b%2FGamepad%20-%20d%20pad%20blocks.svg?alt=media&#x26;token=82f3553f-3e78-4940-a8b7-375a566b8ae6" alt="" data-size="original"> is true (has been pressed) the motor will run in the forward ( or in this case upwards) direction at 20% duty cycle. If  <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_6pxul-r5EMNjjKUza%2FGamepad%20-%20d%20pad%20down.svg?alt=media&#x26;token=29aa6ba0-6ed0-406a-aec7-2ece45c2f701" alt="" data-size="original">is true the motor will run in reverse at 20% duty cycle. If you ran the code at this stage you may have noticed that even when you released the `Dpad` the motor continued to run in the selected direction. The current <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_76Lu914wbfp2TPuaG%2FLogic%20-%20if%20elif.svg?alt=media&#x26;token=15492f0a-0762-4bdb-867c-c9d910f15775" alt="" data-size="original"> statement tells the robot when the motor should move and in what direction, but nothing tells the motor to stop, thus the arm is continuing to run without limits.&#x20;

To fix this edit the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_76Lu914wbfp2TPuaG%2FLogic%20-%20if%20elif.svg?alt=media&#x26;token=15492f0a-0762-4bdb-867c-c9d910f15775" alt="" data-size="original">block to be a <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_6poiXjN6Ho7PTyWm3%2FLogic%20-%20if%20else%20if%20else.svg?alt=media&#x26;token=c6d1c93a-7ca7-4e36-a1ba-3baf88a05acb" alt="" data-size="original"> instead. To do this select the settings icon on the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_76Lu914wbfp2TPuaG%2FLogic%20-%20if%20elif.svg?alt=media&#x26;token=15492f0a-0762-4bdb-867c-c9d910f15775" alt="" data-size="original"> block and add an <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_7ooP0-O2TTvg1kCNI%2F-M_7pUSPlhlQbpyFqiHc%2Flogic%20-%20else.svg?alt=media&#x26;token=3a041334-1689-435d-ab9d-7bece7a05230" alt="" data-size="original"> below the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAnBZGxGoi9TO3k6FC%2FLogic%20-%20else%20if.svg?alt=media&#x26;token=33006b12-eb23-4836-928f-9c7bcd57d0e5" alt="" data-size="original"> .

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_7ooP0-O2TTvg1kCNI%2F-M\_LuuheylqocGOY0N\_J%2FArm%20-%20changing%20to%20an%20if%20else%20if%20els.svg?alt=media\&token=ae7a70f8-9a58-4729-ad26-e66d04e0e6ed)

Add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Ma9eNmmkAyF5RUbfPkd%2F-MaAmcRjToPMPrh6OqtT%2Farm%20-%20set%20power%20to%200.svg?alt=media&#x26;token=a3889b45-d9db-4059-a6b8-55774c2c71fd" alt="" data-size="original"> the else portion of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_6poiXjN6Ho7PTyWm3%2FLogic%20-%20if%20else%20if%20else.svg?alt=media&#x26;token=c6d1c93a-7ca7-4e36-a1ba-3baf88a05acb" alt="" data-size="original"> block.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_7ooP0-O2TTvg1kCNI%2F-M\_M-uNIIp95KM1rQbde%2FArm%20-%20add%20set%20power%20to%200.svg?alt=media\&token=78baf19b-e1a4-4cbf-a951-99dbcc6332f8)

{% hint style="success" %}
Try saving and running the op mode again. Pay attention to the speed of the arm going up versus going down. Does the speed seem the same?
{% endhint %}

Working with an arm introduces different factors for consideration than what you have seen previously with drivetrains. For instance, did you notice a difference in speeds when moving the arm up or down? Unlike the drivetrain, where the effect of gravity impacts the motors consistently across either direction, gravity plays a significant role in the speed of the arm motor.&#x20;

### Adding a Limit Switch&#x20;

Another consideration to make is the physical limitations of your arm mechanism. Certain mechanisms may have a physical limitation, that when exceeded runs the risk of damaging the mechanism or another component of the robot. There are a few ways to limit the mechanism with sensors that will help reduce the potential of a mechanism exceeding its physical limitations. In this section we will focus on using a limit switch to limit the motion range of the arm.

{% hint style="info" %}
This section assumes that you have a basic knowledge of limit switches form the [Test Bed section](../hello-robot-test-bed/test-bed-blocks.md) and the [Digital Sensors](../../sensors/digital.md) article.&#x20;
{% endhint %}

As you may recall from the [Test Bed](../hello-robot-test-bed/test-bed-blocks.md#touch-sensor-basics) section limit switches use Boolean logic to dictate when a limit has been met. Limit switches typically come in the form of digital sensors, like the Touch Sensor, as digital sensors report a **Boolean** on/off to the system, much like a light switch.&#x20;

If you are using a Class Bot your robot should have a Touch Sensor mounted to the front of your robot chassis. You also have a[ Limit Switch Bumper](https://docs.revrobotics.com/15mm/ftc-starter-kit-class-bot/skv3-arm-assemblies#limit-switch-bumper-assembly) installed. Together these items create a limit switch system. By utilizing the limit switch system you can keep your Class Bot arm from exceeding the lower physical limit, or what will be known as our starting position. Lets go ahead and start coding!&#x20;

{% hint style="warning" %}
Before proceeding with code please make sure that your mechanism is interfacing with, and pressing the Touch Sensor. If you have the Class Bot this entails making sure your bumper is actively pressing the Touch Sensor when the arm comes down.&#x20;
{% endhint %}

Start by grabbing the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Ma54anFFV_shkA4tBtj%2F-Ma5a_1yFPykLjStaOFu%2Farm%20-%20inline%20gamepad%20if%20else.svg?alt=media&#x26;token=c05f2ced-b767-41b3-a625-7f25eff50a18" alt="" data-size="original"> statement made in the previous section, and dragging it to the side of the blocks project.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_M9OIwnVSR7pVOcS7-%2F-M\_W92PcLuIvWwY1kHk8%2FArm%20-%20moving%20the%20gamepad%20control%20to%20the%20side.svg?alt=media\&token=8d3bdaae-aad8-4bfc-a794-e5abcb958c4f)

Add a new <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBUDlUpVQmk7Y7zght%2FLogic%20-%20if%20else.svg?alt=media&#x26;token=d48d4eec-5bcf-4086-aa74-b080fbb0527b" alt="" data-size="original"> block to the while loop. Add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_XBQXs62j9nmwzdIAi%2F-M_XZ6sOdt18rwa0wJUh%2Fdigital%20-%20touch%20state.svg?alt=media&#x26;token=81d147e4-20ae-47a1-8f43-8098d017592f" alt="" data-size="original"> block to the conditional portion of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBUDlUpVQmk7Y7zght%2FLogic%20-%20if%20else.svg?alt=media&#x26;token=d48d4eec-5bcf-4086-aa74-b080fbb0527b" alt="" data-size="original"> block.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_XBQXs62j9nmwzdIAi%2F-M\_XaDYOHCUMTh0JyAtB%2FArm%20-%20limit%20if%20else.svg?alt=media\&token=c2d9cb69-5fbd-4b2c-a0de-8d7271235f57)

Add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Ma54anFFV_shkA4tBtj%2F-Ma5a_1yFPykLjStaOFu%2Farm%20-%20inline%20gamepad%20if%20else.svg?alt=media&#x26;token=c05f2ced-b767-41b3-a625-7f25eff50a18" alt="" data-size="original"> block set back to the code in the do port of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Ma54anFFV_shkA4tBtj%2F-Ma9WK_exSd2vEZdTZfK%2Flimit%20-%20ifdo%20inline.svg?alt=media&#x26;token=defa8738-f8eb-4f0c-9b7f-f0b7112c398e" alt="" data-size="original"> block.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Ma54anFFV\_shkA4tBtj%2F-Ma5ZAkDCuGSk20gV3z-%2Farm%20-%20adding%20main%20if%20else%20if%20to%20limit.svg?alt=media\&token=c04b2e12-4282-4b6b-bd8d-8f18207209b6)

If you recall from the initial Limit switch section, the touch sensor operates on a `FALSE/TRUE` binary. When the touch sensors is not pressed the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_XBQXs62j9nmwzdIAi%2F-M_XZ6sOdt18rwa0wJUh%2Fdigital%20-%20touch%20state.svg?alt=media&#x26;token=81d147e4-20ae-47a1-8f43-8098d017592f" alt="" data-size="original">block reports true; when the touch sensor is pressed the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_XBQXs62j9nmwzdIAi%2F-M_XZ6sOdt18rwa0wJUh%2Fdigital%20-%20touch%20state.svg?alt=media&#x26;token=81d147e4-20ae-47a1-8f43-8098d017592f" alt="" data-size="original"> block reports false. At this point the logic of the code states that when touch sensor is not pressed, the gamepad commands that were previously chosen operate normally. To function as a limit switch the motor needs to stop when the touch sensor is pressed.

{% hint style="success" %}
Try adding a <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_7ooP0-O2TTvg1kCNI%2F-M_LwhUWark-M3IZieU2%2Farm%20-%20set%20power%20to%200.svg?alt=media&#x26;token=e995f948-add0-476b-b6c4-e44a8826fdcc" alt="" data-size="original"> block to the else portion of the block.&#x20;

<img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Ma9eNmmkAyF5RUbfPkd%2F-MaATIJuA44rq4uxBFh0%2FLimit%20-%20the%20wrong%20way%20to%20do%20the%20limit.svg?alt=media&#x26;token=44e6412f-8be6-43b5-b8bd-4edc3acc7ab3" alt="" data-size="original">&#x20;

Save the op mode and run it.&#x20;

What happens when the Touch Sensor is pressed?
{% endhint %}

One of the common features of a limit switch, like the Touch Sensor,  is the ability to reset to its default state. If you press the Touch Sensor with your finger, you may notice that as soon as you release the pressure you are applying the Touch Sensor will return to its default "not pressed" state. However, you have to release the pressure in order to accomplish this.&#x20;

{% hint style="warning" %}
Make sure that the mechanism is actually interfacing with the Touch Sensor. For the Class Bot, you may need to adjust the Touch Sensor so that the Limit Switch Bumper is interfacing with it more consistently.&#x20;
{% endhint %}

The code in the info block above dictates that when the Touch Sensor is pressed the arm motor is set to zero. This would work in a mechanism where the Touch Sensor is allowed to return to its default state on its own. However, once the arm presses the Touch Sensor, the weight of the mechanism will keep the Touch Sensor from returning to its default state. The combination of the weight of the mechanism and the logic of the info block code means that once the arm meets its limit it will not be able to move again.&#x20;

To remedy this, an action to move the arm in the opposite direction of of the limit needs to be added to the else statement. To do this lets use another <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBUDlUpVQmk7Y7zght%2FLogic%20-%20if%20else.svg?alt=media&#x26;token=d48d4eec-5bcf-4086-aa74-b080fbb0527b" alt="" data-size="original"> block. Since the Touch Sensor is a lower limit for the arm, the arm will need to move up (or the motor in the forward direction) to move away from the touch sensor. Following the earlier convention for moving the arm, add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_6pst95i16Ri14yZ4b%2FGamepad%20-%20d%20pad%20blocks.svg?alt=media&#x26;token=82f3553f-3e78-4940-a8b7-375a566b8ae6" alt="" data-size="original"> as the condition in the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBUDlUpVQmk7Y7zght%2FLogic%20-%20if%20else.svg?alt=media&#x26;token=d48d4eec-5bcf-4086-aa74-b080fbb0527b" alt="" data-size="original"> . In the do portion of the block add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_7Vk_DJnc0QG4TNlgA%2Fmotor%20-%20arm%20set%20power%20to%201.svg?alt=media&#x26;token=106ab893-7912-41e6-b1bd-4f57d0e8a132" alt="" data-size="original"> block. Change the duty cycle from 100% to 20%. In the else portion add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Ma9eNmmkAyF5RUbfPkd%2F-MaAmcRjToPMPrh6OqtT%2Farm%20-%20set%20power%20to%200.svg?alt=media&#x26;token=a3889b45-d9db-4059-a6b8-55774c2c71fd" alt="" data-size="original"> block.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Ma9eNmmkAyF5RUbfPkd%2F-MaAmpElvyzJoAiZEbB9%2FLimit%20-%20move%20else%20stop.svg?alt=media\&token=7a3d148a-77eb-4033-84f1-827ffc51ab56)

Add this block set to the else portion of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Ma54anFFV_shkA4tBtj%2F-Ma9WK_exSd2vEZdTZfK%2Flimit%20-%20ifdo%20inline.svg?alt=media&#x26;token=defa8738-f8eb-4f0c-9b7f-f0b7112c398e" alt="" data-size="original"> block set.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Ma9eNmmkAyF5RUbfPkd%2F-MaFcI2yx1-iyZM-tv1k%2Flimit%20-%20full%20code.svg?alt=media\&token=70223f06-43c0-4400-a2ee-2d98832d456e)

## Programming an Arm to a Position

In the [Encoder Navigation](robot-navigation-blocks/encoder-navigation-blocks.md) section the concept of moving the motor to a specific position based on encoder ticks was introduced. The process highlighted in _Encoder Navigation_ focused on how to convert from encoder ticks to rotations to a linear distance. A similar procedure can be utilized to move the arm to a particular position. However, unlike the drivetrain, the arm does not follow a linear path. Rather than convert to a linear distance it makes more sense to convert the encoder ticks into an angle measured in degrees.&#x20;

In the image below two potential positions are showcased for the ClassBot arm. One of the positions - highlighted in blue below - is the position where the arm meets the limit of the touch sensor. Due to the limit, this position will be our default or starting position. From the Class Bot build guide, it is known that the Extrusion supporting the battery sits a 45 degree angle. Since the arm is roughly parallel to these extrusion when it is in the starting position, we can estimate that the default angle of the arm is roughly 45 degrees.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MaZOjYoShzpGpEUjqNv%2F-Ma\_\_OatEnD88azc\_Zie%2Fdifferent%20positions.svg?alt=media\&token=f19ee578-4d9b-4708-adda-c99a62259f90)

The goal of this section is to determine the amount of encoder ticks it will take to move the arm from its starting position to a position around 90 degrees.  There are a few different ways this can be accomplished. An estimation can be done by moving the arm to the desired position and recording the telemetry feedback from the Driver Station. Another option is to do to the math calculations to find the amount of encoder ticks occur per degree moved. Follow through this section to walk through both options and determine which is the best for your team.&#x20;

### Estimating the Position of the Arm&#x20;

To estimate the position of the arm using telemetry and testing, lets start with the initial code we created at the start of the [Basics of Programming an Arm](arm-control-blocks.md#basics-of-programming-an-arm), section.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MaUgx24O\_aiERCHX2\_C%2F-MaV9JFbufPja9M5yEtl%2FArm%20-%20returning%20to%20the%20basic%20op%20mode.svg?alt=media\&token=87179123-5364-49b4-a346-ddadc948ef88)

{% hint style="warning" %}
For now you can move the limit switch related blocks to the side of your project.&#x20;
{% endhint %}

Within the loop add a <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBJfpbTuatRMfbhnlO%2FTelemetry%20-%20key%20and%20number.svg?alt=media&#x26;token=d6f21b70-8197-4ead-954a-2604cfb72155" alt="" data-size="original"> block. Add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MaUgx24O_aiERCHX2_C%2F-MaZ6jj3OgarZ9wIkHBe%2Fmotor%20-%20arm%20get%20current%20positon.svg?alt=media&#x26;token=aa7cf01d-1009-44bf-be0f-9eb829475334" alt="" data-size="original"> to the number portion of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBJfpbTuatRMfbhnlO%2FTelemetry%20-%20key%20and%20number.svg?alt=media&#x26;token=d6f21b70-8197-4ead-954a-2604cfb72155" alt="" data-size="original"> block. Change the key string from the default `"key"`to `"Arm Test."`

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MaUgx24O\_aiERCHX2\_C%2F-MaZHeH6pTUWT3mLwdKC%2Farm%20-%20adding%20telemtry.svg?alt=media\&token=4fdaeddb-c169-4848-967c-254cece2b0d3)

Save the op mode and run it. Use the gamepad commands to move the arm to the 90 degree position. Once you have the arm properly positioned read the telemetry off the Driver Station to determine the encoder count relative to the position of the arm.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MadRPzxQDwEcPdg\_MX-%2F-Mae0pJn3Pk9zTlgBL5x%2FClass%20Bot%20side%20view%20arm%20at%2090%20-%20with%20DS%20telemetry.svg?alt=media\&token=6bbd1870-e17a-407a-b7d3-77be74c46e2b)

{% hint style="warning" %}
Recall from the[ Basic Encoder Concepts](broken-reference) section that the encoder position is set to 0 each time the Control Hub is turned on. This means that if your arm is in a position other than the starting position when the Control Hub is turned on, that position becomes zero instead of the starting position.&#x20;

The number given in the image above is not necessarily an accurate encoder count for the 90 degree position. To get the most accurate encoder reading for your robot make sure that your starting position reads as 0 encoder counts. To further increase accuracy consider doing several testing runs before deciding on the number of counts.&#x20;
{% endhint %}

To add the `RUN_TO_POSITION` code the `if/else` statement must first be edited back into an <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_76Lu914wbfp2TPuaG%2FLogic%20-%20if%20elif.svg?alt=media&#x26;token=15492f0a-0762-4bdb-867c-c9d910f15775" alt="" data-size="original"> block, as shown in the code below.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MadRPzxQDwEcPdg\_MX-%2F-Maee9cumu\_AfD4241tn%2FArm%20-%20editing%20if%20else%20for%20position%20changing.svg?alt=media\&token=d74bdf2f-88ac-4118-aa2e-240c166b9573)

Now recall that in order to execute `RUN_TO_POSITION`the following three blocks need to be added to both sections of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_76Lu914wbfp2TPuaG%2FLogic%20-%20if%20elif.svg?alt=media&#x26;token=15492f0a-0762-4bdb-867c-c9d910f15775" alt="" data-size="original"> block.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MadRPzxQDwEcPdg\_MX-%2F-MaeiLgBuj0YrcCb-2zP%2FArm%20-%20set%20position%20blocks.svg?alt=media\&token=0019c334-63c1-440d-b6fd-85ffb3208337)

When `DpadUp` is pressed, the arm should move to the the 90 degree position. When `DpadDown` is pressed the arm should move back to the starting position. To do this set the first <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MadRPzxQDwEcPdg_MX-%2F-Mai71kIttY8M1PhNW8b%2Farm%20-%20set%20arm%20to%20targetPosition.svg?alt=media&#x26;token=a2dfe87f-acc6-44fd-ab81-4d003ba2dbdd" alt="" data-size="original"> equal to the number of ticks it took your arm to get to 90 degrees, for this example we will use 83 ticks.&#x20;

Since we want `DpadDown` **** to return the arm to the starting position, keeping the  <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MajyF-W7HKhicX7wGD3%2F-MaosWQi5hUAA9ONxsD6%2Farm%20-%20set%20arm%20to%20targetPosition.svg?alt=media&#x26;token=028e0f4f-20c7-4728-8804-dfaddbeaf77a" alt="" data-size="original">  block set to 0 will allow us to accomplish this. Set both <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Ma9eNmmkAyF5RUbfPkd%2F-MaAmcRjToPMPrh6OqtT%2Farm%20-%20set%20power%20to%200.svg?alt=media&#x26;token=a3889b45-d9db-4059-a6b8-55774c2c71fd" alt="" data-size="original"> blocks equal to 0.5.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MadRPzxQDwEcPdg\_MX-%2F-MajrW5XFqPgiNJfSfCa%2Farm%20-%20adding%20positions.svg?alt=media\&token=475e2615-dcf5-4e1e-9123-8ad4d8ca519f)

{% hint style="info" %}
Recall that the target position dictates which direction the motor moves, taking over the directionality control from the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Ma9eNmmkAyF5RUbfPkd%2F-MaAmcRjToPMPrh6OqtT%2Farm%20-%20set%20power%20to%200.svg?alt=media&#x26;token=a3889b45-d9db-4059-a6b8-55774c2c71fd" alt="" data-size="original">block, so both blocks can be set to a positive value since they will control the speed.&#x20;
{% endhint %}

If you try running this code you may notice that the arm oscillates around the 90 degree position. When this behavior is present you should also notice the telemetry output for the encoder counts fluctuating. `RUN_TO_POSITION` is a **Closed Loop Control**, which means that if the arm does not perfectly reach the target position, the motor will continue to fluctuate until it does. When motors continue to oscillate and never quite reach the target position this may be a sign that the factors determining tolerances and other aspects of the closed loop are not tuned to this particular motor or mechanism. There are ways to tune the motor, but for now we want to focus on working with the arm and expanding on how limits and positions work with regards to the mechanism.&#x20;

### Calculating Target Position

In the initial introduction to run to position, you worked through the calculations needed to convert the ticks per rotation of a motor into ticks per mm moved. Now we want to focus on how to convert ticks per rotation of the motor to ticks per degree moved. From the previous section you should have a rough estimate of the amount of ticks you need to get to the 90 degree position. The goal of this section is to work through how to get a more exact position.&#x20;

To start you will need some of the same variables we used in [Encoder Navigation](robot-navigation-onbot-java/encoder-navigation-onbot.md#converting-encoder-ticks-to-a-distance):

#### Ticks per Revolution

Recall, that ticks per revolution of the encoder shaft is different than the ticks per revolution of the shaft that is controlling a mechanism. We saw this in the [Encoder Navigation](robot-navigation-onbot-java/encoder-navigation-onbot.md#basics-of-programming-with-encoders) section when the ticks per revolution at the motor was different from the ticks per revolution of the wheel. As motion is transmitted from a motor to a mechanism, the resolution of the encoder ticks changes.&#x20;

{% hint style="info" %}
For more information on the effect of motion transmission across a mechanism check out the [Compound Gearing](https://docs.revrobotics.com/duo-build/actuators/gears/gears-advanced#compound-gearing) section.&#x20;
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

Add the variables`COUNTS_PER_MOTOR_REV` and `GEAR_REDUCTION`variables to the  initialization  section  of  the op  mode.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MajyF-W7HKhicX7wGD3%2F-ManopxUAHj6\_XuNxvWC%2Farm%20-%20adding%20first%20set%20of%20constant%20variables.svg?alt=media\&token=9965e124-73f9-4d7d-b42e-b8b72a46a587)

Once the variables are created and added to the op mode, use the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYQpFaVyN6OAN2wLm6r%2F-MYRB7rWtI2jshN4W7LJ%2FMath%20-%200.svg?alt=media&#x26;token=99ad04a5-2f5e-4c97-a3f1-aa6471df73b2" alt="" data-size="original"> blocks to set the variables to the respective values

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MajyF-W7HKhicX7wGD3%2F-ManrpfRGL9WbH0S\_hlT%2FArm%20-%20the%20first%20two%20constants%20on%20their%20own.svg?alt=media\&token=8401fdda-ac1d-4e1b-bd47-c5d8d9bd224b)

Now that these two variables have been defined, we can use them to calculate two other variables: the amount of encoder counts per rotation of the 125T driven gear and the number of counts per degree moved.

Calculating counts per revolution of the 125T gear (or `COUNTS_PER_GEAR_REV`)is the same formula used in[ Encoder Navigation](robot-navigation-onbot-java/encoder-navigation-onbot.md#circumference-of-the-wheel) for our`COUNTS_PER_WHEEL_REV`variable. So to get this variable we can multiple`COUNTS_PER_MOTOR_REV` by `GEAR_REDUCTION`.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MajyF-W7HKhicX7wGD3%2F-Mao0qRmb6SmLr4iOO5\_%2FArm%20-%20counts%20per%20gear%20rev.svg?alt=media\&token=e1e51c80-738e-4217-ae74-052b51290f97)

To calculate the number of counts per degree or moved or `COUNTS_PER_DEGREE`divide the `COUNTS_PER_GEAR_REV`variable by 360.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MajyF-W7HKhicX7wGD3%2F-Mao6OjsQ1lyb5dBxPIQ%2FArm%20-%20counts%20per%20degree.svg?alt=media\&token=c2a5191c-ece1-4828-b4de-f7afee8b4653)

Add both these variables to the op mode in the initialization section of the op mode.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MajyF-W7HKhicX7wGD3%2F-MaoC0NFfx7yzQRQUKDz%2Farm%20-all%20constant%20variables.svg?alt=media\&token=c1472948-2c5c-4f86-83f9-48e5c55c4ed1)

Finally we need to create a non-constant variable that will act as our position. Create a variable called arm position.&#x20;

To get to the 90 degree position, the arm needs to move roughly 45 degrees. Set arm position equal to `COUNTS_PER_DEGREE`times 45.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MajyF-W7HKhicX7wGD3%2F-Maok2yFCAHOUh00l070%2Farm%20-%20setting%20arm%20position.svg?alt=media\&token=dceec55d-7e8a-45fd-a384-fa2353b7dc8f)

Add this variable to the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_6pst95i16Ri14yZ4b%2FGamepad%20-%20d%20pad%20blocks.svg?alt=media&#x26;token=82f3553f-3e78-4940-a8b7-375a566b8ae6" alt="" data-size="original"> section of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_76Lu914wbfp2TPuaG%2FLogic%20-%20if%20elif.svg?alt=media&#x26;token=15492f0a-0762-4bdb-867c-c9d910f15775" alt="" data-size="original"> statement, as this section dictates the 90 degree position. Add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MajyF-W7HKhicX7wGD3%2F-MaotXo3dfKi8y9Cp7gE%2FArm%20-%20armPosition.svg?alt=media&#x26;token=fdd22974-3023-4463-bbbc-3c4d5eeb30e9" alt="" data-size="original"> block to the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MajyF-W7HKhicX7wGD3%2F-MaosWQi5hUAA9ONxsD6%2Farm%20-%20set%20arm%20to%20targetPosition.svg?alt=media&#x26;token=028e0f4f-20c7-4728-8804-dfaddbeaf77a" alt="" data-size="original"> block.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MajyF-W7HKhicX7wGD3%2F-MaouCy\_cyMP8S-9JUMc%2Farm%20-%20add%20position%20varible.svg?alt=media\&token=66339d05-339a-4fbf-b8d7-74bee96c6f54)

{% hint style="warning" %}
We could set <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MajyF-W7HKhicX7wGD3%2F-MaosWQi5hUAA9ONxsD6%2Farm%20-%20set%20arm%20to%20targetPosition.svg?alt=media&#x26;token=028e0f4f-20c7-4728-8804-dfaddbeaf77a" alt="" data-size="original"> equal to <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MajyF-W7HKhicX7wGD3%2F-MaovdjIxPJFWeiUF5Jm%2Farm%20-%20degrees%20times%20intended%20position.svg?alt=media&#x26;token=2286ff60-7227-44f9-99dd-010c32361577" alt="" data-size="original">. However, it is a good practice to create a variable in situations like this. If we want to add another position later, we can easily edit the variable to fit our needs.&#x20;
{% endhint %}

## Using Limits to Control Range of Motion&#x20;

In the previous sections you worked on some of the building blocks for restricting an arms range of motion. From those sections you should have the foundation you need to perform basic arm control. However, there are some other creative ways you can use encoder positions and limits to expand the control you have over your arm.&#x20;

This section will cover two additional types of control. The first type of control we will explore is the idea of **soft limits**. In the[ Adding a Limit Switch ](arm-control-blocks.md#adding-a-limit-switch)section we discuss the concept of physical limits of a mechanism however, there may be times you need to limit the range of motion of an arm without installing a physical limit. To do this a position based code can be used to create a range for the arm.&#x20;

Once you have a basic idea of how to create soft limits, we will explore how to use a limit switch (like a touch sensor) to reset the range of motion. This type of control reduces the risk of getting stuck outside of your intended range of motion, which can affect the expected behavior of your robot.&#x20;

To set the soft limits we will use some of the basic logic we established in previous sections, with some edited changes. Start with a `Basic Op Mode` and add the constant variables from the [Calculating Target Position](arm-control-blocks.md#calculating-target-position) section to the op mode.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Mb7NRLlN4cP21O7utyz%2F-MbD991wkvVq5isIVrhS%2FArm%20-%20setting%20soft%20limits%20starting%20code.svg?alt=media\&token=45a62ea2-a354-463d-9da2-2fd4ed78df00)

Next we need to create our upper and lower limits. Create two new variables one called `minPosition` and one called `maxPosition`. Add both of these to the initialization section of the op mode.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Mb7NRLlN4cP21O7utyz%2F-MbDF83MERtXh2Wr4aZz%2FArm%20-%20creating%20min%20and%20max.svg?alt=media\&token=401a27ea-8c9c-45a0-9bc2-2f7091f57a08)

For now we want the `minPosition` set as our starting position and the `maxPosition` set to our 90 degree position. Set `minPosition`equal to <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MYQpFaVyN6OAN2wLm6r%2F-MYRB7rWtI2jshN4W7LJ%2FMath%20-%200.svg?alt=media&#x26;token=99ad04a5-2f5e-4c97-a3f1-aa6471df73b2" alt="" data-size="original"> and set `maxPosition`equal to <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mb7NRLlN4cP21O7utyz%2F-MbDKWl-0JA7163odOxB%2FArm%20-%20degree%20times%2045.svg?alt=media&#x26;token=e6a98555-aa7e-4a60-83f9-9d0330139052" alt="" data-size="original"> .&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Mb7NRLlN4cP21O7utyz%2F-MbDKjfbN9esu2cKOBa4%2FArm%20-%20setting%20min%20and%20max.svg?alt=media\&token=1fe11719-7457-41a3-b3ee-ddfac9a3e7fd)

An `if/else if` statement needs to be added to control the arm, for this we can use the same basic logic we use in the [Basics of Programming an Arm](arm-control-blocks.md#basics-of-programming-an-arm) section.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Mb7NRLlN4cP21O7utyz%2F-MbDOTQhQBREe4ZXSqoI%2FArm%20-%20limit%20if%20else%20logic.svg?alt=media\&token=f85b763f-de4a-4031-8774-4e505ebd8547)

To set the limit we need to edit our `if/else if`statement so that the limits are built in. If **** `DpadUp` is selected and the position of the arm is less than the `maxPosition` then the arm will move to the `maxPosition`. If **** `DpadDown` is selected and the position of the is greater that the `minPosition` then the arm will move towards the `minPosition`.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Mb7NRLlN4cP21O7utyz%2F-MbD\_M8XJkOkulzG4Ay4%2Farm%20-%20add%20the%20limits%20to%20the%20op%20mode.svg?alt=media\&token=2c15fc79-0a5d-4a9d-a9c3-a57e10ff7fce)

{% hint style="success" %}
The current code configuration will stop the motor at any point that the conditions to power the motor are not met. Depending to factors like the weight of the mechanism and any load that it is bearing, when the motor stops the arm may drop below the `maxPosition`.  Take time to test out the code and confirm that it behaves in the way you expect it to.&#x20;
{% endhint %}

#### Overriding Limits

One of the benefits of having a soft limit is being able to exceed that limit. Since encoders zero tick position is determined by the position of the arm when the Control Hub powers on; if attention is not payed to what position the arm is on power up the range of motion of the arm is affected. For instance, if we have to reset the Control Hub while the arm is in the 90 degree position, the 90 degree position is equal to 0 encoder ticks. One way around this is to create an override for the range of motion.&#x20;

There are a few different ways an override of sorts can be created, in our case we are going to use the a button and touch sensor to help reset our range.&#x20;

Start by editing the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_6poiXjN6Ho7PTyWm3%2FLogic%20-%20if%20else%20if%20else.svg?alt=media&#x26;token=c6d1c93a-7ca7-4e36-a1ba-3baf88a05acb" alt="" data-size="original"> to add another <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAnBZGxGoi9TO3k6FC%2FLogic%20-%20else%20if.svg?alt=media&#x26;token=33006b12-eb23-4836-928f-9c7bcd57d0e5" alt="" data-size="original"> condition. Use the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mb7NRLlN4cP21O7utyz%2F-MbIJAD2Ou3ksEcYY6ya%2FGamepad%20-%20a%20button.svg?alt=media&#x26;token=d269b4d5-7832-49cf-bcc9-485485e7dfe6" alt="" data-size="original"> block as the condition. Add a <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Ma9eNmmkAyF5RUbfPkd%2F-MaAmcRjToPMPrh6OqtT%2Farm%20-%20set%20power%20to%200.svg?alt=media&#x26;token=a3889b45-d9db-4059-a6b8-55774c2c71fd" alt="" data-size="original"> block to the do portion of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M_2CE63M33f73tG7c96%2F-M_6poiXjN6Ho7PTyWm3%2FLogic%20-%20if%20else%20if%20else.svg?alt=media&#x26;token=c6d1c93a-7ca7-4e36-a1ba-3baf88a05acb" alt="" data-size="original"> block.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Mb7NRLlN4cP21O7utyz%2F-MbI3ILIsW31iiOF1UdH%2FArm%20-%20add%20a%20button%20failsafe.svg?alt=media\&token=40785014-6901-4704-86c6-4f163dac0115)

Now that we have this change in place, when the `a` button is pressed the arm will move toward the starting position. When the arm reaches and presses the touch sensor we want to`STOP_AND_RESET_ENCODER` .

We can create an <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAm39BsREHDm26Al4M%2FLogic%20-%20ifdo%20(blank).svg?alt=media&#x26;token=ce3fdbbd-68c4-4b67-bc50-981a1e204bae" alt="" data-size="original"> statement that focuses on performing this stop and reset when the touch sensor is pressed. Since the touch sensor reports `true` when its not pressed and `false` when it is, we will need to use the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mb7NRLlN4cP21O7utyz%2F-MbIT1X6e91K0qQV64eZ%2FLogic%20-%20not.svg?alt=media&#x26;token=b3140489-980c-4761-a659-d7dd614dabf0" alt="" data-size="original"> block.&#x20;

{% hint style="info" %}
The **not operator** <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-Mb7NRLlN4cP21O7utyz%2F-MbIT1X6e91K0qQV64eZ%2FLogic%20-%20not.svg?alt=media&#x26;token=b3140489-980c-4761-a659-d7dd614dabf0" alt="" data-size="original"> can be used in conditional binary statements when you need inverse whether something is `true` of `false`. For instance, an `if` statement activates when something is true, but when the Touch Sensor reports `true` it is not pressed. In our case we want this if statement to activate when the touch sensor is pressed thus we need to use the not operator.&#x20;
{% endhint %}

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Mb7NRLlN4cP21O7utyz%2F-MbITArF8CcuEcJ1DINm%2Farm%20-%20reset%20limit.svg?alt=media\&token=5fc7a16c-7a8b-4b05-bab3-4a787d6689e6)

So, if the touch sensor returns `false` (or is pressed) the motor run mode `STOP_AND_RESET_ENCODER`will be activated causing the motor encoder to reset to 0 ticks.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Mb7NRLlN4cP21O7utyz%2F-MbIalnUjV2DPcWRy3Wl%2FArm%20-%20add%20stop%20and%20reset.svg?alt=media\&token=36a6e7c1-cc4b-4fcc-a508-e21fdd364204)

Now that this code is done, try testing it!
