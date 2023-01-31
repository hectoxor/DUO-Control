# Updating Firmware

## Updating the Expansion Hub Firmware

There are two boards within the Control Hub: an Expansion Hub **** and an Android controller. The Expansion Hub board built into the Control Hub, facilitates a line of communication between the built in Robot Controller and the motors, servos, and sensors. In order to improve the quality of the Hubs, REV Robotics will release firmware updates for the Expansion Hub. When a firmware release occurs, both Control Hub and Expansion Hub users will need to update their Expansion Hub firmware to the newest version. &#x20;

There are two ways to update the Expansion Hub Firmware. It is recommended to use the [REV Hardware Client](./#using-the-rev-hardware-client) as it will automatically notify the user if the Hub's firmware is out of date, download the latest firmware, and install on the device. The second set of steps utilizes the FIRST Robot Controller Console.&#x20;

To use the FIRST Robot Controller Console, the _Manage_ interface is needed to upload the firmware file to the Control Hub. You can then use a Driver Station that is connected to the Control Hub to initiate the firmware update. You can download the latest firmware below.

## Using the REV Hardware Client

### Control Hub

{% hint style="warning" %}
In order to use the REV Hardware Client for firmware updates, the Robot Controller Application must first be updated to version 5.5. After updating the application you may need to close out of the REV Hardware Client in order for the firmware update to be available.&#x20;
{% endhint %}

| Steps                                                                                                                                                                                                                                                                                                    |                                                                                                                                                                                                                                                                                                                                                           |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Power on the Control Hub, by plugging the 12V Slim Battery ([REV-31-1302](https://www.revrobotics.com/rev-31-1302/)) into the XT30 connector labeled “BATTERY” on the Control Hub.                                                                                                                       | ![C:\Users\Rachel\AppData\Local\Microsoft\Windows\INetCache\Content.Word\g20714.png](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gHM0EmnJzRcHEz%2F48.png?generation=1590614867898772\&alt=media)                                                                  |
| <p>The Control Hub is ready to connect with a PC when the LED turns green. </p><p></p><p><strong>Note:</strong> With Robot Controller Application versions 5.5 and below the light will blink blue every ~5 seconds. Please<a href="../updating-robot-controller-application.md"> update </a>to 6.0.</p> | ![C:\Users\Rachel\AppData\Local\Microsoft\Windows\INetCache\Content.Word\rect22073.png](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MIye5\_C5oSoi2e84W9b%2F-MIym3ENg0UyQJ60AUhH%2FControl%20Hub%20with%205%20second%20blink%202.svg?alt=media\&token=3b8fa3ab-3810-42a1-b48d-78a3125e14ea) |
| Plug the Control Hub into the PC using a USB-A to USB-C Cable ([REV-11-1232](https://www.revrobotics.com/rev-11-1232/))                                                                                                                                                                                  |                                                                                                                                                                                                                                                                                                                                                           |

Startup the REV Hardware Client. Once the Control Hub is fully connected it will show up on the front page of the UI under the **Hardware Tab**. Select the Control Hub.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGJyIN-ZpDXRNFbAZmV%2F-MGL2APuY8U4fo3t11-e%2Fimage.png?alt=media\&token=dc455790-44dc-4410-bd0f-12b4cb50b2d2)

After selecting the Connected Hardware the Update tab will pop up.  Under **Hub Firmware** select Download.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGOrLcs0cp8vrcfHGaJ%2F-MGP0lCsoWn6-eXFK0Mb%2Ffrimware%20update%20start.svg?alt=media\&token=229a6f53-60b8-41a7-ae25-2cb315e2ba5c)

Once the firmware has downloaded, select Update.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGOrLcs0cp8vrcfHGaJ%2F-MGP16QS\_9wDJdsaoslU%2Ffrimware%20update%20update.svg?alt=media\&token=a82b675c-a2f6-432a-a3ee-690767b038cb)

When the firmware update has completed a status message "Firmware successfully updated" The status for the Hub Firmware will also change to "Up-to-Date."

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGOrLcs0cp8vrcfHGaJ%2F-MGOzmNjvHbkulV0CcZ-%2Ffrimware%20update%20complete.svg?alt=media\&token=8eabb152-801d-4719-aee5-bf8cdec73905)

### Expansion Hub&#x20;

{% embed url="https://youtu.be/pCNbb050D7c" %}

Plug the Expansion Hub into a PC using a USB-A to Mini USB Cable.&#x20;

Startup the REV Hardware Client. Once the hub is fully connected it will show up on the front page of the UI under the **Hardware Tab**. Select the Expansion Hub.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGOrLcs0cp8vrcfHGaJ%2F-MGQCMIJLF3ht3rX3HfL%2FEH%20firmware%20-%20open%20page.svg?alt=media\&token=cffcbbe2-2fe3-416f-a0b6-7e331c27c90b)

