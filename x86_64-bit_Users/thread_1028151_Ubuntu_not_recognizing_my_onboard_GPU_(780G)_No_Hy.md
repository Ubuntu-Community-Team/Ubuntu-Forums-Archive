---
title: "Ubuntu not recognizing my onboard GPU (780G) No Hybrid Crossfire"
date: 2009-01-02
forum: x86 64-bit Users
---

### Post by Bloemetjesgordijn on 2009-01-02
Hi,

On my Motherboard I have an onboard GPU (780G) and a descrite graphicscard.

With the new ATI Catalyst drivers (8.12) I should be able to have ATI Hybrid CrossfireX. 

As for some reason Ubuntu does not recognize my onboard GPU.

The Onboard works..., as during boot I get all kinds of normal Ubuntu / Grub messages. However, as soon as Ubuntu starts, I have a black screen with the monitor connected to onboard GPU. Leading me to beleave Ubuntu cant recognize my onboard GPU

Please help me...I would like to make use of Hybrid Crossfire

Specs

[HTML]Motherboard: GA-MA78GM-S2H
Add Graphicscard: HD 3450
Ubuntu 8.10
ATI driver: ATI Catalyst 8.12
Output messages in console: 
HTML Code:
aticonfig --lsa[/HTML]

[HTML]* 0. 01:00.0 ATI Radeon HD 3450
* - Default adapter
HTML Code:
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3450[/HTML]

All help is appreciated

Cheerz

Bloemetjesgordijn

---

### Post by gabrielaca on 2009-01-03
sorry can`t help you, i just need the same info you`re asking `cause i`m upgrading.

---

### Post by Bloemetjesgordijn on 2009-01-04
Well Thanks I guess :-)

I know for others it works....for some reason my GPU HD3200 isnt recognized

Hope someone in this forum helps out.

cheerz

Bloemetjesgordijn

---

### Post by lyricalpapa on 2009-01-04
Don't bother with Crossfire X for now. The consensus on the forums is that there's still too many conflicts between the current kernel code and the video driver code (ATI and N-Vidia) to make it work. 

By Crossfire X, I'm referring to making an onboard video chip (eg ATI 3200) work with an ATI video card (eg ATI 3450) installed in a PCI-e slot.

I worked on this all through the summer and fall, getting input from the Fedora, Suse, Gentoo, Ubuntu, ATI, N-Vidia, Linux Kernel and other forums.

Somewhere along the line in November (I believe it was after installing Envy), I was able to get the kernel to recognize both the PIC-e and onboard video chips and was able to get Crossfire X option to show up in Catalyst 8.12. The system was slow and very unstable.

The first kernel upgrade immediately after that everything completely stopped working (eg wouldn't boot at all).

By the way, I was able to load Ubuntu 8.10 by inserting "iommu=noaperture" in the grub bootup. But I still had flickering. It turns out that since kernel 2.6.26 it might also help some hardware configurations to insert "nopat" in the grub bootup. There's a lot of new changes being made to the kernel that apparently conflict with the new ATI and N-Vidia drivers. 

For the time being I'm not worrying about Crossfire X.](*,)

BTW If you have two video cards in PCI-e slots, you may still be able to run standard Crossfire under Linux. It's the memory access between a 32-bit PCI-e controller with the 64 bit memory on the MB that may the issue.

---

### Post by gabrielaca on 2009-01-05
thanks LyricalPapa:)

---

### Post by Bloemetjesgordijn on 2009-02-06
Hi

According to the release notes of the new 9.1 ATI drivers, Crossfire is supported for Ubuntu 8.10. ([link]("http://ati.amd.com/support/drivers/linux64/linux64-radeon.html"))

