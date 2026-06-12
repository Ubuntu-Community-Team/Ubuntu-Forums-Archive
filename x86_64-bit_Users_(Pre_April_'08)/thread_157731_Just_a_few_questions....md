---
title: "Just a few questions..."
date: 2006-04-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Toddney on 2006-04-09
Mmkay, so I'm using the Live CD of Ubuntu for a bit till i get the hang of it.  I would just like to know, I use iTunes for music in Windows, so what would be the best program to listen to my music with that's similar to iTunes in Linux?  Also does the new 5.1 Breezy install come with CD burner apps and common stuff like that?  These are my system specs and I wondered if you could tell me if you think that all the components would be recognized and I won't have to mess with any drivers of any kind:

AMD 64 3500
512mb ram
ATI Radeon 9800 Pro (I know the 3D graphics won't work but that's fine)
Soundblaster Audigy ZS2 (I remember the 5.04 version didn't have sound support was a major problem for me:-? )

I'm basically hoping they have fixed the sound issues from way back when (i think it was last summer) i last used it.  I also connect to the internet wirelessly through a Linksys wireless G adapter..think it will recognize it and i'll be able to get internet access right away?  

I know i'm asking a lot here, but it's just taking a bit to download so i figured i'd find out now until waiting for it to finish downloading.  Thanks so much!

---

### Post by aysiu on 2006-04-09
No Linux player compares to iTunes.
Just my personal experience.

You can try AmaroK, Banshee, Rhythmbox, Quod Libet, and XMMS, though.

---

### Post by Sutekh on 2006-04-09
[QUOTE=aysiu]No Linux player compares to iTunes.
Just my personal experience.

You can try AmaroK, Banshee, Rhythmbox, Quod Libet, and XMMS, though.[/QUOTE]
Agreed, I still can't find anything that can completely replace iTunes on its own.


[quote=Toddney]Also does the new 5.1 Breezy install come with CD burner apps and common stuff like that?[/quote]
Yes and no.  

For Ubuntu (GNOME) you can use [GNOMEBaker](http://gnomebaker.sourceforge.net/v2/), however it is not part of the default installation.  You will need to install it afterwards.

For Kubuntu (KDE) you can use [k3b](http://www.k3b.org/), this is part of the default installation.

You could use either application in either desktop too.



[quote=Toddney]These are my system specs and I wondered if you could tell me if you think that all the components would be recognized and I won't have to mess with any drivers of any kind:

AMD 64 3500
512mb ram
ATI Radeon 9800 Pro (I know the 3D graphics won't work but that's fine)[/quote]
You may need to do some configuring just to get the card working even without 3D support.  I don't know if you will for sure but you may.

You could try one of several HOWTO's to get your ATI card working, this is one inparticular for ATI Radeon 8500 and newer.

[Ubuntu Document Storage Facility - Install ATI Driver](http://doc.gwos.org/index.php/Install_ATI_driver)


[quote=Toddney]
Soundblaster Audigy ZS2 (I remember the 5.04 version didn't have sound support was a major problem for me )[/quote]
I think 5.10 will be a lot better.  My card SB 24bit Live didn't work in Hoary, but was fine in 5.10.  


[quote=Toddney]I also connect to the internet wirelessly through a Linksys wireless G adapter..think it will recognize it and i'll be able to get internet access right away?
[/quote]
This could be your biggest problem.  Can you provide more info on the model?

Try checking out this link for you card.

[Ubuntu Wiki - Hardware Suport - Wireless Netwrk Cards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

---

### Post by Toddney on 2006-04-09
Well the sound worked great, the only problem was the one you told me about, the Linksys wireless card was not detected.  I checked out that FAQ and it looks as tho i'll have to use a ?nisdwrapper?  or something like that...will it work with the AMD 64 Ubuntu build?  And how do I get it to work?  Can i try it from the live cd?  or will that not do me any good becuase it's not installed on the hard drive?

---

### Post by Sutekh on 2006-04-09
You need to install ndiswrapper-utils.

This package is on the installation CDs but not the LiveCDs. :(

No matter, you can still install stuff using the LiveCD, so long as there is space in your RAM (the LiveCD operates from it).   

You can install it using apt-get
```
sudo apt-get install ndiswrapper-utils
```

Then if you follow the ndiswrapper documentation on the wiki, you might be able to 'wrap' your wireless driver.

---

