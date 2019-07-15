---
layout:     post
title:      Performance and Trade-offs of the new PHY Modes of BLE 5
subtitle:   Author:Michael Spörk，Carlo Alberto Boano and Kay Römer -- Graz University of Technology
date:       2019-07-11
author:     Jackie
header-img: img/Picture/4k-wallpaper-automobile-automotive-1149137.jpg
catalog: true
tags:
    - BLE 5
---

# Performance and Trade-offs of the new PHY Modes of BLE 5

***

## Abstract

With the release of Bluetooth Low Energy (BLE) version 5, the Bluetooth Special Interest Group introduced three additional physical (PHY) modes for BLE communication. These PHY modes enable an application to either double its throughput, or significantly improve its reliability, making BLE applicable to an even wider range of application domains. Unfortunately, no experimental study has yet investigated the actual performance of BLE 5’s PHY modes in BLE connections or shown their trade-offs between energy efficiency, reliability, and throughput. Thus, how to use BLE 5’s PHY modes to achieve specific application requirements is still an open question. To fill this gap, we experimentally study the performance of all four BLE 5 PHY modes in BLE connections and observe that it is, indeed, possible to double BLE’s throughput or to increase BLE’s reliability by using the new PHY modes. Furthermore, we provide guidelines using our measurements on how to select the most suitable PHY mode based on specific application requirements.

***

## Main content

Although BLE 5 devices have been available since 2017 [9] and even BLE version 5.1 (enabling a more advanced localization using multiple antennas) has been released in 2019, no experimental study has, to the best of our knowledge, investigated if the new PHY modes of BLE 5 actually perform as advertised when used in BLE connections. Furthermore, how to use the different PHY modes to sustain specific application requirements, such as a certain power consumption, communication reliability, or throughput, has not been studied in detail and still remains an open question.

### Contributions
In this paper, The author fill this gap and experimentally study the performance of BLE 5 and its new PHY modes. Their investigation allows to understand: 

1. whether the BLE 5 PHYs deliver on their promises.

2. how to select the best PHY for a given application. 

To this end, They perform the first comprehensive experimental study of all four BLE 5 PHY modes used in a BLE connection and answer the following questions:

• Does the 2M PHY really allow to double the throughput?

• Do the Coded S2 PHY and the Coded S8 PHY really increase
the relibility of a BLE connection?

• How does the chosen PHY mode affect the overall power
consumption of a BLE device?

Based on these measurements, The paper show the trade-off between energy efficiency, reliability, and throughput for each PHY mode and provide guidelines on how to select the most suitable PHY for a given application. For this purpose, we derive the effective throughput and effective power consumption of all four PHY modes for BLE connections with different link quality and investigate:

• Which PHY provides the maximum effective throughput?

• Which PHY minimizes the effective power consumption?

With the publication of the BLE 5 specification in June 2016, three additional physical (PHY) modes, the 2M, the Coded S2, and the Coded S8 PHY mode, were introduced. While the 2M PHY, where the M stands for Megasymbols/s (Msym/s), promises twice the data rate compared to the existing 1M PHY mode, the two Coded PHY modes are meant to increase the communication reliability of BLE devices.

#### 1M PHY.

In this mode, the modulation scheme supports a physical modulation of 1 Msym/s, meaning that transmitting a single bit of payload takes 1 μs. All packet data is not coded and, therefore, has no error correction.

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Performance and Trade-offs of the new PHY Modes of BLE 5/BLE1.jpg)

***

Fig. 1a shows the link-layer packet format of the 1M PHY mode. The preamble is 1-byte long and is followed by 4 bytes containing the access address. After the Protocol Data Unit (PDU), which has a variable length between 2 and 257 bytes, the packet ends with a 3-byte CRC checksum, which is used to check for packet corruption.

#### 2M PHY.

This mode uses a physical modulation of 2 Msym/s, resulting in 0.5 μs of air time for a single payload bit.
Similar to the 1M PHY, data sent with the 2M PHY is not coded and has no error correction. The 2M PHY link-layer packet format is similar to the format of the 1M PHY shown in Fig. 1a, however a 2 byte preamble is used. Hence, the new 2M PHY promises twice the throughput at the cost of a lower reliability for poor link qualities.

#### Coded S2 PHY.

This mode uses a physical modulation of 1 Msym/s, but makes use of forward error correction (FEC) with a symbol coding of 2 (S2), leading to an increased robustness. A single data bit encoded with S2 coding takes 2 μs on the air, resulting in a data rate of 500 kb/s.

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Performance and Trade-offs of the new PHY Modes of BLE 5/BLE1.jpg)

***

The link layer packet format of this mode is shown in Fig. 1b. As this figure shows, the packet is split into three parts: a preamble, a FEC block 1, and a FEC block 2. The preamble is 80 μs long and is sent without coding. The FEC block 1 contains the access address as well as the coding indicator (CI) and ends with the first termination field (TERM1). The FEC block 2 contains the PDU and a 3-byte CRC checksum and is terminated by a second termination field (TERM2). According to the BLE specification [4], even when a packet is sent with the Coded S2 PHY, the FEC block 1 always uses S8 Coding. Compared to the 1M PHY, this PHY improves BLE’s reliability, at the cost of less throughput and an increased power consumption.

#### Coded S8 PHY.

