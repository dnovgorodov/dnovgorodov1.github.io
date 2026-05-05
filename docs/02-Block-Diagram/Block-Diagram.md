---
title: Module's Block Diagram

## Overview

Block Diagram for my wireless communication (MQTT) subsystem.

## Block Diagram 

![Block Diagram](EGR314_Subsystem_BlockDiagram.png)

## Explanation

Essentially, I designed the MQTT subsystem around making sure the ESP32 would run stable and reliably while handling wireless communication. Since the ESP32 already has built-in Wi-Fi and supports MQTT, I used it as the main controller and focused on supporting it properly with a solid power setup. Since it requires 3.3V, I used an LM2575-3.3V voltage regulator to make sure it always gets a steady supply, and then used capacitors and inductors to smooth out noise and handle any sudden current spikes, and then there are the enable and boot buttons of course. My subsystem does not have any sensors/actuators because I was responsible for the MQTT.

## Source files

I only really had one source file (the .drawio file), but [here](BlockDiagram314.zip) it is in a zip file.
