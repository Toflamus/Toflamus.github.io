---
layout: post
title: 一次有关primitive cell 的问题的讨论
date: 2024-06-11 9:00:00
description: 起因是我不知道为什么Diamond中间有两个C，在朋友圈发了一圈获得许多insights，原因是因为对于Lattice point的定义不清楚，于是记之。  
tags: insights shortposts chinese
categories: solidstate
---

问题描述：  

> 为什么钻石的Primitive Unit Cell（元胞）有两个C。Primitive cell 只允许一个Lattice point出现，这个lattice point 是一个几何概念与化学无关，这意味着在FCC的四面体中心的C与其他在角与面心的C的化学环境不同，于是现在问题来到如何证明其环境不同？  

* 这里直面关键问题： 什么叫环境相同？也就是Lattice的定义。  

> A ***lattice*** is an infinite set of points defined by integer sums of a set of linearly independent primitive lattice vectors.  
> Or, a ***lattice*** is an infinite set of vectors where addition of any 2 vectors in the set gives a third vector in the set.  
> Or, a ***lattice*** is a set of points where the environment of any given point is equivalent to the environment of any other.
> ——The Oxford solid solid state basics.  

第三个定义有一点模糊。实际上环境相等的定义是只允许平移变换的。这可以从定义1得到。其需要整数的线性组合，意味着只有平移可以实现。  

那么如何看待这个钻石的结构呢？ 

> 钻石的结构可以理解为一个面心立方沿着体对角线平移1/4。这意味着其与其他格点不是很对称。（Intuitive）  
> ——来自我的一位好哥们学长  

> 钻石的结构如果重复性很好或者环境与格点一致，那么这个FCC中有四个C你一眼就应该看出对称性，你没看出来就说明重复的不是很好（Genius and inituitive）
> 更为细节的来讲，观察下图，其正四面体环境是需要旋转90°左右才能重合的，因此环境不同。  
> ——来自我的一位合住的好哥们。  

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2024-06-11-primitivecell/Diamond.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

