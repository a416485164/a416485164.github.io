---
layout:     post
title:      Monitoring a Person’s Heart Rate and Respiratory Rate on a Shared Bed Using Geophones
subtitle:   Geophones
date:       2019-04-15
author:     Jackie
header-img: img/post-bg-miui-ux.jpg
catalog: true
tags:
    - Geophones
---

# Monitoring a Person’s Heart Rate and Respiratory Rate on a Shared Bed Using Geophones

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Geophones1.jpg)

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Geophones2.jpg)

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Geophones3.jpg)

The main contribution of this article is to measure a person's respiratory rate as well as heart rate through a geophone，even when she is
sharing a bed with another person.

In such situations, the vibrations from both persons are mixed together. VitalMon first separates the two heartbeat signals, and then distinguishes the respiration signal from the heartbeat signal for each person.

The author's heartbeat separation algorithm relies on the spatial difference between two signal sources with respect to each vibration sensor, and our respiration extraction algorithm deciphers the breathing rate embedded in amplitude fluctuation of the heartbeat signal.

 A total of 86 subjects participated in author's study, and we collected 5084 geophone samples, totaling 56 hours of data. it shows that the technique is accurate – its breathing rate estimation error for a single person is 0.38 breaths per minute (median error is 0.22 breaths per minute), heart rate estimation error when two persons share a bed is 1.90 beats per minute (median error is 0.72 beats per minute), and breathing rate estimation error when two persons share a bed is 2.62 breaths per minute (median error is 1.95 breaths per minute). 
