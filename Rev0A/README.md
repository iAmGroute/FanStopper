# Fan Stopper revision 0A

### Overview

+ A 431 ([TL431](http://www.ti.com/lit/ds/symlink/tl431.pdf) or [CJ431](https://datasheet.lcsc.com/szlcsc/Changjiang-Electronics-Tech-CJ-CJ431_C3113.pdf)) programmable voltage reference (D1) is at the heart of this circuit. It is used in an open loop configuration as a comparator with an internal 2.5V reference. Its output drives the gate of the 2 p-channel mosfets (Q1 and Q2).
+ Q1 is the primary mosfet and acts like a switch, turning the load (a fan that is connected to VOUT) on when its gate voltage is low and off otherwise. Its gate voltage is determined by D1 whose cathode (pad 1) goes to around 1.9V when its reference input (pad 2) goes above 2.5V. That voltage is determined by the input (VIN) scaled by the resistors R1 and R2 and the potentiometer R3.
+ Q2 provides positive feedback: when it start conducting, it brings R4 and the higher part of the potentometer (pads 1 to 3) in parallel to R1 which causes the reference voltage to rise, thus causing D1's cathode to draw more current and drop Q2's gate voltage further, which makes Q2 conduct even more. This is done to add hysteresis to the circuit so that when the fan turns on, it won't turn back off due to a small drop of the input voltage (which would cause it to turn on and off very often).
+ D2 is added together with D3 for reverse polarity (if the device is plugged in backwards) and reverse current protection (if the fan produces power - perhaps being spun by a vacuum cleaner ?).

### Schematic

![Schematic](Schematic.png?raw=true)

### PCB

### Photos

### Issues

+ The adjustment of the threshold voltage is not linear with respect to the potentiometer's position.
+ The hysteresis in the higher setpoints is significantly larger than that of the lower setpoints, although that is mostly evident in the far ends of the range.
