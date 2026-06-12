---
title: "[SOLVED] segfaults with ati fglrx 8-6 driver 64bit"
date: 2008-06-21
forum: x86 64-bit Users
---

### Post by lavinog on 2008-06-21
I installed the new ATI catalyst 8-6 driver today using the built in installer. It seemed to install ok except glxinfo/fglrxinfo will segfault.
fglrxinfo would at least give its information then segfault at the end.

I am able to play UT2004 just fine, but after I exit the screen gets scrambled with garbage and I have to reboot throught the virtual console.

I reverted back to 8-5 and everything is fine.

I also have a problem having the installer build packages with complaints that it can't find libraries. using a post on this page helped: [http://wiki.cchtml.com/index.php/Talk:Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Talk:Ubuntu_Hardy_Installation_Guide") of course i had to change everything to reflect the 8-6 driver.

Has anyone else experienced this?

---

### Post by Kilz on 2008-06-21
> **lavinog said:**
> I installed the new ATI catalyst 8-6 driver today using the built in installer. It seemed to install ok except glxinfo/fglrxinfo will segfault.
fglrxinfo would at least give its information then segfault at the end.

I am able to play UT2004 just fine, but after I exit the screen gets scrambled with garbage and I have to reboot throught the virtual console.

I reverted back to 8-5 and everything is fine.

I also have a problem having the installer build packages with complaints that it can't find libraries. using a post on this page helped: [http://wiki.cchtml.com/index.php/Talk:Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Talk:Ubuntu_Hardy_Installation_Guide") of course i had to change everything to reflect the 8-6 driver.

Has anyone else experienced this?

I had the scrambled video with Diablo 2 under wine. I reinstalled 8.5, 8.6 looks to be a bad driver. When you create the packages dont use sudo and it will not error.

---

### Post by lavinog on 2008-06-22
> **Kilz said:**
> I had the scrambled video with Diablo 2 under wine. I reinstalled 8.5, 8.6 looks to be a bad driver. When you create the packages dont use sudo and it will not error.

Thank you for the response. 8.5 works great for me, maybe i'll just wait for 8.7

Also you're right. I can build them without sudo. (the guide on wiki.cchtml.com says to use sudo) It makes sense that I shouldn't need to use sudo, but could you explain why it fails when I do? Is it because the sudo enviroment is different? (curious)

---

### Post by lavinog on 2008-07-25
8-7 fixed everything, but glxgears is reading about 2000 instead of 2100fps...this is pretty minor for me, but I have noticed on many other forums that others complain of the same thing...makes me think that the fix for some issues was to reduce performance some.

As for installation: just running: ```
sudo bash ati-driver-installer-8-7-x86.x86_64.run
```
worked just fine.

---

