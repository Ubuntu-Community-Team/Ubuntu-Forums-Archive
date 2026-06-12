---
title: "A couple of questions - Ubuntu - AMD64Bit"
date: 2006-09-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by djeremy on 2006-09-21
Hi there.

An old friend recently told me about Ubuntu and I downloaded it yesterday to play with so I burned ubuntu-6.06.1-desktop-amd64.iso and booted from the disc....

I was in awe as it loaded, and just seemed to be working with absoultely all the hardware I have.
Which is...
an Abit NF-95 Micro AXT motherboard with an AMD Athlon 64 3800+ Chipset and a Gig of DDR[600?] RAM.
GFX powered with a GeForce 6800GS. 256mb/DDR3 PCI-Express.

Ubuntu is the Ducks Nuts (that's good yeah!) and meant that someone who knows the minimal amount of 'code related stuff' could for the first time experience a non-windows / mac related OS that comes with really cool software too! (I'm already a devout believer in Firefox.)

A few questions arose along the way....
The first couple of times the disc would boot and I would be greeted after a short while with a screen containing many coloured square boxes... this was fixed by me choosing the VGA res 1024x768 x32bits so that's OK.

A problem i have not been able to fix is that when I initially log in to Ubuntu there is no visible mouse pointer. The mouse DOES WORK and I find i have to feel my way around to the mouse options and although changing the mouse pointer to 'highlight when press 'Ctrl'... I am still not able to change the pointer style.
If I start Ubuntu in Safe Graphics mode I ONLY get a mouse pointer and NOTHING else appears on the screen EVER.

The next problem i'm encountering is that the Disc Partitioner is not being all together helpful with it's instructions.
I have 2 Physical HDD's 1x 120gb and 1x 140gb. Each have their own uses to me.
The disc partitioner helped me create a virtual partition on the desired drive but I was forced to boot Windows, format it there and try again in Ubuntu to select the 11Gb partition I have created. (Windows helped me finalise the partition and assign it a letter, It's called "E" so i now have C:, E:, and J:)
So, even after I formatted the partition in Windows, rebooted Ubuntu from the CD, reloaded my "Highlight mouse when Ctrl button is pressed", and went to the LOAD UBUNTU, I am still UNSURE HOW to select the 11Gb "E:" from the /root, /Dev, / etc screen. 
The instuctions need to be more specific at that point for someone like me to be able to select the Drive I want to use from a list and then know what folder to use from there. 
Even now i wouldn't know whether to use /DEV, /root, etc?
And do i need to create ANOTHER PARTITION for the swap file?
I have no idea.

I really appreciate what you are all doing and look forward to one day being able to use your OS.

Rgds,

---

### Post by Kilz on 2006-09-21
> **djeremy said:**
> Hi there.

An old friend recently told me about Ubuntu and I downloaded it yesterday to play with so I burned ubuntu-6.06.1-desktop-amd64.iso and booted from the disc....

I was in awe as it loaded, and just seemed to be working with absoultely all the hardware I have.
Which is...
an Abit NF-95 Micro AXT motherboard with an AMD Athlon 64 3800+ Chipset and a Gig of DDR[600?] RAM.
GFX powered with a GeForce 6800GS. 256mb/DDR3 PCI-Express.

Ubuntu is the Ducks Nuts (that's good yeah!) and meant that someone who knows the minimal amount of 'code related stuff' could for the first time experience a non-windows / mac related OS that comes with really cool software too! (I'm already a devout believer in Firefox.)

A few questions arose along the way....
The first couple of times the disc would boot and I would be greeted after a short while with a screen containing many coloured square boxes... this was fixed by me choosing the VGA res 1024x768 x32bits so that's OK.

A problem i have not been able to fix is that when I initially log in to Ubuntu there is no visible mouse pointer. The mouse DOES WORK and I find i have to feel my way around to the mouse options and although changing the mouse pointer to 'highlight when press 'Ctrl'... I am still not able to change the pointer style.
If I start Ubuntu in Safe Graphics mode I ONLY get a mouse pointer and NOTHING else appears on the screen EVER.

The next problem i'm encountering is that the Disc Partitioner is not being all together helpful with it's instructions.
I have 2 Physical HDD's 1x 120gb and 1x 140gb. Each have their own uses to me.
The disc partitioner helped me create a virtual partition on the desired drive but I was forced to boot Windows, format it there and try again in Ubuntu to select the 11Gb partition I have created. (Windows helped me finalise the partition and assign it a letter, It's called "E" so i now have C:, E:, and J:)
So, even after I formatted the partition in Windows, rebooted Ubuntu from the CD, reloaded my "Highlight mouse when Ctrl button is pressed", and went to the LOAD UBUNTU, I am still UNSURE HOW to select the 11Gb "E:" from the /root, /Dev, / etc screen. 
The instuctions need to be more specific at that point for someone like me to be able to select the Drive I want to use from a list and then know what folder to use from there. 
Even now i wouldn't know whether to use /DEV, /root, etc?
And do i need to create ANOTHER PARTITION for the swap file?
I have no idea.

I really appreciate what you are all doing and look forward to one day being able to use your OS.

Rgds,


From what I gather you formated the partition in windows. Im hoping that you use the installer and let it set up the partitions without doing to much. Because if you pointed it to a space it would create the swap file and format it in ext3 format for linux. So I dont think you need a swap partition.
Linux doesnt use drive letters. Even if you could see it as drive E on the windows install Ubuntu wont call it E: . You can think of it as E: if you want, but to Ubuntu its the file system. In other words E: is all the folders.
Pretty much the only area you as a user can write to is your home folder. So dont worry about /dev or /root. You cant write to them because its part of the system. Ubuntu protects itself from something messing it up. This is why viruses and spyware cant mess with it.
I have a feeling your missing mouse is because you need to install the video card drivers. [You can find info on how to do that here.]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by djeremy on 2006-09-28
I let it's auto install do it's thing and it's formatted my HDD with all my overseas photos on it!!!

Can you recommend an un-format program that will recover my lost photos from my holiday i got back from last week???

Please help - really pissed off!!!!!

---

### Post by DRF on 2006-09-28
I've seen some programs for windows to recover files accidently deleted from a removable disk. But if you have formatted the disc (and more so if you have written to the disk since) I would be surprised if those tools would work. (but still worth looking online in case I'm wrong)

I hope you sent a copy of the pictures to a friend of made a backup.
Hope this doesn't deter you from trying ubuntu and opensource products in the future. (when ever I've dual booted windows and linux it's normally windows that wants to wipe out linux)

If you are still trying to install ubuntu and windows on the same computer I would install windows first but only partition part of the hard drive and leave some space unallocated. Then from the ubuntu installer choose the option to install into free space. (Not the format and use entire hard disk drive option) checking that the confirmation box before you install describes what you want to do.
If you get the option to resize the windows partition and use the free space that's another easy option, if it doesn't work often the cause is an unclean ntfs partition. Running check disk from windows before installing will often fix this.

Alternativly if you want a complicated partition setup the way i set it up on my computer is to use the Gparted live CD (a search for gparted should find the website) which will allow you to partition your hard drive how you want so from ubuntu/windows/other you only need to choose the partition to install to. (make sure to have at least a 256mb swap partition, and a reasonable sized ext3 partition for ubuntu).

Daniel

*P.S I know the manual partitioner in the installer is gparted but I've had more luck with the gparted live cd in the past and the gparted version on the live cd may well be able to perform operations not supported on the ubuntu installers version of gparted - but that is an option if you want to use that partitioner, remember with gparted what each partitions ID is (hda1 hda2 etc) as you'll need this when your asked what partition to install into.*

---

