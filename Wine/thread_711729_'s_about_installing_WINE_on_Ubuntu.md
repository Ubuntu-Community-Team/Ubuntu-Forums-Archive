---
title: "?'s about installing WINE on Ubuntu"
date: 2008-02-29
forum: Wine
---

### Post by justin0101 on 2008-02-29
My problem is not trying to figure out how to install WINE but here are the steps I took:

1. Downloaded WINE package off of Ubuntu Homesite
2. Transfered to reliable USB device
3. Transfered package to Desktop
4. Opened package 
5. ERROR MESSAGE: Dependency is not Satisfactory

Got a new version instalkled it but now I cant get to it because it wont show up in my menu. I CANT FIGURE OUT HOW TO RUN IT!!!!!!!!!!!!!!!!!!!

---

### Post by sstusick on 2008-02-29
The error means that you're missing a dependency that WINE needs to run. If you can figure out what that dependency is, you should be able to download it and transfer it to the desired computer. It should tell you what the  dependency is.

---

### Post by Victormd on 2008-02-29
Try installing wine from the repositories, this should install the proper dependencies, then update using the version you downloaded.

---

### Post by Victormd on 2008-02-29
Ok, just re-read your whole post.
The "dependency is not satisfactory" means that Wine needs other pieces of software (libraries) to be installed in order for it to run. Without direct internet connection, installing them can be a bit tricky. However, [www.winehq.org](www.winehq.org) should have some good how to for this case.

---

### Post by justin0101 on 2008-02-29
Sorry for double posting

I have tried winehq but when I click on download for ubuntu it tells me to use my terminal to download the file which again without a direct internet connection is frustrating. I need wine to install a driver for my wireless card.

---

### Post by Victormd on 2008-03-01
Why do you need wine for your wireless?
What's your configuration?

---

### Post by sstusick on 2008-03-01
Uhh WINE will not help you with your wireless connection...

That's what NDISWrapper is for.

---

### Post by justin0101 on 2008-03-01
Whats that?

---

### Post by FrozenFox on 2008-03-01
Google is your friend.. "I'm feeling lucky" of ndiswrapper returns...

[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

NdisWrapper is a program that tries to work around linux not having native wireless support for some cards (mostly from companies who refuse to give the linux community sufficient resources to create a driver) by allowing the windows ones to be used and sort of hooking it into the linux system. Look around these forums or google for a good tutorial on how to use it or see the wiki/documentation on their website. I'd suggest looking in the ubuntu forums first, because the ndiswrapper website does not have a .deb or anything to install and wants you to compile instead, which is unnecessary on ubuntu. You should be able to find ndiswrapper by running synaptic and installing it there.

---

### Post by justin0101 on 2008-03-01
Ughhhhhhhhhhhhhhhhhhhhhhh!!!!!!!!!!!

---

### Post by Victormd on 2008-03-01
that's why I asked you for your configuration. This forum has several threads on HP and Dell Wireless cards. I have a HP and had to use ndiswrapper, and it worked great! Also, search for your wireless model (i.e. Broadband 43xx).
Here are a few links that I researched prior to getting my wireless to work:

[http://ubuntuforums.org/showthread.php?t=572005](http://ubuntuforums.org/showthread.php?t=572005)
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)
[https://wiki.ubuntu.com/HP_dv6000_Series](https://wiki.ubuntu.com/HP_dv6000_Series)

Hope these help.

---

