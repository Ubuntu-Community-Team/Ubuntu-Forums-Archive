---
title: "locks up on install"
date: 2006-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by linedpaper on 2006-10-30
I'm trying to install 6.10 on my amd64 system, but things keep locking up.  I have tried 64bit desktop install and the alternate cd.  I have tried the regular cd in safe graphics mode as well as regular.  With the regular 64bit desktop cd the boot freezes while showing the loading bar for x.  With the text install on the alternate cd it fails when it gets to package selection.  Here's the thing.  I just booted up the 6.06 i386 cd and it worked fine.  It's just the amd64 cd's that seems to have a problem.  I'm downloading 6.06 amd64 version right now to give it a try.  Any ideas though as to why I can't get 6.10 x64 to boot up.  The gui boot is all black and white and distorted before it gets to x, but looks normail with the i386 cd.  I'm guessing it's a video card issue, just not sure where to go next.

Hardware:
Amd 64 3200
2gb ram
300gb hd
sb audigy
msi mobo w/nforce 250gb chipset
nvidia 5600fx

---

### Post by linedpaper on 2006-10-30
Well I was able to install 6.06 64 bit version.  I then upgraded to 6.10.  Everything seems to be working.  A few problems, there is something wrong with the video card drivers as the boot screen is all messed up and in black/white only, and it is giving me a max resolution of 1024x768.  Anyone have a problem like this with an nvidia card in 6.10?

---

### Post by tymek666 on 2006-10-30
I'm running Kubuntu 6.10 and i haven't any problems with my gf6600 card.
However, i had some hangs during install caused by cd error. I've downloaded it again and now works fine.

---

### Post by linedpaper on 2006-10-30
I had the same error with multiple cds.  the 6.06 cd worked though, now the boot screen looks all funky since I upgraded the 6.06 install to 6.10, so I'm assuming there is a graphics driver issue.  I haven't had too much time to look into since I did the upgrade though.

---

### Post by canuda10 on 2006-10-31
I have been using dapper for some time with excellent results.
Edgy locks up as you said, but I managed to have it running by adding the "-noapic" option (although logo is black and white etc, it manages to get to a running live cd, from where I can install ok).

---

### Post by linedpaper on 2006-10-31
yeah i got it installed now and everything seems to be running ok.  I had to install 6.06 and upgrade to edgy.  Everything works, but I still get the ugly b/w on the boot up, but then everything looks ok after that.  I need to do the nvidia config in x so I can get my resolution higher than 1024x768, but other than that it seems to all work.  Any idea on the b/w during boot though?  Not that it needs to be fixed, but it would be nice.  I'm assuming that it is a kernel issue.

---

