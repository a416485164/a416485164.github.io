---
layout:     post
title:      DeepASL:Enabling Ubiquitous and Non-Intrusive Word and Sentence-Level Sign Language Translation
subtitle:   DeepASL
date:       2019-04-15
author:     Jackie
header-img: img/home-bg-o.jpg
catalog: true
tags:
    - DeepASL
---

# DeepASL:Enabling Ubiquitous and Non-Intrusive Word and Sentence-Level Sign Language Translation

![](https://raw.githubusercontent.com/a416485164/a416485164.github.io/master/img/DeepASL.jpg)

Help deaf-mute people to talk to normal people. The scene is that deaf-mute people talk to normal people. When normal people speak, deaf-mute people use smart glasses to recognize and display text on glasses. When deaf-mute people want to express their ideas, they can use gestures, then sensors on the neck to recognize gestures and translate them into speech to normal people.

The main contribution of this paper is to first recognize the gesture and then convert it into speech through deep learning, which can be a single word or even a sentence.

DeepASL uses Leap Motion – an infrared light-based sensing device that can extract the skeleton joints information of fingers, palms and forearms – to non-intrusively capture the ASL signs performed by a deaf person. 
By leveraging the extracted skeleton joints information, DeepASL achieves word and sentence-level ASL translation via three innovations. First, DeepASL leverages domain knowledge of ASL to extract the key characteristics of ASL signs buried in the raw skeleton joints data. Second, DeepASL employs a novel hierarchical bidirectional deep recurrent neural network (HB-RNN) to effectively model the spatial structure and temporal dynamics of the extracted ASL characteristics for word-level ASL translation. Third, DeepASL adopts a probabilistic framework based on Connectionist Temporal Classification (CTC) for sentence-level ASL translation. 

It incorporates a novel hierarchical bidirectional deep recurrent neural network (HB-RNN) and a probabilistic framework based on Connectionist Temporal Classification (CTC) for word-level and sentence-level ASL translation respectively. 

To evaluate its performance, we have collected 7, 306 samples from 11 participants, covering 56 commonly used ASL words and 100 ASL sentences. DeepASL achieves an average 94.5% word-level translation accuracy and an average 8.2% word error rate on translating unseen ASL sentences.
