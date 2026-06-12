---
title: "software suggestions"
date: 2006-09-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by McMarley on 2006-09-03
hi,
i wanted to run a game on my computer, but since its windows based i was wondering which virtualisation programm (WINE, XEN... ) is best.
or is just the best thing to do is get a tiny XP partition?
which is the simplest and best XP virtualisation program??

ty all

---

### Post by John.Michael.Kane on 2006-09-03
You can try wine theres no guaranty it will work. theres also transGaming’s cedgea which i believe is a pay to use program.

---

### Post by Kilz on 2006-09-03
> **McMarley said:**
> hi,
i wanted to run a game on my computer, but since its windows based i was wondering which virtualisation programm (WINE, XEN... ) is best.
or is just the best thing to do is get a tiny XP partition?
which is the simplest and best XP virtualisation program??

ty all

Running a game on a virtual machine may work, but more likely it will run slow if at all. What game are you trying to run? If its a modern game like WOW, forget it. If its elf bowling you may be able to do it.

---

### Post by McMarley on 2006-09-04
ok thanks
it is a pretty modern game, so i'm not going to try and virtualisation.
i'll just use a separate XP partition
I hve also had an other problem which is that some internet sites have
videos i'd like to see and when I try to see them a message comes up
saying that i need windows to see them. what should i do????

---

### Post by kuja on 2006-09-04
Dependant on the game, of course, you could look it up in the [Wine Application Database](http://appdb.winehq.org), just to see if it will run in wine.

---

### Post by McMarley on 2006-09-04
I dont realy want to spend alot of time setting it up, ill just use XP
but what about the online videos?

---

### Post by kuja on 2006-09-04
Time?? You're a bit ill informed on the part of this one. I installed wine and had diablo 2 installed and running in it inside of ten minutes :)

If the online videos use proprietary codecs (wmv being the main culprit), you can try using mplayer32... there's a howto for it somewhere around here... I'll dig it up. Then again, this probably works a bit better in Kubuntu (kmplayer-konq-plugins :)) ---- [http://www.ubuntuforums.org/showthread.php?t=188974&highlight=wmv+amd64](http://www.ubuntuforums.org/showthread.php?t=188974&highlight=wmv+amd64)
If you mean flash videos online... well, there's always flash player 7, which'll work in 32-bit browsers like Opera, or a 32-bit firefox, whichever tickles your fancy. Supposedly other methods around too, but I've not tried them since breezy, so I won't comment. Shame is Flash player 7 is a little out of date though.

--Edit: Also note, Wine is not actually a virtualization program. See the first paragraph or two of [this page](http://winehq.org/) to see what it actually is. Seeing as it isn't a virtualization program, there isn't a slowdown.

---

### Post by McMarley on 2006-09-06
thanks but how do I get flash player 7?, I tried synaptik but it doesnt find anything...

---

### Post by kuja on 2006-09-06
Well, I'm not sure if there's a more "ubuntu-ish" way or not, but you can always just go to adobe.com and download it from there (like I did). It will come in an archive file (I forget which format), extract it with the tool of your choice (In Kubuntu it would be Ark, but I don't know the Gnome equivalent). There will be two files you need in it, copy flashplayer.xpt and libflashplayer.so to the directory /home/yourusername/.firefox/plugins.

Assuming you have your (32-bit) browser set up, that should get it working. If not, Kilz has some information on Firefox in his signature, else, you can get Opera from their website. The easiest way to get it is to get the "static deb" from their site, and install it in a terminal with "sudo dpkg -i --force-architecture opera*deb".

Whatever tickles your fancy.

---

### Post by Kilz on 2006-09-06
> **kuja said:**
> Well, I'm not sure if there's a more "ubuntu-ish" way or not, but you can always just go to adobe.com and download it from there (like I did). It will come in an archive file (I forget which format), extract it with the tool of your choice (In Kubuntu it would be Ark, but I don't know the Gnome equivalent). There will be two files you need in it, copy flashplayer.xpt and libflashplayer.so to the directory /home/yourusername/.firefox/plugins.

Assuming you have your (32-bit) browser set up, that should get it working. If not, Kilz has some information on Firefox in his signature, else, you can get Opera from their website. The easiest way to get it is to get the "static deb" from their site, and install it in a terminal with "sudo dpkg -i --force-architecture opera*deb".

Whatever tickles your fancy.

The manual part of my firefox howto will work for installing the pulgins into Opera, someone tried it ahile back. You will just have to change the locations to wherever Opera stores its plugins.

---

