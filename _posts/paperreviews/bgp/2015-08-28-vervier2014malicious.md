---
layout: post
title: "Review: Malicious BGP Hijacks : Appearances Can Be Deceiving"
categories: [paper review]
tags: [BGP, hijack, attack]
comments: True
citekey: vervier2014malicious
hidden: True
---

The authors mentioned a key idea in the paper:

>Correlation of suspicious routing events with malicious activities
>is insufficient to evidence harmful BGP hijacks.

This arugument just went against the `duan2011empirical` paper's main methodology.

## System Design

The authors use all four types of data methods in the design of the system.

|               | active          | passive                     |
| ------------- | :-------------: | -----:                      |
| control-plane | RIR             | RIPE BGP Updates            |
| data-plane    | SpamTrap        | Munich's Scientific Network |

[![arch][arch]][arch]

[arch]: http://i.imgur.com/CEYjKdA.png

## Benign MOAS

The authors defined the benign MOAS as

1. multiple origins of a prefix share a direct AS-level link
2. uptime of the prefix is larger than a threshold T

They found out that a lot of the "hijacks" or malicious MOAS are actually benign or unable to be classified.

Bib entry:

    @article{vervier2014malicious,
        author = {Vervier, Pierre-antoine and Jacquemart, Quentin and Schlamp, Johann and Thonnard, Olivier and Carle, Georg and Urvoy-keller, Guillaume and Biersack, Ernst and Dacier, Marc},
        isbn = {9781479920037},
        pages = {890--895},
        title = {{Malicious BGP Hijacks : Appearances Can Be Deceiving}},
        year = {2014}
    }

