---
title: "very fusterated Flash and Ubuntu 64bit"
date: 2009-06-21
forum: x86 64-bit Users
---

### Post by nacho32 on 2009-06-21
all my browsers crash fire fox and opera tried a reinstall 3 time still crash on sites that contain flash. Why I ask hasn't a patch been released for this problem? I spend more time trying to find a solution then actually using the dam operation system. I booted into windows just to come here. When this patch issued give me a email..:confused:

---

### Post by Arup on 2009-06-21
Which version of flash are you trying to install, the x64 Alpha runs fine here.

---

### Post by C0NSTANTIN on 2009-06-21
using xubuntu, here the applications > add/remove manager worke installing "macromedia flash plugin" ... 
just restarted firefox and all the youtube opened up to me :)

---

### Post by izizzle on 2009-06-21
There is always [THIS]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html") script that you could use...

---

### Post by nacho32 on 2009-06-21
> **izizzle said:**
> There is always [THIS]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html") script that you could use...

izizzle  that worked like a charm so far so good , this should be a sticky that script was easy to use did the job for me ,, 

thank you

---

### Post by caeroe on 2009-06-27
> **nacho32 said:**
> izizzle  that worked like a charm so far so good , this should be a sticky that script was easy to use did the job for me ,, 

thank you

Gonna second that.  For the first time in months I can watch Flash in fullscreen without it being so choppy.  I never experienced crashes like some, but I had to close out of fullscreen because the FPS dropped to about 1-2, but audio continued fine.

Thanks!

BTW, the problems I've experienced was with just my desktop, using the Nvidia 8800GT.  My notebook with an ATI card always worked just fine, both run x64 Jaunty.  Which seems to be the opposite of many having issues with ATI and Flash.

---

### Post by Therion on 2009-06-27
Install the Adobe Flash plugin.

Open Synaptic.

Search on **swfdec**.  Uninstall any installed packages you find on this search.

Search on **gnash**.  Uninstall any installed packages you find on this search.

This should solve the problem.

---

### Post by Slim Odds on 2009-06-27
Yes, the alpha 10 works great for me.

P.S. Don't get fusterated, get a dictionary.  :)

---

### Post by nmaster on 2009-06-27
> **izizzle said:**
> There is always [THIS]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html") script that you could use...

i used this one too.  its great :)

---

### Post by jschodde on 2009-10-22
> **izizzle said:**
> There is always [THIS]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html") script that you could use...

Woohoo! After blowing nearly 5 hours on this I finally got it working thanks to this script! \\:D/

My FF version info: Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3 GTB6


Thanks for sharing!

---

### Post by RaveJunkie on 2009-10-23
[COLOR="Blue"]yes this works for most everything and you tube no problem. I am on x64bit 9.04 and ext4 with SLI 9800GTX+'s with 8 gigs DDR3 and most everything work BUT HULU crashes and so does "fancast" by comcast but i think they use the same streaming flash..... for the most part works though. I hope with the 9.10 release this will be addressed. *crosses fingers*

anyone know a work around for HULU for flash 10 x64 firefox users?

to install firefox 3.5 - [http://www.blogsdna.com/3824/how-to-...-904-linux.htm](http://www.blogsdna.com/3824/how-to-...-904-linux.htm)

or

[http://ubuntuforums.org/showthread.php?t=1200446](http://ubuntuforums.org/showthread.php?t=1200446)

then just get flash alpha 10 from adobe and put into your Plugins folder under .mozilia

after you install it it will be called like "shirkto" cause its "too new" and ubuntu goes with the super stable one.[/COLOR]

---

### Post by lonniehenry on 2009-10-23
For hulu and 64 bit, go to .huludesktop and edit the line flash_location + (null)  
It should read the location of your flashplayer.so 

In my case:
flash_location = /usr/lib64/mozilla/plugins/libflashplayer.so

Your location may be different.  Save and it should work.

---

### Post by RaveJunkie on 2009-10-23
lonniehenry

you sir are a genius thank you..... all is well again  :)

---

### Post by lonniehenry on 2009-10-23
Glad you got it going. I am not a genius - just had the problem sooner than you and found a solution because it couldn't find the flashplayer so I pointed hulu to the one I use in Firefox.
Helping out is what these forums are for.

---

### Post by harecanada on 2009-10-28
Hey  lonniehenry, I'm having some difficuty and I'm not sure if it's the same or not. I can watch video feed from BBC news feed and YouTube but not Quicktime movie trailers.And there is one site that I do a kind of servalance for some friends and that site locks my computer so bad I have to do a cold boot and even that won't stop Shiretoko(Fire Fox) from getting into a loop and refusing to work! I was at the point of wanting to dump Fire Fox but I don't know what else is better. It's bizarre and I can't work it out. I'm not very good at problem solving Ubuntu so I really depend on the forums.
Let me know if you can help.
Thanks in advance,
harecanada

---

