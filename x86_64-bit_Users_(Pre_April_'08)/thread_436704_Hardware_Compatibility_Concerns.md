---
title: "Hardware Compatibility Concerns"
date: 2007-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by the_priest on 2007-05-08
Hey guys, I'm thinking of upgrading my pc system again. Been forever since the last upgrade :P

Anyway I'm just REALLY worried that the equipment I want won't be compatible. The last system I bought ran great under M$ but totally sucked in linux, I couldn't get 3d graphics nor surround sound. It was a old nForce2 with a ATI 9550X. Now I definitely don't want to make the same mistake again.

These are the components that I'm considering buying:
MSI K9N Neo-F mobo
3800+ AM2
GeForce 8600GTS PCIex
WD 320GB Sata (16mb cache)


Has anyone here used some or all of this equipment successfully with minimal hassles in Ubuntu???

Thanks for all the help.

---

### Post by ronacc on 2007-05-08
You shouldn't have any problem with that setup. I dont have that HDW exactly but I have 2 MSI mobos running feisty , a k8tneo2  / amd64 3000+  and a k9vgm / amd64x2 3800+ , the only problem I hit was linux didn't like the onboard VIA graphics  on the k9vgm , an nvidia 7300le cured that. Nvidia has the best graphics support for linux so the 8600gts will be fine, both propriatary and OSS video drivers are available and support 3D (beryl.compiz , etc). The amd 3800 and the drive are NP. I can't say anything about the sound I just use a basic sound system I have a tin ear so fancy sound would be wasted on me .

---

### Post by John.Michael.Kane on 2007-05-08
MSI K9N Neo-F  Reading the spec's on this it would seem your golden. 

3800+ AM2  You should have no problem with this processor.

GeForce 8600GTS PCIex  Looks like nvidia has not added this card to the linux driver support list.
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

WD 320GB Sata (16mb cache) This golden as well


You may have to hold off on the 8600 or wait until another member can vouch for it working under linux/ubuntu

---

### Post by Tanker Bob on 2007-05-08
NVIDIA has a new 100.14.03 beta driver out for 8600 support, but I don't know if it includes your specific card.  NVIDIA's Linux support forum [here](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14) may have more information for you on your specific card.

---

### Post by Cappy on 2007-05-08
I would go with a 3600+ Brisbane. You may not ever decide to overclock it but the brisbane is newer. It's also a bit cheaper ($65 or so).

---

