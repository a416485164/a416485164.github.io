---
layout:     post
title:      Interference Alignment and Cancellation
subtitle:   Author:Shyamnath Gollakota, Samuel David Perli and Dina Katabi -- MIT CSAIL
date:       2019-05-06
author:     Jackie
header-img: img/post-bg-alibaba.jpg
catalog: true
tags:
    - MIMO
    - IAC
---

# Interference Alignment and Cancellation

***

## Main content

MIMO can make full use of space resources, achieve multiple transmission and multi-receiver through multiple antennas, can double the system channel capacity, show obvious advantages, and be regarded as the core technology of next-generation mobile communication. However, when the number of packets sent is greater than the number of antennas, the receiver cannot decode the packet. There have been many papers on this issue, but the previous methods have some shortcomings. In this paper, the authors propose interference alignment and cancellation (IAC) for the concurrent sender-receiver pairs in MIMO networks. It applies to scenarios where interference cancellation alone does not apply. IAC mainly includes a physical layer, a MAC protocol and an effective mechanism. Regarding the physical layer, the author's method is as follows. First, the vector of the received packet is controlled, and a received packet is projected onto a vector perpendicular to the alignment interference. Since the two vectors are already aligned, there is a vector orthogonal to them, so the AP can decode. Then the decoded data is shared with other Aps and uses interference cancellation to subtract the decoded packet, so that the entire received packet is decoded. In order to satisfy the simultaneous transmission of multiple clients and APs, the author modified the MAC and used the concurrency algorithm. The author proposes that the MAC can access multiple media at the same time by adjusting the running mechanism during contention-free and contention. The concurrency algorithm considers how to combine clients and decide which clients upload/download at the same time when multiple clients are running. The estimated channel is a standard MIMO technique. By measuring, the author uses APs to estimate the channel using the reciprocal relationship between the uplink and downlink channels. The experiment uses 20 USRP nodes, each with two antennas. Experimental results show that IAC improves the average throughput of MIMO LAN by 1.52x on the downlink and 2.08x on the uplink.

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/IAC1.jpg)

***

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/IAC3.jpg)

***

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/IAC4.jpg)
![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/IAC5.jpg)

***

When the number of received packets is greater than the number of antennas of the receiver, there are two equations, three unknowns, which is impossible to solve.

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/IAC6.jpg)

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/IAC7.jpg)

***

If the transmitter multiplies the packet p1 by a different vector, e.g.,v, the AP will receive the vector Hvp1. by changing Vi, we can control the vector along which the AP receives the packet.

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/IAC9.jpg)

H11v2 = H21v3

Since these two vectors are already aligned, there is a vector that is orthogonal to both of them, and thus the AP can decode. 

Note that without alignment, AP1 could not decode because H11v2 and H21v3 would have different directions,
and no vector will be orthogonal to both.


***

Let us try to increase the number of concurrent packets on the uplink to 4. We cannot do this with only 2 clients and 2 APs. We need to add an additional AP-client pair. 

The first client transmits packets p1 and p2, the second client transmits p3 and the third client
transmits the fourth packet, p4.  p1, which can be decoded with orthogonal projection. From the
perspective of AP2, p1 is already decoded at AP1, and hence can be subtracted and removed from the signal. Thus, AP2 is left with three unknown packets. To decode one more packet, it needs to have 2 out of 3 packets aligned From the perspective of AP3, two packets are already decoded at AP1 and AP2, and their signal can
be canceled using interference cancellation. Thus, AP3 is left with only two unknown packets, which it can decode. Hence, AP3 does not need to align any packets. 

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/IAC8.jpg)

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/IAC10.jpg)

***

## Advantage

1. The author is the first person to intervene the interference calibration from concept to implementation.
2. The author first proposed a new interference management technology that combines interference alignment and interference cancellation.
3. The author solves the limitation that the number of packets is larger than the number of antennas and can not be decoded, which improves the throughput of data.
4. The method proposed by the author provides a solution to the current problems and broadens the thinking for others.

***

## Weakness

1. The method proposed by the author is only suitable for scenes with interference calibration and interference cancellation.
2. The method proposed by the author is a bit complicated to implement, and it needs to decode a packet first and then share it with other nodes to decode other packets.
3. Ethernet is required to connect between APs, and hardware is added, so the scope of use is limited.
4. The method proposed by the author is limited, and the use of the scene is limited, that is, the node can not be too much, if too many nodes, it will bring a huge amount of computation and complexity.

***

### Paper

<p>Paper <a href="https://homes.cs.washington.edu/~gshyam/Papers/IAC.pdf">👉Paper Pages</a>




