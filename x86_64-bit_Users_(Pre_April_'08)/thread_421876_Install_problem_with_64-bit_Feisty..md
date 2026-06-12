---
title: "Install problem with 64-bit Feisty."
date: 2007-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by AceRimmer on 2007-04-24
Hello, I am trying to install the new 64 bit Feisty on my computer. 
The cd will boot to the install menu, where I select either Install or safe mode and it loads the kernel and then the screen goes black and I get a message at the bottom saying 
"kernel alive"
"kernel direct mapping tables up to ######## ###########" the # are real numbers on the screen though, it just flashes by so fast I can't tell just what they are. 

Any ideas on what this could be?

---

### Post by MarkyD83 on 2007-04-24
Check the CD. How fast did you burn the CD at? I had problems when i burned my cd at 16x try burning at a slower speed.

---

### Post by Churnd on 2007-04-25
> **AceRimmer said:**
> Hello, I am trying to install the new 64 bit Feisty on my computer. 
The cd will boot to the install menu, where I select either Install or safe mode and it loads the kernel and then the screen goes black and I get a message at the bottom saying 
"kernel alive"
"kernel direct mapping tables up to ######## ###########" the # are real numbers on the screen though, it just flashes by so fast I can't tell just what they are. 

Any ideas on what this could be?

I get the message too, but my install worked fine.  I think the message is just part of the 64 bit OS, as it doesn't show up on my 32 bit install.  As far as why you're getting a blank screen, I have no idea.  I don't think it's related to the message though.  I agree with the previous suggestion to re-burn the CD, and even re-download the image.  MD5 sums are your friend.  Google "check MD5" for how to use them in either Windows or Linux.

---

### Post by jespdj on 2007-04-25
> **AceRimmer said:**
> "kernel alive"
"kernel direct mapping tables up to ######## ###########" the # are real numbers on the screen though, it just flashes by so fast I can't tell just what they are. 

Any ideas on what this could be?
Those messages are normal. I also see this. Does your installation work or not?

---

### Post by kesnei on 2007-04-25
I am running AMD 64-bit and I burned the cd on 16x, and got that message as well... but it installed just fine as well however I do remember it stopping for a moment... Does it just hang at that message?

---

### Post by Tomtenizze on 2007-04-25
Hi, I'm having the same issue with the screen going black right after the text " "kernel alive"
"kernel direct mapping tables up to ######## ###########" ". Have tryed ubuntu burned at max, ubuntu burned at 24x and xubuntu burned at 16x with the same problem and I'm all out of CDs now.

---

### Post by feliponz on 2007-04-25
try burning at 8x,if you can,  it worked for me.

---

### Post by AceRimmer on 2007-04-25
Doh. sorry guys.  After it shows that message the system appears to reboot, but it appears to just hang and the Caps lock light and another light on the keyboard just blink.  It's weird.

---

### Post by patrickgamer on 2007-04-25
I had a similar problem.

I got through it by going into the additional options (F6) and 1) removed the splash command 2) added the noapic command.

That got me to boot into the GNOME interface. But I have the problem of my system not reading the boot partition after i remove the CD and reboot.

Any ideas why grub won't start?

---

### Post by diegolaz on 2007-04-25
Same problem. 
I tried with 7.04 64bit and the Alternative CD... get the initial menu and when I try to install I get a black screen, the CD reads for a while but nothing ever happends. (some times I get the Kernet Alive, etc messege).

AMD64, ATI X800Pro, Viewsonic 20.1 widescreen LCD.

Even when I try text install with the Alternative CD I get the black screen. 

Can I set the screen settings before installation? Why doesnt it keep what it uses for the initial menu which works?

Thanks!

---

### Post by kwunderlich on 2007-04-25
I am also having the same issue as patrickgamer in that I needed to specify the F6 options of removing the splash and adding the noapic to even use the amd64 Desktop Live CD at all.  I am going to wait till someone responds with an answer before I install since this could cause a problem with grub (which I use as a dual boot with XP).  I also tried the i386 Desktop Live CD which worked fine and installed fine, but I wanted to use the 64-bit instead.

My components:

Intel Core 2 Duo 6600
EVGA 6800i motherboard
EVGA GeForce 8800 GTS 320 MB
4GB Patriot memory

---

### Post by Tomtenizze on 2007-04-26
> **AceRimmer said:**
> Doh. sorry guys.  After it shows that message the system appears to reboot, but it appears to just hang and the Caps lock light and another light on the keyboard just blink.  It's weird.

The exact same problem I have, though I manage to get into the installer by pressing F4 and changing resolution to 1024x768 but the screen goes black when I choose to boot ubuntu in grub.

