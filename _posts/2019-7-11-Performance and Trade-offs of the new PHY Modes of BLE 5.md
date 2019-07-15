---
layout:     post
title:      Exploiting Multi-Cell Battery for Mobile Devices:Design, Management, and Performance
subtitle:   Author:Sungwoo Baek, Minyoung Go, Seokjun Lee and Hojung Cha -- Yonsei University
date:       2019-07-15
author:     Jackie
header-img: img/post-bg-miui6.jpg
catalog: true
tags:
    - Multi-Cell Battery
---

# Exploiting Multi-Cell Battery for Mobile Devices:Design, Management, and Performance

***

## Abstract

Extending battery lifetime is an important issue for mobile devices. While extensive attempts have been made at the software level, optimization often risks hampering user experience. One fundamental method to increase battery lifetime is to improve the efficiency of the battery itself. We argue that the multi-cell battery system, which is widely used for enhancing battery efficiency in the electric vehicle (EV) field, can solve this issue. However, due to the hardware constraints and device usage characteristics, battery advancements in the EV field are not directly applicable to mobile devices. In this paper, we propose BattMan, a multi-cell battery management system for mobile devices, for the enhancement of battery efficiency. We develop an accurate battery cell model to estimate the expected battery lifetime considering the recovery effect, the rate capacity effect, and battery aging. We also propose a multicell scheduling algorithm to maximize the overall battery lifetime. We implemented BattMan on recent smartphones and evaluated its impact on battery lifetime. The experimental results show that a two-cell configuration of the proposed system increases battery lifetime by an average of between 14-19%, depending on cell aging, in real usage scenarios over a single-cell battery of the same overall cpacity.We hope the proposed multi-cell battery scheme opens up a new direction towards battery lifetime improvement in mobile devices.

***

## Main content

As the functionality of mobile applications grows more versatile and complex, the demand for high performance mobile devices rapidly increases. Diverse approaches have attempted to prolong battery lifetime, such as software optimization, constraining hardware performance, and device idle time management. Softwarebased
methods often result in performance issues along with user experience tradeoffs.There are several methods for improving batteries that result in enhanced device lifetime. First, battery capacity can be augmented by increasing the battery size or utilizing new materials in battery production. However, this is unlikely to happen in imminent future, because battery size tends to be smaller and thinner for design purposes, and developing new battery materials is challenging indeed.Another solution is to improve battery efficiency.For
example, multi-cell batteries could be exploited even for mobile devices. In fact, a multi-cell battery system that consists of several small battery cells instead of a single large one is commonly employed in the EV field. To maximize the lifetime of a multi-cell battery system, the use policy for each constituent cell should be accurately determined at runtime, because the recovery effect and rate capacity effect exhibit different characteristics depending on the discharging current and the number of cells employed in the system. Moreover, the use policy should reflect the degree of cell aging or degradation, often called the State of Health (SoH) of the cell, because the degraded battery cell significantly affects both the recovery effect and the rate capacity effect. This brings us a big challenge, i.e., battery cell modeling. In order for the multi-cell battery system to work in mobile devices, the battery itself should be modeled to predict the battery lifetime accurately considering the battery characteristics mentioned above. The second challenge lies in the development of cell discharge scheduling for multi-cell battery systems, which would increase overall lifetime by maximizing both the rate capacity and recovery effects. To this end, a sophisticated algorithm should be developed to optimize cell usage. In this paper, the author propose BattMan, a prototype of a multi-cell battery system specifically designed for mobile devices, to address these issues. They first developed a battery cell model to estimate its lifetime accurately, considering various factors such as discharging current, SoH, the rate capacity effect, and the recovery effect. They then developed a multi-cell scheduling
scheme called the weighted SoC-based round robin (WSRR) to select the best use policy which maximizes the efficiency of the rate capacity effect and the recovery effect. A multi-cell battery system utilizes multiple cells instead of a single, large cell for its power source. As described above, two main phenomena of the battery—rate capacity effect and recovery effect— are exploited in the multi-cell configuration.

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Multi-cell battery/Multi-cell battery1.jpg)

***

Figure 2 shows the potentials of a multi-cell system over that of a single-cell battery.

Figure 2(a) illustrates the concept of the rate capacity effect, that is, the available capacity of a battery cell changes subject to power consumption: the smaller the power consumption, the larger the available capacity. 

Figure 2(b) illustrates the effective use of the recovery effect. 

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Multi-cell battery/Multi-cell battery2.jpg)

***

Figure 3(a) shows that battery lifetime increased approximately 10% over sequential use when the three
batteries were switched every 30 seconds.

Figure 3(b) shows the voltage traces of a single battery exhibiting the capacity fade on different C-rates.

The experiment shows that the rate capacity effect indeed exists in real device since there is additional
capacity loss with a high discharge current.

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Multi-cell battery/Multi-cell battery5.jpg)

***

The results in Figure 4 show that the efficiency of both effects increases with the degree of aging (i.e.,
toward low SoH).

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Multi-cell battery/Multi-cell battery6.jpg)

***

Figure 5 shows that the best use policy which shows the maximum lifetime gain changes with discharging current.

With low discharging current, utilizing recovery effect is more efficient while rate capacity effect is dominant under high discharging current.

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Multi-cell battery/Multi-cell battery3.jpg)

***

Figure 6 shows the overall architecture of BattMan. The BattMan hardware monitors the device’s discharge
current, and also the status of each cell such as voltage, SoC, and SoH.

As the number of charging/discharging cycle increases, a battery’s internal resistance becomes larger. 
The increased voltage during recovery is caused by the capacitances in RC networks. In other words, The author consider that the electric charge is stored in capacitance during discharging and it is returned to battery in recovery phase, increasing cells voltage.

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Multi-cell battery/Multi-cell battery4.jpg)

***

### Contribution :
1. They provide an accurate battery cell model to estimate the battery lifetime considering the rate capacity effect, the recovery effect, and the SoH factor. Also, a runtime algorithm for optimizing the multi-cell use policy is proposed to maximize battery lifetime.

2. The proposed scheme is implemented in real mobile devices and delivers battery lifetime extension. Various experiments conducted in real application scenarios validate the effectiveness of the proposed scheme in terms of battery lifetime improvement.

***

### Paper

<p>Paper <a href="https://mobed.yonsei.ac.kr/mobed_pages/pdf/index.php?name=Battman">👉Paper Pages</a>






