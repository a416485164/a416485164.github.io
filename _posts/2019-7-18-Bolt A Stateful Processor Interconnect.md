---
layout:     post
title:      Bolt:A Stateful Processor Interconnect
subtitle:   Author:Felix Sutton, Marco Zimmerling, Reto Da Forno, Roman Lim, Tonio Gsell, Georgia Giannopoulou, Federico Ferrari, Jan Beutel, and Lothar Thiele -- ETH Zurich, Switzerland
date:       2019-07-18
author:     Jackie
header-img: img/apple-coffee-desk.jpg
catalog: true
tags:
    - BOLT
---

# Bolt:A Stateful Processor Interconnect

***

## Abstract

The wireless sensor network community is currently under-going a platform paradigm shift, moving away from classical single-processor motes toward heterogeneous multi-processor architectures. These emerging platforms  promise efficient concurrent processing with energy-proportional system performance. The use of shared interconnects and shared memory for inter-processor communication, however, causes interference in the time, power, and clock domains, which pre- vents designers from fully harnessing these benefits. We thus designed  Bolt, the first ultra-low-power processor interconnect for the compositional construction of heterogeneous wireless embedded platforms. This paper presents the architectural blueprint for interconnecting two independent processors, while enabling asynchronous inter-processor communication with predictable run-time behavior. We detail a prototype implementation of Bolt, and apply formal methods to analytically derive bounds on the execution time of its message passing operations. Experiments with a custombuilt dual-processor 
platform show that our Bolt prototype incurs a negligible power overhead relative to state-of-the-art platforms, offers predictable message passing with empirical bounds that match the analytical ones to within a few clock cycles, and achieves a high throughput of up to 3.3 Mbps.

***

## Main content

Low-power operation was achieved by interleaving sensing, data processing, and communication tasks and by 
judiciously managing the power state of hardware components. The  engineering  effort in realizing such systems is labor-intensive with respect to the design, test, and diagnosis of hardware and software components. While difficult to quantify, so these practical complexities lead to implementations that are often unreliable, not readily adaptable to changing requirements, exhibit long development cycles, and are over-dimensioned to satisfy performance targets. Why is it difficult to design such systems? The main problem is rooted in the interference of hardware and software components in the time, power, and clock domains. Reading sensors, processing data and transmitting packets is executed concurrently. These concurrent tasks interfere when they compete for shared resources such as clock cycles, memory, and peripherals. Although some measures may be effective in a short period of time, it will have a very bad impact on the system for a long time and will also affect the operation. This paper presents Bolt, the first processor interconnect that enables the composable construction of ultra-low-power wireless embedded systems.Bolt provides predictable asynchronous communication between two arbitrary processors, and thus decouples the processors in the time, power, and clock domains. Two message queues, one for each direction, with first-in-first-out (FIFO) semantics form the core of this stateful interconnect. One queue is for messages written into Bolt by A and read out by C, while the other queue is for
messages written by C and read by A. A signaling protocol allows for concurrent message reads and writes on both queues, and indicates when there is at least one message ready to be read out from a queue and when a queue is empty.

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/BOLT/BOLT1.jpg)

***

As depicted in Fig. 1, Bolt is a piece of integrated hardware and software that sits between two processors A and C. Bolt lets A and C asynchronously exchange messages while executing within their own time, power, and clock domains. Bolt adopts asynchronous message passing to avoid interference between processors A and C wherever possible. 

Operating the control channel means coordinating data channel access for message transfers and indicating the availability of messages to the target processor. The actual message transfer between a processor and Bolt occurs over a bidirectional data bus that supports master/slave operation. Each interconnected processor is the master of its dedicated data channel; that is, it provides the clock required to transfer each bit over the bus, while Bolt is always the slave.

In the time domain, however, A and C may interfere. Since message transfers are asynchronous, it is possible that A and C simultaneously request a message operation on the same queue: one processor wants to read a message, while the other processor wants to write a message.

The author intend to tightly bound the execution time of read and write operations despite this kind of resource interference.

### BOLT IMPLEMENTATION

#### Hardware Architecture

