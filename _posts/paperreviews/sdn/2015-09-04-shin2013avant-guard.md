---
layout: post
title: "Review: Avant-guard: Scalable and vigilant switch flow management in software-defined networks"
categories: [paper review]
tags: [SDN, security]
comments: True
citekey: shin2013avant-guard
hidden: True
---

**Avant-guard** propose two ideas in the paper:

1. Connection migration
2. Condition triggers for rule processing

## Connection Migration

The connection migration box mainly focused on solving the problems of SYN flood in SDN environment.
The SYN flood will trigger a `packet_in` message flood from the SDN switch to SDN controller.
While the SDN switch waiting for the reply from the SDN controller,
the cache of the switch is vulnerable to exhaustion and thus could potentially crash the switch entirely.

The main idea of solving this problem is to process the TCP SYN separately.
It will first classify the traffic and remove all unrecognized TCP FIN or RST packets.
Then the migration box itself will do the handshake with the source.
After a full handshake, it will then report to the controller and make connection with the real destination.
After the controller replies, the migration box will work as a relay, forwarding all the traffic to the destination.
**Essentially, the migration box works as a men-in-the-middle, and filter out SYN flood messages without involving the controller.**

The delaying mode of the connection migration only start the contacting the controller when it receives the traffic content after the handshake.

**Standard connection migration scenario:**

[![mc][mc]][mc]

[mc]:http://i.imgur.com/7cGUTxX.png

**Standard connection migration delay mode scenario:**

[![mcdelay][mcdelay]][mcdelay]

[mcdelay]:http://i.imgur.com/6npXjQe.png


## Actuating Trigger

The idea of the `actuating trigger` is simple as putting a condition check in SDN switch.
After the matching of flows complete, the SDN switch will also collect some basic statistics and check the condition.
If the condition is met, the SDN switch will run a call-back function that can notify and react to the situation.

This idea can be used for close-to-real-time anomaly detection without pulling/polling the switches. 
However, this design requires changes to the existing SDN switches and adds additional component in between the flow processing procedure, and thus could face hurdles in deployment.

Here is an example scenario of the actuating trigger:

[![trigger][trigger]][trigger]

[trigger]:http://i.imgur.com/sHEuvAa.png

Bib entry:

	@article{shin2013avant-guard,
		author = {Shin, S and Yegneswaran, V and Porras, P and Gu, G},
		isbn = {9781450324779},
		journal = {Proceedings of the 2013 ACM \ldots}
		title = {{Avant-guard: Scalable and vigilant switch flow management in software-defined networks}}
		year = {2013}
	}
