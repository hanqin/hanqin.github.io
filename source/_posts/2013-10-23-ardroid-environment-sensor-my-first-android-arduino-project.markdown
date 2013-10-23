---
layout: post
title: "Ardroid environment sensor - my first android - arduino project"
date: 2013-10-23 22:37
comments: true
categories: [notes, android, arduino]
keywords: android, ardunio, bluetooth, DHT11, gradle, Firmata, AChartEngine
description: build android - arduino project with bluetooth
---

Recently, I have spent most of my spare time on [arduino](http://www.arduino.cc/), an open-source
electronics prototyping platform.

Arduino is very easy to use that one with little hardware
knowledge like me could start making something quickly, and with various shields
and sensors, it is also very powerful.

Ok, let's go to the main topic today, my first android arduino project.

The reason for the small project is very tricky, that is, I usually doubt the
weather and envrionmental info from official departments, especially for the PM
2.5, As a result I decided to build an environment sensor and take it with me
every day. The data around me is the most accurate one, right?

{% img center /images/ardroid.png 'image' 'images' %}
Above is how ardorid looks like, at the time of writing, I havn't found
a satisfying PM2.5 sensor, so you can only see two lines showing.

#### The basic idea is:

1. android device (my Huawei Y300) will act as a collector, analyser and display
   of the envriomental data.

2. arduino(openjumper mega2560, openjumper sensor shield v3, bluetooth adapter,
   dht11 sensor) will retrieve data and feed to the collector.

#### Some details of the tech stack:

1. For the beautiful dynamic chart, the framework is _AChartEngine_.

2. For communication between android and arduino, _Firmata_ is your friend.

3. Also, _bluetooth_ is a nice choice besides google ADK board.
_OpenJumper sensor shield v3_ makes the integration of bluetooth module, _DHT11_ sensor supper easy.
4. Others like the battery-powersource, gradle will lead you a good life:)

Please refer to [Github](https://github.com/hanqin/Ardroid) for the code.
