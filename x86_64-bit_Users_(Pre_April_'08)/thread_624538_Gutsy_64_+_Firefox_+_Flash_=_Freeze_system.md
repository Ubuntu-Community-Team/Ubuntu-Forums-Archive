---
title: "Gutsy 64 + Firefox + Flash = Freeze system"
date: 2007-11-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by sexus6 on 2007-11-27
Hi
I make a new installation with Gutsy 7.10 64 bits. When I visit with firefox a web page with flash, they asked me to install flash plugin. I accept, and install the non-free plugin. Firefox and Ubuntu installs some libraries (ia32 etc) and the plugin needed. 

This proces I made manually with feisty with swiftfox and works.

But now, I have the problem that when I browse web pages with flash, youtube and similars, the system freezes completely. I have no keyboard access and I have to make a hard reset. If I use firefox with webs pages withou flash all is OK.

I was crazy sarching at logs (user.log, systemlog, etc) and there is no error visible. I start firefox in terminal (to see posible errors) but when the system freezes I can't get access to anything, mouse, keyboard, etc, and I can't see the posible log issue from firefox.

What's the problem? possible workarounds?
Thanks in advance.

---

### Post by Kilz on 2007-11-27
> **sexus6 said:**
> Hi
I make a new installation with Gutsy 7.10 64 bits. When I visit with firefox a web page with flash, they asked me to install flash plugin. I accept, and install the non-free plugin. Firefox and Ubuntu installs some libraries (ia32 etc) and the plugin needed. 

This proces I made manually with feisty with swiftfox and works.

But now, I have the problem that when I browse web pages with flash, youtube and similars, the system freezes completely. I have no keyboard access and I have to make a hard reset. If I use firefox with webs pages withou flash all is OK.

I was crazy sarching at logs (user.log, systemlog, etc) and there is no error visible. I start firefox in terminal (to see posible errors) but when the system freezes I can't get access to anything, mouse, keyboard, etc, and I can't see the posible log issue from firefox.

What's the problem? possible workarounds?
Thanks in advance.

Open a terminal and enter.
```
sudo apt-get remove nspluginwrapper
```
```
sudo apt-get install flashplugin-nonfree
```
That will install flash to your 64bit browser.

---

### Post by sexus6 on 2007-11-27
I reinstall with this method, but still freezing the system when I see flash videos  :(

---

### Post by junior aspirin on 2007-11-27
i get this too. i think i have narrowed it down to flash, but it doenst always happen. as a note it also did the smae thing on 32bit gutsy on this machine.

as a bit more info, the whole screen locks up, as does the keyboard. i can still move the mouse about, but not click anything. the interesting thing is that my samba network shares are still accessable (acording to a house mate), and my music from rhythmbox continues to play.

I am still not 100% sure that it is flash, since i switched some stuff in my pc over before i installed gutsy.

Edit: i use epiphany, but thats still firefox under the hood.

---

### Post by david_2001 on 2007-11-27
> **junior aspirin said:**
> as a bit more info, the whole screen locks up, as does the keyboard. i can still move the mouse about, but not click anything. the interesting thing is that my samba network shares are still accessable (acording to a house mate), and my music from rhythmbox continues to play.

Random thought: Sounds like Xorg is hanging up.  Do you have desktop effects (compiz or whatever) running and, if so, does your system still freeze with the effects turned off?

---

### Post by junior aspirin on 2007-11-27
yeah i have compiz-fusion running. using the open Ati divers at the moment, it maybe something to do with that, i still think flash is the root cause though. my uptime is over a day at the moment, but can freeze after a few minutes.

edit: probably should not that i never had this problem with fiesty 32bit. the only thing that I may have done is damage my grapics card - i did dismantle the fan on it, to oil it, although the fan seems to be working ok.

---

### Post by sexus6 on 2007-11-28
I disable compiz too. I'm not sure 100% that will be flash, but when I see flash videos this freezes are more frequently. Yesterday freezes when I use virtualbox (with win xp inside) with ADobe Indesign.

For some tests I disable compiz and I use VESA driver... For now, there is not freeze but the freezes are randomly.

---

### Post by junior aspirin on 2007-11-28
i just uninstalled flash. will post back when/if i get a lock up again.

---

### Post by david_2001 on 2007-11-28
> **sexus6 said:**
> For some tests I disable compiz and I use VESA driver... For now, there is not freeze but the freezes are randomly.
If it freezes again try hitting Ctrl-Backspace immediately to kill the X server - don't leave it too long or this will not work.

---

### Post by sexus6 on 2007-11-28
>  If it freezes again try hitting Ctrl-Backspace immediately to kill the X server - don't leave it too long or this will not work.

CTRL+ALT+BACKSPACE does'nt work. The system is freezed completely, no mouse movement, no keyboard actions...

I have new tests. I think that is not flash problem. I test all system, soft, firefox, flash, virtualbox, and does not freezes never with VESA driver. I disable private drivers, and this works.

I don't understand why nvidia private drivers freezes the system. The before installation was a 7.04=>7.10 gutsy installation that works with this nvidia drivers. When I reinstall the system, with a new installation (not update) nvidia private drivers does not work.

Why? What can I do to use nvidia drivers without freezings? I'm now with VESA.

---

### Post by david_2001 on 2007-11-28
> **sexus6 said:**
> Why? What can I do to use nvidia drivers without freezings? I'm now with VESA.
You're going to have to post your video hardware specifications, nvidia driver version and /etc/X11/xorg.conf so people can check them over.

---

### Post by junior aspirin on 2007-11-28
ok, mine is not to do with flash. it just froze 3 times in the past hour or so. i was only doing a bit of light editing in inkscape. will disable compiz at some point and see if that helps. in the mean time im gonna have to use windows since i have a Uni dead line fast approaching.

---

### Post by kthardin on 2007-11-29
I'm having the same problem.  Every single time I go to youtube, it will inevitably lock my system.  No response from anything.  I saw a few threads that said to disable the Nvidia drivers (I run a GeForce 6800), but after switching to the nv drivers, I still have the lock ups. 

Though doing that DID allow many of my video files to play with the correct color settings.

I'm at a loss.

I'm running 64bit Firefox with the new flash plugin.

---

### Post by jlacroix on 2008-01-04
The problem you guys are experiencing is likely the same as the one I've been fighting. If your problem is similair to mine, you can fix this issue by:

Not using an onboard soundcard.

Use a PCI card and you'll be set, if you have a desktop that is.

Otherwise, if I misunderstood and this is not the same problem as mine, I apologize. However, Adobe Flash has serious bugs when working with onboard sound cards, ESPECIALLY Realtek.

---

### Post by firecat53 on 2008-01-05
I have an hp laptop with the nvidia geforce 7200 graphic driver and for a lot of the nvidia drivers there seems to be a recurrent lockup problem. I have to use the nvidia-glx driver (which I believe is the .9639) and that prevents all the lockups. Other people have solved the lockups by upgrading to the newest nvidia beta drivers (via Envy or from the nvidia site).  YMMV -- not sure how different the problems are for 7000 series and 8000 series cards.

good luck!
Scott

---

### Post by MariusSilverwolf on 2008-01-06
I had this same problem.  I fixed it by following the below HowTo:

[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

I now have a 32-bit version of FireFox with Flash and Java working on my 64-bit build of Gutsy without any problems.  ESPN InMotion works, YouTube works, Flash games work, and all without any hint at freezing.

Maybe it'll do ya right like it did me. ;-)

---

### Post by jarbroens on 2008-02-11
Thanks for suggesting the above link.  
I started having problems this weekend with my computer just freezing and firefox sometimes hanging and going to a grayed out screen.  I wasn't having trouble before this weekend and the only thing I'd changed is I added flash to firefox because I was tired of youtube and other flash sites not working right.
Anyway, I gave the 32 bit firefox w/ add ins a shot and right away it was running quick like before.

---

### Post by Freddy on 2008-02-11
This is a known bug on both 32 and 64bits Ubuntu. I've tried many different solutions but all of them have failed. Most freezes comes when having multiple tabs open so when I make a visit to Youtube I close all down.

---

### Post by rickyrockrat on 2008-04-14
If it is a memory-eating app problem, and you  want to find it, go here:
[http://ubuntuforums.org/showthread.php?t=587905&page=9](http://ubuntuforums.org/showthread.php?t=587905&page=9)
and read entry #640.
Follow the instructions on setting up top before the crash. It is likely gnash.

Once your system goes to swap, every keystroke can take 1-10 minutes to respond, so you will need extreme patience to find it.

Good luck.

---

