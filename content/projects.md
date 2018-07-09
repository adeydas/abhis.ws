---
title: "Projects"
date: 2018-07-08T20:29:48-07:00
draft: false
---
A (*partial*) list of stuff I have either done in the public domain or can share with the same.

## Personal projects
**Polygon Creator**

Based on a project by Di-Labs, PolygonCreator can be used to visually select a geography and product the WKT for it. Useful while doing ad-hoc spatial analysis.

Here's the application: [Polygon Creator](http://polygoncreator.abhis.ws/)

**Biryani Lover**

Biryani Lover is a [twitter account](https://twitter.com/biryanilvr) that scrapes twitter to get tweets on biryani, especially ones with delicious pictures of the dish. Once it finds a tweet that contains a delicious photo of biryani, it runs it through an image recognition algorithm to determine how awesome it is and then retweets it.

Follow [it](https://twitter.com/biryanilvr) to get regular, awesome and delicious tweets on biryani from all around the world.

## Freelance projects
I worked as a freelance developer for sometime. These are some projects I worked on:

**[Zelinx (now UnoLinks)] (http://unolinks.com/)**

Developed the entire backend, and email collaboration system for POP/IMAP servers and an API to “talk” with its mobile apps in PHP and MySQL.

**[DropMiddleMan](http://getfundinggroup.com/)**

Developed the entire backend of the system starting from the admin panel to the interfaces and application logic for all layers of abstraction in PHP with MySQL database at its backend.

**[MotiveMinds CMS](http://www.motiveminds.com/)**

Developed the code base of the CMS, a caching system to optimize the executable code and a search engine optimized URL system in PHP and MySQL.

**[WingSoft Technologies](http://wingsofttechnology.com/)**

Developed the Joomla theme and an extension for connecting with vTiger.


## Academic projects
**CometPark**

CometPark, named after [Comets](https://www.utdallas.edu/news/2012/8/20-19131_The-Whoosh-A-Sign-of-Comet-Spirit-Has-Become-Campu_article-wide.html), is an automated parking spot finder. Imagine if there was an app that could direct you to the next available parking spot. The project was part of a course for my Masters, and these were my responsibilities:

1. Wrote code for the Arduino system to communicate the status of a spot to the central server.
2. Designed and developed an API to "talk" with embedded devices to update parking spot status.
3. Modified GUI to include parking lot switching.
4. Developed an API using Twilio to receive texts and update the system based on the text content.

And now a recorded demo:

<iframe width="420" height="315" src="https://www.youtube.com/embed/JuL5LIw7KDw" frameborder="0" allowfullscreen></iframe>

---

**Cyberminer**

A part of a course I took called Advanced Software Architecture and Design, Cyberminer is a KWICK (Key Word In Context) based search engine. If you are looking forward to read more, here's a bunch of presentations and literature:

1. [Presentation](https://prezi.com/ym5gpflk0fte/cyberminer/#).
2. [Requirement Specifications](Requirement_Specification.docx).
3. [Architecture Document](/files/Architecture_Document.docx).
4. [Test plan](/files/Test_Plan.doc).
5. [User manual](/files/Test_Plan.doc).
6. [Source code](https://github.com/adeydas/Cyberminer).

---

**Monitor VM security in Openstack Cloud**

A course project which was later selected for an independent study, the project had the following goals:

1. Established multi-node private cloud using OpenStack (Folsom version)
2. Created and monitored victim and attacker VMs using Horizon (GUI component of OpenStack)
3. Used attacker VM to simulate following attacks on victim VM
    1. Denial of Service (DoS) attack using Slow HTTP Test
    2. Denial of Service on SSL port 
    3. Port probing using NMap (This is not a attack but the information exposed from this tool can be used in Black Hat Attack process i.e. to study system usage and behavior)
    4. ARP Spoofing using Nemisis
4. Used Nagios monitoring tool to detect DoS attack; and health of Glance, Keystone and Swift components of OpenStack.