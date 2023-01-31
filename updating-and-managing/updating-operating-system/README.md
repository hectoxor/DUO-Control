# Updating Operating System

The Control Hub’s Operating System is field upgradable. New updates are released to incorporate fixes, improvements, and new features as they are developed. &#x20;

There are two ways you can update the Operating System. It is recommended to use the [REV Hardware Client](./#using-the-rev-hardware-client) as it will automatically notify the user if the Hub's Operating System is out of date, download the latest OS, and install the OS on the device. The second way utilizes the FIRST Robot Controller Console.  For using the FIRST Robot Control Console, you will need to download the latest Operating System.&#x20;

{% hint style="info" %}
Updating the Operating System can take some time depending on the size of the update. Expect the update to take approximately 5 minutes to fully complete and keep the Control Hub powered during this process.
{% endhint %}

{% hint style="warning" %}
The following procedure works with Control Hubs with the part number REV-31-1595. For support using the REV-31-1152 Control Hub v0 please reach out to REV support (support@revrobotics.com).
{% endhint %}

## Using the REV Hardware Client&#x20;

| Steps                                                                                                                                                                                                                                                                                                    |                                                                                                                                                                                                                                                                                                                                                           |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Power on the Control Hub, by plugging the 12V Slim Battery ([REV-31-1302](https://www.revrobotics.com/rev-31-1302/)) into the XT30 connector labeled “BATTERY” on the Control Hub ([REV-31-1595](https://www.revrobotics.com/rev-31-1595/)).                                                             | ![C:\Users\Rachel\AppData\Local\Microsoft\Windows\INetCache\Content.Word\g20714.png](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gHM0EmnJzRcHEz%2F48.png?generation=1590614867898772\&alt=media)                                                                  |
| <p>The Control Hub is ready to connect with a PC when the LED turns green. </p><p></p><p><strong>Note:</strong> With Robot Controller Application versions 5.5 and below the light will blink blue every ~5 seconds. Please<a href="../updating-robot-controller-application.md"> update </a>to 6.0.</p> | ![C:\Users\Rachel\AppData\Local\Microsoft\Windows\INetCache\Content.Word\rect22073.png](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MIye5\_C5oSoi2e84W9b%2F-MIym3ENg0UyQJ60AUhH%2FControl%20Hub%20with%205%20second%20blink%202.svg?alt=media\&token=3b8fa3ab-3810-42a1-b48d-78a3125e14ea) |
| Plug the Control Hub into the PC using a USB-A to USB-C Cable ([REV-11-1232](https://www.revrobotics.com/rev-11-1232/))                                                                                                                                                                                  |                                                                                                                                                                                                                                                                                                                                                           |

Startup the REV Hardware Client. Once the hub is fully connected it will show up on the front page of the UI under the **Hardware Tab**. Select the Control Hub.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGJeXWQDT5V\_EiH93Iv%2F-MGJhqYWj4hhfVFI930Y%2FUpdateOS%20-%20ClientStartupScreen.svg?alt=media\&token=93cca0e8-0ff1-41d1-abdb-9466b34ce6e4)

After selecting the Connected Hardware the Update tab will pop up.  Under **Control Hub Operating System** select Download.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGJeXWQDT5V\_EiH93Iv%2F-MGJhz2RYl00wfxKPaX7%2FUpdateOS%20-%20Click%20Download.svg?alt=media\&token=51a720ed-4c48-4395-a39b-996344174472)

Once the OS has downloaded, select Update.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGJeXWQDT5V\_EiH93Iv%2F-MGJlEbvs2GJpS16ZJjD%2FUpdateOS%20-%20Click%20Update.svg?alt=media\&token=714adaf5-2aec-4016-a189-88cd308eab64)

Keep the Control Hub powered while the upload finishes.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGJeXWQDT5V\_EiH93Iv%2F-MGJlMj8Sj7-1kTxzO26%2FUpdateOS%20-%20upload.svg?alt=media\&token=33685e63-041e-4805-8919-c9aa2493dd7e)

A successful upload will be denoted by the "Update Verification Succeeded" message highlighted in the image below. Once the upload is successful the install will begin.&#x20;

Keep the Control Hub powered while the update is installed. The Control Hub will reboot to complete the update.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGJeXWQDT5V\_EiH93Iv%2F-MGJlToDh6Ol9qOTBemV%2FUpdateOS%20-%20Install.svg?alt=media\&token=b0961ec8-6e4e-416d-b2b3-451cea447b8c)

When the OS update has completed a status message "Operating System update complete." The status for the Control Hub Operation System will also change to "Up-to-Date."

