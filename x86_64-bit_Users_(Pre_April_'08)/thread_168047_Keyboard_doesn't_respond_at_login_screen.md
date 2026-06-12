---
title: "Keyboard doesn't respond at login screen"
date: 2006-04-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by andrej on 2006-04-29
This problem is similar to those who posted [**here**](http://ubuntuforums.org/showthread.php?t=161054), [**here**](http://ubuntuforums.org/showthread.php?t=122163), [**here**](http://ubuntuforums.org/showthread.php?t=93178), and [**here**](http://ubuntuforums.org/showthread.php?t=69159).

I have an iMac G5, and I just finished installing Ubuntu. I get to the login screen, but just after the screen displays and I get to type in my username, the mouse and keyboard no longer respond. In fact, when I try to unplug and replug in my keyboard to the computer, the keyboard isn't even recognized. (The caps lock light doesn't turn on when I press it, and my mouse does not have that red glow.) It doesn't matter which one of the three USB ports I use to plug in the keyboard, since I cannot get power to the keyboard. I was able to use the keyboard and mouse right up until that screen. What's going on?

---

### Post by Giles on 2006-04-30
I have the same problem. I am dual-booting OSX and Ubuntu on an iMac G5 17 inch. None of the fixes work for me becuase I do not have time to log in after pressing Control + Alt + F1. Are there any other workarounds?

---

### Post by andrej on 2006-04-30
I can install Ubunti on my old iBook (G3, 466MHz) fine (and after erasing the hard disk).

iBook installation: The Ubuntu start-up screen has a black background with reflecting, table-top-like lettering of "ubuntu" in brown letters and the Ubuntu logo, followed by a vertical, two-column list of verified items, displaying their status in brown colored text. The horizontal progress bar in between the log and the list is, also, brown.

The log-in screen is functional.


My iMac installation consisted of a dual-boot configuration. I used the leftover partitions for boot, swap, and the mount, which I set to be at **/**. Out of the partition options for **/**, I used the Ext3 journaling file system.

iMac G5 installation: The Ubuntu start-up screen has a black background with extremely rough lettering of "ubuntu" in metallic, gray, red, blue, and green letters, with the Ubuntu logo almost unrecognizable, because it looks completely recolored as someone would with experimental pixel art. The same thing, "ubuntu" and the logo, appears right below, but vertically flipped and somewhat less colorful. These items are followed by a vertical, two-column list of verified items, displaying their status in green colored text for a success and pink for a failure. There is no brown color anywhere. The horizontal progress bar has a blue background, and red fills it from left to right as the list grows. (Note: The red and blue colors might be reversed.)

The log-in screen is inaccessable, but it appears exactly as on the iBook.


I did not use the internet to install further components for either system.

I even tried installing every extra module during my iMac installation by typing in **expert-powerpc64** on the resulting black screen with white text that comes from booting off the CD with the Ubuntu ISO burned, and that did not change the installation patterns.


Here is what I am thinking of doing now for further tests:
[1] Reinstall Ubuntu while having my monitor resolution set differently before using the bootable CD.
[2] Repartition the entire Hard Drive and installing Ubuntu first before OS X.
[3] Use a different format for the **/** partition.
[4] Combine the above three tests somehow.
[5] Study like mad for my five final exam tests instead.


[**An earlier thread**](http://www.ubuntuforums.org/archive/index.php/t-89712.html) suggested the temporary disabling of the sound system, but I want to use and control the sound system at all times.

Any other suggestions before I go study?

---

### Post by andrej on 2006-05-07
[one week later]

Oh, and now this one is just bizzare! I just downloaded the Kubuntu 6.06 beta Live CD, and the same thing happens! It locks up during the log-in process! I tried the monitor resolution change. Nope, didn't work. But because the Live CD causes problems (including the discoloration on the start-up screen), as well as Ubuntu, the other tests won't work.

I went through the [**Live CD**](http://ubuntuforums.org/showthread.php?t=118282) thread (again), and... you've gotta be kidding me! Why don't the developers recognize the incompatibilities with *buntu and the iMac G5? When is this going to be fixed so that I can use any *buntu distro on my iMac?

Well, I guess I now know why the computer locks up.

---

### Post by Torrance on 2006-05-08
The work-around for this issue is here: [http://ubuntuforums.org/showthread.php?t=89712&page=3](http://ubuntuforums.org/showthread.php?t=89712&page=3)

This bug has been around for a while and is still unresolved in the latest Betas of the next version - I hope they get it sorted!

---

### Post by andrej on 2006-05-08
Yeah, I read through your post a few times in the past two weeks, but I wanted a more permanent fix than that. Seeing as how there is none, I'll wait a while before I get more seriously dedicated with Ubuntu.

---

