---
layout:     post
title:      Moving Beyond Competitions:Extending D-Cube to Seamlessly Benchmark Low-Power Wireless Systems
subtitle:   D_Cube
date:       2019-04-12
author:     Jackie
header-img: img/post-bg-re-vs-ng2.jpg
catalog: true
tags:
    - Benchmarking
    - D_Cube
---
# Moving Beyond Competitions: Extending D-Cube to Seamlessly Benchmark Low-Power Wireless Systems

## Background

1，缺少标准化的基准来评估性能

2，D-Cube的扩展

3，the traffic patterns and node identities被开发者写入，不能自动更改

面对第三个问题，作者的解决方法是利用已知的数据结构，并让开发者使用传递到基准测试基础设施的配置文件描述其内存地址

低功耗无线基准测试理想情况下包括一个实验装置，支持在实际硬件上自动，无缝和可重复执行实验，允许用户定义系统行为参数，网络密度等系统参数，持续时间等实验参数，环境参数，定义测试性能指标。

***

## Advantage

1,短时间对系统无法优化，所以支持远程实验

2,支持多traffic patterns和按需要禁用节点、多个GPIO输入事件能力

3,支持多个参数设定，

4,根据参数组合，自动实例化运行

### D-Cube已实现的功能

1，EWSN18的参数特性需求

2，大多数输入参数可以不需要开发者交互更改

3，可以向D-Cube提供流量负载，作为要生成事件数量的描述

4，可以添加干扰

5，添加实验参数

6，控制网络节点密度

7，处理输入参数，提供的固件和性能指标的描述，自动执行，生成报告

***

## Weakness

1,流量模式和节点标识由开发者写入，不能自动更改

解决方法：扩展D-cube，使用C文件提供一个结构，通过hex指定结构的内存位置，基准测试设施，使用二进制补丁框架自动更改所有配置变量的值：使用Python分三步执行

2,实验数据不够丰富，论据不能很好支持论点，作者目的是优化D-Cube,解决流量模式和节点标识由开发者写入，不能自动更改问题，然后作者花了很大篇幅在讲比赛的事情.

***

### Paper

<p>Paper <a href="http://www.carloalbertoboano.com/documents/schuss18benchmark.pdf">👉Paper Pages</a>

<p>PPT <a href="https://cpsbench2018.ethz.ch/wp-content/uploads/2018/04/DCube.pdf">👉PPT Pages</a>
