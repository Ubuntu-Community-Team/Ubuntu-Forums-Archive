---
title: "Why does my 7.10 installation just freeeze?"
date: 2008-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by JGuritza on 2008-01-05
First off I am very new to Linux. 

I have the following:
Assus k8s-mx mother board with 2.21 gHz 64-bit AMD processor
1.5 GB DDR-SDRAM
160 GB SATA hard drive
Radeon 9550 256 MB video card

I have downloaded a copy of alternative (text) Ubuntu 7.10 using a bit torrent client. I verified the image. I have burned the image at 2X speed. I have checked the image using disk it self with the self test. I have tested the memory and no issues there. 

I used a 76 GB partition for Windows XP SP2 so I can still play Rome Total War and Combat Mission. The rest of the hard drive is just for Ubuntu.

I am able to install no problem. I loaded the brub boot loader and that works like a champ. I get to the login in screen and log in ok. Once I get to the desktop I have any where from 20 seconds to 2 minutes before the entire desktop locks up.

I know there has been issues in the past with the ATI Radeon 9550 cards and I have downloaded and printed large amount of information from this site to help make sure I have that setup properly but Ubuntu 7.10 does not stay unfrozen long enough for me to do anything.

Please help...

---

### Post by s_spiff on 2008-01-05
Well there have been several threads with respect to your issue, as it has been faced by quite a few.. Here are the links, try to follow them, may be you'll sort out your issue :D

[http://ubuntuforums.org/showthread.php?t=624538](http://ubuntuforums.org/showthread.php?t=624538)
[http://ubuntuforums.org/showthread.php?t=587905](http://ubuntuforums.org/showthread.php?t=587905)

Hopefully this will help you.

---

### Post by JGuritza on 2008-01-05
Thanks for the help...

I will give them a try...

---

### Post by Danyl on 2008-01-05
Sounds like a similar problem as to what I was experiencing.

I'm guessing you have 2 or 3 chips of RAM in your machine?

This may sound crazy but remove all of your RAM chips but one and try running 7.10 then.

I recently have discovered my PC (which has very similar specs to yours) will only run 7.10 "freeze free" with one piece of RAM. I don't know why, but it works.

---

### Post by MariusSilverwolf on 2008-01-06
> **Danyl said:**
> Sounds like a similar problem as to what I was experiencing.

I'm guessing you have 2 or 3 chips of RAM in your machine?

This may sound crazy but remove all of your RAM chips but one and try running 7.10 then.

I recently have discovered my PC (which has very similar specs to yours) will only run 7.10 "freeze free" with one piece of RAM. I don't know why, but it works.

That sounds more like a chipset control issue on the motherboard.  Unless you're using mixed RAM, with different clock cycles for each slot.  That would cause problems on any OS, I'm sure,

---

### Post by Kilz on 2008-01-06
Its also possible you have some bad ram. There is a memory test on the install menu of the install disk.

---

### Post by Danyl on 2008-01-07
> **MariusSilverwolf said:**
> That sounds more like a chipset control issue on the motherboard.  Unless you're using mixed RAM, with different clock cycles for each slot.  That would cause problems on any OS, I'm sure,

I'm not sure. I have tested the memory using a BIOS program that didn't find any errors (not that those programs are 100% accurate). Its possible it is my motherboard but I figured buying a new RAM chip was cheaper than getting a whole new motherboard! :P

Its strange though, because I got no problems whatsoever running the RAM under XP, only ever under Linux (including different distros, Fedora and Ubuntu).

Sorry to hijack your thread here JGuritza but can someone answer this question: is it possible XP isn't as memory intensive as Fedora and Ubuntu hence why these freezes occur? Its just weird for XP to be smooth sailing over Ubuntu!

---

### Post by njparton on 2008-01-07
Try uninstalling compiz (via synaptic remove anything with compiz in title) and then resetting the default gnome window manager to metacity.

This fixed all sorts of desktop issues for me :)

Compiz appears to be a very buggy gimick in my book.

---

### Post by JGuritza on 2008-01-07
> **Danyl said:**
> 
Sorry to hijack your thread here JGuritza but can someone answer this question: is it possible XP isn't as memory intensive as Fedora and Ubuntu hence why these freezes occur? Its just weird for XP to be smooth sailing over Ubuntu!

No worries about the hijack. I am going to try your suggestion about the memory chips. I do have two installed right now and I will just leave my 1 GB in and see what happens. I will agree with you that XP runs fine with both but if I have to go to 1 chip I guess I can survive if it works.

---

### Post by njparton on 2008-01-07
Don't ignore compiz either :wink:

---

### Post by JGuritza on 2008-01-07
I won't I need to get a stable desktop first. I get 20 to 45 seconds before everyhting locks up solid. If it is a memory conflict I can work woth that to start with.

Thanks!

---

### Post by Danyl on 2008-01-08
Yeah try the 1 gig stick, I'd be interested to see what happens (ie if its the same thing that happened to me).

I'm not sure if it is Compiz though that caused my freezes because I'm fairly certain I ran it without to see what would happen.

I'm thinking its more of a motherboard issue (but as I mentioned, can't justify getting a new one when RAM is cheaper and easier to replace).

