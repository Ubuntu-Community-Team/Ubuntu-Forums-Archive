---
title: "Wine Freezes System"
date: 2008-01-06
forum: Wine
---

### Post by Don S on 2008-01-06
Posted this in General Help, figured it would probably be better to post it here.

> It appears a lot people have issues with Wine freezing, but I can't seem to find an answer or a problem completely similar to mine.

I had Wine working perfectly 6 days ago. All my games and applications were running smoothly and I don't recall changing anything. Well, all of a sudden (this might've been because of an update), any game I ran with Wine froze up within 5 to 20 minutes (randomly each time) - mouse couldn't move, keyboard interaction weren't a possibility and so I couldn't close Wine or kill X or basically anything. I tried to reinstall Wine several times, and nothing worked, so I went ahead and did a complete fresh install of Ubuntu. I updated the updates the update manager had to offer, installed Wine, Audacious and a couple of other applications I had, even before the problem started and the problem still happens.

It seems that this is not actually related to an update to Wine, as I hadn't updated it. It's neither something I installed, as I've rebuilt my computer exactly as it were before, when Wine was working.

This might be related to some sound driver problem, though, as it's only an issue when running applications/games that requires sound. I've tried to configure the sound driver in any way I could figure (OSS, ALSA, both at the same time and without. Hardware and Emulation of sound etc.). So it might possibly be related to an update to the sound system, if there have been one recently, because the issue came out-of-nowhere and stays even after a complete reinstall of Ubuntu. It could also possibly be related to some issue with hardware getting damaged, but I highly doubt it, as everything non-Wine is working. But again, the problem stays, even without sound drivers enabled.

Help would be much appreciated.

- Don S.

---

### Post by Don S on 2008-01-06
No one knows an answer to this issue?

---

### Post by Don S on 2008-01-07
Still in trouble.

---

### Post by Don S on 2008-01-07
I would like some help on this topic.

---

### Post by Don S on 2008-01-07
So far, the problem appears to be solved, but it's only based on one test.

---

### Post by Wiifreak on 2008-01-08
Same problem on my computer:

Fresh install of Ubuntu.
When I install Wine with Add/remove software (in the menu) it gets installed, but **when I click on what so ever is from Wine my system freezes**.
Also when I instal the packages (Wine, Wine manager) I only get the pop-up screens with info and **when I click on create C drive my system freezes**.

Is this an error of Wine or being not compatable of Ubuntu.
(When I install KDE desktop environment the problem stays)

---

### Post by Wiifreak on 2008-01-08
@Don S: Relax, they will help you patience...

#Don't worry, ... , be happy!#:biggrin::guitar:

---

### Post by Wiifreak on 2008-01-09
Now I get impatience too...

---

### Post by Minigun on 2008-01-09
I have a similar problem: if I start anything from the Wine submenu (in a system applications menu) my system just freezes completely.

Xubuntu 7.10 here.

---

### Post by rudedcam on 2008-01-09
guys, I too have the exact same problem.
just updated from 6.o6 to 7.10 couple of days ago, installed wine but it freezes my system too.
glad i ain't alone:D

rudecam

---

### Post by happyhamster on 2008-01-09
Could you guys all give some more info on your setup? Specifically:
- ubuntu version  (in a terminal, type: uname -a)
- also if you're using ubuntu/kubuntu/xubuntu
- wine version (in a terminal: wine --version)
- how did you install wine? how do you run wine (terminal/menu/etc)
- which video driver: nvidia/ati/etc (and which version)
- sound card info, in a terminal: 
cat /proc/asound/cards
cat /proc/asound/modules

- any other info you think might be useful to start troubleshooting this :)

- also: when your system freezes, can you regain control of your box pressing:

Alt-r-SysRq

followed by:

Ctrl-Alt-Backspace

---

