# Test Bed - Blocks

The Blocks Programming Tool is a visual, programming tool that lets programmers use a web browser to create, edit and save their op modes. Blocks, like other scratch based programming tools, is a collection of preset code snippets that users can drag-and-drop into the appropriate code line.  In this section users can learn how to create an op mode, as wells as the basics of programming the actuators and sensors featured on the test bed.&#x20;

Follow the guide in order to get an in depth understanding of working with Blocks or navigate to the section that fits your needs:

| Section                                                              | Goals of Section                                                                                                                                           |
| -------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Creating an Op Mode](test-bed-blocks.md#creating-an-op-mode)        | Focuses on how to navigate the Blocks interface and create an op mode.                                                                                     |
| [Programming Essentials ](test-bed-blocks.md#programming-essentials) | Breaks down the structure and key elelments needed for an op mode, as well as some of the essential components of Blocks and programming logic.            |
| [Programming Actuators ](test-bed-blocks.md#programming-actuators)   | How to code servos and motors. This section walks through the basic logic of coding actuators, controlling actuators with a gamepad, and using telemetry.  |
| [Programming Sensors ](test-bed-blocks.md#programming-sensors)       | How to code a digital device. The section focuses on the basic logic of coding a digital device, like a REV Touch Sensor.                                  |

## Creating an Op Mode&#x20;

Before diving in and creating your first op mode, you should consider the concept of [**naming conventions**](https://en.wikipedia.org/wiki/Naming\_convention\_\(programming\)). When writing code the goal is to be as clear as possible about what is happening within the code. This is where the concept of naming conventions comes into play. Common naming conventions have been established by the programming world to denote variables, classes, functions, etc. Op modes share some similarities to [**classes**](https://en.wikipedia.org/wiki/Class\_\(computer\_programming\))**.** Thus the naming convention for op modes tends to follow the naming convention for classes; where the first letter of every word is capitalized.&#x20;

{% hint style="info" %}
This section assumes that you have already accessed the Blocks platform during the [Hello Robot - Introduction to Programming](../hello-robot-introduction-to-programming.md). If you are unsure how to access blocks please revisit this section before proceeding.&#x20;
{% endhint %}

To start, access the Robot Controller Console and go to the Blocks page. In the upper right-hand corner of there is a _**Create New Op Mode**_ button, click it.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMaksa1NF8Ki6mSUARF%2F-MMatLKYlfdPuBpHuGIU%2FBlocks%20-%20Start%20Screen.svg?alt=media\&token=5f88702a-e97a-48ec-9fd3-cc3ae070fa96)

Clicking the _**Create New Op Mode**_ button will open up the _**Create New Op Mode**_ window. This window allows users to name their op modes and select a sample code to build off of. For this guide use the default **BasicOpMode** sample and name the op mod **HelloRobot\_TeleOp** as shown in the image below.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMWthOxRowXhFCMHWAY%2F-MMaErIOjmHpFm7asnQ9%2Fnaming%20op%20mode.svg?alt=media\&token=f17185fa-0594-49f8-8dac-c931aa2c3b4b)

Once the op mode has been named click 'OK' to proceed forward. Creating an op mode will open up the main Blocks programming page. Before moving on to programming, take some time to learn and understand the following key components of Blocks featured in the image below.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMaksa1NF8Ki6mSUARF%2F-MMarRCHc5SIhgQHffKR%2FBlocks%20-%20Main%20Screen.svg?alt=media\&token=e20744af-fb2f-4519-9b57-2f3f0f65a719)

1. **Save Op Mode** - Click this button to save an op mode to the robot. It is important to save the op mode any time you stop working on a code, so that progress is not lost.&#x20;
2. **TeleOp/Autonomous** - This section of blocks allows users to change between the two types of op modes: teleop and autonomous.&#x20;
3. **Categorized Blocks** - This section of the screen is where the programming blocks are categorized and accessible. For instance, clicking **Logic** will open access to programming blocks like if/else statements.&#x20;
4. **Programming Space** - This space is where blocks are added to build programs.&#x20;

{% hint style="danger" %}
If a configuration has been made then the Actuators, Sensors, and Other Devices in the Categorized Blocks section should appear as drop down menus, where blocks that are unique to specific hardware can be accessed. If this is not the case a configuration file has not been made. For more information visit the [Configuration](../hello-robot-configuration.md) page, before moving forward with programming.&#x20;
{% endhint %}

## Programming Essentials

During the process of creating an op mode the Blocks tool prompted the selection of a sample code. In Blocks these samples act as templates; providing the blocks and logical structure for different robotics use cases. In the previous section the sample code **BasicOpMode** was selected. This sample code, seen in the image below, is the structural shell needed in order to have a working op mode.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMpuMleDxBO45eJs1yt%2F-MMpzTo0\_SfkSyeDenpk%2FBlocks%20-%20Basic%20Op%20Mode.svg?alt=media\&token=2f6cfaa7-3f90-4cf9-ae33-da4ec53ddc66)

An op mode can often be considered a set of instructions for a robot to follow in order to understand the world around it. The BasicOpMode provides the initial set of instructions that are needed in order for an op mode to properly function.&#x20;

Though this sample is given to users to reduce some of complexities of programming as they learn; it introduces some of the most important code blocks. It is also important to understand what is happening in the structure of the BasicOpMode, so that code blocks are put in the correct area.&#x20;

#### Key Op Mode Blocks

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMaksa1NF8Ki6mSUARF%2F-MMbkIxlEQkmZDqnt9Yy%2FBlocks%20-%20comments%20main.svg?alt=media\&token=f9ccb6c6-5d34-4ec1-8dad-aa1762973d86)

**Comments** are blocks of code that benefit the human user. They are used by programmers to explain the function of a section of code. This is especially helpful in collaborative programming environments. If code is handed from one programmer to another, comments communicate the intent of the code to the other programmer. Blocks like <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MMaksa1NF8Ki6mSUARF%2F-MMbu6ZmCbsuIyI-QR0s%2FBlocks%20-%20intilization%20comment.svg?alt=media&#x26;token=240d3076-8806-4661-9abc-b797b41e1888" alt="" data-size="original"> are comments written by the FIRST Tech Team to inform the user what will happen when blocks are added directly beneath the comment.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMaksa1NF8Ki6mSUARF%2F-MMbu6ZmCbsuIyI-QR0s%2FBlocks%20-%20intilization%20comment.svg?alt=media\&token=240d3076-8806-4661-9abc-b797b41e1888)

For instance, any programming blocks that are placed after the<img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVRzzz2RWu0i_oNzqo3%2FComment%20-%20Put%20intialization%20blocks.svg?alt=media&#x26;token=5b100e29-9c67-4bb3-be74-0d35d452cb76" alt="" data-size="original">comment (and before the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MWA60vPJ8ku9W4vMscg%2FClasses%20-%20waitForStart.svg?alt=media&#x26;token=7c8e15ac-67c8-4801-86fa-d9e595d8513b" alt="" data-size="original">block) will be executed when the op mode is first selected by a user at the Driver Station. Typically, blocks put in this section are meant to create and define **variables** between the initialization and start phases of the op mode.&#x20;

