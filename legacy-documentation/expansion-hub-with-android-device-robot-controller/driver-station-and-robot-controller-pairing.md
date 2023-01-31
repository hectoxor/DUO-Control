# Driver Station and Robot Controller Pairing

When you first receive your Expansion Hub, you will have to install the Driver Station and Robot Controller Applications and pair (link) your Driver Station (Android Device) to your Robot Controller. The following sections of the page will walk through how to install the applications and how to connect the Driver Station to the Robot Controller's Network.&#x20;

## **Install Applications**&#x20;

### **Android Developer Options**

In order to install the Driver Station Application _****_ or Robot Controller Application onto and Android phone, the phone's developer settings and USB debugging options need to be turned on.&#x20;

The developer options on Android Devices are hidden within the phone as a default. Different phone manufactures will have different ways of accessing the developer options. However, once the developer options are available in the phone's settings, the steps for activating USB debugging and development settings are similar.&#x20;

{% hint style="danger" %}
Before moving forward it is advised to look up where the developer options on your Android Device are located. For Motorolla users, the Motorolla Support Page has information on how to unlock the developer options.
{% endhint %}

| ​                                                                                                                    | ​                                                                                                                                                                                                                                                                                                     |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Open the Android Devices settings                                                                                    | <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MGnDtY08gY940ZZA2Gp%2F-MGnOO0_68a5pk5k8QLx%2FScreenshot_20200903-094800.png?alt=media&#x26;token=eff8c4a9-39a7-4820-ae2d-b02a2dca23b7" alt="" data-size="original"></p> |
| Scroll to the bottom of the settings, where the unlocked developer options are available. Open the developer options | <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MGnDtY08gY940ZZA2Gp%2F-MGnOyKijL413uuk7knF%2FScreenshot_20200903-094811.png?alt=media&#x26;token=489fbc53-e8ef-42da-83c5-862e528634fb" alt="" data-size="original"></p> |
| At the top of the developer options page is an on/off switch. Turn the developer options on.                         | <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MGnDtY08gY940ZZA2Gp%2F-MGnPDBGGK5c7fDjSZ-5%2FScreenshot_20200903-094818.png?alt=media&#x26;token=aeab77dc-41cf-47c5-8d6a-082d024e2c9d" alt="" data-size="original"></p> |
| The device will open a confirmation message. Select 'OK.'                                                            | <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MGnDtY08gY940ZZA2Gp%2F-MGnPPXxOtGHr_j_mX0M%2FScreenshot_20200903-094822.png?alt=media&#x26;token=d33ab940-b148-4e8d-a690-9d9cd0b97bd7" alt="" data-size="original"></p> |
| Scroll through the developer options until you find the Debugging section. Turn USB Debugging on.                    | <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MGnDtY08gY940ZZA2Gp%2F-MGnPd1do5isMW8cmfRW%2FScreenshot_20200903-094831.png?alt=media&#x26;token=3c8b9b9c-1e12-49a0-bb9f-c4d76b8d8047" alt="" data-size="original"></p> |
| Another confirmation message will appear, click 'OK.'                                                                | <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MGnDtY08gY940ZZA2Gp%2F-MGnPvVMgVSi6cRbmCQv%2FScreenshot_20200903-094835.png?alt=media&#x26;token=8f78d6e4-87d5-42e0-9603-38c1665c2cfc" alt="" data-size="original"></p> |

USB debugging is now on! You can move on to the steps for installing the application.

### Driver Station Application&#x20;

{% hint style="info" %}
The following steps will go through how to install the Driver Station Application via the REV Hardware Client. It is possible to install the application via the FTC GitHub repository as well.
{% endhint %}

Connect the Android Device to a PC with the REV Hardware Client installed.

Startup the REV Hardware Client. Once the Android Device is fully connected it will show up on the front page of the UI under the **Hardware Tab**. Select the Android Device.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGnDtY08gY940ZZA2Gp%2F-MGnQndSMGYRPbtPXYaW%2FAndroid%20Device%20Connected.png?alt=media\&token=ab1273e8-56f8-4f08-af27-93cc5c28fd7e)

After selecting the Connected Hardware the Update tab will pop up. Under **Driver Station App** select Download.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGnDtY08gY940ZZA2Gp%2F-MGnTeLef0pI\_QyCR3qO%2FAndroid%20Device%20Menu%20Download%20DS%20.png?alt=media\&token=7c973e40-3b83-4409-b839-e55627599002)

Once the Driver Station App has downloaded, select Install.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGnDtY08gY940ZZA2Gp%2F-MGnX5ZLpzALgiEYbFM3%2FAndroid%20Device%20Menu%20Installing%20DS.png?alt=media\&token=b27a1d1b-189b-43e9-814a-5b568b9aa05f)

When the application installation has completed the status for the Robot Controller App will change to "Up-to-Date."

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGnDtY08gY940ZZA2Gp%2F-MGnXY2dmMqPZ43PKYai%2FAndroid%20Device%20Menu%20DS%20Installed.png?alt=media\&token=ff2c6780-4571-454b-a4f0-bbc4b9a0fde0)

#### Robot Controller Application <a href="#robot-controller-application" id="robot-controller-application"></a>

The following steps will go through how to install the Robot Controller Application via the REV Hardware Client. It is possible to install the application via the [FTC GitHub repository](https://github.com/FIRST-Tech-Challenge/FtcRobotController) as well.

Connect the Android Device to a PC with the REV Hardware Client installed.

Startup the REV Hardware Client. Once the Android Device is fully connected it will show up on the front page of the UI under the **Hardware Tab**. Select the Android Device.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGnDtY08gY940ZZA2Gp%2F-MGnQndSMGYRPbtPXYaW%2FAndroid%20Device%20Connected.png?alt=media\&token=ab1273e8-56f8-4f08-af27-93cc5c28fd7e)

After selecting the Connected Hardware the Update tab will pop up. Under **Robot Controller App** select Download.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGnDtY08gY940ZZA2Gp%2F-MGnZAiOc7Sd\_clC9WP\_%2FAndroid%20Device%20Menu.png?alt=media\&token=3f83ba60-1db3-412d-a6e1-2e000af2713a)

Once the Robot Controller App has downloaded, select Install.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGnDtY08gY940ZZA2Gp%2F-MGn\_xwJz3sYGpauvwwP%2FAndroid%20Device%20Menu%20Installing%20RC.svg?alt=media\&token=64cab7ab-487b-4534-9f0e-b18c15e916c1)

When the application installation has completed the status for the Robot Controller App will change to "Up-to-Date."

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGnDtY08gY940ZZA2Gp%2F-MGnYy9ImkUOExlPbtDX%2FAndroid%20Device%20Menu%20RC%20installed.png?alt=media\&token=94524528-cd0e-4c99-8e03-4c553b53cda0)

## Driver Station and Robot Controller Pairing&#x20;

{% hint style="warning" %}
You should update your Driver Station(DS) and Robot Controller(RC) phones to the latest app version in order to use the Expansion Hub controller. The minimum compatible version is 3.1 released on May 10th, 2017
{% endhint %}

Please ensure that the Driver Station and Robot Controller phones are properly configured and paired. Refer to the latest pairing and troubleshooting instructions provided by in the [FTC Control System Wiki](https://github.com/ftctechnh/ftc\_app/wiki).
