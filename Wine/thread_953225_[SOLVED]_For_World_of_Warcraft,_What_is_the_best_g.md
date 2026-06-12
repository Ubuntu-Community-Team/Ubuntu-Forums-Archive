---
title: "[SOLVED] For World of Warcraft, What is the best graphics card?"
date: 2008-10-19
forum: Wine
---

### Post by Ugeen on 2008-10-19
Hello,

It was recommended that I get a new graphics card for my computer.

[LIST=1]
[*]What is the best graphics card for playing World of Warcraft (WOW)?
[LIST=a]
[*]nVidia?
[*]ATI?
[*]Other?
[/LIST]
[/LIST]
CPU
[LIST]
[*]Dell Dimension 4600
[*]Intel(R) Pentium(R) 4
[*]Dual Processor
[/LIST]
Video Card
[LIST]
[*]PNY Verto nVidia GeForce FX 5200 PCI 256MB DDR ([Google]("http://images.google.com/images?gbv=2&hl=en&q=PNY+Verto+nVidia+GeForce+FX+5200+PCI+256MB+DDR"), [TigerDirect.ca]("http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=2148789&CatId=319"))
[*]nVidia Driver Version: 173.14.12
[*]Resolution:  1440 x 900
[*]In a Terminal window, I typed:  sudo lshw -C display
[INDENT]
*-display UNCLAIMED
[INDENT]
description: Display controller
product: 82865G Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm cap_list
configuration: latency=0
[/INDENT]
*-display
[INDENT]
description: VGA compatible controller
product: NV34 [GeForce FX 5200]
vendor: nVidia Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a1
width: 32 bits
clock: 66MHz
capabilities: pm vga_controller bus_master cap_list
configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
[/INDENT]
[/INDENT]
[/LIST]
Operating System
[LIST]
[*]Installed: xUbuntu
[*]Version: 8.04
[*]Desktop Environment: Xfce
[*]Release: Hardy Heron for i386
[/LIST]
System Monitor says
[LIST]
[*]System tab
[LIST]
[*]Ubuntu
[LIST]
[*]Release 8.04 (hardy)
[*]Kernel Linux 2.6.24-21-generic
[/LIST]
[*]Hardware
[LIST]
[*]Memory:  3.0 GiB
[*]Processor 0:  Intel(R) Pentium(R) 4 CPU 2.80GHz
[*]Processor 1:  Intel(R) Pentium(R) 4 CPU 2.80GHz
[/LIST]
[*]System Status
[LIST]
[*]Available disk space:  16.3 GiB
[/LIST]
[/LIST]
[*]Resources tab
[LIST]
[*]Memory and Swap History
[LIST]
[*]Memory:  3.0 GiB
[*]Swap:  5 GiB
[/LIST]
[/LIST]
[/LIST]
Thank you in advance for your help.
Sincerely,
--Ugeen

---

### Post by Gcentrex on 2008-10-20
If your going to be sticking with Linux then stick to Nvida the ATI card drivers for anything but windows are crap and it will make things unplayable or take a lot of work to configure your system to work at a decent level, were with an Nvida card you have great performance with little to no effort plus it also works well in Windows their FreeBSD and also Solaris drivers available too.

My advice is to always stick to Nvida if you want to use more then just windows that is unless at a later point in time ATI make good drivers for more platforms that are actually good.

---

### Post by Mistrblank on 2008-10-20
Is the graphics card slot PCI-E or AGP?

If it's AGP, which is very possible since you have a 4 year old system, I recommend a whole new system.

---

### Post by Ugeen on 2008-10-20
> **Mistrblank said:**
> Is the graphics card slot PCI-E or AGP?

If it's AGP, which is very possible since you have a 4 year old system, I recommend a whole new system.

Hello Mistrblank,
[LIST=1]
[*]Is there a Terminal command that I can run to find out if my graphics card is using a PCI-E or AGP slot?
[LIST=a]
If not, how can I find out?
[/LIST]
[/LIST]
Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by Gcentrex on 2008-10-20
A quick google and I came across this have a look at the image the first is an AGP slot and their is also PCI slots shown in a image below 

