---
title: "Installing latest IE Explorer in Wine"
date: 2008-08-07
forum: Wine
---

### Post by wordman2 on 2008-08-07
Anyone done this? Hold my hand please!

---

### Post by ooobuntooo on 2008-08-07
> **wordman2 said:**
> Anyone done this? Hold my hand please!

IEs4Linux is the easiest way of installation. I'm not sure there is IE7 support.

What's wrong with Firefox?

---

### Post by sharks on 2008-08-07
why u want to use IE? FF is better than ie in many ways.

---

### Post by tuxxy on 2008-08-07
FF is better than IE in windows :lolflag:

---

### Post by ooobuntooo on 2008-08-08
IEs4Linux is only for web developers! Use Firefox!

If you use IE in Linux, you will cause a miscount in the census, a miscount!!

---

### Post by gjoellee on 2008-08-08
no it doesn't support IE7 yet, but maybe v.3 will, it is like v.2.99 now so it should not be long before

---

### Post by siman on 2008-08-08
there is ie7 support, but's is beta and ie7 will very likly crash often if it starts at all.

just download the usual package and click on "advanced options" or smth, when installing - there is an ie7 checkbox.

---

### Post by tuxxy on 2008-08-08
You know you could change your browsers identity to IE7 from in firefox if you wanted, in firefox download the plugin **user agent switcher** and change the settings in the tools menu

---

### Post by ooobuntooo on 2008-08-08
> **tuxxy said:**
> You know you could change your browsers identity to IE7 from in firefox if you wanted, in firefox download the plugin **user agent switcher** and change the settings in the tools menu

I meant it will display the OS as windows and not Linux.
Hence: if every Linux user used IE then the Linux marketshare will drop and the M$ fanboys will gloat!

---

### Post by tuxxy on 2008-08-08
I meant switch the identity to IE7 for his specific site he needs to access in IE7, this may save him a lot of time as its only a plugin.

---

### Post by dlmoak on 2008-08-08
There ***are*** applications out there that require IE6, that will not run on ie4linux, and for which using the Firefox agent switcher has no effect.

---

### Post by ooobuntooo on 2008-08-08
> **dlmoak said:**
> There ***are*** applications out there that require IE6, that will not run on ie4linux, and for which using the Firefox agent switcher has no effect.

What are these applications? I have heard about them but I have never encountered any!

---

