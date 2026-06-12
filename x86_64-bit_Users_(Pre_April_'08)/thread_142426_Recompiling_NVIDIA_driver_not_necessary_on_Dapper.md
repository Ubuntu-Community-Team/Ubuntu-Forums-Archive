---
title: "Recompiling NVIDIA driver not necessary on Dapper?"
date: 2006-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by AngryPanda on 2006-03-10
So, Dapper just updated the kernel, and I restarted the machine, all expecting to have to re-run the binary NVIDIA driver installer to keep my GNOMEy goodness going.

But GDM booted fine! UT2K4 ran beautifully!

What gives? I'm all for not having to recompile the driver every time, but I can't help but feel this has all been too easy. Any ideas?

---

### Post by klahjn on 2006-03-10
[QUOTE=AngryPanda]So, Dapper just updated the kernel, and I restarted the machine, all expecting to have to re-run the binary NVIDIA driver installer to keep my GNOMEy goodness going.But GDM booted fine! UT2K4 ran beautifully!What gives? I'm all for not having to recompile the driver every time, but I can't help but feel this has all been too easy. Any ideas?[/QUOTE]

Once i had the nvidia drivers installed for my machine, every time i've updated my kernel through apt-get or synaptic, i do not have to rerun the driver installation for nvidia in dapper.  I believe it was something i had to do in breezy, hoary, and warty, as well as countless other distros, but not in this release.  I'm assuming its just an "unnoticed" feature in this release.  I'm quite happy with this "feature"

---

### Post by Hatchetfish on 2006-03-11
I seem to recall some kernel updates that didn't require a change to the nvidia drivers in the past, and I've never installed dapper, so it must have been 4.10-5.10.  Also seems like once or twice it was mentioned in the security announcement that some specific kernel interface had changed, requiring driver updates for compatibility.  I think it's just dependant on the specific kernel changes in other words.

Not to say it's not something new, the nvidia-something-or-other to run after it installed was new as well.  It just might not be. ;)

---

