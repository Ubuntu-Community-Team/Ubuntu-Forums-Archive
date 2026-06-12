---
title: "Firewire"
date: 2008-04-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Enul on 2008-04-18
I recently moved from windows xp to ubuntu 7.10 amd64 and so far i'm really happy with the move with the exception of one small item. I cant seem to get my IEEE Firewire VT6307 card to work with ubuntu. It worked fine with windows but for some reason upon boot up i see a message saying resources cant be allocated to the card. I've searched everywhere for information but as of yet i havent found any. The people i've talked to on the ubuntu irc channel say the card should work with ubuntu but i cant seem to make it do anything. Any help or advice would be appreciated.

---

### Post by Unterseeboot_234 on 2008-04-19
Do you have Kino? It works fine in 64-bit from the repos. Maybe it will also install the control IEEE 1394 audio/video devices kernel module when you install DVgrab.

Now, I have only been able to control a firewire handyCAM once, and that was when I spent a lot of effort compiling Kino and also compiling all the prerequisites for Kino (and it's not worth making your own Kino, there are too many dependencies, use the repositories).

Here's the link for [**Kino pre-requisites**]("http://www.kinodv.org/article/static/3").

The simplest test is DVgrab, that is in the repositories. Use Menu: System--> Synaptic Package Manager. Look for the 1394 mods. If they aren't installed, my advice is to go for the DVGrab, which is a command-line tool. The online docs for DVGrab are located at the kinodv website. After that works, then you at least have bulk capture (but not camera control) with Kino if you decide to install that.

---

### Post by Unterseeboot_234 on 2008-04-19
Do you have Kino? It works fine in 64-bit from the repos. Maybe it will also install the control IEEE 1394 audio/video devices kernel module when you install DVgrab.

Now, I have only been able to control a firewire handyCAM once, and that was when I spent a lot of effort compiling Kino and also compiling all the prerequisites for Kino (and it's not worth making your own Kino, there are too many dependencies, use the repositories).

Here's the link for [**Kino pre-requisites**]("http://www.kinodv.org/article/static/3").

The simplest test is DVgrab, that is in the repositories. Use Menu: System--> Synaptic Package Manager. Look for the 1394 mods. If they aren't installed, my advice is to go for the DVGrab, which is a command-line tool. The online docs for DVGrab are located at the kinodv website. After that works, then you at least have bulk capture (but not camera control) with Kino if you decide to install that.

---

