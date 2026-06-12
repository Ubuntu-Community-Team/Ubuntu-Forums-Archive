---
title: "Accidental kernel change, Help!"
date: 2008-05-10
forum: x86 64-bit Users
---

### Post by painterh on 2008-05-10
I made a big mistake.  I just did a fresh install of Ultimate Edition 1.8 x64 (hardy), and had everything set up nicely. Then I used synaptic to install Virtualbox (I had Win XP set up on it in Gutsy).  I accidently installed the one for the server kernel, and I realized it before I did anything else.  I immediately removed it (again through synaptic), and restarted.  On reboot, Grub now presented me with only the server kernel boot option.  I booted up, and during bootup it was complaining a bit about the "image" but continued to boot into the "low graphics mode".  Apparently my video drivers got screwed in the process.  I do not want, and don't need to run the server kernel, but I cannot figure out how to undo what has happened.  When I look into the boot folder, this is what I see.(attached image)
If anyone has an idea how to restore the default kernel for 64bit Hardy, I would greatly the help.  I don't want to re-install.

+

---

### Post by Kilz on 2008-05-10
> **painterh said:**
> I made a big mistake.  I just did a fresh install of Ultimate Edition 1.8 x64 (hardy), and had everything set up nicely. Then I used synaptic to install Virtualbox (I had Win XP set up on it in Gutsy).  I accidently installed the one for the server kernel, and I realized it before I did anything else.  I immediately removed it (again through synaptic), and restarted.  On reboot, Grub now presented me with only the server kernel boot option.  I booted up, and during bootup it was complaining a bit about the "image" but continued to boot into the "low graphics mode".  Apparently my video drivers got screwed in the process.  I do not want, and don't need to run the server kernel, but I cannot figure out how to undo what has happened.  When I look into the boot folder, this is what I see.(attached image)
If anyone has an idea how to restore the default kernel for 64bit Hardy, I would greatly the help.  I don't want to re-install.

+

Install the generic kernel in synaptic, reboot into it , then remove the server kernel in synaptic.

---

### Post by painterh on 2008-05-10
Thanks Kilz; I used synaptic to remove server kernel.  It was a little confusing because apparently every kernel entry with the number 26.24-17 was for the kernel I accidentally installed.  There was 4 different entries with that number so I removed all of them.  Now my system boots just like it did before, and all is well in the universe.  There is another person in the Ultimate Edition forums that did the same thing so I will pass it on.  Thanks again!

---

### Post by painterh on 2008-05-10
Thought I better post solved because everything is working fine now.  Thanks again Kilz. cheers

---

### Post by Kilz on 2008-05-10
> **painterh said:**
> Thought I better post solved because everything is working fine now.  Thanks again Kilz. cheers

Your welcome, glad to help. :) I remember doing something similar long ago and I ended up reinstalling for nothing.

---

