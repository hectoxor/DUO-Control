# Status LED Blink Codes

The RGB LED located on the Control Hub ([REV-31-1595](https://www.revrobotics.com/rev-31-1595/)) and Expansion Hub ([REV-31-1153](https://www.revrobotics.com/rev-31-1153/)) near the RS485 ports and on the bottom of the Driver Hub ([REV-31-1956](status-led-blink-codes.md)) provide user feedback regarding the status of the Hub. Below is a Table of the Blink Codes.&#x20;

## Control Hub&#x20;

{% hint style="info" %}
All Control Hub Blink Codes assume the latest [Control Hub Operating System](../updating-and-managing/updating-operating-system/) is running on the device
{% endhint %}

### Robot Controller Application 6.0 or Higher&#x20;

If a Control Hub is running Robot Controller Application 5.5 or lower the LED Blink Codes for the Hub will be the same as an [Expansion Hub running Firmware Version 1.7.0 or higher](status-led-blink-codes.md).&#x20;

| **LED Status**                                                                                                                                                                                                                                                                                                                               | **LED Description** | **When**                                                                                                                                                                    | **Hub Status**                                                                                                                                                                                                                                                               |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gTUs6f_i1L-cEQ%2F60.png?generation=1590614867875017&#x26;alt=media" alt="" data-size="original"></p><p>​</p>                                                                         | Solid Blue          | At Boot                                                                                                                                                                     | Control Hub has power; Battery is >7V and is waiting to initialize communications.                                                                                                                                                                                           |
| <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gUxP3oImsccuCM%2F61.png?generation=1590614867882163&#x26;alt=media" alt="" data-size="original"></p><p>​</p>                                                                         | Solid Blue          | Anytime                                                                                                                                                                     | <p>Hub is waiting for communication with the Driver Station Host.</p><p>Control Hub has power; Battery is >7V.</p>                                                                                                                                                           |
| <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MIyof0PrJeWfI7k0uAK%2F-MIz6EtgaDw3bcbe6ZKC%2FControl%20Hub%20with%20not%20blink%20(Led%20blink%20codes.svg?alt=media&#x26;token=9088e107-29af-46bf-830e-b89d9b5d411a" alt="" data-size="original"></p><p>​</p> | Solid Green         | Anytime                                                                                                                                                                     | Hub has power and active communication with the Android Platform.                                                                                                                                                                                                            |
| <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gXhpjQ3WIQI9_M%2F64.png?generation=1590614867867223&#x26;alt=media" alt="" data-size="original"></p><p>​</p>                                                                         | Blinking Blue       | Anytime                                                                                                                                                                     | Keep alive has timed out. Fault will clear when communication resumes.                                                                                                                                                                                                       |
| <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gYOL7YboxKfFeO%2F65.png?generation=1590614867913470&#x26;alt=media" alt="" data-size="original"></p><p>​</p>                                                                         | Blinking Orange     | Anytime                                                                                                                                                                     | <p>Battery Voltage is lower than 7V. Either the 12V battery needs to be charged, or the Expansion Hub is running on USB power only. This fault will clear when battery voltage is raised above 7V.</p><p>This will not be overwritten by the keep alive timeout pattern.</p> |
| <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MOhf57w92ewfOX_crbm%2F-MOhizyMHL9yNcExH3Wp%2FMagenta%20Blink.svg?alt=media&#x26;token=0241bb33-1c99-4e00-a0ed-97bb5aee536e" alt="" data-size="original"></p>                                                   | Blinking Magenta    | <p>​</p><p><a href="../updating-and-managing/managing-wi-fi-on-the-control-hub.md#supported-android-devices-and-wi-fi-band-capabilities">During Wi-Fi Reset</a></p><p>​</p> | Control Hub changed Wi-Fi Band to 5GHz after pressing the button                                                                                                                                                                                                             |
| <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-MOhf57w92ewfOX_crbm%2F-MOhj9MgOLMUtsvlUEbv%2FYellow%20Blink.svg?alt=media&#x26;token=58423089-a773-4100-a72c-6582530751fb" alt="" data-size="original"></p>                                                    | Blinking Yellow     | <p>​</p><p><a href="../updating-and-managing/managing-wi-fi-on-the-control-hub.md#supported-android-devices-and-wi-fi-band-capabilities">During Wi-Fi Reset</a></p><p>​</p> | Control Hub changed Wi-Fi Band to 2.4GHz after pressing the button                                                                                                                                                                                                           |

## Driver Hub

{% hint style="info" %}
All Driver Hub Blink Codes assume the latest [Driver Hub Software](../updating-and-managing/updating-the-driver-hub/) is running on the device
{% endhint %}

#### LED A

| LED Status                                                                                                                                                                                                                                                                                | LED Description | Hub Status                  |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | --------------------------- |
| <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FUOOiQ4S2QcMWmVoSmeQ8%2Fuploads%2FoLbmw3reHO0AON1Fl9dT%2FWhite%20Blink.svg?alt=media&#x26;token=1a3952a4-968e-4781-81be-b59669b86f86" alt="" data-size="original"></p><p>​</p> | Blinking White  | Operating System is Booting |
| <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FUOOiQ4S2QcMWmVoSmeQ8%2Fuploads%2FHHJlRMlZPsCRYdWPwSaI%2FGreen%20Blink.svg?alt=media&#x26;token=4765fa46-7f96-4d44-8bb6-ebc841d4c2cd" alt="" data-size="original"></p><p>​</p> | Blinking Green  | General Activity            |

#### LED B

| LED Status                                                                                                                                                                                                                                                                        | LED Description | Hub Status   |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ------------ |
| <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FUOOiQ4S2QcMWmVoSmeQ8%2Fuploads%2FOV1kePk53TatOm8jigfN%2Fimage.png?alt=media&#x26;token=7991df34-ee23-4751-bc9b-201e06428acc" alt="" data-size="original"></p><p>​</p> | Solid Green     | Device is on |

#### Battery Status LED

| LED Status                                                                                                                                                                                                                                                                              | LED Description | Hub Status       |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ---------------- |
| <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FUOOiQ4S2QcMWmVoSmeQ8%2Fuploads%2FElAO73RNlAflSjec3xY7%2FRed%20Blink.svg?alt=media&#x26;token=36f645b9-0eba-4a0c-a91c-f3d3221d0986" alt="" data-size="original"></p><p>​</p> | Blinking Red    | Battery Charging |
| <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FUOOiQ4S2QcMWmVoSmeQ8%2Fuploads%2FKsmJ1fwu1igZA5dzfTKx%2FRed%20Solid.svg?alt=media&#x26;token=a12f8075-3146-471e-8c15-e8acdcb4b810" alt="" data-size="original"></p><p>​</p> | Solid Red       | Battery Charged  |

## Expansion Hub

### Firmware Version 1.7.0 or Higher&#x20;

#### Firmware Version 1.7.0 or Higher <a href="#firmware-version-1.7.0-or-higher" id="firmware-version-1.7.0-or-higher"></a>

| **LED Status**                                                                                                                                                                                                                                                                           | **LED Description**                                                    | **When** | **Hub Status**                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gTUs6f_i1L-cEQ%2F60.png?generation=1590614867875017&#x26;alt=media" alt="" data-size="original"></p><p>​</p>                     | Solid Blue                                                             | At Boot  | Hub has power; Battery is >7V and is waiting to initialize communications.                                                                                                                                                                                                                                                                                                                                                                           |
| <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gUxP3oImsccuCM%2F61.png?generation=1590614867882163&#x26;alt=media" alt="" data-size="original"></p><p>​</p>                     | Solid Blue                                                             | Anytime  | <p>Hub is waiting for communication with the Robot Controller.</p><p>Hub has power; Battery is >7V.</p>                                                                                                                                                                                                                                                                                                                                              |
| <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4_pJHI8HTuZFQTNfcy%2F-M8MwLCHioGUmBeHgdmq%2F-M8N8UYa5t0kzRXp0G4I%2Fimage.png?alt=media&#x26;token=ca7eb6c6-2cd9-4a41-8afa-e89d91c94917" alt="" data-size="original"></p><p>​</p> | <p>Solid Green with one or more blue blinks every</p><p>~5 Seconds</p> | Anytime  | <p>Hub has power and active communication with the Android Platform. The number of blue blinks is the same as the Expansion Hub’s address.</p><p>The factory default address is 2 (</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gWZ_ijZcjG3K9F%2F63.png?generation=1590614867922880&#x26;alt=media" alt="" data-size="original"></p><p>).</p> |
| <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gXhpjQ3WIQI9_M%2F64.png?generation=1590614867867223&#x26;alt=media" alt="" data-size="original"></p><p>​</p>                     | Blinking Blue                                                          | Anytime  | Keep alive has timed out. Fault will clear when communication resumes.                                                                                                                                                                                                                                                                                                                                                                               |
| <p>​</p><p><img src="https://2589213514-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gYOL7YboxKfFeO%2F65.png?generation=1590614867913470&#x26;alt=media" alt="" data-size="original"></p><p>​</p>                     | Blinking Orange                                                        | Anytime  | <p>Battery Voltage is lower than 7V. Either the 12V battery needs to be charged, or the Expansion Hub is running on USB power only. This fault will clear when battery voltage is raised above 7V.</p><p>This will not be overwritten by the keep alive timeout pattern.</p>                                                                                                                                                                         |