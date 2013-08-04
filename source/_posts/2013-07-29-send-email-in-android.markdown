---
layout: post
title: "implement email function in android"
date: 2013-07-29 22:45
comments: true
categories: [notes, android, intent, intent filter, email]
---

There are several ways to implement email function in android, with their own pros and cons. I will try to summarize everything here, and you can find a [demo application](https://github.com/hanqin/AndroidEmailDemo) at the end.

###1) Use installed mail apps

+ Create an intent with *ACTION_SEND* and *mailto* scheme:

+ MimeType can be set to *message/rfc822* instead of *text/plain*, to limit applications displayed in the chooser dialog.

+ *message/rfc822* stands for
> Email; EML files, MIME files, MHT files, MHTML files; Defined in RFC 2045 and RFC 2046

+ There is also an enhanced version, from which you can determine what will be displayed in the chooser dialog.


``` java
Intent intent = new Intent(Intent.ACTION_SEND, Uri.fromParts("mailto", TO_ME, null));
intent.setType("message/rfc822");
intent.putExtra(Intent.EXTRA_EMAIL, new String[]{TO_ME});
intent.putExtra(Intent.EXTRA_SUBJECT, subject);
intent.putExtra(Intent.EXTRA_TEXT, text);
activity.startActivity(Intent.createChooser(intent, "Send mail..."));
```

###2) Use the java mail api
(ported to android by [Jon Simon](http://www.jondev.net/)).

Firstly, you will need to download three jar files from https://code.google.com/p/javamail-android/ .

Then, simply follow the code provided in the demo application, or you can refer to http://www.tutorialspoint.com/java/java_sending_email.htm for a comprehensive guide.

###3) Use specifically built backend Api

Most applications have a backend service, it is easy to add an api that collects info from handsets and send mail on the server side.

####Demo application: (last update on Aug, 4, 2013)
https://github.com/hanqin/AndroidEmailDemo

####References:

http://stackoverflow.com/questions/2197741/how-to-send-email-from-my-android-application
http://stackoverflow.com/questions/6827407/how-to-customize-share-intent-in-android
http://en.wikipedia.org/wiki/Internet_media_type
http://www.jondev.net/articles/Sending_Emails_without_User_Intervention_(no_Intents)_in_Android
http://developer.android.com/guide/components/intents-filters.html

