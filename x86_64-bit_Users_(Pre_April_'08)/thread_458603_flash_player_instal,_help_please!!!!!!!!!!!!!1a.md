---
title: "flash player instal, help please!!!!!!!!!!!!!1a"
date: 2007-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by elquer on 2007-05-29
hi, 
i'm totally new to ubuntu and linux, i finally decided to try it out for the second time and am in love with the simplicity of it. please, need help installing flashplayer. i have a compaq pressarion v2000 AMD turion64 with ati radeonxpress 200m Graphics card. please i need help istalling flash player, and am willing to hear any advices for new users, like the essential apps needed and stuff. and also, i hear about this wine, i don't really understand it fully, all know is that it enables windows apps to work on linux. please someone get back to me asap,

---

### Post by jerrylamos on 2007-05-29
There are a number of ways to install flashplayer.  I'd suggest trying this first:
close Firefox if you've got it running
from the top line on the screen, System, Administration
enter your regular password
select Synaptic
If you haven't already, do 
Settings, repositories, select all but source
close
click on search, enter: flashplayer
right click flashplugin
select mark for install
click on Apply
then try Firefox, YouTube.com to see if it works.

Synaptic gives you access to endless tons of applications.........

---

### Post by incubus on 2007-05-29
elquer,

Wait.  Did you actually install the 64 bit version of Ubuntu?  You can check that by typing this in the terminal:
```

$ arch

```

If you get "x86_64", then you did.  The procedure for flash will be different.  Let us know.

If not, then follow what jerrylamos explained.  But just so you know, this section of the forum was created for people who are running the 64 bit version, even if they have a 64 bit processor (and opted for emulating 32 bit).

incubus

---

### Post by incubus on 2007-05-29
elquer,

Also, if I may suggest a few links:

How to get some restricted formats in Ubuntu (flash, mp3, DVDs, etc)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

How to get Wine to work
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

And in general, you'll find lots of useful information just by searching this forum.  There's a section of HowTos that is very interesting too.

Best,
incubus

---

### Post by elquer on 2007-05-30
wow, i'm impressed with the level of professionalism and quickness you guys reply, thanks a lot guys. i do have the 64 bit version, i'm about to try what u guys suggested right now. i'll let you know if it works. by the way, ubuntu rocks.

---

### Post by elquer on 2007-05-30
i tried what jerrylamos recomended but when i searched for flashplayer nothing came up. is it because i didn't download it yet ? thanks again .

---

### Post by Cappy on 2007-05-30
That flash package is only for i386 installs. 64-bit users must use this guide:
[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

Another alternative is simply to use Automatix:
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
It installs flash + firefox 32-bit with a click but some people don't like it because it can cause problems (mostly when you want to upgrade to a new Ubuntu). I recommend it if you just "want to get it over with".

---

### Post by Kilz on 2007-05-30
If **all** you require is flash [nspluginwrapper will also work]("http://ubuntuforums.org/showthread.php?t=425672").

---

### Post by elquer on 2007-05-30
thanks a lot for all the reply, i read some post and i found that my best option was to install opera and takea  few easy steps to install flash, i got it to work, thanks guys, any help relating to getting getting my music playing is apriciated. thanks

---

### Post by Steve_Barker on 2007-06-20
Many thanks for that Jerry. Having struggled to no avail to load flash drivers to Opera, that worked a treat.

A new computer, and new Ubuntu user thanks you.

---

### Post by rahimveron on 2007-07-14
Thanks for the help.For opera i used " Another install" - Yes and gave the pathas /usr/lib/opera and it worked!!

---

