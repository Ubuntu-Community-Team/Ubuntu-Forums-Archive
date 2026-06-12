---
title: "Problems with compiz/GLX on 6.06"
date: 2006-07-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by lehardi on 2006-07-24
Hi!
I'm trying to install compiz/GLX on my machine but I got some errors. First I've tried this tutorial [http://forum.ubuntu.pl/viewtopic.php?t=8669](http://forum.ubuntu.pl/viewtopic.php?t=8669) (it's in Polish but I linked it becuse commands are English and you can see what I've done). I got this error:
compiz.real: No GLXFBConfig for default depth, this isn't going to work.
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
So I tried this tutorial: [http://ubuntuforums.org/showthread.php?t=133427](http://ubuntuforums.org/showthread.php?t=133427) unfortunately I got some errors again:
compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No managable screens found on display :0.0

I dont't know what can I do... . I have some Linux experience but I'm beginner in Ubuntu. Please help me to run this amazing, as I heard, thing :)

Regards:
-- 
LeHardi

---

### Post by mreynolds on 2006-07-25
I followed a tutorial for 32bit :/ Turns out you have to compile from source. There is a thread here some where.

---

### Post by RAOF on 2006-07-26
> **mreynolds said:**
> I followed a tutorial for 32bit :/ Turns out you have to compile from source. There is a thread here some where.

Hey!  No way.  It's been months since you need to compile-from-source.  Check out [http://compiz.net](http://compiz.net)!  There are a number of howtos there (the second one you linked to was quite old).

---

### Post by RAdams on 2006-07-26
Yeah, I didn't compile from source, and it installed. I followed the tutorial at [http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper). However, I did have to add the repositories for amd64 dapper at moshen.de (deb [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/) dapper eyecandy, deb-src [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/) dapper eyecandy) to get the 64-bit libsvg-cairo.

So lehardi, I would try that how-to (if you have ati, if you've got nvidia, go to ubunutuguide.org and look for compiz on nvidia). Just remember to add the sources I mentioned above, or you'll be hunting for libsvg-cairo as long as I was.

That being said, I'm having some major issues with compiz. The drawing sequence when an application opens turns the majority of the screen to black and white "noise"- it just looks awful, something's wrong there. I can avoid it by disabling the drawing effect in gconf --> apps --> panel, but I want it to work. Also, when I start the session, the background looks like that (black and white patterned) for a few seconds, then it redraws. Also, my titlebars have gone, and I can't get them back. Every help source I saw said to put the effects in a certain order. I tried that order, and it didn't bring back my titlebars. Another help suggested I don't need title bars. Well, I don't need beer either. I hope you can see where I'm going with that.

Anyway, I'm also having general redrawing issues, which could be related to the first problem I mentioned. Lastly, gcompiz-themer doesn't do squat for me.

Any suggestions? Lehardi, if you come across a better tutorial for installing that works, or if you try the one I suggested and it works dandy for you all the way through, please post your new wisdom to us. Because thus far, while I'm maybe a step or so ahead of your current predicament, I'm still
](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by lehardi on 2006-07-30
I think that runninng Compiz on 6.06 AMD64 it's suicide mission in my case. :) I've eliminated previous problems but now I've got new one. When I'm tryin' start compiz I'm getin' "No composite extension" error. So according tutorials I've added:
 Option "Composite" "Enabled" into my xorg.conf. But with this line added xserver resets while tryin' get compiz running.
I have recent nvidia drivers installed. Any ideas?
-- 
LeHardi

---

