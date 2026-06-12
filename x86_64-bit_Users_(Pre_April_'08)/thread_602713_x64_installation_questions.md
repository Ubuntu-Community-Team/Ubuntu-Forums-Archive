---
title: "x64 installation questions"
date: 2007-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by bartt on 2007-11-04
Noob here.. 
I got 7.10 up and running fine on an old Athlon system, so I thought I would install on my dev box (dual Opteron w/4gig ram). Install went ok, but Ubuntu only recognizes 2 gig ram and if I dare install the nvidia 6series drivers, I get an out of range error on my LCD panel. 
I was hoping that these fixes would help speed up this system, it is terribly slow at this point. 
Can anyone tell me explicitly how to: 
[INDENT]
Make it recognize the 4 gig of ram 
Get the right drivers for my video card working
[/INDENT]

TIA..

---

### Post by brianbarry on 2007-11-05
To my understanding the 7.10 kernel should access all 4 gigs so I'm no help there, however I can suggest you use envy to install the nvidia drivers.  [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
The program makes the installation painless and it works.

Brian

---

### Post by orthopod on 2007-11-05
Are you sure you're using the 64 bit version too?.  Somehow I thought I downloaded the 64bit version, and wound up with the 32 bit version.  Not sure if that will impose a memory limit, but you shuold check it anyway.

BTW, I'm using the 64 bit version 7.10, and my free -m results give this, so I know I should be able to access the full 4 gigs memory
free -m
             total       used       free     shared    buffers     cached
Mem:          3957       3277        680          0        365       1988
-/+ buffers/cache:        923       3033
Swap:         7852          0       7851

---

### Post by bartt on 2007-11-05
Thanks Guys-
This is helpful, 
I am pretty sure that I am running the 64 bit version, but perhaps not. I didn't really check, just assumed it was so. Your output at least showed a great deal more than 2gig, which is all that mine shows.

---

### Post by bartt on 2007-11-07
Thanks for questioning my install. Looks like the download that I got (which I'm certain was marked x64) was indeed a 32 bit version. I re-downloaded and installed once more and things look different. 
System monitor now states that it is using 3.9gig of ram Yeah!.
I did a little research and found references to Envy (thanks to Alberto), installed and ran that and my video card is performing much better. 
I hope that this info can help others...:KS

Bottom line here is that the original download was not what it was supposed to be, which caused me a lot of grief. Perhaps it would be a good idea to have the splash display either "32" or "64" and possibly "release" or "beta", so we could all be sure what we're installing.:confused:

---

### Post by dabl on 2007-11-07
It's pretty easy to type ```
uname -a
``` and see what you've got running.

:guitar:

---

### Post by bartt on 2007-11-07
Thanks. 
That is easy. But I still think that a bit more info on the splash screen would be nice.

---

### Post by John.Michael.Kane on 2007-11-07
> **bartt said:**
> Thanks. 
That is easy. But I still think that a bit more info on the splash screen would be nice.

You can also download 64bit iso's from this link [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607) This will assure you that you are getting 64bit.

---

### Post by Handssolow on 2007-11-08
How do I know I've got 64 bit running?
uname -r shows
2.6.22-14-generic

Looks like got 32 bit?

Some while back I thought too that I downloaded 64 bit Feisty onto a new Sata drive which I've since upgraded to Gutsy. I've continued to use 32 bit on an IDE drive but checking out today it looks like my 64 bit OS is 32 bit? Agree?

If I re-install with a fresh downloaded CD of 64 bit Gutsy on my Sata drive will it automatically overwrite the old software which is want I would want?

---

### Post by cjazz on 2007-11-08
> **Handssolow said:**
> How do I know I've got 64 bit running?
uname -r shows
2.6.22-14-generic

Looks like got 32 bit?



Try

```
uname -a
```

not "uname -r."

---

### Post by John.Michael.Kane on 2007-11-08
> **cjazz said:**
> Try

```
uname -a
```

not "uname -r."

Another option is to simply type.
```
arch
```
Which will out put arch type only.
```
x86_64
```

Anything other then x86_64 is shown then you are running a non 64bit OS.

---

### Post by Handssolow on 2007-11-08
> **SD-Plissken said:**
> Another option is to simply type.
```
arch
```
Which will out put arch type only.
```
x86_64
```

Anything other then x86_64 is shown then you are running a non 64bit OS.

Thanks folks. Looks like I've got 64 bit on my Sata drive?
uname -a 
Linux Handssolow-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
uname -m
x86_64

arch
reports command not found
Synaptic shows no arch packages loaded

comments?

---

### Post by John.Michael.Kane on 2007-11-08
> **Handssolow said:**
> Thanks folks. Looks like I've got 64 bit on my Sata drive?
uname -a 
Linux Handssolow-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
uname -m
x86_64

arch
reports command not found
Synaptic shows no arch packages loaded

comments?
uname -m seems to accomplish the same thing as the arch command did in previous versions.

Why the arch command was removed or change is unknown to me.

---

