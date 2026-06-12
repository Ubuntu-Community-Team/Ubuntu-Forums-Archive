---
title: "need help booting to text mode."
date: 2006-01-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by zenlakin on 2006-01-18
Ok. I am new to linux and I have windows xp and kubuntu dual booted. When I select kubuntu from GRUB it just boots to a blank screen because I have some issues with the video chip on my laptop that I need to resolve. My question is how do I boot kubuntu to text mode so I can edit my xconf file? Thanks.

---

### Post by 23meg on 2006-01-18
Choose recovery mode in the list of kernels presented in the GRUB menu. This will log you in as root into single user mode.

---

### Post by zenlakin on 2006-01-18
haha, I knew it would be any easy answer. Now all I need to do is get the xconf file working with my video chip on my laptop. Which I have heard is a real pain in the arse.

---

### Post by zenlakin on 2006-01-19
Have you had any experience with the issue of X not starting on a laptop with the ati 200m graphics chip?

---

### Post by Hygelac on 2006-01-25
ATI 200M?  I have one of those in an HP zv6000, and it would only boot in text-mode on start-up.  My situation sounds a bit different from yours (I never had GRUB boot to a blank screen with the default ATI driver, although I still have that problem with the FGLRX driver), but a good temporary solution (which gets you running X but without the full fancy hardware acceleration of the graphics card, which requires a working FGLRX) is to add the "Option" of "NoAccel" to the "Device" section.  Mine looks like this:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option		"NoAccel"
EndSection
```

Does that help?  If it does, you can see its limitations if you try to run some of the default screensavers (the fanciest ones overwhelm it; although none of this is a problem if you aren't going to need such features anyways).  I'm new too, so that's about all I would know how to do for this.

---

### Post by gba3 on 2007-05-05
I need to boot up in text mode too.
The only problem is that I don't have no other OS installed (no GRUB and thus no options to choose).

The reason why I need it...
I was trying to configure my monitor's refresh rate (freq was only 60Hz on CRT monitor) and messed up xorg.conf file. Now it doesn't show anything. I hope text mode will be the solution.

---

### Post by coolcalt on 2007-05-05
boot from your live cd, (ubuntu install disk), you should be able to look at your filesystem.  

I say the next bit because I'm really new and just don't know the exact files or problem.

Find the file xconf er whatever, prolly best to search on black screen at boot too,

---

### Post by ronocdh on 2007-05-05
> **coolcalt said:**
> boot from your live cd, (ubuntu install disk), you should be able to look at your filesystem.  

I say the next bit because I'm really new and just don't know the exact files or problem.

Find the file xconf er whatever, prolly best to search on black screen at boot too,
This is indeed the best method if you've no other OS installed. Once in the live CD, you can mount your hard drive's installation of Ubuntu and edit what's necessary there, such as your xorg.conf.

It would be helpful to reconfigure xorg, but you may have to do a chroot to do it. Careful with that.

---

