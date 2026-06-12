---
title: "Trying to get openchrome driver to work with 7.04 and X86 64"
date: 2007-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by jnutter on 2007-04-24
I've installed Feisty on a new machine with an MSI motherboard (AMD64x2 3800+ CPU) that has the K8M890 chip set and on board graphics. 

I can't get either the VIA or OpenChrome drivers to work. It only comes up with the VESA driver, which is slow and freezes up a lot. Both of those driver's are in Synaptic. I can't get either to work. I've searched extensively over the last few days and tried everything I could find. I don't understand what I am doing wrong. The drivers appear to be installed in Synaptic. I've switched between VIA and OpenChrome a few times, I can only have one or the other installed.  When I try to edit my xorg.conf and change 'vesa' to either 'via' or 'openchrome', the GUI no longer works and I end up putting the original xorg.conf back in place to get the GUI working again. 

LSPCI shows that it knows that I have the K8M890. Xorg just can't seem to detect it. 

Has anyone figured out a work around for this? 

Would I have any better luck if I were to buy an Nvidia based video card for my PCI express slot? 

Any help would be appreciated

John Nutter

---

### Post by kuja on 2007-04-29
You might need to do more than just change the driver in the xorg.conf (hard to say), try changing it by running the command "sudo dpkg-reconfigure xserver-xorg -phigh". Failing thisI doubt you'd have any trouble with an nvidia card. I'm unsure of the status of the GeForce 8s, but the 7s (with the exception of the 7800gs) and the 6s seem to be particularly well supported.

---

### Post by jnutter on 2007-04-30
Thanks nVidia card showed up today. Life is much better. 

I'm posting this in case anybody else with the onboard K8M890 find this thread while looking for answers. An nVidia based card is worth the money. I wish I had bought one in the first place instead of wasting a week trying to make the K8M890 work...

---

