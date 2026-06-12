---
title: "64-bit allowing 32-bit applications?"
date: 2008-11-28
forum: x86 64-bit Users
---

### Post by stunet on 2008-11-28
hi,

I use the 32-bit version as a dual-boot on my laptop and love it :)

I plan to dual-boot it onto my main system soon, but when i do it'll be the 64-bit version as i have 8GB of ram on that system.

question time, currently use vista x64 on the main system and I know the 64-bit versions of windows has wow64 which allow 32-bit applications to run perfectly under the 64-bit OS.

I also know that in both linux & windows, 64-bit is still new and things like drivers are a pain to get as well as software.

so my question is, if I go Ubuntu 64, will I encounter any driver issues or software problems? last i heard, most 64-bit linux distros only allow 64-bit things to run, which has my concerned.

hope someone can clear that up as I do wish to add Ubuntu to my main system and being able to use the full 8GB will be an added plus :)

much thanks.

---

### Post by jpeddicord on 2008-11-28
64-bit support isn't too new; it's been supported for quite a while. Most (most) drivers and software have 64-bit counterparts, even Flash does now. In general, it's a pretty easy experience.

And yes, you can still run a good amount of 32-bit applications on the 64-bit installation. The ia32-libs package has most of the 32-bit libraries needed to run many 32-bit apps.

---

### Post by ByteJuggler on 2008-11-28
It used to be the case that you could expect a few problems when installing 64 bit Linux (java, flash, et al), but most of the major issues have been resolved by now.  Also, although it was an option from fairly early on to install 32-bit versions of applications on a 64-bit system using a set of 32-bit libraries (somewhat akin to WoW 64), this did used to be a bit problematic in the past.  That too however is today nearly seamless and usually only requires installation of the required 32bit libraries.  

So, unless you're the type of person that can't tolerate the smallest of potential bumps in the road, I'd suggest you install the 64-bit Ubuntu going forward.  (But then, you probably shouldn't be installing Linux, if that's the case ;) )  

Anyway, for what it's worth, most of my machines are now 64-bit and I'm pretty much installing 64-bit by default these days, without too many problems as a result.  

What are the key things you need to have working?  Maybe we can confirm whether or not they work on 64-bit?

---

### Post by stunet on 2008-11-28
for now being a dual-boot, I plan to mostly use it for web server use. the basic LAMP stuff and whatever editor i can find that will work in linux for PHP 5.2 coding.

As I get more confortable, I may do more in linux, but somethings I do require windows(and vm is an option but dont want to get in too deep just yet)

bumps i am not concerned about, when i first put windows xp x64 on the machine i had BSOD for 2 months, so i'm not concerned about bumps, just wanted to know if 64-bit was catching up faster in linux than it seemed to in windows.

main reason I'm thinking of 64-bit is just to get the full use of my 8GB of ram, otherwise the 32-bit does the job fine(though 64-bit MySQL is nice)

---

### Post by jpeddicord on 2008-11-28
Your web services in 64-bit mode will shine; all of the standard server applications run excellently in 64-bits. :)

---

### Post by Hyper Tails on 2008-11-28
yea I need help installing avg or any good anti-virus because i have 64-bit intrepid and I can't install it because it says it 32-bit only :(

---

### Post by jpeddicord on 2008-11-28
> **Hyper Tails said:**
> yea I need help installing avg or any good anti-virus because i have 64-bit intrepid and I can't install it because it says it 32-bit only :(

You really don't need anti-virus at all unless you are using the machine to clear your network of Windows-based viruses (which won't run on Linux). But it's best to post a new thread if you are having issues with that.

---

### Post by stunet on 2008-11-28
> **jacobmp92 said:**
> Your web services in 64-bit mode will shine; all of the standard server applications run excellently in 64-bits. :)

awesome to know that :)

I already use MySQL 64-bit and like it :)

btw love the new release, 8.10 is really nice, no driver issues :D

---

