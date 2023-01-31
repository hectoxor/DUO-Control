# Managing Wi-Fi on the Control Hub

The Control Hub creates a Wi-Fi access point to connect a Driver Station device or laptop to the Control Hub for programming and operation. Settings for the Control Hub access point are managed through the Robot Controller Console or the User Button on the Control Hub.

Before making changes to the Control Hub's Wi-Fi network checking what Wi-Fi bands are supported by the devices being used is important to ensure they will work as expected. Below are the Android Devices that are officially supported:&#x20;

#### Supported Android Devices and Wi-Fi Band Capabilities

| Android Device                                                           | Wi-Fi Band                  |
| ------------------------------------------------------------------------ | --------------------------- |
| REV Driver Hub ([REV-31-1596](https://www.revrobotics.com/rev-31-1596/)) | 2.4 GHz & 5 GHz (Dual Band) |
| Moto G (2nd generation)                                                  | 2.4 GHz (Single Band)       |
| Moto G (3rd generation)                                                  | 2.4 GHz (Single Band)       |
| Moto G (4th generation)                                                  | 2.4 GHz (Single Band)       |
| Moto G5                                                                  | 2.4 GHz & 5 GHz (Dual Band) |
| Moto G5 Plus                                                             | 2.4 GHz & 5 GHz (Dual Band) |
| Moto E4                                                                  | 2.4 GHz & 5 GHz (Dual Band) |
| Moto E5                                                                  | 2.4 GHz & 5 GHz (Dual Band) |
| Moto E5 Play                                                             | 2.4 GHz & 5 GHz (Dual Band) |

The following page is split into two sections. The first will cover how to access the Wi-Fi Settings through the Robot Controller Console. It is recommended to use the [REV Hardware Client](managing-wi-fi-on-the-control-hub.md#rev-hardware-client) as it will allow the user to access the Wi-Fi settings over a wired connection. The second will run through the steps for using the Control Hub's User Button to preform a Wi-Fi reset or Wi-Fi band change.&#x20;

{% hint style="info" %}
If you run into any problems trying to use the Hardware Client or when resetting the Wi-Fi, please contact **staf14367@gmail.com**
{% endhint %}

## Using the Robot Controller Console

The Robot Controller Console gives access to the Wi-Fi settings of the Control Hub. Below are the steps to access the Robot Controller Console through the [REV Hardware Client](managing-wi-fi-on-the-control-hub.md#rev-hardware-client) and the [Driver Station ](managing-wi-fi-on-the-control-hub.md#driver-station-application)application for updating Wi-Fi settings.

### REV Hardware Client&#x20;

The REV Hardware Client allows teams access to the Hub's Wi-Fi Settings information through a wired connection. The information is visible through the main page of the Robot Control Console and updated through the Program and Manage tab.

[Download the latest version of the REV Hardware Client](https://github.com/REVrobotics/REV-Software-Binaries/releases/download/rhc-1.4.2/REV-Hardware-Client-Setup-1.4.2.exe) and install on a Windows PC. Skip this step if completed already.

| Steps                                                                                                                                                                              |                                                                                                                                                                                                                                                                                              |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Power on the Control Hub, by plugging the 12V Slim Battery ([REV-31-1302](https://www.revrobotics.com/rev-31-1302/)) into the XT30 connector labeled “BATTERY” on the Control Hub. | ![C:\Users\Rachel\AppData\Local\Microsoft\Windows\INetCache\Content.Word\g20714.png](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gHM0EmnJzRcHEz%2F48.png?generation=1590614867898772\&alt=media)     |
| The Control Hub is ready to connect with a PC when the LED turns green. Note: the light blinks blue every \~5 seconds to indicate that the Control Hub is healthy.                 | ![C:\Users\Rachel\AppData\Local\Microsoft\Windows\INetCache\Content.Word\rect22073.png](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gICw6\_gms8beSs%2F49.png?generation=1590614867893475\&alt=media) |
| Plug the Control Hub into the PC using a USB-A to USB-C Cable ([REV-11-1232](https://www.revrobotics.com/rev-11-1232/))                                                            |                                                                                                                                                                                                                                                                                              |

Startup the REV Hardware Client. Once the hub is fully connected it will show up on the front page of the UI under the **Hardware Tab**. Select the Control Hub.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGiTkPM64QDvClOs1pw%2F-MGiVDNfFRESoYAwBz8s%2FResetAP%20-%20Start%20screen.svg?alt=media\&token=63f90329-95e7-4fc7-a0e9-652b5ff84168)

After selecting the Connected Hardware the Update tab will pop up.  Select the Program and Manage tab. This will take you to the Robot Controller Console build into the REV Hardware Client.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGiTkPM64QDvClOs1pw%2F-MGiVq2dC15lP3XjXlZg%2FResetAP%20-%20%20home%20screen.svg?alt=media\&token=0e3569e0-edd5-4285-b580-1aa7e25bc850)

Once in the Robot Controller Console, there are two options.&#x20;

If just the Wi-Fi Access Point name and password need to be found, they can be seen on the main page of the Robot Controller Console.&#x20;

If any of the Wi-Fi Access Point information needs to be changed, select the menu button in the upper right-hand corner of the page, indicated in the image below.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGiTkPM64QDvClOs1pw%2F-MGiWtKw2qnPRcb0-SUj%2FResetAP%20-%20%20program%20and%20manage%201.svg?alt=media\&token=9f73a40b-196a-4db7-bb3d-56f98387ba09)

When the menu opens, select Manage.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGiTkPM64QDvClOs1pw%2F-MGiXVPe5NHwUoYHWID-%2FResetAP%20-%20%20program%20and%20manage%202.svg?alt=media\&token=8332ee8e-e0be-4278-a6cb-ac4fc86216ef)

The Manage page is where the Wi-Fi Access Point information for the Hub can be viewed and changed. In the image below, the Hub's Wi-Fi name, password, band, and channel can be changed. Editing these settings can help when the Hub is not showing up as a potential connection point from a computer or Driver Station device.&#x20;

Once changes have been made select **Apply Wi-Fi Settings**.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGiTkPM64QDvClOs1pw%2F-MGiYK1O8HCxJlCjDn6L%2FResetAP%20-%20%20program%20and%20manage%203.svg?alt=media\&token=b3265b6c-22a1-43e4-af42-30ac1854f8ab)

{% hint style="warning" %}
Once updates are made to the network reconnection  to the new Wi-Fi network is needed. When accessing the REV Hardware Client via a USB connection the Control Hub will stay connected to the REV Hardware Client. Rescanning for devices is necessary for changes to show in the Hardware Client.&#x20;
{% endhint %}

### Driver Station Application&#x20;

The Manage page of the Robot Controller Console can also be accessed via the Driver Station Application. This is helpful in event environments, where Field Technical Staff may request that you change Wi-Fi bands or channels to mitigate disconnections.&#x20;

Select the three horizontal dots in the upright corned of the Driver Station Application&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_biLePwYuJ3rC-fkeb%2F-M\_genai4ratvTaqPPuW%2FAccessing%20RCC%20-%20selecting%20drop%20down%20menu.svg?alt=media\&token=0e2d22bf-b1bd-44d4-98be-9d03f75b211b)

In the drop down menu select **Program & Manage**.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_biLePwYuJ3rC-fkeb%2F-M\_gfMg9ITaC6n5bq6aV%2FAccessing%20RCC%20-%20program%20and%20manage.svg?alt=media\&token=ad5db48a-2e48-4063-b4cb-991a11b74036)

Once in the Robot Controller Console, there are two options.&#x20;

If just the Wi-Fi Access Point name and password need to be found, they can be seen on the main page of the Robot Controller Console.&#x20;

If any of the Wi-Fi Access Point information needs to be changed, select the menu button in the upper right-hand corner of the page, indicated in the image below.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_biLePwYuJ3rC-fkeb%2F-M\_gfs3aelJh-9QKEp5\_%2FAccessing%20RCC%20-%20select%20drop%20down%20menu%20in%20RCC.svg?alt=media\&token=0ec86a64-ca71-4d00-8379-f988d044de7f)

When the menu opens, select Manage.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_biLePwYuJ3rC-fkeb%2F-M\_ggQJ9xEkQShZvamBU%2FAccessing%20RCC%20-%20selecting%20manage.svg?alt=media\&token=448b295d-ae4b-4896-8767-282023093c1b)

