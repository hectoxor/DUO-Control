# Control Hub Specifications

The REV Robotics Control Hub ([REV-31-1595](https://www.revrobotics.com/rev-31-1595/)) is an affordable all in one educational robotics controller that provides the interfaces required for building robots, as well as other mechatronics, with multiple programming language options. The Control Hub was designed and built as an easy to use, dependable, and durable device for use in classroom and the competition. It features an Android operating system, built-in dual band Wi-Fi (802.11 ac/b/g/n/w), and a mature software package designed for both basic and advanced use cases. When the Control Hub software is updated with new features, the controller can receive a "field upgrade," through an update process that is fast and simple.&#x20;

The Control Hub is an approved device for use in FIRST® Global and FIRST Tech Challenge.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M7xwW\_Zlhwx3rRVvBv3%2F-M7xwqJwuFVOnDDc6Tu2%2Fimage.png?alt=media\&token=56a956f2-9a47-4148-b177-3999bfc89ee0)

| **Port Label** | **Qty** |                            **Connector**                           | Description                                                         |
| -------------- | :-----: | :----------------------------------------------------------------: | ------------------------------------------------------------------- |
| Battery        |    2    |         [XT-30](cables-and-connectors/xt-30-power-cable.md)        | Connect one 12V NiMh battery, add an Expansion Hub with second port |
| Motor          |    4    |    [JST VH, 2-pin](cables-and-connectors/jst-vh-motor-power.md)    | Motor power output                                                  |
| Encoder        |    4    | [JST PH, 4-pin](cables-and-connectors/jst-ph-sensors-and-rs485.md) | Quadrature encoder input                                            |
| Servo          |    6    |                             0.1” Header                            | Extended range 5V servo output                                      |
| +5V Power      |    2    |                             0.1” Header                            | Power for auxiliary device(s)                                       |
| Analog         |    4    | [JST PH, 4-pin](cables-and-connectors/jst-ph-sensors-and-rs485.md) | Analog input with two channels per connector.                       |
| Digital        |    8    | [JST PH, 4-pin](cables-and-connectors/jst-ph-sensors-and-rs485.md) | Digital Input/Output with two channels per connector                |
| I2C            |    4    | [JST PH, 4-pin](cables-and-connectors/jst-ph-sensors-and-rs485.md) | Four separate I2C busses                                            |
| RS485          |    2    | [JST PH, 3-pin](cables-and-connectors/jst-ph-sensors-and-rs485.md) | Use this serial communication port to add an Expansion Hub          |
| UART           |    2    | [JST PH, 3-pin](cables-and-connectors/jst-ph-sensors-and-rs485.md) | Debugging only                                                      |
| USB C          |    1    |                                USB C                               | Connect directly to the Control Hub via PC, USB 2.0                 |
| USB 2.0        |    1    |                                USB A                               | Connect USB cameras and other USB peripherals to the Control Hub    |
| USB 3.0        |    1    |                                USB A                               | Connect USB cameras and other USB peripherals to the Control Hub    |
| HDMI           |    1    |                               HDMI A                               | Supports 4k @ 60Hz                                                  |

## Specifications

The following tables provide the operating and mechanical specifications for the Control Hub.

### General Specifications

| Feature type | Description                                                                     |
| ------------ | ------------------------------------------------------------------------------- |
| Processor(s) | <p>RK3328 Quad-core ARM® Cortex-A53</p><p>Texas Instruments ARM® Cortex®-M4</p> |
| Memory       | 1GB LPDDR3                                                                      |
| Storage†     | 8GB eMMC 4.51                                                                   |
| Wireless     | <p>802.11 ac/b/g/n/w Wi-Fi; Dual Band 2.4 &#x26; 5 GHz</p><p>Bluetooth 4.1</p>  |
| Graphics‡    | <p>GPU - ARM® Mali 450MP4</p><p>HDMI 2.0 support for 4k @ 60Hz</p>              |

|   |                                                                  |
| - | ---------------------------------------------------------------- |
| † | Supports expandable storage through the SD Card slot             |
| ‡ | Display graphics supported through an external display over HDMI |

{% hint style="danger" %}
DO NOT exceed the absolute maximum electrical specifications. Doing so will cause permanent damage to the Control Hub and will void the warranty.
{% endhint %}

### Input Power Specifications

| **Parameter**                        | **Min** | **Typ** | **Max** | **Units** |
| ------------------------------------ | :-----: | :-----: | :-----: | :-------: |
| Operating voltage range ($$V_{IN}$$) |    8    |    12   |    15   |     V     |
| Absolute maximum supply voltage      |    -    |    -    |    15   |     V     |

### Motor Port Specifications

| **Parameter**                     | **Min** | **Typ** | **Max** | **Units** |
| --------------------------------- | :-----: | :-----: | :-----: | :-------: |
| Continuous output current †       |    -    |    -    |    10   |     A     |
| Absolute maximum output current ‡ |    -    |    -    |    20   |     A     |

|    |                                                                                                                                                 |
| -- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| †  | Exceeding the continuous current maximum depends on many thermal factors. The outputs will self protect once they approach their thermal limit. |
| ‡  | Maximum current is ultimately limited by the in-line battery fuse.                                                                              |

### Encoder Port Specifications

| **Parameter**                     | **Min** | **Typ** | **Max** | **Units** |
| --------------------------------- | ------- | ------- | ------- | --------- |
| Encoder port input voltage        | 0       | -       | 3.3     | V         |
| Encoder port supply voltage       | -       | -       | 3.3     | V         |
| Encoder port total supply current | -       | -       | 500     | mA        |

{% hint style="info" %}
See [Sensors - Encoders](../sensors/encoders/) for more information on encoders and using the encoder ports. For using non-REV motor encoders see [Using 5V Sensors - Encoders](../sensors/using-3rd-party-sensors/) for more details.
{% endhint %}

### Digital Port Specifications

| **Parameter**                     | **Min** | **Typ** | **Max** | **Units** |
| --------------------------------- | ------- | ------- | ------- | --------- |
| Digital port input voltage        | 0       | -       | 3.3     | V         |
| Digital port supply voltage       | -       | -       | 3.3     | V         |
| Digital port total supply current | -       | -       | 1       | A         |

{% hint style="info" %}
See [Sensors - Digital](../sensors/digital.md) for more information on using the digital ports. See [Using 5V Sensors](../sensors/using-3rd-party-sensors/) for information on using 5V logic level devices with the digital ports.
{% endhint %}

### Analog Port Specifications

| **Parameter**                     | **Min** | **Typ** | **Max** | **Units** |
| --------------------------------- | ------- | ------- | ------- | --------- |
| Analog port input voltage range † | 0       | -       | 5       | V         |
| Analog port supply voltage        | -       | -       | 3.3     | V         |
| Analog port total supply current  | -       | -       | 500     | mA        |

|   |                                                                                                                                                                               |
| - | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| † | The analog input will accept up to 5V. When using 5V analog sensors, a custom wiring harness is needed to provide 5V of power for the sensor as the power pin provides 3.3V.  |

{% hint style="info" %}
See [Sensors - Analog](../sensors/analog.md) for more information on using the analog ports.
{% endhint %}

### I2C Port Specifications

| **Parameter**                 | **Min** | **Typ** | **Max** | **Units** |
| ----------------------------- | ------- | ------- | ------- | --------- |
| I2C port input voltage range  | 0       | -       | 3.3     | V         |
| I2C port supply voltage       | -       | -       | 3.3     | V         |
| I2C port total supply current | -       | -       | 500     | mA        |
| Bus speed                     | -       | 100/400 | -       | kHz       |

{% hint style="info" %}
See [Sensors - I2C](../sensors/i2c/) for more information on using the I2C ports. See [Using 5V Sensors](../sensors/using-3rd-party-sensors/) for information on using 5V logic level devices with the I2C ports.
{% endhint %}

### Servo Port Specifications

| **Parameter**                           | **Min** | **Typ** | **Max** | **Units** |
| --------------------------------------- | ------- | :-----: | ------- | --------- |
| Servo output signal voltage             | 0       |    -    | 5       | V         |
| Servo port supply voltage               | -       |    5    | -       | V         |
| Servo port pair total supply current †  | -       |    -    | 2       | A         |
| Absolute maximum total supply current ‡ | -       |    -    | 5       | A         |
| Servo port output pulse range           | 500     |    -    | 2500    | μs        |

|   |                                                                                |
| - | ------------------------------------------------------------------------------ |
| † | Total supply is shared across pairs of ports (0-1, 2-3, 4-5)                   |
| ‡ | The 5A total supply current for all servo ports and +5V power ports is shared. |

### +5V Power Port Specifications

| **Parameter**                              | **Min** | **Typ** | **Max** | **Units** |
| ------------------------------------------ | ------- | :-----: | ------- | --------- |
| +5V power port output voltage              | -       |    5    | -       | V         |
| +5V power port pair total supply current † | -       |    -    | 2       | A         |
| Absolute maximum total supply current ‡    | -       |    -    | 5       | A         |

|   |                                                                                |
| - | ------------------------------------------------------------------------------ |
| † | Total supply current is shared across both ports                               |
| ‡ | The 5A total supply current for all servo ports and +5V power ports is shared. |

### Mechanical Specifications

| **Parameter**       | **Min** | **Typ** | **Max** | **Units** |
| ------------------- | :-----: | :-----: | :-----: | :-------: |
| Body length         |    -    |   103   |    -    |     mm    |
| Body width          |    -    |   143   |    -    |     mm    |
| Body height         |    -    |   29.5  |    -    |     mm    |
| Weight              |    -    |   209   |    -    |     g     |
| Mounting hole pitch |    -    |    16   |    -    |     mm    |
