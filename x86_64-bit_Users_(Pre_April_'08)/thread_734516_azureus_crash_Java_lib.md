---
title: "azureus crash Java lib"
date: 2008-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by mschira on 2008-03-24
Hi
I want to use azureus for torrent download. It works quite fine with XP, but with Ubuntu 7.10x64 it crashes when I try to run it...

mschira@blues:~$ azureus
changeLocale: *Default Language* != English (Australia). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Australia)' (en_AU), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002aaafc379b4a, pid=6479, tid=1076017488
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0_03-b05 mixed mode)
# Problematic frame:
# C  [libglibjni-0.4.so+0xcb4a]
#
# An error report file with more information is saved as hs_err_pid6479.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)

It does look like a bug, right? should I report it on the Java site?
or does anybody know a fix?
Cheers
M.

---

### Post by Thelasko on 2008-03-25
There are bugs in the 64-bit versions of Java but some versions of Azureus are buggy too.  I would recommend seeing if you can get some web applets to work.    Try something like [Yahoo Stock screener]("http://screener.finance.yahoo.com/fscr/us/launch.html").  I should note that web applets require a plugin for Firefox.  Make sure you have the appropriate plugin for the version of Java you are using.  If those work then try using the version of Azureus from the Azureus website.

There are several [versions of Java available]("https://help.ubuntu.com/community/Java") for 64-bit.  I can't seem to get any of them to work but maybe you will have better luck.  You can see what's installed on your system by going to the [Java Tester website]("http://www.javatester.org/version.html").

---

### Post by dungheap on 2008-04-14
I'm having the exact same problem. Azureus has been working fine for days and then this happens out of the blue. What's going on? I'd really like to fix it because I don't like Bittornado that much. I'm new at this obviously and I really like Ubuntu most of the time but I had no idea it was going to be this buggy and frustrating. ;_; I'm on v7.10 because I'm scared about updating (also it refuses to update but that's another story).

---

### Post by dungheap on 2008-04-14
Oh yeah, and btw the java apps you mentioned aren't working properly, either that or they're being slow. How much of Azureus is written in java? :? UGH and Firefox crashed halfway through writing this. I'm going for a cry now.

---

### Post by dungheap on 2008-04-15
Fine, no one help me, I don't care. :(

---

### Post by Thelasko on 2008-04-15
@dungheap

1) Your problem seems to be different than what is posted here.  Azureus never worked for us, it did for you until recently.  Firefox also doesn't crash for me.  It's quite stable.

2) The problem hasn't been solved for anybody.  It appears to be a problem with 64-bit Java that others are experiencing.

Don't expect immediate help on the boards.  Especially if it's a difficult problem to solve.

---

### Post by dungheap on 2008-04-15
I'm sorry for being rude, I didn't mean to be, I just get a bit frustrated sometimes. :( True, it did work, but when it didn't I got the same message thing as the OP. I shall be quiet now. Sorry.

---

### Post by Thelasko on 2008-04-15
What changed from when it worked to when it stopped working?  Did you install any programs or updates?

---

### Post by dungheap on 2008-04-15
I don't think so, as far as I remember it was inexplicable. If you have any suggestions on a suitable replacement for Azureus that could be good too.

---

### Post by Thelasko on 2008-04-16
No, from what I heard the closest thing to Azureus is µTorrent and that's only available for Windows.

---

### Post by boyofford on 2008-04-16
i tried azureus and had same problem i think, so installed deluge and no probs so far.
Have had utorrent running under wine in 32bit gutsy too and worked ok but could never quite get download to run as fast as utorrent under vista.

---

### Post by cozmicharlie on 2008-04-16
Azureus works fine.  You have so many options with Azureus that it is a great bittorrent client.  It is especailly good if you are networking since it can run in Windows, Linux and Mac.  The problem is most likely a problem with Java (most Azureus problems are).  Type (or cut and paste) this command.

```
sudo update-alternatives --config java
```

What versions of Java do you have installed and which are being used (they have the +)?  For Azureus to work all you need is the Sun Java6-JRE.  Look to see if you have the Iced Tea version of Java.  Even if it does not have the + mark.  If it is installed you have to uninstall it.  Post back your results and lets see if we can get it working for you.

---

### Post by Thelasko on 2008-04-17
Good information about IcedTea effecting Azureus.  Unfortunately, I already tried that.  I have been using only one version of Java at a time to try to prevent issues with two versions of Java on the same machine.

Still, no dice.

---

### Post by cozmicharlie on 2008-04-17
Do you have the Sun-java6-jre fonts installed?
Have you tried to uninstall Azuerus and reinstall using this method [http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus?](http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus?)
If you try that make sure and delete the files in ./azuerus (hidden in you home folder).

---

### Post by Washer on 2008-04-18
this kept happening for me until I got the latest version

Go to [http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)
Get Azureus3053-B03.jar (*or w/e is the latest by the time you read this*)
rename it as Azureus2.jar & overwrite the old one located in /usr/share/java/
use sun java & delete ~/.azureus if necessary (*wasn't for me)*

---

### Post by Artemis3 on 2008-04-18
Just so you know, there is an azureus 3.5 .deb package at getdeb...

---

### Post by cozmicharlie on 2008-04-18
Just to add to what Artemis3 and washer wrote - I agree to use the latest version and the deb works also.  I just wanted to add though some don't like the Vuze interface of the 3.5 version.  Don't worry about that - you can change it to the old interface in options so don't be concerned about installing the new version.  Once you get it installed I can walk you through changing the interface if that is what you prefer.

---

