---
title: Reflection
---

## Review of Module's Sucess

I succeeded in connecting the ESP32 to MQTT Explorer and having commands sent both ways (from the board to MQTT explorer and vice versa).

I also succeeded in receiving and sending data via RX and TX by using the UART communication protocol.

## Module Startup

Basically, the main issue I had with starting up the module was that I did not have the proper firmware installed. I just wish I had known that, and it would have saved me a few hours of troubleshooting.

## Lessons Learned

From working on this project, I learned a lot about both the design and implementation of a PCB system. One of the biggest takeaways was how important it is to plan everything out before starting the schematic and layout, including choosing the right components and understanding their datasheets. I learned how to design a stable power system using a 3.3V regulator and proper decoupling capacitors, and also how important PCB layout decisions are, especially things like grounding, component placement, and making sure to choose the correct trace widths depending on the current. I also learned how to create and double check custom footprints, after making a mistake with a push button that caused it to always be connected. On the assembly side, I learned how to use solder paste and a heat gun for surface-mount components. That made soldering and working with surface-mount components a lot easier than whan I tried to solder them the standard way. I also gained experience flashing firmware onto an ESP32 and using MQTT to send and receive data. Throughout the project, I improved my debugging skills by dealing with both hardware and software issues, and I learned that testing smaller parts of the system step by step is much more effective than trying to build everything at once. Finally, I learned how to apply feedback from design reviews and how even small design mistakes can have a big impact on the final system.

## Recommendations for Future Students

1. Start your design early and try not to procrastinate, because waiting for the board to get here takes time to get here in and of itself.
2. Test your system in smaller sections instead of trying to get everything working at once. It makes debugging much easier.
3. Try to get experience with using solder paste and heatguns. It makes soldering surface-mount components a lot easier.
4. Consider making surface-mount pads slightly wider than the width of the component's terminals. That can also make soldering easier.
5. Pay close attention to PCB layout, including trace widths, grounding, and component placement, because these directly affect performance.
