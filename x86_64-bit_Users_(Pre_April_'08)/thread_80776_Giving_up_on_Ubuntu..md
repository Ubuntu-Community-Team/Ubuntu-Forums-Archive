---
title: "Giving up on Ubuntu."
date: 2005-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by kioshi on 2005-10-23
I was really looking forward to testing ubuntu and I've spent more than 10 hours reading articles and trying to install it.

I tried to install:

1) On a partition on my ext FW drive

2) On a partition of my internal HD

3) Erasing my insternal HD completely and installing only ubuntu

Problem is, everything always goes well until yaboot installation. It NEVER installs. And I've tried creating all the partitions myself and also letting the installer do it automatically, everything that you can imagine (non-commandline wise) I've tried.

Right now the Ubuntu system is in my third partition, hda3, and I just can't boot it because yaboot never manages to install in the bootstrap partition (number 2).

I guess, if not even a 'clean' install (I mean, with no other system in the disk) won't work, I'd better move out to Opensuse or yellowdog, all the articles about partitions and installing yaboot manually, or moving the partition's place, revolves around using commad lines through a shell, but the shell that comes with ubuntu installer has none of these commands.

I mean, how do I use pdisk, mac-fdisk? I don't even know which program to use that.

Sorry, I am terribly disappointed. If anyone could help me...

---

### Post by ssam on 2005-10-23
is this a newworld  or old world mac?

---

### Post by djjuice on 2005-10-23
hey i may not have had your problems.. but I give up using ubuntu as well on a PPC.. sound is distorted.. and there is no ATI support whatsoever for my 9800. I'll stay using a functioning OS on my mac.

---

### Post by Brian McConnell on 2005-10-23
[QUOTE=djjuice]hey i may not have had your problems.. but I give up using ubuntu as well on a PPC.. sound is distorted.. and there is no ATI support whatsoever for my 9800. I'll stay using a functioning OS on my mac.[/QUOTE]
I'm using an ATI Radeon 9800 Pro on my dual 1.8ghz G5, which runs Ubuntu.

---

### Post by Rxke on 2005-10-23
Try to switch off the ext. HD during install. People have reported succes this way...

---

### Post by Blue1k on 2005-10-23
Yes..you need to remove the external drive during install. 

I have the same problem with my SATA drive and PATA. I need to unplug my PATA drive while installing any Linux (or even WIndows) or the MBR is seen as the first sector on PATA instead of my SATA drive.

---

### Post by pauljwells on 2005-10-24
It's a shame to see these kind of posts. I came pretty close to giving up on Ubuntu too, but there is so much information and help out there that eventually I got Breezy on both a dual-display PC and a Mac laptop. I've learnt plenty and now when something goes a bit wrong it's more of a fun challenge than a headache! Don't give up!! Ubuntu is a fantastic OS and well worth the effort.

I'll echo one of the previous posts here though, which is to disconnect everything but mouse and keyboard before you try to install any new OS, linux, mac,  M$ or whatever. Don't make life more dificult than it needs to be.

---

### Post by bete on 2005-10-24
seems like ATI does not work "at all " on ubuntu...

 You can add x800pro and ATI Technologies Inc 264VT [Mach64 VT] to the "does  not work list"

---

### Post by daller on 2005-10-26
I'm having the same problem with YaBoot on my PowerBook G4 laptop...

I have no external devices plugged in!

Is this a general issue?

---

