---
title: "Anyone tested the 1-click install?"
date: 2007-09-15
forum: openSUSE and SUSE Linux Enterprise
---

### Post by 67GTA on 2007-09-15
I tried 10.3 a couple of weeks ago, and uninstalled it again becuase of the package manager. It was a little faster, but more of the same. I ran across this link today and was curios. It is supposed to be included in 10.3 by default? Package management is the only reason I never keep open suse installed. Has anyone tried it out yet?

[http://opensuse-community.org/Restricted_Formats/10.3](http://opensuse-community.org/Restricted_Formats/10.3)

---

### Post by Incense on 2007-09-16
I tried it out, but not with the restricted formats link. They have an entire software portal, much like getded.net for ubuntu. It looks like the OpenSUSE reops are down right now though, so there really isn't much going on anywhere, but when things are online, you can check out the portal [here.]("http://software.opensuse.org/") 

It's not just a 10.3 thing either. You can install compiz-fusion in 10.2 using the one click installer! Read [here!]("http://dev.beryl-project.org/~cyberorg/suse/38")

Here are a few more [examples]("http://benjiweber.co.uk/installdemo/") of the one click install. Good Stuff!

---

### Post by 67GTA on 2007-09-16
That is pretty exciting. I always said that opensuse might climb back up the Distrowatch ladder if they could ever simplify their package management.

---

### Post by RedDwarf on 2007-09-16
> **Incense said:**
> It looks like the OpenSUSE reops are down right now though, so there really isn't much going on anywhere, but when things are online, you can check out the portal [here.]("http://software.opensuse.org/")
software.opensuse.org is down but the repos are available through the redirector: [http://download.opensuse.org/distribution/](http://download.opensuse.org/distribution/) and [http://download.opensuse.org/repositories/](http://download.opensuse.org/repositories/)

---

### Post by LuisAugusto on 2007-09-30
It works very nice. It's easy and fast.

BuildService can even be use in Ubuntu and other distros, I believe it will become (in a near future) the place for searching software for all distros.

---

### Post by Erunno on 2007-10-01
Hm, if my memory doesn't fail me I remember that Ubuntu is planning to establish their own build service in one of the upcoming releases. Pretty sensible from a marketing point of view to not guide your audience to a service offered by a competitor.

---

### Post by LuisAugusto on 2007-10-02
> **Erunno said:**
> Hm, if my memory doesn't fail me I remember that Ubuntu is planning to establish their own build service in one of the upcoming releases. Pretty sensible from a marketing point of view to not guide your audience to a service offered by a competitor.

What a disappointing way of think. BuildService already offer Ubuntu, Fedora, and other distro support, why making double effort? It would just be the software place for Linux, that's all. Nobody believe that Linspire agreement was bad because it guide Ubuntu audience to CNR, a servide offered by a competitor.

Linux shouldn't be fighting with himself. It should offer different options, but that doesn't mean that they can't share more than a kernel.

---

### Post by Erunno on 2007-10-02
> **LuisAugusto said:**
> What a disappointing way of think. BuildService already offer Ubuntu, Fedora, and other distro support, why making double effort? It would just be the software place for Linux, that's all. Nobody believe that Linspire agreement was bad because it guide Ubuntu audience to CNR, a servide offered by a competitor.

Linux shouldn't be fighting with himself. It should offer different options, but that doesn't mean that they can't share more than a kernel.

Well, they're competing for the same audience and probably trying to break into the enterprise sector by being a force on the user desktop (with SuSE/Novell having already a foot in the business sector). A Linux distribution cannot lock you with technical measures but they can try to offer you anything you might ever want by themselves so that you never develop the desire to look at anything else. Yes, this means a lot of duplication but on the other hand duplication of effort has been a trademark of the Linux desktop for a long time *shrug*

There's no "working together" when you're a corporate entity. Distributions work together as long as they think it helps their own agenda (making money).

---

### Post by LuisAugusto on 2007-10-03
> **Erunno said:**
> Well, they're competing for the same audience and probably trying to break into the enterprise sector by being a force on the user desktop (with SuSE/Novell having already a foot in the business sector). A Linux distribution cannot lock you with technical measures but they can try to offer you anything you might ever want by themselves so that you never develop the desire to look at anything else. Yes, this means a lot of duplication but on the other hand duplication of effort has been a trademark of the Linux desktop for a long time *shrug*

There's no "working together" when you're a corporate entity. Distributions work together as long as they think it helps their own agenda (making money).
 Yes, Yes, that's why everything in their code is GPL or compatible, of course. Open Source it's about being rich and selfish.

---

### Post by Erunno on 2007-10-03
> **LuisAugusto said:**
> Yes, Yes, that's why everything in their code is GPL or compatible, of course. Open Source it's about being rich and selfish.

In my opinion this is certainly the case when it comes to large companies like Novell and RedHat. While there are a lot of people who work for free in their leisure time in Free Software projects the aforementioned companies have simply found a way to make money with Free Software (nothing bad about that). That doesn't mean that they have to believe the slightest in Free Software ideals. It's just the case that they have to play nice with the FS community as a lot of code gets developed outside their company so it's in their best interest to maintain a good relationship to this community.

---

### Post by S3Indiana on 2007-10-03
The [interface]("http://software.opensuse.org/search") appears to be missing basic features (like browsing) and the results aren't encouraging...> **Get Software from the openSUSE Build Service**                
                                                                              [CENTER]     **Searching**   [/CENTER]
                  firefox
    
Ubuntu 7.04  
  0 collections and 0 binaries from 0 source packages
    [Permanent link to this result]("http://software.opensuse.org/search?p=1&q=firefox&baseproject=Ubuntu%3A7.04") 
  Nothing found

---

### Post by LuisAugusto on 2007-10-03
> **S3Indiana said:**
> The [interface]("http://software.opensuse.org/search") appears to be missing basic features (like browsing) and the results aren't encouraging...

Ubuntu support has just been added (1 month I think).

---

### Post by kiran_aryan on 2007-10-05
1 click install is good but the opensuse servers are slow right now.

---

### Post by mindtrick on 2007-10-06
It's addictive. Installing Nvidia drivers with one-click was awesome. But reloading repositories thing is annoying.

---

### Post by mindtrick on 2007-10-06
BTW does anyone know a one click install for Windows fonts ? :D

---

### Post by Incense on 2007-10-06
> **mindtrick said:**
> BTW does anyone know a one click install for Windows fonts ? :D

How about two clicks?

```
wget ftp://ftp.gwdg.de/pub/linux/misc/suser-jengelh/UNSPEC/noarch/MicrosoftFonts-1-jen14.noarch.rpm
```

```
rpm -Uvh Microsoft*.rpm
```

That worked with 10.2. Should with 10.3 I would think...

---

### Post by mindtrick on 2007-10-06
Works perfectly, thanks!

---

### Post by RebounD11 on 2007-10-17
works fine for me ... love it :D I just wish I could one click install more apps at the same time :D

---

