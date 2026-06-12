---
title: "Hibernate problems"
date: 2007-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by ghettosamson on 2007-12-04
Good Day.
I recently dual booted xp and ubuntu gutsy gibbons. I had xp 1st and then installed ubuntu. Both of them are working fine, except for some features/functions. I would really like to be able to Hibernate my machine. So what happens is I click the Hibernate button, close the lid, then when I open the lid there is nothing I can do to get it back up. I try the power button, the space bar, etc.. nothing seems to work. This also happens with my sleep button. What can I do to fix this? Also, xp was never able to perform the consistency check after ubuntu resized the partition, ad everytime i start up xp, it tries to perform the consistency check and before it can do so it says, disk checking cancelled. What can I do to let it happen that way it will stop popping up and cancelling itself.
Thank you

---

### Post by azbarcea on 2007-12-05
hi

I haven't met this bug, but, 2 friends of mine happened to step on the same bug. One of them on the Kubuntu distro, and the other on Gentoo distro (very weird), and both having **reiserfs** filesystem.

What happend was that "hibernate" somehow destroyed the file system tree

What they did, was to rebuild the entire filesystem tree:

```

sudo reiserfsck --scan-whole-partition --rebuild-tree /dev/hda2

```

By the way ... you must replace "**/dev/hda2**" with the root partition "**/**"

I know is a rough solution, but please give feedback if this works

bye

---

### Post by ghettosamson on 2007-12-24
how can i find out the name of my root partition. i have xp and ubuntu dual booted.
thank you. happy holidays

---

### Post by ghettosamson on 2008-01-09
For anyone who cares, this fixed my problems.

This is the weirdest thing ever!

When I compare my Ubuntu 7.04 installation to my 7.10 installation the only thing I remember doing differently is using the restricted graphics driver for my ATI graphics card in Ubuntu 7.10 So I disabled the restricted driver in 7.10, rebooted the pc and hibernate works again!

Too bad to have to choose between using the (better) restricted graphics driver or the hibernate function, though.

Anyway, try it on your machine, it might work for you too...

(-And if anyone has an explanation for this strange behavior, please share. )

---

