# Elapsed Time - Blocks

## Introduction to Elapsed Time

One way to create an autonomous code is to use a timer to define which actions should occur when. Within the SDK actions can be set to a timer by using **ElapsedTime.**&#x20;

Timers consist of two main categories: count up and count down. In most applications a timer is considered to be a device that counts down from a specified time interval. For instance, the timer on a phone or a microwave. However, some timers, like stopwatches, count upwards from zero. These types of timers measure the amount of time that has elapsed.&#x20;

ElapsedTime is a count up timer. Registering the amount of time elapsed from the start of a set event, like the starting of a stopwatch. In this case, it is the amount of time elapsed from when the timer is created or reset within the code.&#x20;

The ElapsedTime timer starts counting the amount of time elapsed from the point of its creation within a code. For instance, in this section ElapsedTime will be created in the section of code that occurs when the op mode is initialized. There is no option to stop the ElapsedTime timer. Instead, the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MWA9r9R96ap93E44ByF%2FElapsed%20Time%20-%20Reset%20(with%20rando%20variable).svg?alt=media&#x26;token=01ba5307-a59a-4e15-ae42-1dcfc29f7e11" alt="" data-size="original"> block can be used within your code to reset the timer at various intervals.&#x20;

Once the timer has been reset, the amount of time that has elapsed is queried by calling blocks like <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW6Q3E8gf10M-S_gPLC%2FElapsedTime%20-%20ET.seconds.svg?alt=media&#x26;token=5d0dd010-2572-4ee7-85f0-2aa23d46a505" alt="" data-size="original"> . The time given by the queried blocks can be used in loops to dictate how long a specific action should take place.&#x20;

| Sections                                                                                                  | Goals of Section                                                       |
| --------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| [Basics of programming with Elapsed Time](elapsed-time-blocks.md#basics-of-programming-with-elapsed-time) | Learning the logic needed to use elapsed time for autonomous control.  |

## Basics of Programming with Elapsed Time

Since this section focuses on creating an autonomous program using ElapsedTime it is important to understand where the elapsed time related blocks are located. At the top of the Categorize Blocks section there is a drop down menu for **Utilities**. The utilities drop down is a list of various utilities in alphabetical order. Towards the bottom of the the list select **Time** drop down menu. From there you can select **Elapsed Time**.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MRQ9yIkxBieLbHHoHvx%2F-MRQrLGm2TB-0LCOp-89%2FBlocks-%20elapsed%20time%20blocks%20location.svg?alt=media\&token=17b8900c-fa15-4468-8556-00f6fc9a9504)

### Programming with Elapsed Time

Start by creating a new op mode call `HelloWorld_ElapsedTime` using the `BasicOpMode` sample.&#x20;

{% hint style="warning" %}
When creating an op mode a decision needs to be made on whether or not to set it to autonomous mode. For applications under 30 seconds, typically required for competitive game play changing the op mode type to autonomous is recommended. For applications over 30 seconds, setting the code to the autonomous op mode type will limit your autonomous code to 30 seconds of run time. If you plan on exceeding the 30 seconds built into the SDK, keeping the code as a teleoperated op mode type is recommended.&#x20;

For information on how op modes work please visit the [Introduction to Programming ](../../hello-robot-introduction-to-programming.md#op-modes)section.&#x20;

For more information on how to change the op mode type check out the[ Test Bed - Blocks ](../../hello-robot-test-bed/test-bed-blocks.md#creating-an-op-mode)section.&#x20;
{% endhint %}

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MRQ9yIkxBieLbHHoHvx%2F-MRQuSLpF7Z3teQuOEGP%2Fcreat%20new%20op%20mode.svg?alt=media\&token=87bae6a8-35f1-4c64-8efa-0b0c66a791b4)

Create a variable named `runtime`.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MRQ9yIkxBieLbHHoHvx%2F-MRQE2gij3X-3R0XTgtw%2Fcreate%20new%20variable.svg?alt=media\&token=8b54cd20-ee50-44f3-afb3-0bae1da2aebb)

