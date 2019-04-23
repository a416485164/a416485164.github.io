---
layout:     post
title:      Efficient, Long-Term Logging of Rich Data Sensors using Transient Sensor Nodes
subtitle:   EMU
date:       2019-04-18
author:     Jackie
header-img: img/post-bg-iWatch.jpg
catalog: true
tags:
    - EMU
    - Rich Data
---

# Efficient, Long-Term Logging of Rich Data Sensors using Transient Sensor Nodes

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/EMU1.jpg)

***

## Background

### Energy sources are variable and environmental conditions unknown

In many cases, harvesting the maximum power from a particular source (e.g. solar,
thermal, etc) requires an impedance matching circuit which dynamically adjusts to changing environmental conditions.But the system designer has no control over the environmental conditions.

### Loads have highly variable I/V characteristics and energy requirements

A system has multiple sensors and voltage requirements are different. How to use energy harvesting to power multiple sensors is a challenge. It is necessary to decouple the source and load voltages, allowing each to operate at their respective optimal power point.

### Storage element must be minimized

Some scenes are more stringent, such as wearables. The battery should be suitable, and the large size battery is easy to waste energy.

maximize the energy input and minimize the energy output.To maximize the harvested energy in dynamic scenarios, the sources’ maximum power point needs to be tracked. To minimize the load’s energy, its power needs to be minimized by dynamically adjusting its operating voltage. 

***

## Contributions

The paper focus on specific design aspects of transient nodes which do long term
logging of rich data sensors. Rich data sensors such as cameras bring their own challenges to transient system design. Logging applications are particularly costly, due to the large volume of data that rich data sensors produce. The author thus propose a novel Non-Volatile Memory Hierarchy (NVMH), which increases the energy efficiency of rich data sensor logging applications. The author proposed EMU-based
design uses an optimally sized capacitor which minimizes the required start-up time
and energy from zero, while maintaining a low cost, small form factor, high efficiency and virtually unlimited charge cycles.

### The main contributions of this work are summarized as follows:

— Energy Management Unit (EMU) that efficiently converts variable low power levels to short, high power energy bursts.

— Feedback-based Dynamic Energy Burst Scaling (DEBS) technique to track the load’s optimal power point. The DEBS technique is based on a feedback loop (Fig. 1) that allows the load to configure the EMU to supply the energy burst at the optimal operating point.

— Non-Volatile Memory Hierarchy (NVMH) that reduces the energy cost of long-term data logging. NVMH = FRAM + SD，Firstly, store the data in FRAM. When the FRAM data is full, FRAM can write data to SD.

— Accurate model to optimize system’s application-specific parameters for low input power scenarios, including energy and data buffer sizes as well as harvester’s dimension.

— Experimental validation of the high energy efficiency and proportionality of the proposed transfer scheme in long-term image acquisition application, as well as the trade-off between energy cost per image stored and minimum buffer size.

***

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/EMU1.jpg)

***

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/EMU6.jpg)

***

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/EMU11.jpg)

***

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/EMU12.jpg)

***

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/EMU13.jpg)

***

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/EMU14.jpg)

***

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/EMU7.jpg)

***

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/EMU2.jpg)

***

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/EMU8.jpg)

***

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/EMU3.jpg)

***

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/EMU9.jpg)

***

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/EMU4.jpg)

***

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/EMU5.jpg)

***

To minimize the capacitance, it is important to understand how much energy is needed to flush the entire FRAM buffer to Flash. To simplify the discussion, we assume that once the FRAM buffer is full, the application schedule ensures the buffer is fully flushed before acquiring new pictures. Depending on the capacitor size, which limits the maximum burst size, flushing the entire buffer might take one or more bursts. The data-dependent energy cost to transfer a block of one or more images from the FRAM to the SD card is given by

***

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/EMU10.jpg)

***

### Paper

<p>Paper <a href="https://www.tik.ee.ethz.ch/file/d443eff28ed052659b30cc1d88fa11e5/GSSBT2017a.pdf">👉Paper Pages</a>




