---
title: "Titanium Powerbook w/ external display--is it possible? Help please!"
date: 2006-04-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by twoblackeyes on 2006-04-18
Hello,

I have an original titanium powerbook G4 (500Mhz) with a busted LCD that I recently replaced with a Macbook Pro. I have a spare LCD (Samsung Syncmaster) that I would love to attach to my old powerbook to use as a Linux machine. 

The powerbook's display is usable (but with several defect lines on it), and I have Ubuntu installed and running. When I boot my machine with the external plugged in, the ext. LCD flickers and briefly displays some startup text, but then goes dark. Can anyone point me in the direction of some solid instructions on how to get it to recognize my external LCD? 

Preferably, I would like to bypass the powerbook's LCD completely and only use the external display with the lid closed. If it's easier to set up a dual head system though I'd be willing to do that too. 

I'm pretty new with Linux (love it though, got Parallels VM running on my Macbook and Ubuntu is excellent). I'd really like to get a few more years out of this powerbook, so any help at all would be greatly appreciated. 

Thanks
I

---

### Post by hentaidan on 2006-04-20
Do you know what videocard is in the powerbook (ATI? nvidia?)?

What text do you see when it starts?

I have a 2005 iBook and all I had to do was add a few lines to xorg.conf (relatively easy), though it was in Dapper. I had trouble getting it to work in Breezy.

---

### Post by twoblackeyes on 2006-04-20
It has the ATI Rage Mobility 128 with 8MB of VRAM. The text on the screen is only visible for a split second and is partially obscured by the monitor's status display thing so I can't really read it. I'd be willing to install dapper if it's easier. Can you share what you added to your xorg file?

---

### Post by hentaidan on 2006-04-20
Sure, my iBook G4 xorg.conf is @ [http://yet-to.be/wordpress/2006/03/18/ibook-g4-radeon-9550-mirroring-on-ubuntu/]("http://yet-to.be/wordpress/2006/03/18/ibook-g4-radeon-9550-mirroring-on-ubuntu/")

It has an ATI Radeon 9550, using the ATI driver. Only problem I have encountered was with movies only appearing on the first screen. Second monitor needs to be plugged in at boot up for it to be detected, else just the original works.

---

### Post by davidmaxwaterman on 2006-04-22
[QUOTE=hentaidan]Sure, my iBook G4 xorg.conf is @ [http://yet-to.be/wordpress/2006/03/18/ibook-g4-radeon-9550-mirroring-on-ubuntu/]("http://yet-to.be/wordpress/2006/03/18/ibook-g4-radeon-9550-mirroring-on-ubuntu/")

It has an ATI Radeon 9550, using the ATI driver. Only problem I have encountered was with movies only appearing on the first screen. Second monitor needs to be plugged in at boot up for it to be detected, else just the original works.[/QUOTE]

Hey there. Does this sort of thing work for the svideo output too?

My Tibook has :

PCI:*(0:16:0) ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] rev 0

I figured if I connect the svideo connector (instead of the DVI), then that'd be the second monitor.

I get this in the /var/log/Xorg.0.log file :

```
(II) RADEON(0): Modes for CRT2: ********************
(--) RADEON(0): Virtual size is 640x480 (pitch 640)
(**) RADEON(0): *Mode "1280x854"
(**) RADEON(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) RADEON(0): Generating MergedFB mode list
(II) RADEON(0): Merged 1280x854 and 0x0 to 1280x854 (Clone)
(II) RADEON(0): Merged 1280x854 and 0x0 to 1280x854 (Clone)
(--) RADEON(0): MergedFB: Virtual width 1280
(--) RADEON(0): MergedFB: Virtual height 854
(**) RADEON(0): MergedFB: DPI set to (100, 100)

```

which makes it look like it's actually trying....

[here]("http://reality.sgiweb.org/maxw/tmp/ubuntu/")'s the complete Xorg.0.log file.

This is the most major thing missing for me. I've been running ubuntu for a few weeks, and this is the thing making me want to move back to OS X. Any help greatly appreciated!

Max.

---

### Post by twoblackeyes on 2006-04-23
[QUOTE=hentaidan]Sure, my iBook G4 xorg.conf is @ [http://yet-to.be/wordpress/2006/03/18/ibook-g4-radeon-9550-mirroring-on-ubuntu/]("http://yet-to.be/wordpress/2006/03/18/ibook-g4-radeon-9550-mirroring-on-ubuntu/")

It has an ATI Radeon 9550, using the ATI driver. Only problem I have encountered was with movies only appearing on the first screen. Second monitor needs to be plugged in at boot up for it to be detected, else just the original works.[/QUOTE]

I tried adding in the changes you used in your xorg.conf but i'm still only getting video on the powebook's LCD. The external goes to a gray screen immediately after pressing enter at the "boot:" prompt, but it only stays for about 3 seconds, after that everything just boots normally on my PB screen. 

Any ideas? I can post my xorg.conf if that helps, but i basically just made it match yours.

---

### Post by hentaidan on 2006-04-23
Hmm. All I did was hack away at xorg.conf, not really knowing what I was doing.

What did it for me was commenting out ```
Option		“UseFBDev”		“true”
```

Have you been to the site I linked to in the post ( [http://ozlabs.org/~jk/docs/mergefb/](http://ozlabs.org/~jk/docs/mergefb/) ) ? It explains the setup in detail, perhaps there is something in it that may help?

---

### Post by hentaidan on 2006-04-23
[QUOTE=davidmaxwaterman]Hey there. Does this sort of thing work for the svideo output too?[/QUOTE]
I'm afraid I don't know - my iBook only has the VGA output.

---

