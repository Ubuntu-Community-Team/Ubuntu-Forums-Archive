---
title: "Can't have flash 10, now what?"
date: 2009-01-05
forum: x86 64-bit Users
---

### Post by wolfyking2 on 2009-01-05
Ok, I can't have adobe flash-player 10 on my computer, that Gnash thing doesn't work, so now what?  How am I supposed to play games on miniclip (and what-not) and go on youtube, without any plugins that allow me too?  I am getting desperate, pleash help!

---

### Post by Therion on 2009-01-05
Well the obvious question is...  ***WHY*** can't you install Flash 10?  Further, what happens when you do and how have you tried to install it?

Have you tried using the following in a Terminal:```
wget http://queleimporta.com/downloads/flash10_en.sh
sudo bash ./flash10_en.sh
```

---

### Post by stchman on 2009-01-05
> **wolfyking2 said:**
> Ok, I can't have adobe flash-player 10 on my computer, that Gnash thing doesn't work, so now what?  How am I supposed to play games on miniclip (and what-not) and go on youtube, without any plugins that allow me too?  I am getting desperate, pleash help!

You can have Flash 10 on your 64 bit Ubuntu!!!

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz)

Then extract the archive into your ~/.mozilla/plugins

Make sure you remove any previous Flash from your system.

Flash 10 for 64 bit Linux is Alpha but it works VERY well.

---

### Post by wolfyking2 on 2009-01-05
I have a powewpc iMac.  And I went to Add/Remove programs, found flash plugin, but said it can't be installed on the hardrive.  And yes, I tryed what both of you did.

---

### Post by Therion on 2009-01-05
> **wolfyking2 said:**
> I have a powewpc iMac.  And I went to Add/Remove programs, found flash plugin, but said it can't be installed on the hardrive.  
And yes, I tryed what both of you did.
You're posting in the x86 64-bit forums.  If you're an Apple/PowerPC user you should be posting your issues in the Apple-user support forum:

[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by tuxxy on 2009-01-05
Have you tried the swf moziall plugins already recommended

---

### Post by wolfyking2 on 2009-01-05
> **tuxxy said:**
> Have you tried the swf moziall plugins already recommended yes I have, nothing works.

---

### Post by bumanie on 2009-01-06
As a work around, if it is only you tube you want to watch, Movie player has a plugin that will let you watch you tube. In the right hand top corner, where it says playlist, click on the arrows and you find you can choose you tube - click that and you can watch as much you tube as you wish. I don't know about your flash 10 problems, flash 10 works fine on my 64bit - go to the apple support forum as per therion's suggestion.

---

### Post by steeleyuk on 2009-01-07
There is no PowerPC version of Flash. Its an antiquated architecture, so theres no chance of an official version. Maybe Gnash or Swfdec will come up with something but they are in development.

The only way to get it working is to use nspluginwrapper.

---

### Post by wolfyking2 on 2009-01-08
how do I get the nspluginwrapper?

---

### Post by albinootje on 2009-01-08
> **wolfyking2 said:**
> how do I get the nspluginwrapper?

Check whether it's available :
$ apt-cache search nspluginwrapper

---

