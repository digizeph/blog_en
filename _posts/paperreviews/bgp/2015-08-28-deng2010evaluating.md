---
layout: post
title: "Review: On evaluating BGP routing stress attack"
categories: [paper review]
tags: [BGP, attack]
comments: True
citekey: deng2010evaluating
hidden: True
---

This paper introduce a new attack inspired from synchronization and resonance in complex system.
The attack is essentially exaust router's storage processing power and storage capacity,
and cause the routers to restart and reannounce its learned RIB table.
By **carefully select target routers to attack**, the resonance effect could cause a globally flood of BGP announcements.

## Evaluation by Simulation

The method and topology for simulation is shown in the figures below.

[![topo][topo]][topo]
[![method][method]][method]

[topo]: http://i.imgur.com/nRs9YhL.png
[method]: http://i.imgur.com/C6AhH7Q.png

## Cascading Failure

If one AS fails, its neighbors need to withdraw all the routes learned from the failed AS.
The ripple effects will cause a large amount of withdrawal and announcements.

Bib entry:

    @article{deng2010evaluating,
        author = {Deng, Wenping and Zhu, Peidong and Lu, Xicheng and Plattner, Bernhard},
        issn = {17962021},
        journal = {Journal of Communications},
        number = {1},
        pages = {13--22},
        title = {On evaluating BGP routing stress attack},
        volume = {5},
        year = {2010}
    }