{% hint style="info" %}
A [variable ](https://en.wikipedia.org/wiki/Variable\_\(computer\_science\))is a storage location with an associated symbolic name, which contains some known or unknown quantity of information referred to as a value. Variables can be numbers, characters, or even motors and servos.
{% endhint %}

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMpuMleDxBO45eJs1yt%2F-MMq1iJ2ccEY2FVuDvud%2FBlocks%20-%20Wait%20for%20Start.svg?alt=media\&token=e04ba7bb-f13f-412b-81bb-e7cfa12de22d)

When the Robot Controller reaches the block <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MWA60vPJ8ku9W4vMscg%2FClasses%20-%20waitForStart.svg?alt=media&#x26;token=7c8e15ac-67c8-4801-86fa-d9e595d8513b" alt="" data-size="original"> it will stop and wait until it receives a Start command from the Driver Station. A Start command will not be sent until the user pushes the Start button on the Driver Station. Any code after the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MWA60vPJ8ku9W4vMscg%2FClasses%20-%20waitForStart.svg?alt=media&#x26;token=7c8e15ac-67c8-4801-86fa-d9e595d8513b" alt="" data-size="original"> block will get executed after the Start button has been pressed.

After the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MWA60vPJ8ku9W4vMscg%2FClasses%20-%20waitForStart.svg?alt=media&#x26;token=7c8e15ac-67c8-4801-86fa-d9e595d8513b" alt="" data-size="original">_,_ there is a conditional **if** block  <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAOWw9Me8lCfsveXqy%2FLogic%20-%20Ifdo%20(opModeIsActive).svg?alt=media&#x26;token=b7f86360-bf79-47cb-b4ce-2bf3d96f8f6b" alt="" data-size="original"> that only gets executed if the op mode is still active (i.e., a stop command hasn't been received).

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMpuMleDxBO45eJs1yt%2F-MMq8T0zaQH\_ANfSo\_gE%2FBlocks%20-%20ifdo.svg?alt=media\&token=f9cb886f-1fe8-4b66-b2fa-8fe2fe10d252)

{% hint style="info" %}
**If-then** (if-else) statements are similar to the concept of cause and effect. If cause (or condition) happens, then perform effect.&#x20;
{% endhint %}

Any blocks that are placed after the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MWACAqNiP66tvS4fGxc%2FComment%20-%20Put%20run%20blocks%20here.svg?alt=media&#x26;token=a002379b-48fb-4d1f-a08c-e2568d142683" alt="" data-size="original"> __ comment and before the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWARGR5n3WOEAJHYiC4%2FLoops%20-%20While%20(opModeIsActive).svg?alt=media&#x26;token=ba1d56e4-13dc-4ec6-b762-ea4eeb29ed36" alt="" data-size="original"> __ will be executed sequentially by the Robot Controller after the Start button has been pressed.

The <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWARGR5n3WOEAJHYiC4%2FLoops%20-%20While%20(opModeIsActive).svg?alt=media&#x26;token=ba1d56e4-13dc-4ec6-b762-ea4eeb29ed36" alt="" data-size="original"> is an **iterative or looping** control structure.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMpuMleDxBO45eJs1yt%2F-MMqBeJec8ww9lkDtKnY%2FBlocks%20-%20while.svg?alt=media\&token=55e1c068-604f-4845-9846-7dd7af375833)

This control will perform the steps listed under the “do” portion of the block as long as the condition <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW9zQx4RBqrvpcF0pji%2FClasses%20-%20Call%20Op%20mode%20active.svg?alt=media&#x26;token=427a0621-4a75-4476-aaa5-17e7c7388d99" alt="" data-size="original"> is true_._ What this means is that the statements included in the “do” portion of the block will repeatedly be executed as long as the op mode _HelloRobot\_TeleOp_ is running.&#x20;

Once the user presses the Stop button, the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW9zQx4RBqrvpcF0pji%2FClasses%20-%20Call%20Op%20mode%20active.svg?alt=media&#x26;token=427a0621-4a75-4476-aaa5-17e7c7388d99" alt="" data-size="original"> __ clause is no longer true and the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWARGR5n3WOEAJHYiC4%2FLoops%20-%20While%20(opModeIsActive).svg?alt=media&#x26;token=ba1d56e4-13dc-4ec6-b762-ea4eeb29ed36" alt="" data-size="original"> loop will stop repeating itself.

#### Functions and Methods

The previous section did not go into a detailed discussion of the purple **** [**function**](https://en.wikipedia.org/wiki/Functional\_programming) (or [**method**](https://en.wikipedia.org/wiki/Method\_\(computer\_programming\))) blocks. Functions and methods are similar procedures in programming that are more advance than what will be covered in this guide.&#x20;

For now the most important thing to know is that occasionally methods within the SDK libraries will need to be called in order to perform a certain task. For instance, the<img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW9zQx4RBqrvpcF0pji%2FClasses%20-%20Call%20Op%20mode%20active.svg?alt=media&#x26;token=427a0621-4a75-4476-aaa5-17e7c7388d99" alt="" data-size="original"> line calls the method _opModeIsActive_, which is the procedure in the SDK that is able to tell when the robot was been started or stopped.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMpuMleDxBO45eJs1yt%2F-MMqaUGi9zzpfaMsgnjh%2FBlocks%20-%20Methods.svg?alt=media\&token=f2610d23-4577-42d8-aaaf-036a606f9d8e)

When your programming skills have advanced take sometime to visit the concepts of functions and methods and explore how they can help you enhance your code.&#x20;

## Programming Actuators&#x20;

### Servo Basics

The goal of this section is to cover some of the basics of programming a servo within Blocks. By the end of this section users should be able to control a servo with a gamepad, as well as understand some of the key programming needs of the servo.&#x20;

{% hint style="info" %}
This section is considering the Smart Robot Servo in its default mode. If your servo has been changed to function in continuous mode or with angular limits it will not behave the same using the code examples below. You can learn more about the[ Smart Robot Servo](https://docs.revrobotics.com/duo-build/actuators/servos/smart-robot-servo) or changing the Servo's mode via the [SRS Programmer](https://docs.revrobotics.com/duo-build/actuators/servos/srs-programmer) by clicking the hyperlinks.&#x20;
{% endhint %}

With a typical servo, you can specify a target position for the servo. The servo will turn its motor shaft to move to the target position, and then maintain that position, even if moderate forces are applied to try and disturb its position.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MBtA\_rAKndrhw3UEHOy%2F-MBtffLxjwr8kU4I5jjV%2Fimage.png?alt=media\&token=08c50111-d056-48fc-86ec-1bd85b1b7f57)

For both Blocks and OnBot Java, you can specify a target position that ranges from 0 to 1 for a servo. For a servo with a 270° range, if the input range was from 0 to 1 then a signal input of 0 would cause the servo to turn to point -135°. For a signal input of 1, the servo would turn to +135°. Inputs between the minimum and maximum have corresponding angles evenly distributed between the minimum and maximum servo angle. This is important to keep in mind as you learn how to code servos.&#x20;

Since this section will focus on servos it is important to understand how to access servos within Blocks. At the top of the Categorize Blocks section there is a drop down menu for **Actuators**. When the menu is selected it will drop down two choices: **DcMotor** or **Servo**. Selecting Servo will open a side window filled with various servo related blocks.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNdBL4wh8RtAfHHB0zL%2F-MNeE8erC97w6RMOufZz%2FBlocks%20-%20selecting%20servo%20blocks.svg?alt=media\&token=f0a0821f-9c01-45ae-bc90-470a56317a7a)