---

### Post by JGuritza on 2008-01-08
> **Danyl said:**
> Yeah try the 1 gig stick, I'd be interested to see what happens (ie if its the same thing that happened to me).

I'm not sure if it is Compiz though that caused my freezes because I'm fairly certain I ran it without to see what would happen.

I'm thinking its more of a motherboard issue (but as I mentioned, can't justify getting a new one when RAM is cheaper and easier to replace).

Well this is what I did last night:

I tried to install 7.10 with just my 1 GB RAM and nothing but issues and freezes. 

Late last night I said to myself lets just try it with a 512 MB stick I had. The installation went fine and 7.10 is running like a top right now. I have not had any freezes or issues. I was even able to get my ATI 9550 Radeon drivers installed without issue.

This screams a memory issue to me. Does this mean if I try to re-install my 1 GB I am opening up Pandora's Box?

---

### Post by njparton on 2008-01-08
Try the 64 bit distro - I'm using that with 4GB RAM without any issues.

**edit**

oops just noticed that this was posted in the 64 bit section of the forum :redface:

Does your system pass memtest86+ with all RAM installed?

---

### Post by JGuritza on 2008-01-08
> **njparton said:**
> Try the 64 bit distro - I'm using that with 4GB RAM without any issues.

**edit**

oops just noticed that this was posted in the 64 bit section of the forum :redface:

Does your system pass memtest86+ with all RAM installed?

Yes it does. I did that first even before installing. It passed. I guess that is why I am a little perplexed. I left for work this morning after running 7.10 all night. I will see what happens when I get home.

---

### Post by njparton on 2008-01-08
Have you tried my compiz suggestion yet?

---

### Post by JGuritza on 2008-01-08
> **njparton said:**
> Have you tried my compiz suggestion yet?

I will be honest I have not. I was shocked late last night to have a working installation that was not freezing I went to bed. This morning I checked it for 10 seconds to make sure it was still alive and not frozen. Tonight when I get home from work will be the time I get to sit down and see if everything works. I have printed out your post for Compiz. Thank you so much for the advice. That is on the list to investigate tonight.

---

### Post by njparton on 2008-01-08
Search the threads I've posted in recently that involve gnome slowing down - they will tell you how to assign metacity as the default window manager after you've uninstalled compiz.

Not doing this will give you further issues (not critical as such though e.g. missing title bars).

To start with in a terminal you can do the following to cure but it's not permanent:

```

metacity --replace

```

---

### Post by hotbit on 2008-01-08
Hi all, for the last few weeks I was fighting with my freezing system, finally reinstalled system twice and... in 1-5 minutes it was frozen after every reboot again and again!
I checked memory, even hoovered inside from dust ... nothing.
Finally for about 6 hours there was no freeze! It looks as **removing one of the two 512 Mb RAM I have had helped**!

---

### Post by 6568912 on 2008-01-08
maybe you just should boot in safe mode?

---

### Post by Danyl on 2008-01-08
> **JGuritza said:**
> Well this is what I did last night:

