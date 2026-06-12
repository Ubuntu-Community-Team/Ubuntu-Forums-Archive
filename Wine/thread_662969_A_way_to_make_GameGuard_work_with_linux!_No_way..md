---
title: "A way to make GameGuard work with linux?! No way."
date: 2008-01-09
forum: Wine
---

### Post by Bensky on 2008-01-09
"Just replace GLib with NPTL (Native Posix Threading Library) and then
run any Gameguard protected games on Linux using your favorite
Windozed Emulator like WinE, WinEX, Cedega or Point2Play!

The only downside is - it slows down a little..

But beware - replacing GLib is no an easy task for novice linux user!
You must still ask for some assistance from someone who really knows
Linux! Or else you'll be trashing your system if you do not do it
correctly!"

^Found this on a forum somewhere. Can anyone verify this? Does this apply to ubuntu?

The only thing holding me back from switching to ubuntu right now is that one of my favorite games uses gameguard and will not work properly with Wine.

---

### Post by K.Mandla on 2008-01-09
Do you have a link? Perhaps if someone could read more about it, they might be able to help.

---

### Post by Bensky on 2008-01-10
> **K.Mandla said:**
> Do you have a link? Perhaps if someone could read more about it, they might be able to help.

[http://www.linuxquestions.org/questions/showthread.php?p=1877332#post1877332](http://www.linuxquestions.org/questions/showthread.php?p=1877332#post1877332)

Unfortunately, since the post was made in 2005, the link to the thread where the guy quoted from is broken. :(

---

### Post by Bensky on 2008-01-15
Bump. Does anyone know anything about this?

---

### Post by Tarmael on 2008-01-20
bump.

Anyone???

ANYONE know how to get through GG?

---

### Post by kazuya on 2008-01-21
I am trying this thus far on the game 2moons. It is not easy. So far I downloaded and installed gameguard, but it is having issue with either the linux firewall or an antivirus  program.


I was testing the game 2moons, which is listed as untested. I was trying to give back feedback on the success or failure of trying to install and run the game on linux {archlinux}
I had all the videocard drivers properly installed. Ensure 3d was working. Then via Crossover office Pro 6.2.0, I successfully installed IE6, activex, and then 2moons.
Installation went by flawlessly.

When I attempted to run, it updated and started similarly as it would in windows XP. It download al updates, etc., I had even downloaded the gameguard executable and installed it via cross over pro and it installed fine as well.

When I go to launch the game, it loads up, but upon clicking the start for it connect to server and startup, I get a complaint from the gameguard client as below:

GameGuard Error: 360 - From archlinux
Failed to complete GameGuard Update. Try again after disabling any anti-virus programs or change its settings using PC Management Program.

Some window users used to get these error, but I do not know how to get around that in linux. We have IP table firewalls and different firewall settings than in windows. Is there a way to disable  the firewall or enable the gameguard to bypass the firewall, by allowing it through some known port that it uses?

---

### Post by Bensky on 2008-01-22
> **kazuya said:**
> I am trying this thus far on the game 2moons. It is not easy. So far I downloaded and installed gameguard, but it is having issue with either the linux firewall or an antivirus  program.


I was testing the game 2moons, which is listed as untested. I was trying to give back feedback on the success or failure of trying to install and run the game on linux {archlinux}
I had all the videocard drivers properly installed. Ensure 3d was working. Then via Crossover office Pro 6.2.0, I successfully installed IE6, activex, and then 2moons.
Installation went by flawlessly.

When I attempted to run, it updated and started similarly as it would in windows XP. It download al updates, etc., I had even downloaded the gameguard executable and installed it via cross over pro and it installed fine as well.

When I go to launch the game, it loads up, but upon clicking the start for it connect to server and startup, I get a complaint from the gameguard client as below:

GameGuard Error: 360 - From archlinux
Failed to complete GameGuard Update. Try again after disabling any anti-virus programs or change its settings using PC Management Program.

Some window users used to get these error, but I do not know how to get around that in linux. We have IP table firewalls and different firewall settings than in windows. Is there a way to disable  the firewall or enable the gameguard to bypass the firewall, by allowing it through some known port that it uses?

Check out this:
[http://www.plaync.com/us/support/doc_1713.html?prod=10](http://www.plaync.com/us/support/doc_1713.html?prod=10)

> 
If you have a cable or DSL modem and are connecting through a router, switch, or a hub, try disconnecting this device and connecting directly to your cable/DSL modem. If you are able to connect this way, then there is a chance you may need to update the firmware on the device that you are connecting through, which you can find on the manufacturer's website. If, however, you already have the latest firmware, you should check to make sure that the correct ports are still open, which are TCP 7777, 2106, 2009 and 80, and DNS (TCP/UDP) 53. You should also check to see if the appropriate files listed above are added to your router's exceptions, if applicable.


---

### Post by Kingfield on 2008-01-23
Doesn't Make sense. Different Programs use different versions of gameguard anyways.

---

### Post by kazuya on 2008-01-23
the game loads fine on my windows partition, but I would prefer to run it in my linux partition as I am typically in my linux side of the machine. I switch to the windows side just to play that game. That makes me single-tasking, which may be fine now. However, I have some other systems where I have deleted the windows partition and turned it into another linux partition or storage..

Any ideas?

Different types of gameguard? How do I know which to use for my game? It seems a crappy app though.

I am looking for other good free MMORPH games with good graphics that do not require this gameguard thing?

Just wrote my little email complaint to acclaim about this gameguard thing. Hope it was polite enough, I hinted at them looking at the success of Blizzard in WoW  and also games like GuildWars and even their game Silk Road Online. Waiting for response. I won't hold my breath.

---

### Post by Bensky on 2008-01-26
> **kazuya said:**
> the game loads fine on my windows partition, but I would prefer to run it in my linux partition as I am typically in my linux side of the machine. I switch to the windows side just to play that game. That makes me single-tasking, which may be fine now. However, I have some other systems where I have deleted the windows partition and turned it into another linux partition or storage..

Any ideas?

Different types of gameguard? How do I know which to use for my game? It seems a crappy app though.

I am looking for other good free MMORPH games with good graphics that do not require this gameguard thing?

Just wrote my little email complaint to acclaim about this gameguard thing. Hope it was polite enough, I hinted at them looking at the success of Blizzard in WoW  and also games like GuildWars and even their game Silk Road Online. Waiting for response. I won't hold my breath.

It's almost certain that Acclaim has a contract with INCA (company that makes gameguard), so it's almost certain that they won't listen to you. D:

---

### Post by kazuya on 2008-01-31
so best bet would be to contact the company INCA directly to change or Boycott the games.

---

### Post by Tarmael on 2008-02-01
You'll be waiting a while.

Fastest results is boycott the game.

However, I feel confident that there is a way to get game guard to work. Just dunno how...

---

### Post by Dvorakis on 2008-11-05
you would think that maybe booting and mounting the windows hard drive and then running the game throught the hard drive and wine might work...

---

### Post by warzt on 2008-12-19
I think the point is firewall of linux. I always have error 114. My friend (he use XP) said i must uninstall all antivirus program but right now I don't install any antivirus program.

---