### Post by rudedcam on 2008-01-10
-Linux ***** 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
-ubuntu
-wine-0.9.46
-i installed/uninstall  wine with the terminal several times without success. I also downloaded 7.10-1_i386 then i tried 7.04-1_i386 from [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) double clicking on the package installing it without any success either.
I tried to run wine by the menu only (don't know how by the terminal)
-i do not know which video driver
- cat /proc/asound/cards
 0 [V8235          ]: VIA8233 - VIA 8235
                      VIA 8235 with AD1980 at 0xe000, irq 19
cat /proc/asound/modules
 0 snd_via82xx

i hope it helps

---

### Post by Wiifreak on 2008-01-10
- ubuntu version
[INDENT]Linux ruben-Linux 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux[/INDENT]
- also if you're using ubuntu/kubuntu/xubuntu
[INDENT]Ubuntu with KDE installed (but was using only Fresh install)[/INDENT]
- wine version (in a terminal: wine --version)
[INDENT]wine-0.9.46[/INDENT]
- how did you install wine? how do you run wine (terminal/menu/etc)
[INDENT]Installed via install/delete in menu and selected is[/INDENT]
- which video driver: nvidia/ati/etc (and which version)
[INDENT]Dont know[/INDENT]
- sound card info, in a terminal:
cat /proc/asound/cards
[INDENT] 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with VIA1617A at 0xe600, irq 20[/INDENT]
cat /proc/asound/modules
[INDENT] 0 snd_via82xx[/INDENT]
- any other info you think might be useful to start troubleshooting this
[INDENT]When I installed it via terminal and started wine tools (worked), it freezes with creating C drive.[/INDENT]
- also: when your system freezes, can you regain control of your box pressing:
Alt-r-SysRq
followed by:
Ctrl-Alt-Backspace
[INDENT]Have to try.[/INDENT]

---

### Post by happyhamster on 2008-01-10
Perhaps you're both using onboard Via graphics? You can check in xorg.conf. In a terminal type (or copy&paste):

cat /etc/X11/xorg.conf

Which shows your graphics configuration (warning: *don't* edit this file). Under the section "Device" it shows the graphics driver. If it's "via" you're problems are probably related to this:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+bug/43154](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+bug/43154)

Which seems pretty bad. :(

---

### Post by Don S on 2008-01-10
I'm using the "nvidia" driver, with an nVidia 7600 card. Also tried every Wine version from 0.9.46 -> 0.9.52. But the problem was new, and it came out of nowhere. Before I had it working flawlessly fine.

Now, I played a bit with Compiz, to get different wallpapers on each side, but ended up screwing it totally, removed it completely and reinstalled it from Synaptic.  I am now able to play games in Wine, although not fullscreen (if I go fullscreen, the GNOME panels stay), and I can't use certain keys (Backspace, enter, shift etc. Delete works, though).
So it appears my problem is related to Compiz, somehow, although I tried disabling it using Appearance -> Visual Effects: None (not sure if it disables Compiz though). Haven't yet tried "Raising Skinny Elephants Is Utterly Boring", as I acquired knowledge of it, after it "started working again".

- Don S

PS: Ubuntu version:
Linux Cybonatron 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

---

### Post by Wiifreak on 2008-01-10
Yes, I have a VIA Chipset...
It gave problems in Windows too...

---

### Post by Don S on 2008-01-10
Just when I thought my problem had left me, it appears to have returned once again. I managed to Alt+SysRq+R S E I U B and reboot normally though, so the computer is not totally dead. But after Alt+SysRq+R I wasn't able to go to a terminal via Alt+Ctrl+F2 or kill X using Alt+Ctrl+Bkspc.

So, still in great need of help.

Is there a place where you can keep track of, which updates that happened between the 29th of December till the 2nd of January?

EDIT: Wine does not freeze when running the Wine config.

---

### Post by Don S on 2008-01-11
*Bringing attention back to this thread*

---

### Post by ellis rowell on 2008-01-11
I have the same problem. Having upgraded my O/s to v7.10 I am at a loss to know if it is Wine or V7.10 which is causing the problem. I cannot even use the uninstall program to get rid of it. Has anyone any suggestions?

---

### Post by Don S on 2008-01-13
Haven't found a solution yet.

---

### Post by craiger45 on 2008-01-13
I noticed my system either running slow or hanging up, so i ran system monitor to see what was using the resources of the computer. I found when I turned on my laptop, CPU would run at about 5 to 10 % and memory was at 127mb being used. As soon as i open any microsoft program such as internet explorer, cpu would jump to 100%, memory would start to go up over 350mb. After that the laptop would slow down or freeze up. As soon as I would shut down the wine server using the kill process in system monitor, cpu and memory usage would go back down to normal and the computer would operate normally.
I installed the latest wine updated yesterday and this may be the problem since the computer never behaved like this before the update.

---

### Post by Don S on 2008-01-13
I've noticed that this problem happened once, when I tried to use KDE 4... One of my friends mentioned this might be because I had a corrupt version of Hardy on a partition. The problem actually started around the time I deleted everything on the partition and formatted it to FAT32 (don't know why I choose FAT, I don't really like that filesystem, but I had some idea, that it might clean up the whole partition, because it's a Windows partition). However the 8.04 appeared on the Grub list, even after I had removed it. I've removed it from the list in /boot/grub/menu.lst (I think that's the filename), but my computer still prompts me to choose a partition to mount, on startup.

Might it be related in any way?

---

### Post by Don S on 2008-01-15
Help would still be much appreciated.

---

### Post by Chad.S on 2008-01-15
I had weird issues with wine freezing on me and I narrowed it down to my sound card (I was using a Dynex 5.1 PCI sound card). I found out that if I talk the sound card out completely then the lock-ups stoped. When I put the card back in it would only look up when it had to output sound. I'm pretty sure it's a driver related issue and not a WINE issue. I ended up just getting a different sound card.

---

### Post by Don S on 2008-01-15
As this apparently used to work, I'm not going to spend money on a new sound card, for which there is only a minor chance that it will solve my problem. And if this is in fact related to the driver, it should be possible to get an older version of it, as I'm not using any restricted drivers for that.

---

### Post by zodiacdm on 2008-01-19
wait a minute. i have been all over looking for a solution to this problem. i too have a dynex dxsc51 sound card. anybody else? i was leaning more torwards a video card issue but...

---

### Post by Stefano Fonzarelli on 2008-01-24
At the Office we have a HP-laptop with an Intel CPU that has no problem running WINE. Our AMD-desktop has the problems that you mention, could it have to do something with the type of CPU. On both systems the 32-bit Ubuntu is installed.

We are actually only running MS-Paint on it, since my boss refuses to learn an more complicated program under Ubuntu.

On selecting Wine-config from the menu I get no response whatsoever.
On executing a command-line starting Paint, the system freezes immediately.

---

### Post by Gilvin on 2008-01-28
same problem here, it freezes so completely that i have to hard reset...

fresh installed Ubuntu 7.10

display card: Nvidia 7600GS with latest driver installed with Synaptic

sound card: Mediatek Sound Image 1723 (VT1723 Chip)

core version: Linux hyde-desktop 2.6.22-14-generic

wine version: 0.9.46.0 , installed with Synaptic

i ran wine via menu, and BLING! the system freezed about 5 minutes until i hard reset the computer.

---

### Post by zodiacdm on 2008-01-30
> **Stefano Fonzarelli said:**
> At the Office we have a HP-laptop with an Intel CPU that has no problem running WINE. Our AMD-desktop has the problems that you mention, could it have to do something with the type of CPU. On both systems the 32-bit Ubuntu is installed.

We are actually only running MS-Paint on it, since my boss refuses to learn an more complicated program under Ubuntu.

On selecting Wine-config from the menu I get no response whatsoever.
On executing a command-line starting Paint, the system freezes immediately.
no, this isn't a amd thing, i'm running a pentium 4. what kind of video cards are you running in either of those computers?

I find it hard to believe no one has found an answer to this. there are alot of people with this problem, and if it does have something to do with the video cards, then there are alot of people who are unhappy right now, as any gamer who runs linux relies on wine. 

does anyone know if this has happened on any other distro's? it seems like ubuntu is the only one with this problem. even when i googled linux and wine problems, every thread and post said something about ubuntu. maybe we have all been missing it. I think gusty's to blame.

---

### Post by iprat on 2008-01-30
Just a thought... have you tried disabling completely compiz effects ?

---

### Post by Don S on 2008-01-31
Tried a completely fresh install with openSUSE, yet the problem remains. I have come to the conclusion, that this is an unsolvable problem for me. Anyhow, I'm buying a new laptop soon, which should work fine.

---

### Post by rbrociek on 2008-02-01
> **Chad.S said:**
> I had weird issues with wine freezing on me and I narrowed it down to my sound card (I was using a Dynex 5.1 PCI sound card). I found out that if I talk the sound card out completely then the lock-ups stoped. When I put the card back in it would only look up when it had to output sound. I'm pretty sure it's a driver related issue and not a WINE issue. I ended up just getting a different sound card.

I had an almost identical issue (thanks for posting this by the way...it helped me figure it out).  I actually had two sound cards in my system...one on board and one pci.  After reading these forums yesterday, specifically this post, I went home after work and yanked the pci sound card and viola! wine runs fine now.

Now I just need to get quake 4 to recognize my 512 MB video card instead of low end 64MB card...i don't know what that's all about...nother post, nother day :)

