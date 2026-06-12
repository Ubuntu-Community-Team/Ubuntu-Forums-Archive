---
title: "Where the menu.lst go now?"
date: 2009-11-08
forum: x86 64-bit Users
---

### Post by goldstar1 on 2009-11-08
Just installed Karmic...would you know it, Grub has no pretty face and I need to get into the menu.lst to make some changes. Well...all has changed and I don't know what to do.

Will someone please help?

Okay I found 'grub.cfg' but I can't save my changes...

How do I make it more beautiful then?

---

### Post by lidex on 2009-11-08
Grub 2 info here:
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

theming:
[http://ubuntuforums.org/showthread.php?t=1182436]("http://ubuntuforums.org/showthread.php?t=1182436")

---

### Post by malangaman on 2009-11-08
grub.cfg shows the result of two other files:

 /etc/default/grub   and    /etc/grub.d

There are scripts that churn these two up to produce grub.cfg.

I spent all day yesterday working on this thing and finally was able to do it by following this guide:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I started in the morning updating these two files, got frustrated and gave up.

Later I succeeded in modifying grub.cfg. You have to make it writable by removing the read only status.

But the Ubuntu kernel update altered it automatically and I lost hours of work.

I was so frustrated I wanted to remove it and re-install good old grub that was so familiar. But I decided to give it one more try.

I returned to modifying the above two files  and achieved a total victory in the evening.

 Grub2 is in Beta and I expect it will be improved soon, I am sure.

If you love command line gibberish you will find ecstasy doing this.

---

### Post by lidex on 2009-11-08
> **malangaman said:**
> 
If you love command line gibberish you will find ecstasy doing this.

:lolflag:

---

### Post by goldstar1 on 2009-11-08
Thank You for you guizes quick responses!

---

### Post by alperkins on 2009-11-14
@malangaman - THANKs for the link, this is so cool.  Didn't have to play with GRUB.CFG, just followed the instructions on the link to edit /ect/default/grub and then did the update-grub to write the info back to GRUB.CFG.  You guys are the best!  Thank you.

---

### Post by oldos2er on 2009-11-15
"This is the file most closely resembling GRUB's /boot/grub/menu.lst. This file contains the GRUB 2 menu information but unlike GRUB's menu.lst the *grub.cfg file is not meant to be edited*." 

 [https://help.ubuntu.com/community/Grub2/#/boot/grub/grub.cfg](https://help.ubuntu.com/community/Grub2/#/boot/grub/grub.cfg)

---

