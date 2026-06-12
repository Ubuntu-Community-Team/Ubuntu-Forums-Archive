---
title: "Wine is driving me insane! (Worms Armageddon)"
date: 2007-07-02
forum: Wine
---

### Post by FRuMMaGe on 2007-07-02
Up until now, I have not been able to get any games fully working through wine.  Even ones such as Diablo II and other platinum rated ones.  I follow all the instructions and am no stranger to the terminal but still it refuses to work properly.  My one success has been Counter Strike Source.

I've recently been trying to return to the nostalgic world of Worms Armageddon.  The rating is "Gold" on the winehq site.  However, I cannot even get the installer to run.  All that happens is a message asking me to check the CD.  I tried using a different version (not the Sold Out version) and as soon as I run the installer, FREEEEEEEEZE.  My laptop completely crashes, to the point when even the caps lock keys dont work.

If I can just achieve this small victory I will be very please.  Any suggestions?

---

### Post by almkglor on 2007-07-02
Here's some information which you could provide, that *might* allow us to help you:

1.  Ubuntu Distribution number.  For instance, the Long Term Support that Ubuntu should "still" be supporting is Dapper Drake, 6.06.  The newer distributions are Edgy Eft, 6.10 and Feisty Fawn, 7.04.   Feisty is the latest. I had problems with running Wine on Drake.
2.  Laptop hardware.  For example, Intel 950GM motherboard with Intel945GM video card.   Intel video drivers suck somewhat by the way.
3.  winecfg (Default) settings, especially sound and graphics tabs.

---

### Post by hikaricore on 2007-07-02
He is using an Intel card and probably the i810 driver, I've mentioned this as a possible issue to him before and he's ignored it.

---

### Post by Matakoo on 2007-07-02
> **hikaricore said:**
> He is using an Intel card and probably the i810 driver, I've mentioned this as a possible issue to him before and he's ignored it.

In this case, I seriously doubt it's a graphics driver issue. If it was, the problems should show up when the game runs or is starting - not when trying to install it. 

If the problem was that the graphics show artifacts, the game runs slowly, or the graphics and sounds were unsynchronized, yes. In that case, I would suspect the driver.

I'm not sure what it could be, but the game has trouble running on my computer as well. I get further than the OP but there are still problems. The game installs fine. Once trying to run it, I just get a black screen. The game hasn't completely crashed though, since I do get sound. No way of getting back to my desktop without ctrl-alt-backspace, but the computer is otherwise running as it should. But to be honest, I haven't looked into what could be causing the problem. I tried it more out of curiosity in how wine runs games more than anything else. 

So, if it is a driver issue then the nvidia-drivers are equally buggy.

---

### Post by hikaricore on 2007-07-02
My appologies I didn't really read his full post as I was in a hurry this morning, I just assumed the game was freezing up.

