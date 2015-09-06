---
layout: post
title: "Review: An empirical study of behavioral characteristics of spammers: Findings and implications"
categories: [paper review]
tags: [BGP, spammer, attack]
comments: True
citekey: duan2011empirical
hidden: True
---

## Key Idea

This paper analyzes the charasteristics of the spammers.
The results include a pretty interesting fact that the spammers use
BGP updates to steal IP addresses to send spams.

## Findings

The behaviors of spammers can help develop the **content-independent** anti-spam techniques.
This type of techniques is more resistent to the variantion of the spams
and potentially be more accurate than identifying spams through only the content of the messages.

The authors developed a set of **metrics** to assess the characteristics of the spammers.
The metrics include:

* **spam/non-spam ratios of servers:**
    the majority of the servers are either spam-only or non-spam-only.
    the mixed type of servers are rare.
* **statistics of messages across different spammers:**
    most servers only send a very small amount of spam emails per day
    (less than 10 emails per day is considered small amount)
* **arrival patterns of the spam emails across the IP spaces:**
    most spam emails were sent from a few /8 IP blocks
* **number of mail servers in different networks: **
    86% of the networks have less than 10 spam servers
* **active duration of the spam networks:**
    85% of the spam networks were active for less than 3 days before they went dark
* **correlation with BGP updtes:**
    the spam emails were sent soon after the short-lived BGP updates

Bib entry:

    @article{duan2011empirical,
        author = {Duan, Zhenhai and Gopalan, Kartik and Yuan, Xin},
        journal = {Computer Communications},
        number = {14},
        pages = {1764--1776},
        publisher = {Elsevier B.V.},
        title = {{An empirical study of behavioral characteristics of spammers: Findings and implications}},
        url = {http://dx.doi.org/10.1016/j.comcom.2011.03.015},
        volume = {34},
        year = {2011}
    }