---

### Post by Don S on 2008-02-03
Geez, I feel so relieved. It shows up, that this in fact, has nothing to do with drivers or software at all. It's a hardware issue. I've removed the Nvidia card now, and running using the onboard SiS chipset instead, on which there is (believe it or not), better support for Linux than Windows. I can't run advanced 3D, but the solution seems better than the unexpected crashes, my Nvidia card caused me in these last times (apparently the problem has worsened in the time since it started).

Anyway, it feels nice not spending all my time on a computer, trying to fix it any more. It's so refreshing, although it's not fixed, it's just not an undocumented issue.

Anyway, problem solved. This thread may be closed (unless other wants to use it).

---

### Post by rudedcam on 2008-02-04
yeah, don't delete it yet, i'll try it too.

---

### Post by SergioOnline on 2008-02-29
Hello, I have just installed Linux Ubuntu in the last 2 days. I have attempted to install wine but without success, when I installed it from the add/remove applications, it went all ok until I tried to run winefile through the terminal. this just froze the computer. When I restarted the computers the WINE selection was under applications so I tried to execute it but only to have it freeze again. same problem as you guys I'm guessing.

---

### Post by Minigun on 2008-03-14
Problem finally solved!

Solution: remove/rename the file /usr/lib/wine/wineoss.drv.so

