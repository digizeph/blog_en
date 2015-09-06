---
layout: post
title: "Review: Concurrent Prefix Hijacks : Occurrence and Impacts"
categories: [paper review]
tags: [BGP, attack, hijack]
comments: True
citekey: khare2012concurrent
hidden: True
---

## Key Obseravation

**Simutaneous originations of prefixes of many other networks is suspicious.**

> But when a network simultaneously originates prefixes of many other networks,
> it is highly likely to be a real hijack
> since operational arrangements with many different networks
> are unlikely to take effect at the same time.

## Methodology

The first keep track of the **origin changes** from any single monitor on the Internet.
Then it compile the results from many monitors together to form a global view of the origin changes.

Then it will estimate the legitimate changes, and rule them out from the dataset.
The authors considered the following cases legitimate changes:

* **stable AS set**:
    the set of long-lived origin ASes for each prefix
* **related set**:
    the ASes that announces subprefixes or the ASes that are the direct provider of the origin AS
* **large-IXP**:
    the ASes that are among large-IXP collaborations are also considered legitimate origins.
* **same organization**:
    the ASes that are from the same organizations.
    the data is obtained from WHOIS database.

The last step is then to assign a offensive value for each AS:
**the ASes that are not in legitimate set but still announcing the prefixes are assigned with higher offensive value**.

## Validation

The validation of this work is done by sending massive emails (582 in total).

Bib entry:

    @article{khare2012concurrent,
        author = {Khare, Varun and Ju, Qing and Zhang, Beichuan},
        isbn = {9781450317054},
        pages = {29--35},
        title = {Concurrent Prefix Hijacks : Occurrence and Impacts},
        year = {2012}
    }

