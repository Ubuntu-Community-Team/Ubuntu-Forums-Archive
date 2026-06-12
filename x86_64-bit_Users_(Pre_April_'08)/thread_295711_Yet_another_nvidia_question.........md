---
title: "Yet another nvidia question........"
date: 2006-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jimtheplanner on 2006-11-08
Help... Please:p 

Ok here's the problem I ran dapper on my 64 using nvidia-glx without any problem. However, since edgy arrive I've had problems. I had edgy running using:- 

[INDENT]sudo apt-get update
[INDENT]sudo apt-get install nvidia-glx
[INDENT]sudo nvidia-xconfig

However, my box was not a happy one... No sir, it stalled & stuttered, I gave up for a while. Now i've had another bash, following the "Documentation" wiki for 6.10 using nvidia-glx again problems & I get the following:-

Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

Where do I go from here](*,)  I know there are nvidia issues out there  - am I stuck in one???

Any advice welcome.....
Jimtheplanner

---

### Post by John.Michael.Kane on 2006-11-08
I'm on a clean install of edgy using this guide [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy) I have not had the errors you speak of.

Have you tried sudo dpkg-reconfigure xserver-xorg,and reinstalling the driver's

Also is your edgy install clean or was it a dist-upgrade?

---

### Post by Jimtheplanner on 2006-11-08
Thanks for the reply.

I have a clean install rather than an upgrade. I've not tried sudo dpkg-reconfigure xserver-xorg I give a try... I I fail I'll follow the guide you've kindly posted & see where it takes me...

Thanks again!

---

### Post by Jimtheplanner on 2006-11-08
Hi SD,

Just a follow up thank you I followed sudo dpkg-reconfigure xserver-xorg & had some 3D success..

Now I got to revert my keyboard back from US to GB my @ & " is in the wrong place. If I retrace my steps I should fix it.

Thanks once again.....

Jimtheplanner

---

### Post by Jimtheplanner on 2006-11-08
SD,

Just when I thought all was going well. I reset my keyboard the right way round. However, now I have nvidia working I have music problems! If i rip in sound jucer my system hangs or if I play using rhythmbox it hangs. In the old days when music was in vinyl the record would get stuck in the groove - that's the sound I have. Yes I'm an old dude!!!

Is there a fix for this????

---

### Post by John.Michael.Kane on 2006-11-08
The soundjuicer issues could be due to not having the GStreamer pipeline set right,however.this is just a guess being that I don't do rips. 

Theres another program called **grip** which may do what you need as well.

Sorry I could not be of more help on the particular issue.

---