I tried this, but I am still getting after running “aticonfig --lscc” that the CrossFire candidate adapters are listed as “none” :(

Does anybody had any success???

Cheerz 

Bloemetjesgordijn

---

### Post by Bloemetjesgordijn on 2009-02-09
Bump

---

### Post by dburnett77 on 2009-02-09
> **Bloemetjesgordijn said:**
> Hi,

On my Motherboard I have an onboard GPU (780G) and a descrite graphicscard.

With the new ATI Catalyst drivers (8.12) I should be able to have ATI Hybrid CrossfireX. 

As for some reason Ubuntu does not recognize my onboard GPU.

The Onboard works..., as during boot I get all kinds of normal Ubuntu / Grub messages. However, as soon as Ubuntu starts, I have a black screen with the monitor connected to onboard GPU. Leading me to beleave Ubuntu cant recognize my onboard GPU

Please help me...I would like to make use of Hybrid Crossfire

Specs

[HTML]Motherboard: GA-MA78GM-S2H
Add Graphicscard: HD 3450
Ubuntu 8.10
ATI driver: ATI Catalyst 8.12
Output messages in console: 
HTML Code:
aticonfig --lsa[/HTML]

[HTML]* 0. 01:00.0 ATI Radeon HD 3450
* - Default adapter
HTML Code:
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3450[/HTML]

All help is appreciated

Cheerz

Bloemetjesgordijn

I looked into this, neither Hybrid Crossfire, nor Nvidia's option of dual cards is supported via onboard GPU's.  At this time, there is some interest, and there may be an option.

There are some programs that will allow you to utilize the GPU's processor time for other tasks non-video related, but not for graphics.

Typically, for the market-shares, these things take about 1/2 year to be compiled for the open-source market.  So, exercise patience.

---

### Post by Bloemetjesgordijn on 2009-02-10
> **dburnett77 said:**
> I looked into this, neither Hybrid Crossfire, nor Nvidia's option of dual cards is supported via onboard GPU's.  At this time, there is some interest, and there may be an option.

According to the new driver specs (Ati 9.1) Hybrid crossfire is supported on Ubuntu 8.10 [link]("http://www.linux-gamers.net/modules/news/article.php?storyid=2528")

> **dburnett77 said:**
> 
Typically, for the market-shares, these things take about 1/2 year to be compiled for the open-source market.  So, exercise patience.

Patience isnt one of my virtues :-)

---

### Post by bregale on 2009-02-10
crossfire is a problem at the moment i dont use it on ubuntu but did you say you are using a, on board graphics card ? and not crossfiring through pci.

---

### Post by itendo on 2009-02-10
As far as the ATI element, you can only Crossfire Discrete GPUs. You can't use the on-board card in the array (97% positive anyway).