#### Programming a Servo

From the Servo menu select the block <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAc8IF4-_ItJzHXisV%2FServo%20-%20set%20to%200.svg?alt=media&#x26;token=e58e949a-a8a7-4917-9427-4e737208328b" alt="" data-size="original">&#x20;

{% hint style="info" %}
The block above will change names depending on the name of the servo in a configuration file. If there are multiple motors in a configuration file the arrow next to test\_servo will drop down a menu of all the servos in a configuration.&#x20;
{% endhint %}

Add this block to the op mode code within the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWARGR5n3WOEAJHYiC4%2FLoops%20-%20While%20(opModeIsActive).svg?alt=media&#x26;token=ba1d56e4-13dc-4ec6-b762-ea4eeb29ed36" alt="" data-size="original"> **.** Click on the number block to change from <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAc8IF4-_ItJzHXisV%2FServo%20-%20set%20to%200.svg?alt=media&#x26;token=e58e949a-a8a7-4917-9427-4e737208328b" alt="" data-size="original"> to **** <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAcLYKFQSC3PM2Cbef%2FServo%20-%20set%20to%201.svg?alt=media&#x26;token=978c25bf-c57e-4e8f-84a0-285fdde44b2d" alt="" data-size="original"> **.**

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNdBL4wh8RtAfHHB0zL%2F-MNelnoFt4JUVdHOthEC%2Fblocks-servo%20-%20first%20block%20set.svg?alt=media\&token=fdb17d79-d269-4bcb-b0fd-783c1bb34004)

Select **Save Op Mode** in the upper right corner in the Robot Controller Console.

{% hint style="success" %}
Try running this op mode on the test bed two times and consider the following questions:

* Did the servo move during the first run?
* Did the servo move during the second run?

If the servo did not move switch from <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAcLYKFQSC3PM2Cbef%2FServo%20-%20set%20to%201.svg?alt=media&#x26;token=978c25bf-c57e-4e8f-84a0-285fdde44b2d" alt="" data-size="original"> back to <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAc8IF4-_ItJzHXisV%2FServo%20-%20set%20to%200.svg?alt=media&#x26;token=e58e949a-a8a7-4917-9427-4e737208328b" alt="" data-size="original"> and try again.&#x20;
{% endhint %}

The intent of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAcLYKFQSC3PM2Cbef%2FServo%20-%20set%20to%201.svg?alt=media&#x26;token=978c25bf-c57e-4e8f-84a0-285fdde44b2d" alt="" data-size="original"> is to set the position of the servo. If the servo is already in the set position when a code is run, it will not change positions. Lets try adding another <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAc8IF4-_ItJzHXisV%2FServo%20-%20set%20to%200.svg?alt=media&#x26;token=e58e949a-a8a7-4917-9427-4e737208328b" alt="" data-size="original"> __ block and see what changes_._&#x20;

Drag an additional <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAc8IF4-_ItJzHXisV%2FServo%20-%20set%20to%200.svg?alt=media&#x26;token=e58e949a-a8a7-4917-9427-4e737208328b" alt="" data-size="original"> __ block into the op mode code under the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVRzzz2RWu0i_oNzqo3%2FComment%20-%20Put%20intialization%20blocks.svg?alt=media&#x26;token=5b100e29-9c67-4bb3-be74-0d35d452cb76" alt="" data-size="original"> **** comment.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNdBL4wh8RtAfHHB0zL%2F-MNep4Hs9buaHiqcvOWF%2Fblocks-servo%20-%20secondblock%20set.svg?alt=media\&token=390fbcb5-15ac-4b2b-b07e-d59f93f73be2)

{% hint style="success" %}
Try running this op mode on the test bed and consider the following question:

* What is different from the previous run?
{% endhint %}

The <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAc8IF4-_ItJzHXisV%2FServo%20-%20set%20to%200.svg?alt=media&#x26;token=e58e949a-a8a7-4917-9427-4e737208328b" alt="" data-size="original"> __ that was added in the step above changes the servo position to 0 during the initialization phase, so when the op mode is run the servo will always move to position 1. For some applications starting the servo in a **known state**, like at position zero, is beneficial to the operation of a mechanism. Setting the servo to the known state in the initialization ensures it is in the correct position when the op mode runs.&#x20;

#### Programming a Servo with a Gamepad

The focus of this example is to assign certain servo positions to buttons on the gamepad. For this example the known state will stay at position 0, so that after initialization the servo will be a the -135 degree position of the servo range. The following list shows what buttons correspond with which servo position.&#x20;

