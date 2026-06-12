---
title: "Strange Thunderbird issue"
date: 2006-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by gorgor_bay on 2006-04-20
Here is my problem, I spent hours browsing around and trying to find an answer, but I found nothing. So here I come :

I'm using since a few months Thunderbird both on Linux and Windows with a shared profile folder.
This morning, I launched Thunderbird under Windows. Once back to Ubuntu, Thunderbird doesn't want to launch anymore. The error message is :
```
selected locale: fr-FR
observe:
nothing here: null
observe called
FILE: [xpconnect wrapped nsIFile]DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 *** Failed to load overlay chrome://spf/content/spf.xul
*** Failed to load overlay chrome://spf/content/statusoverlay.xul
```
I'm using Breezy for amd64 k8, and the Windows Thunderbird version is 1.5 whereas the Ubuntu one is 1.0
Everything went fine until today, I had many switched between Linux & Windows, but this time all went wrong.
I still can access my mails under Windows but this is highly upseting as I wish I could use Windows as few as possible.

Here is a screenshot of Thuderbird stuck :
[[img=http://img85.imageshack.us/img85/4869/capture8fr.th.png]](http://img85.imageshack.us/my.php?image=capture8fr.png)

I tryed backing up my profle under windows, reinstalling it.
I tryed uninstalling Thunderbird under Ubuntu, reinstalling it and going through the profile exchange process again.
I checked the character encoding also...

Anybody has a hint ?

---

### Post by oberoc on 2006-04-22
Crap, I though that I reply to you. do an strace and let's see the bottom couple lines. That might give us something to work with

---

