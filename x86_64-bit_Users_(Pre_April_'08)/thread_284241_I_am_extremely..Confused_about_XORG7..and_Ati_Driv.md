---
title: "I am extremely..Confused about XORG7..and Ati Driver Issues"
date: 2006-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by xthaparian on 2006-10-25
Guys..
Its been 2 days of searching..and No HELP..on How to solve the
issue of ATI driver instalaltion.
After following the Following Tutorial
[http://www.ubuntuforums.org/showthread.php?t=204910&highlight=ati](http://www.ubuntuforums.org/showthread.php?t=204910&highlight=ati)

I cannot get 3-D to work!!!!!!!

I get after rebooting
> $fglrxinfo
> Error: couldn't find RGB GLX visual!


glxgears command still gives me same error..

Any HELP WOULD BE GREATLLLLLLLLY APPRECIATED...I need a GOD to save from this   ](*,) 

I am Using Latest XORG7 that came with system installation CD

System:
Sapphite Radeon 9600
AMD 64, Ubuntu 6.06 amd64

---

### Post by ReaderRat on 2006-10-25
Have you tried this site....
ATI Video - How to install the drivers
          **[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)**

---

### Post by John.Michael.Kane on 2006-10-25
Have you looked over this thread [http://ubuntuforums.org/showthread.php?t=235145](http://ubuntuforums.org/showthread.php?t=235145)

---

### Post by xthaparian on 2006-10-25
> **ReaderRat said:**
> Have you tried this site....
ATI Video - How to install the drivers
          **[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)**

I have installed using Method 2 with the latest drivers from ATI...
Still have the same problem..

---

### Post by xthaparian on 2006-10-25
> **SD-Plissken said:**
> Have you looked over this thread [http://ubuntuforums.org/showthread.php?t=235145](http://ubuntuforums.org/showthread.php?t=235145)

Sounds promising...I will try this after I reach home today...Lets wait and see...

I have learnt that there is some problem with libglu.so.1
Because the Xorg is updated to 7 the problem is caused by some symbolic links to the files..

Anyways..I'll try this.

Thanks

---

### Post by xthaparian on 2006-10-25
> **SD-Plissken said:**
> Have you looked over this thread [http://ubuntuforums.org/showthread.php?t=235145](http://ubuntuforums.org/showthread.php?t=235145)

Ok...I tried it and Looks Like it has worked!!!!!!!!!
But when I type 

> glxgears

Then I do get gears...but they run..Slow..and I dont see any FPS in the Window..?

But I Also Get..

> xthaparian@xthaparian-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5946 (8.27.10)


So..the Questions Remains...Wheather the 3D is working or not?

How Do I do the real test for that?

Thanks for Input...:KS

---

### Post by John.Michael.Kane on 2006-10-25
I would believe your set.

Does the desktop it self seem to be more smother?

I just ran glxgears on my machine ,and did not get fps,however that has not had an effect on my system performance.

---

### Post by xthaparian on 2006-10-26
> **SD-Plissken said:**
> I would believe your set.

Does the desktop it self seem to be more smother?

I just ran glxgears on my machine ,and did not get fps,however that has not had an effect on my system performance.

Yes desktop is way smoother..But There should be a fix for that too..
Thanks Anyways..for Helping me Out..:mrgreen:

---

### Post by John.Michael.Kane on 2006-10-26
Your welcome.

---