As far as your motherboard, i was looking into it and couldnt find reference to it being Crossfire or SLI compatible, and looking at the AMD Southbridge, i dont think that it is because i would have expected more mention in the specs. typically the mobos try to get you that way, but on newegg ([http://bit.ly/1It4Uk](http://bit.ly/1It4Uk)) and two others i found no mention.

Do you have doc on the mobo being Crossfire compatible?

---

### Post by terranz on 2009-02-11
I have the chipset is question and am using hybrid crossfire in windows with the onboard 3200 and a discrete 3450.

The only way I can start x in ubuntu 8.10 is to disable surround view in the bios before i boot linux.

with surroundview enabled I am dumpped to the console with a complain about having no memory hole.

In the morning I will try this
> By the way, I was able to load Ubuntu 8.10 by inserting "iommu=noaperture" in the grub bootup.
from the last page.  I don't care about having crossfire in linux but I want to dual boot without having to change a bios setting every time.

---

### Post by terranz on 2009-02-11
Well I typed "iommu=noaperture" into the menu.lst file (don't know it it was the right place and I got the same error telling me I need a memory hole.

I dont have an aperture option in my bios so I'm stuck

---

### Post by Davidovitch on 2009-02-14
I have the same problem here (780G with HD 3450)
result of aticonfig --list-adapters:
```
* 0. 01:00.0 ATI Radeon HD 3450

* - Default adapter


```
and corresponding aticonfig --list--candidates 
```

Master adapter:  0. 01:00.0 ATI Radeon HD 3450
    Candidates:  none

```

So the 780G graphics unit isn't working at all

I saw on the Phoronix forums that somebody succeeded in getting it to work, but he didn't mentioned how...
[http://www.phoronix.com/forums/showthread.php?t=15110&page=8](http://www.phoronix.com/forums/showthread.php?t=15110&page=8)

---

### Post by Bloemetjesgordijn on 2009-02-16
Thx you guys,

I am glad I am not the only one with these problems.:evil:

I allready made a bug report @ ATI, but the didnt react.


Cheerz

Bloemetjesgordijn

---

### Post by Reeman on 2009-02-16
Try the command.. "sudo aticonfig --initial -f" if you have not already done so. Sounds like you installed the right ati drivers but missed the fact that it does not automatically change /etc/x11/xorg.conf ...post your xorg.conf file if you have issued the command. I ran into the same thing myself until I went to the AMD/ATI web site and read the docs. The automated Ubuntu installs of the ATI drivers can mess things up big time. I did a manual install instead using the newest drivers from AMD and got really good results.

---

### Post by BB2008 on 2009-02-16
> **Bloemetjesgordijn said:**
> Thx you guys,

I am glad I am not the only one with these problems.:evil:

I allready made a bug report @ ATI, but the didnt react.


Cheerz

Bloemetjesgordijn

Bloemetjesgordijn, I am in the same boat as you - I have a GA-MA78GM-S2H mobo which has ubuntu 8.10 installed on it. I ordered a ASUS EAH3450/DI/256M Radeon HD 3450 256MB 64-bit GDDR2 PCI Express 2.0 x16 HDCP Ready CrossFire Supported video card today from Newegg, should be with me in a couple of days. I want to enable crossfire after installing this card so I can watch x264 encoded media w/o the stutters that I get currently.

Have you tried the instructions on this link - [http://forumubuntusoftware.info/viewtopic.php?f=7&t=2336](http://forumubuntusoftware.info/viewtopic.php?f=7&t=2336). Dunno if these work, and honestly I am wary as the instructions do seem to take your system to the bleeding edge...

Please let me know when you are able to resolve the crossfire issue, I will deeply appreciate it. I will be watching this thread, but if you get a solution elsewhere, please send me a private message, or post it here as well.

Thanks and good luck!

---

### Post by Bloemetjesgordijn on 2009-02-17
> **Reeman said:**
> Try the command.. "sudo aticonfig --initial -f" if you have not already done so. 

Thnx Reeman I will give it a go. If my memory serves my right, I did the manual install.


@ BB2008
Sure, but I cannot give an update not sooner then Wednessday
Also thx for the link, I will try the instructions also

---

### Post by Davidovitch on 2009-02-17
So I installed the new 9.1 driver manually, as pointed out on [http://wiki.cchtml.com](http://wiki.cchtml.com). By the way, I have Ubuntu 8.04 64-bit and the 780G board with HD3450 discrete video card.

My xorg.conf file looks like this:
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "nl"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

When I try out to the list-candidates command, only my HD3450 appears in the list.

---

### Post by Bloemetjesgordijn on 2009-02-18
> **Davidovitch said:**
> So I installed the new 9.1 driver manually, ........By the way, I have Ubuntu 8.04 64-bit and the 780G board with HD3450 discrete video card.


If I am correct the ATI 9.10 should provide Hybrid Crossfire support for Ubuntu 8.10 (I dont have the release notes with me)


> **BB2008 said:**
> Have you tried the instructions on this link - [http://forumubuntusoftware.info/viewtopic.php?f=7&t=2336](http://forumubuntusoftware.info/viewtopic.php?f=7&t=2336). 

The solution as described in the link doesnot work. The driver used in Envy is ATI 8.5. ATI driver 9.1 is necessary for Hybrid Crossfire


> **Davidovitch said:**
> So I installed the new 9.1 driver manually, as pointed out on [http://wiki.cchtml.com](http://wiki.cchtml.com).

The solution as described in the link doesnot work. The only candidate found is my HD3450 graphics carrd not my descrete / IGP 3200 card

Bummer

So in short nothing helps, do you guys have any better news???

Cheerz

Bloemetjesgordijn

---

### Post by HeikoH on 2009-02-19
Hello everybody, Bloemetjesgordijn pointed me to this topic because I do have hybrid crossfire working with Catalyst 9.1. Let me talk you through the steps I have taken, perhaps this may help you to get it working. I did everything manually, but I think it should also work when using the graphical installer:

First some details about my system and OS:

[LIST][*]Ubuntu 8.04.2, 64 bits, fully updated
[*]Motherboard: Asus M3A78-EM, has an AMD 780G chipset and onboard HD3200
[*]Graphics card: Asus HD3450 with 512mb memory[/LIST]

The steps I took to install the driver (mostly I'm doing this booting in single user mode, but you could also do this from graphical mode):

[LIST][*]remove the old driver manually:
```
dpkg -P fglrx-amdcccle
dpkg -P fglrx-modaliases
dpkg -P libamdxvba1
dpkg -P xorg-driver-fglrx
dpkg -P fglrx-kernel-source
```
[*]I had to enable an option in the bios to use both videocards (I think it is called surround view on the Asus motherboard)
[*]generate the packages for Ubuntu: ```
./ati-driver-installer-9-1-x86.x86_64.run --buildpkg Ubuntu/hardy
# for Ubuntu 8.10 should be:
# ./ati-driver-installer-9-1-x86.x86_64.run --buildpkg Ubuntu/intrepid

```
[*]install the packages manually:
```
dpkg -i fglrx-kernel-source_8.573-0ubuntu1_amd64.deb
dpkg -i xorg-driver-fglrx_8.573-0ubuntu1_amd64.deb
dpkg -i libamdxvba1_8.573-0ubuntu1_amd64.deb
dpkg -i fglrx-modaliases_8.573-0ubuntu1_amd64.deb
dpkg -i fglrx-amdcccle_8.573-0ubuntu1_amd64.deb
```[/LIST]

What I did to configure the driver and setup crossfire:
```
aticonfig --initial --adapters=all -f # this forces a new configuration
aticonfig --lsa               # this now shows two adapters, the HD3200 and the HD3450
                              # it also shows a number for each adapter (probably 0 and 1)
aticonfig --lscc              # the crossfire candidates, shows also both adapters

aticonfig --cfa --adapter=0,1 # in this case card 0 is the master card,
                              # card 1 is the slave card. I think I use
                              # the HD3450 as the master card, so check
                              # with aticonfig --lscc which number it has

aticonfig --cf=on --adapter=0 # again, in case the mastercard of the chain
                              # has number 0 assigned, this should enable
                              # crossfire on the next start of Xorg

# after rebooting:
aticonfig --lsch              # this should show the crossfire chain using
                              # both graphics cards, and it should be
                              # enabled

```

What I have done besides this is checking my xorg.conf (/etc/Xorg/xorg.conf) to see if everything is setup correct by aticonfig. Make sure in the xorg.conf file the monitor/screen sections use the correct device (if according to xorg.conf a monitor is connected to your slave card, ie the HD3200, while nothing is connected to this card, you might boot in a black screen. So I checked if any monitors were listed that were not actually connected and removed them.


If (one of) the cards is not recognized by `aticonfig --lsa' you might try to reinstall the driver (including regenerating the packages) after removing `/etc/ati' directory. Regenerating the packages is necessary, otherwise complaints arise about some file in `/etc/ati/' are not found. I think these are regenerated when the packages are generated.

---

### Post by alejandro.mc on 2009-02-19
Would you be so kind as to post your xorg.conf? If possible comment on how the xorg.conf should be configured simply to use through the onboard vga without suffering strange issues?

Thank you a lot!

Many of us are having trouble with th 780g, but i think it's worth looking into solving all this; it has a much better perfomance with HD TVs (thx Avivo) than the nvidia alternative. At least that's my humble opinion, for what I've seen in MSW desks.

Thanks!!

Alejandro
Buenos Aires
Argentina

---

### Post by HeikoH on 2009-02-19
In my xorg.conf I have three device sections. One is for the internal HD3200. I have two HD3450 device sections because I also use the TV-out of the graphics card.

I think what happened on one of the occasions I tried to get this working, was that aticonfig created a Screen section that used the HD3200 as device and created a dummy monitor for that device (there was no monitor connected to the HD3200).

If you see a Screen section in your xorg.conf that uses the HD3200 (or the HD3450), while no monitor is connected to the HD3200 (or the HD3450). Remove that Screen section. So basically you should just look at your xorg.cong and check whether:

For each monitor you have connected:
[LIST]
[*]there is a Monitor section
[*]there is a Screen section that uses the Monitor section
[*]the device mentioned in the Screen section is the device to which the monitor is actually connected
[/LIST]

So, how do you know which device section belongs to which videocard?
Try:
```

lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
02:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3450

```

As you can see, in my case the HD3200 has BusID 01:05.0 (which translates in your xorg.conf too "PCI:1:5:0") and the HD3450 has BusID 02:00.0 (which translates in xorg.conf too "PCI:2:0:0"). Another way to find out what BusID your cards have (and see whether aticonfig recognizes both cards) is:

```

aticonfig --lsa
* 0. 02:00.0 ATI Radeon HD 3450
  1. 01:05.0 ATI Radeon HD 3200 Graphics

* - Default adapter

```


My xorg.conf looks like this (I replaced the auto generated names of the devices to make it a bit clearer):

```

# the server layout, this specifies two desktops, one on my normal
# computer monitor and one on my TV. I cannot drag windows from one to
# another, but I can move the mouse from one to another (the dual-head
# option of aticonfig creates such a configuration).
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

# my normal computer monitor
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

# monitor section for my TV
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "false"
EndSection

# device section for the HD3450
Section "Device"
	Identifier  "HD3450-0"
	Driver      "fglrx"
	BusID       "PCI:2:0:0"
EndSection

# also device section for the HD3450, but this is for the TV-out
# (hence the Screen option)
Section "Device"
	Identifier  "HD3450-1"
	Driver      "fglrx"
	BusID       "PCI:2:0:0"
	Option      "TVFormat" "PAL-B"
	Screen      1
EndSection

# device section for the internal HD3200
Section "Device"
	Identifier  "HD3200"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

# screen section for my computer monitor (uses the first HD3450 device)
Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "HD3450-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

# screen section for the TV-out (uses the device from the second HD3450 device section)
Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "HD3450-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

I hope this helps. Much more info I can't give I think. In my case it was also a bit of trial and error, and I found my pc booting into a black screen several times during the configuration.

Anyway, to get Crossfire working, at least aticonfig should recognize both devices and should tell you both devices are candidates for a crossfire chain (changing xorg won't help you if aticonfig does not see one of the devices).

---

### Post by Davidovitch on 2009-02-20
HeikoH, thanks very much for you input. I already looked in my bios to find the settings to switch on my on-board video, but didn't realize it had anything to do with Surroundview. After it was activated, I deleted and reinstalled the ati driver as before and now it works like a charm.

The **./ati......run** file did not work for me, I had to use **sh ati....run** to get it started. Don't know why.

Much appreciated your help, regards.

---

### Post by BB2008 on 2009-02-20
I did not have ati driver to start with, but I followed the driver removal instructions anyway, to be on the safe side

```
dpkg -P fglrx-amdcccle
dpkg -P fglrx-modaliases
dpkg -P libamdxvba1
dpkg -P xorg-driver-fglrx
dpkg -P fglrx-kernel-source
```

After doing this, I rebooted, went into the BIOS setup of my rig, enabled the surroundview option, and then booted up to a command prompt - I mean, I went from a GUI to a NON GUI desktop...is that ok??? Please help! :(

Bloemetjesgordijn, since you have the same board as mine (ga-ma78gm-s2h), have you been able to switch to surroundview and still boot up to a gnome desktop?

---

### Post by Bloemetjesgordijn on 2009-02-21
HeikoH, Thx very much


Comments for future reference.
1) first set your bios to surround
2) ./ati.... didnt work for me sh ati did work
3) I had to install some add dependencies (The reason could be, that I did a clean install of Ubuntu)

One question still left is:
how do I arrange that my HD 3200 is my primairy card
```

marc@htpc:~$ aticonfig --lsa
* 0. 02:00.0 ATI Radeon HD 3450
  1. 01:05.0 ATI Radeon HD 3200 Graphics

```

Should I change
aticonfig --cf=on --adapter=0
to 
aticonfig --cf=on --adapter=1

Sorry to ask this, I am a bit reluctant to try this out as I just had to do a clean install.

---

### Post by BB2008 on 2009-02-23
HeikoH, you rock!

Thankyou Bloemetjesgordijn as well for getting HeikoH to this thread!

I am now (X)firing on all cylinders! :guitar:

BTW, I found this post very helpful in resolving some of my earlier troubles when I was booting into a NON X (Commandline) environment - [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/267241](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/267241).

Peace to all!

---

### Post by Bloemetjesgordijn on 2009-02-24
> **BB2008 said:**
> 
Bloemetjesgordijn, since you have the same board as mine (ga-ma78gm-s2h), have you been able to switch to surroundview and still boot up to a gnome desktop?

BB2008

No, it failed. That is the reason I had to do a clean install.


By the way can you help me in the following:
One question still left is:
how do I arrange that my HD 3200 is my primairy card

Code:
marc@htpc:~$ aticonfig --lsa
* 0. 02:00.0 ATI Radeon HD 3450
  1. 01:05.0 ATI Radeon HD 3200 GraphicsShould I change
aticonfig --cf=on --adapter=0
to 
aticonfig --cf=on --adapter=1

Sorry to ask this, I am a bit reluctant to try this out as I just had to do a clean install.

---

### Post by HeikoH on 2009-02-24
> **Bloemetjesgordijn said:**
> HeikoH, Thx very much


Comments for future reference.
1) first set your bios to surround
2) ./ati.... didnt work for me sh ati did work


Thats correct, I always change the permissions on the file so it becomes an executable file:

```

chmod 700 ./ati-driver-installer-9-1-x86.x86_64.run

```

This makes the ati-driver installer readable, writable and executable for the user owning the file. Hereafter you can do:

```

./ati-driver-installer-9-1-x86.x86_64.run --buildpkg Ubuntu/hardy

```

> 
3) I had to install some add dependencies (The reason could be, that I did a clean install of Ubuntu)


Could very well be indeed, I used the Ubuntu `BinaryDriverHowto/ATi' the first time I installed the driver manually (see: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20for%20Ubuntu%208.04%20(Hardy)%20with%20ATi%208.443.1-1%20and%20above%20binary%20drivers]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20for%20Ubuntu%208.04%20(Hardy)%20with%20ATi%208.443.1-1%20and%20above%20binary%20drivers")). That also lists some dependency packages.

> 
One question still left is:
how do I arrange that my HD 3200 is my primairy card
```

marc@htpc:~$ aticonfig --lsa
* 0. 02:00.0 ATI Radeon HD 3450
  1. 01:05.0 ATI Radeon HD 3200 Graphics

```

Should I change
aticonfig --cf=on --adapter=0
to 
aticonfig --cf=on --adapter=1

Sorry to ask this, I am a bit reluctant to try this out as I just had to do a clean install.

If your config is like this and you want the HD3200 to be the master card in the crossfire setup, proceed as follows:

```

aticonfig --cfa --adapter=1,0 # the adapter that is listed first is the master card

# now you have created the chain, hereafter you have to enable it:
aticonfig --cf=on --adapter=1

```

A small table, of possible different setups. In the first case the HD3450 is recognized as device 0 and the HD3200 is recognized as device 1:

```

# assume if you execute aticonfig --lsa, you see the following:
aticonfig --lsa
* 0. 02:00.0 ATI Radeon HD 3450
  1. 01:05.0 ATI Radeon HD 3200 Graphics

# now you want the HD3450 to be the master card
aticonfig --cfa --adapter=0,1
aticonfig --cf=on --adapter=0

# now you want the HD3200 to be the master card
aticonfig --cfa --adapter=1,0
aticonfig --cf=on --adapter=1

```

Another possibility. The HD3200 is now recognized as device 0, while the HD3450 is recognized as device 1:

```

# assume if you execute aticonfig --lsa, you see the following:
aticonfig --lsa
* 0. 01:05.0 ATI Radeon HD 3200 Graphics
  1. 02:00.0 ATI Radeon HD 3450

# now you want the HD3450 to be the master card
aticonfig --cfa --adapter=1,0
aticonfig --cf=on --adapter=1

# or you want the HD3200 to be the master card
aticonfig --cfa --adapter=0,1
aticonfig --cf=on --adapter=0

```

One other personal experience I had when trying to install the 9.2 driver: I also have a tv connected as a second monitor. This tv causes lots of problems when setting up the driver. Changing options made Ubuntu boot up with a black screen (the pc completely crashed after rebooting, I also could not reach a command line with Ctrl-Alt-Fn). What I did was disconnect the cable of my tv. Install the driver, setup hybrid crossfire and if everything works: connect my tv again (you have to make sure though there are the correct sections for monitor, screen and device in xorg.conf to make this work).

---

