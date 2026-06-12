---
title: "64-bit wine and WoW"
date: 2008-01-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikeprincipito on 2008-01-18
At first glance it seems like WoW will definitely work with 32 bit Wine. But I am wondering if it works with the 64 bit Wine that can be downloaded from the WineHQ debs. I looked through a few posts and they seem to be rather old talking about Fiesty and Edgy.

Does anyone here run WoW on a 64-bit? Please let me know your successes, failures, and what to expect.

---

### Post by Kilz on 2008-01-18
> **mikeprincipito said:**
> At first glance it seems like WoW will definitely work with 32 bit Wine. But I am wondering if it works with the 64 bit Wine that can be downloaded from the WineHQ debs. I looked through a few posts and they seem to be rather old talking about Fiesty and Edgy.

Does anyone here run WoW on a 64-bit? Please let me know your successes, failures, and what to expect.

First off , there is no such thing as 64bit wine. 64bit wine would be an application layer to run 64bit windows applications, those dont really exist in large enough numbers to create a 64bit wine yet. But I read someplace its in the discussion phase.
Wine is a windows application layer, even the packages for the AMD64 version of Ubuntu are 32bit. They have to be , they need to run common windows applications, and everything on windows is 32bit.  The packages just make wine easier to install to the amd64 version, but it is essentaly the same thing.
I would also trust what is written for feisty (and even Edgy) for the most part is true on Gutsy when dealing with Wine. You will want to look at the wien application database , it has a wiki for WoW linked on the WoW page.

---

### Post by mikeprincipito on 2008-01-19
Thank you for your response. I suppose you are correct about the 64 bit wine, perhaps I should have phrased it different. There seem to be AMD-64 Wine packages on WineHQ.org. Some older threads talk about jumping through a few hoops to get Wine running on an AMD-64. I am curious if with these new packages "It Just Works".

Once again, thank you for your response, but I am really looking for personal experience of Ubuntu users w/ an AMD-64, Wine, and WoW.

---

### Post by Kilz on 2008-01-19
> **mikeprincipito said:**
> Thank you for your response. I suppose you are correct about the 64 bit wine, perhaps I should have phrased it different. There seem to be AMD-64 Wine packages on WineHQ.org. Some older threads talk about jumping through a few hoops to get Wine running on an AMD-64. I am curious if with these new packages "It Just Works".

Once again, thank you for your response, but I am really looking for personal experience of Ubuntu users w/ an AMD-64, Wine, and WoW.

Since the packages are labeled amd64, it is a 100% certainty that they were designed to install and work with the amd64 version. Why not just install and come back if you have any questions , rather than look for problems that may not exist?

---

### Post by soxs on 2008-01-19
In fact the wine is always a 32bit program, it's just possible to compile it for 64bit so it runs fine, but its core styas 32bit and so all applications should run as well as on 32bit ubuntu.
The packages provided by wine just work.

---

### Post by mikeprincipito on 2008-01-19
I like it when things "Just Work". I'd hate to miss out on my daily WoW fix.

---

### Post by buntunub on 2008-01-19
There is an amd64 Ubuntu package for the latest wine. However, if you want to compile it yourself, you can easily via wine-git. Just make sure you follow the wiki for compiling it on a 64 bit system or your hosed. LOTS of symlinks there.

---

### Post by Kilz on 2008-01-19
> **mikeprincipito said:**
> I like it when things "Just Work". I'd hate to miss out on my daily WoW fix.

There is no operating system in existence, no software anyplace on earth that in some way shape or form does not require some setup. New users tend to think that "just works" means they dont have to do anything. That isnt reality. Wine will install without issues. But You may have to do some setup to get Wow or other applications running under wine. 
Just in case you havent run applications with wine, realize that there is no wine gui. No application to start called wine. Wine is a layer that allows Windows applications to run on linux.

---

### Post by mikeprincipito on 2008-01-20
> **Kilz said:**
> There is no operating system in existence, no software anyplace on earth that in some way shape or form does not require some setup. New users tend to think that "just works" means they dont have to do anything. That isnt reality. Wine will install without issues. But You may have to do some setup to get Wow or other applications running under wine. 
Just in case you havent run applications with wine, realize that there is no wine gui. No application to start called wine. Wine is a layer that allows Windows applications to run on linux.

I am far from a Linux newbie. Just Works for me means that I don't have to fight with compiling things for days, searching for dependences, and uncommitted patches. I switched to Ubuntu years ago because I was sick of that.

Although compiling from source and getting things to work can be fun, I simply don't have the time or patience anymore. If I am going to build a new compy that is 64-bit then I want to make sure I am close to the path of least resistance.

---

### Post by Kilz on 2008-01-20
> **mikeprincipito said:**
> I am far from a Linux newbie. Just Works for me means that I don't have to fight with compiling things for days, searching for dependences, and uncommitted patches. I switched to Ubuntu years ago because I was sick of that.

Although compiling from source and getting things to work can be fun, I simply don't have the time or patience anymore. If I am going to build a new compy that is 64-bit then I want to make sure I am close to the path of least resistance.

Then you will have no problems. I do not believe in sugar coating , or telling lies to people. I would rather you be prepared for what will happen. Sadly as I said , some get the idea that they will have to do nothing.

---

### Post by The other One on 2008-01-22
Yes, WoW runs in Wine on 64 bit. I've been playing through various versions of Wine and Ubuntu for some months.

What you can expect?
In game voice chat is difficult (for me anyway) to configure. I still can't get it happening with a USB headset.

The game and all addons work as they would in windows, although anecdotally, the framerate is better in Linux.

Horde FTW!

---

### Post by DDuong on 2008-01-23
I second that.  WoW works great on my laptop (Thinkpad T61p) with Xubuntu 64bit.

---

### Post by mikeprincipito on 2008-01-25
Horde FTW! Here here!

Glad to hear I am not going to have any [more] problems. I deal w/ voice chat by NOT using a USB headset. Plain old microphone w/ a +20 DB boost. It's not great, but it was easy to configure :)

---

### Post by mrpena on 2008-05-27
> **The other One said:**
> Yes, WoW runs in Wine on 64 bit. I've been playing through various versions of Wine and Ubuntu for some months.

What you can expect?
In game voice chat is difficult (for me anyway) to configure. I still can't get it happening with a USB headset.

The game and all addons work as they would in windows, although anecdotally, the framerate is better in Linux.

Horde FTW!

i'm actually getting worse framerate under linux than windows.  followed the instructions on [http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine) too.

windows i get easily 60+ fps (most of the time in the low 100's) under linux i'm lucky to get 28fps.

---

