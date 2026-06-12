---
title: "re-install advice needed please"
date: 2006-03-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by outofnicks on 2006-03-07
I'm trying to install Ubuntu 5.10 on a B&W G3, dual-boot with Jaguar, on the 4th partition out of 5. The first install went good, but would not boot into Gnome--I could only get in to the shell. Never found out exactly why, but after messing around with different possible solutions, I decided to try a re-install after getting to a dead end and not even being able to log in to the shell.
So back to the install CD, I got to the partitioning and erased the root partition where Ubuntu was installed, thinking I could re-install over that. But I got stuck in a loop, with no way to continue I could see.
My goal as I see it is to get back the single partition I started with, as free unformatted space, using parted in the CD so I can start over fresh.

I just want to make sure I'm on the right track--so, should I erase the boot, root, and swap partitions created by the first install, then do a resize in parted to make it a single partition again?
Or can I go straight for the resize, starting with the start block for the boot partition and ending with the end block of the swap partition, to make it into a single partition? If so, which of the three partitions should I choose to resize?

Another problem I had during original partitioning was Ubuntu not allowing a swap size of more than 300-something mb, but my RAM is 768 mb. I just went with that the first time, not knowing how to make it right but this time I want to make the swap at least as big as my actual RAM.

But I need to get back to square one first. Advice, please?

---

### Post by ssam on 2006-03-07
if you delete the three partitions then you will be left with empty space. you can then create the partitions in the sizes that you want. you don't need to join up the free space.

the not being able to log into gnome may be because your PRAM battery is old and the clock is wrong. see [https://wiki.ubuntu.com/UbuntuDateBug](https://wiki.ubuntu.com/UbuntuDateBug)

---

### Post by outofnicks on 2006-03-07
Thanks, then I can just delete the install-created partitions, and start over--good news.

I'll check the pram battery, but I don't have any problems with the time in OS X. I think the battery is fairly new. I thought a brown screen was the sign of the  Date Bug, mine is black with an underscore at the top, and from there I could log in to the shell with Ctl-Opt-F1.

---

### Post by montablac on 2006-03-08
well,ive gained sumthing from this

IVE LERNT HOW TO CONVERT THE SCHOOL!

muhahahaha

---