{% hint style="info" %}
If you are using a PS4 Controller, like the Etpark Wired Controller for PS4 ([REV-39-1865](https://www.revrobotics.com/rev-39-1865/)), see the [Using Gamepads](./#using-gamepads) section to determine how the gamepad code used in this section translates to the PS4 Gamepad.&#x20;
{% endhint %}

| **Button** | Degree Position | Code Position |
| ---------- | --------------- | ------------- |
| Y          | -135            | 0             |
| X          | 0               | 0.5           |
| B          | 0               | 0.5           |
| A          | 135             | 1             |

The best way to switch the servo position will be to use a conditional _ `if/ else if`_ statement. An if statement considers whether a conditional statement is true or false. If the conditional statement is true a defined action (like the servo moving) is performed. If the conditional statement is false the action is not performed.&#x20;

An _`if/ else if`_statement takes in multiple different conditional statements. If the first conditional statement is found to be false then the second conditional state is analyzed. Each statement in the _ `if/ else if`_ will be analyzed one by one until a statement is found true or all statements are found false. For this example, there will be three conditions that will need to be checked.

From the **Logic** Menu in Blocks select the __ <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAm39BsREHDm26Al4M%2FLogic%20-%20ifdo%20(blank).svg?alt=media&#x26;token=ce3fdbbd-68c4-4b67-bc50-981a1e204bae" alt="" data-size="original"> block and drag in into the op mode's while loop.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MOCUO16aUQtXqwjHqb1%2F-MOD2p4k1LTDAMxJdJQF%2FBlocks%20-%20if%20do%20if%20do.svg?alt=media\&token=21b4711d-7727-4334-a8b5-0ed168ad56da)

Click on the blue and white Settings icon for the __ <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAm39BsREHDm26Al4M%2FLogic%20-%20ifdo%20(blank).svg?alt=media&#x26;token=ce3fdbbd-68c4-4b67-bc50-981a1e204bae" alt="" data-size="original"> block. This will display a pop-up menu that lets you modify the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAm39BsREHDm26Al4M%2FLogic%20-%20ifdo%20(blank).svg?alt=media&#x26;token=ce3fdbbd-68c4-4b67-bc50-981a1e204bae" alt="" data-size="original"> block.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MOCUO16aUQtXqwjHqb1%2F-MOD1C5RlmjZU9do-SyX%2Fblocks%20-%20creating%20elifs.svg?alt=media\&token=42075d92-8367-46fd-9631-1776e3c9d4fc)

Drag an <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAnBZGxGoi9TO3k6FC%2FLogic%20-%20else%20if.svg?alt=media&#x26;token=33006b12-eb23-4836-928f-9c7bcd57d0e5" alt="" data-size="original"> block from the left side of the pop-up menu and snap it into place under the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWArvlb-3XYFHtH9B4t%2FLogic%20-%20if.svg?alt=media&#x26;token=2e5db9f2-15c6-4886-8634-5553126eb918" alt="" data-size="original"> block. Drag a second <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAnBZGxGoi9TO3k6FC%2FLogic%20-%20else%20if.svg?alt=media&#x26;token=33006b12-eb23-4836-928f-9c7bcd57d0e5" alt="" data-size="original"> block from the left side and snap it into place on the right side under the first __ <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAnBZGxGoi9TO3k6FC%2FLogic%20-%20else%20if.svg?alt=media&#x26;token=33006b12-eb23-4836-928f-9c7bcd57d0e5" alt="" data-size="original"> __ block.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MOCUO16aUQtXqwjHqb1%2F-MOD4n01A0sOcYwiTOCL%2FBlocks%20-%20elif.svg?alt=media\&token=663e1574-e7f2-4baf-b21a-c68c45cc8995)

There are three different paths in this _ `if/else if`_ block. Each one corresponds with one of the three chosen servo positions 0, 0.5, and 1. However, there are four different buttons that will be used for this example. Both button B and button X should be able to move the servo to position 0.5. In order to do this the logical operator **or** needs to be used. &#x20;

{% hint style="info" %}
The logical operator **or** considers two operands if either (or both) are true the or statement is true. If both operands are false the _or_ statement is false.&#x20;
{% endhint %}

From the **Logic** Menu in Blocks select the __ <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW9yJdVdzRolyWei1gK%2FLogic%20-%20and.svg?alt=media&#x26;token=129d69e5-1d08-4d91-8eb6-77ee65a3458b" alt="" data-size="original"> __ block.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MOHTneSAfprqWldgpoU%2F-MOHrUwITP2r1YwxdbcL%2FBlocks%20-%20and%20block.svg?alt=media\&token=9dc0db3e-d2e9-4779-8894-b9565a92bef9)

Add this block to the `If/else if` block, as shown in the image below. Use the drop down menu on the block to change it from an <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW9yJdVdzRolyWei1gK%2FLogic%20-%20and.svg?alt=media&#x26;token=129d69e5-1d08-4d91-8eb6-77ee65a3458b" alt="" data-size="original"> block to an <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWB9-FbRpvUKsRz3Tbi%2Flogic%20-%20or%20block.svg?alt=media&#x26;token=28de91ba-b844-4003-9c38-0a19d6e70e17" alt="" data-size="original"> block.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MOHTneSAfprqWldgpoU%2F-MOIHFk-0ic7dmqGn6-a%2FBlocks%20-%20adding%20or.svg?alt=media\&token=b3ad93fa-f6da-433d-b71a-fe566d8b5677)

All gamepad related blocks are in the **Gamepad** Menu.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MOCUO16aUQtXqwjHqb1%2F-MODeNYnEnY6OHhGJPcj%2Fblocks%20-%20servo%20gamepad%20control.svg?alt=media\&token=3044e006-1a9a-449a-8f53-dd892de9e686)

Add each button to the `if/else if` block as seen in the image below.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MOJYlLvcofA0iXjq9FA%2F-MOXbzXh7yIqqtfiSZC5%2Fblocks%20-%20servo%20if%20else%20gamepad.svg?alt=media\&token=a8b3567a-2e63-4756-8047-8002f161195d)

Add <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWAcLYKFQSC3PM2Cbef%2FServo%20-%20set%20to%201.svg?alt=media&#x26;token=978c25bf-c57e-4e8f-84a0-285fdde44b2d" alt="" data-size="original"> blocks to each section of the _If/else if_ block. Set the servo position to correspond with the assigned gamepad button. __&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MOJYlLvcofA0iXjq9FA%2F-MOXfCyVfccuoatlLDF9%2Fblocks%20-%20servo%20if%20else%20gamepad%20finished.svg?alt=media\&token=e8e93c31-25da-49e6-b516-edb21b9aba0e)

There are three different paths in this_`if/else if`_ statement. If the first conditional statement is true (the Y button is pressed) the servo moves to code position 0 and the other conditional statements are ignored. If the first condition is false (the Y button is not pressed) the second condition is analyzed. Recall that this behavior repeats until a condition is met or all conditions have been tested and found false.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MOJYlLvcofA0iXjq9FA%2F-MOXhxUXE3uAuanEOBLV%2Fblocks%20-%20servo%20final%20code.svg?alt=media\&token=45f7adac-8cb7-4412-b4b3-746113ee50d9)

#### Servos and Telemetry&#x20;

**Telemetry** is the process of collecting and transmitting data.  In Robotics telemetry is used to output internal data from actuators and sensors to the Driver Station. This data can then be analyzed by users to make decisions that can improve code.&#x20;

The most useful telemetry from the servo is the the position of the servo along its 270 degree range. In order to get that information the following line needs to be used.&#x20;

In order to access the telemetry blocks select the **Utilities** drop down. The utilities drop down is in alphabetical order, so telemetry is towards the bottom of the drop down options. Select the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBCD-8cdq6zfjWEnDn%2FTelemetry%20-%20key%20and%20number.svg?alt=media&#x26;token=bbc24af7-4844-414c-bcc6-fa0ed1ba1efe" alt="" data-size="original"> block from the telemetry menu.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMw\_wgvL4PSQqA7a9Dc%2F-MN0G4nTqozJhWgKlDi3%2FBlocks%20-%20telemetry%20select.svg?alt=media\&token=df3cc456-bdee-4038-a1a0-0d3dc9265cb0)

Drag the __ <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBCD-8cdq6zfjWEnDn%2FTelemetry%20-%20key%20and%20number.svg?alt=media&#x26;token=bbc24af7-4844-414c-bcc6-fa0ed1ba1efe" alt="" data-size="original"> block and place it beneath the_`if/else if`_ block set.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MOJYlLvcofA0iXjq9FA%2F-MOXlG9lFnMward0t0H-%2Fblocks%20-%20servo%20telemetry.svg?alt=media\&token=5854db7b-774b-489c-a3c8-4686be82676c)

