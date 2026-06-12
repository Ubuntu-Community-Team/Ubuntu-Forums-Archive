---
title: "Wine with Spore"
date: 2008-09-30
forum: Wine
---

### Post by xnerdx on 2008-09-30
Hey everyone!
   Here is the problem, I have spore and I have it installed on my laptop. The problem lies in the fact that wine will not let me load the game. I have an intel X3100 graphics card, which is a supported card, and according to the specs:
```
The GMA X3100 is the mobile version of the GMA X3000 used in the Intel GL960 and GM965 chipsets. The X3100 supports hardware transform and lighting, up to 128 programmable shader units, and up to 384 MB memory. Its display cores can run up to 333 MHz on GM965 and 320 MHz on GL960. Its render cores can run up to 500 MHz on GM965 and 400 MHz on GL960. The X3100 display unit includes a 300 MHz RAMDAC, two 25-112 MHz LVDS transmitters, 2 DVO encoders, and a TV encoder. In addition, along with the latest drivers, the product can support DirectX 10.0, Shader Model 4.0 and OpenGL 2.0.
```
That is a quote from wikipedia.

Okay, I try to load up the game in Wine and I get the following error message, Sorry your graphics card is below the min spec. The game will not run.

Here is a copy of my xorg.conf file which took a very long time to get it to run appropriately to setup compiz as well as raise the appearance settings on ubuntu.
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"intel"
	BusID		"PCI:00:02:0"
EndSection
```

Any idea?? Please help

---

### Post by HappyCheeze on 2008-09-30
> **xnerdx said:**
> Hey everyone!
 
Here is a copy of my xorg.conf file which took a very long time to get it to run appropriately to setup compiz as well as raise the appearance settings on ubuntu.



The X3100 is an integrated graphics card rather than dedicated, which means it's sharing a chunk of your system's ram instead of having its own. These make for poor gaming cards and pretty desktop effects because they just don't have the power of a dedicated card. 

I guess you could try going into your BIOS and see if you can assign more ram to it, but I don't know how much good that will do you. If you don't know how to access the BIOS let me know and I'll try to help you.

---

### Post by xnerdx on 2008-10-01
Thank you very much for the reply, I am currently running a Toshiba Satellite A205-S5000 laptop, walmart :). Anyways, it came preloaded with Windows Vista (GAG) as well as a "recovery disk" from Toshiba. What I did when I first received the system, in hopes to speed up the boot process I formated the HDD with the Toshiba backup disk, well that didn't do anything because they have all of their "bloat-ware" on the back up disk as well. So I tried to use my Dell "Windows disk" and it didn't quite work so I just decided to follow through with my idea of returning to my studies of linux. The laptop has 2 gig's of RAM, now of course I am not a normal windows user who thinks "I NEED MORE RAM" haha. But, if it is about devoting RAM to my graphics card that is not a problem, I have plenty and especially with linux :). I am currently running the latest version of Ubuntu's Kernal 8.04 Hardy Huron. I do not know exactly how to access the BIOS settings but I do know about the "F2" key on boot bringing somewhat of a BIOS menu. What do you think?

---

### Post by Archmage on 2008-10-01
Kindly note that Spore is a pice of DRM-sh*t that wont allow you to install it more then three times unless you call each time a expensive hotline and beg that you just allowed to install it one more time.

Trying it with differen Wine-configuration can make Spore to think that it had been installed on different systems and therefore push you above the tree times.

Therefore, unless you enjoy beging on expensive hotlines I would avoid Spore and Wine as an configuration. If you enjoy the expensive hotlines, I can give you the numbers of a few nice Ladies... ;)

---

### Post by xnerdx on 2008-10-01
Thank you for the tip but I think I have that under control ;) haha.

---

### Post by davidryder on 2008-10-01
> **Archmage said:**
> 
Therefore, unless you enjoy beging on expensive hotlines I would avoid Spore and Wine as an configuration. If you enjoy the expensive hotlines, I can give you the numbers of a few nice Ladies... ;)

It's an 800 #.

---

### Post by HappyCheeze on 2008-10-01
F2 is the usual default, it should say something like "Press F2 for setup". 

When you're in the BIOS you'll have to look for an option, I remember on my dad's comp, his BIOS have an "integrated" sections or "Integrated Periphreals" and you should be able to change the amount of memeory that is going into your GPU.

If your lappy came with a manual you can look in that or google your BIOS brand (ex. Phoenix bios) and see how to navigate it.

---

### Post by YokoZar on 2008-10-01
> **xnerdx said:**
> Thank you for the tip but I think I have that under control ;) haha.

You're not the first person to crack software legally owned in order to run it in Wine.

---

### Post by xnerdx on 2008-10-01
I opened up the BIOS, with F2, and there was absolutely nothing involving any graphics card related activity. Hell for that matter there was absolutely no possible BIOS edits except for things like "wake on lan", mainly enable/disable settings. It doesn't have anything about over clocking for sharing ram with GPU or anything. Any ideas?

---

### Post by xnerdx on 2008-10-01
I have looked around and found some Toshiba pages
[http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_modItemList.jsp?moid=2106078&rpn=PSAE3U&ct=DL&BV_SessionID=@@@@1776304602.1222892857@@@@&BV_EngineID=ccccadefflgmjefcgfkceghdgngdgnn.0]("http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_modItemList.jsp?moid=2106078&rpn=PSAE3U&ct=DL&BV_SessionID=@@@@1776304602.1222892857@@@@&BV_EngineID=ccccadefflgmjefcgfkceghdgngdgnn.0")

---

### Post by xnerdx on 2008-10-01
Ok, my BIOS are Phoenix TrustedCore. So here is the problem, I am pretty sure that these BIOS are "special" for Vista, so I need to know how to update the BIOS with another Phoenix BIOS through Ubuntu. Any ideas?? Please help!

---

### Post by Archmage on 2008-10-02
> **davidryder said:**
> It's an 800 #.

Not in all countries. In my country we pay 2 US$ for each minute.

---

