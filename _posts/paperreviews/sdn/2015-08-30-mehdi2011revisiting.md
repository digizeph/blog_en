---
layout: post
title: "Review: Revisiting Traffic Anomaly Detection using Software Defined Networking"
categories: [paper review, SDN]
tags: [SDN, security, anomaly detection]
comments: True
citekey: mehdi2011revisiting
hidden: True
---

## Anomaly Detection in Data Plane	
The data plane anomaly detection can be deployed at core network,
or at end-point network.

The paper [mehdi2011revisiting] argues that the deployment of ADS at core network suffers from the following two problems:

* low detection rate
* slow in processing speed

These two problems disabled ADS from being deployed at core network.
As a result, the deployment schemes should be then more focused on end-point networks.

## Anomaly Detection Algorithms

There are four algorithms mentioned and implemented in this paper.

### Threshold Random Walk with Credit Based Rate Limiting

The key idea of this algorithm is to keep track of all the un-established TCP handshakes.
The timed out handshakes or RSTs will result in an increment of suspicious value.
The higher the suspicious values are, the lower the rate will be limited to.

### Rate Limiting

Delay all new connections unless they are in working set.
Only install rules if the traffic successfully finished the handshakes.

### Maximum Entropy Detector

The method is divided into training phase and operation phase.
During the training phase, the algorithm use maximum entropy estimation to establish a based line benign distribution for each class of packets (2,348 classes in total).

Then during the operation phase, use Kullback-Leibler divergence measure of estimate the entropy.
An alarm is raised if a packet KL divergence exceeds a threshold K, more than H times in the last W windows.

The maximum entropy detector requires to examine **all packets**.

### NETAD

NETAD is a rule-based filtering method that can filter out *"uinterested traffic"*.
During implementation, each new packets will be passed to the controller, and the controller check the rules.
If the packet passes the rules, then the corresponding flows will be added to the switch to allow the traffic passing through.

This method also requires to examine **all packets**.


## Data Set

> We decided to collect our own benign and attack
datasets and make them available for repeatable performance evaluations.

### Benign Traffic

The benign traffic was collected in three different locations:

* Home Network
* Small Office/ Home Office (SOHO)
* Internet Service Provider

### Attack Traffic

> we launched (TCP SYN), DoS (TCP SYN)
and fraggle (UDP flood) simultaneously from three end hosts in our research lab.

## Result

The evaluation result shows that the deployment scheme at end-point networks has better accuracy than on ISP. 
The result details shown in the figure below.

[![result][result]][result]

[result]: http://i.imgur.com/ywQx9nN.png

The authors also evaluated the implement on efficiency on the four parameters:

* Percent of total packets that pass through the controller
* Average rate of packets passing through the controller
* Average number of flows in the switch's flow table
* Peak size of the switch's flow table

The result is shown below.

[![efficiency][efficiency]][efficiency]

[efficiency]: http://i.imgur.com/2DQk49r.png

Bib entry:

```
@article{Mehdi2011,
	author = {Mehdi, Syed Akbar and Khalid, Junaid and Khayam, Syed Ali},
	isbn = {978-3-642-23643-3},
	issn = {0302-9743},
	journal = {Entropy},
	keywords = {anomaly detection,network security,openflow,programmable networks,software defined net,working},
	pages = {1--20},
	title = {{Revisiting Traffic Anomaly Detection using Software Defined Networking}},
	volume = {6961},
	year = {2011}
}
```