{% hint style="warning" %}
When using OS 1.1.2 the Control Hub operates by default on the 5Ghz band. You may need to update the [Wi-Fi settings](../../nachalo-raboty-s-control-hub/obnovlenie-nastroek-wi-fi.md) depending on what [Driver Station device](../../nachalo-raboty-s-control-hub/obnovlenie-nastroek-wi-fi.md#supported-android-devices-and-wi-fi-band-capabilities) you are using.
{% endhint %}

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGJeXWQDT5V\_EiH93Iv%2F-MGJlXfS-UACbHjrq00g%2FUpdateOS%20-%20Final%20Step.svg?alt=media\&token=84507dec-e92f-40e5-9f6d-4953794ee195)

## Using the Robot Controller Console&#x20;

#### [Download the Latest REV Control Hub Operating System - Version 1.1.3](https://github.com/REVrobotics/REV-Software-Binaries/releases/download/chos-1.1.3/ControlHubOS-1.1.3.zip)

{% hint style="warning" %}
When updating from OS 1.1.1 or earlier to OS 1.1.2 or later, the Control Hub will switch to the 5 GHz band, regardless of the previous Wi-Fi band setting. Some devices do not support 5 GHz Wi-Fi, and will not be able to connect to the Control Hub wirelessly while it is using the 5 GHz Wi-Fi band. To switch to the 2.4 GHz band without needing a computer, see the [Changing Wi-Fi Band section](../managing-wi-fi-on-the-control-hub.md#changing-wi-fi-band).
{% endhint %}

| Step                                                                                                                                                                                                                                         | Image                                                                                                                                                                                                                                                                                        |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Power on the Control Hub, by plugging the 12V Slim Battery ([REV-31-1302](https://www.revrobotics.com/rev-31-1302/)) into the XT30 connector labeled “BATTERY” on the Control Hub ([REV-31-1595](https://www.revrobotics.com/rev-31-1595/)). | ![C:\Users\Rachel\AppData\Local\Microsoft\Windows\INetCache\Content.Word\g20714.png](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gHM0EmnJzRcHEz%2F48.png?generation=1590614867898772\&alt=media)     |
| The Control Hub is ready to connect with a PC when the LED turns green. Note: the light blinks blue every \~5 seconds to indicate that the Control Hub is healthy.                                                                           | ![C:\Users\Rachel\AppData\Local\Microsoft\Windows\INetCache\Content.Word\rect22073.png](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gICw6\_gms8beSs%2F49.png?generation=1590614867893475\&alt=media) |
| Connect to the Control Hub’s Wi-Fi Network. If it is not renamed, the name will begin with either “FIRST-“ or “FTC-“.                                                                                                                        | ![A picture containing computer, white&#xA;&#xA;Description automatically generated](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gJvq-glVmBeshZ%2F50.png?generation=1590614867897710\&alt=media)     |
| Open a browser and navigate to the FIRST Robot Controller Console (type 192.168.43.1:8080 in the navigation bar). Select the Manage Tab.                                                                                                     | ![A picture containing drawing, knife&#xA;&#xA;Description automatically generated](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gK8YnBXOaVMPqJ%2F51.png?generation=1590614867878508\&alt=media)      |
| Scroll down to “Update Control Hub Operating System” and press the “Select Update File” button.                                                                                                                                              | ![A screenshot of a cell phone&#xA;&#xA;Description automatically generated](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gLcSHx-f\_DO4M7%2F52.png?generation=1590614867884487\&alt=media)            |
| Choose the latest version downloaded in Step 1 and press the “Update & Reboot” button.                                                                                                                                                       | ![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gMBdooY7y\_JfmB%2F53.png?generation=1590614868013857\&alt=media)                                                                                     |
| Keep the Control Hub powered while the upload finishes.                                                                                                                                                                                      | ![A screenshot of a cell phone&#xA;&#xA;Description automatically generated](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gNlaiDDZx-afiL%2F54.png?generation=1590614868013518\&alt=media)             |
| Keep the Control Hub powered while the update is installed. The Control Hub will reboot to complete the update.                                                                                                                              | ![A screenshot of a cell phone&#xA;&#xA;Description automatically generated](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gOtZlha2zV0M1h%2F55.png?generation=1590614868017494\&alt=media)             |
| When the OS update has completed, the Control Hub LED will switch from blue, back to its normal blink pattern.                                                                                                                               | ![C:\Users\Rachel\AppData\Local\Microsoft\Windows\INetCache\Content.Word\rect22073.png](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gP0Mwe-Yzn3xRm%2F56.png?generation=1590614867988195\&alt=media)  |
| Reconnect your computer to the Control Hub network and verify that the update was a success.                                                                                                                                                 | ![A screenshot of a cell phone&#xA;&#xA;Description automatically generated](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gQaAA6Yvu7Ry0a%2F57.png?generation=1590614867910449\&alt=media)             |
