---
title: "32 bit apps lost internet connectivity"
date: 2008-04-23
forum: x86 64-bit Users
---

### Post by timeoff on 2008-04-23
Following yesterdays updates on hardy various 32 bit apps which I have installed locally (flock, secondlife etc) seem to have lost the ability to access the net. Curiously, skype continues to work. The standard 64bit apps are unaffected (Firefox3 etc). Reinstallation of ia32libs makes no difference.

Anyone else had a similar issue arise or have any clues what to try to bring them back to life?

---

### Post by timeoff on 2008-04-23
After some digging around this [bug]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/220377") refers.

---

### Post by mthome on 2008-04-23
None of the references I've found seem to apply to my situation - how 'bout a pointer to your solution?
[edit]
Workaround is to install lib32nss-mdns for some reason, also breaks java networking and various other things.
On reference is [https://bugs.launchpad.net/ubuntu/+bug/220314](https://bugs.launchpad.net/ubuntu/+bug/220314)

---

### Post by stoneage on 2008-04-28
I have the same problem with 64 bit Flock on Hardy. After upgrading Flock stopped working properly. I tried reinstalling from get-deb.net and now it won't work at all. Launched from a Terminal I get a 'segmentation fault', and launched from the icon, Flock opens, but seems unable to connect to the internet. 
Firefox and Epiphany are problem free.

---

### Post by stoneage on 2008-04-29
Ahaa.  You could try the 'disable ipv6' thing.
[http://ubuntuforums.org/showthread.php?t=772396&highlight=flock](http://ubuntuforums.org/showthread.php?t=772396&highlight=flock)

---

