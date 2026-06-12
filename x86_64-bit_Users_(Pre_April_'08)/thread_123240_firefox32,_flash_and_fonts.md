---
title: "firefox32, flash and fonts"
date: 2006-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tink on 2006-01-29
Hi Guys,

Following the excellent description of the ff32 & flash install 
here:
[http://www.ubuntuforums.org/showthread.php?t=90106&highlight=firefox32+flash](http://www.ubuntuforums.org/showthread.php?t=90106&highlight=firefox32+flash)
I got the combo going in no time;  I do, however, have ONE problem:  some fonts
aren't being displayed within a flash application on
[http://www.dulux.co.nz](http://www.dulux.co.nz), namely the names of the colour one has highlighted
in the colour selection panel isn't being displayed.

Any hints on where to get the missing fonts, how to find out WHAT font
flash is trying to use there?


Cheers,
Tink

---

### Post by Tink on 2006-02-03
<bump> 

Any takers?
Any further info required? :}

---

### Post by jrib on 2006-02-03
Try installing gsfonts-x11.  If you are still having problems, install msttcorefonts as
well.

That's what seems to work usually anyway, don't know if your problem is instead related to the chroot setup.

---

### Post by Tink on 2006-02-04
The firefox isn't running in a chroot, but on the linux32 layer ;}

And the fonts unfortunately didn't fix the issue. :/  Thanks anyway!


Cheers,
Tink

---

### Post by jrib on 2006-02-04
The fonts athttp://www.dulux.co.nz/ seem to all display for me.  I was going to attach the output of xlsfonts, so that you could diff it with yours and see where the missing fonts were coming from.  That should let you see if it's a font problem or a problem with flash not looking the right place.  However, the file is about 150k and the forums won't let me attach it.  Let me know if you want me to email it somewhere.

---

### Post by Tink on 2006-02-10
Thanks again for the response, my fonts-list would be around 210K, if you
think that those are my issue feel free to e-Mail it to me
tinkster ( at ) linuxquestions ( period )  net



:}


Cheers,
Tink

---

### Post by selinake on 2006-02-12
I've got same problem.

[https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)

Thanks to this i finally get my flash and java correctly working :) \\:D/

---

### Post by Tink on 2006-02-19
Thanks for the comment selinake, but I don't have a probem
running flash.  I have a problem with certain fonts within a 
particular flash-application.  And the tutorial/link won't fix that
since what I have done is pretty much exactly that.


Cheers,
Tink

---

### Post by nemesa on 2006-02-23
It's weird... I have exactly the same font problem, but only at my workplace... I have breezy on my home computer too, but the fonts displayed there correctly... I don't have any idea... 

(the difference between the two computer, the graphic card... i have problem with the computer which has an ati card... but maybe it's not important)

:( :( :(

---

### Post by nemesa on 2006-02-23
The answer is here...

[http://www.ubuntuforums.org/showthread.php?t=97620&page=2](http://www.ubuntuforums.org/showthread.php?t=97620&page=2)

sorry for the pointless post...

---

### Post by Tink on 2006-02-26
[QUOTE=nemesa]The answer is here...

[http://www.ubuntuforums.org/showthread.php?t=97620&page=2](http://www.ubuntuforums.org/showthread.php?t=97620&page=2)

sorry for the pointless post...[/QUOTE]

Well, I have a GForce card with the mosr recent drivers on that machine,
but I'll try editing xorg.conf and see what happens.

Thanks for the hint!


Cheers,
Tink

---

