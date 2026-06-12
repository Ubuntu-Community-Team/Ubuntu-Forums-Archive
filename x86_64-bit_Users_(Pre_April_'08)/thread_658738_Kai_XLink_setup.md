---
title: "Kai XLink setup"
date: 2008-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by brianbjjohnson on 2008-01-05
I am trying to put [Kai XLink]("http://www.teamxlink.co.uk/") on Ubuntu so I could play Halo 2 online. I tried downloading the Linux (x86) version, but when I try to run the applications in it... Nothing happens! I looked at the file and it said it was an executable file type. I think that might be the problem. But I am not sure. Could somebody please show me how to make this work?!

---

### Post by devzero on 2008-01-05
> **brianbjjohnson said:**
> I am trying to put [Kai XLink]("http://www.teamxlink.co.uk/") on Ubuntu so I could play Halo 2 online. I tried downloading the Linux (x86) version, but when I try to run the applications in it... Nothing happens! I looked at the file and it said it was an executable file type. I think that might be the problem. But I am not sure. Could somebody please show me how to make this work?!

Hi,

I only got kaid run in the chroot32 same as skype.
then you can start gkaiui in the normal 64 bit environment

---

### Post by Kilz on 2008-01-05
> **devzero said:**
> Hi,

I only got kaid run in the chroot32 same as skype.
then you can start gkaiui in the normal 64 bit environment

chroot's are not needed since Dapper Drake. [Getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs") will install the missing 32bit libraries for 32bit applications.

---

### Post by devzero on 2008-01-05
> **Kilz said:**
> chroot's are not needed since Dapper Drake. [Getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs") will install the missing 32bit libraries for 32bit applications.

I Installed them, Teamspeak works with that libs.

But kaid tells me:

sudo ./kaid
KAID: Kai Engine for Linux is initialising...
Floating point exception

in chroot u get:

sudo ./kaid
KAID: Kai Engine for Linux is initialising...
KAID: Kai Engine for Linux is starting...
THREAD: Engine thread started...
THREAD: Packet sniffing thread started...
THREAD: Orbital stream thread started...
THREAD: Datagram server thread started...
KAID: Kai Engine for Linux has started...
UI: UI Attached...
ORBSTREAM: Orbital stream established...


you need to run that thing as root because it must
switch the desired NIC in promiscuous mode.

the Software, you connect to that net runs in usermode..

---

### Post by Cappy on 2008-01-05
Did you install using this post:
[http://www.teamxlink.co.uk/forum/viewtopic.php?p=164765&sid=d03829309c2114950665e38f40943510](http://www.teamxlink.co.uk/forum/viewtopic.php?p=164765&sid=d03829309c2114950665e38f40943510)

According to this post [http://community.livejournal.com/ubuntu_users/269013.html](http://community.livejournal.com/ubuntu_users/269013.html) one of the files was corrupt and recompiling kaid fixed the problem

That is, of course, if you wanted to run it without a chroot. I've never used a chroot myself

---

### Post by devzero on 2008-01-06
hmm I may compile kaid, if I have a source of it.
But none of the people posted didn't have a link to the sources,
nor you get one from the xlink mainpage...

---

