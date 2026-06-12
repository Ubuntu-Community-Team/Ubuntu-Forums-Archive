---
title: "UbuntuStudio fails check cd for defects"
date: 2007-11-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by phidia on 2007-11-28
I do know how to check an iso file and burn one-thanks-just getting that out of the way. 
I wanted to try ubuntustudio for amd64 and I've downloaded the 7.10x64 alternate iso image twice now-last time as a torrent. md5sum is ok for the iso but when I run the check cd for defects option from the cd on both cd's i've burned i get > The ./pool/multiverse/l/linux-meta/linux_rt_2.6.22.14.20_amd64.deb file failed the md5 checksum verification. Your CD-ROM or this file may have been corrupted.
Has anyone else seen this? Is it a bug or known issue? Thanks

---

### Post by stmiller on 2007-11-28
Have you tried verifying the CD burn in K3B, or whichever burning app you are using? The torrent should perform an integrity check so the iso you have should be good.

Maybe try burning at a slower speed.

---

### Post by phidia on 2007-11-28
I'm burning at the slowest speed & i've burned hundreds of cds/dvds without a hitch.

Anyway it just doesn't make sense that a bad burn could produce the identical error in two different iso's, one retrieved thru torrent, the other thru ftp.

---

### Post by ZachSka87 on 2007-11-28
I also was having this problem before settling for regular Ubuntu

---

### Post by phidia on 2007-12-01
Not sure if this info will be helpful to anyone else, but i rechecked the md5sum on the iso-it matched. So i tried burning to a dvd instead of a cd and that worked-i got a cd that passed "check cd for defects" I'm using the Ubuntu Studio install now.

---

