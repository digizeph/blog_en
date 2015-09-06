---
layout: post
title: "How to install Monitorix on Ubuntu 14.04"
comments: True
---

[Monitorix][monitorix] is a very useful and open source tool to provide overall Linux system monitoring.
Here is some screenshot provided on their website.

![main](http://www.monitorix.org/imgs/main.png)
![netstat](http://www.monitorix.org/imgs/netstat.png)

Pretty cool ha? It is especially useful when you do not have a clear idea of where to look for anomalies on your system.
However the provided installation guide for [Ubuntu][monitorix:deb] is not so clear (it is actually wrong for the new version of Ubuntu).
Therefore I spent sometime on figuring out how to correctly install the Monitorix on Ubuntu 14.04, and here we go.

Download the deb package from the [download link][monitorix:download].

	wget http://www.monitorix.org/monitorix_3.6.0-izzy1_all.deb

Install the package using ```dpkg```  command.

	sudo dpkg -i monitorix_3.6.0-izzy1_all.deb

In this step you will probably encounter some errors like the following image. Ignore them and proceed on the next step.

![](https://farm8.staticflickr.com/7418/16549989652_32c937296b.jpg)

Automatically fix the installation error using ```apt-get``` command.

	sudo apt-get -f install

Note that there is nothing after "install".
In this step, ```apt-get``` will automatically fix the dependency problems happened in the previous installation.

![](https://farm8.staticflickr.com/7302/16363415998_bdd7fdc359.jpg)

Now you can go to 

	http://yoururl:8080/monitorix/

and enjoy this monitoring system.


[monitorix]: http://www.monitorix.org/
[monitorix:download]: http://www.monitorix.org/downloads.html
[monitorix:deb]: http://www.monitorix.org/doc-debian.html