The Coded S8 PHY uses an even more robust coding and error correction scheme than the Coded S2 PHY. This
PHY also transmits with a physical modulation of 1 Msym/s, but uses an FEC with a symbol coding of 8 (S8) for the whole packet. Using the Coded S8 PHY, a single data bit takes 8 μs on the air. Fig. 1b shows the link-layer packet format of the Coded S8 PHY mode. Using the Coded S8 PHY, all packet fields are sent with a coding of 8, resulting in a data rate of 125 kb/s for the whole packet. The Coded S8 PHY promises to improve BLE’s reliability for poor link qualities even further, at the cost of a lower throughput and increased power consumption compared to the other PHYs.

BLE supports two modes of communication: a connection-less and a connection-based mode.  In connection-less mode, if two devices need to bidirectionally exchange data packets, they need to use connection-less primitives to establish a BLE connection. Every connection event starts with a link-layer packet from the master, to which the slave responds. In case master and slave have no additional data to send, the connection event ends after this mandatory exchange of keep-alive messages.If, however, more data needs to be transmitted, master and slave keep exchanging link-layer packets until all data is successfully sent or the maximum connection event length (tCE ) is reached. The last link-layer packet during a connection event is always sent by the slave, after which both devices disable their radio and resume communication at the next connection event.

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Performance and Trade-offs of the new PHY Modes of BLE 5/BLE2.jpg)

***

Fig. 2 shows an example where, after the connection setup using connection-less primitives, the master starts connection event N0 by sending a short keep-alive packet to the slave. The slave has data to send and therefore responds with a link-layer packet (which is longer than the keep-alive packet from the master) carrying the
data. During connection event N1, both devices have no data to transmit and therefore only exchange the mandatory keep-alive packets. In connection event N2, however, the master has data to send and therefore starts the connection event by sending a linklayer packet carrying data. Because the master has additional data to send, it waits for the slave’s response before sending a second link-layer packet containing the rest of the data. The slave responds with a second link-layer packet, ending the connection event.

In the connection-based BLE mode, the link layer autonomously handles packet acknowledgment (ACK) and flow control using a 1-bit ACK field and a 1-bit sequence number in every link-layer packet header. If a link-layer packet was not successfully sent, it is automatically retransmitted. To further ensure reliable communication,
BLE connections use adaptive frequency hopping (AFH). Using AFH, one of the enabled data channels in the data channel map is selected at the start of every connection event and is used by master and slave to exchange all packets during the event.

#### Power Consumption

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Performance and Trade-offs of the new PHY Modes of BLE 5/BLE3.jpg)

***

First, we can clearly observe that PAVG (average power consumption) increases when using a lower connection
interval, as the BLE radio is more active. Second, we can see a significant difference in power consumption when different PHY modes are used. As expected, the 2M PHY mode results in the lowest PAVG, as it has the lowest radio duty cycle due to its fast data rate. The Coded S8 PHY, however, leads to the highest power consumption, because of its higher radio duty cycle caused by the overhead of the employed coding scheme.
Compared to the legacy 1M PHY, the 2M PHY consumes approximately 8% less power in our experiments. The Coded S2 and S8 PHY consume approximately 61% and 70% more power compared to the 1M PHY for all four connection intervals, respectively.

#### Throughput

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Performance and Trade-offs of the new PHY Modes of BLE 5/BLE5.jpg)

***

Fig. 5 shows the TLL for different PHY modes and connection intervals measured at the master. As expected, the 2M PHY, having a physical modulation of 2 Msym/s, provides the highest throughput of all PHYs, while the Coded S8 PHY has the lowest TLL in our experiments.

#### Packet Reception Rate

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Performance and Trade-offs of the new PHY Modes of BLE 5/BLE6.jpg)

***

Fig. 6 shows the PRR of the four PHY modes of BLE 5 for different attenuation values. As expected, the 2M PHY mode has the lowest PRR out of the four available PHY modes. The Coded S2 PHY and the Coded S8 PHY increase the link-layer PRR of BLE connections for poor link qualities, and therefore BLE’s reliability, due to their employed coding schemes.

#### Robustness to Interference

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/Performance and Trade-offs of the new PHY Modes of BLE 5/BLE7.jpg)

***

Fig. 7 shows the average PRR of the BLE connection for different PHY modes and Wi-Fi transmission power settings. The Coded S8 PHY mode provides the highest PRR and thus the highest reliability under interference. The data also show that the Coded S2 and S8 PHY increase the link budget by 5dBm under Wi-Fi interference.

##### Which PHY mode of BLE 5 provides the maximum effective data throughput?

In case only a few link-layer data packets are corrupted and thus need to be retransmitted, the 2M PHY mode
provides the highest TEFF(the effective link-layer throughput). If packets are frequently corrupted,
because of a poor link quality of the underlying BLE connection, the Coded S8 PHY is able to recover most corrupted packets and hence achieves the highest effective throughput.

##### Which PHY mode of BLE 5 minimizes the effective power consumption?

The most energy efficient PHY mode mainly depends on the link quality of the BLE connection. In case only a few link-layer packets are corrupted and therefore retransmitted, due to a good link quality, the 2M PHY mode provides the most energy-efficient communication. When packets are frequently corrupted, the Coded S8 PHY leads to a lower power consumption, as most corrupted packets can be recovered and do not need to be retransmitted. 

### Paper

<p>Paper <a href="http://39.137.36.61:6310/www.carloalbertoboano.com/documents/spoerk19ble5phy.pdf">👉Paper Pages</a>







