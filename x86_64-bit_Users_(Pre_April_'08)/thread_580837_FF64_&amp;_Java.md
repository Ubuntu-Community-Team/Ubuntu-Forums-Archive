---
title: "FF64 &amp; Java"
date: 2007-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by LoneWolfJack on 2007-10-19
There seem to be 1000 threads about FF64 and Flash/Java because it still doesn't seem to be working right out of the box. I managed to get the flash plugin working because I happened to find some thread where it said only the flash-nonfree package works, which can only be acquired through synaptic.

Java won't work though... I tried installing the packages that are available through add/remove applications as well as the ones available through synaptic (even though it could be possible I just didn't find the right ones there).

I finally ended up installing the 32 bit JRE kit from sun.com, which at least made FF recognize it's Java it needs to run the applet, not just some unknown type of plugin.

If someone would be able to point me in the right direction regarding a fix, this would be appreciated.

Thank you.

---

### Post by andreasiro on 2007-10-19
I tried with Gnash or whatever it's called, but nothing worked...

---

### Post by LoneWolfJack on 2007-10-19
Gnash didn't work for me either and in another thread someone was talking about terrible performance of this package.

If you are using Gutsy 64 with FF64, get the "flash-nonfree" package from synaptics, this worked for me.

Still trying to fix the Java issue though.

---

### Post by FredB on 2007-10-19
There is no 64 bits java plugin for now. We will have to wait for java7. With a little luck it will be available for 8.04 LTS.

---

### Post by captaink on 2007-10-19
Until then, if you wanna use FF64, you should install Blackdown Java 2 JRE 64bit. It's a bit old, though it's the only java available for 64-bit with a working plugin for FF.
The other solution is to use free java, check [here]("http://help.ubuntu.com/community/Java"), though I don't know if it still exists on Gutsy. However, you should be cautious with that machine, since it's not as secure as Sun Java.
If you don't find solution to the above, use 32-bit FF and don't bother. Search [help.ubuntu.com]("http://help.ubuntu.com") for more info on how-to.

---

### Post by yostral on 2007-10-19
Java7 is in the repos... it's called Icedtea. And there's a plugin for Web browsers. But it's too young for the moment. I'm unable to run any applet :(.

---

### Post by LoneWolfJack on 2007-10-20
Well, I happen to have blackdown installed... apparently it comes pre-installed with gutsy... still no applets though.

Any other ideas?

---

### Post by chaosrl on 2007-10-23
try uninstalling and reinstalling blackdown. when i first upgraded to gutsy from feisty my java apps didn't work, but i reinstalled blackdown (making sure to follow the recommendation for stop:thread or whatever), and it works fine now.

---

