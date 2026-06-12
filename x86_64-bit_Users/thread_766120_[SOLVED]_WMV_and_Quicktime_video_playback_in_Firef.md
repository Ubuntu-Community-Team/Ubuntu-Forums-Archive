---
title: "[SOLVED] WMV and Quicktime video playback in Firefox/Swiftweasel"
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by GumbyX on 2008-04-25
Just upgraded to 8.04 (it was a bumpy ride I can assure you) and am having a slight problem getting Firefox2 or Swiftweasel (my preferred web browser) to play WMV and Quicktime videos. I was able to while running 7.10, but that was due to Automatix. Since Automatix isn't around anymore, I am trying to find out the proper way to get these codecs installed and working in a web browser. Anyone think they can give me a hand?

Def would appreciate it. Thanks ahead of time to those who help me out.

---

### Post by dtrot55 on 2008-04-25
same here, is there not a kodec pack out that would come with all of these?

---

### Post by GumbyX on 2008-04-25
> **dtrot55 said:**
> same here, is there not a kodec pack out that would come with all of these?

Update: I was able to get Quicktime to play properly by installing ubuntu-restricted-extras from the repository, but for some reason WMV isn't working. Here is where I found the info on the restrict package: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by SunnyRabbiera on 2008-04-25
odd as WMV works for me, but then again I installed the win32 codecs via medibuntu

and I dont use a AMD

---

### Post by GumbyX on 2008-04-25
> **SunnyRabbiera said:**
> odd as WMV works for me, but then again I installed the win32 codecs via medibuntu

and I dont use a AMD

...ok... now its working now. I may have messed something up by installing mozilla-mplayer manually, but not sure. 

Anyway, for those who are having the problem I had, just install ubuntu-restricted-extras from the repository and you should be perfectly fine.

---

### Post by soundengine355 on 2008-06-29
But what about the .wmv that are the new windows media player 9 version? I've installed all the codec packs and still cannot get it to play under 64bit.

---

