---
title: "How I Created an Overwhelming Home Network"
date: 2018-10-18T19:03:07-07:00
draft: true
tags: [networking,wifi]
shorturl: https://abhi.ws/easywe3b49
layout: "post"
---
The first router I purchased was a cheap TP-Link one, supported only the 2.4GHz band with a handful of channels, had minimal configurable options and was just that: a cheap consumer grade router. Not saying it was bad, in fact it served its purpose pretty well. Internet speeds were much slower then, RF environments were less noisy and WiFi throughput was not a major concern. Fast forward many years and we have all those, and more problems now.

So, I started re-thinking my home network. I already had a TP-Link AC3200, a very powerful consumer grade router and it did what it was designed to do, very very well. What it didn’t (probably because it was never meant to) do were these:

1. Provide a way to create subnets so I can put my IoT devices on a different subnet, my trusted devices (like our phones and computers) on a second subnet and guests on a third subnet.
2. Be able to serve VPN traffic. Read my [post on why its a good idea](https://abhis.ws/posts/easy-way-to-protect-myself-on-public-wifi-networks/).
3. Create reasonable QoS configuration for my VOIP phones.
4. Separate out the guest network subnet with the ability to provide access to certain resources in other subnets to guests, e.g., to the plex server.

## The end product
I am going to start from how the finished product looks and work backwards and explain how and why I got there. My current setup is best described by this topology schematic:
![Network topology](https://abhis.ws/images/blog/home_network_topology.png)