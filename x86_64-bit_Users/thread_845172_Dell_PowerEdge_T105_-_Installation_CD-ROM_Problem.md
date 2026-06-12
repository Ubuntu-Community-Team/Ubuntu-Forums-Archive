---
title: "Dell PowerEdge T105 - Installation CD-ROM Problem"
date: 2008-06-30
forum: x86 64-bit Users
---

### Post by luksol on 2008-06-30
If you want to install Ubuntu (in my case it was a server edition) on DELL PowerEdge T105 and you are getting error message regarding CD-ROM (that it cannot be mounted) all you have to do is edit boot options when you are at the beginning of the process and add:

sata_nv.adma=0

at the end of boot options line.

Hope it helps anyone, I couldn't find a solution for a long time.

---

### Post by OneMixDJ on 2008-07-03
I'm just learning about Ubuntu, but I will take note of this.

I have a old Dell Poweredge 2200 server that currently running NT that I am considering replacing with Ubuntu Server.

I also have an old Compaq Presario that I'm considering Ubuntu Desktop.

Both will be used for DJ related tasks like Audacity, burning, and file storage (server).

I still have a lot more to read up on though.

---

### Post by Joril on 2008-10-07
Many many thanks, you saved me!

---

### Post by luksol on 2008-10-07
I'm glad you find it useful.

---

### Post by frozenfyer on 2008-10-09
It works! Tried it with 8.04 Server Edition AMD64 and it solved the cd-rom mounting problem.
Thank you x100! If you ever stop by Pittsburgh, let me know and I'll buy you lunch.

Out of curiosity, how did you find out about the fix?

---

### Post by luksol on 2008-10-10
I found this solution in one of the documentation files available on dell website, I think it was titled "Information Update" and it was a 'patch' to a manual.
According to it there is a fault within nvidia sata module implementation that causes error with T105 CD-ROM. above solution was given as a temporary workaround.
Also in several other places it was mentioned that it might be a DMA problem, but without any confirmation or solution given.

I hope my post saved you some time, I've spent several hours trying to find this solution.

---

