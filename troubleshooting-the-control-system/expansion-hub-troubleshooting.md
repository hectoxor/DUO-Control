# Expansion Hub Troubleshooting

The following sections, "[Common Indicators and their Solution Steps](broken-reference)," provides common indicators of issues seen in the Expansion Hub. Think about what the potential indicators your Hub is currently exhibiting and consider the following questions:&#x20;

* Did you perform a firmware update before the Hub began to have issues?
* What is the behavior of the Status LED on the Expansion Hub?
* Is the Driver Station showing an error message 'Cant find the Expansion Hub Portal"?
* Did the Robot Controller app open when you plugged in the RC phone and gave power to the Hub?
* Are you experiencing issues with communication between a primary and secondary Hub?

{% hint style="info" %}
_If a path in this guide does not resolve the issue please contact REV Robotics Support at support@revrobotics.com_
{% endhint %}

### Common Indicators and their Solution Steps&#x20;

* The firmware update failed and the Hub is unresponsive&#x20;
  * Try a [Firmware Update](https://docs.revrobotics.com/duo-control/managing-the-control-system/updating-firmware#expansion-hub)
* The LED on the Expansion Hub is not lighting up&#x20;
  * Try a [Firmware Update](https://docs.revrobotics.com/duo-control/managing-the-control-system/updating-firmware#expansion-hub)&#x20;
  * [The LED is still not lighting up ](expansion-hub-troubleshooting.md#usb-serial-converter-check)
* The Hub is not being recognized or communicating with the phones&#x20;
  * Try doing the [Hub Startup Procedure ](expansion-hub-troubleshooting.md#hub-startup-procedures)
* There are [issues seeing a secondary Expansion Hub](expansion-hub-troubleshooting.md#issues-seeing-a-secondary-expansion-hub)

{% hint style="info" %}
**Expansion Hubs purchased AFTER December 2021 no longer include an internal IMU**
{% endhint %}

### Issues Seeing a Secondary Expansion Hub&#x20;

{% embed url="https://youtu.be/f1ev2Ap9Ywo" %}

The steps below utilize information provided in the [Adding an Expansion Hub ](../adding-more-motors/adding-an-expansion-hub.md)article. Use this article to help you navigate as you run through the troubleshooting flowchart. &#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MX985Hm4J6FTl0\_gLCi%2F-MX9Hh9d7HgKrItUJ7tP%2FAdding%20an%20Expansion%20Hub%20.svg?alt=media\&token=2cbd961e-9aac-447d-b8a4-c754009ddcc9)

{% hint style="info" %}
To update a Robot Controller check out the article on [Updating the Robot Controller Application](../updating-and-managing/updating-robot-controller-application.md).
{% endhint %}

If you are attempting to connect two Expansion Hubs together please confirm that the first Expansion Hub is connected to the Robot Controller. From there change the Expansion Hub address. For information on how to change the Expansion Hub address check out the [FTC Wiki Using a Second Expansion Hub](https://github.com/FIRST-Tech-Challenge/FtcRobotController/wiki/Using-Two-Expansion-Hubs#checking-the-address-of-an-expansion-hub) article.&#x20;

### XT30 Pins are Compressed

Over time, the pins on the XT30 connector of your Expansion Hub can become compressed from frequent use and may lose contact with the opposing connector. To remedy this, we recommend using a small flat-head screwdriver to slightly separate the tines on the top of the pins. This will cause them to make better contact inside the opposing connector.

<figure><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FUOOiQ4S2QcMWmVoSmeQ8%2Fuploads%2F5j6IkWQUC5DlWC6XFf12%2FImage_20221108_113427_781.jpeg?alt=media&#x26;token=83f29278-949a-4df1-b90a-0a479c392822" alt=""><figcaption><p>Gently use a flat-head screwdriver to slightly separate the tines.</p></figcaption></figure>

<figure><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FUOOiQ4S2QcMWmVoSmeQ8%2Fuploads%2F58QWdUfzEZWA6xH5J5Ru%2FImage_20221108_113427_954.jpeg?alt=media&#x26;token=1ac9c8ec-d56f-4bc4-88df-cfe2631df193" alt=""><figcaption><p>An XT30 connector pin should look like the picture above, with a small "X" on the top.</p></figcaption></figure>

After separating the tines, the pins should make a better connection with female connectors.

{% hint style="warning" %}
The pins on the XT30 connector should have a visible "X" on the top, like the picture shown above.
{% endhint %}

### **Firmware Update**

Use the[ REV Hardware Client](https://docs.revrobotics.com/rev-hardware-client/) to [update the Expansion Hub](https://docs.revrobotics.com/rev-hardware-client/expansion-hub/updating-expansion-hub).

### USB Serial Converter Check&#x20;

1. Plug your Expansion Hub into a Windows PC
2. Open the Device Manager in Settings
3. Click the arrow next to Universal Serial Bus Controllers
4. Find USB Serial Converter under the menu
5. If this is not present there maybe a larger issue with your hub. Email **staf14367@gmail.com** with details of the steps you have taken so far and any order numbers for the Expansion Hub (if you have them)

{% hint style="warning" %}
If you are using a Mac you can use System Information in Lion or later (or System Profiler in Snow Leopard and earlier versions of Mac OS) in Spotlight (press ⌘ and Space ). The program is in /Applications/Utilities and is the tool to see the connected USB devices and other hardware details.
{% endhint %}

### Hub Startup Procedures&#x20;

1. Unplug the USB from your RC phone
2. Power off the main robot switch (turn off 12V power from the Expansion Hub(s))
3. Wait a few seconds
4. Turn on the Main Robot Switch (supply 12V power to the Expansion Hub(s))
5. On your RC phone, press the square button and the swipe to close the FTC RC app
6. Plug your RC phone into the USB-- the FTC app should automatically open
   1. If the app doesn't automatically open you do not have a good connection from the Expansion Hub to the Phone. Check your cables first, followed by the micro and mini USB connections.
   2. Consider using some form of strain relief (like the[ REV USB Retention Mount](http://www.revrobotics.com/rev-41-1214/) or one of the many 3d printable options available on places like Thingiverse) to keep the USB-mini port from being damaged.

{% hint style="info" %}
If the issues persists after applying the Retention Mount try running through the [Firmware Update](../updating-and-managing/updating-firmware/) procedure.
{% endhint %}

### Still Need Assistance?

Contact REV Support with details of the troubleshooting information you have collected such as the answers to the questions above and the outcome of your troubleshooting thus far. It will also help to send logs or other diagnostic data to REV Support.&#x20;

{% hint style="info" %}
Need help getting the Log Files to send to REV Support? See [Downloading Log File](../updating-and-managing/accessing-log-files.md) for more information.
{% endhint %}
