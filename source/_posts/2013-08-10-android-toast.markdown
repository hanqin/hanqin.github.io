---
layout: post
title: "android toast usages and tests"
date: 2013-08-10 11:37
comments: true
categories: [notes, android, robolectric]
keywords: android, android toast, android toast duration, robolectric, robolectric ShadowToast
description: tips for android toast and toast testing
---

### Usage tips

I have been perplexed for a long time by the duration parameter of android Toast function,
before I noticed the warning message from android studio

{% img center /images/android_studio_magic_constant_warning.png 'image' 'images' %}

The right way is

``` java
Toast.makeText(activity, "Email was sent successfully.", Toast.LENGTH_LONG).show();
```

or

``` java
Toast.makeText(activity, "Email was sent successfully.", Toast.LENGTH_SHORT).show();
```

### Test

I will demonstrate how to test toast function with [Robolectric](http://robolectric.org/)

1, For default toast message
``` java
Toast toast = ShadowToast.getLatestToast();
String text = Robolectric.shadowOf(toast).text;
```

Also, you can use
``` java
String text = ShadowToast.getTextOfLatestToast();
```

To check shown toast count
``` java
int count = ShadowToast.shownToastCount();
```

To verify a toast message has been displayed
``` java
CharSequence message = "custom message"
boolean showed = ShadowToast.showedToast(message);
```

To get all shown toasts
``` java
List<Toast> toasts = Robolectric.getShadowApplication().getShownToasts();
```

To reset all shown toasts list
``` java
ShadowToast.reset(); // or..
Robolectric.getShadowApplication().getShownToasts().clear();
```

2, For custom toasts
``` java
CharSequence message = "custom message";
int layoutResourceIdToCheckForMessage = R.id.custom_toast_text_view_id;
boolean showed = ShadowToast.showedCustomToast(message, layoutResourceIdToCheckForMessage);
```

For busy developers who don't have time to look at source codes of robolectric. :)