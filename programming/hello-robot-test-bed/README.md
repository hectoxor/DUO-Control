# Hello Robot - Test Bed

One of the most important steps in the engineering design process and the software development lifecycle is testing. When working with code, ensuring that it works without errors and works to the standard decided upon in the planning stage of the process is crucial.  In order to ensure that the code is working as intended testing needs to be performed. &#x20;

Before delving into the introduction to programming sections, [Test Bed - Blocks](test-bed-blocks.md) or [Test Bed - OnBot Java](test-bed-onbot-java.md); its important to understand testing, the benefits of creating a test bed, the components needed for the next sections, and how to use gamepads. Follow through the rest of this section to learn more about testing!

| Section                              | Goals of Section                                                                                                                                         |
| ------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Testing Basics ](./#testing-basics) | Learn why is one of the most important aspects of Software Development and how it differs from troubleshooting.                                          |
| [Test Bed](./#test-bed)              | Why creating a test bed of actuators and sensors can help with programming. This test bed, or something equivalent, will be used in following sections.  |
| [Using Gamepads](./#using-gamepads)  | Understanding the naming conventions for programming a gamepad.                                                                                          |

{% hint style="info" %}
Keep in mind that this is the introduction to the basic programming guide. [Test Best - Blocks ](test-bed-blocks.md)and [Test Bed - OnBot Java](test-bed-onbot-java.md) will walk you through the basics of programming with the REV Control System.&#x20;
{% endhint %}

## Testing Basics&#x20;

The purpose of testing is to identify, isolate, and correct potential issues in a design before the design is put into use. Testing takes on different forms or provides different metrics for various intents in design. A mechanism,  like a shooter for instance, might be tested to confirm that it is running reliably. During the planning phase of the design process you should create various performance, quality, and reliability metrics. When the design is built, or the program is written, these metrics will help you identify **** whether the mechanism meets the standards you expect it to. If the standards of operation are not met then the problem needs to be isolated.&#x20;

In order to fix a problem in the design process, you must isolate the source of the issue. To understand how this works consider the following example:

{% hint style="success" %}
A team has recently purchased a Control Hub and a Core Hex Motor. They plug the Core Hex Motor into the Control Hub using the correct wiring, but when they go to run their code the motor doesn't move. What is the most likely reason for this failure:

1. The program is the issue&#x20;
2. The motor is the issue
3. The wire connecting the motor to the Hub is the issue&#x20;
4. The Hub is the issue.&#x20;
{% endhint %}

Without more information there is not a good way to discover why the motor is not running. In order to narrow things down the different components have to be tested until the root of the issue is found. Common practice is to start with a code that is known to work, such as one of the sample codes in the SDK. If the motor still doesn't run the next thing the team should check is whether or not the wires are working as intended. One by one the team should go through and test, or troubleshoot, the different potential origins of the problem to see what is working and what isn't.&#x20;

Once the source of an issue has been isolated, the issue needs to be corrected. The duration of the fix depends on the sources of the problem and how deep it runs. For instance, if an op mode doesn't work as intended the fix may be a simple change, like to the configuration file or the hardwareMap.  A larger issue that requires a redesign, like a mechanism not meeting performance metrics, triggers a restart of the engineering design process.

### Testing vs. Troubleshooting&#x20;

Previously, testing was defined as the process of identifying, isolating, and correcting potential issues during the design process. This differs from troubleshooting which is the process of identifying, isolating, and correcting issues of a mechanism that went through the testing process and worked as intended.&#x20;

In the [troubleshooting section](broken-reference) the examples of a cars check engine light was used. In this example, the known indicator of a failure was the cars engine light. The check engine light informs the driver that something is wrong with the car but in order to find the cause of the issue troubleshooting and diagnostic steps must be performed. To maintain that comparison, testing is what the engineers of the car use to establish the metrics of expected engine performance. If those standards are not met then the check engine light turns on to warn the driver of the issue.&#x20;

## Test Bed&#x20;

One of the fallbacks to **testing** code in a system of components, like the REV Control System, is that there is not a guarantee that all components are functioning as they should be. For instance, if a motor on the robot isn't working there are several potentials reasons for the failure. The motor, the motor port on the Control Hub, the wire connecting the motor to the port, and the code are all potential causes of motor failure.&#x20;

If a failure occurs after the Robot is assembled it can be hard to go back and make changes, or **troubleshoot** without having to disassemble the robot. One of the ways to plan ahead for this circumstance is to create a test bed prior to creating a robot.&#x20;

{% hint style="info" %}
When testing code do not assume that a failure is due to the mechanism rather than the code. [Testing and troubleshooting](./#testing-vs.-troubleshooting), while being similar concepts, are fundamentally different. Checking the code or using a known code that works should always occur before troubleshooting components like actuators and sensors.&#x20;
{% endhint %}

A **test bed** is a testing environment for hardware and software components, commonly used in the engineering world. Test bed applications includes a broad range of different equipment and measurement testing. In some cases a test bed is a piece of equipment for testing a specific product, in other cases it is a system of components that create a testing environment. Regardless, the end goal of a test bed is to ensure a component is working before it is used for its intended purpose.&#x20;

Creating a test bed eases the process of troubleshooting if there is a failure during code testing. The purpose of this section is to create a test bed to test basic code in the Test Bed - Blocks and Test Bed - OnBot Java sections.

#### Creating a Test Bed&#x20;

The design of a test bed depends on the use case and available resources. For instance, one of the design requirements for the test bed featured below was accessibility. Notice that the placement of the hardware components on the Extrusion allows for the actuators, sensors, and Control Hub to be removed or swapped out with ease.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MP6VrNaGfoArSJpmaFB%2F-MP6buoAEDmow92oEQPr%2FIMG\_6726%202.svg?alt=media\&token=83f04406-8e9e-4c6f-a643-ff8d1f4f3049)

Another major design consideration for this test bed was that it include the common components necessary to teach users the basics of programming with the REV Control System. In this case components were chosen from the REV FTC Starter Kit.&#x20;

1. Control Hub&#x20;
2. REV Core Hex Motor&#x20;
3. Smart Robot Servo&#x20;
4. Touch Sensor&#x20;
5. Color Sensor V3
6. Battery&#x20;

{% hint style="info" %}
Any one of these test beds components can be swapped out for an equivalent component. For instance, if you have an Expansion Hub rather than a Control Hub. However, with an Expansion Hub you may need to consider placement for the Robot Controller Phone.&#x20;
{% endhint %}

There are other minor, but important, design considerations to make for a test bed. For example, when adding an actuator to a test bed consider the following questions:

* **What level of constraint does the actuator need?** One of the benefits of creating a test bed for motors, or other actuators, is that the motors can be properly constrained during the testing process. In this case providing basic motion support and constraint is valuable.&#x20;
* **How will you be able to tell the behavior of the actuator?** The example test bed uses a wheel with a zip tie to help users visualize the behavior of the motor. Tape or other markers can be used, as well.&#x20;

For the purpose of this guide a test bed similar to the example one can be built.

## Using Gamepads

The Test Bed sections highlights the necessary robot components needed to learn the basic programming concepts used in the Test Bed - Blocks and Test Bed - OnBot Java sections. However, there are two more components needed to succeed in testing your code: A Driver Hub (or equivalent Driver Station Android Device) and a gamepad.

{% hint style="info" %}
For information on setting up a Driver Hub and gamepad please visits the [Getting Start with Driver Hub](../../nachalo-raboty-s-driver-hub.md) guide.
{% endhint %}

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Mef03GnAoBcRAuOvVBl%2F-MefIm2DvUiOnc92AXOR%2Fgamepad%20and%20driver%20hub.svg?alt=media\&token=c389678c-0ab8-40d9-a046-baed376f2584)

All buttons on a gamepad can be programmed to a specific task or behavior. Throughout the Hello Robot Guide you will encounter several different places where the gamepad is utilized. Knowing the general naming convention for the gamepads will help you program them correctly. The guide assumes you are using either a Logitech gamepad or a PS4 gamepad, like Etpark Wired Controller for PS4 ([REV-39-1865](https://www.revrobotics.com/rev-39-1865/)). To understand how to program a gamepad, especially with difference in the way certain buttons are named, please see the following graphic and table, showcasing what the code lines correspond with which button.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FUOOiQ4S2QcMWmVoSmeQ8%2Fuploads%2F7AeoWPIv7Tp4XqxnNF68%2FGamepad-Labels.png?alt=media\&token=575cd53f-f430-4e82-8f2a-92bed94b7573)

|   PS4 Controllers  | Default (Logitech Gamepad)  |                                                                                                                                         Blocks                                                                                                                                        |              Java             | Data Type |
| :----------------: | :-------------------------: | :-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :---------------------------: | :-------: |
|        Cross       |              a              |         <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-MefyGMd_cjtIMfaGFye%2Fgampad_a.svg?alt=media&#x26;token=dd90bd44-5a3a-43bb-82d6-990ccb011666" alt="" data-size="original">          |          `gamepad1.a`         |  Boolean  |
|       Circle       |              b              |         <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-MefyIl-Ll13ocSPLPBb%2Fgampad_b.svg?alt=media&#x26;token=6fa37c13-a24c-4a04-8a98-31a398bd259e" alt="" data-size="original">          |          `gamepad1.b`         |  Boolean  |
|      Triangle      |              y              |         <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-MefyLTC5XT0ZCUcL4qa%2Fgampad_y.svg?alt=media&#x26;token=b1e666ba-1574-4609-8599-80e594a0f988" alt="" data-size="original">          |          `gamepad1.y`         |  Boolean  |
|       Square       |              x              |         <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-MefyNihIOjS-Ex05c3V%2Fgampad_x.svg?alt=media&#x26;token=b0a8b9de-9ac3-4b76-9657-0e8037d7a49c" alt="" data-size="original">          |          `gamepad1.x`         |  Boolean  |
|      Dpad Up       |           Dpad Up           |       <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-MefyQc43fGBd8YPQ1KH%2Fgampad_DpadUp.svg?alt=media&#x26;token=64b363fd-fb6d-4c76-9026-bb9b2e7f02cc" alt="" data-size="original">       |       `gamepad1.dpad_up`      |  Boolean  |
|      Dpad Down     |          Dpad Down          |      <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-MefyWzBxrbhm_nxZdwK%2Fgampad_DpadDown.svg?alt=media&#x26;token=deaf0174-06fd-4ffa-9f16-cbf05d2357a5" alt="" data-size="original">      |      `gamepad1.dpad_down`     |  Boolean  |
|      Dpad Left     |          Dpad Left          |      <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-MefyZrTvZ4--3FR-LtP%2Fgampad_DpadLeft.svg?alt=media&#x26;token=fc6053b7-1b9f-404a-917c-e09665a0e3f7" alt="" data-size="original">      |      `gamepad1.dpad_left`     |  Boolean  |
|     Dpad Right     |          Dpad Right         |     <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-MefycRzLKZCh8Nyihuf%2Fgampad_DpadRight.svg?alt=media&#x26;token=56fddd18-dae8-4923-896b-c8ec47142200" alt="" data-size="original">      |     `gamepad1.dpad_right`     |  Boolean  |
|     Left Bumper    |         Left Bumper         |     <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-MefvsReeMM-BoSDwSo9%2Fgampad_LefBumper.svg?alt=media&#x26;token=81174557-1b7e-4fc5-bd6e-096401928904" alt="" data-size="original">      |     `gamepad1.left_bumper`    |  Boolean  |
|    Right Bumper    |         Right Bumper        |    <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-MefyhTGT065OSFPQMsO%2Fgampad_RightBumper.svg?alt=media&#x26;token=5d912eb0-bf4c-4f91-bd7b-918ca3e2653c" alt="" data-size="original">     |    `gamepad1.right_bumper`    |  Boolean  |
|    Left Trigger    |         Left Trigger        |    <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-Meg1ixhp5UYWLTIwpfA%2Fgampad_LeftTrigger.svg?alt=media&#x26;token=a914fdbd-2fb1-405a-9864-2917600753ea" alt="" data-size="original">     |    `gamepad1.left_trigger`    |   Float   |
|    Right Trigger   |        Right Trigger        |    <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-Meg1l3U6mcavar6qAT0%2Fgampad_RightTrigger.svg?alt=media&#x26;token=e6acdacf-3d2a-45b7-bda0-dcd17a9d8bae" alt="" data-size="original">    |    `gamepad1.right_trigger`   |   Float   |
|         PS         |             n/a             |         <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-Meg23NRA8GyJEd6wi5t%2Fgampad_PS.svg?alt=media&#x26;token=37580382-0dd9-486e-9772-cb366291862f" alt="" data-size="original">         |          `gamepad.ps`         |  Boolean  |
|       Options      |            Start            |       <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-Meg25mUFbikYvJ0CP2o%2Fgampad_Start.svg?alt=media&#x26;token=3e8f2326-0fea-417d-9263-4cd919930cf2" alt="" data-size="original">        |        `gamepad1.start`       |  Boolean  |
|        Share       |             Back            |        <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-Meg289jpsjclF39NFy6%2Fgampad_Back.svg?alt=media&#x26;token=a3227121-7317-4907-ae6b-b706b40492d4" alt="" data-size="original">        |        `gamepad1.back`        |  Boolean  |
|  Left Stick Button |      Left Stick Button      |   <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-MefymdCUyynn8QoQhb5%2Fgampad_LeftStickButton.svg?alt=media&#x26;token=38dc7618-56a6-4568-9cd8-b5d6d6db4f8d" alt="" data-size="original">  |  `gamepad1.left_stick_button` |  Boolean  |
|  Left Stick X Axis |      Left Stick X Axis      |     <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-Meg2Bkc5e_G0-UfhDL7%2Fgampad_LeftStickX.svg?alt=media&#x26;token=75127398-a2a9-407a-82b6-39f1db9479b3" alt="" data-size="original">     |    `gamepad1.left_stick_x`    |   Float   |
|  Left Stick Y Axis |      Left Stick Y Axis      |     <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-Meg2EWU1Uo-OOYRTZdx%2Fgampad_LeftStickY.svg?alt=media&#x26;token=0223c867-f1b0-4d63-9a0c-b62f59bee112" alt="" data-size="original">     |    `gamepad1.left_stick_y`    |   Float   |
| Right Stick Button |      Right Stick Button     |  <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-Mefypw4O9JtYoO9CQQj%2Fgampad_RightStickButton.svg?alt=media&#x26;token=570245c6-3d49-4c76-ac45-9f9bbf8c578d" alt="" data-size="original">  | `gamepad1.right_stick_button` |  Boolean  |
| Right Stick X Axis |      Right Stick X Axis     |     <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-Meg2IxQy9Nnb5ojouxt%2Fgampad_RighStickX.svg?alt=media&#x26;token=fb93265e-8985-4caf-a8c3-e23f54ef256a" alt="" data-size="original">     |    `gamepad1.right_stick_x`   |   Float   |
| Right Stick Y Axis |      Right Stick Y Axis     |     <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MefjIYccgNxbJIm89ND%2F-Meg2Lw3rWVWYEzLC8sq%2Fgampad_RighStickY.svg?alt=media&#x26;token=f0ec5796-c8fc-4f73-8ae3-09ebda0a95f7" alt="" data-size="original">     |    `gamepad1.right_stick_y`   |   Float   |

### Data Types

#### Boolean&#x20;

Boolean data has two possible values: **True and False**. These two values can also be represented by **On and Off** or **1 and 0**. Buttons, bumpers, and triggers on the gamepad provide boolean data to your robot. For example, a button that is not pressed will return a value of False and a button that is pressed will return the value True.&#x20;

#### Float

Float data is a number that can include decimal places and positive or negative values. On the gamepad, the float data returned will be between 1 and -1 for the joystick's position on each axis. Some examples of possible values are 0.44, 0, -0.29, or -1.