### Post by oldsoundguy on 2008-08-08
Even tho MS now can only "brag" a 51% (and shrinking every month) usage for IE (of any kind), there are still sites in the dark ages and that ONLY use IE.  (Virgin Mobil's FINAL page on the activation site requires Active X scripting, for instance!)

Hence, there IS a need to have a version of IE on your Linux box if you do not have access to a Windows machine.

And IEs4Linux does not work .. no scripting support for one.

Maybe installing in WINE would do it?  Been going through this with a friend and we have yet to find a solution that is WINDOWS FREE!

---

### Post by dlmoak on 2008-08-08
> **ooobuntooo said:**
> What are these applications? 

My office, a medical office, is run using an intranet application that is browser based.  So far, I have not been able to run it outside of Windows using IE6.

---

### Post by ooobuntooo on 2008-08-08
IE6 works on Crossover Linux 7.

---

### Post by dlmoak on 2008-08-08
> **ooobuntooo said:**
> IE6 works on Crossover Linux 7.

Yes, I wasn't clear.  I can get IE6 to run on Linux, but this program requires that it actually be running under Windows because it installs some features of its own which only run under Windows.

---

### Post by Grandma_DOG on 2008-08-08
I run a small data company in Austin.  I have been forced to install ie4linux because some proprietary imaging websites use Alternatiff plugins to display their data.  Alternatiff does not run in Firefox on Linux.  There is no other way around the problem that we haven't tried and failed at.  The vendor must protect his product, Alternatiff was the way for him to go.  We must use it, so Bam, we have to install friggin ie4linux.



> **ooobuntooo said:**
> What are these applications? I have heard about them but I have never encountered any!

---

### Post by Inane_Asylum on 2008-08-09
Also, Netflix instant watch requires IE.  It won't even run on Firefox on a windoze machine.  There was a FF workaround involving an "IETab" plugin, but no worky on Linux.

And I'm not buying that $100 Netflix box for my TV, either :mad:.

---

### Post by oldsoundguy on 2008-08-09
IE can run from a Windows install in Virtual PC .. but all of the protection required to run Windows as a stand alone has to be installed and kept up to date, or you may trash the virtual PC and have to re install. (The trashing would not spread, just that to keep it working you have to do the same crap as you would as if you dual booted or had Windows on a separate box!)  

A friend just did the above. Here is a link to a desktop!

[http://soloact-the-bard.deviantart.com/art/Virtual-PCs-Are-Great-94295587](http://soloact-the-bard.deviantart.com/art/Virtual-PCs-Are-Great-94295587)

---

### Post by Wolfhere on 2008-11-29
Awesome!
Thanks

---

### Post by flameproof on 2009-01-28
I am trying IE on 8.10 AM64 too and run into problems.

I must have IE for online banking, try yourself if you get to the actual login form of corporate banking:

[http://www.shacombank.com.hk/scb/en_index.html](http://www.shacombank.com.hk/scb/en_index.html)

I tried WINE + ies4linux, but I can't get the Java to install in IE. IE itself runs fine though.

I don't really understand VirtualBox. Can I just run IE from VB, or do need to install Win in any form via VB?

If I need Win, I have an old Win98 from an obsolete PC...

---

### Post by Inane_Asylum on 2009-01-28
Think of VirtualBox as a little computer inside your computer.  You'll have to install Windows on that little computer.  You can't install IE on a computer without having Windows.

The problem is that VirtualBox doesn't work well **at all** with Windows 98.  It's optomized for 2000/XP or later (not even sure about 2000...).  I tried running 98 on VB so I could play some of my pre-XP games, and it ***dragged.***

My only options for required-IE sites (netflix IW, bank sites) is dual-boot with XP or VB with XP.  There just isn't enough compatibility between later renditions of IE and WINE yet...believe me, I know how frustrating it is.

---

### Post by flameproof on 2009-01-29
> **Inane_Asylum said:**
> The problem is that VirtualBox doesn't work well **at all** with Windows 98.

Win 98 did install in VirtualBox with no problem. I have no net connection via IE yet. Of course, if banking will work is another question....

> My only options for required-IE sites (netflix IW, bank sites) is dual-boot with XP or VB with XP.  There just isn't enough compatibility between later renditions of IE and WINE yet...believe me, I know how frustrating it is.

To buy Xp to run it in Linux sounds silly to me. If I had a spare Xp I would certainly not use Linux at all. The whole idea for Linux for me is to save money on O/S and confront the many limitations linux has.

Ok, I have a free Win98, but that will not run on modern hardware standalone. Compare to Win98 I would keep Linux, put compare to Xp not.

---

### Post by Inane_Asylum on 2009-01-30
I agree completely that it's silly to buy XP to run on Linux.  I happened to have a few legit copies lying around, so it wasn't a big issue for me.  What's sad is that many companies forget that anything but Windows + IE exists.  I'd imagine Mac users have similar problems.  It may be silly, but as far as I know, it's the only option for many sites.  I also picked up Linux to avoid many of the headaches associated with Windows, only to find that now, I can't live without either.  At least until companies figure out that other operating systems exist...

Windows 98 **installed** easily enough for me, but running it was a different story.  It drug worse than Vista did on the same computer...

---

### Post by SunnyRabbiera on 2009-01-30
you could try installing IE6 in wine, it can be found on the net if you know where to look.

---

### Post by flameproof on 2009-01-31
I got a Xp license now free and installed Xp in the VirtualBox. It installed with no flaw. IE is running, and I can finally get to my banking site.

---

### Post by Inane_Asylum on 2009-01-31
Good to hear.  I'll keep my eyes out for any pure Linux resolutions that may pop up for this type of problem.  Sad that it's something we're going to have to live with at least for a while in this Windows-dependant world...

---

### Post by chudder on 2009-01-31
I've tried installing IEs4Linux but the script runs partially and then it quits without ever finishing the installation.


What should I do?

---

