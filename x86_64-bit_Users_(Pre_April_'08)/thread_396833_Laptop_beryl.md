---
title: "Laptop beryl"
date: 2007-03-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by StandardBlueCaboose on 2007-03-29
Hi everybody,

It's been a while since I posted on these forums.

Anyway, I bought a laptop a few months ago and was surviving with Windows XP. I recently decided I'd put Linux on it and see how much faster it would be. Quite frankly, it blows Windows away. 

Now I want to put some eye-candy on it. 

I was wondering where to get started. I know that I want Beryl or Compiz on it.

I have a 64-bit processor and I definitely want to keep a 64-bit OS on it. I have an ATI graphics card, and I am running Kubuntu.

From what I know, and have experienced before, I basically have one of the most difficult/unfriendly configurations possible for installing Beryl. 

I have beryl installed on my desktop, and I love it. It was quite difficult to set up with a 64-bit operating system. I use an Nvidia card on my desktop, though. 

Can anybody tell me if they've gotten beryl to work on an Acer Aspire with an 1100 IGP (ATI Radeon Xpress 1100 IGP)? Should I try upgrading to feisty? Is it easier to go with compiz or beryl? Is it easier to use Aiglx or Xgl?

---

### Post by mjhb on 2007-03-29
What ATI card do you have? The official ATI driver does not support Beryl, only XGL. Cards that are supported by the open source driver do support it however I'm not too sure what the performance is like.

---

### Post by StandardBlueCaboose on 2007-04-01
> **mjhb said:**
> What ATI card do you have? The official ATI driver does not support Beryl, only XGL. Cards that are supported by the open source driver do support it however I'm not too sure what the performance is like.


> **StandardBlueCaboose said:**
> 


 ...on an Acer Aspire with an 1100 IGP (ATI Radeon Xpress 1100 IGP)? ... 

Is my card supported? Has anybody gotten beryl to work with the same card?

Would my question be better suited in the laptop forum?

---

### Post by marsmissionaries on 2007-04-02
> **StandardBlueCaboose said:**
> Is my card supported? Has anybody gotten beryl to work with the same card?

Would my question be better suited in the laptop forum?

my radeon xpress 200m works, i think they use the same drivers.

---

### Post by StandardBlueCaboose on 2007-04-02
> **marsmissionaries said:**
> my radeon xpress 200m works, i think they use the same drivers.

That's good news. Did you use the open source drivers? If not, which driver from ATI did you download? 

Thanks.

---

### Post by qamelian on 2007-04-02
> **StandardBlueCaboose said:**
> That's good news. Did you use the open source drivers? If not, which driver from ATI did you download? 

Thanks.

You don't necessarily have to download anything from ATI. The FGLRX drivers are available in the Ubuntu repositories.

---

### Post by BIGtrouble77 on 2007-04-03
Just so you know, the Beryl Wiki ( [http://wiki.beryl-project.org/wiki/Main_Page](http://wiki.beryl-project.org/wiki/Main_Page) ) has great info for getting Beryl up and running in Ubuntu.  From what I know, Beryl works fine with current ATI cards.  I think you have to use XGL rather than AIGLX, tho.

---

### Post by marsmissionaries on 2007-04-03
i used xgl and fglrx drivers. I didn't like it though so i uninstalled it, it's way to much eye candy for me.

---

### Post by StandardBlueCaboose on 2007-04-03
I found an automatic installation script on that wiki. 

I was wondering if somebody would be so kind as to modify it so that it works with KDE, rather than gnome... At least, I think that's my problem... 

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI")

A beryl installer tailored for a 64-bit, ATI, and KDE is hard to find.

---

### Post by trippinnik on 2007-04-04
From what I've read the openshource drivers are better.  They allow you to use XGl instead of AIGLX (which uses more memory).  Your card should work as I have gotten it running on a much older card.

---

### Post by config on 2007-04-04
About automatic installation and XGL for KDE... do:
```
sudo gedit /usr/bin/startxgl.sh
```
though, I don't really remember where startxgl script is put, but you can always find out typing in console ```
whereis startxgl.sh
```
In that script you gotta change "gnome-session" to "startkde" and than you'll have kde session started when logging in "Xgl"
I think this should do the trick :).

My case of Beryl with x86_64 is rather funny... I have AMD 64 3000+  and ATI x1950pro and I had a lot of time trying to find out how to set up Beryl and make it work. One day it has started working and was doing just fine. I even got used to it :). But yesterday something went wrong, when I was surfing internet (and I haven't installed any updates for Beryl since it started working). The system hang up a bit and than the screen became black... Now whenever I start Beryl, there are problems with menus not showing up and windows not redrawing. But the cube itself works and I can see caps of cube when rotating it... Don't know what to do. May be anyone had some familiar problems?
I use Beryl binary for x86_64 from Trivinjo repository, start it with "beryl-xgl --use-copy", xorg.conf is set as it is recommended with all the "agp-lock=0" stuff :).
Any help out there?

P.S. Standart opensource ati driver doesn't wan to work with my graphics card...

---

### Post by StandardBlueCaboose on 2007-04-08
> **config said:**
> About automatic installation and XGL for KDE... do:
```
sudo gedit /usr/bin/startxgl.sh
```
though, I don't really remember where startxgl script is put, but you can always find out typing in console ```
whereis startxgl.sh
```
In that script you gotta change "gnome-session" to "startkde" and than you'll have kde session started when logging in "Xgl"
I think this should do the trick :).


Thank you very much, this worked. I tried to change where it said "gnome-session" in the script, not in startxgl.sh. For some reason, that didn't work. Thanks again.

Unfortunately, I can't help you with your problem. Seems like something went wrong with your driver. You could try reinstalling it using the automatic script. But I have no idea.

---

### Post by jgrantham on 2007-08-29
The wiki is down. Does someone have the script they could post?

---

### Post by ann smith on 2007-09-28
Hello!
Can anyone help me please: i'm trying to get Beryl to work on Dell 6400 ATI Radeon X1400 with Kubuntu Feisty Fawn, fglrx drivers, i've installed it and nothing happens; I dont know how to install and get working XGL; when I search for the file startxgl.sh it's not here and the wiki.beryl-projects link isn't working. Please if you can help me
Thank you

---

### Post by jdonald1 on 2007-09-28
Dell inspiron 6400 with X1400 Ubuntu 64 7.04

Same issue, I get everything installed according to:
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

I am missing the tray jewel icon so I have no way to change the default window manager.

My ati card is showing as Generic for some reason.

---