---

### Post by patrickgamer on 2007-04-26
As of the time I went to bed last night, I still couldn't get around it.

The last attempt I had was to create a 500MB boot partition, a primary root partition (74GB), and a swap (5GB).

But during my fitful sleep, I got to thinking: could the issue have to do with my disk orders on the mobo? In my specific case, my linux HDD is in the 3rd SATA slot (and I have a media storage disk at point 0). This config wasn't done on purpose, it was just a result of convenient wiring and lazyness. 

But I'm thinking maybe grub is always assuming it's on disk 0. I'm at work right now, but I'm going to try moving my OS disk to SATA0 and see if that helps. I can't do that until late this evening.

Can anyone (kwunderlich perhaps?) check to see if their disks are not in the first slot, and if so check to see if the rearrangement satisfies grub (which I'm really starting to get annoyed with).

If not, I'll post my results later tonight.

---

### Post by SuperDuperCruizer on 2007-04-26
I get the same message...  then it seems to lock up.  I'll try the F6, remove splash, noaptic & post what happens later.

---

### Post by kwunderlich on 2007-04-26
I'm at work now also, but will look when I get home.  I actually have 2 SATA 320 GB disks but also have a SATA LITE-ON DVD burner, so I am not sure which SATA channel they are on.

The motherboard I have is:

EVGA 122-CK-NF68-A1(nForce 680i SLI 775 A1 Version)

---

### Post by patrickgamer on 2007-04-26
My mobo is the Asus A8N-SLI nForce 4 chipset.

---

### Post by brew1brew on 2007-04-26
> **patrickgamer said:**
> As of the time I went to bed last night, I still couldn't get around it.

The last attempt I had was to create a 500MB boot partition, a primary root partition (74GB), and a swap (5GB).

But during my fitful sleep, I got to thinking: could the issue have to do with my disk orders on the mobo? In my specific case, my linux HDD is in the 3rd SATA slot (and I have a media storage disk at point 0). This config wasn't done on purpose, it was just a result of convenient wiring and lazyness. 

But I'm thinking maybe grub is always assuming it's on disk 0. I'm at work right now, but I'm going to try moving my OS disk to SATA0 and see if that helps. I can't do that until late this evening.

Can anyone (kwunderlich perhaps?) check to see if their disks are not in the first slot, and if so check to see if the rearrangement satisfies grub (which I'm really starting to get annoyed with).

If not, I'll post my results later tonight.

I don't know if yours is the same as mine, but I have 2 PATA drives ans a SATA. The SATA is my newest drive, I had my bios set to boot the DVD ROM then the SATA then the PATA, when Grub installed it was installed on the boot sector of my PATA drive, as it's where LILO was for my Mandriva install was, so it would just sit there with a cursor line blinking in the top left corner.

I went to bios and set it to boot my PATA drive after my DVD ROM drive. Grub comes up and i select Ubuntu and all is good.

I do need to find out how to get grub to install on my SATA drive, but as long as it's on the first boot drive it doesn't really matter I guess.

Les

---

### Post by Spyrious on 2007-04-26
That is the same problem as described here

[http://ubuntuforums.org/showthread.php?t=420410](http://ubuntuforums.org/showthread.php?t=420410)

---

### Post by AceRimmer on 2007-04-26
Yep that's it.  I'm going to try it again tonight but if I'm going to get errors on shutdown and restart I'm sticking with 32-bit.

---

### Post by SuperDuperCruizer on 2007-04-26
Okay... I had a chance to try the F6, remove 'quiet splash' & replaced it with 'noapic'  I'm now up and running Ubuntu!  I'm stoked.  I've been having soo many problems with XP64 Pro.  This is my first shot at an alternative to M$.  I sort of feel like I'm handing it to the man.

---

### Post by diegolaz on 2007-04-26
> Okay... I had a chance to try the F6, remove 'quiet splash' & replaced it with 'noapic' I'm now up and running Ubuntu! I'm stoked. I've been having soo many problems with XP64 Pro. This is my first shot at an alternative to M$. I sort of feel like I'm handing it to the man.

Almost! With that I was able to boot into the LiveCD installer....created partitions, installed (i think), when I reboot grub gives me the ubuntu ,etc, etc, windows option... when I choose ubuntu I get the kernel alive messege and then black screen.... is there a way to put the noapci here???

Thanks!

---

### Post by diegolaz on 2007-04-26
ok. Edited the GRUB line, removed quiet splash and added noapic and I'm posting from UBUNTU 64!! :D
Thanks!

---

### Post by patrickgamer on 2007-04-27
Yup. I tried my drive theory. It worked. So, I don't know if this is just for 64bit or not, but grub always assumes that your target disk is HD0, if it isn't, your /boot partition isn't going to load before you fail on whatever disk comes before it in your BIOS.

---

### Post by kwunderlich on 2007-04-27
I installed fine last night without any issues using the 64-bit desktop version of feisty.  The only change that was needed was during the Live CD boot, after hitting the F6 key and changing the parameter "splash" to be "nosplash".  This enabled the install to complete, then after booting from the hard drive in safe video mode, it was able to make the grub parameter change to also specify "nosplash" and everything worked just fine.  Also, I was able to get the GeForce 8800 GTS to display using the NVidia driver (that I downloaded from NVidia) to display the desired resolution of 1680 X 1050 with no trouble at all.

---

### Post by davidturley on 2007-04-30
Hardware Configuration
----------------------------
Motherboard: Gigabyte GA-M59SLI-S5 (rev. 1.0)
Controller:      NVIDIA® nForce 590 SLI chipset  
Processor       AMD Athlon Athlon™64 X2 socket AM2 platform - Model 4200  
Note: I used default BIOS version v6.00PG - that came with board - did not upgrade it.

History of problem and final working Solution.
------------------------------------------------------
To help other peope out, I'm just droping a quick note to say how we overcame the following errors when trying to installing both Ubuntu 7.04 Server and Desktop in both 64bit or 32bit editions. I think this error is quite common not matter what distributions of Linux you have.

Note: 
a) The problems below were not caused by having hardware device connected or NOT connected to the motherboard (like Hard Disks, Graphics Cards, input devices). 
b) Al Ubuntu ISO's above were burnt to the CD a 24x speed. Basically the CD is not a problem.

1st Problem: 
---------------
Got the BIOS to Booted from CD. After booting we got the following error message
Result:     got error message: "CRC ERROR --SYSTEM HALTED" 
Solution: Remove the other DRR2 Memory card and only left one DRR2 memory card on the board.

2nd Problem
---------------
Again, got the BIOS to Booted from CD. The Ubuntu Boot Menu appears. No matter what boot menu option to select you always get the following error.
Result:   
    "Kernel alive"
    "Kernel direct mapping table up to 100000000 @ 8000 d000"

Solution: 
Reboot, when the Ubuntu menu appears, press option F6.
a) For Ubuntu 7.04 Server on AMD 64bit, add "noapic" to the boot command 
From:  "...../initrd.gz quiet --"
To:      "...../initrd.gz quiet noapic --"

