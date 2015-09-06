---
layout: post
title: "Review: A Longitudinal Study of BGP MOAS Prefixes"
categories: [paper review]
tags: [bgp, moas, attack]
citekey: "jacquemart2014longitudinal"
comments: True
hidden: True
---

This [paper][pdf] looks at the MOAS 'problem' in a long-term perspective, and the results are pretty interesting.

## MOAS - Multiple Origin AS - Problem

MOAS has been brought out by TODO.
Orginally, this is treated as problematical scenarios, since there should only be one destination for a prefix.
However, people have been arguing that MOAS can have multiple legitimate uses.
For example, a prefix owner could be client to multiple upstream ISPs,
and ask all of them to announce the prefix for the prefix owner.
The world would see two origins toward the same prefix.
However, in this case, the situation is totally legitimate.

## Methodology

The authors took two year's routing table entry dumps from 2002 and 2012, 10 years apart.
They then conduct a set of genral statistics for MOAS and SOAS events.
The results show that MOAS prefixes have much longer uptime and life time,
suggesting that the MOAS helped the reachability of these prefixes.

![general statistics](http://i.imgur.com/LGB2PBv.png)

They also looked at the comparison between the long-lived (longer than 1 day) and short-lived events.
The results showed that the majority of the MOAS events are long-lived.

![long-lived and short-lived](http://i.imgur.com/oJC15SZ.png)

## Patterns

The authors found three patterns (models) among all the MOAS events:

* Peering: provider and owner both announcing, same AS path
* Classical: multiple providers announcing the prefix, different AS path
* Me-too: combination of peering and classical

![patterns](http://i.imgur.com/qYB9VfL.png)

## Findings

1. Most of the MOAS are long-lived.
2. Three patterns of MOAS.
3. There is little difference in uptime, MOAS durations, and category proportions between 2012 and 2002.

[pdf]: http://www.eurecom.fr/fr/publication/4254/download/rs-publi-4254.pdf 

Bib entry:

    @incollection{jacquemart2014longitudinal,
      title={A longitudinal study of BGP MOAS prefixes},
      author={Jacquemart, Quentin and Urvoy-Keller, Guillaume and Biersack, Ernst},
      booktitle={Traffic Monitoring and Analysis},
      pages={127--138},
      year={2014},
      publisher={Springer}
    }

