---
title: "[SOLVED] The Distro For Intel 64bit CPU"
date: 2007-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by AlistairH on 2007-03-14
I have a new machine with, supposedly, an Intel Pentium 4 531 HT 3.0Gz processor. My understanding, and what I'm being told by the supplier, is that this is a 64bit processor.

I believe the correct Ubuntu distro is ubuntu-6.10-desktop-amd64.iso. even though this is an Intel processor and not an AMD one as the distro name implies.

That being the case, it appears that my cpu isn't 64bit as the Live CD halts on boot up with a message saying that this machine is not an AMD64.

I just wanted to check first of all if I'm using the correct distro.

My supplier says that this processor uses Physical Address Extension which makes it 64bit. I understood PAE to be a means of allowing RAM greater than 4GB to be addressed whereas the 64bit of a processor refers to the size of the internal registries of the cpu giving it greater computational power as it can handle, theoretically, twice as much data per computing cycle than a 32bit cpu can.

Am I barking up the wrong tree or have I been misled when purchasing and not bought what I thought I had?

Ali

---

### Post by kaffelars on 2007-03-14
Have you looked around your BIOS?

I have a Pentium D 920, and on my computer I can enable and disable 64-bit support in BIOS.

---

### Post by colo on 2007-03-14
PAE is a technology allowing 32bit Applications and OSes do address more than a theoretical 32bit maximum of 4GB memory. Applications have to be specifically adapted to make use of PAE though.

x86_64 (often called amd64 due to historical reasons) completely does away with memory limit as low as 4GB, and does not suffer from any of PAE's disadvantages.

Intel's implementation of x86_64, which they licensed from AMD, is called EM64T. You can check your processor's data sheet if it's supported.

Anyway, EM64T on Netburst is quite a bit slower than IA-32. You're better off with a distribution optimized for i686, like, for instance, Archlinux.

---

### Post by John.Michael.Kane on 2007-03-14
The specifications on that cpu state that it supports EM64T. 

You should be fine installing ubuntu 64,however. with out knowing your full system specifications ie: mainboard/gpu make model as well as any errors given during the install it will hard to give help.

---

### Post by Kilz on 2007-03-14
> **colo said:**
> Anyway, EM64T on Netburst is quite a bit slower than IA-32. You're better off with a distribution optimized for i686, like, for instance, Archlinux.

Do you have a link to any data that confirms this?

---

### Post by AlistairH on 2007-03-14
I downloaded an indentifying utility directly from the Intel site. Running under WinXP (32bit version) it reports the following...

==========
Intel Pentium 4 CPU 530 3.00GHz

Reported Speed: 3.0GHz
Reported System Bus: 800MHz
L2 Cache Memory: 1MB

Supported Advanced Intel Processor Technologies...
Virtualisation: No
Hyper-Threading: Yes
Extended Memory 64T: No      <<==***

Intel(R) Extended Memory 64 Technology (Intel(R) EM64T) requires a computer system with a processor, chipset, BIOS, OS, device drivers and applications enabled for Intel(R) EM64T.  Performance will vary depending on your hardware and software configurations.  Intel EM64T enabled OS, BIOS, device drivers and applications may not be available.  Check with your vendor for more information.
==========

From this it doesn't appear that 64bit is enabled, yet, as indicated by the above paragraph, is EM64T being reported as not supported because the utility I'm using is running under a 32bit version of XP? As a result, I'm not sure if I'm any further forward as a question remains over the cpu.

I've been into the BIOS but I cannot find any setting that would allow me to enable/disable 64bit. Nor can I find anything in the mobo manual. The mobo is a Foxconn SiS 661Fx7MJ/661GX7MJ and uses Phoenix AwardBIOS V6.00PG software.

When booting from the 64bit Ubuntu distro, there are no errors displayed on the screen other than.."This is not an amd64 machine. Please install the i386 distribution of Ubuntu" which appears after the kernel has loaded from the live CD. The screen goes blank and displays the message.

Any other suggestions folks?

Ali

---

### Post by John.Michael.Kane on 2007-03-14
In your first post you id your cpu as a 531 which as you can see from the links support 
the EM64T instruction set.

[http://processorfinder.intel.com/details.aspx?sspec=sl8pq](http://processorfinder.intel.com/details.aspx?sspec=sl8pq)
[http://processorfinder.intel.com/details.aspx?sSpec=SL8HZ](http://processorfinder.intel.com/details.aspx?sSpec=SL8HZ)

However.
Your specs are showing you have an Intel Pentium 4 Processor 530

[http://processorfinder.intel.com/details.aspx?sSpec=SL7J6](http://processorfinder.intel.com/details.aspx?sSpec=SL7J6)
[http://processorfinder.intel.com/details.aspx?sSpec=SL7KK](http://processorfinder.intel.com/details.aspx?sSpec=SL7KK)

This cpu does not have the EM64T instruction set. if the machine was sold to you as having a 531 with the EM64T instruction set. it would seem you have been sold the wrong spec machine or the info was not made clear to you.

---

### Post by AlistairH on 2007-03-14
Well tracked down SD. It seems that I've bought something that's not quite as advertised. That'll will serve me right for buying from an eBay 'Powerseller'

I shall send them all my evidence I have collected with the forums' help and see what they have to say for themselves.

Cheers

Ali

---

### Post by John.Michael.Kane on 2007-03-14
No problem. hope it works out.

---

### Post by colo on 2007-03-14
> **Kilz said:**
> Do you have a link to any data that confirms this?
I quickly google up a series of benchmarks shocasing how EM64T fails to deliver a speed-boost comparable to AMD's K8.
[http://www.pcstats.com/articleview.cfm?articleid=1838&page=10](http://www.pcstats.com/articleview.cfm?articleid=1838&page=10)

When I've done research for the company I work for a few months ago, I happened to stumble over rather disastrous benchmarks relevant for server-tasks (MySQL, Apache2) - I can't seem to dig those up just now, though...

---