From the **Servo** menu pullout the block <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBETk3wvRYKbvYxj0p%2FServo%20-%20servo%20value.svg?alt=media&#x26;token=a3e33f56-9b3e-461d-888c-dfe234296d47" alt="" data-size="original"> Drag the Block and attach it to the number **parameter** on the telemetry blocks.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MOJYlLvcofA0iXjq9FA%2F-MOXm62ScLxui-9zOPzG%2FBlocks%20-%20.position.svg?alt=media\&token=0b00ac2d-cd90-49fb-8761-1e5d50a4a4bf)

Change the key parameter to "Servo Position"&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MOJYlLvcofA0iXjq9FA%2F-MOXmhLO0lm-X1DQyrZq%2Fblocks%20-%20servo%20telemetry%202.svg?alt=media\&token=73dc3d2f-725e-4e2e-b4d5-82729b4d6663)

When the op mode is run the telemetry block will display the current position information will be displayed with the Servo Position Key. The number that corresponds with the current position will change as the servo shaft position changes.

### Motor Basics&#x20;

{% hint style="warning" %}
Modify your op mode to add the motor related code. This can be done by clearing out your current code modifications or adding the motor related code to your current op mode.&#x20;
{% endhint %}

The goal of this section is to cover some of the basics of programming a motor within Blocks. By the end of this section users should be able to control a motor using a gamepad, as well as understand some of the basics of working with motor encoders.&#x20;

Since this section will focus on motors it is important to understand how to access motors within Blocks. At the top of the Categorize Blocks section there is a drop down menu for **Actuators**. When the menu is selected it will drop down two choices: **DcMotor** or **Servo**. Selecting DC Motor will open a side window filled with various motor related blocks.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNdBL4wh8RtAfHHB0zL%2F-MNeG90CRUDslXVSylCi%2FBlocks%20-%20Finding%20motors.svg?alt=media\&token=356ac737-7028-467e-bb53-d2a1b4f5884b)

#### Driving Motors&#x20;

From the Dc Motor menu in Blocks select the block __ <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBG9sHCXphC82ifCqS%2FMotor%20-%20%20testmotor%20set%20power.svg?alt=media&#x26;token=41a570cb-db24-4cc9-a41f-7bbd92ce8ff2" alt="" data-size="original"> _._

{% hint style="info" %}
The block above will change names depending on the name of the motor in a configuration file. If there are multiple motors in a configuration file the arrow next to test\_motor will drop down a menu of all the motors in a configuration.&#x20;
{% endhint %}

Add this block to the op mode code within the **while loop**.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMv8gv8JkbM6WI5d7mX%2F-MMwGssZgjuifm2hXVEl%2FBlocks%20-%20test%20motor%20full%20code.svg?alt=media\&token=41d33c4f-d881-4b87-a888-5c9809233247)

Select **Save Op Mode** in the upper right corner in the Robot Controller Console.

{% hint style="success" %}
Try running this op mode on the test bed and consider the following questions:

* How fast is the motor running?&#x20;
* What happens if you change the power from **1** to **0.3**?
* What happens if you change the power to **-1**?
{% endhint %}

The level of power sent to the motor is dependent on the numerical number assigned to the motor. The change from 1 to 0.3 decreased the motors speed from 100% of duty cycle to 30% of duty cycle. Meanwhile, the change to -1 allowed the motor to rotate at 100% duty cycle in the opposite direction. So, power can be fluctuated to drive a motor _forward_ or _backwards_.&#x20;

However, the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBG9sHCXphC82ifCqS%2FMotor%20-%20%20testmotor%20set%20power.svg?alt=media&#x26;token=41a570cb-db24-4cc9-a41f-7bbd92ce8ff2" alt="" data-size="original"> block will run the motor in the assigned direction until something in the code stops the motor or causes a change in direction.&#x20;

{% hint style="info" %}
To better understand motors and the concept of duty cycle check out the our [Motors ](https://docs.revrobotics.com/15mm/actuators/motors)and [Choosing an Actuator](https://docs.revrobotics.com/15mm/actuators/choosing-an-actuator) documentation.&#x20;
{% endhint %}

#### Driving Motors with the Gamepad&#x20;

In the previous section you learned how to set the motor to run at a specific power level in a specific direction. However, in some applications, it may be necessary to control the motor with a gamepad, to easily change the direction or power level of a mechanism.&#x20;

From the Gamepad Menu in Blocks select the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBHSepopUHbk0AbzGq%2Fgamepad%20-%20leftsticky.svg?alt=media&#x26;token=214b31c1-622c-4913-884c-a6b9d2e6ebb9" alt="" data-size="original"> __ Block_._&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMv8gv8JkbM6WI5d7mX%2F-MMw6P788Rxd4dHcmJza%2FBlocks%20-%20LeftStickY%20selection.svg?alt=media\&token=c37aa912-adec-4d82-9490-3dfdd84156e8)

Drag the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBHSepopUHbk0AbzGq%2Fgamepad%20-%20leftsticky.svg?alt=media&#x26;token=214b31c1-622c-4913-884c-a6b9d2e6ebb9" alt="" data-size="original"> block so it snaps in place onto the right side of the __ <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBG9sHCXphC82ifCqS%2FMotor%20-%20%20testmotor%20set%20power.svg?alt=media&#x26;token=41a570cb-db24-4cc9-a41f-7bbd92ce8ff2" alt="" data-size="original"> block. This set of blocks will continually loop and read the value of gamepad #1’s left joystick (the y position) and set the motor power to the Y value of the left joystick.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMv8gv8JkbM6WI5d7mX%2F-MMwHFmk6X27q5uMv35j%2FBlocks%20-%20Gamepad1%20motor%20power.svg?alt=media\&token=6fd0408d-7123-491e-9a12-92335d17f045)

Note that for the Logitech F310 gamepads, the Y value of a joystick ranges from -1, when a joystick is in its topmost position, to +1, when a joystick is in its bottommost position. If the motor is not running in the intended direction adding a **negative symbol**, or negation operator, to the line of code will change the direction of the motor in relation to the gamepad.&#x20;

From the **Math** Menu in Blocks select the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBJQVp02qR-776BhMA%2FMath%20-%20negatives.svg?alt=media&#x26;token=de3bec61-c328-4b6e-be0c-9c89c64e112b" alt="" data-size="original"> block in the image below_._&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNZ4vrQq5bO6kOESz-Y%2F-MN\_ZU7TL-UPxm1tPCyR%2FBlocks%20-%20negative%20symbolselection.svg?alt=media\&token=720e79ba-a473-406b-a15e-f40511d82432)

Drag the negative symbol block so it snaps in place between the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBG9sHCXphC82ifCqS%2FMotor%20-%20%20testmotor%20set%20power.svg?alt=media&#x26;token=41a570cb-db24-4cc9-a41f-7bbd92ce8ff2" alt="" data-size="original"> and <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBHSepopUHbk0AbzGq%2Fgamepad%20-%20leftsticky.svg?alt=media&#x26;token=214b31c1-622c-4913-884c-a6b9d2e6ebb9" alt="" data-size="original"> __ blocks.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMv8gv8JkbM6WI5d7mX%2F-MMwSxFtPuBm3rJNcmuN%2FBlocks%20-%20negation%20operator%20for%20motor%20control.svg?alt=media\&token=b8f9b350-a37e-4a81-b79d-9f3f6f0e3643)

#### Motors and Telemetry&#x20;

Recall that **telemetry** is the process of collecting and transmitting data.  In Robotics telemetry is used to output internal data from actuators and sensors to the Driver Station. This data can then be analyzed by users to make decisions that can improve code.

In order to gain telemetry data from the motor, motor encoders need to be used. REV DC Motors, like the Core Hex Motor, are equipped with internal encoders that relay information in the form of counts.&#x20;

In order to access the telemetry blocks select the **Utilities** drop down. The utilities drop down is in alphabetical order, so telemetry is towards the bottom of the drop down options. Select the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBJfpbTuatRMfbhnlO%2FTelemetry%20-%20key%20and%20number.svg?alt=media&#x26;token=d6f21b70-8197-4ead-954a-2604cfb72155" alt="" data-size="original"> block from the telemetry menu.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMw\_wgvL4PSQqA7a9Dc%2F-MN0G4nTqozJhWgKlDi3%2FBlocks%20-%20telemetry%20select.svg?alt=media\&token=df3cc456-bdee-4038-a1a0-0d3dc9265cb0)

Drag the __ <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBJfpbTuatRMfbhnlO%2FTelemetry%20-%20key%20and%20number.svg?alt=media&#x26;token=d6f21b70-8197-4ead-954a-2604cfb72155" alt="" data-size="original"> block and place it beneath the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBKtkCEeCGzWbwuI34%2FCombo%20Block%20%20-%20set%20power%20to%20negatibve%20leftsticky.svg?alt=media&#x26;token=8a411797-6d87-4064-a2af-5ecaceb3a8f2" alt="" data-size="original"> __ block set.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMw\_wgvL4PSQqA7a9Dc%2F-MN0Z-DAnJ7lW3w7e150%2FBlocks%20-%20adding%20motor%20telelmetry.svg?alt=media\&token=5d70687a-7e68-466f-857f-f03940b8edf9)

From the DC Motor menu pullout the block <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBOGk55UYqpXnAAa0V%2FMotor%20-%20test_motor%20current%20position.svg?alt=media&#x26;token=fa1b1e27-5f53-49d5-a4b2-ef4e79cbfcb3" alt="" data-size="original"> . Drag the Block and attach it to the number **parameter** on the telemetry blocks.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMw\_wgvL4PSQqA7a9Dc%2F-MN0aDxqhiJfxT2MLn3O%2Ftest\_motor.currenrPosition.svg?alt=media\&token=4383c677-94f4-4bf3-9d36-489ab2afdcb6)

Change the key parameter to "Counts Per Revolution: "&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMw\_wgvL4PSQqA7a9Dc%2F-MN0\_0aazlEqpFgmIK-2%2FBlocks%20-%20counts%20per%20rev%20telemetry.svg?alt=media\&token=5a209c7c-b895-4b99-92d7-9b5333a4c0b7)

