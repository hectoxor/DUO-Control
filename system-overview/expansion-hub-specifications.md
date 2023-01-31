# Expansion Hub Specifications

The REV Robotics Expansion Hub ([REV-31-1153](https://www.revrobotics.com/rev-31-1153/)) is a low-cost educational device that can communicate with any computer (commonly the [REV Robotics Control Hub](control-hub-specifications.md) or an Android Phone) to provide the interfaces required for building robots and other mechatronics. The Expansion Hub was purpose built to stand up to the rigors of the classroom and competition field. It features a mature firmware designed for basic and advanced use cases with the ability to be field upgraded in the future. &#x20;

The IO ports of the Expansion Hub are identical in specification to the Control Hub. Within this documentation, many sections may refer to the Control Hub, but the connections are the same for the Expansion Hub.

The REV Robotics Expansion Hub is an approved device for use in the FIRST Tech Challenge and FIRST Global.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M8LyoEbz8PG8p4KiY2\_%2F-M8MS9GTmSyQytKMtbo8%2Fimage.png?alt=media\&token=08a58294-6a28-49e6-b373-27a05c4e337e)

| **Port Label** | **Qty** | **Connector** | **Description**                                                                                                  |
| -------------- | :-----: | :-----------: | ---------------------------------------------------------------------------------------------------------------- |
| Battery        |    2    |      XT30     | Connect one 12V NiMh battery, add an Expansion Hub with second port                                              |
| Motor          |    4    | JST VH, 2-pin | Motor power output                                                                                               |
| Encoder        |    4    | JST PH, 4-pin | Quadrature encoder input                                                                                         |
| Servo          |    6    |  0.1” Header  | Extended range 5V servo output (500-2500ms)                                                                      |
| 5V Aux Power   |    2    |  0.1” Header  | Auxiliary device 5V/2A                                                                                           |
| Analog         |    4    | JST PH, 4-pin | Analog input 0-5.0V measurement range with two channels per connector. 3.3V provided on the connector power pin. |
| Digital        |    8    | JST PH, 4-pin | Digital Input/Output with two channels per connector                                                             |
| I2C            |    4    | JST PH, 4-pin | Four separate I2C busses, 100kHz/400kHz bus speed                                                                |
| RS485          |    2    | JST PH, 3-pin | Serial communication port to add a Hub (Control or Expansion)                                                    |
| UART           |    2    | JST PH, 3-pin | Debugging only                                                                                                   |
| MINI USB       |    1    |   USB Mini-B  | Connect directly to the Robot Controller Android device or PC                                                    |

## Specifications

The following tables provide the operating and mechanical specifications for the Expansion Hub.

{% hint style="danger" %}
DO NOT exceed the absolute maximum electrical specifications. Doing so will cause permanent damage to the Expansion Hub and will void the warranty.
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
See [Sensors - Encoders](../sensors/encoders/) for more information on encoders and using the encoder ports. For using non-REV motor encoders see [Using 3rd Party Sensors - Encoders](../sensors/using-3rd-party-sensors/#connecting-5v-encoder) for more details.
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
| I2C pull-up resistor          | -       | 2.49    | -       | kΩ        |

{% hint style="info" %}
**Expansion Hubs purchased AFTER December 2021 no longer include an internal IMU**
{% endhint %}

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
