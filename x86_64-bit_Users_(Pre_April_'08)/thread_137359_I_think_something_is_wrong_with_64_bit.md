---
title: "I think something is wrong with 64 bit"
date: 2006-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by opensourcerocks on 2006-02-27
I have just tried to install 5.10 breezy and 6.04 flight cd 4 of kubuntu.
Neither has worked with my system because KDE never launchs.
Should I try the x86 version because I am still very new to linux.
I heard that you don't get very good preformance with out a 64 bit os.

Computer:
AMD 3700+ 
Gigabyte Motherboard
1 Gig of Kingston value ram
Shappier ATI X700
250gig hd

---

### Post by Segovia on 2006-03-01
[QUOTE=opensourcerocks]Should I try the x86 version because I am still very new to linux.  I heard that you don't get very good preformance with out a 64 bit os.[/QUOTE]
I think you will find GNU/Linux quite enough challenge at the start... even without worrying about the problems (and there are quite a few) with getting things working flawlessly with 64bit.

You should remember also that, in most cases, 32bit apps will actually run SLOWER on a 64bit OS.

---

### Post by Hygelac on 2006-03-02
> You should remember also that, in most cases, 32bit apps will actually run SLOWER on a 64bit OS.
:shock: 

I never knew that!  Do you have more information on this?  Specifically, what do you mean by a "32bit app" (something run with chroot, a 32bit program only crudely modified to run on a 64bit system, etc...)?  I run 64bit but only because I assumed it would be faster and that everything will be that way soon; not because of any real technical knowledge...

---

### Post by gingermark on 2006-03-02
[QUOTE=opensourcerocks]I have just tried to install 5.10 breezy and 6.04 flight cd 4 of kubuntu.
Neither has worked with my system because KDE never launchs.
Should I try the x86 version because I am still very new to linux.
I heard that you don't get very good preformance with out a 64 bit os.
[/QUOTE]

If you're new try the 32-bit version - getting non-free (ie not open source) stuff working, especially related to multimedia, will be far easier.

When you say KDE doesn't load, do you mean you just end up at a command line (black screen with something like 'username@computername:- $ ') ? If so you're having a problem with your graphics card.

Type 'sudo dpkg-reconfigure xserver-xorg', press enter, then enter your password. You will be guided though a part of the settup again. Try selecting the 'vesa' driver - this won't look great, but should get you into kde, and you can then set about installing the proper non-free driver.

---

### Post by Segovia on 2006-03-02
[QUOTE=Hygelac]I never knew that!  Do you have more information on this?  Specifically, what do you mean by a "32bit app" (something run with chroot, a 32bit program only crudely modified to run on a 64bit system, etc...)?[/QUOTE]
Well yea, that's the thing.  There are very few applications out right now that have been built from the start to take advantage of 64bit hardware/software.  Basically just recompiling something so that it'll run in 64bit is not going to give some magical speed increase.  And running 32bit applications (using emulation) on a 64bit OS wont help either.  At least that's the way I understand it.

I have not seen any benchmarks yet that show ANY apps (that a home desktop would be running) benefitting from a 64-bit OS. 

BTW, I have very little technical knowledge myself on the topic.  I'm just basing my opinions on what I've read, and benchmarks I've seen.  These are just some links I just found on Google.  I'm sure you'll find many more if you research it some.

[http://www.firingsquad.com/hardware/far_cry_64-bit/](http://www.firingsquad.com/hardware/far_cry_64-bit/)
[http://answers.google.com/answers/threadview?id=514147](http://answers.google.com/answers/threadview?id=514147)
[http://www.osnews.com/story.php?news_id=5768](http://www.osnews.com/story.php?news_id=5768)

---

### Post by Hygelac on 2006-03-02
Thanks for those links Segovia.  I'll have to look into this more when I can find the time...

---

### Post by nalmeth on 2006-03-02
> You should remember also that, in most cases, 32bit apps will actually run SLOWER on a 64bit OS.

Not at all for me.

I have an intel64 bit processor, and installed the 64bit kernel first, because I thought naively that running anything else would damage my card or something...

Everything worked good in the 64-bit environment, after I set up a 32-bit chroot environment for all the non-64 bit apps. All the 32-bit apps ran awesome, without a hitch. It was a learning experience, and an easy one at that, for the chroot was done with a walkthrough, stepbystep, copying and pasting commands. Thats it.

The only reason I went to the 32-bit kernel, is that for some reason the 64-bit kernel wouldn't setup my graphics card. Also, I learned it isn't dangerous.. :oops: 

Everything runs GREAT on this 32-bit kernel. Don't be easily discouraged against trying out ubuntu. 

> I'm sure you'll find many more if you research it some.

I'm sure you will too.. But you'll learn in no better way than personal experience. If you have the time, try the 64-bit kernel, and follow the howto here:
[http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit](http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit)
its easier than it looks, and by the end you'll execute your 32-bit apps normally. if 64-bit isn't working out, just use the i386 kernel. Like I said, it ended up working out better for me. 

Good luck, and use the forum for any help

---

### Post by rplantz on 2006-03-12
There is a good article at arstechnica about 64- versus 32-bit. The author points out in his conclusion that the primary benefit in the case of the AMD and Intel x86-64 CPUs is the additional _number_ of registers rather than their size. The conclusion is at [http://arstechnica.com/cpu/03q1/x86-64/x86-64-5.html](http://arstechnica.com/cpu/03q1/x86-64/x86-64-5.html).

Compilers attempt to use registers for computations because they can be accessed much, much faster than memory. (Registers are memory that is located within the CPU.) The x86-32 architecture does not have many general registers compared to more modern architectures. It has 8 each of general purpose, floating point, and SIMD registers. The x86-64 doubles the number of general purpose and SIMD registers to 16 each. This is still very few compared to others. (For example, Intel's Itanium has 128 64-bit general purpose registers and 128 80-bit floating point registers.) But doubling a small number should help quite a bit.

---