{% hint style="info" %}
For information on creating variables in blocks please revisit the [Test Bed - Blocks](../../hello-robot-test-bed/test-bed-blocks.md#programming-a-digital-device) section.&#x20;
{% endhint %}

Add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW6E-QPblWZt1LMlC9-%2FVariable%20-%20set%20runtime%20to.svg?alt=media&#x26;token=03cddd91-5388-4f24-9b13-5e9ce7f720c6" alt="" data-size="original"> block to the op mode below the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVRzzz2RWu0i_oNzqo3%2FComment%20-%20Put%20intialization%20blocks.svg?alt=media&#x26;token=5b100e29-9c67-4bb3-be74-0d35d452cb76" alt="" data-size="original"> __ comment block.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MRQ9yIkxBieLbHHoHvx%2F-MRRBkKUH0tZRbkMhpUJ%2Fset%20runtime%20to.svg?alt=media\&token=a3c1d586-c812-456d-a25c-cf684319864c)

In order to utilize elements of the `ElapsedTime`, `runtime` will act as the `ElapsedTime` variable.  Add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW6Id3RUFs-McuyZkjF%2FElapsedTime%20-%20new%20ElapsedTime.svg?alt=media&#x26;token=20afae34-23e2-42b6-b638-d2445d265e56" alt="" data-size="original"> block to the __ <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW6E-QPblWZt1LMlC9-%2FVariable%20-%20set%20runtime%20to.svg?alt=media&#x26;token=03cddd91-5388-4f24-9b13-5e9ce7f720c6" alt="" data-size="original"> block.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MRQ9yIkxBieLbHHoHvx%2F-MRRF-G8F9erACtpn8C1%2Fruntime%20is%20qualt%20to%20new%20elapsed%20time.svg?alt=media\&token=d39cd920-775b-404b-a394-896445203302)

Before moving on to the rest of the `ElapsedTime` structure lets go ahead and add the motor related blocks. Add <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MVrZYOdMO43YdZ0zxXy%2F-MVwRA9auYOOqnGmzAX7%2FDual%20Motor%20-%20set%20to%20positive.svg?alt=media&#x26;token=ed171c16-63c4-4531-89f3-ed93ce36dbae" alt="" data-size="original"> to the op mode to the while loop.

{% hint style="info" %}
When there are multiple of the same type of variable (such as multiple Dc Motor variables) the variable specific blocks will choose a default variable based on alphabetical order. For this example Op Mode Dc Motor blocks will default to the arm variable. Click the arrow next to the motor name to change the arm motor variable to the rightmotor variable. Use the variable drop down menu on the block to change from arm to rightmotor.![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MVIIB5oT9i9P2l29VHj%2F-MVNdPNK1aoHjru6tzHV%2FDual%20Motor%20-%20Variable%20Drop%20Down%20Menu.svg?alt=media\&token=3cb22ad9-52e4-42e1-8e29-95650ac60e79)
{% endhint %}

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MS3fVNmGQTWHn4XFsy9%2F-MS9-DU2zj7cNTmBpooo%2Fadding%20dual%20motor%20block.svg?alt=media\&token=16e763ee-050a-45d5-9634-47170658a9c1)

&#x20;If you recall from [Programming Drivetrain Motors](../robot-navigation-onbot-java/#programming-drivetrain-motors) article; the motors on the drivetrain mirror each other. The mirrored nature of the motor mounting causes the motors to rotate in opposing directions. In order to remedy this discrepancy the direction of the right motor needs to be reversed. Add the __ <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW6L1g4Y8GSBICwwFHF%2FMotor%20-%20rightmotorDirection.svg?alt=media&#x26;token=67d93d39-a4fd-441f-ae5d-6d323d657c6c" alt="" data-size="original"> block to the op mode under the the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MWA6F39D-6nHYXTbLoY%2FElapsedTime%20-%20set%20runtime%20to%20new%20ElapsedTime.svg?alt=media&#x26;token=e2db2476-668a-4353-886b-93fb97093da4" alt="" data-size="original"> block set.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MS3fVNmGQTWHn4XFsy9%2F-MS92DwHBGHFjVRvcTP7%2FBlocks%20-%20Add%20motor%20direction%20block.svg?alt=media\&token=ac773e65-243f-4795-8135-77710332daf4)

The goal is to have the motor move forward for 3 seconds. To accomplish this the While loops needs to be edited so that it triggers when the op mode is active and the ElapsedTime timer is less than or equal to 3 seconds. Lets start by creating the less than or equal to condition. Grab the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW6NHckRVPOzOmTIXSr%2FLogic%20-%20sign%20operators.svg?alt=media&#x26;token=818b475f-52b5-4312-94fe-ead593ac4a5e" alt="" data-size="original"> __ from the **Logic** menu.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MS9XpsWD2nUvkMIsd5j%2F-MS9j0TzPCtzilrte9jz%2FBlocks%20-%20%3D%20block.svg?alt=media\&token=74308fcf-0c4d-497c-8c20-2cf9f77498ef)

