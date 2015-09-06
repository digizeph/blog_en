---
layout: post
title: "Prefix lengths in BGP RIB table"
categories: [bgp]
tags: [bgp, rib, analysis, routeviews]
comments: True
---

Today, I did a quick and dirty analysis of the prefixes lengths in one RIB table dump.

### Question

I am always curious about the prefix lengths in a BGP RIB table.
I learned that the most prefixes are /24, however, I have never confirmed it myself.
So here we are.

### Data source

There are two usual places to go for BGP raw data, RouteViews or RIPE.
For this little test, I used RouteViews #2 collector's RIB dump file.

### Results with Overlapping Prefixes

The result is shown in the figure below.
Here are some findings:

* The largest prefixes are /8.
* Over half of the prefixes are /24 (314,322/591,462)
* There are about 1,000 entries for each length smaller than /24
* Even /32 has 2,458 entries in the RIB, they are the prefixes that only have one IP address!

[![data][image]][image]

[image]: http://i.imgur.com/iSokQEY.png

The only surprise that I have is that there are over two thousand /32 entries in the RIB dump.
Now I am curious about what they are, and what they are for.

The raw result csv files is at [here][raw].

[raw]: https://gist.github.com/digizeph/890ad7d2ac668f4e69d3

### Results without Overlapping Prefixes

After a while, I did another analysis of the prefixes length by removing the overlapping prefixes.
If a prefix in the result is a sub-prefix of any prefixes in the result, 
then I will remove this sub-prefix in the result.
There are  270,354 prefixes left in the resulting prefixes.
There are significant drop of the number of prefixes in all lengths.

[![data][image2]][image2]
[![data][image3]][image3]

The raw result csv files is at [here][raw2].

### IP Space Coverage

The prefixes covers 2794942214 IP addresses, and in total there are 4294967296 addresses.
This takes up 65% of the entire IP address space.

[raw2]: https://gist.github.com/digizeph/45eb4b8950a91c6a6080
[image2]: http://i.imgur.com/jfTrHzw.png
[image3]: http://i.imgur.com/lKv4nt2.png

