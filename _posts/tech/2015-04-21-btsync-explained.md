---
layout: post
title: "BitTorrent Sync mode explained"
comments: true
---

There are three modes for each [BitTorrent Sync](https://www.getsync.com/) folders.
I am totally lost at the begining how these three modes work when I first get my hands on Sync. Here is what I learned after a fruity hour of my life.

Before I talk about the modes, I need to explain the file with suffix ```.bts```. 
This is a special file used by Sync to represent a file that has not been synced on your computer. 
You can think of it as a "link" to the real file that is located on another remote machine.

BTSync introduced this ```.bts``` file to enable the partial synchronization mechanism, which means you can choose to only download the links instead the actual files on your machine.
This makes great sense when you are hosting large files on a remote server, and you only want to access some of them on your laptop.
This also makes sense for BT the company, for which they charge $40 a year as one of the [premium functions](https://www.getsync.com/buy/pro).
I personally wish they could include this as part of the free package, but since they've done a great job on the product, I will not complain.
After all, for less than $4 a month, you can get a fully controlled personal cloud as large as you want (and unfortunately, you still need to purchase the harddrives).

***

OK, back to the main topic. There are three modes of the folders:

* disconnected
* connected
* sync all

For **sync all** folders, all the files will be fully synchronized to the local folder. 
This means any file created on other machines will be uploaded to this folder.
If you delete any file in this folder, the file removal will also be synchronzed on other machines.

For **connected** folders, you will have the "links" for all the files in the folder. 
You can choose to download the files by double click on the files. 
If you add new files in the connected folder, it will upload the files to all the **sync all** folders on other machines.
The new files will also show as links on other **connected** folders.
When you remove a file from the **connected** folder, BTSync will soon add back a ```.bts``` link file to it.
This means you can never truly delete a file unless you do a **sync all** on it.

For **disconnected** folders, all you know about them is that you have access to these folders, but you don't know anything about the files in these folders.
BTSync will not create a folder on your local machine.
No actions will be synchronized.

***

When should you use these modes? Here is an example set up:

* a file server at home: use **sync all** to store all the files uploaded from any devices.
* a laptop: use **connected** folders to only check out files on demand, and upload files to the home server.
* a tablet: use **disconnected** folders to check out what folders are shared from you other devices, and use **connected** folders to selectively download the files on-demand.

As a summary, here is my interpretation of the three modes:

* sync all: the central file hub, everything is uploaded here.
* connected: need on-demand consuming and uploading files to the hub
* disconnected: not interested in this folder, but good to know there is one.
