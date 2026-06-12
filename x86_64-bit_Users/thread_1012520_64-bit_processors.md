---
title: "64-bit processors"
date: 2008-12-15
forum: x86 64-bit Users
---

### Post by squelchy451 on 2008-12-15
hi.

I am thinking of getting a Laptop.
When I use Ubuntu, i see that many apps (like Opera Browser and WINE) are not available for 64-bit processors. 

Is there a way around this?
Are all AMD processors 64-bit?
Which Intel processors are 64-bit and which are not? (I'm considering Intel Atom, Pentium Dual Core, and Core 2 Duo).
Do those Intel CPU's have the pesky 64-bit problems?

Thanks

---

### Post by Arup on 2008-12-15
Using Opera 9.62x64, you have to download it from Opera site, sadly its no longer in the Ubuntu repos for some strange reason. Wine is in the repos, just add the medibuntu repos. Almost everything in x32 Ubuntu is there in x64 Ubuntu.

---

### Post by Sef on 2008-12-15
>  When I use Ubuntu, i see that many apps (like Opera Browser and WINE) are not available for 64-bit processors. 

Opera has a 64-bit browser.

>  Do those Intel CPU's have the pesky 64-bit problems?

I have an Intel 64-bit processor, and it works just great with Ubuntu.

---

### Post by omegamike3 on 2008-12-15
Most any processor you get today is going to be 64bit. It is generally more a matter of whether or not the OS you install will take advantage of that functionality. As for worrying about the compatibility of programs... There really isn't anything you can't do on a 64bit system that you can do on a 32bit one. You might run into a hiccup here or there, same way you might installing any software, but that's about it. The biggest problem you may run into, assuming you're not doing anything terribly fanciful is having to install some 32bit libraries to get something running. Now that 64bit Flash is available, the very beginnings of 64bit Wine have been announced AND, as I just read on Slashdot, a 64bit Java plugin for browsers all of the "typical" headaches are going away. Not that Wine is really a headache on 64bit machines anyways... Really, my point is that you won't notice any difference except for the speed boots (where available) and other small things, like 3.5GB of RAM recognition without things like PAE. Might as well get every penny's worth out of your hardware, that's why you're running Linux anyhow, right? :P

---

### Post by jespdj on 2008-12-16
> **squelchy451 said:**
> Are all AMD processors 64-bit?
Which Intel processors are 64-bit and which are not? (I'm considering Intel Atom, Pentium Dual Core, and Core 2 Duo).
Do those Intel CPU's have the pesky 64-bit problems?

See [List of Intel microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_microprocessors) and look under 64-bit processors: Intel64.

What "pesky 64-bit problems"? I've never heard of any special 64-bit problems with Intel processors.

Note that 32-bit software also runs on 64-bit Ubuntu.

---

### Post by mattman85 on 2008-12-17
> **squelchy451 said:**
> When I use Ubuntu, i see that many apps (like Opera Browser and WINE) are not available for 64-bit processors. 

I just saw this the other day, and I thought I would make mention of it..

[Wine64]("http://wiki.winehq.org/Wine64")

I can't wait til it actually is functional, but until it is, they have a link ([Wine on 64-bit]("http://wiki.winehq.org/WineOn64bit")) that explains how to set up 32-bit Wine on a 64-bit processor.  I've done this, and it works great!

---

### Post by revidnus on 2008-12-17
I would not get a laptop with an AMD 64 bit processor right now as there is a boot up problem with those processors and Ubuntu 8.10 .
Mostly its the HP laptops. I have a HP 2007 Pavillion 9610us multimedia and you have to hold any key down to get it to boot up. That or wait untill the bar freezes and plug in the power pack / charger. Once its up and running I have no problem.
Philip
:p

---

### Post by Arup on 2008-12-17
No boot up issues on my Pana Toughbook with Intel Centrino, also installed Ubuntu Intrepid x64 on my friend's Toshiba with AMD dual core x64. The system boots fine and has been running very nice actually.

---

### Post by Kilz on 2008-12-18
> **mattman85 said:**
> I just saw this the other day, and I thought I would make mention of it..

[Wine64]("http://wiki.winehq.org/Wine64")

I can't wait til it actually is functional, but until it is, they have a link ([Wine on 64-bit]("http://wiki.winehq.org/WineOn64bit")) that explains how to set up 32-bit Wine on a 64-bit processor.  I've done this, and it works great!

1. Wine64 = emulates 64bit windows and allows you to run 64bit windows applications. But since there are few if any 64bit windows applications, its a waste of time.

Wine has been in the repositories since Gutsy. No need for hacks.

---

### Post by Robstarusa on 2008-12-18
> **jespdj said:**
> See [List of Intel microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_microprocessors) and look under 64-bit processors: Intel64.

What "pesky 64-bit problems"? I've never heard of any special 64-bit problems with Intel processors.

Note that 32-bit software also runs on 64-bit Ubuntu.

Here is a [pesky one!]("http://ubuntuforums.org/showthread.php?t=1014386&highlight=atom")

---

### Post by jespdj on 2008-12-18
> **Robstarusa said:**
> Here is a [pesky one!]("http://ubuntuforums.org/showthread.php?t=1014386&highlight=atom")
And how do you know that that problem is because of the 64-bit processor or the 64-bit version of Ubuntu? It could be something completely different related to some other piece of hardware in the computer.

---

### Post by Robstarusa on 2008-12-18
> **jespdj said:**
> And how do you know that that problem is because of the 64-bit processor or the 64-bit version of Ubuntu? It could be something completely different related to some other piece of hardware in the computer.

Considering i386 works fine on it......?  Wouldn't that rule out hardware problems?

It's a VERY simple setup.  Motherboard + cpu are integrated.  1 SDHC card, 1 CF card. 1 * 2G ram chip.  That composes the entire box.

Centos i386 also installs on it just fine.  I haven't tried x86_64 (CentOS) yet.

---

### Post by Yellow Pasque on 2008-12-18
> Considering i386 works fine on it......? Wouldn't that rule out hardware problems?
Your CPU might support it, but for Intel CPU's to do x86_64, the mobo and BIOS need to support it too. Form Intel's site:
> 64-bit computing on Intel® architecture requires a computer system with a processor, chipset, BIOS, operating system, device drivers and applications enabled for Intel® 64 architecture. Processors will not operate (including 32-bit operation) without an Intel 64 architecture-enabled BIOS. Performance will vary depending on your hardware and software configurations. Consult with your system vendor for more information

EDIT: I just re-read the above quote and realized it's probably not a BIOS issue. Also, did you verify your CD .iso, burn at a low speed, and do the media self-check before installing?

---

### Post by sloggerkhan on 2008-12-18
I haven't had any trouble using ubuntu 64... most everything seems to work.

---

### Post by phlembob on 2008-12-18
Hi):P
1.  64 bit processors aren't a real problem except in battery life of your laptop.
2.  You can read these forums and download the 32 bit libs for all 32 bit programs that may have a problem with the 64 bit libs.  Yes, they can be operated in the Hardy 8.04.1 LTS under the 64 bit OS.
3.  If I were you, I would not play with 8.10 Intrepid att.  Hardy is far much more reliable.
4.  I use Firefox --- in Hardy I have only heard praises for all Linux based browsers.
5. For any 64 bit processor (AMD 64 bit here writing) you shouldn't have too many problems that can't be solved.

Go for it  :guitar:

---

### Post by stchman on 2008-12-18
> **squelchy451 said:**
> hi.

I am thinking of getting a Laptop.
When I use Ubuntu, i see that many apps (like Opera Browser and WINE) are not available for 64-bit processors. 

Is there a way around this?
Are all AMD processors 64-bit?
Which Intel processors are 64-bit and which are not? (I'm considering Intel Atom, Pentium Dual Core, and Core 2 Duo).
Do those Intel CPU's have the pesky 64-bit problems?

Thanks

WINE installs and functions on Ubuntu 64 bit.  Pretty much everything in the repos works on 64 bit except SUN Java plugin.  Use Icedtea for the Java plugin for 64 bit.

---

### Post by ndale686738 on 2008-12-18
Intrepid has far better support for my Inspiron 1521 X64 laptop than hardy did. in fact i went back to Gutsy after only 2 days of messing with hardy. 

With the exception of a few bluetooth issues which i posted the resolution i came up with here [http://ubuntuforums.org/showthread.php?t=964139&page=17](http://ubuntuforums.org/showthread.php?t=964139&page=17) i have not had many issues. 

as the "main" issues with x64 are usually web view-ability i thought i would mention that the flash x64 alpha has been very good for me as well as the icedtea6-plugin for java. i have also been highly successful with x32 web browsers running official flash and java releases. 

I have run numerous X64 distros and ubuntu releases and have yet to not resolve an issue. I will agree that X32 is a little simpler but only because native x64 support is not available in all areas yet. There is a large x64 community that will help you, as it is for the Linux community as a whole. 

happy X64ing

---

### Post by Kilz on 2008-12-19
> **Robstarusa said:**
> Here is a [pesky one!]("http://ubuntuforums.org/showthread.php?t=1014386&highlight=atom")

[It looks like that hardware just isnt supported well. ]("http://ubuntuforums.org/showthread.php?t=863767&highlight=atom+230+kernel+panic") Both the 32bit version and the 64bit have issues. So this doesnt look like a "pesky 64bit problem".

---

### Post by Erlander on 2008-12-19
I had to do a fresh install of Ubuntu a couple of weeks ago.  So I set up separate partitions for 32 bit and 64 bit 8.10 Intrepid.  I hadn't used 64 bit until then so I wanted to be sure.

After about a week I found that everything I am used to doing in 32 bit could be done in 64 bit so I deleted the 32 bit partitions and edited my grub boot up list.

64 bit only now and no regrets.  All my memory is recognised and video work goes just as well.

System specs below.

Rob

---

