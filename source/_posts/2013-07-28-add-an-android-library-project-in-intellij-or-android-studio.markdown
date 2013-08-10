---
layout: post
title: "add an android library project in intellij or android studio"
date: 2013-07-28 22:44
comments: true
categories: [notes, android]
keywords: android library project, intellij, android studio
description: How to implement email function in android
---

It can be tricky sometimes when adding an android library project in intellij or android studio.
The reasons may vary from time to time but two I recently encountered are:

1. Automatic update of project.properties is disabled in intellij, thus the android library project cannot be added.
2. Creating a new library module in android studio, for an ant based project, Studio only creates a settings.gradle, but _forget_ to change the project.properties.

So far, the root cause is clear, the inconsistency between ide settings and android configs.

1. You can manually update project.properties to a correct value
```
target=android-16
android.library.reference.1=../../actionbarsherlock
```
and
```
android.library=true
target=android-14
```
2. Remember to update settings in your IDE

{% img center /images/intellij_update_project_properties.png 'image' 'images' %}

That's it.