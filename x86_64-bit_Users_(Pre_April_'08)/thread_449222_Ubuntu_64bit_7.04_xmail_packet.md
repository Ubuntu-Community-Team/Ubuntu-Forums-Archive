---
title: "Ubuntu 64bit 7.04/ xmail packet"
date: 2007-05-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by ian dobson on 2007-05-20
Hi All,

I've just installed feisty on my new Quad C2D system and all has gone quite well apart from one small problem and one major one.

Problem 1.
The onboard network card on my ASUS P5B (ATL1) wasn't recoganised by installation scripts, but when I manually loaded the ATL1 driver it worked, as a linux noob it took me sometime to solve that one but google is your friend.

Problem 2.
I would like to use xmail for my email (I know it's not the "normal" linux MTA, but linux is all about choices and as I already run xmail on a windows box (that this thing will replace). But when I do apt-get install xmail I get the following error:-
```

root@alpha2:/data/Xmail/config# apt-get install xmail
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  xmail
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/228kB of archives.
After unpacking 815kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package xmail.
(Reading database ... 19512 files and directories currently installed.)
Unpacking xmail (from .../xmail_1.22-5_amd64.deb) ...
Setting up xmail (1.22-5) ...
Starting XMail server: XMail.
I: Adding new domain.
ErrCode   = -148
ErrString = Controller response error
ErrInfo   = Resource lock entry not found
dpkg: error processing xmail (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 xmail
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now apt-get/dpkg complains that a package (xmail) is not correctly installed.

It looks as if the xmail packet is broken under 64bit feisty.

Regards and thankyou for all your help
Ian Dobson

---

### Post by ian dobson on 2007-05-20
Hi,

Anyone?

OK the xmail package is broken. Looks as if I'll have to install it from the source, not very comfortable but it's the only solution I can see.

Regards
Ian Dobson

---

### Post by ian dobson on 2007-05-26
Ok,

ended up doing a manual install using the info from here:- [http://www.linuxforen.de:80/forums/showthread.php?t=145931](http://www.linuxforen.de:80/forums/showthread.php?t=145931)

Regards
Ian Dobson

---

