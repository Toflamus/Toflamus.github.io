---
layout: post
title: Is it possible for a high voltage battery to shock a man?How? 一块高压蓄电池能否以及如何让人中电?
date: 2024-04-28 21:25:00
description: A interesting problem regarding a man holding battery electrode and standing on the ground.一个关于高压蓄电池如何让人中电的有趣问题。
tags: batteries insights shortposts chinese
categories: battery-study
---

今天在看L.Plett的BMS书，Vol2 电池安全防护这一节（1.7）。突然让我重新回忆起一个困扰我许久的问题。

>假设一个人手握一个12V的电池的正负极的任意一级光脚站在地上。它感受到的电压是多少？握在正极和负极的感受到的电压一样吗？btw 这里我主要是想讨论中电问题，也就是说一个人是否会因为触摸高电压电池而中电。  

我之前所想的是：  

* 一块高压蓄电池的电压的主要部分是由物理化学规律决定的，那么这个电压就是一个相对电压，我无法得到某个电极的绝对电压。因此也无法衡量一个电极和大地的电势差，也无法根据36V安全定律来判断是否会安全。  
* 并且因为人和电池没有形成回路，那么如何放电。  

然而在朋友圈进行询问之后不久便得到了一个答案，醍醐灌顶：

>你把它想象成电容就好理解了,12V只是两块板之间的电压差，而你感受的电压跟你手中那块极板到地面的距离，还有各种其他因素决定，不是固定的。  
>——来自Magdalen的好兄弟  

从\[C = \frac{\epsilon S}{d}\] 上来讲，因为距离很远，面积很小，所以电容基本上是0，\[U = Q/C\] 所以电压可能会很大，但是因为电荷是非常少的，所以电压也不会大到离谱的地步。  

电容解释非常中肯，在真实的电池体系中也会出现Double layer capacitance。在电极材料表面就会充电。电池的充放电的回路要求是建立在基尔霍夫定律上的。就是说电荷守恒的条件，但是这个条件在带电体的形况下不满足。  

这不禁让我回想起初中时的测量物体是否带电的实验。摩擦毛皮和玻璃棒让后放到测电器的金属球上面，测电器的金属箔片会打开一个小张角，证明玻璃棒带电。  
