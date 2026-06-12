---
title: "Adobe Flash 10 for Linux available (32-bit)"
date: 2008-10-15
forum: x86 64-bit Users
---

### Post by MedianMajik on 2008-10-15
[http://ubuntuforums.org/showthread.php?t=948729]("http://ubuntuforums.org/showthread.php?t=948729")

Adobe now offers Flash 10 32-bit for .deb linux on their webpage.  No 64-bit verson is listed.  [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=DXLUJ]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=DXLUJ") 
Hopefully we'll soon get ours as well

---

### Post by Yellow Pasque on 2008-10-15
> Hopefully we'll soon get ours as well

I heard a rumor about Flash 11-64. Of course, I heard that rumor about Flash 10 as well. Bottom line .. Don't hold your breath.

---

### Post by northwestuntu on 2008-10-16
how can it be that hard for a company that big to release a 64bit version of it? there must be more to this?

flash is the most frustrating thing using linux 64.  it works, but not very reliable.

---

### Post by jespdj on 2008-10-16
There's a script to make it easy to install it on 64-bit Ubuntu 8.04: [http://ubuntuforums.org/showpost.php?p=5974204&postcount=30](http://ubuntuforums.org/showpost.php?p=5974204&postcount=30)

My first impression is that it certainly works better than Flash 9. I had no major problems with Flash 9; occasionally, a Flash element would show as a gray block (problem could be solved by refreshing the page), and full-screen Flash video was choppy with Flash 9. With Flash 10, full-screen video is smooth.

---

### Post by steveneddy on 2008-10-16
Interesting.....

---

### Post by Kilz on 2008-10-16
I think a post with some information is needed to make sure this thread isnt used for FUD in the future.

1. While flash 10 does not have a 64bit plugin, we have nspluginwrapper to make it work. I currently have flash 10 enabled on my system (Hardy).
2.  Flash on 32bit installs has some of the same issues like the grey box.


Its mostly automatic now. With Gutsy they tried, Hardy it works better, it can only get better. A quick read of the flash sticky will give the info needed to get flash installed, apt-get is not a hack.

---

### Post by Locke2053 on 2008-10-16
"I currently have flash 10 enabled on my system"

Care to share with us how you made that work? The .deb for Flash 10 fails on my system, whether or not I have nsplugginswrapper installed. It says I have the wrong architecture.

---

### Post by Thelasko on 2008-10-16
I think it's in the [backports repository]("http://packages.ubuntu.com/hardy-backports/flashplugin-nonfree").(the package downloads flash from adobe.com)  Please correct me if I'm reading this wrong.

---

### Post by jespdj on 2008-10-16
> **Locke2053 said:**
> "I currently have flash 10 enabled on my system"

Care to share with us how you made that work? The .deb for Flash 10 fails on my system, whether or not I have nsplugginswrapper installed. It says I have the wrong architecture.
Did you see my post above?

---