After selecting the Connected Hardware the Update tab will pop up.  Under **Hub Firmware** select Download.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGOrLcs0cp8vrcfHGaJ%2F-MGQCJfKeWakIibCEHXK%2FEH%20firmware%20-%20download.svg?alt=media\&token=2e9de8d2-ebab-429d-8514-6178a77ac73f)

Once the firmware has downloaded, select Update.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGOrLcs0cp8vrcfHGaJ%2F-MGQD1sC5d\_TUcdhHEDr%2FEH%20firmware%20-%20update.svg?alt=media\&token=6ca8b2e4-917f-4cd4-a4d8-56f92adfa1e8)

When the firmware update has completed a status message "Firmware successfully updated" The status for the Hub Firmware will also change to "Up-to-Date."

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGOrLcs0cp8vrcfHGaJ%2F-MGQDgXCpQFBAcDaQt-p%2FEH%20firmware%20-%20complete.svg?alt=media\&token=bc419b1a-bdc3-49b3-b951-7b1745eadd2f)



## Using the Robot Controller Console

#### [Download the Latest REV Hub Firmware - Version 1.08.02](https://www.revrobotics.com/content/sw/REVHubFirmware\_1\_08\_02.bin)

| Updating the Expansion Hub Firmware                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>1. On the <em>Manage</em> page of the Control Hub user interface, press the <em>Select Firmware</em> button to to select the firmware file that you would like to upload.<br><img src="https://github.com/FIRST-Tech-Challenge/SkyStone/wiki/images/Managing-a-Control-Hub/selectFirmwareFile.jpg" alt="" data-size="original"></p><p></p><p>An <em>Upload</em> button should appear after you successfully selected a file.</p>                                                                        |
| <p>2. Press the <em>Upload</em> button to upload the firmware file from your computer to the Control Hub.<br><img src="https://github.com/FIRST-Tech-Challenge/SkyStone/wiki/images/Managing-a-Control-Hub/uploadFirmwareFile.jpg" alt=""></p><p></p><p>The words "Firmware upload complete" should appear once the file has been uploaded successfully.</p>                                                                                                                                               |
| <p>3. On the Driver Station, touch the three dots in the upper right hand corner to display a pop-up menu.</p><p></p><p><img src="https://github.com/FIRST-Tech-Challenge/SkyStone/wiki/images/Managing-a-Control-Hub/touchThreeDots.jpg" alt=""></p>                                                                                                                                                                                                                                                      |
| <p>4. Select <em>Settings</em> from the pop-up menu to display the Settings activity.</p><p></p><p><img src="https://github.com/FIRST-Tech-Challenge/SkyStone/wiki/images/Managing-a-Control-Hub/touchSettings.jpg" alt=""></p>                                                                                                                                                                                                                                                                            |
| <p>5. On the Driver Station, scroll down and select the <em>Advanced Settings</em> item (under the <em>ROBOT CONTROLLER SETTINGS</em> category).</p><p></p><p><img src="https://github.com/FIRST-Tech-Challenge/SkyStone/wiki/images/Managing-a-Control-Hub/selectAdvancedSettings.jpg" alt=""></p>                                                                                                                                                                                                        |
| <p>6. Select the <em>Expansion Hub Firmware Update</em> item on the <em>ADVANCED ROBOT CONTROLLER SETTINGS</em> activity.</p><p></p><p><img src="https://github.com/FIRST-Tech-Challenge/SkyStone/wiki/images/Managing-a-Control-Hub/selectExpansionHubFirmwareUpdate.jpg" alt=""></p>                                                                                                                                                                                                                     |
| <p>7. If a firmware file that is different from the version currently installed on the Expansion Hub was successfully uploaded, the Driver Station should display some information about the current firmware version and the new firmware version. Press the <em>Update Expansion Hub Firmware</em> button to start the update process.</p><p></p><p><img src="https://github.com/FIRST-Tech-Challenge/SkyStone/wiki/images/Managing-a-Control-Hub/pressUpdateExpansionHubFirmwareButton.jpg" alt=""></p> |
| <p>8. A progress bar will display while the firmware is being updated. Do not power off the Control Hub/Expansion Hub during this process. The Driver Station will display a message when the update process is complete.<br></p><p><img src="https://github.com/FIRST-Tech-Challenge/SkyStone/wiki/images/Managing-a-Control-Hub/dsUpdateComplete.jpg" alt=""></p>                                                                                                                                        |
