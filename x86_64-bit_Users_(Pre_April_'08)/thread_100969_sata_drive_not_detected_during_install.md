---
title: "sata drive not detected during install"
date: 2005-12-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by jamuir on 2005-12-08
hello,

I just put together a new system last Saturday and was looking forward to installing breezy.  I downloaded and burned the amd64 install iso.  Unfortunately, the installer does not detect my sata hard drive :-(  This is the only hard drive in my system.

Here are my specs:

cpu: athlon amd64
motherboard: asus a8v-mx  (via chipset)
hard drive: maxtor 200 gb sata drive

My optical drive is installed as my primary master and the bios reports this correctly.  The bios lists the harddrive as something like "third primary IDE".

I've heard that sata support can be a problem with some kernels.  Is there some option I can give to the installer that might help it find the hard drive?

thanks,

-James

---

### Post by jamuir on 2005-12-08
I found the source of my problem.  It's the SATA controller on the asus a8v-mx motherboard:

southbridge VIA VT8251

It is **not supported in linux**.  Apparently, it does work in FreeBSD 5.4.

Some interesting discussion here:

[http://forums.viaarena.com/messageview.aspx?catid=28&threadid=68455&enterthread=y](http://forums.viaarena.com/messageview.aspx?catid=28&threadid=68455&enterthread=y)

Anyone else similarly afflicted?

-James

---

### Post by erikwithak on 2006-06-16
i have a similar problem

I have a Maxter 250gb sata harddrive. I had to disable my SATA ports to get ubuntu installed on my Dell dimension 8400. Now when i go back and turn them back on it wont boot. I get this "target file system doest have /sbin/init - can't access tty; job control turned off". I really want to get onto my second harddrive because it has all my music, movies, and photos on it. Anybody think they can offer some help?

---

### Post by ph8 on 2006-09-15
This is still happening with my SATA IIs on a Asus P5B Mobo with Edgy Knot 3

---

### Post by hexsel on 2006-10-04
Ack, Im also having this problem.  Core Duo with Asus P5B, SATA Maxtor 250GB, IDE DVD RW.  Actually got it to install with the lastest daily snapshot, but on first boot it gives me a GRUB error 21 (partition not found), which to me just means it's not actually recognizing the drive. 

There's mention of this on a "Core Duo" page in the wiki, but it doesnt appear to have a solution I can use.

[]s Gus

---

### Post by timvets on 2006-10-12
same problem here on the following hardware:
(just reading the prints on the mobo)

FSB 800
Presscott 800
compatible with Intel D4B & D4A processors
ASROCK DUAL CHANNEL
DUAL CORE CPU DDR 400
775i65GV

The SATA drive isn't listed in Device Manager.

I'll try to hook up an IDE disk and see if that works.
But it would be a pitty if I cant use this pc with its own SATA disk.
I'll try downloading a daily build of edgy and see if that's any better.
hope to find a fix for this soon...

gr,
Tim

---

### Post by timvets on 2006-10-12
Ubuntu edgy, latest ISO, finds the SATA drive

---

