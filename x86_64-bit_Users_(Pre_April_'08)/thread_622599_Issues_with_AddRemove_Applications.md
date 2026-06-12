---
title: "Issues with Add/Remove Applications"
date: 2007-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by netsurfau on 2007-11-24
I´m having issues with installing applications with the Add/Remove interface.

The majority of applications wont install.  I keep getting the same error:
(using MPlayer Movie Player as example)

[I]Cannot install 'mplayer'

This application conflicts with other installed software. To install 'mplayer' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.[/I]

This even extends to a number of games I´ve tried to install.
There doesn´t seem to be any commonality with the apps that are rejected.

I´m not very ¨cluey¨ with how to use the Synaptic package manager & have no
idea where to even look for the conflicting software.  Or, even if it´s a single bit
of software or a number of them.

Your help (& guidance) appreciated (needed even :) ).

---

### Post by PmDematagoda on 2007-11-25
Open up the Synpatic Package Manager in System>Administration, then search and try to install the package "mplayer", if it gives any errors, post them.

---

### Post by netsurfau on 2007-11-25
Did get errors when I tried to mark the additional dependencies.

Error Message:

<i><b>Could not Mark all packages for Installation or Upgrade</b>

The following packages have unresolvable dependencies.
Make sure all required depositories are added and
enabled in the preferences.

mplayer:
 Depends: libartsc0 (>=1.5.0-1) but it is not installable
 Depends: libaudio2  but it is not installable
 Depends: libfaac0 (>=1.24clean) but it is not installable
 Depends: liblame0 (>=3.97) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable
 Depends: libmp4v2-0 (>=2.0.0+cvs20040908+mp4v2+bmp) but it is not installable
 Depends: libmpcdec3  but it is not installable
 Depends: libungif4g (>=4.1.4) but it is not installable
 Depends: libx264-54  but it is not installable
 Depends: libxvidcore4 (>=1:1.0.0-0.0) but it is not installable
 Depends: libxvmc1  but it is not installable
 Depends: mplayer-skins  but it is not installable </i>

Hope this gives you an idea to what´s going on.

---

### Post by PmDematagoda on 2007-11-25
Could you post the result of:-
```

cat /etc/apt/sources.list
```

---

### Post by netsurfau on 2007-11-25
Pardon me if I take a day or so to reply with info, I have three assessment 
items I have to finish.  One for today, one for Wednesday night & the other by Friday.

The Friday one has caused me a bit of a problem

To get the assessment done, I had to install M$ Windoze Server 2003.

So I installed it, and now I've lost my Grub menu - I know, I'm a dumb-***

How do I get it back?  I can't access my Ubuntu partition at all (I'm d/loading the 64bit 
Live version on my other desktop system).

The more I have to do with Windoze the more I love my Ubuntu.

---

### Post by netsurfau on 2007-11-26
I did a quick search for a fix to my ¨boo boo¨, and got Grub back & working.

Here´s the output of the sources list, as requested.
I´ve only copied in the entries that didn´t have the ¨#¨ at the start.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by georgeakasirius on 2007-12-02
Hey there sorry to interfere here..

But i had the same problem when i am trying to install many programs..

I am a new user to linux and am using ubuntu 7.04

Please help me too..

Mainly I wanted to install "WINE "

---

