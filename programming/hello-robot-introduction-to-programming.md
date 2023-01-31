# Hello Robot - Introduction to Programming

## Hello Robot - Choosing Your Path

In almost every programming class, the first lesson taught is some variation of the **Hello World** code. Hello World, often a one to two line segment of code, displays the line Hello World when the code is built and run. Though this code may seem like a very simple introduction to programming, it introduces several crucial concepts in programming. Hello World is the first lesson many students get in the **logic** of programming, as well as, language specific **syntax**. But, most importantly, the simplicity of Hello World allows it to be a **testing point** for the system used to execute the code. &#x20;

Though it is possible to display Hello World or Hello Robot on an Android Device in the REV Control System, it doesn't serve quite the same purpose. In order to properly consider syntax, logic, and testing in the REV Control System; consideration has to be paid to a multitude of system elements like actuators and sensors. For that reason the Hello World lesson has been edited into Hello Robot.&#x20;

By the end of this guide users should understand how to configure their robot and test their robot mechanisms. The following outline walks through the flow and goals of this section. Choose the path that best fits your needs.&#x20;

{% hint style="info" %}
If you are new to programming or the REV Control System we recommend that you follow through the whole guide to learn how to properly utilize the system.&#x20;
{% endhint %}

| Section                          | Sub Section                                                                                                                            | Goals                                                                                                                                                                                                                          |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Introduction**                 |                                                                                                                                        |                                                                                                                                                                                                                                |
|                                  | [Programming Tools](hello-robot-introduction-to-programming.md#programming-tools)                                                      | There are three programming tools for the REV Control System. Learn about the benefits of each option and choose the best option to fit your needs. Section also includes instructions on how to access the option you choose. |
|                                  | [Op Modes](hello-robot-introduction-to-programming.md#op-modes)                                                                        | What are Op Modes? Learn about the different types of Op Modes in the REV Control System                                                                                                                                       |
| **Configuration**                |                                                                                                                                        |                                                                                                                                                                                                                                |
|                                  | [Importance of Configuration](hello-robot-configuration.md#the-importance-of-configuration)                                            | What is Configuration and why should you configure before you begin to program?                                                                                                                                                |
|                                  | [Configuring Common Hardware](hello-robot-configuration.md#configuring-common-hardware-devices)                                        | Learn how to configure commonly used hardware like motors, servos, and sensors.                                                                                                                                                |
|                                  | [Common Errors in Hardware Mapping](hello-robot-configuration.md#common-errors-in-hardware-mapping)                                    | Understand and solve the common errors that occur when configuring and mapping hardware.                                                                                                                                       |
| **Test Bed: Introduction**       |                                                                                                                                        |                                                                                                                                                                                                                                |
|                                  | [Test Bed](hello-robot-test-bed/#test-bed)                                                                                             | Why creating a test bed of actuators and sensors can help with programming. This test bed, or something equivalent, will be used in following sections.                                                                        |
|                                  | [Testing Basics ](hello-robot-test-bed/#testing-basics)                                                                                | Learn why is one of the most important aspects of Software Development and how it differs from troubleshooting.                                                                                                                |
| **Test Bed: Blocks**             |                                                                                                                                        |                                                                                                                                                                                                                                |
|                                  | [Creating an Op Mode](hello-robot-test-bed/test-bed-blocks.md#creating-an-op-mode)                                                     | Focuses on how to navigate the Blocks interface and create an op mode.                                                                                                                                                         |
| ****                             | [Programming Essentials ](hello-robot-test-bed/test-bed-blocks.md#programming-essentials)                                              | Breaks down the structure and key elelments needed for an op mode, as well as some of the essential components of Blocks and programming logic.                                                                                |
|                                  | [Programming Actuators ](hello-robot-test-bed/test-bed-blocks.md#programming-actuators)                                                | How to code servos and motors. This section walks through the basic logic of coding actuators, controlling actuators with a gamepad, and using telemetry.                                                                      |
|                                  | [Programming Sensors ](hello-robot-test-bed/test-bed-onbot-java.md#programming-sensors)                                                | How to code a digital device. The section focuses on the basic logic of coding a digital device, like a REV Touch Sensor.                                                                                                      |
| **Test Bed: OnBot Java**         |                                                                                                                                        |                                                                                                                                                                                                                                |
|                                  | [Creating an Op Mode](hello-robot-test-bed/test-bed-onbot-java.md#creating-an-op-mode)                                                 | Focuses on how to navigate the OnBot Java interface and create an op mode.                                                                                                                                                     |
|                                  | [Programming Essentials ](hello-robot-test-bed/test-bed-onbot-java.md#programming-essentials)                                          | Breaks down the structure and key elelments needed for an op mode, as well as some of the essential components of Java.                                                                                                        |
|                                  | [Programming Actuators ](hello-robot-test-bed/test-bed-onbot-java.md#programming-actuators)                                            | How to code servos and motors. This section walks through the basic logic of coding actuators, controlling actuators with a gamepad, and using telemetry.                                                                      |
|                                  | [Programming Sensors ](hello-robot-test-bed/test-bed-onbot-java.md#programming-actuators)                                              | How to code a digital device. The section focuses on the basic logic of coding a digital device, like a REV Touch Sensor.                                                                                                      |
| **Robot Control**                |                                                                                                                                        |                                                                                                                                                                                                                                |
|                                  | [Create a Basic Robot ](hello-robot-robot-control/#create-a-basic-robot)                                                               | Introduces a potential robot to work with as well as the configuration file used in the following sections.                                                                                                                    |
|                                  | [Drivetrain Basics](hello-robot-robot-control/#drivetrain-basics)                                                                      | Differences between differential and omnidirectional drivetrains and their affect on teleoperated control types.                                                                                                               |
| **Robot Navigation: Blocks**     |                                                                                                                                        |                                                                                                                                                                                                                                |
|                                  | [Basics of Programming Drivetrains](hello-robot-robot-control/robot-navigation-blocks/#basics-of-programming-drivetrains)              | What to consider when [programming drivetrain motors](broken-reference) and how to apply this to an[ arcade style teleoperated control](broken-reference).                                                                     |
|                                  | [Elapsed Time](hello-robot-robot-control/robot-navigation-blocks/elapsed-time-blocks.md)                                               | Learn how to use the concept of elapsed time to create time controlled autonomous programs.                                                                                                                                    |
|                                  | [Encoder Navigation](hello-robot-robot-control/robot-navigation-blocks/encoder-navigation-blocks.md)                                   | Learn how to use encoders to create more consistent autonomous pathing.                                                                                                                                                        |
| **Robot Navigation: OnBot Java** |                                                                                                                                        |                                                                                                                                                                                                                                |
|                                  | [Basics of Programming Drivetrains](hello-robot-robot-control/robot-navigation-onbot-java/#basics-of-programming-drivetrains)          | What to consider when [programming drivetrain motors](broken-reference) and how to apply this to an[ arcade style teleoperated control](broken-reference).                                                                     |
|                                  | [Elapsed Time](hello-robot-robot-control/robot-navigation-onbot-java/elapsed-time-onbot-java.md)                                       | Learn how to use the concept of elapsed time to create time controlled autonomous programs.                                                                                                                                    |
|                                  | [Encoder Navigation](hello-robot-robot-control/robot-navigation-onbot-java/encoder-navigation-onbot.md)                                | Learn how to use encoders to create more consistent autonomous pathing.                                                                                                                                                        |
| **Arm Control: Blocks**          |                                                                                                                                        |                                                                                                                                                                                                                                |
|                                  | [Basics of Programming an Arm](hello-robot-robot-control/arm-control-blocks.md#basics-of-programming-an-arm)                           | Introduction to coding an arm for teleoperated control and working with a limit switch                                                                                                                                         |
|                                  | [Programming an Arm to a Position](hello-robot-robot-control/arm-control-blocks.md#programming-an-arm-to-a-position)                   | Using motor encoders to move an arm to a specific position, such as from 45 degrees to 90 degrees.                                                                                                                             |
|                                  | [Using Limits to Control Range of Motion](hello-robot-robot-control/arm-control-blocks.md#using-limits-to-control-range-of-motion)     | Working with the basics of arm control, motor encoder, and limit switches to control the range of motion for an arm.                                                                                                           |
| **Arm Control: OnBot Java**      |                                                                                                                                        |                                                                                                                                                                                                                                |
|                                  | [Basics of Programming an Arm](hello-robot-robot-control/arm-control-onbot-java.md#basics-of-programming-an-arm)                       | Introduction to coding an arm for teleoperated control and working with a limit switch                                                                                                                                         |
|                                  | [Programming an Arm to a Position](hello-robot-robot-control/arm-control-onbot-java.md#programming-an-arm-to-a-position)               | Using motor encoders to move an arm to a specific position, such as from 45 degrees to 90 degrees.                                                                                                                             |
|                                  | [Using Limits to Control Range of Motion](hello-robot-robot-control/arm-control-onbot-java.md#using-limits-to-control-range-of-motion) | Working with the basics of arm control, motor encoder, and limit switches to control the range of motion for an arm.                                                                                                           |

## Programming Tools&#x20;

Choosing the appropriate programming tool or language is one of the most crucial decisions a user can make. In the REV Control System there are three programming tools to choose from: Blocks, OnBot Java, and Android Studio. Each tool comes with different benefits and difficulty levels.&#x20;

|  Basic | Intermediate |    Advanced    |
| :----: | :----------: | :------------: |
| Blocks |  Onbot Java  | Android Studio |

The programming tools for the Software Development Kit (SDK) were chosen as a means of giving users the ability to choose among alternatives, but also as a means of allowing users to naturally move from basic to advanced programming. A user can reasonably start with Blocks and build their way up to Android Studio. In fact, this is often our suggestion to rookie users. Android Studio is a very powerful tool but, as you are learning the basics of programming, has the potential to be a hindrance rather than a help.&#x20;

Review the following sections to learn about each programming tool and the benefits that come with it. Once you are done reviewing make an educated choice about what tool will work best for you!

### Blocks&#x20;

The Blocks Programming Tool is a visual, programming tool that lets programmers uses a web browser to create, edit and save their op modes. Blocks, like other scratch based programming tools, is a collection of preset code snippets that users can drag-and-drop into the appropriate code line.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MKBCtYfZMoyOlpcLg6e%2F-MKByDIetz\_lJtdChazX%2FScreenshot%20\(392\).svg?alt=media\&token=200715b6-5ed6-49e7-b382-7cbf7e731678)

Blocks was created to cater to users who have little to no experience programming. Unlike OnBot Java or Android Studio, Blocks works to insulate and protect users from the complexities of the SDK. The Blocks interface accomplishes this by hiding, or abstracting, some of the more complex overhead the system requires, like calls to specific libraries or classes. The code snippets make those connections and assumptions for the user.&#x20;

One of the other major benefits of Blocks are the built-in features that allow users to naturally transition from little to no programming knowledge to a basic understanding of Java. Blocks teaches users the logic of programming, while protecting them from syntax mistakes. As users gain more confidence and ability they can use the "Show Java" option. "Show Java" allows users to see the Java syntax that corresponds with each Block that is added to the code.&#x20;

| Summarization of Benefits                                                                           |
| --------------------------------------------------------------------------------------------------- |
| Hides complexities from the user allowing them to focus on learning the logic                       |
| Has an option to Show Java which allows users to see what the corresponding syntax would be in Java |
| Web-based interface - accessible on most devices                                                    |
| Saves directly to the robot                                                                         |
| Just as powerful as OnBot Java                                                                      |

#### Accessing Blocks

{% hint style="danger" %}
This section assumes that you have already gone through the steps of setting up your REV Control System. For more information on how to setup your control system check out the [Getting Started with the Control Hub](../nachalo-raboty-s-control-hub/) guide.&#x20;

This section also assumes that you have a JavaScript enabled web browser.&#x20;
{% endhint %}

1. Go to Wi-Fi Settings, on a Windows 10 Computer, by clicking on the Wi-Fi symbol.&#x20;
2. Once the list of available Wi-Fi networks in the vicinity is displayed select the network that matches the name of your Wi-Fi access point.&#x20;
3. Enter the password that you set when setting up the [Control System](../updating-and-managing/managing-wi-fi-on-the-control-hub.md).&#x20;
4. Once connected, open a JavaScript enabled browser (FIRST recommends Google Chrome).
5. Go to IP Address **http://192.168.43.1:8080**
6. At the top of the Robot Controller Console Page, there should be 3 menu options: Blocks, OnBot Java, and Manage. Choose Blocks.&#x20;

{% hint style="info" %}
Passwords are case sensitive. If you do not remember your password, use the [Hardware Client ](../updating-and-managing/managing-wi-fi-on-the-control-hub.md#rev-hardware-client)to check the Program and Manage section of the Robot Controller Console&#x20;
{% endhint %}

### OnBot Java

A text-based programming tool that lets programmers use a web browser to create, edit and save their Java op modes.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MKBCtYfZMoyOlpcLg6e%2F-MKBxNa0iDuCupGggowS%2FScreenshot%20\(393\).svg?alt=media\&token=2078d03d-7a5e-476e-b36f-3d7ff28fb7ae)

OnBot Java is great for programmers with basic to advanced Java skills who would like to write text-based op modes. OnBot Java shares some of insulative properties of Blocks, but gives users access to the more complicated elements of the SDK libraries.For instance, OnBot requires users to make calls to classes like the hardwareMap, which are hidden within the Blocks code snippets.&#x20;

OnBot Java shares a web-based interface with the Blocks Programming tool. The web-based model is easy to access on most devices to make code change and reduces the need to have one set device for code changes.

| Summarization of Benefits                                                |
| ------------------------------------------------------------------------ |
| Access to more complicated library classes for more advance programming  |
| Reduces coding issues by hiding complex classes from the user            |
| Allows users to learn Java in simplified interface                       |
| Web-based interface - accessible on most devices                         |
| Saves directly to the robot                                              |

#### Accessing OnBot Java

{% hint style="danger" %}
This section assumes you have already gone through the steps of setting up your REV Control System. For more information on how to setup your control system check out the Getting Started or Managing the Control System sections of the [Control System Guide](https://app.gitbook.com/o/YVRlgEE8wQREEYYeolkQ/s/9olCqQm11wJ3CrwszPvs/).&#x20;

This section also assumes that you have a JavaScript enabled web browser.&#x20;
{% endhint %}

1. Go to Wi-Fi Settings, on a Windows 10 Computer, by clicking on the Wi-Fi symbol.&#x20;
2. Once the list of available Wi-Fi networks in the vicinity is displayed select the network that matches the name of your Wi-Fi access point.&#x20;
3. Enter the password that you set when setting up the [Control System](../updating-and-managing/managing-wi-fi-on-the-control-hub.md).&#x20;
4. Once connected, open a JavaScript enabled browser (FIRST recommends Google Chrome).
5. Go to IP Address **http://192.168.43.1:8080**
6. At the top of the Robot Controller Console Page, there should be 3 menu options: Blocks, OnBot Java, and Manage. Choose OnBot Java&#x20;

{% hint style="info" %}
Passwords are case sensitive. If you do not remember your password, use the [Hardware Client ](../updating-and-managing/managing-wi-fi-on-the-control-hub.md#rev-hardware-client)to check the Program and Manage section of the Robot Controller Console&#x20;
{% endhint %}

### Android Studio

An advanced integrated development environment for creating Android apps. This tool is the same tool that professional Android app developers use. Android Studio is only recommended for advanced users who have extensive Java programming experience.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MA1a4XNkSOFI2pu0KXh%2F-MA1mKiPnGaeWa4lqwFP%2Fimage.png?alt=media\&token=eb33a4be-8b0b-42bc-8c0e-ce5184d9469a)

Android Studio allows programmer with an advanced understanding of Java a more powerful development environment to work in. It offers enhanced editing and debugging features not available with OnBot Java or Blocks. It also allows programmers the ability to work with 3rd Party libraries not included within the SDK. However, Android Studio is not a web-based software and will need a dedicated laptop to run on.&#x20;

| Summarization of Benefits                                                |
| ------------------------------------------------------------------------ |
| Access to more complicated library classes for more advance programming  |
| Enhanced editing and debugging features                                  |
| Enables access to 3rd Party Libraries                                    |

#### Accessing Android Studio

To learn about how to properly download and work with Android Studio please visit the [FTC Wiki. ](https://github.com/ftctechnh/ftc\_app/wiki/Android-Studio-Tutorial)

{% hint style="danger" %}
FIRST Global does not have support for Android Studio.&#x20;
{% endhint %}

## Op Modes

**Op modes** (or operational modes) are computer programs that are used to customize or specify the behavior of a robot. The Robot Controller, either the Control Hub **** ([REV-31-1595](https://www.revrobotics.com/rev-31-1595/)) or an Android device paired with an Expansion Hub ([REV-31-1153](https://www.revrobotics.com/rev-31-1153/)), stores and executes op modes.  The Driver Station allows users to select from any of the op modes stored on the Robot Controller and initialize, start, or stop the op modes.&#x20;

In the SDK there are two types of op modes: **autonomous** and **teleoperation**. Both types of op modes have initialization, start, and stop features on the Driver Station phone. Each feature corresponds with different types of code segments that will be discussed in detail in the programming tool specific Test Bed sections of this document.

The main difference between autonomous and teleoperation op modes is how they show up in the Driver Station application. Autonomous op modes show up in a drop down menu on the left side of the Driver Station application. The Driver Station assigns a 30 second timer to autonomous op modes. If the autonomous op mode is not manually stopped prior to the end of the 30 seconds the Driver Station will automatically stop the code. TeleOp op modes will appear in a drop down menu on the right side of the Driver Station application. These op modes will run until they are manually stopped.&#x20;

It is also worth noting that in the SDK op modes can be **linear op modes** or **iterative op modes**. This guide focuses on Linear op modes, which execute code lines in a sequential order. In order to repeatedly call actions within in a linear op mode, a loop function must be used. This topic will be discussed in further detail as you follow along this guide.