It's the OSS driver for wine. With ALSA, some soundcards just freeze if wine tries to touch them with OSS. After removing the file, just run winecfg and select ALSA as the audio driver.

---

### Post by joe3204 on 2008-03-15
i am using ubuntu 7.10 and wine 0.9.57...i am facing the same problem...i have an onboard via graphics controller...wine hangs as soon as i run either winecfg or notepad thru wine....so is my problem hardware???

also i read some thread and that guy was using 0.9.36 withour any problems but after updating he was facing the same problem...should i just replace my 0.9.57 with the older version????

graphics information - VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated

---

### Post by kulotzy on 2008-03-15
> **joe3204 said:**
> i am using ubuntu 7.10 and wine 0.9.57...i am facing the same problem...i have an onboard via graphics controller...wine hangs as soon as i run either winecfg or notepad thru wine....so is my problem hardware???

also i read some thread and that guy was using 0.9.36 withour any problems but after updating he was facing the same problem...should i just replace my 0.9.57 with the older version????

graphics information - VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated

Same here, i updated and it wouldnt work anymore. Im using VIA Unichrome as well.

---

### Post by Minigun on 2008-03-15
> **Don S said:**
> It's a hardware issue. I've removed the Nvidia card now, and running using the onboard SiS chipset instead, on which there is (believe it or not), better support for Linux than Windows.

I have a nvidia gf 7600GS and it's working like charm. For me the solution to freezing was removing the /usr/lib/wine/wineoss.drv.so file. It was an ALSA issue with a certain soundcard. (ESI Juli@ / ice1724)

---

### Post by The Minder on 2009-04-13
> **Minigun said:**
> Problem finally solved!

Solution: remove/rename the file /usr/lib/wine/wineoss.drv.so

It's the OSS driver for wine. With ALSA, some soundcards just freeze if wine tries to touch them with OSS. After removing the file, just run winecfg and select ALSA as the audio driver.

I've been putting up with this freeze issue for more than a year, until now.   To borrow a quote:

You Sir, are a steely-eyed missile man.

Thank you.

---

