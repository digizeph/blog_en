---
layout: post
title: "Review: Securing BGP - A Literature Survey"
categories: [paper review, BGP]
tags: [BGP, security]
comments: True
citekey: huston2011securing
hidden: True
---

## BGP Threat Model

The BGP theats can be categorized by asking the following questions:

* How do we talk? -- the TCP channel security
* Who am I talking to? -- the identity verification
* What are you saying? -- the message integrity
* Should I believe you? -- the trust model
* How recent is your info still valid? -- TTL for your messages

These questsions essentially includes all the aspects that a communication between 
two BGP routers would have.
If we could secure all of the aspects, 
we are then on the pretty secure side of the war.

However, the design of BGP does not take these aspects into consideration,
and thus creates a set of serious problems.
The consequences include the capability for the attackers to:

1. eavesdrop on the Internet traffic
2. conduct denial of service using invalid messages
3. potentially masquerade different entities on the Internet
4. steal unused addresses for malicious purposes

Years of efforts has been devoted to secure the BGP and here are some apporaches.

## Securing BGP

Approaches:

### Securing BGP Operations

* GTSM
* IPSec
* MD5 signature

### Securing BGP Messages

* Out of band: DNS or IRV
* S-BGP, BGPSec
* soBGP
* psBGP
* IRV
* chained hash function
* SPV
* signature amortisation and aggregate signatures
* path stability

### Securing data plane

Issues are that Mao et al. [143] found that up to 8% of the routes advised through control plane channel
do not match the data plane path that the traffic actually took.
Several approaches has been devoted on securing the data-plane security of BGP:
* *secure traceroute*
* *Faith*
* *Listen and Whisper*

## Deployment Status

The figure below shows the depoyment status of the existing BGP security approaches.
3 out of 12 approaches has been implemented, and 2 of them were actually deployed.

[![deployment][deployment]][deployment]


[deployment]: http://i.imgur.com/MOWnd51.png

Bib entry:

    @article{huston2011securing,
        author = {Huston, Geoff and Rossi, Mattia and Armitage, Grenville},
        issn = {1553-877X},
        journal = {IEEE Communications Surveys \& Tutorials},
        keywords = {BGP,BGP security,Computer Network Protocols,Inter-domain routing security,routing},
        number = {2},
        pages = {199--222},
        title = {{Securing BGP ? A Literature Survey}},
        volume = {13},
        year = {2011}
    }