Select the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW6PY8JlulBh-f7_unJ%2FElapsedTime%20-%20ET.seconds.svg?alt=media&#x26;token=57c868f4-18f1-42e2-a9aa-5f9ffd8f05db" alt="" data-size="original"> block from the **Elapsed Time** menu. Drop the block into the left side of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW6NHckRVPOzOmTIXSr%2FLogic%20-%20sign%20operators.svg?alt=media&#x26;token=818b475f-52b5-4312-94fe-ead593ac4a5e" alt="" data-size="original"> block. Use the drop down menu to change the generic <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW6QB-agKBBHOb7HoT5%2FElapsedTime%20-%20ET%20variable.svg?alt=media&#x26;token=8042b434-408b-4f3e-8a8f-482a617c8773" alt="" data-size="original"> to the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWQebosYtMKEurna84n%2F-MWQgYaPEaq9DOao9riu%2FVariable%20-%20runtime.svg?alt=media&#x26;token=d0ade039-e4c4-4a6f-b9b5-1df34a316a45" alt="" data-size="original"> variable.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MS9XpsWD2nUvkMIsd5j%2F-MSEOrhLJ5-yF4Xzdq3i%2Felapsed%20time%20.Seconds%20inside%20equal%20sign.PNG?alt=media\&token=cfecb0f5-82e6-49a2-984b-d26099fa0df5)

Grab the __ <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW9tTS01Grlc87QDdhk%2FMath%20-%200.svg?alt=media&#x26;token=d80bfdbc-7d70-4109-8d23-f1037a2b4d16" alt="" data-size="original"> block from the **Math** menu.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MS9XpsWD2nUvkMIsd5j%2F-MSA984vacu\_JlN4dtZp%2FBlocks%20-%200.svg?alt=media\&token=01152ffa-5304-45e1-8ee6-dbadb6efface)

Add the number block to the right side of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW6NHckRVPOzOmTIXSr%2FLogic%20-%20sign%20operators.svg?alt=media&#x26;token=818b475f-52b5-4312-94fe-ead593ac4a5e" alt="" data-size="original"> __ block. Change the number block to 3.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MS9XpsWD2nUvkMIsd5j%2F-MSE064eO7zln0pxWMKH%2Fruntime%20equal%20to%203%20seconds.svg?alt=media\&token=b1f1d134-eca1-4739-9115-bd2f1bbd407f)

Right now the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MWA26bM2CihY0G3zhg3%2FElapsedTime%20-%20ET.seconds%20Runtime.svg?alt=media&#x26;token=e6db5727-4dba-4653-a465-53b86f52cc7d" alt="" data-size="original"> is equal to three. Use the arrow next to the equal sign to choose the less than or equal to sign from the drop down menu.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MS9XpsWD2nUvkMIsd5j%2F-MSDzQ7kK6Qdxa-ru6\_q%2Felapsed%20time%20less%20than%203.svg?alt=media\&token=e57dddee-41eb-4802-8d18-082ad51b1fe1)

Set this block set to the side for now. Grab an <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW9yJdVdzRolyWei1gK%2FLogic%20-%20and.svg?alt=media&#x26;token=129d69e5-1d08-4d91-8eb6-77ee65a3458b" alt="" data-size="original"> block from the **Logic** menu&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MOHTneSAfprqWldgpoU%2F-MOHrUwITP2r1YwxdbcL%2FBlocks%20-%20and%20block.svg?alt=media\&token=9dc0db3e-d2e9-4779-8894-b9565a92bef9)

Add the call <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW9zQx4RBqrvpcF0pji%2FClasses%20-%20Call%20Op%20mode%20active.svg?alt=media&#x26;token=427a0621-4a75-4476-aaa5-17e7c7388d99" alt="" data-size="line"> block to the left side of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW9yJdVdzRolyWei1gK%2FLogic%20-%20and.svg?alt=media&#x26;token=129d69e5-1d08-4d91-8eb6-77ee65a3458b" alt="" data-size="original">block. Add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MWA0ZnQRJp7_PnmCnog%2FCombo%20Block%20-%20ET%20lest%20than%203.svg?alt=media&#x26;token=53da31d7-077e-4739-9665-e9a1d1345839" alt="" data-size="original"> block set to the right side of the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW9yJdVdzRolyWei1gK%2FLogic%20-%20and.svg?alt=media&#x26;token=129d69e5-1d08-4d91-8eb6-77ee65a3458b" alt="" data-size="original"> block.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MS9XpsWD2nUvkMIsd5j%2F-MSF1BTFOwrvBCa5bCaU%2Ffull%20elapsed%20time%20and%20statement.PNG?alt=media\&token=3bb1ea3c-c9d7-4649-9382-f168dcb0f86d)

This block set will replace the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW9zQx4RBqrvpcF0pji%2FClasses%20-%20Call%20Op%20mode%20active.svg?alt=media&#x26;token=427a0621-4a75-4476-aaa5-17e7c7388d99" alt="" data-size="line"> block that is currently attached to the while loop. With this block set in place the while loop will now activate when both conditions of the _and_ block are true.&#x20;

