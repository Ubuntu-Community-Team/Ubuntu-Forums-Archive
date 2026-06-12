---
title: "Ubuntu 6.1 desktop: Dual Core support"
date: 2007-01-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by FractalBrain on 2007-01-12
Hey there everyone!!
I apologize in advance if this is a duplicate thread...lemme know.

I will be installing the Ubuntu 6.10 AMD 64 desktop version on a computer with a "dual core" ADM Athlon 64 X2 5200 processor.

I think I understand that the binary release of Ubuntu does not utilize multiprocessors...it runs, but using only one processor.  It seems that one compile a new kernal to utilize both.

So my question is this:  Does the Ubuntu 6.10 AMD64 desktop version have support for "Dual core" processors, or is this also treated as a multiprocessor system meaning that I must recompile?  If that question is too narrow, are there any thoughts on this particular topic?

Thanks, and I am excited to be part of the Linux world (moving from MacOS X)!!!!  

-FractalBrain

---

### Post by juyanith on 2007-01-12
It'll use both cpus (cores) right out of the box. No kernel compiling will be necessary.

---

### Post by FractalBrain on 2007-01-16
Hey,

I installed Ubuntu 6.10 (64 bit for and AMD64 X2 5200) and yes, like you say, both cores are being utilized with no recompiling necessary.  Yay!!

However, I have found the 64 bit version really isnt for me...no matter how much I try to make myself believe it is!  :-(.  Sadly I need Java and Wine really and fully working.  Sooooo, I will install Ubuntu 6.10 32 bit on this system and report back if it worked or not.  Ill try the 64 bit version in awhile (months-year).  -Fractalbrain

Brain Status:  Highly fractal and NOT working on my data analysis or manuscript

---

### Post by DavidGX on 2007-01-17
> **FractalBrain said:**
> Hey,

I installed Ubuntu 6.10 (64 bit for and AMD64 X2 5200) and yes, like you say, both cores are being utilized with no recompiling necessary.  Yay!!

However, I have found the 64 bit version really isnt for me...no matter how much I try to make myself believe it is!  :-(.  Sadly I need Java and Wine really and fully working.  Sooooo, I will install Ubuntu 6.10 32 bit on this system and report back if it worked or not.  Ill try the 64 bit version in awhile (months-year).  -Fractalbrain

Brain Status:  Highly fractal and NOT working on my data analysis or manuscript


No don't do that, use the 64bit version. Just install the 32 bit version of swiftfox and within that you can install the 32bit flash and java. Go here: [http://www.getautomatix.com/](http://www.getautomatix.com/) and you'll find a nifty little utility that will do it all for you.

---

### Post by FractalBrain on 2007-01-17
Hey DavidGX, 
Well, your "No don't do that..." must have been convincing :-).  I just figured out how to use R (statistical programming language) without the GUI (Java based), which was the biggest thing holding me back.  I was going to try MS Word in office (I only use the outline view), but I just installed LyX, which also will solve my Endnote biblographical referencing program problem.  Soooo, I think I will stick with it and enjoy my 64 bit operating system.  Ill keep Swiftfox in mind!  Thanks, Fractal Brain

FBStatus:  Off the deep end with no productivity.

---

### Post by enzomatrix on 2007-01-17
There is a Java Runtime package for AMD64:
[http://packages.ubuntu.com/edgy/libs/sun-java5-bin](http://packages.ubuntu.com/edgy/libs/sun-java5-bin)
[http://packages.ubuntu.com/edgy/libs/sun-java5-jre](http://packages.ubuntu.com/edgy/libs/sun-java5-jre)
And even a JDK:
[http://packages.ubuntu.com/edgy/devel/sun-java5-jdk](http://packages.ubuntu.com/edgy/devel/sun-java5-jdk)

---

### Post by FractalBrain on 2007-02-08
Annnd Im back.  Since I was last here I tried Suse 10.2 64 bit and wound up with Kubuntu 6.10 32 bit.  I found I lied to myself about being able to use lyx and R command line as a replacement...I do need them working :-(.  Apparently I like to exploit MS Word to its fullest and have become attached to some of the more advanced functions.  Anyway, if anyone is interested....

I installed Kubuntu 6.10 32 bit with the i386 kernel.  That doesnt offer SMP support.  I used apt-get to install the generic kernel (instead of i386).  The generic version had SMP support.  I saw that in another thread somewhere, but I dont remember where.  

One day I will become 64!  -Fractal

---

### Post by Kilz on 2007-02-08
> **FractalBrain said:**
> Annnd Im back.  Since I was last here I tried Suse 10.2 64 bit and wound up with Kubuntu 6.10 32 bit.  I found I lied to myself about being able to use lyx and R command line as a replacement...I do need them working :-(.  Apparently I like to exploit MS Word to its fullest and have become attached to some of the more advanced functions.  Anyway, if anyone is interested....

I installed Kubuntu 6.10 32 bit with the i386 kernel.  That doesnt offer SMP support.  I used apt-get to install the generic kernel (instead of i386).  The generic version had SMP support.  I saw that in another thread somewhere, but I dont remember where.  

One day I will become 64!  -Fractal

You already are. Your system is a corvette, a AMD 64 X2 5200. But you have chosen to go under the hood and pull out 4 of the spark plug wires in an attempt to burn cheap gas.

---