I tried to install 7.10 with just my 1 GB RAM and nothing but issues and freezes. 

Late last night I said to myself lets just try it with a 512 MB stick I had. The installation went fine and 7.10 is running like a top right now. I have not had any freezes or issues. I was even able to get my ATI 9550 Radeon drivers installed without issue.

This screams a memory issue to me. Does this mean if I try to re-install my 1 GB I am opening up Pandora's Box?

Weird huh? FYI, when I was getting freezes I had 2x 512mb chips running. It ran smoothly with just one 512mb chip but I decided I still wanted a gig of memory so I bought a new 1gig stick and just have that installed at the moment.

I however am no longer experiencing freezes with my 1gig stick so its a little different to your end result (as you were still getting freezes with a 1 gig stick) but at least its running now and you're somewhere closer to resolving the issue! :P

I wonder what the bigger picture is here? Ie does 7.10 not like certain types of RAM, if so which ones? I'm at a loss (and don't really know alot about the specifics of RAM anyway).

---

### Post by Danyl on 2008-01-08
> **hotbit said:**
> Hi all, for the last few weeks I was fighting with my freezing system, finally reinstalled system twice and... in 1-5 minutes it was frozen after every reboot again and again!
I checked memory, even hoovered inside from dust ... nothing.
Finally for about 6 hours there was no freeze! It looks as **removing one of the two 512 Mb RAM I have had helped**!

lol my exact scenario! :P Don't you just hate hardware issues?!

I would love to try running 7.10 with a new motherboard and my same RAM to see what would happen but alas, I can't justify spending $200-$300 on that just for experimental purposes! (hence the cheaper option of buying a single gig stick of RAM).

---

### Post by njparton on 2008-01-09
I don't want to appear to be gloating, but I run an ubuntu desktop with 4 x PC2-6400 1gig sticks in a 680i motherboard no problems using the 64 bit distro.

---

### Post by JGuritza on 2008-01-09
> **Danyl said:**
> Weird huh? FYI, when I was getting freezes I had 2x 512mb chips running. It ran smoothly with just one 512mb chip but I decided I still wanted a gig of memory so I bought a new 1gig stick and just have that installed at the moment.

I however am no longer experiencing freezes with my 1gig stick so its a little different to your end result (as you were still getting freezes with a 1 gig stick) but at least its running now and you're somewhere closer to resolving the issue! :P

I wonder what the bigger picture is here? Ie does 7.10 not like certain types of RAM, if so which ones? I'm at a loss (and don't really know alot about the specifics of RAM anyway).

I was going to try and reinstall just the 1 GB tonight and see what happens. I would love to get a full 2 GB the max my motherboard can handle but I am understandablly concerned to try.

---

### Post by JGuritza on 2008-01-09
> **njparton said:**
> Search the threads I've posted in recently that involve gnome slowing down - they will tell you how to assign metacity as the default window manager after you've uninstalled compiz.

Not doing this will give you further issues (not critical as such though e.g. missing title bars).

To start with in a terminal you can do the following to cure but it's not permanent:

```

metacity --replace

```

Thanks for all the help. Last night through this morning and everything is running smoothly...

---

### Post by njparton on 2008-01-09
No worries, you can replace compiz with metacity as the default window manager by using gconf-editor.

The option resides somewhere in there...

---

### Post by Danyl on 2008-01-09
> **JGuritza said:**
> Thanks for all the help. Last night through this morning and everything is running smoothly...

So how much RAM are you running successfully now?

---

### Post by JGuritza on 2008-01-09
> **Danyl said:**
> So how much RAM are you running successfully now?

I have been extremely successful running 512 MB with no issues at all. When I just install a single 1 GB everything locks up. The windows XP has no problem but I have nothing but issues in Ubuntu any version.I have tried several combinations but it looks like the 1 GB is a no go with my current configuration.

To me it is a simple hardware conflict. Maybe another type of ram would work. It is a little perplexing because I am using a brand of memory recommended by Asus makers of my motherboard.

---

### Post by wjgeorge on 2008-01-10
i had a problem using hdmi

used a vga adapter on the cable . Works great

---