When the op mode is run the telemetry block will display the current position information will be displayed with the Counts Per Revolution Key. The number that corresponds with the current position will change as the motor shaft position is changed.&#x20;

{% hint style="info" %}
For more information on programming encoders check out the [Using Encoders](../using-encoders.md) page. For more information the counts per revolution metric and how to use it check out the[ Encoders ](../../sensors/encoders/)page.&#x20;
{% endhint %}

## Programming Sensors&#x20;

### Touch Sensor Basics

{% hint style="warning" %}
Modify your op mode to add the digital device related code. This can be done by clearing out your current code modifications or adding the digital device code to your op mode.&#x20;
{% endhint %}

The goal of this section is to cover some of the basics of programming a digital device, or Touch Sensor, within Blocks.&#x20;

Since this section will focus on digital devices it is important to understand how to access digital device specific blocks. At the top of the Categorize Blocks section there is a drop down menu for **Other Devices**. When the menu is selected it will drop down an option for **Digital Devices.** Selecting Digital Devices will open a side window filled with various digital device related blocks. The one that will most commonly be used is __ <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBS-GvXt4u8yqE8N_X%2FTouch%20-%20test_touch%20state.svg?alt=media&#x26;token=08c36ffa-5fd3-46c6-baa8-a79dcfce2abe" alt="" data-size="original"> .

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMw\_wgvL4PSQqA7a9Dc%2F-MN0llD0-rUrxyzyBWIk%2FBlocks%20-%20grabbing%20digital%20device%20info.svg?alt=media\&token=eb5e2e87-d0e8-4091-becc-90e7083e8461)

{% hint style="info" %}
Before programming with a Touch Sensor or other digital device it is important to understand what a digital device is and what the common applications for digital devices are. Visit the [Digital Sensors ](../../sensors/digital.md)page for more info.&#x20;
{% endhint %}

#### Programming a Digital Device

The information from digital devices comes in two states, also known as binary states. The most common way to utilize this information is to use a conditional statement like an `if/else` statement.&#x20;

From the **Logic** Menu in Blocks select the __ <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBUDlUpVQmk7Y7zght%2FLogic%20-%20if%20else.svg?alt=media&#x26;token=d48d4eec-5bcf-4086-aa74-b080fbb0527b" alt="" data-size="original"> __ block.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNZ4vrQq5bO6kOESz-Y%2F-MN\_Ybpbmv6KFQkXfGFd%2FBlocks%20-%20ifdo.svg?alt=media\&token=471135d1-21bd-4a13-bb80-46b4ebb2e798)

Drag the __ <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBUDlUpVQmk7Y7zght%2FLogic%20-%20if%20else.svg?alt=media&#x26;token=d48d4eec-5bcf-4086-aa74-b080fbb0527b" alt="" data-size="original"> __ block and place it beneath the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWPfpmWuWVqh1EweC06%2FComment%20-%20Put%20loop%20blocks.svg?alt=media&#x26;token=f8741193-0083-4e16-8d7c-0ca7277c2dde" alt="" data-size="original"> __ comment.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNZ4vrQq5bO6kOESz-Y%2F-MN\_Y8BMC2UJqtzZSv8q%2Fblocks%20\_ts%20adding%20if%20do.svg?alt=media\&token=6127b75d-9a93-4c05-899b-02c38e135ae9)

Select a <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBS-GvXt4u8yqE8N_X%2FTouch%20-%20test_touch%20state.svg?alt=media&#x26;token=08c36ffa-5fd3-46c6-baa8-a79dcfce2abe" alt="" data-size="original"> __ block from the Digital Devices menu and add it to the _if/do/else_ block as shown in the image below.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNOuurQM3\_5onapKgnu%2F-MNQO0DRQsCuktziXgGe%2FBlocks%20-%20ts%20-%20add%20statwe.svg?alt=media\&token=acff2b1b-0d3e-4984-a3f3-8b1eda2d6d8f)

