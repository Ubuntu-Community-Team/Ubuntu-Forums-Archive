---
title: "x64 install cd boot fails -- NOT hanging black screen"
date: 2007-12-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by dlikhten on 2007-12-09
i've tried to install ubuntu 7.10 x64 on
Specs:
Intel Core2Quad Q6600 processor
Gigabyte p35-ds3r mobo
nvidia 8800GTS video card

I keep getting a computer restart a few seconds into the boot. It appears to be kernel-related.

What I have tried:
Remove the quiet splash --
Remove the quiet splash -- and add noapic (initially i noticed that it rebooted when it tried to start apic (apic would always fail)

I used 2 different isos to create 2 cds, neither one work.
I also tried the alternative cd--text based installer, nothing
I cannot even launch the cd-integrity check because same problem happens and it just reboots. There is no hanging black screen.

---

### Post by dlikhten on 2007-12-10
bump

---

### Post by dlikhten on 2007-12-11
bump

---

### Post by dlikhten on 2007-12-12
Anyone has any ideas? Is there any other information necessary?

I installed FC8 64 bit and it works... but I really want to get ubuntu working. I need 64 bit because of the evil creative drivers :(

---

### Post by rsambuca on 2007-12-12
What happened when you tried the alternate CD?  That should definitely work.

---

### Post by dlikhten on 2007-12-15
same exact crash issue it seems like kernel is at fault not the installer.

---

### Post by patrick71797 on 2007-12-15
I have the exact same problem when I try to install 7.10 64 bit edition.  I did a check sum of the ISO and it was correct so I burned a second ISO boot CD and it fails in the same exact manner of the first ISO boot CD.  If I select the install option it dosent do much but maybe a few commands or loads the kernel and then my screen will go black with my monitor light flashing on and off and same with my keyboard lights, flashing on and off.  Same thing happens when I try and do a check CD option.  It just locks up and so I just gave up and was checking the forums to see if anyone else was having problems like this.   I'm not a linux guru more of a newbie and this was my first ever attempt at installing a linux distro...not very encouraging when you can't even get the install going. :( 

I'm running, AMD Athlon 64 3200+
1.5 GB of Ram DDR 400
ATI X800 Pro
MSI K8n Neo Platinum MOBO with Nvidia Nforce3 250bg chipset

---

### Post by dlikhten on 2007-12-16
32 bit install works for me, you can try that. I need 64 bit because of my sound card (evil creative w/ xfi)

Honestly I would rather go for 32 ATM because 64 bit is just not yet "plug-and-play", but I need that sound :( Probably gona do 32 bit and use my on-board sound card :P

---

### Post by kajillin on 2007-12-16
... wierd both my x64 machines work perfectly with the text base installer. And patrick if you are dicouraged by this.... just wait till you actually get it installed, thats where the real problems come into play.

---

### Post by tensai_999 on 2007-12-16
same problem here and almost identical hardware specs with dlikhten. Right now i haven't tried the 32 bit edition of 7.10. The version i've tried is the 7.04 both the 32 and 64 bit edition and it works.

---

### Post by tensai_999 on 2007-12-17
i've just installed the ubuntu 7.10 by using the text based installer(alternate ubuntu cd) but you would encounter the same scenario upon first boot after a successful installation like that of  installing the live cd wherein after selecting install ubuntu(option) blank screen will appear(monitor led turn to orange) but this would last for about 20 seconds after that the logon will appear, some users explained it is because ubuntu will used the highest resolution supported by the video card which in contrary the monitor could not attain, so if using live cd they would suggest adding vga=771 option in the boot option.

since your graphic card is 8800gts check if your monitor could support the highest resolution of the video card if not try either using the alternate cd(works for me) or by adding vga options in boot options of live cd.

---

### Post by frankyboy4 on 2007-12-20
I have a very similar setup and ran into the same problem. I tried 4 different CD-Rom drives and burned the cd on 2 different machines and still the same problem.

My workaround for this was to burn the DVD-Rom and I was then able to install.

The only frustrating thing there was that I was installing to a drive that had some data on it and I was not able to split and resize the single partition, and I was not able to just install to the drive because It required formatting of the partition, so I had to use another drive for the installation.

I am using the ATI R300 PCIx16 video card, and will be setting up the compiz stuff this weekend.

I would say if possible and you have a drive to read it, try the DVD installer.

Frankyboy4

---

### Post by Envy0pla on 2007-12-20
Fantastic, been trolling the forums for weeks hoping to find someone else with the same problem as me! 

Im in exactly the same boat,  Get the install screen,  get loading kernel....computer restarts round and round it goes. 

I have previously had Ubuntu installed on this machine quite happily,  but wanted to duel boot with XP for games.

I too have tried 32x install,  Downloading x64 again,  and installing from a dvd  that came with a PC magazine. No luck.

I think I will try the text based installer(alternate ubuntu cd) next? 

But I will check back and see if other options are offered and of course post if I fix it.

---

### Post by lukcic on 2007-12-23
I have the same problem, the only difference is that Fedora allso doesn't work. Before I get to the install process it makes an exeption error creating Xwindow. In the text mode says that I should run debug mode etc... No future :(

---

### Post by dlikhten on 2007-12-23
I installed 32 bit and it works flawlessly... I am using my motherboard audio instead of sound blaster xfi... I am regretting getting it now, my mobo's sound card is more than sufficient for my needs.

I am going to try 64 bit using DVD instead of cd... If I can find it :P

This thread is moving rather slowly so sorry for the delays in responses... Hopefully I can get a reliable way to install that will solve the issue for others as well, then we can document it...

Would help if i had a way to dump the log somewheres since this is during installation...

Unfortunately i am a bit short of spare time now so i will have another reply to this thread once i have more information. If anyone else experiencing this issue with no resolution wants to give it a shot, by all means.

---

### Post by dlikhten on 2007-12-24
> **frankyboy4 said:**
> I have a very similar setup and ran into the same problem. I tried 4 different CD-Rom drives and burned the cd on 2 different machines and still the same problem.

My workaround for this was to burn the DVD-Rom and I was then able to install.

Frankyboy4

What is the DVD-Rom image? Or did you just burn the iso onto a DVD?

---

### Post by tensai_999 on 2007-12-26
> **dlikhten said:**
> What is the DVD-Rom image? Or did you just burn the iso onto a DVD?

an iso for dvd's and it is different from iso which is usually offered by ubuntu site for download(cd iso)  the dvd iso is around 4gb compared to 700mb for cd iso. You couldn't burn cd iso to a dvd-r.

here's a link wherein you can get dvd iso: [http://cdimages.ubuntu.com/releases/7.10/release/](http://cdimages.ubuntu.com/releases/7.10/release/)

---

### Post by dlikhten on 2007-12-28
My co-worker gave me the official ubuntu CD which he bought (dont know why) and that didn't work either. I am downloading the DVD.

---

### Post by cprofitt on 2007-12-28
After 60 days of using Ubuntu on my work PC I took the leap to load it on my Home PC yesterday and ran in to the same exact issue.

I will try the VGA option to see if that helps...

Fedora Core 8 loaded up just fine.
Debian Loaded, but had issues with the Nvidia driver install.

with all these 'bugs' in the distro one can appreciate the work that Microsoft has to go through to get their OS to load on so many different hardware setups.

---

### Post by IIsi on 2007-12-28
Well, I ran into the same problem after I upgraded my BIOS from the version that the motherboard was sold with. After upgrade, i686 version install CD was still bootable but my 64-bit install and the install CD failed and rebooted while initializing the kernel. By changing to failsafe mode I could see (I hope I remember this correctly, too lazy to reinstall the faulty BIOS) some complaints about the APIC for every processor core.

So if you want to run 64-bit ubuntu without trouble, don't upgrade your BIOS. And if you already have, a quick and dirty way of getting it working again could be to downgrade the BIOS, yuck :-(

Simply put, the APIC is (at least according to wikipedia) a part of the mother board responsible for making it possible to have several processor cores running at once. This probably means that there is a bug in the BIOS update and hopefully not in Ubuntu. 

If you don't want to downgrade the BIOS, maybe trying the noapic option from grub might work. But I don't know if there would be any adverse side effects like only being able to use one core or the system ending up a lot slower. Who knows? 

My computer:

Intel Core2Quad Q6600 processor
Gigabyte p35-ds3r rev2.0 mobo
nvidia 8600GTS video card

---

### Post by dlikhten on 2007-12-28
that would make sense but then why can i run 32 bit perfectly?

---

### Post by IIsi on 2007-12-29
After googling with different combinations of amd64 64-bit, APIC etc, I found this: 

[http://lists.openwall.net/linux-kernel/2007/06/30/129](http://lists.openwall.net/linux-kernel/2007/06/30/129)

So there are definitely some differences in the way the APIC is handled in 64-bit and 32-bit. And when the trouble is with only certain motherboards after a BIOS update, from an emotional standpoint I want to blame the company responsible for the BIOS :-) 

My motherboard uses the AWARD BIOS, maybe the other people having trouble also use the same bios.

---

### Post by Bedbug105 on 2007-12-31
> upon first boot after a successful installation like that of installing the live cd wherein after selecting install ubuntu(option) blank screen will appear(monitor led turn to orange) but this would last for about 20 seconds after that the logon will appear, some users explained it is because ubuntu will used the highest resolution supported by the video card which in contrary the monitor could not attain, so if using live cd they would suggest adding vga=771 option in the boot option.

Hey guys :)

Actually, I've installed 64 bits using the live CD installation, the distro is working fine but I have this "standby" screen instead of the usual bootsplash. I could try to reinstall using the alternate version, but, since everything is working, I don't want to erase everything and spend two hours reconfiguring. Does anyone has an idea how to fix this once Ubuntu is already installed?

My ubuntu is 7.10 and my graphical card is Nvidia GF8600GT in case that's useful. If you need more information, tell me, i'll let you know.

Thanks in advance. All the best for the coming year.

---

### Post by lukcic on 2008-01-04
Hey guys I solved my problem.... Now I can run x64 OS. :D The problem was in the hardware, I can't tell if it was the problem in Adaptec AHA-2940UW controller or in the video converter (Pinnacle Studio Plus 700-PCI version 10). Maybe for the ubuntu (in my case) was the converter the who confused the kernel. The drivers for this piece of hardware wasn't made yet. It had been made a certain part of it, but not the whole one. ;)

Try to remove or disable (in bios) hardware and see if there's any other hardware fault. Otherwise guessing the problem should be bios itself. :confused:

---

### Post by dlikhten on 2008-01-11
Yea AWARD BIOS here too. Ver F11 is current...

I guess we should keep this thread going with versions of the bios until it works.

---

### Post by bipp5 on 2008-01-12
I'm seeing the same thing too when installing Ubuntu Server 7.10, APIC not able to start up any of the 4 cores, then just restarting over and over again. Hardware specs:

Intel C2D Q6600
Gigabyte GA-P35-DS3L
4GB RAM

---

### Post by sebastjanp on 2008-01-19
> **dlikhten said:**
> i've tried to install ubuntu 7.10 x64 on
Specs:
Intel Core2Quad Q6600 processor
Gigabyte p35-ds3r mobo
nvidia 8800GTS video card

I keep getting a computer restart a few seconds into the boot. It appears to be kernel-related.

What I have tried:
Remove the quiet splash --
Remove the quiet splash -- and add noapic (initially i noticed that it rebooted when it tried to start apic (apic would always fail)

I used 2 different isos to create 2 cds, neither one work.
I also tried the alternative cd--text based installer, nothing
I cannot even launch the cd-integrity check because same problem happens and it just reboots. There is no hanging black screen.

Hi everybody my comp configuration is the same as dlikhten's and totally the same problem but I have an logitech cordless desktop wave (USB keyboard and mouse) and of course I have enabled USB options in the BIOS (USB keyboard, USB mouse and USB legacy drive support). After I disabled all of this options the install was possible. I'm not sure which version of bios i have.

But than one other problem occured. I get a blank screen randomly sometimes right after boot or after starting some program (like firefox). I have forgoten to tell you that I had (at first) installed the proprietary Nvidia drivers and blamed those for the problem but the problem remains even after I have removed Nvidia drivers.

If somebody have any idea...?

---

### Post by dlikhten on 2008-01-21
> **sebastjanp said:**
> Hi everybody my comp configuration is the same as dlikhten's and totally the same problem but I have an logitech cordless desktop wave (USB keyboard and mouse) and of course I have enabled USB options in the BIOS (USB keyboard, USB mouse and USB legacy drive support). After I disabled all of this options the install was possible. I'm not sure which version of bios i have.

But than one other problem occured. I get a blank screen randomly sometimes right after boot or after starting some program (like firefox). I have forgoten to tell you that I had (at first) installed the proprietary Nvidia drivers and blamed those for the problem but the problem remains even after I have removed Nvidia drivers.

If somebody have any idea...?

Note: I am unable to install x64 linux because the installer won't load. This is NOT after linux installed. It is working flawlessly in 32bit version. I just want x64 for my darn creative drivers, but instead I am using my onboard sound card for linxu, less headakes :)

I am going to try installing with every bios revision i get of the AWARD bios until it works or developers have a nifty workaround :)

---

### Post by martinitime1975 on 2008-01-30
My problems are very similar.  When I boot up with the 64 live cd and choose the default option (run or install in graphical mode) it displays a couple of kernel errors and then power cycles the computer.  I was able to use the alternative-install cd to install the system, however, when I get the splash screen to start up Ubuntu, if I choose the first option it reboots the machine again.  If I choose safe mode, I can get a root prompt and run "startx".  The desktop loads perfectly at that point.  Any suggestions?  And if I remember, I've had similar problems with all of the 64 bit Ubuntu versions I've tried (edgy, feisty, gutsy).

---

### Post by tenmoi on 2008-01-30
First my hardware
Gigabyte GA-M61P-S3
AMD Athlon 64x2 4000+
RAM 2 GIGs
onboard GeForce 6100.
BIOS: Award

I think the problem lies with the BIOS. 2 weeks ago I attempted to install ubuntu 64 bit and could never succeed. The liveCD could only boot to a black screen though I could hear the welcoming sound. I tried the alternate CD to no avail. Installation stucked midway. I gave up and installed windows and update the BIOS to the newest version. (I downloaded the BIOS from Gigabyte). I then installed Fedora 64 bit successfully. After two weeks, I decided to return to Ubuntu. I used the exact CD that I had thought to be corrupt and tried with the boot options. And at long last I figured that I just needed to add the following line to the boot line and things would go fine: INSTALL HW-DETECT/START_PCMCIA=FALSE.

And now I am here back in with the Ubuntu world. 

So my suggestion is update the BIOS to the newest version and fiddle with the various options till you find  the right one.:guitar:


EDIT:

And none of the 32 bit CDs I have, feisty, edgy could boot or install.

---

### Post by dlikhten on 2008-02-05
Has anyone tried installing Fedora Core <any version> x64? If it installs I must lean towards this being an Ubuntu bug. Otherwise Bios2...

---

### Post by lukcic on 2008-02-06
I've found out what's the matter.... USB. I got a motherboard runing USB in "compatibility" mode.... In 1.1 mode and also in 2.0. That's it makes a kernel panic.... With all USB ports disabled in BIOS I could run x64 linux operating system. But it's interesting because all the x64 linuxes have the same problem.... So guessing the kernel can't handle USB 1.1 and that's why crashes, problem could be solved by buying extension cards for USB without the support for USB 1.1. :mad:

---

### Post by ccdee on 2008-02-15
same problem checking 32 bit now

---

### Post by Svenstaro on 2008-02-15
You can "fix" it by running Hardy x64 like I do now. Gutsy x64 will not work with Intel Quadcores or Nvidia 8800-class cards. I have no idea why. 
Though make sure to remove "splash quiet" in the Hardy boot menu. It will work without but you'll get a blackscreen for the time it loads up Ubuntu instead of a splash. Splash breaks when you use a 8800-class Nvidia Geforce. Booting brakes by using an Intel Quadcore. Heh, talk about bad luck.
Anyway, let me hear your results.
And give Hardy a try, after updating it's quite stable.

---

### Post by Drathas on 2008-02-15
When you boot the O/S hit escape then go to the second kernel loader option.  remove 'splash' then press enter and press b.  If it boots, it's the usplash bug - I have it too and just wrote it out of the bootloader.

---

### Post by Svenstaro on 2008-02-15
> **Drathas said:**
> When you boot the O/S hit escape then go to the second kernel loader option.  remove 'splash' then press enter and press b.  If it boots, it's the usplash bug - I have it too and just wrote it out of the bootloader.

Nah with the Intel Quadcores and the 8800's it's more than that which makes it tricky. It's the ACPI issue plus the splash issue which kinda sucks.

---

### Post by Drathas on 2008-02-15
> **Svenstaro said:**
> Nah with the Intel Quadcores and the 8800's it's more than that which makes it tricky. It's the ACPI issue plus the splash issue which kinda sucks.

bizarre - did you try a Hardy LiveCD ?

---

### Post by Svenstaro on 2008-02-15
Yeah I did and am running Hardy now as mentioned 4 posts above.

---

