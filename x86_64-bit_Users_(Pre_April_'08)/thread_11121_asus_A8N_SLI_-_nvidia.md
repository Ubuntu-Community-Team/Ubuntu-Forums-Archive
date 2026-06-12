---
title: "asus A8N SLI - nvidia"
date: 2005-01-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrf on 2005-01-13
Hi,

I've just managed to get warty running on a ASUS8N-SLI (nforce4) board. I'm impressed, because I assumed my best chance of getting a machine such a new chipset working would be gentoo, but no luck there (2004.3 doesnt recognize the SATA controllers). 

There were a couple issues : firstly ubuntu assigns eth0/eth1 the the network cards in a differing order to the gentoo live cds (causing a bit of head scratching till I realized what was going on). Secondly, xfree's nv module in warty doesnt work with my PCI-e card. The nvidia driver works fine (6111). 

The last remaining issue I have is this : [img]http://www.angryspaceyetis.org.nz/mrf/shot0000.jpg[/img].

texture corruption in quake, and I assume other games. I've tried upgrading to 6629 and it occurs identically there too.... any ideas?

thanks.

---

### Post by daniels on 2005-01-14
Yeah, the nv driver doesn't do it until X.Org in Hoary; you might need the 6629 nVidia driver from Hoary to do PCI-E properly also.  If there's any intrinsic problem with the board, it'll bloody well get fixed quickly, because there's one sitting on my desk, waiting for the CPU/RAM/case/X800XTPE to show up.

---

### Post by litbos on 2005-01-14
I have the same problem with enemy territory. I have a geforce fx5200 with k8v-x (ASUS).

did you have a solution ?

---

### Post by mrf on 2005-01-14
[QUOTE=daniels]you might need the 6629 nVidia driver from Hoary to do PCI-E properly also.[/QUOTE]

It seemed to work for me on 6111. But with this textures issue. Bleeding edge stuff I guess.

---

### Post by daniels on 2005-01-15
Unfortunately, because the nVidia driver is binary-only, I can't look at it to see what the problem is, or suggest a fix.  You'll have to ask nVidia, because they're the only ones with the code.

---

### Post by Tichondrius on 2005-01-31
I've got the A8N-SLI with 6600GT running warty-i386 perfectly with the Nvidia display driver version v6629.  I installed the 6629 driver using the nvidia packages (nvidia-kernel-source & nvidia-glx) from debian (see HOWTO forum for a step by step tutorial on how to install nvidia v6629 driver on warty). I haven't tried this on warty-amd64, but I think it should work just as well, because I know the v6629 driver works fine on hoary-amd64. The v6629 gives a significant performance boost. For audio, I had to downloaded the realtek ALC850 driver from ASUS website, and followed the included installation instructions, but you may be able to use the nvidia "unified" chipset drivers for linux (which support nforce4), available on nvidia's website. Networking seems to have been auto-detected and auto-configured fine by warty.

btw, I've got this board running a A64 3000+ at 2350 mhz on 1.6V with  2x512MB dual channel at DDR433.  You need to update the bios to a newer version  (>1002) to be able to overclock, but beware of the beta bios's available from ASUS - they are buggy as hell (horror stories abound on the net, and I also got slightly burned by it). Overall I would say it's a very good board, with solid performance, but like any cutting edge technology, it has its fair share of quirks and pitfalls, which you have to watch out for.

---

### Post by coolmike890 on 2005-05-22
Ah - I see now! Beware the nVidia unified driver. I should have realized ASUS would have one for the Realtek sound. The nVidia driver caused me grief. I'll try just the Asus drivers.

I've been using the 1008 series BIOS's. They're much improved over the early ones. Very solid - good options. I'm very impressed with this board.

---

