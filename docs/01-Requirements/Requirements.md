---
title: Module's Requirements
---

## Module Requirements
My module will include a two-way wireless communication using ESP-32s.

| **Requirement Description** | **Measure of<br> Threshold** | **Target<br>Measure** |**Stretch<br>Requirement<br>(Y-N)**|
|-----------------------------| ----------------- | ----------------- | :-----: |
| Surface mounted, 3.3V switching power regulator | 3.2 Volts | 3.3 Volts | No |
| Surface mounted microcontroller | 1 PIC or ESP | ESP-32 | No |
| Wireless Communication | Able to send or receive a Wi-Fi data | Send and receive Wi-Fi Data to MQTT | Yes |
| Controller of some sorts | Able to send signals | Send signals to ESP-32 | Yes |

- The ESP-32 will be powered by using an outside power source which will be regulated down to 3.3V using the voltage regulator.
- I will likely use some sort of controller that will send the signals to the ESP-32, which will control the movement of the rover.
- I do not believe I will need either a motor or a serial sensor.
