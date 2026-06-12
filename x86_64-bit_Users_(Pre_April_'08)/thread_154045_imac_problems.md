---
title: "imac problems"
date: 2006-04-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by kandr on 2006-04-02
hallo.
new to linux.
having problems.
installed breezy badger on my g3 imac 350mhz after trying yellow dog and mandriva.
yellow dog just wouldn't. mandriva ran even slower than breezy, and didn't look as good nor feel as good.
upgraded the memory by 512mb, thinking that would make a difference.
was right, it has. running a lot faster.
but having lots of problems.
applications freeze quite randomly. from mozilla to the gimp, to solitaire to update manager, they will all either freeze or not, drop themselves out of running back to the desktop, to have to start all over again.
the screen has started to dance from time to time, and much as i'm all for a party, it's a wee bit disconcerting when my computer's partying on its own.
have been reading the threads, and will try re-installing later to maybe check what the screen resolution is at, but i don't get a blank or black screen...
am quite perplexed about where to go forward, but don't want to give up on it
i re-installed breezy after upgrading the memory, maybe upgrading the sgram and harddisk will help, but i don't think that would explain why the applications are acting as they are.
installed it from an install disk, not livecd.
some applications just refuse to work, even after i've apparently upgraded them.
dvd's not recognised. minor inconvenience, but seems all part of the bigger picture.
anybody any ideas to help appease my gremlins?

---

### Post by stocksy on 2006-04-02
Hey there,

I'm having a lot of success with Ubuntu on my Bondi iMac using xubuntu.  Xubuntu is a version of Ubuntu for people like us who have older computers, take a peep at [https://wiki.ubuntu.com/Xubuntu](https://wiki.ubuntu.com/Xubuntu)

Essentially, one just does a server install by typing 'server' at the prompt when booting from the install CD.  When the base system is installed, just do:

$ sudo -s
# nano /etc/apt/sources.list
 (uncomment the universe lines)
# apt-get update
# apt-get install xubuntu-desktop
# reboot

---

### Post by kandr on 2006-04-06
thanks a lot.
have re-installed breezy since my last post - after fourteen attempts!?
screen not dancing anymore, and so far no application closures or freezes, however, still problems with many applications and some disturbing failures on start-up.
didn't write them down, and can't remember just now the specifics, but will try your advice on xubuntu tomorrow.
thanks again, let you know how i get on.

---

### Post by kandr on 2006-04-20
how long has this really been?

have xfce installed. 
it is in the main stable, but still crashing and dancing from time to time.
particularly whenever i'm trying to post something on this forum!!!!
or maybe it just seems that way...?
again it is mostly stable.
can't work out what needs tweaking,
on start up, there are several 'failed' boots.
probably most disturbingly  for me anyhow 'filemount' is always failed. 
got to go again.
will be back.

---

