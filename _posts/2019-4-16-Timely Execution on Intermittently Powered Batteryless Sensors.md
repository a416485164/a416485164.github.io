---
layout:     post
title:      Timely Execution on Intermittently Powered Batteryless Sensors
subtitle:   Mayfly
date:       2019-04-16
author:     Jackie
header-img: img/post-bg-ioses.jpg
catalog: true
tags:
    - Batteryless
    - Timely Execution
    - Mayfly
---

# Timely Execution on Intermittently Powered Batteryless Sensors

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Mayfly1.jpg)


![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Mayfly2.jpg)


![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Mayfly3.jpg)


![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Mayfly4.jpg)

## Background
Battery-free energy harvesting sensors Irregular power supply and low energy storage result in frequent power failures, and reliable operation in frequent failure situations is a challenge.Because power down is unpredictable, we can use Flash or FRAM to solve this problem.  However, each of these methods ignores the fact that an application’s success or failure often depends on when tasks are executed and when data are collected, processed, and communicated. Application designers often understand these constraints (albeit imperfectly), but lack effective tools for communicating them in code.Also, Timekeeping is Complex. Real data often ages: When the sensor collects the data and is about to process it, this time the power is turned off. When the power is available, the data may be old, so we need to add the time value to the program, but this increases the power consumption and is complicated.In batteryless sensors, it is difficult to meet stringent timing requirements because the sensors are present in an unpredictable energy environment.When devices operate intermittently, programmers must add code to track when data are generated, when data have expired, and when it is advantageous to gather more data.Current languages ignore the timeliness property of data caused by intermittent execution,
leaving the developer with few ways to strongly and safely express time constraints of data.

## Contributions
The Mayfly language is a declarative, graph based programming language that enables developers to focus on application policy, sensing goals, and timing of sensing tasks while reducing the cognitive burden of intermittent programming.Mayfly is a coordination language and runtime built on top of Embedded-C that combines intermittent execution fragments to form coherent sensing schedules—maintaining forward progress, data consistency, data freshness, and data utility across multiple power failures. Mayfly makes the passing of time explicit, binding data to the time it was gathered, and keeping track of data and time through power failures.

 <p>论文信息 <a href="http://www.cs.virginia.edu/~bjc8c/class/cs6501-f18/papers/hester17mayfly.pdf">👉Paper Pages</a>