{% hint style="info" %}
It is important to know that, within a linear op mode, a while loop must always have the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW9zQx4RBqrvpcF0pji%2FClasses%20-%20Call%20Op%20mode%20active.svg?alt=media&#x26;token=427a0621-4a75-4476-aaa5-17e7c7388d99" alt="" data-size="line"> Boolean as a condition. This condition ensures that the while loop will terminate when the stop button is pressed.&#x20;
{% endhint %}

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MS9XpsWD2nUvkMIsd5j%2F-MSF0GnZuCekFMDBjaei%2Ffull%20while%20loop.svg?alt=media\&token=61a41b1e-63d8-4eac-bb78-c1b3d4f2b60b)

{% hint style="success" %}
Use tape to mark the distance from where the robot starts to where you would like it to end up. Try running the code using the following conditions:&#x20;

* Press the init button and immediately press play
* Press the init button, wait 30 seconds and then press play&#x20;

What difference in behavior did you notice?
{% endhint %}

Recall that the`ElapsedTime` timer starts when the timer is created, which occurs where the<img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MWA6F39D-6nHYXTbLoY%2FElapsedTime%20-%20set%20runtime%20to%20new%20ElapsedTime.svg?alt=media&#x26;token=e2db2476-668a-4353-886b-93fb97093da4" alt="" data-size="original">block is placed. Since the timer is created prior to <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MWA60vPJ8ku9W4vMscg%2FClasses%20-%20waitForStart.svg?alt=media&#x26;token=7c8e15ac-67c8-4801-86fa-d9e595d8513b" alt="" data-size="original">, the timer will start when the program is initialized.&#x20;

If you tested the program you may have noticed that the robot didn't move the during the second run. Depending on how long you wait to start after initialization the timer may be close to or past 3 seconds by the time the program is played. To keep this from happening the timer should be reset once the op mode is active. Grab the call <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MWA9r9R96ap93E44ByF%2FElapsed%20Time%20-%20Reset%20(with%20rando%20variable).svg?alt=media&#x26;token=01ba5307-a59a-4e15-ae42-1dcfc29f7e11" alt="" data-size="original"> block. Use the drop down menu on the variable block to change the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MW6QB-agKBBHOb7HoT5%2FElapsedTime%20-%20ET%20variable.svg?alt=media&#x26;token=8042b434-408b-4f3e-8a8f-482a617c8773" alt="" data-size="original"> to <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MWQebosYtMKEurna84n%2F-MWQgYaPEaq9DOao9riu%2FVariable%20-%20runtime.svg?alt=media&#x26;token=d0ade039-e4c4-4a6f-b9b5-1df34a316a45" alt="" data-size="original"> .&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MS9XpsWD2nUvkMIsd5j%2F-MSEjra212WRenTZaPaH%2Felapsedtime.reset.svg?alt=media\&token=2a7aeced-e1c0-48c0-abc3-be8bb0732e95)

Add the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MWAAooN8dw_8N49YaIo%2FElapsed%20Time%20-%20Reset.svg?alt=media&#x26;token=bfd41d91-da89-479c-b06b-1fd1b47df651" alt="" data-size="original"> to the op mode beneath the <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MWACAqNiP66tvS4fGxc%2FComment%20-%20Put%20run%20blocks%20here.svg?alt=media&#x26;token=a002379b-48fb-4d1f-a08c-e2568d142683" alt="" data-size="original"> comment and above the while loop.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MS9XpsWD2nUvkMIsd5j%2F-MSF0DgmjC8sI\_bFPFqD%2Fadding%20reset.svg?alt=media\&token=ae734b14-0392-4c25-8260-2ba22cdac9f0)

As mentioned in previous sections, it can be beneficial to have a telemetry output when testing code. In the following example telemetry is used to output the amount of time that has passed with the timer.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MS9XpsWD2nUvkMIsd5j%2F-MSFBpaqoFrSxpIhhsg4%2Fadding%20telemtry%20to%20elapsed%20time.svg?alt=media\&token=f28016b9-522d-4bdb-9920-48c83c007776)

The above code will allow your motor to drive straight for 3 seconds. Additional movements can be added by duplicating the while loop. Right click the while loop block and select duplicate

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MS9XpsWD2nUvkMIsd5j%2F-MSFIFI3bUj5YSlKF1gD%2Fduplicate%20while%20look.svg?alt=media\&token=10ba4df5-2f07-4360-bf07-80f79361c3cb)

Once you have duplicated the while loop you can change some of the basic information like motor power or the time interval of the loop. You will also need to add a <img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MW6-jSLF6Z7O0wWozgO%2F-MWAAooN8dw_8N49YaIo%2FElapsed%20Time%20-%20Reset.svg?alt=media&#x26;token=bfd41d91-da89-479c-b06b-1fd1b47df651" alt="" data-size="original"> __ block between the two loops.

### Full Code Example

<figure><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MS9XpsWD2nUvkMIsd5j%2F-MSFK6pJdjwDoKlOheFr%2Fphase%202.svg?alt=media&#x26;token=6417dbfb-a6a2-4407-9c09-df936de8888c" alt=""><figcaption></figcaption></figure>
