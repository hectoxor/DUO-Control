# SPARKmini Motor Controller

The SPARKmini Motor Controller ([REV-31-1230](https://www.revrobotics.com/rev-31-1230/)) is an inexpensive in-line brushed DC motor controller designed to give _FIRST®_ Tech Challenge teams more bang for their buck. It offers the same performance characteristics as the REV Control Hub ([REV-31-1595](https://www.revrobotics.com/rev-31-1595/)) or Expansion Hub **** ([REV-31-1153](https://www.revrobotics.com/rev-31-1153/)) motor ports in a small 60mm x 22mm footprint. Now FTC teams can add a SPARKmini Motor Controller to utilize more than four DC motors from a single Hub in a space-efficient package.&#x20;

### Power and Motor Connections

The SPARKmini has three integrated wires with connectors dedicated to power, control, and the motor; one [XT30 connector ](../system-overview/cables-and-connectors/xt-30-power-cable.md)for power, one 3-wire servo-PWM connector for control, and one [JST-VH ](../system-overview/cables-and-connectors/jst-vh-motor-power.md)connector for the motor. The figure below shows each of these connections.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8S63YNATJr5J\_ZuT4z%2F-M8S6x4RlQpD17v6ojlt%2F2.png?generation=1590700268318203\&alt=media)

Connect the power wire to a free XT30 port on the REV Control Hub , REV Expansion Hub ([REV-31-1153](https://www.revrobotics.com/rev-31-1153/)), or through an XT30 Power Distribution Block ([REV-31-1293](https://www.revrobotics.com/rev-31-1293/)) that is connected to a free Control/Expansion Hub XT30 port. Connect the control wire to an open servo port on the hub and the motor wire to a JST-VH port on a motor, like the REV HD Hex Motor ([REV-41-1301](https://www.revrobotics.com/rev-41-1301/)) or the REV Core Hex Motor ([REV-41-1300](https://www.revrobotics.com/rev-41-1300/)).

{% hint style="danger" %}
DO NOT reverse polarity on the power input connections. The SPARKmini does not contain reverse polarity protection. This can permanently damage the SPARKmini and will void the warranty.
{% endhint %}

{% hint style="danger" %}
DO NOT swap the motor and power connections. This can result in uncontrolled motor operation and can permanently damage the SPARKmini, voiding the warranty.
{% endhint %}

### &#x20;Servo-PWM Input

A motor’s speed is controlled by varying the voltage that is applied to it. The SPARKmini’s output voltage can be controlled by sending it an extended-range servo-PWM pulse. The extended 500µs to 2500µs servo-pulse corresponds to full-reverse and full-forward rotation with 1500µs as the neutral position (no rotation). The pulses are proportionally related to the motor output duty cycle, therefore variable speed can be achieved with pulses in between the extremes. The following table describes the pulse ranges in more detail.

Table - Control Signal Pulse Ranges

| **Pulse Width (**_**p**_** in µs)** |                   |                   |                   |                  |
| ----------------------------------- | ----------------- | ----------------- | ----------------- | ---------------- |
| **Full Reverse**                    | **Prop. Reverse** | **Neutral**       | **Prop. Forward** | **Full Forward** |
| _p_ ≤ 500                           | 500 < _p_ < 1490  | 1490 ≤ _p_ ≤ 1510 | 1510 < _p_ < 2500 | 2500 ≤ _p_       |

### Zero-Power Behavior

When the SPARKmini is receiving a neutral command it will not provide any power to the attached motor. There are two options for how the SPARKmini handles this zero-power state:

**Brake** - Motor terminals are shorted to each other to dissipate electrical energy, effectively braking the motor.\
**Coast** - Motor terminals are disconnected, allowing the motor to spin down at its own rate.

The zero-power behavior can be selected via a switch located towards the center of the SPARKmini housing, shown in Figure 2. Each mode can be selected by sliding the switch to either the Brake (B) or Coast (C) positions.

![Coast/Brake Switch](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8S63YNATJr5J\_ZuT4z%2F-M8S6x4SV5pOuTuqJEl4%2F3.png?generation=1590700268319111\&alt=media)

The SPARKmini will indicate whether it is in Brake or Coast mode via the Status LED, located in the center of the housing, whenever it is outputting zero-power. Solid or flashing blue indicates Brake Mode while solid or flashing yellow indicates Coast Mode. See the LED Status Codes section for more details.

### LED Status Codes

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MBpTihAyYN0ZC30Q7rL%2F-MBpVtluQt88S1r89S-z%2FSPARKmini%20Codes%20-%20Export.svg?alt=media\&token=f71c289c-5028-4645-be17-eb92356e4dbc)

### Specifications

| **Parameter**                   | **Min** |    **Typ**   | **Max** | **Unit** |
| ------------------------------- | :-----: | :----------: | :-----: | :------: |
| Supply voltage range (VIN)      |   6.0   |      12      |    20   |     V    |
| Supply voltage absolute maximum |    -    |       -      |    25   |     V    |
| Continuous output current       |    -    |       -      |    15   |     A    |
| Peak output current             |    -    |       -      |    20   |     A    |
| Output voltage range            |  - VIN  |       -      |  + VIN  |     V    |
| Output frequency                |    -    |      10      |    -    |    kHz   |
| Input pulse width range         |   500   |       -      |   2500  |    µs    |
| Input frequency                 |    16   |      50      |   200   |    Hz    |
| Input timeout                   |    -    |     65.5     |    -    |    ms    |
| Input deadband                  |    -    |      ±10     |    -    |    µs    |
| Input low-level voltage         |   -0.3  |       -      |   0.8   |     V    |
| Input high-level voltage        |   2.0   |      5.0     |   5.3   |     V    |
| Weight                          |    -    |     0.87     |    -    |    oz    |
| Dimensions (excluding wires)    |    -    | 60 x 22 x 12 |    -    |    mm    |

