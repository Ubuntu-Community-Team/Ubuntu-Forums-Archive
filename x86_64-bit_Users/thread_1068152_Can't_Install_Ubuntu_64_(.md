---
title: "Can't Install Ubuntu 64 :("
date: 2009-02-12
forum: x86 64-bit Users
---

### Post by n3tjm on 2009-02-12
Just got a Compaq Presario CQ60-215DX notebook PC. I installed Ubuntu 32bit on it and it runs fine (- the wireless adapter card, but have not spent much time on that). Decided to download the latest 64 bit version of Ubuntu. On installing, I get past the language selection, then I select install. Get the black screen with Ubuntu logo and the scrolling bar. After a little while of the drives running, it freezes. No HD activity, no CD activity. Cap Lock light blinks (not sure what that means). I try downloading it again from a different server, still have the same problem. Please help :(

---

### Post by sanderj on 2009-02-13
"Cap Lock light blinks"? Scroll lock LED too? That would mean a kernel panic. Which is bad.

Options:
Easy: Stay on 32-bit

<EDIT: Correct procedure for changing boot options live CD inserted below>

Long: 
Boot the 64-bit live CD, select the language, and then press F6 ("other boot options"),  go to end of line, remove "quiet splash", then press enter
Ubuntu linux should then boot non-graphically and should show all boot/kernel messages. If/when you get a kernel panic, you should use your camera to make a picture of the screen and post that picture here. And search Google for the error message you see.

---

### Post by n3tjm on 2009-02-13
Here is what the screen looks like when the laptop freezes.

[IMG]http://www.gardei.com/Project/Ubuntu%2064%20Install%20Crash.jpg[/IMG]

---

### Post by sanderj on 2009-02-14
That looks quite bad. And alas I don't see anything google-able, so I can't help you any further.

You could try some other 64-bit versions (Ubuntu 8.04.2, Fedora, etc) and see what happens. Or just stay on 32-bit as that works.

---

### Post by darco on 2009-02-14
Is the Live CD x64? If so, try running it w/o installing, see if it loads.

darco

---

### Post by bart1452 on 2009-02-15
You could try the minimal install, also called net intstall in other Linux versions. I was unable to install the desktop 64 bit image or run it as a live CD but it did install from the minimal install image. I also had to select almost no software but the Ubuntu desktop during the installation to make it go. There were other issues that I ran into but those showed up in the 32 bit image also.

---

### Post by shadowhacker on 2009-02-15
Please see my article [[COLOR="Blue"]here[/COLOR]]("http://www.ehow.com/how_4692369_linux-compaq-presario-cqnr-laptop.html"). I had the exact same problem on a very similar laptop. Hopefully this will solve yours too.

---

### Post by sanderj on 2009-02-16
> **shadowhacker said:**
> Please see my article [[COLOR="Blue"]here[/COLOR]]("http://www.ehow.com/how_4692369_linux-compaq-presario-cqnr-laptop.html"). I had the exact same problem on a very similar laptop. Hopefully this will solve yours too.


So you blacklist the Atheros, and then re-enable it? Is this the same as the Atheros problem mentioned in the 8.10 release notes ([http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros) ath5k wireless driver not enabled by default)?

@OP: have you tried booting an older 64-bit Ubuntu version, like 8.04?

---

### Post by n3tjm on 2009-02-23
Right now I got the 32 bit version of Ubuntu installed. 

It would not boot into Ubuntu 64 from the CD. 

I did try Fedora 11 but it was very sluggish (I understand it was Alpha). 

I may try again later on, but right now looking for second or better job and that is taking a lot of my time (sucks when company you been working for makes cuts so you get paid less than what your bills are)

Doug

---

### Post by Vince4Amy on 2009-02-24
```
I did try Fedora 11 but it was very sluggish (I understand it was Alpha).
```

If you still want to try other distros, give Fedora 10 a go as it comes with 2.6.27.x like Ubuntu does. If that works then it's a Ubuntu specific issue, if it doesn't then it's a Kernel issue.

If it does work you will probably enjoy Fedora 10, it's quite a nice polished distro, and the package management (YUM) is awesome.

---

### Post by shadowhacker on 2009-02-25
As I understand it, the issue is in the WIFI driver. For some reason, the madwifi (I think) driver the 64-bit edition uses for our Atheros 5xxx WIFI cards causes issues. I don't know if the 32-bit edition uses a different driver, or if the driver just works better with the 32-bit environment. I haven't really looked into it much as I was more interested in getting Ubuntu 8.10 working on my laptop. Anyway, disabling the built in driver for the Atheros WIFI and installing the backported 5K version fixes this issue in many many laptops as described in my guide. I had to figure things out the hard way, that's why I wrote it.

---

