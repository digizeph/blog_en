---
layout: post
title: "Review: Losing Control of the Internet: Using the Data Plane to Attack the Control Plane"
categories: [paper review]
tags: [BGP, attack]
comments: True
citekey: schuchard2010losing
hidden: True
---

## Key idea

The BGP routers are vulnerable to Coordinate Croos Plane Session Termination (CXPST) attack.
The vulnerability is based on the fact that the control-plane and data-plane use the same medium.
A flooded medium could jam the control-plane messages and trigger the connected router to believe that the BGP sessions has failed.

The attackers could explote the vulnerability to disconnect a pair of routers.
The disconnected routers will thus generate a surge of BGP updates
that will spread across the Internet's core routers.

>In this paper we show how an adversary can attack multiple BGP sessions simultaneously
>and measure the impact these session failures have on the control plane of the Internet.
>We directly simulate the BGP activity resulting from this attack
>and compute the impact those messages have on router processing loads.
>Through simulations we show that botnets on the order of 250, 000 nodes
>can increase processing delays from orders of microseconds to orders of hours.

Key tasks for CXPST to work:

1. select correct BGP session to maximize the number of BGP updates it will genreate.
2. direct traffic to the target link.
3. minimize the impact of falp dampening mechanisms on the attack.

[![topo][topo]][topo]

[topo]: http://i.imgur.com/OKvQD5b.png

The paper is still vague about how they could actually direct the traffic to the target link.
The evaluation is also done in simulation, which could be impractical in real-world cases.

Bib entry:

    @article{schuchard2010losing,
        author = {Schuchard, Max and Mohaisen, Abedelaziz and Kune, Denis Foo and Hopper, Nicholas and Kim, Yongdae and Vasserman, Eugene Y},
        isbn = {9781450302449},
        journal = {Proceedings of the 17th \ldots},
        pages = {726--728},
        title = {{Losing control of the internet: using the data plane to attack the control plane}},
        url = {http://dl.acm.org/citation.cfm?id=1866411},
        year = {2010}
    }

