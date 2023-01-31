# Getting Started with Driver Hub

After receiving the Driver Hub it is advised to unbox the device, plug the Driver Hub in to charge over USB-C, and power on the Driver Hub. Below is the initial bring up process of the Driver Hub.&#x20;

### Required Materials

* Driver Hub ([REV-31-1596](https://www.revrobotics.com/rev-31-1596/))
* USB-A to USB-C Cable
* USB-A Wall Charger

{% embed url="https://youtu.be/RPcZOzUOZHg" %}

## Battery Installation

To install the battery place it with the REV Logo out and the -/+ located near the contacts for the device. Add on the rear door and screw in using the included M3 hardware.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MeW\_d-08gZU4NADc-BD%2F-MeWhoP-8ghsKkUj-wlG%2FDriver\_Hub\_Battery\_Placement\_In\_Hub.svg?alt=media\&token=57132bcd-bd3a-4b51-a249-af5246a13373)

{% hint style="warning" %}
Before continuing to set up the Driver Hub allow the battery to charge over USB-C or keep the Driver Hub plugged into a power source during set up.
{% endhint %}

## Setting up the Driver Hub

When the Driver Hub is first powered up, or a factory reset is performed, an initial set up process is needed. Start by selecting next on the main screen to continue.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Ma4GRqpAVceRyxZP8o5%2F-Ma4Kw2BqMS8pPcVdkH1%2FDriverHub\_Front\_Screen\_Blank\_on%20Hub.svg?alt=media\&token=3bace857-aac6-47d6-8474-44e08960c35f)

Select a local Wi-Fi network that has access to the internet, enter in the password for that network if required, and select next.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Ma4GRqpAVceRyxZP8o5%2F-Ma4PodMhgHwQZ3eK7pv%2Fnetworkconnection\_screenshot\_onHUB.svg?alt=media\&token=cdd6f4b2-5120-4c5a-8554-b77f80d15bd4)

Time zone and date of the device are set by the local Wi-Fi network. Confirm these settings are correct before proceeding by the Next button.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Ma4GRqpAVceRyxZP8o5%2F-Ma4RSciGsmofJRRwXyN%2Fdateconfirm\_screenshot\_onHUB.svg?alt=media\&token=eeb2e24d-d272-4867-83d2-89ab251e72ef)

Initial set up is complete! Select Finish to operate the Driver Hub.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Ma4GRqpAVceRyxZP8o5%2F-Ma4SIHuWsaCR0ZRYjkx%2Ffinish\_screenshot\_onHUB.svg?alt=media\&token=61ad91e9-12a5-4a1b-9c06-39b4b98fbcdd)

### Initial Update

After setting up the Driver Hub, the Software Manager application will open. Select the Update All button to start the download and installation of software updates for the Driver Hub.

{% hint style="info" %}
The updates can take several minutes to complete. Make sure the Driver Hub is charged or plug in the Driver Hub during the updating process.
{% endhint %}

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Ma4zAFPDoyUBGnyvWPk%2F-Ma5AKbvt2TL3KEjzCSb%2Fsoftwaremanagerupdateall\_screenshot\_onHUB.svg?alt=media\&token=c45898e0-7553-4458-bea4-c3489cc2c0ba)

{% hint style="success" %}
Now the Driver Hub is [ready to connect to a Control Hub](nachalo-raboty-s-control-hub/podklyuchenie-driver-station-k-control-hub.md)!
{% endhint %}

## Navigating the Driver Station Application

Once the Driver Hub is connected to a Control Hub, you will have access to the entire Driver Station Application interface. Like any application, understanding the major components that make up the Driver Station Application interface, will maximize your ability to utilize the application efficiently. Consider the following components:

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Meez4dA5ROtbExbO3rp%2F-Mef-NbV-gDoaPN6Irwa%2FDriveHub\_DS%20navigation1.svg?alt=media\&token=057e5efb-053b-434b-87cb-7c4bcd951e35)

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Meez4dA5ROtbExbO3rp%2F-Mef-PY2EjvmCLVD8ZmZ%2FDriveHub\_DS%20navigation2.svg?alt=media\&token=6e46ac42-c415-473f-803b-d08ee1c93a02)

| 1  | Initialize, start, and stop programs | Only available when a program has been selected.                                                                                                                                                                                                          |
| -- | ------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2  | Telemetry display                    | <p>Displays telemetry outputs. </p><p></p><p>Displays any system warnings and error codes</p>                                                                                                                                                             |
| 3  | Active configuration                 | <p>Displays which configuration file is currently active. </p><p></p><p>If this section says <strong>&#x3C;no config file></strong> you will need to activate or <a href="programming/hello-robot-configuration.md">create a configuration file</a>. </p> |
| 4  | Network information                  | Displays Control Hub SSID Name, signal strength, and ping time.                                                                                                                                                                                           |
| 5  | Gamepad connections.                 | See [Connecting Gamepads](getting-started-with-driver-hub.md#connecting-gamepads) for more information.                                                                                                                                                   |
| 6  | Autonomous drop down menu            | Drop down menu that displays all autonomous programs saved on the Control Hub.                                                                                                                                                                            |
| 7  | Teleop drop down menu                | Drop down menu that displays all teleop programs saved on the Control Hub.                                                                                                                                                                                |
| 8  | System power display                 | Displays the amount of battery voltage powering the robot, when connected to a Control Hub.                                                                                                                                                               |
| 9  | Settings drop down menu              | Access settings, configure the robot, restart the robot, check to see if your system meets competition inspection requirements and more.                                                                                                                  |
| 10 | Practice Timer                       | A built in timer that can be used to to practice for different portions of a match.                                                                                                                                                                       |

### Tips and Tricks&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Meez4dA5ROtbExbO3rp%2F-Mef-NbV-gDoaPN6Irwa%2FDriveHub\_DS%20navigation1.svg?alt=media\&token=057e5efb-053b-434b-87cb-7c4bcd951e35) ![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-Meez4dA5ROtbExbO3rp%2F-Mef-PY2EjvmCLVD8ZmZ%2FDriveHub\_DS%20navigation2.svg?alt=media\&token=6e46ac42-c415-473f-803b-d08ee1c93a02)

If you tap on area 4, it will switch to displaying the link speed and signal strength. It will go back to showing the signal strength and ping time if you tap it again.

The smaller number in area 8 is the lowest voltage that the Driver Station has observed from the Robot Controller. If you tap area 8, the lowest voltage will be reset to the current voltage.

## Connecting Gamepads

The Driver Station Application allows for the connection of two gamepads. When working with the Driver Hub these gamepads can be plugged into any of the three USB 2.0 ports. Once the gamepads are plugged in, you will need to initialize them. For the following example we will use PS4 controllers, such as the Etpark Wired Controller for PS4 ([REV-39-1865](https://www.revrobotics.com/rev-39-1865/)).

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MeWOpi0HEE7Kp2xk1IP%2F-MeWQwVq7Ime2JHIk06v%2FDriveHub\_dualGamepad.svg?alt=media\&token=616cb403-62e6-4192-b907-6497bfa35bef)

To initialize the gamepad that will act as User 1 (gamepad1, in code) press the **options** button and the **`X`**button on the gamepad at the same time. To initialize User 2 ( gamepad2, in code) press the **options** button and the **`O`** button at the same time.&#x20;

{% hint style="info" %}
For the Logitech F310 Gaming Controller and Xbox 360 Controller for Windows, press **start** and **A** at the same time to initialize User 1 and **start** and **B** at the same time to initialize User 2.&#x20;
{% endhint %}
