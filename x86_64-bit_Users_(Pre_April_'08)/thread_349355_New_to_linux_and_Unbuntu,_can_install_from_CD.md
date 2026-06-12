---
title: "New to linux and Unbuntu, can install from CD"
date: 2007-01-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Micke Witt on 2007-01-30
Hi!
I´m new to Linux and Ubuntu and having problems to install on my AMD64. 
Booting from the install CD (Ubuntu 6.10 AMD64) and gets the install options, selects install and the installation hangs on "Loading kernel" with a blinking command promt. Nothing happens after that, does not read from CD and I have to do a manual reboot.

Tried it with Kubuntu AMD64 6.10, same result. Guess this is a driver problem, but have no idear on how to proceed.

My specs are:

ASUS A8N SLI Motherboard
2 GD RAM
AMD Dual core 4400 x64
Nvidia 7800 GTX
Soundblaster X-Fi Fatal1ty

Thankfull for any help I can get.

/Micke

---

### Post by mvaniersel on 2007-01-30
a few quick suggestions:

*  there could  be a scratch on the CD.  Have you tried to run the cd check option when you boot the live cd?
* hardware support for different distro's is very different. I had tons of problems with fedora before I switched to ubuntu. For you it may be opposite, I would certainly recommend trying out different live cd's (e.g. knoppix) and see if you have better luck with those.

---

### Post by Micke Witt on 2007-01-30
Well the media is ok, fresh from the burner and I tried both Ubuntu and Kubuntu, so it seem unlikely they would have the same problem based on the media.

/Micke

---

### Post by xmastree on 2007-01-30
Have you tried the 32 bit (i386) version? I would be tempted to try that.

---

### Post by Micke Witt on 2007-01-30
Well, 32-bit is up for trial, but having a 64bit proc. seems a waste of money...
/Micke

---

### Post by mvaniersel on 2007-01-31
xmastree has a good point. There are still issues with 64-bit drivers etc. I've got two amd64 machines but I run 32 bit ubuntu on both of them

Installing 32-bit ubuntu may be a waste of money, but
installing 64-bit ubuntu is a waste of my time.

---

### Post by xmastree on 2007-01-31
> **mvaniersel said:**
> xmastree has a good point. There are still issues with 64-bit drivers etc. Thanks for confirming that. When I tried it, there were issues with certain things, and some programs wouldn't work without hassle (chroot?) so I went with the 32 bit version instead. It wasn't recommended for new users.

I wasn't sure of the current status, so I couldn't comment.

**Micke**, I would suggest, run with 32bit until the 64bit's problems have been resolved and your linux skills have improved, then make the switch.

---

### Post by bearswatchin on 2007-01-31
I am fairly new to Linux but have 'played' with it since SuSe 7.1.

I am also having a problem with 64 bit Linux. Ubuntu will boot from CD and freeze at the Ubuntu splash screen. Tried the SuSe 64 bit - same problem. Tried PCLinuxOS - Same problem. The problem occurs with either the live CD or a DVD full install disk on either of the distros listed.  (Not PCLinuxOS) I did manage to successfully install SuSe 10.0 from CD but I want Ubuntu 6.10.

Bottom line: I cannot seem to install a 64 bit distribution of any flavor.

System:
AMD 64 X2 @ 2ghz each
200 gig hd with XP MCE2005
40 gig hd dedicated to Linux
DVD RW
1.2 gig RAM
NVIDIA video
Nvidia ethernet

Another question, probably pretty simple but my brain is fried: I need to run fdisk /mbr to fix a boot problem. No floppy drive. Can anyone tell me how to make a CF card bootable so I can put Win 98 startup on it and run the fdisk /mbr?

---

### Post by incubus on 2007-02-01
I wonder if it could be something related to the graphics card.

This is just my two cents, but I would recommend trying the good ol' non-graphical installer.  It's never failed me and despite the appearance it's very straightforward to follow.  On my laptop with an ATI card, that was the only way I could get the installation to work.  (If I remember correctly, it used to hang up on the Loading Kernel message as well)

If you can get Ubuntu installed from that, we can debug some logs and see what could be the source of the problem -- if it persists.

incubus

---

### Post by incubus on 2007-02-01
> **bearswatchin said:**
> 
Another question, probably pretty simple but my brain is fried: I need to run fdisk /mbr to fix a boot problem. No floppy drive. Can anyone tell me how to make a CF card bootable so I can put Win 98 startup on it and run the fdisk /mbr?

By "CF card", do you mean "compact flash card"?  I don't have much experience on that area, but I believe you need to:
1. check the boot sequence in the BIOS setup
2. copy some boot files to the CF.  If you are using windows and if memory serves me, I think you can format with the option of copying system files.

But if you have a windows xp disc, you can also run "fixmbr".  Or a command similar to that.

I'm glad I'm forgetting all these things. : )

incubus

---

### Post by joN_jai on 2007-02-01
> **Micke Witt said:**
> Hi!
I´m new to Linux and Ubuntu and having problems to install on my AMD64. 
Booting from the install CD (Ubuntu 6.10 AMD64) and gets the install options, selects install and the installation hangs on "Loading kernel" with a blinking command promt. Nothing happens after that, does not read from CD and I have to do a manual reboot.

Tried it with Kubuntu AMD64 6.10, same result. Guess this is a driver problem, but have no idear on how to proceed.

My specs are:

ASUS A8N SLI Motherboard
2 GD RAM
AMD Dual core 4400 x64
Nvidia 7800 GTX
Soundblaster X-Fi Fatal1ty

Thankfull for any help I can get.

/Micke



I had the same problem.
WHen you at the start up screen, press F6 and a Boot line will pop up.
at the end of the line you will see" -- " type noapic nolapic

it'll look like this

"-- noapic nolapic"

---

### Post by bearswatchin on 2007-02-06
Follow up on my previous post on this subject: 

I managed to install Ubuntu as a virtual machine on my XP MCE system. That is the only way I have found to run it.

Does anyone know if it is possible the vendor of the machine can install some kind of "lock" that would cause the machine to not allow installation of 'alien' software? I am getting pretty frustrated with the whole thing and am about ready to do a clean install. With my luck the "lock" would be in the bios. :( 

bw

---

### Post by Oxides on 2007-02-07
I have the same problem booting off the 64bit CD(ubuntu-6.10-desktop-amd64.iso).  Graphics are messed up at the splash screen with the progress bar and check cd screen.  When i get to the peach desktop screen it totally hangs.  If i use 32bit I boot off the CD fine.  I haven't tried that apic command yet.

My system:
DFI lanparty nf4-d AMD X2 3800 4G ram
Nvidia 7800GTX
SB Audigy2 value

None of that hardware is new or cutting edge:(

Update: The previous version boots correctly (ubuntu-6.06.1-desktop-amd64.iso).  So the 6.10 release is defective somehow.

---

