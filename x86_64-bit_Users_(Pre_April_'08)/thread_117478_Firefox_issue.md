---
title: "Firefox issue"
date: 2006-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by DigitalTiger89 on 2006-01-15
I just installed Ubuntu 5.1 (Breezy Badger) 64 bit on my system.  I went a little upgrade/install happy with Synaptic, and noticed that I could no longer run any kind of web browser.  

Whenever I clicked Firefox, I would see a taskbar item appear saying "Starting Firefox" and the cursor would change, but after several seconds, everything would then stop, as if I had never selected/clicked anything.  I received NO error messages.  Thinking that I corrupt Firefox, I proceeded to install Mozilla and Galeon, which also exhibited the same behavior.  I know my connection is working, since I was able to downloaded packages for update (and also ping).

Is anyone aware of a known conflict?  I know I installed aMorak and RealPlayer10 (I'm suspecting its Realplayer-- just a gut feeling?  I've since just reinstalled everything, and I have it back working.  I'm going to go slower with the package updates, and test Firefox after each one!

Thanks,

---

### Post by RKB on 2006-01-15
Seems we are heading down the same road, I have found that downloading firefox and thunderbird goes fine, I install them into a new DIR and they will not run even though the launcher is pointing at the respective files, I have had to reinstall the old versions to get the system up and going.

RKB

---

### Post by DigitalTiger89 on 2006-01-15
I'm suspecting that the RealPlayer10 install I tried did it, though I did install Thunderbird last time.  What I'm curious about is the fact I was getting no kind of feedback from the system.  I would have expected an error window or something...

---

### Post by John Jason Jordan on 2006-01-15
[QUOTE=DigitalTiger89]I'm suspecting that the RealPlayer10 install I tried did it, though I did install Thunderbird last time.  What I'm curious about is the fact I was getting no kind of feedback from the system.  I would have expected an error window or something.[/QUOTE]
I have a similar problem, although Firefox is still working. And I chatted with someone else who had the same problem as you two are experiencing. But first, note that I am using Firefox 1.07, not the new 1.5 version.

First, I downloaded the tar file for RealPlayer 10 and followed the instructions to install it. However, I could not get it to run. It installed a launch item in the menu, but when I clicked on it, RealPlayer would start, a window would appear on the screen, and then just disappear. No error messages. When I went to a website with streaming audio that called RealPlayer (e.g., [http://www.allclassical.org](http://www.allclassical.org)), again RealPlayer would pop up briefly, then disappear, and then Firefox would disappear also. Never an error message from either RealPlayer or Firefox.

While chatting on IRC with another Ubuntu-64 Breezy user, he installed RealPlayer 10 also, the same as I had done. Afterwards he got the same results I did, except that he was no longer able to launch Firefox. In other words, he got the same results as you guys did. I don't know what he did to resolve the problem, as I have not chatted with him since.

Later I installed chroot. Originally I did so in order to get Adobe Reader 7.0 running. But after succeeding at that, I decided to use it to install RealPlayer 10 as well. Synaptic32 from chroot shows RealPlayer 10, so I installed it using Synaptic32. Now I can get RealPlayer to run by launching it, but it hasn't changed the behavior of Firefox. That is, when I click on a streaming audio link that calls RealPlayer, RealPlayer pops up briefly, then disappears, and takes Firefox with it.

I think the problem is the link in Firefox. It may be calling the version I installed previously; the version that never worked. I would uninstall it if I could figure out how, but it seems the installation script scattered files all over my computer, and there is no uninstall script. Someone told me there is a .log file somewhere that says what it installed, but I haven't tried to uninstall it yet. And even if I did, the link in Firefox is still broken. I think all I really need to do is figure out how to change the link to the RealPlayer in chroot. Unfortunately, I can't figure out where Firefox stores that information or how to change it.

So I guess I'll just watch this thread and see if someone else chimes in with some answers.

---

