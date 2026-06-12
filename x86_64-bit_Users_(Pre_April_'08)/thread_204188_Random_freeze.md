---
title: "Random freeze"
date: 2006-06-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by jvictor on 2006-06-26
I recently decided to try out 64 bit Ubuntu... and find that the machine freezes at random. I tried searching the forums but couldnt find a conclusive answer. 


This is my machine config

AMD 64 3000+ [754 pin]
Gigabyte K8VM800M mobo
1G Ram (512x2) [Kingston] 
Nvidia GF 5200 256 MB
Sony DVD+RW DRU-810-A


I checked the /var/log/ * but dint find anything interesting .. 

Appears like the k/b and mouse freeze, and I doubt if its something to do with X coz downloads go on in the b/g even if the machines UI freezes.

Btw I use the prop: nvidia drivers and this is the device section

Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option "RenderAccel" "On"
        Option "IgnoreDisplayDevices" "DFP,TV"
#       Option "NoRenderExtension" "On"
        Option "Accel" "On"
        Option "AllowGLXWithComposite" "On"
EndSection


Any similar experiences ?

---

### Post by jvictor on 2006-06-27
Looks like its got something to do with Firefox, the freeze happens when im browsing and sometimes use alt-tab to switch between windows. It has always froze with firefox open even though alt-tab wasnt used

Edit
----
One more freeze , this is getting to be so irritating , have to hard reboot every time

---

### Post by jvictor on 2006-06-27
Freeze can be reproduced **sometimes** when we handle websites with pagenation , like the ubuntu forums where a thread spans multiple pages. Ironically windows doesnt show this prob !!

---

### Post by jvictor on 2006-06-27
Update, The problem seems to occur with 32 bit Elive live session too. 

And I guess the villain is the gfx card bcoz thats the only piece of hardware that has changed . 

I was running a TNT2 perfectly fine and now since ive replaced it with the GeForce FX5200 card things seem to be going haywire on Linux. 

On windows things still work perfectly 

Edit::

Once again firefox was open, has it to do something with X in general ?

---

### Post by jvictor on 2006-06-27
**LOOKS** like theres a breakthru 

I changed my device section in the xorg.conf file to look like this

Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option "NvAGP" "0"
        Option "RenderAccel" "Off"
        Option "IgnoreDisplayDevices" "DFP,TV"
        Option "NoRenderExtension" "Off"
        Option "AllowGLXWithComposite" "Off"
EndSection

as mentioned in a HOWTO at 

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

and It seems to have brought in a fix to the problem as of now. I went thru  34 pages of a thread on this forum that had actually 67 pages and the hangman seems to have disappeared. :rolleyes: 

Will update if a freeze happens again. Im gonna leave the machine on for  few hours together.

---

### Post by jjoganic on 2006-06-27
[QUOTE=jvictor]Looks like its got something to do with Firefox, the freeze happens when im browsing and sometimes use alt-tab to switch between windows. It has always froze with firefox open even though alt-tab wasnt used

Edit
----
One more freeze , this is getting to be so irritating , have to hard reboot every time[/QUOTE]

I am encountering the same problem in Firefox and some other applications as well.  I boot the machine, login, and launch Firefox.  I open three or four tabs using Ctrl-Right click. When I switch between tabs or close a tab using the gui 'X', there is a high probability of a freeze followed by, in my case, a reboot.  This happens in the ubuntu forums as well as on other sites with many images.

The machine also locked up and rebooted while running device manager.  It also rebooted when I selected quit from the gnome menu, but before I could click "Logout".

My configuration:

dual AMD Opteron 246 at 2GHz
1GB RAM, 826MB "free"

lspci says:

AMD-8111 PCI, ISA, IDE, SMBus2.0, ACPI
AMD-8131 PCI-X Bridge, IOAPIC
AMD-8151 System controller, AGP bridge
AMD hypertransport, addrmap, drm controller
ATI Radeon RV100 QY (Radeon 7000/VE)
Broadcom NetXtreme BCM5703X Gigabit Ethernet
Satalink ATA (SiI 3114)
Texas Instruments TSB43AB22/A firewire controller

This machine ran like a champ on Breezy. I just recently upgraded and had trouble with the process... deleted a lib file per a forum recommendation and re-ran the upgrade to completion.

I will look at your solution.  I may also need to reinstall from scratch.

-John Joganic

---

### Post by jjoganic on 2006-06-27
On further examination, my problem may be different from jvictor's -- most likely an ATI device driver problem in my case.  I'm noticing that buttons (Help and Close) on the Software Update screen are rendered incorrectly.  The backgrounds for the buttons contain incorrect pixels -- all gray with repeating patterns of black dots.  Anything graphic intensive seems to destablize the system.  The only thing that can bust through past the kernel is the video display driver.  I'm not familiar enough with the current kernel to know the full ramifications of userspace X on the linux kernel, but it's crashing my machine fully to reboot, and without any indication or log message.

-John Joganic

---

### Post by jvictor on 2006-06-27
Looks like the problem has been solved , 3 -4 hrs of continous browsing and no lockups :)

---

