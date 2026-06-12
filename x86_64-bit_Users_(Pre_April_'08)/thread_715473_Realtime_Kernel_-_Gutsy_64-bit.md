---
title: "Realtime Kernel - Gutsy 64-bit"
date: 2008-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by JammerPro on 2008-03-04
64-bit AMD Gutsy Gibbon installed like a dream on my homemade AMD64 Athlon machine with a MSI motherboard with the S3 Unichrome Pro VGA Adapter.

So, I thought I'd try ubuntu-studio. 

The linux-rt kernel simply doesn't work on my machine...

Everything seems to be going fine until Gnome is called then I get the black screen of death... and I wait, but nothing happens. I think X is not working properly.

Any suggestions would be appreciated.

I don't understand why the Gutsy generic kernel works, but the rt doesn't!

:confused:

---

### Post by dcstar on 2008-03-05
> **JammerPro said:**
> 64-bit AMD Gutsy Gibbon installed like a dream on my homemade AMD64 Athlon machine with a MSI motherboard with the S3 Unichrome Pro VGA Adapter.

So, I thought I'd try ubuntu-studio. 

The linux-rt kernel simply doesn't work on my machine...

Everything seems to be going fine until Gnome is called then I get the black screen of death... and I wait, but nothing happens. I think X is not working properly.

Any suggestions would be appreciated.

I don't understand why the Gutsy generic kernel works, but the rt doesn't!

:confused:

I have found the RT kernels more trouble than they are worth, I used to use the low-latency kernels (and before that compile my own with the CK patches) but now I just use the generic - this is especially important since I use the Nvidia drivers now.

You can try reporting the problems as a bug, or just send one of these to the people who build the rt kernel :tongue:

---

