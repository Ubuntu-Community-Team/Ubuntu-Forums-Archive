---
title: "Trying to get 7.10 x64 to run on a Dimension 8400"
date: 2008-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by drick on 2008-01-03
Hi,

I'm trying to get Ubuntu 7.10 X64 desktop installed on my Dimension 8400. When i start the installation dvd, it see's the hdd, and boots into the installer. it then starts the script, then kills the keyboard and monitor / halts the install.

i tried installing the server version on the same machine with the same BIOS settings, and it worked correctly. 

any suggestions?

---

### Post by ~LoKe on 2008-01-03
Have you tried the alternate install CD?

---

### Post by drick on 2008-01-03
> **~LoKe said:**
> Have you tried the alternate install CD?

no, i don't have that cd, and don't see it on the main ubuntu download site. i assume this is what you are referring to:

[http://cdimage.ubuntu.com/ubuntustudio/releases/gutsy/release/](http://cdimage.ubuntu.com/ubuntustudio/releases/gutsy/release/)

---

### Post by ~LoKe on 2008-01-03
It's right [here](http://www.ubuntu.com/getubuntu/download), but you have to check the box that says "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

---

### Post by drick on 2008-01-03
> **~LoKe said:**
> It's right [here](http://www.ubuntu.com/getubuntu/download), but you have to check the box that says "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

i'm pulling them down right now, and will give it a try.

---

### Post by Yellow Pasque on 2008-01-03
I have to ask the standard, "Did you md5sum your iso and verify your burn?"

---

### Post by drick on 2008-01-03
> **Temüjin said:**
> I have to ask the standard, "Did you md5sum your iso and verify your burn?"

no on the md5 (but it worked on another system), yes on the burn

---

### Post by drick on 2008-01-04
> **drick said:**
> Hi,

I'm trying to get Ubuntu 7.10 X64 desktop installed on my Dimension 8400. When i start the installation dvd, it see's the hdd, and boots into the installer. it then starts the script, then kills the keyboard and monitor / halts the install.

i tried installing the server version on the same machine with the same BIOS settings, and it worked correctly. 

any suggestions?

interesting, just for giggles i tried 7.1 server x64 and that one gets past the initial setup screen, and installs correctly?

i'm going to try the alternate cd's this am

---

### Post by ~LoKe on 2008-01-04
> **drick said:**
> interesting, just for giggles i tried 7.1 server x64 and that one gets past the initial setup screen, and installs correctly?

i'm going to try the alternate cd's this am

The alternate CD should work, then.  That's how it was for me, too.

---

### Post by drick on 2008-01-04
> **~LoKe said:**
> The alternate CD should work, then.  That's how it was for me, too.

grr, i spoke too soon... :mad:

[http://ubuntuforums.org/showthread.php?t=658232](http://ubuntuforums.org/showthread.php?t=658232)

---

### Post by ~LoKe on 2008-01-04
> **drick said:**
> grr, i spoke too soon... :mad:

[http://ubuntuforums.org/showthread.php?t=658232](http://ubuntuforums.org/showthread.php?t=658232)

Try the alternate anyways.

---

### Post by drick on 2008-01-04
> **~LoKe said:**
> Try the alternate anyways.

yup was planning on it, but i have a few questions about this before i do it.

q1 - which version?
32 bit or 64bit
client or server

q2 - what bios settings should i use?
RAID force on
RAID/AHCI
RAID/ATA
ATA/PATA combo mode

---

### Post by ~LoKe on 2008-01-04
> **drick said:**
> 64bit
Client
ATA/PATA combo mode

=]

---

### Post by Yellow Pasque on 2008-01-04
> no on the md5 (but it worked on another system)

You should REALLY make a habit out of doing that. It's worth the minute of your time or whatever it takes to type the command to avoid spending an hour (or more) trying to do an install with a corrupt source.

Oh, and just because it works with one system doesn't mean the iso was bit-perfect. It's possible that some code or data got corrupted that wasn't needed on one machine but may be needed on another (e.g a driver).

---

