---
title: "Multimedia and MythTV on AMD64"
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Drain on 2005-10-15
Hey all - 
I just wanted to see/hear people's experiences of running multimedia applications on Breezy before I made the plunge -  it sounds like most people are upgrading pretty easily. Here are my thoughts/questions:

I recall having a problem with the installation of transcode on Hoary, so that I could run dvd::rip. There were a couple of howtos that pointed to other file repositories that helped with the install - has that been simplified at all?

I also saw in the [forum thread here]("http://ubuntuforums.org/showthread.php?t=75278") how to install Win32 codecs, which looks great! But does anyone have a solution for handling wmv9 files, 'cause that would be amazing. (Perhaps we should have a separate How-To list in the AMD64 forums?)

And finally, I understand that MythTV on AMD64 in Breezy is having problems getting off the ground with version 0.18-1. Some parts are upgraded, some parts are still back at the 0.17-3 revision. What gives? I know there were some problems with compiling this for AMD64, is this a MythTV thing moreso than an Ubuntu thing or vice-versa? Can the community get behind one or the other or both of the groups to get this done?

Enough of me ranting. What do other people think/have information on?

---

### Post by RAOF on 2005-10-16
I have a [bug]("https://launchpad.net/distros/ubuntu/+sources/mythtv/+bug/2492") in malone about the mythtv issue.  I can't actually complie mythtv myself, so I think it's more than just a packaging issue.

---

### Post by fimbulvetr on 2005-10-16
I've successfully installed mythtv from source on my breezy amd64 after I found that:
A. The packages don't work.
and
B. I need firewire support, and the packages don't come with that built in.

---

### Post by RAOF on 2005-10-16
Ooooh!  Please, tell us how :KS Does anything funky need to be done?

---

### Post by FluffyElmo on 2005-10-17
Try this thread:
[http://ubuntuforums.org/showthread.php?t=74660]("http://ubuntuforums.org/showthread.php?t=74660")

---

### Post by Drain on 2005-10-17
[QUOTE=FluffyElmo]Try this thread:
[http://ubuntuforums.org/showthread.php?t=74660]("http://ubuntuforums.org/showthread.php?t=74660")[/QUOTE]

Kick ass! FluffyElmo, that rocks.... 

I guess the next steps are to write a How-To and/or submit it to the Ubuntu development people for packaging. :-)

---