Anyway, Matakoo, I was going to point you to the tips on running it at [WINE's Application Database]("http://appdb.winehq.org"), but I'm getting an odd error from the site at the moment.

In order to actually run the game you'll need to replace the ddraw.dll file in the game's directory with an alternate version (no clue where to get it as the link was on the appdb site).  You will also need to launch the game as such:

```
wine wa.exe /NOINTRO
```

I've attached the modified ddraw.dll file I use to run Worms Armageddon.  This is the file I got from a guide to
get WA running or from a link on the WINE appdb site.  Use at your own risk, blah blah blah, I didn't make it,
it comes with no warranty, and like and iPod it should not be eaten under any circumstances.

---

### Post by FRuMMaGe on 2007-07-02
> **hikaricore said:**
> My appologies I didn't really read his full post as I was in a hurry this morning, I just assumed the game was freezing up.

Anyway, Matakoo, I was going to point you to the tips on running it at [WINE's Application Database]("http://appdb.winehq.org"), but I'm getting an odd error from the site at the moment.

In order to actually run the game you'll need to replace the ddraw.dll file in the game's directory with an alternate version (no clue where to get it as the link was on the appdb site).  You will also need to launch the game as such:

```
wine wa.exe /NOINTRO
```

I've attached the modified ddraw.dll file I use to run Worms Armageddon.  This is the file I got from a guide to
get WA running or from a link on the WINE appdb site.  Use at your own risk, blah blah blah, I didn't make it,
it comes with no warranty, and like and iPod it should not be eaten under any circumstances.

Yes WineHQ was down for about 24 hours recently.  I am beginning to think that my installshield is broken, as this freeze happened again the other day when trying to install Warcraft III.

However, I managed to get it to install using a downloaded ISO (I assume this is ok as I have the original game) and it installed fine.  The game runs perfectly, except for the videos but this is not a problem.

---

### Post by Matakoo on 2007-07-02
> **hikaricore said:**
> 
Anyway, Matakoo, I was going to point you to the tips on running it at [WINE's Application Database]("http://appdb.winehq.org"), but I'm getting an odd error from the site at the moment.

Yeah, I've seen those tips. Patching the game to the latest beta-version and all of that. The patches seem to work...at least I didn't get any error messages. Now all I need to figure out is how to make the game SEE my CD...well, that's a problem I sure is easy to fix once I'm more awake than I am now.

Kinda funny...that you can get so absorbed in trying to get a game to work in wine just to see how well it works. Curiosity killed the cat...

---

### Post by FRuMMaGe on 2007-07-03
> **Matakoo said:**
> Yeah, I've seen those tips. Patching the game to the latest beta-version and all of that. The patches seem to work...at least I didn't get any error messages. Now all I need to figure out is how to make the game SEE my CD...well, that's a problem I sure is easy to fix once I'm more awake than I am now.

Kinda funny...that you can get so absorbed in trying to get a game to work in wine just to see how well it works. Curiosity killed the cat...

Type winecfg into the terminal and go onto the "drives" tab.  Now click on the drive letter of your CD and go onto the advanced settings.  Make sure it is set up as "CD-ROM".

Anyway I know about the patched, but to use them you have to have actually installed the game. :(

---

### Post by Matakoo on 2007-07-03
> **FRuMMaGe said:**
> Type winecfg into the terminal and go onto the "drives" tab.  Now click on the drive letter of your CD and go onto the advanced settings.  Make sure it is set up as "CD-ROM".

Thanks for the tip, but it wasn't that. I've had it set up like that since wine was originally installed, so dunno why it didn't work with worms yesterday. Today it did though....without me changing a thing. Wine is too alike windows I guess...it works or not depending on its mood and the phase of the moon ;)

---

### Post by madewokherd on 2007-07-05
Dapper comes with Wine 0.9.9, and since that release Wine has become much better at detecting CD-ROM drives and setting them up properly. I recommend getting the most recent version of Wine from the winehq repository, as described here: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

Use a real CD. Recent versions of Wine are very good at configuring real CD's, but they'll give you no help with ISO's (I wouldn't trust an ISO I got from the Internet anyway.. it could be broken).

Also, if nothing has worked for you yet, I suggest you remove ~/.wine and start fresh (this will of course get rid of anything you have managed to install).

If that still doesn't work, change to the Install directory on the cd and run Install.exe. People have had trouble with the "launcher" on the Sold Out Software version of WA but have usually been ok running the installer directly.

Edit: Ignore that. I can't keep track of the different users with different issues in this one thread. :|

---

### Post by FRuMMaGe on 2007-07-05
> **madewokherd said:**
> Dapper comes with Wine 0.9.9, and since that release Wine has become much better at detecting CD-ROM drives and setting them up properly. I recommend getting the most recent version of Wine from the winehq repository, as described here: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

Use a real CD. Recent versions of Wine are very good at configuring real CD's, but they'll give you no help with ISO's (I wouldn't trust an ISO I got from the Internet anyway.. it could be broken).

Also, if nothing has worked for you yet, I suggest you remove ~/.wine and start fresh (this will of course get rid of anything you have managed to install).

If that still doesn't work, change to the Install directory on the cd and run Install.exe. People have had trouble with the "launcher" on the Sold Out Software version of WA but have usually been ok running the installer directly.

Edit: Ignore that. I can't keep track of the different users with different issues in this one thread. :|

These are all good suggestions but:
> I am already on the latest Wine (9.40 or something).
> I am using an original CD, but I have tried an ISO to see if it made a difference (it didn't).
> When I run the SoldOut installer nothing happens, but when I run the game installer my computer completely freezes on the spash screen.

---

### Post by gymmeh on 2008-04-01
or just DL wormux

---

### Post by tajmox on 2008-06-05
wormus makes me want to hit myself.  By the way, if anyone needs help setting up Worms Armageddon let me know, I'll help ya.

---

### Post by BigMeanMikeRich on 2008-11-21
I would love some help setting up Worms Armageddon.  I am running wine 1.0.1 on Ubuntu 8.10, and have successfully installed WA and updated it to the latest 3.6.29.0_beta.  I placed a custom ddraw.dll in the Worms Armageddon directory, and I can run the game!

The problem I run into is more of a playability issue.  The main menu defaults to 640x480, and if I leave the gameplay resolution set to 640x480, the game runs well. For those of you who have not tried playing Worms in 640x480, you can't see anything on the map, and spend most of your time moving the mouse around to get a better view.

When I set the resolution higher, say to 800x600, or the desired 1024x768, the window increases in size to the appropriate number of pixels, but only a 640x480 chunk of it actually displays the game-- the rest is all garbage and artifacts.

I set wine's graphics options to emulate a 1024x768 desktop, which auto-resizes down to 640x480 when I launch the game.  When I turn off desktop emulation and allow wine to run WA fullscreen, I get no image, just a bunch of artifacts.

Any advice on how to get the game to work in a higher resolution?

---

### Post by hikaricore on 2008-11-22
On my media server I'm running WINE version 0.9.48 to get the most out of Worms Armageddon.
I'm currently running it at 1360x768 with few troubles.  My starting screens are 
off-centered a half inch or so but once I'm ingame it's perfect.

Not sure if this will help you, but it's worth a shot.

---

### Post by Lomendil on 2008-12-03
Hello.

I can't get the game to work, it keeps showing me a black screen. I would greatly appreciate if you could give me a link to your ddraw.dll, it's a very hard one to find for Wine 1.0.1

Thanks ! :)

---

### Post by hikaricore on 2008-12-03
You'll likely need to compile the dll yourself if it's not here: [http://glados.iwanek.co.uk/dokuwiki/projects:wine-hacks](http://glados.iwanek.co.uk/dokuwiki/projects:wine-hacks)

If you can use a lower version number of WINE you'll have much better luck.

---

### Post by Lomendil on 2008-12-05
As it seems to be 404, i'll try to see if I can compile it myself.

---

### Post by cthulhuuk on 2008-12-24
> **Lomendil said:**
> As it seems to be 404, i'll try to see if I can compile it myself.
my site was under maintanance that day - sos about that - lots of new versions of the binary are being uploaded :-)

---

