---
layout: post
title: "send email in android"
date: 2013-07-29 22:45
comments: true
categories: [notes, android, intent, intent filter, email]
---

There are lots of topics about how to implement email function in android on Stackoverflow, and surprisingly, even for such a simple
function, there are still many things to consider. I will try to summarize and explain in details here, a [demo application](https://github.com/hanqin/AndroidEmailDemo) is included as well.

In brief, I find there are there ways.

1. create a intent with *Action_SEND* and mimeType *message/rfc822*, the codes are listed below
``` java
Intent intent = new Intent(Intent.ACTION_SEND);
intent.setType("message/rfc822");
intent.putExtra(Intent.EXTRA_EMAIL, new String[]{"recipient@example.com"});
intent.putExtra(Intent.EXTRA_SUBJECT, subject);
intent.putExtra(Intent.EXTRA_TEXT, text);
activity.startActivity(Intent.createChooser(intent, "Send mail..."));
```
Few things to note here:

+ mimeType should be set to *message/rfc822* rather than *text/plain*, otherwise there will be bunch of applications displayed in the chooser dialog.

To be continued.

Demo application:

https://github.com/hanqin/AndroidEmailDemo

References:

http://stackoverflow.com/questions/2197741/how-to-send-email-from-my-android-application
http://stackoverflow.com/questions/6827407/how-to-customize-share-intent-in-android
http://www.jondev.net/articles/Sending_Emails_without_User_Intervention_(no_Intents)_in_Android
http://developer.android.com/guide/components/intents-filters.html