The <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBS-GvXt4u8yqE8N_X%2FTouch%20-%20test_touch%20state.svg?alt=media&#x26;token=08c36ffa-5fd3-46c6-baa8-a79dcfce2abe" alt="" data-size="original"> block stores the binary `FALSE/TRUE` information from the touch sensor and acts as the condition for the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBUDlUpVQmk7Y7zght%2FLogic%20-%20if%20else.svg?alt=media&#x26;token=d48d4eec-5bcf-4086-aa74-b080fbb0527b" alt="" data-size="original"> statement. If <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBS-GvXt4u8yqE8N_X%2FTouch%20-%20test_touch%20state.svg?alt=media&#x26;token=08c36ffa-5fd3-46c6-baa8-a79dcfce2abe" alt="" data-size="original"> is true, any code placed in the do portion of the block will be activated. If <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBS-GvXt4u8yqE8N_X%2FTouch%20-%20test_touch%20state.svg?alt=media&#x26;token=08c36ffa-5fd3-46c6-baa8-a79dcfce2abe" alt="" data-size="original"> is false anything placed in the else portion of the clock will be activated

The `FALSE/TRUE`state of a REV Touch Sensor corresponds with whether or not the button on the Touch Sensor is pressed. When the button is not pressed the state of the Touch Sensor is True. When the button is pressed the state of the Touch Sensor is False,&#x20;

To help remember how the physical and digital states of the sensor correspond in the next few sections lets use some comments.&#x20;

Comment blocks can be found in the **Miscellaneous** menu.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNOuurQM3\_5onapKgnu%2F-MNQFMBgyjixgTpvW9zw%2FBlocks%20-%20comments%202.svg?alt=media\&token=aeb56dad-4d06-4997-a170-dda02a516aa6)

Place one comment block in the do portion of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBUDlUpVQmk7Y7zght%2FLogic%20-%20if%20else.svg?alt=media&#x26;token=d48d4eec-5bcf-4086-aa74-b080fbb0527b" alt="" data-size="original"> block and change the comment to say <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWPnQmEThS1pV-sQmW1%2FComments%20-%20Touch%20is%20Not%20Pressed.svg?alt=media&#x26;token=16be69cf-f81a-4ba5-bada-3a9f33046bc4" alt="" data-size="original"> Add another comment to the else portion of the block and change that comment to say <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWPnWFl3eEG9TUCCEpc%2FComments%20-%20Touch%20is%20Pressed.svg?alt=media&#x26;token=db399b82-c429-44a7-bcbe-3ffdc25b90ef" alt="" data-size="original"> , as shown in the image below.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNUOS40tGaeGAIcjc0S%2F-MNVO42PkOQXnuauij0K%2FBlocks\_Ts\_add%20comments.svg?alt=media\&token=33f2ff55-a23f-4c99-b987-ecec692bebca)

The next step in the process is to use telemetry to display the status of the Touch Sensor on the Driver Station phone. To do this, lets create a **string** variable called __ `touchStatus`.&#x20;

{% hint style="info" %}
[String](https://en.wikipedia.org/wiki/String\_\(computer\_science\)#String\_datatypes) refers to data that consists of a sequence of characters.
{% endhint %}

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNZ4vrQq5bO6kOESz-Y%2F-MNZTp2m4EJRsshROIVh%2Fblocks%20-%20creating%20variables.svg?alt=media\&token=71f0e3bb-97a4-4fb0-8934-28d9ed5f4336)

1. Click on the **Variables** menu. This will open a side window&#x20;
2. Select the _Create variable..._ block
3. A prompt from the FIRST Robot Controller will appear asking for a name for the variable. Name the variable `touchStatus`. Click okay&#x20;

This process created a variable named `touchStatus`. Currently `touchStatus` is undefined, in order to define it the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWPpY_sCEUimdduoxN7%2FVariable%20-%20set%20touchStatus.svg?alt=media&#x26;token=98d531ec-9c6c-4c37-b0fd-5aa1e82de884" alt="" data-size="original"> __ block needs to be used. This block can be found in the **Variables** menu now that the variable has been created.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNZ4vrQq5bO6kOESz-Y%2F-MNZXmM25ci4RqqfL9bp%2Fselecting%20variable%20specific%20code.svg?alt=media\&token=461c128c-9c85-4e5f-a579-43cee8f74753)

Drag a <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWPpY_sCEUimdduoxN7%2FVariable%20-%20set%20touchStatus.svg?alt=media&#x26;token=98d531ec-9c6c-4c37-b0fd-5aa1e82de884" alt="" data-size="original"> block and place it beneath the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWPnQmEThS1pV-sQmW1%2FComments%20-%20Touch%20is%20Not%20Pressed.svg?alt=media&#x26;token=16be69cf-f81a-4ba5-bada-3a9f33046bc4" alt="" data-size="original"> comment block. Add another <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWPpY_sCEUimdduoxN7%2FVariable%20-%20set%20touchStatus.svg?alt=media&#x26;token=98d531ec-9c6c-4c37-b0fd-5aa1e82de884" alt="" data-size="original"> __ block to the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBUDlUpVQmk7Y7zght%2FLogic%20-%20if%20else.svg?alt=media&#x26;token=d48d4eec-5bcf-4086-aa74-b080fbb0527b" alt="" data-size="original"> block set under the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWPnWFl3eEG9TUCCEpc%2FComments%20-%20Touch%20is%20Pressed.svg?alt=media&#x26;token=db399b82-c429-44a7-bcbe-3ffdc25b90ef" alt="" data-size="original"> comment.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNZ4vrQq5bO6kOESz-Y%2F-MN\_XR87hZyiQY4LbLZk%2Fblocks%20-%20adding%20touchStatus.svg?alt=media\&token=325674d7-d928-4d12-9264-8e9f2d0405b8)

The  <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWPpY_sCEUimdduoxN7%2FVariable%20-%20set%20touchStatus.svg?alt=media&#x26;token=98d531ec-9c6c-4c37-b0fd-5aa1e82de884" alt="" data-size="original">block allows you to define the `touchStatus` variable. Depending on what the status is of the touch sensor is, `touchStatus`will be set to a different string. For this select the string <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWQ1Sti6_zke6WN3-gF%2FString%20-%20String%20block%20blank.svg?alt=media&#x26;token=ace2e861-0ecc-4bcd-9981-324447a4e1f9" alt="" data-size="original"> block from the **Text** menu, as seen in the image below.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNZ4vrQq5bO6kOESz-Y%2F-MN\_UYAthamkPBbPdyk-%2Fstring.svg?alt=media\&token=697f7a65-b715-444d-96bc-78a428cad188)

Attach a string block to both <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWPpY_sCEUimdduoxN7%2FVariable%20-%20set%20touchStatus.svg?alt=media&#x26;token=98d531ec-9c6c-4c37-b0fd-5aa1e82de884" alt="" data-size="original"> blocks. Fill the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWQ1Sti6_zke6WN3-gF%2FString%20-%20String%20block%20blank.svg?alt=media&#x26;token=ace2e861-0ecc-4bcd-9981-324447a4e1f9" alt="" data-size="original"> blocks with a status message that relates to the state of the Touch Sensor. For instance, <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWQ1_LwuIJwVAjFkTvy%2FString%20-%20not%20pressed.svg?alt=media&#x26;token=e20c1f7f-875b-4605-9d37-2cdb08914771" alt="" data-size="original"> and <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWQ1d-fE0tUOTRTxSJi%2FString%20-%20pressed.svg?alt=media&#x26;token=78f2b974-a0cb-4e7c-ae34-fd2266021f81" alt="" data-size="original"> .

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNZ4vrQq5bO6kOESz-Y%2F-MN\_bMzlCzW0HlxclPV-%2Fnaming%20strings.svg?alt=media\&token=212d3730-59f6-4690-99a8-caa955a61d2c)