The Manage page is where the Wi-Fi Access Point information for the Hub can be viewed and changed. In the image below, the Hub's Wi-Fi name, password, band, and channel can be changed.&#x20;

Once changes have been made select **Apply Wi-Fi Settings**.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_biLePwYuJ3rC-fkeb%2F-M\_ggsCk28dyRHR1BInM%2FAccessing%20RCC%20-%20manage%20page.svg?alt=media\&token=321f9780-9d1e-4d37-a7b5-c8f8ec735293)

{% hint style="danger" %}
You will need to reconnect to the new Wi-Fi network after changing the name/and or password.
{% endhint %}

## Using the User Button

The Control Hub has a user button underneath the LED on the right side of the device. This button allows for a [Wi-Fi reset](managing-wi-fi-on-the-control-hub.md#wi-fi-reset) or [changing the Wi-Fi band](managing-wi-fi-on-the-control-hub.md#changing-wi-fi-band) currently being used on the Control Hub.

### Wi-Fi Reset

If you are unable to connect to the Control Hub's Wi-Fi after switching to the 5 GHz band, you can perform a Wi-Fi factory reset. The Wi-Fi network name and password will be reset to their default values, and the Wi-Fi band will be set to 2.4 GHz. To perform a Wi-Fi reset, please follow the steps below.&#x20;

{% hint style="info" %}
The Wi-Fi reset can take several minutes to complete.&#x20;
{% endhint %}

| Step                                                                                                                                                                            | Image                                                                                                                                                                                                                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Press and hold the button on the front of the Control Hub.                                                                                                                      | ![A picture containing remote, monitor, black, electronics&#xA;&#xA;Description automatically generated](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gRI0-TiCIKyOqh%2F58.png?generation=1590614868007820\&alt=media) |
| While pressing the button, power on the Control Hub.                                                                                                                            | ![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gSDiif0kH2u05j%2F59.png?generation=1590614868035362\&alt=media)                                                                                                      |
| Release button when the Control Hub LED begins to flash a multitude of colors. When the Control Hub flashes Blue then Green it has completed the reset and is ready to connect. |                                                                                                                                                                                                                                                                                                              |

{% hint style="success" %}
When the Control Hub flashes Blue then Green it has completed the reset and is ready to connect. The Wi-Fi network will reset back to the default name and password.
{% endhint %}

### Changing Wi-Fi Band

When running version 1.1.2 or later of the Operating System, the Control Hub can switch between the 2.4GHz and 5GHz Wi-Fi bands without access to the REV Hardware Client or the Robot Controller Console. This will only change the Wi-Fi band. When switching to a Wi-Fi band this way, the most recent channel selected on that band will be used (defaulting to auto).



| Step                                                                                                                  | Image                                                                                                                                                                                                                                                                                                                                                                      |
| --------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| While pressing the button, power on the Control Hub.                                                                  | ![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gSDiif0kH2u05j%2F59.png?generation=1590614868035362\&alt=media)                                                                                                                                                                    |
| Press and hold the button on the front of the Control Hub after the Control Hub has fully booted (LED is solid green) | ![A picture containing remote, monitor, black, electronics&#xA;&#xA;Description automatically generated](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MIye5\_C5oSoi2e84W9b%2F-MIym3ENg0UyQJ60AUhH%2FControl%20Hub%20with%205%20second%20blink%202.svg?alt=media\&token=3b8fa3ab-3810-42a1-b48d-78a3125e14ea) |
| Release button when the Control Hub LED flashes MAGENTA or YELLOW.                                                    |                                                                                                                                                                                                                                                                                                                                                                            |

{% hint style="info" %}
The Control Hub's LED blinks magenta when the band is switched to 5 GHz and yellow when the band is switched to 2.4 GHz.
{% endhint %}
