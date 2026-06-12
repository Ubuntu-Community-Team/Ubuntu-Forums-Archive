---
title: "Virtual Mac OS X under Linux??"
date: 2006-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by areitze on 2006-05-28
So I've been thinking...  mmm that is dangerous...  well anyway!, I have my whole Hard Drive set under Ubuntu...  I'm starting to gert thins to work as I want to...  but still i need to visit clients and need to show Mac OS running...  I work as an IT Consultant, specialized for Apple.   But am starting to see how I can start workling to offer the linux alternative..  Been out there and everytime I'm with a client seeing the alternative of Xserve and Xserve Raid, they have Linux running, and if a windows is there it's being migrated to linux, so maybe, I can start offering both...  I have all the contacts for distruibutors and enginiers that would set up the sistems...  so cool to have both running, but wish to keep linux as my primary sistem for now...  works, why wess with it...  been tinkering a lot latly to get it up and running as I like it..  and am almost there..

Been reading about Xen.  Under Intel Apple machines I can use Paralell to run virtual machines..  can I do the same with OS X here, plus adding windows, would'nt be bad...  just to show off this last one though...

Thx for any advice you have..  sure hope not to have to erase everything and partition my tiny 30Gb HD for SO X and Linux..

ARV.-

---

### Post by ssam on 2006-05-28
mac on linux is what you need, see [https://wiki.ubuntu.com/MacOnLinuxHowto](https://wiki.ubuntu.com/MacOnLinuxHowto)

the howto assumes that out have mac os x installed somewhere already, so its not exactly what you need.

i am 90% sure you can install mac os x on to a disk image. in linux everything is treated as a file, even hard disks. so you should be able to make a file a couple of gigs big and format is as hfsplus. then play with the MOL configs to point to that file instead of a /dev/hdaX. and to boot from /dev/hdc (and put the mac os x install disk in your cd drive.)

---

### Post by areitze on 2006-05-28
h well looked at it, thx for the idea, but it's not what I expected...  I've seen the new Intel systems running Paralel que it's great, good speeds, and it's that that I wish to do...  Is it posible under PPC or is it only for x86???

thx again..
ARV.-

---

### Post by kanzelsberger on 2006-05-28
[QUOTE=areitze]h well looked at it, thx for the idea, but it's not what I expected...  I've seen the new Intel systems running Paralel que it's great, good speeds, and it's that that I wish to do...  Is it posible under PPC or is it only for x86???

thx again..
ARV.-[/QUOTE]

MacOnLinux works only on PowerPC.

---

### Post by areitze on 2006-05-28
So MOL is the only thing I can do???  No other Alternative???   seems kinda complidated..  I llike that though, but don't have the time to make all the configurations, plus learn how to do it...  mmm  No other way???

Thx again,
ARV.-

---

### Post by ssam on 2006-05-29
you could use the ubuntu live cd to resize your linux partiton, you dont need to erase and reinstall.

you could look at qemu, but i dont think it would be any simpler. but for either i think you need to know the basics of the command line and editing config files.

---

### Post by EuroCity on 2006-05-29
QEMU (or, better, the *qemu-system-ppc* part) on the PPC is a real nightmare, for now; and slow as hell, emulating x86: if VPC is slow, QEMU is 10x slower! For a guest PC, it only supports Linux kernel 2.4, and OS X support from Linux is even worse, AFAIK.

So, at the current state of things, MOL would really be the only viable way to have OS X in a "virtual PC" sandbox from Ubuntu.

At least in Dapper, it shouldn't be too difficult to configure - and it even shows up as a graphical menu entry in the Debian menu (to be installed separately)! :) :cool:

---

### Post by gamgee911 on 2006-06-01
where are the mol-drivers-macosx ?!  I couldn't find them with synaptic or with apt-get.  please help?

---

### Post by stealth17 on 2007-05-12
With the arrival of Mac OSx x86 do you still need a PPC for MOL to work?

Sorry for old thread, only good one I could find on the topic.

---

