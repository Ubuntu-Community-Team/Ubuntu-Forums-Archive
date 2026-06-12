---
title: "Can I use an older kernel"
date: 2007-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Thelasko on 2007-10-26
I'm finding the Gusty kernel doesn't play nice with my Core 2 Duo.  Everything runs at half the speed it should.  Is there some way to use the Feisty kernel in Gusty?

---

### Post by jpkotta on 2007-10-26
If you just upgraded from Feisty (you didn't do a clean install), the Feisty kernels will still be there.  Just hit ESCAPE or whatever the key is when the system boots, so you can get to the grub menu and pick your kernel.  But it's probably not the kernel's fault.  I'd put my money on some configuration that is independent of the kernel.  

If you did a clean install, it shouldn't be too hard to just find a linux-image package from packages.ubuntu.com.  You'll also want linux-headers and linux-restricted-modules.

---

### Post by Thelasko on 2007-10-30
Thanks for the help!

I did a clean install of Gusty (again) and this time it worked.  I don't know why I have so many install problems.

---

