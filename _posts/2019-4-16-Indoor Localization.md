---
layout:     post
title:      Indoor Localization with Aircraft Signals
subtitle:   Indoor Localization
date:       2019-04-16
author:     Jackie
header-img: img/post-bg-debug.png
catalog: true
tags:
    - Indoor Localization
    - Aircraft Signals
    - ADS-B
---

# Indoor Localization with Aircraft Signals

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Aircraf1.jpg)
***
The main contribution of this article is to use the aircraft's signals for indoor positioning.The prototype implementation achieves a user localization accuracy of approximately 25 meters. 
***
The localization system consists of: 

• a network of receivers with known positions, which we call ground stations;

• a receiver whose position should be determined – we refer to this receiver as the handset;

• a server, which connects the ground stations and the handset.

As aircraft messages do not include a time stamp, we also solve a time synchronization problem using a small number of ground stations with known positions.
***
![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Aircraf3.jpg)

Figure 1 shows the concept of our system. The ground stations and the handset send the recorded ADS-B messages with the corresponding time stamps to a server. The server collects the messages and matches the messages from the handset to those from the ground stations and computes send times of the messages and the position of the handset by solving least squares problems using the relative timing of these messages and their transmit position.The localization method can be partitioned into two steps:

• Calculation of message send times and aircraft positions (if not given in messages): Matching messages received at multiple receivers are used to calculate the clock offset and drift of the receivers, the message send times and optionally the aircraft positions.

• User localization: Multilateration using messages with now known send times.
***

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Aircraf6.jpg)
***
![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Aircraf4.jpg)
***
![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Aircraf5.jpg)
***
![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Aircraf2.jpg)
***
Plenty of accuracy improvements to our prototype system are possible:

• Using more advanced signal processing to more precisely detect signal arrival times and detect more signals per time.

• Improvements to the RF chain, such as employing antennas designed for ADS-B.

• Applying enhancements to the position estimation, such as selecting only “good” measurements for the least squares computation, computing a weighted least-squares solution, applying multipath mitigation techniques or using a different localization algorithm such as a maximum likelihood approach.

• Precisely localizing ground station positions.

• Choosing an optimal placement of the ground stations, to reduce error sources such as multipath and to maximize received signal strength, number of received messages and observed unique aircraft.
***
### Paper

<p>Paper <a href="https://www.tik.ee.ethz.ch/file/cde383a03b70cfc765a1e12f70e1c066/Indoor%20Localization%20with%20Aircraft%20Signals.pdf">👉Paper Pages</a>

<p>Aircraft <a href="https://www.flightradar24.com/49.83,29.29/8">👉Aircraft Pages</a>.