To display this information on the Driver Station phone[ telemetry ](test-bed-onbot-java.md#motors-and-telemetry)must be used. In order to access the telemetry blocks select the **Utilities** drop down. The utilities drop down is in alphabetical order, so telemetry is towards the bottom of the drop down options. Select the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWQ4WzzLea_Forb_Xmr%2FTelemetry%20-%20key%20and%20text.svg?alt=media&#x26;token=4fb4a99f-af99-42cc-8a5d-8862b8372e1a" alt="" data-size="original"> block from the telemetry menu.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNZ4vrQq5bO6kOESz-Y%2F-MN\_faAv8gEyq6bYGiOZ%2FBlocks%20-%20telemetry%20select2.svg?alt=media\&token=9711f531-9a4b-41ef-a610-495e111cd08d)

Drag the __ <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWQ4WzzLea_Forb_Xmr%2FTelemetry%20-%20key%20and%20text.svg?alt=media&#x26;token=4fb4a99f-af99-42cc-8a5d-8862b8372e1a" alt="" data-size="original"> block and place it beneath the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBUDlUpVQmk7Y7zght%2FLogic%20-%20if%20else.svg?alt=media&#x26;token=d48d4eec-5bcf-4086-aa74-b080fbb0527b" alt="" data-size="original"> block set.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNZ4vrQq5bO6kOESz-Y%2F-MN\_hi3Q-b0w2\_iSJXZh%2Fblocks%20-%20ts%20-%20add%20telemetry.svg?alt=media\&token=f598ddbd-4e2d-4663-9c6d-f5a787e6d34d)

From the Variables menu select the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWQ6habgSK0WCNMfHN-%2FVariable%20-%20touchStatue.svg?alt=media&#x26;token=6771a49d-678d-4be5-9172-187e259f40c4" alt="" data-size="original"> __ block. Drag the Block and attach it to the text **parameter** on the telemetry block.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNZ4vrQq5bO6kOESz-Y%2F-MN\_jB\_7jUbCvgo20vRG%2Ftouch%20status.svg?alt=media\&token=e4992947-b252-40ee-9de4-bf9b2fbde8ba)

Change the key parameter to "Button Status: "&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNZ4vrQq5bO6kOESz-Y%2F-MN\_kXi8wjFPIzcFc--j%2Fblocks%20-%20ts%20-telemetry%20finished.svg?alt=media\&token=c23b0349-bdcb-492d-aabd-86e539d36e0b)

When this program is run the `touchStatus` telemetry will appear on the Driver Station phone. The `touchStatus` information will change based on the state of the Touch Sensor button.&#x20;

#### Digital Devices as Limit Switches&#x20;

One of the most common uses for a digital device like a touch sensor is to use it as a [limit switch](../../sensors/digital.md#applications). The intent of a limit switch is to stop a mechanism, like an arm or lift, before it exceeds its physical limitations. In this application power needs to be cut from the motor when the limit is met.&#x20;

The concept of a limit switch involves many of the same steps from the previous section on programming a digital device. For that reason lets pick up from the following block set:

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNUOS40tGaeGAIcjc0S%2F-MNVO42PkOQXnuauij0K%2FBlocks\_Ts\_add%20comments.svg?alt=media\&token=33f2ff55-a23f-4c99-b987-ecec692bebca)

The <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBUDlUpVQmk7Y7zght%2FLogic%20-%20if%20else.svg?alt=media&#x26;token=d48d4eec-5bcf-4086-aa74-b080fbb0527b" alt="" data-size="original"> block establishes a conditional environment for the limit switch. If the touch sensor is not pressed the motor can run, however, if it is pressed the motor can not run. To add this to the code the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWQ6yOrHotHNULEWsLB%2FMotor%20-%20%20testmotor%20set%20power.svg?alt=media&#x26;token=3b1c4ca7-a303-4fdf-9434-c9f456fd5e3a" alt="" data-size="original"> block needs to be used.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MMqveSKZ\_mfcBDKtjad%2F-MMrFOQLZ\_4IVGLK2QUy%2Ftest%20motor%20power.svg?alt=media\&token=acbaf3ac-66e6-48ee-a5cb-f0e6109496c6)

{% hint style="info" %}
For information on where to find motor specific blocks please revisit the [motor ](test-bed-blocks.md#motor-basics)section.&#x20;
{% endhint %}

Add a <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWQ6yOrHotHNULEWsLB%2FMotor%20-%20%20testmotor%20set%20power.svg?alt=media&#x26;token=3b1c4ca7-a303-4fdf-9434-c9f456fd5e3a" alt="" data-size="original"> block under the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWPnQmEThS1pV-sQmW1%2FComments%20-%20Touch%20is%20Not%20Pressed.svg?alt=media&#x26;token=16be69cf-f81a-4ba5-bada-3a9f33046bc4" alt="" data-size="original"> comment. Change the power to 0.3. Add another <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWQ6yOrHotHNULEWsLB%2FMotor%20-%20%20testmotor%20set%20power.svg?alt=media&#x26;token=3b1c4ca7-a303-4fdf-9434-c9f456fd5e3a" alt="" data-size="original"> block under the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWBfZTWW7pkkhMBnEix%2F-MWPnWFl3eEG9TUCCEpc%2FComments%20-%20Touch%20is%20Pressed.svg?alt=media&#x26;token=db399b82-c429-44a7-bcbe-3ffdc25b90ef" alt="" data-size="original"> comment. Change the power to 0.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MNdBL4wh8RtAfHHB0zL%2F-MNdfESil3WCVVQOA9f2%2Fblocks%20-%20ls%20-%20adding%20motor%20info.svg?alt=media\&token=1167ffa3-5c95-4355-b894-f959a322ceba)

This <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWACJyDlnpPjKwQvDeW%2F-MWBUDlUpVQmk7Y7zght%2FLogic%20-%20if%20else.svg?alt=media&#x26;token=d48d4eec-5bcf-4086-aa74-b080fbb0527b" alt="" data-size="original"> block introduces the basics of a limit switch. Like with most sensors, its good to have telemetry that updates the Driver Station on the status of the sensor. Consider the code from the previous section, or the following code as potential ideas for telemetry.

<figure><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MNdBL4wh8RtAfHHB0zL%2F-MNdhbYoQe5Pf6JbN4v4%2Fblocks-Limit%20switch.svg?alt=media&#x26;token=6b8f2af0-8fa6-488e-8aaf-400ca2a8ca35" alt=""><figcaption></figcaption></figure>
