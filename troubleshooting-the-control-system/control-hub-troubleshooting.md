# Control Hub Troubleshooting

The following questions consider common indicators of issues seen in the Control Hub. Think about the potential indicators your Hub is currently exhibiting and consider the following questions:&#x20;

| Is the Driver Station device unable to connect to to the Control Hub Wi-Fi?                              | [Yes](control-hub-troubleshooting.md#cant-connect-the-control-hub-to-a-computer)          |
| -------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| Is the Driver Station connected to the Wi-Fi but not showing a ping or any other signs of communication? | [Yes](control-hub-troubleshooting.md#driver-station-wont-connect)                         |
| Has the Status LED been solid blue for longer than 30 seconds (after start up)?                          | [Yes](control-hub-troubleshooting.md#status-led-is-solid-blue-for-longer-than-30-seconds) |

### Can't Connect the Control Hub to a Computer

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MX-6gWBX7dIZAlir0th%2F-MX2aVu1gqRHcEf68CFN%2FCantConnectviaWiFi%20\(2\).svg?alt=media\&token=47a50aa7-cb0a-4cca-9b4a-7388bf236cfc)

{% hint style="warning" %}
The Wi-Fi reset will down grade the Wi-Fi connection to 2.4GHz. If you have an android device with 5GHz you may want to switch the Wi-Fi Band in order to run on 5GHz. _Check out the_ [_Updating Wi-Fi Settings_ ](../nachalo-raboty-s-control-hub/obnovlenie-nastroek-wi-fi.md)_Section to learn more about making this switch._
{% endhint %}

External factors, such as local Wi-Fi environment, play a part in the ability to establish or maintain a connection between a Control Hub and a computer. Like all aspects of of troubleshooting its important to isolate an issue by asking questions and discovering the answers! As you work on troubleshooting consider the following questions:&#x20;

* **What is your local Wi-Fi environment like?**&#x20;
  * Local Wi-Fi environment effects the consistency of a connection to the Control Hub. Use a [Wi-Fi analyzer](https://play.google.com/store/apps/details?id=com.farproc.wifi.analyzer\&hl=en) to check the local environment for channels that are cluttered with Wi-Fi networks. [Change the Control Hubs Wi-Fi channel ](../updating-and-managing/managing-wi-fi-on-the-control-hub.md#rev-hardware-client)to a channel with the least amount of overlap with other networks.
* **Are you connected to another Wi-Fi network?**
  * The Control Hub produces a non internet Wi-Fi connection. Settings on the individual computer may cause the device to jump to a local, remembered network that produces an internet connection.
* **Are you in a school or a place of business?**
  * In addition to the amount of local networks in an environment its important to understand what those local networks are capable of. For instance, some school districts have security measures in place that block unauthorized Wi-Fi access points. Talk to your local Wi-Fi adminstrator to find out what you need to get the Control Hub as an approved network.

{% hint style="warning" %}
If the Control Hub SSID is not shown in the list of available Wi-Fi networks, try manually entering the Control Hub SSID to see if that allows you to connect.&#x20;
{% endhint %}

Contact REV Support with details of the troubleshooting information you have collected such as the answers to the questions above and the outcome of your troubleshooting thus far. It will also help to send logs or other diagnostic data to REV Support.&#x20;





{% hint style="info" %}
Need help getting the Log Files to send to REV Support? See [Downloading Log File](../updating-and-managing/accessing-log-files.md) for more information.
{% endhint %}

### Driver Station Won't Connect&#x20;

{% hint style="danger" %}
Information in this flowchart is for the initial bring up of connecting the Control Hub with a Driver Station. For issues with intermittent connection or periodic connection drops please check out the information below this flowchart.
{% endhint %}

<figure><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FUOOiQ4S2QcMWmVoSmeQ8%2Fuploads%2FKz71WusVtJfx9iH1dV4e%2FDSwontConnect.drawio.png?alt=media&#x26;token=25bf750e-0eed-47f0-a499-6d5da56a0683" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
The Wi-Fi reset will down grade the Wi-Fi connection to 2.4GHz. If you have an android device with 5GHz you may want to switch the Wi-Fi band in order to run on 5GHz. _Check out the_ [_Updating Wi-Fi Settings_ ](broken-reference)_Section to learn more about making this switch._
{% endhint %}

External factors, such as local Wi-Fi environment, play a part in the ability to establish or maintain a connection between a Control Hub and a Driver Station device. Like all aspects of of troubleshooting its important to isolate an issue by asking questions and discovering the answers! As you work on troubleshooting consider the following questions:&#x20;

* **Is your system operating on a 2.4 GHz band or 5GHz band?**
  * REV recommends, if you have a dual band Driver Station device, that you operate on the 5GHz Wi-Fi band. Check out the [Updating Wi-Fi Settings](../nachalo-raboty-s-control-hub/obnovlenie-nastroek-wi-fi.md) section to learn more about making this switch.
* **What is your local Wi-Fi environment like?**&#x20;
  * Local Wi-Fi environment effects the consistency of a connection to the Control Hub. Use a [Wi-Fi analyzer](https://play.google.com/store/apps/details?id=com.farproc.wifi.analyzer\&hl=en) to check the local environment for channels that are cluttered with Wi-Fi networks. [Change the Control Hubs Wi-Fi channel ](../updating-and-managing/managing-wi-fi-on-the-control-hub.md#rev-hardware-client)to a channel with the least amount of overlap with other networks.&#x20;
* **Are you in a school or a place of business?**
  * In addition to the amount of local networks in an environment its important to understand what those local networks are capable of. For instance, some school districts have security measures in place that block unauthorized Wi-Fi access points. Talk to your local Wi-Fi administrator to find out what you need to get the Control Hub as an approved network.
* **Does the the Driver Station connect to the Control Hub until a mechanism is run?**&#x20;
  * Certain mechanisms draw enough power from the Control Hub to put a strain on the battery. If you notice a drop in displayed voltage when you start a code, or when a particular mechanism is run, this may be indicative of a brown out condition. Other indicators include:&#x20;
    * The Driver Station throwing errors about power to the system
    * The Driver Station making a disconnect sound
    * The voltage on the Driver Station showing 9 volts or lower when running code&#x20;
    * Motors running at lower speeds then what they have been set to run
  * To remedy this issue check out our instructions on [proper battery care.](https://www.revrobotics.com/rev-31-1302/)&#x20;

{% hint style="warning" %}
If the Control Hub SSID is not shown in the list of available Wi-Fi networks, try manually entering the Control Hub SSID on the Driver Station to see if that allows you to connect.&#x20;
{% endhint %}

If you are still experiencing connection issues, once you have gone through the flowchart and worked on addressing the potential root of connection issues describe in the list above, start looking for patterns in the behavior. How often does this behavior appear? Are there certain things that happen around the same time the disconnects happen? The following list provides some ideas on what sort of patterns you might see:

* The Control Hub connects fine when a team member takes it home but doesn't seem to like to connect at school.
* The Control Hub connects fine until you start driving the robot around.

{% hint style="info" %}
Just remember correlation does not equal causation of an event but is useful data to further troubleshooting
{% endhint %}

Contact REV Support with details of the troubleshooting information you have collected such as the answers to the questions above and the outcome of your troubleshooting thus far. It will also help to send logs or other diagnostic data to REV Support.&#x20;

{% hint style="info" %}
Need help getting the Log Files to send to REV Support? See [Downloading Log File](../updating-and-managing/accessing-log-files.md) for more information.
{% endhint %}

### Status LED is Solid Blue for Longer than 30 Seconds&#x20;

{% hint style="info" %}
This section is for troubleshooting a Control Hub. If you have an Expansion Hub please refer to the [Expansion Hub Troubleshooting](expansion-hub-troubleshooting.md) guide for help solving Expansion Hub related issues.&#x20;
{% endhint %}

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MX2iOEKWFN2\_tWR9r9m%2F-MX8iS5r1n7k4BZx9hZb%2FSolidBlueLED%20\(1\).svg?alt=media\&token=07c203ff-fa2c-4fa1-8176-7dccc7b90192)

The status LED on the Control Hub is similar to a check engine light on a car. A solid blue status LED indicates the Robot Controller is not communicating to the I/O of the Control Hub, but not what the root cause is. Updating the Control Hub to the latest version of all the software is a first step to resolving this issue, listed below are two ways to update.

#### Using the REV Hardware Client

The [REV Hardware Client](../updating-and-managing/rev-hardware-client.md) is software designed to make managing REV devices easier for the user. This Client automatically detects connected device(s), downloads the latest software for those device(s), and allows for seamless updating of the device(s). Using the REV Hardware Client allows you to perform any required updates that may be needed to recover your Control Hub. The Hardware Client can also be used to [Send Diagnostic Data to REV](../updating-and-managing/accessing-log-files.md).&#x20;

{% hint style="info" %}
If you do not have a Windows 10 or higher PC, see [Downloading Log File](../updating-and-managing/accessing-log-files.md) for more options on getting your diagnostic data to REV, and [Updating Firmware](../updating-and-managing/updating-firmware/), [Updating Operating System](../updating-and-managing/updating-operating-system/), and [Updating Robot Controller Application](../updating-and-managing/updating-robot-controller-application.md) for steps to update the software.
{% endhint %}

#### Using Android Studio&#x20;

{% hint style="warning" %}
The Control Hub must run version 5.0 or higher of the Robot Controller Application. If using Android Studio, make sure you are using a 5.0 or higher project.
{% endhint %}

If you use Android Studio for coding you will need to update your Robot Controller application by creating a new Android Studio project with the most recent version of the Robot Controller APK. Information on this process can be found in [FTC Wiki Android Studio Tutorial](https://github.com/FIRST-Tech-Challenge/FtcRobotController/wiki/Downloading-the-Android-Studio-Project-Folder).

### XT30 Pins are Compressed

Over time, the pins on the XT30 connector of your Control Hub can become compressed from frequent use and may lose contact with the opposing connector. To remedy this, we recommend using a small flat-head screwdriver to slightly separate the tines on the top of the pins. This will cause them to make better contact inside the opposing connector.

<figure><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FUOOiQ4S2QcMWmVoSmeQ8%2Fuploads%2F5j6IkWQUC5DlWC6XFf12%2FImage_20221108_113427_781.jpeg?alt=media&#x26;token=83f29278-949a-4df1-b90a-0a479c392822" alt=""><figcaption><p>Gently use a flat-head screwdriver to slightly separate the tines.</p></figcaption></figure>

<figure><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FUOOiQ4S2QcMWmVoSmeQ8%2Fuploads%2F58QWdUfzEZWA6xH5J5Ru%2FImage_20221108_113427_954.jpeg?alt=media&#x26;token=1ac9c8ec-d56f-4bc4-88df-cfe2631df193" alt=""><figcaption><p>An XT30 connector pin should look like the picture above, with a small "X" on the top.</p></figcaption></figure>

After separating the tines, the pins should make a better connection with female connectors.

{% hint style="warning" %}
The pins on the XT30 connector should have a visible "X" on the top, like the picture shown above.
{% endhint %}

### Still Need Assistance?

Contact REV Support with details of the troubleshooting information you have collected such as the answers to the questions above and the outcome of your troubleshooting thus far. It will also help to send logs or other diagnostic data to REV Support.&#x20;

{% hint style="info" %}
Need help getting the Log Files to send to REV Support? See [Downloading Log File](../updating-and-managing/accessing-log-files.md) for more information.
{% endhint %}