The author implement a Bolt prototype using the 16-bit TI MSP430FR5969 MCU running at an 8MHz clock frequency.
The core, the FRAM, and all peripherals are attached to a shared 16-bit data bus and a 20-bit address bus. The instruction processing of the core may be interrupted by either the generalpurpose input/output (GPIO) module or the direct memory access (DMA) controller using auto-vectored interrupt processing.

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/BOLT/BOLT2.jpg)

***

The GPIO module has two ports, namely PORT3 and PORT4. PORT3 has a higher priority than PORT4. The MCU provides two independent SPI hardware modules, namely SPI A and SPI C. The byte-wise transfer be- tween the SPI receive buffer and the FRAM is coordinated by dedicated DMA channels, that is, DMA0 for SPI A and DMA1 for SPI C. The DMA controller manages the bus arbi- tration and interrupt priority, with DMA0 having a higher priority  than  DMA1. Allow the CPU to run the current cycle before the DMA starts. The byte transfer between SPI and FRAM takes precisely two clock cycles.A dedicated GPIO port is used to implement the control channel toward each interconnected processor. PORT3 is assigned to processor A, while PORT4 is assigned to processor C.

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/BOLT/BOLT3.jpg)

***

The control channel consists of the four lines R/W, REQ, ACK, and IND. The R/W line defines the requested operation as either a message read or a mes- sage write.  The REQ line is used by the interconnected pro- cessor to request the specified message operation, while the ACK  line is used by Bolt to grant a message 
transfer over the corresponding data channel. The two REQ  lines are configured as interrupt wakeup sources.
The MCU is put into deep sleep (LPM4), while all other hardware blocks are turned off. The MCU remains in deep sleep until a read or write operation is initiated. 

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/BOLT/BOLT4.jpg)

***

When either processor initiates a read or write operation by setting the R/W line and raising the REQ line, the associated IRQ wakes the MCU from deep sleep. Once the core is awake, the GPIO ISR will first determine the requested mode of operation and configure the corresponding SPI module and DMA channel for message transfer 
before updating  the ACK line accordingly. The MCU will then enter a low-power mode (LPM0) with the core turned off, while the DMA and SPI modules remain active.

The completion of a message transfer is also processed by an ISR. However, depending on the message operation, either the GPIO or DMA ISR will be invoked. If the operation is a write, the falling edge of the REQ line signals the end of the message, thereby invoking the GPIO ISR. If the operation is a read, the DMA controller will trigger an interrupt toward the core. The ISR will update the internal data structures, update the ACK  and IND lines, and disable the associated SPI and DMA peripherals. If there is an on-going message transfer involving the alternate processor, the MCU will return to the LPM0 sleep mode; otherwise it will return to the LPM4 deep sleep mode.

If interference is unavoidable, try to tightly bound it. An approach, and one that has been well-studied in the embedded systems community, is to use formal methods such as model checking. Through the construction of an accurate model of the system, one can apply rigorous mathematical tools to analytically derive safe bounds on interfering resources. The challenge in constructing a model of our Bolt prototype is capturing the complexity of several time-dependent and interacting state machines each of which has their own independent clock domain.
As a solution to this challenge we propose to model all interactions as timed automata and to extend each automaton with an independent clock variable.

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/BOLT/BOLT10.jpg)

***

Fig. 10 shows a custom-built heterogeneous dual-processor platform, where Bolt interconnects two state-of-the-art processors with different computing capabilities and power dissipation: a 32-bit STM ARM Cortex-M4 STM32F303VCT6 running at 72 MHz and a 16-bit TI CC430F5137 SoC running at 20 MHz.

When Bolt does not perform reads or writes, its power dissipation of 1.3 µW is less than state-of-the-art low-dropout voltage regulators. Bolt’s active power dissipation of 1.1 mW is comparable to the sleep  mode  power dissipation of the Cortex-M4.

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/BOLT/BOLT_EX.png)

***

### Paper

<p>Paper <a href="https://www.researchgate.net/publication/301464248_Bolt_A_Stateful_Processor_Interconnect">👉Paper Pages</a></p>

<p>Video <a href="https://www.youtube.com/watch?v=FdvdMuP5-NU">👉Video</a></p>

<p>Github <a href="https://github.com/ETHZ-TEC/BOLT">👉Github</a></p>

<p>ETH <a href="https://tec.ee.ethz.ch/research/networked-embedded-systems/bolt.html">👉ETH</a></p>










