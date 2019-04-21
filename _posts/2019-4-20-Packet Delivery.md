---
layout:     post
title:      Predictable 802.11 Packet Delivery from Wireless Channel Measurements
subtitle:   802.11 OFDM NICs
date:       2019-04-20
author:     Jackie
header-img: img/post-bg-github-cup.jpg
catalog: true
tags:
    - Packet Delivery
    - CSI
---

# Predictable 802.11 Packet Delivery from Wireless Channel Measurements

***

## Main content

Wireless LANs based on 802.11 are used almost everywhere. For good performance, the reliability and coverage of signal is important. The signal-to-noise ratio (SNR) is the gold standard for performance in narrowband channels. The most accessible channel measurement is received signal strength indication (RSSI), which serves as a proxy for the true SNR. However, RSSI has many problems in practice, and it does not fully reflect the performance of the signal. Another way to evaluate signal performance is to guide the search form. However, search becomes less effective as channels change more quickly and the configuration space becomes more complex. For rate selection, SoftRate and AccuRate can predict the effects on packet delivery of changing the rate. However, these methods are not defined for selecting other useful parameters. In response to the above situation, the author propose a practical 802.11 packet delivery model. Because 802.11n NICs measure the channel at the OFDM subcarrier level to support MIMO (multiple antenna) operation, we can acquire Channel State Information (CSI). The model takes as input 802.11n Channel State Information and predicts whether the link will deliver packets for a wide range of NIC configurations. The configuration includes selection of transmit and receive antennas, transmit power level, and transmit rate. Also, the author proposes a rate selection algorithm that is as good as the best 802.11a/g rate adaptation algorithms and extends this excellent performance to 802.11n. Finally, the author evaluates performance using two stationary wireless testbeds deployed in indoor office environments, T1 and T2. T1 consists of 10 nodes spread over 8 100 square feet. T2 is less dense by comparison with 11 nodes over 20 000 square feet. Experiments have shown that the narrow transition region is similar to a narrowband, near-ideal case with a flat frequency channel. The author's model can predict the highest rate, reduce transmission energy consumption, etc. Moreover, the authors show that the rate prediction is as good as the best rate adaptive algorithm of 802.11a/g by tracking drive simulation, and extends this good performance to 802.11n. The author's main contribution is to propose that the OFDM NIC on the actual link only uses the channel measurements provided by the NIC to predict signal performance. The author is the first to propose this method of evaluating signal performance. And the author is the first to propose an algorithm for 802.11n rate selection.

***

## Advantage

This article solves the current problems and adds another method to signal quality evaluation.

The authors mentioned the model to evaluate the signal factor than the current RSSI.

The author is the first to propose this evaluation model using CSI. Also, OFDM NICs on the actual link use only channel measurements to predict signal performance.


***

## Weakness

This paper is not very compact in the overall content.

The content of the experiment is not very rich, the author's consideration is not very thoughtful.

The author's model cannot predict the scene in which the signal has interference, but there are still many interference situations in practice.

***

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Predict1.jpg)

***

First, MIMO processing separates the signals of multiple spatial streams that have been mixed by the channel. As wireless channels are frequency-selective, this operation happens separately for each subcarrier. The demodulator converts each subcarrier’s symbols into the bits of each stream from constellations of several different modulations (BPSK, QPSK, QAM-16, QAM-64). This happens in much the same way as demodulating a narrowband channel. The bits are then deinterleaved to undo an encoding that spreads errors that are bursty in frequency across the data stream. A parallel to serial converter combines the bits into a single stream. Forward error correction at any of several rates (1/2, 2/3, 3/4, and 5/6) is then decoded. Finally, the descrambler exclusive-ORs the bitstream with a pseudorandom bitmask added at the transmitter to avoid data-dependent deterministic errors.

***

### Paper

<p>Paper <a href="http://djw.cs.washington.edu/papers/predictable wireless.pdf">👉Paper Pages</a>




