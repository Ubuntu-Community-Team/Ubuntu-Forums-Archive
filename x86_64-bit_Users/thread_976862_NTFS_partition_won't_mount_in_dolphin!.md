---
title: "NTFS partition won't mount in dolphin!"
date: 2008-11-09
forum: x86 64-bit Users
---

### Post by Sir Rodness on 2008-11-09
Hi All,

I decided to move from Ubuntu (happily working) to a new challenge of Kubuntu. Kubuntu is a tough cookie to crack when getting it up and running. Compiz install was a little trickier then I thought it would be along with some other querks (don't have any screensavers what the heck, anyway). But I really ran into a wall when I went to browse my ntfs partition. Kubuntu would not mount my NTFS Windows drive. It showed it, but I could not access it. I went to every forum, every site to find a fix. Edited the fstab with different combinations of other solutions used by other people with the same issue, verified that every single ntfs related program was installed and still nothing... what the hell!!

So I started looking for ntfs fixes on my own. In the end I did 2 things.

1. make sure ntfsprogs is installed
2. run ntfsfix (a command in ntfsprogs) specifying the difficult ntfs drive. (i.e. ntfsfix /dev/<ntfs drive>)

Voila my ntfs partition mounts in dolphin! Hope this is something that helps others out.

---

### Post by krazyd on 2008-11-09
hey, did you know that kwin has it's own desktop effects similar to compiz, making compiz unnecessary?

---

### Post by Sir Rodness on 2008-11-13
Really? Hmm, I'll try that sometime. However I moved back to Ubuntu. Kubuntu, though looks prettier I'd say, just doesn't get it done like Ubuntu does for me. Then again everyone has their flavour of linux they prefer.

Oh after some more testing the ntfsfix, it may have side effects on Windows ability to start up. Which is not surprising since windows infuriates me to no end. If it were for some just a couple things that I actually need windows for it would be gone forever!

---