b) For Ubuntu 7.04 Desktop on AMD 64bit, add remove "splash" and add "noapic" to the boot command 
From:  "...../initrd.gz quiet splash --"
To:      "...../initrd.gz quiet noapic --"

Then press Enter and the OS will progress and install correctely for both Server and Desktop editions, even thought the error
    "Kernel alive"
    "Kernel direct mapping table up to 100000000 @ 8000 d000"
will continue to appear at the bottom of the screen.

Later an error message saying "fd0" (floppy disk) is not present will appear, but just ignore it, it will go away after a while and the OS will progress to install correctely.

Wikipedia Reference on APIC - [http://en.wikipedia.org/wiki/Intel_APIC_Architecture](http://en.wikipedia.org/wiki/Intel_APIC_Architecture)
-----------------------------------------------------------------------------------------------------
APIC Architecture by Intel is a system of Advanced Programmable Interrupt Controllers (APICs) designed by Intel for use in Symmetric Multi-Processor (SMP) computer systems. 
...
Design Issues
The Intel APIC architecture is well known for having a large amount of jitter in its interrupt latency.

Hardware Bugs
There are a number of known bugs in implementations of APIC systems, especially with concern to how the 8259 is connected.

There are defective BIOSes which do not set up interrupt routing properly. This includes the errors in the implementation of ACPI tables and Intel Multiprocessor Specification tables.

Operating System Issues
It can be a cause of system failure, as some versions of some operating systems do not support it properly. If this is the case, disabling I/O APIC may cure the problem. For Linux, try the 'noapic nolapic' kernel parameters on bootup; for FreeBSD, the 'hint.apic.0.disabled' kernel environment variable.

In Linux, problems with I/O APIC are one of several causes of error messages concerning "spurious 8259A interrupt: IRQ7.". It is also possible that I/O APIC causes problems with network interfaces based on via-rhine driver, causing a transmission time out. Uniprocessor kernels with APIC enabled can cause spurious interrupts to be generated.


Hope this helps somebody 
Cheers
Dave

---

### Post by dptxp on 2007-04-30
> **patrickgamer said:**
> Yup. I tried my drive theory. It worked. So, I don't know if this is just for 64bit or not, but grub always assumes that your target disk is HD0, if it isn't, your /boot partition isn't going to load before you fail on whatever disk comes before it in your BIOS.

If I remember well, in Feisty Fawn 64-bit, you are supposed to select you target disk after partitioning, the default shown is HD0, I think you can edit it there before pressing ENTER.

---

### Post by r_rehashed on 2007-04-30
I think the Message is just normal.

Maybe there is a problem with loading Gnome, if the screens going blank.

---

### Post by SuperDuperCruizer on 2007-05-05
It took quite a bit of digging to find something that was directly to the point.  Here's what I found:

[https://answers.launchpad.net/ubuntu/+question/1808](https://answers.launchpad.net/ubuntu/+question/1808)

---

### Post by DUNC4N on 2007-05-19
> **kwunderlich said:**
> I installed fine last night without any issues using the 64-bit desktop version of feisty.  The only change that was needed was during the Live CD boot, after hitting the F6 key and changing the parameter "splash" to be "nosplash".  This enabled the install to complete, then after booting from the hard drive in safe video mode, it was able to make the grub parameter change to also specify "nosplash" and everything worked just fine.  Also, I was able to get the GeForce 8800 GTS to display using the NVidia driver (that I downloaded from NVidia) to display the desired resolution of 1680 X 1050 with no trouble at all.

Man I whish I could understand :(

I managed to install doing the f6 and replace splash with noapic

when I reboot I get the option to choose between ubuntu and vista, when I hit ubuntu black screen again.

If you would be so kind to help me out, as I have 8800gts, and need 1680 x 1050.

I have been searching, and writing, and trying, however I'm still a badburger with linux.

Thanks again!

---

### Post by deekayen on 2007-08-06
> **patrickgamer said:**
> I got through it by going into the additional options (F6) and 1) removed the splash command 2) added the noapic command.

Just confirming that worked for me in the 7.04 install.

---

### Post by butcher99 on 2007-08-09
you probably found the fix by now but just in case, you need to edit the line (press f6) and add in noapic nolapic nosplash.  Then hit b to boot.  How to edit is explained on the screen, but basically hit e to edit, hit enter then hit b to boot.  

    Now I have to figure out how to make that permanent.

jim

---

### Post by abdo88 on 2007-08-12
PEOPLE, I can't thank you enough!!!

---

### Post by kwunderlich on 2007-08-22
The issue is really with the feisty splash screen for EM64T processors using the 64-bit installation.  The solution on install is to press F6 and change the "splash" argument to "nosplash".  This will allow the install to proceed.  Once the install completes, you will need to reboot and start in "safe" mode which is typically the second option shown in the grub menu.  Once Ubuntu boots in this mode, the command line will appear and you will be root.  Simply use vi to edit the /boot/menu.lst (make a backup first such as /boot/menu.lst_backup) by changing any instance of "splash" to be "nosplash".  This will provide the needed argument when you reboot.  Once the file is edited, reboot and when grub appears again, just select the normal Ubuntu OS installation.  Instead of showing the nice graphical loading progress bar, you will instead get all of the text showing which components are loading and their messages (not a big deal).  There is no need to add the "noapic" or anything beyond what I mentioned above.  I also tried installing on a machine very similar to my own using the 64-bit kernel and instead an AMD Athlon 64 X2 5600+ and it installed without needing to do anything special like above, so this issue seems to be specific to the EM64T and the Feisty x86_64 code.

---

### Post by popeyeray on 2007-10-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/127406](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/127406) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **butcher99 said:**
> you probably found the fix by now but just in case, you need to edit the line (press f6) and add in noapic nolapic nosplash.  Then hit b to boot.  How to edit is explained on the screen, but basically hit e to edit, hit enter then hit b to boot.  

    Now I have to figure out how to make that permanent.

jim

Like this: I had to use a program that allowed me to edit the boot/grub/menu.1st from Windows, but I think you should be able to use the F6 option upon boot also. I was not comfortable with that so I opened it via Wordpad from Windows and saved it back to the boot/grub/ directory. I used Paragon's Partition Explorer Version 5.6, the newer versions don't allow you to edit, import, or export anything, but the old version does. Anyway I changed the FIRST boot option below just after the "ro" part. It was "ro quiet splash", I changed it as you can see to "ro noapic nolapic nosplash". I rebooted and Ubuntu 64 booted up as normal no problems whatsoever. And yes it's permanent.:-\"
By the way this isn't my whole menu.1st only the part at the bottom.

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5cd3ac5e-5630-445f-84d3-4d8b8138019e ro noapic nolapic nosplash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5cd3ac5e-5630-445f-84d3-4d8b8138019e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