[http://www.kids-online.net/learn/click/details/agp.html](http://www.kids-online.net/learn/click/details/agp.html)

If it is an AGP slot it is possible to get an AGP card but a new system would be a better option as Mistrblank has said above.

---

### Post by Ugeen on 2008-10-20
> **Gcentrex said:**
> A quick google and I came across this have a look at the image the first is an AGP slot and their is also PCI slots shown in a image below 

[http://www.kids-online.net/learn/click/details/agp.html](http://www.kids-online.net/learn/click/details/agp.html)

If it is an AGP slot it is possible to get an AGP card but a new system would be a better option as Mistrblank has said above.

Hello Gcentrex,

My graphics card is in an AGP slot.

Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by Ugeen on 2008-10-20
> **Gcentrex said:**
> A quick google and I came across this have a look at the image the first is an AGP slot and their is also PCI slots shown in a image below 

[http://www.kids-online.net/learn/click/details/agp.html](http://www.kids-online.net/learn/click/details/agp.html)

If it is an AGP slot it is possible to get an AGP card but a new system would be a better option as Mistrblank has said above.
Hello Gcentrex,

I'm not sure if my graphics card is in an AGP slot or not.  Please look at the results in the following Terminal window, which looks like I have it in a PCI slot.  However, my graphcis card is in the longer slot whereas a PCI slot looks like it's a smaller slot.
[LIST=1]
[*]Do you think that my graphics card is in an AGP or PCI slot?
[/LIST]

In a Terminal window, I typed:  sudo lshw -C display
[INDENT]
*-display UNCLAIMED
[INDENT]
description: Display controller
product: 82865G Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm cap_list
configuration: latency=0
[/INDENT]
*-display
[INDENT]
description: VGA compatible controller
product: NV34 [GeForce FX 5200]
vendor: nVidia Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a1
width: 32 bits
clock: 66MHz
capabilities: pm vga_controller bus_master cap_list
configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
[/INDENT]
[/INDENT]
Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by Gcentrex on 2008-10-20
> **Ugeen said:**
> Hello Gcentrex,

I'm not sure if my graphics card is in an AGP slot or not.  Please look at the results in the following Terminal window, which looks like I have it in a PCI slot.  However, my graphcis card is in the longer slot whereas a PCI slot looks like it's a smaller slot.
[LIST=1]
[*]Do you think that my graphics card is in an AGP or PCI slot?
[/LIST]

In a Terminal window, I typed:  sudo lshw -C display
[INDENT]
*-display UNCLAIMED
[INDENT]
description: Display controller
product: 82865G Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm cap_list
configuration: latency=0
[/INDENT]
*-display
[INDENT]
description: VGA compatible controller
product: NV34 [GeForce FX 5200]
vendor: nVidia Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a1
width: 32 bits
clock: 66MHz
capabilities: pm vga_controller bus_master cap_list
configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
[/INDENT]
[/INDENT]
Thank you again for all of your help.
Sincerely,
--Ugeen

Doing that command myself just to be sure about your card, you see this is my card and it PCI express card.

```
  *-display               
       description: VGA compatible controller
       product: GeForce 8500 GT
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

```

So yes your card is an AGP card according to this.

---

### Post by Ugeen on 2008-10-20
> **Gcentrex said:**
> 
Doing that command myself just to be sure about your card, you see this is my card and it PCI express card.

```
  *-display               
       description: VGA compatible controller
       product: GeForce 8500 GT
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

```

So yes your card is an AGP card according to this.


Hello Gcentrex,
[LIST=1]
[*]If I'm reading this right, you're saying that my graphics card is an AGP because of the capabilities line, right?
(i.e. mine doesn't say:  pciexpress)


[LIST]
[*]Gcentrex's
capabilities:  pm msi pciexpress vga_controller bus_master cap_list


[*]Ugeen's
capabilities:  pm vga_controller bus_master cap_list
[/LIST]


[*]Why does the bus info say: pci@0000:01:00.0?
[LIST=a]
[*] Is it because that port is capible of using a PCI card?
[/LIST]


[*]Mine also has a display of:  UNCLAIMED
[LIST=a]
[*]Could this be interfering with the nVidia GeForce FX 5200 driver?
(FYI:  When I was using Windows, I had a hard time getting the nVidia GeForce FX 5200 driver to work because of the computer's default video driver.  I solved that problem at that time by doing the following.
[LIST=1]
[*]Booting up in SafeMode
[*]Uninstalling the computer's default video driver
[*]Installing the nVidia GeForce FX 5200 driver
(FYI:  I don't remember now which driver I installed at that time because it was a long time ago.  However, I do know that it wasn't the nVidia 173 or 177 driver because they didn't exist at that time.)
[/LIST]
[/LIST]
[/LIST]
Thank you again for your help.
Sincerely,
--Ugeen

---

### Post by Gcentrex on 2008-10-20
> **Ugeen said:**
> Hello Gcentrex,
[LIST=1]
[*]If I'm reading this right, you're saying that my graphics card is an AGP because of the capabilities line, right?
(i.e. mine doesn't say:  pciexpress)


[LIST]
[*]Gcentrex's
capabilities:  pm msi pciexpress vga_controller bus_master cap_list


[*]Ugeen's
capabilities:  pm vga_controller bus_master cap_list
[/LIST]


[*]Why does the bus info say: pci@0000:01:00.0?
[LIST=a]
[*] Is it because that port is capible of using a PCI card?
[/LIST]


[*]Mine also has a display of:  UNCLAIMED
[LIST=a]
[*]Could this be interfering with the nVidia GeForce FX 5200 driver?
(FYI:  When I was using Windows, I had a hard time getting the nVidia GeForce FX 5200 driver to work because of the computer's default video driver.  I solved that problem at that time by doing the following.
[LIST=1]
[*]Booting up in SafeMode
[*]Uninstalling the computer's default video driver
[*]Installing the nVidia GeForce FX 5200 driver
(FYI:  I don't remember now which driver I installed at that time because it was a long time ago.  However, I do know that it wasn't the nVidia 173 or 177 driver because they didn't exist at that time.)
[/LIST]
[/LIST]
[/LIST]
Thank you again for your help.
Sincerely,
--Ugeen

Pretty much yes your system is old 4 years old plus the lines from my output I would say it is an AGP card.

The reason it is showing another unclamined display is because you have an onboard chipset built into the motherboard, I'm also going to guess in the Bios it was not disabled when you were loading windows so it was causing you the problems installing the drivers for the Nvida card.

---

