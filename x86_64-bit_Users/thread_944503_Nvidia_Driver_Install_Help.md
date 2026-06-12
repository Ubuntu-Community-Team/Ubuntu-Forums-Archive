---
title: "Nvidia Driver Install Help"
date: 2008-10-11
forum: x86 64-bit Users
---

### Post by wagb278 on 2008-10-11
Newbe - be gentile; 

I have a MSI Nvidia 9600 GT video card being used in very basic mode - no card specific driver. Decided to try installing a vendor driver. Found one (version 177.80) on an Nvidia web site. My 64-bit Ubuntu 8.04 is up to date.

Reading the README file it gives instructions to verify dependent software is resident on the computer using the following suggested commands:

Software Element_____Min Requirement_____Check With...
Linux kernel_________2.4.7_______________cat /proc/version
XFree86/X.Org_______4.0.1/6.7 __________XFree86 -version/Xorg -version
Kernel modutils______2.1.121_____________insmod -v

The last two (XFree86 and insmod) return Not Found. But a file search finds files with those names. XFree86 search finds 9 files and insmod returns 3 files.

I suspect that I need links to the correct files in the correct location for the install to work. If the files are not found by me in a terminal window - the install process will not be able to find them. 

Once that is resolved - Reading further it tells me to terminate the X server and terminate all OpenGL applications and suggests to set the default run level to boot to a VGA console and not into X.  I HAVE NO CLUE! Can someone help me here?

Thanks,
Jim

PS Solved by using envyNG and selecting manual driver install.

---

### Post by linux_lover69 on 2008-10-11
I found that its easiest to go to system then hardware drivers and click enable beside the driver and then let it install.

---

### Post by nikgare on 2008-10-11
What do you get if you go to System->Administration->Hardware drivers?
Is the nvidia driver listed?
You may need to enable it here.

---

### Post by wagb278 on 2008-10-11
No Hardware drivers appear. The list is empty

---

### Post by Elim_Garak on 2008-10-13
> **wagb278 said:**
> Once that is resolved - Reading further it tells me to terminate the X server and terminate all OpenGL applications and suggests to set the default run level to boot to a VGA console and not into X.  I HAVE NO CLUE! Can someone help me here?

[FONT="Courier New"]For this part, the way I did it, as I recall, is to reboot and go into the recovery mode.  I was confused for a time, too, but got the driver package from NVidia to work.[/FONT]

---

### Post by dabl on 2008-10-13
Assuming version 8.04 or earlier, and not 8.10, open the console window and:

```
sudo apt-get install envyng-core
```

(when it finishes installing)

```
sudo envyng -t
```

Choose #1 "Install Nvidia Driver"

follow onscreen instruction, including the final step, #5 "Restart X server".

That's it.  :)

---

### Post by wagb278 on 2008-10-13
Thanks for the advice.

I discovered the restart in recovery mode which gave me a non GUI interface. - Thanks Elim_Garak!

I tried EnvyNG and it does not recognize my card. I get the following
```
Envy does not recognise your card as compatible with any version of the driver. 
this might happen because either your card is not supported by the driver or Envy's hardware detection failed. 
```

I performed a "sudo lspci -v" command and get the following:
```
01:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 1270
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at e2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at e0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Expansion ROM at <ignored> [disabled]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint IRQ 0
	Capabilities: [b4] Vendor Specific Information

```

I suspect the "Unknown device 1270" output (above) is because there is no driver active - other than basic VGA.

I tried installing the new driver from NVidia (while in the Ubuntu recovery mode) as root. It failed because there was no pre-built module available for the installed Linux kernel. 

**dabl** - can you do a "sudo lspci -v" and tell me what yours says? What manufacturer card do you use?

Are there utility applications that can interrogate my card and provide useful information?

I noticed that Envy uses driver version 173.14.12; that should be new enough to recognize my card, unless it is a quirk with the MSI card. The current driver version on the NVidia web site is 177.80

Why does my System --> Administration --> Hardware Drivers list not contain even older versions of a NVidia drivers? I believe I have all the correct repositories enabled as "Sources".  But maybe not; what repository has the third party NVidia drivers?

Thanks for the assist.  

Oh yes - I am running 8.04 64-bit.  I have considered trying SuSE version 11, but I loaded that on an old P-III machine and I don't like it.  Think I will stick with Ubuntu.

---

### Post by phlembob on 2008-10-13
[https://help.ubuntu.com/community/Bi...erHowto/Nvidia](https://help.ubuntu.com/community/Bi...erHowto/Nvidia)

[http://ubuntuguide.org/wiki/Ubuntu:H...ricted_drivers](http://ubuntuguide.org/wiki/Ubuntu:H...ricted_drivers)

or just

alt & f1 = console

then

sudo /etc/init.d/gdm stop

sudo sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run

Do not download the kernel module, just say no if nvidia is asking..

after that install, configure your xorg.conf..(nv to nvidia)

And start gdm again

sudo /etc/init.d/gdm start

but i rather would go with envyng because it makes your life easier.. i think..

and maybe someone is posting a detailed how to.. or a better link
:guitar:

---

### Post by wagb278 on 2008-10-13
Thanks phlembob, I must admit that CTL+Alt+F1 and stopping gdm worked and allowed the driver install to execute. I must have screwed something up when I tried that yesterday.

I tried your sequence and got basically the same results as before. No module for the kernel. I tried two different driver files (173.14.12 and 177.80) not expecting any difference. It wants to compile and can't - reporting that I don't have "libc" files, or at least not where, or with correct permissions for the installer to use. So it quit.  I am not sure I want to compile anyway. I did a file search and there are a number of libc files in various places. 

The two links you provided are to empty pages, I think you knew that.

I sent an email to Envy with my "sudo lspci -v" output asking for suggestions. Maybe I will hear back.

---

### Post by Elim_Garak on 2008-10-14
> **wagb278 said:**
> 
**dabl** - can you do a "sudo lspci -v" and tell me what yours says? What manufacturer card do you use?


While you asked dabl for his results, I'll give you mine, too, in case you would like another comparison.

```
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0401 (rev a1) (prog-if 00 [VGA controller])
	Subsystem: XFX Pine Group Inc. Unknown device 2286
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=512M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at bf00 [size=128]
	[virtual] Expansion ROM at fb000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint IRQ 0

```

Mine shows it as an unknown device (everything in Ubuntu is an unknown device, it would seem).  :lolflag:

However, it does work, and I got the driver from NVidia installed.  I was tempted to try Envy as well, but I tried with the vendor driver first, and it worked fine.  The card works nicely.

---

### Post by dabl on 2008-10-15
Sorry -- I'm away from my Kubuntu system and can't post the lspci output.  However, I can state that it is an EVGA card, and it does show up correctly in the lspci listing.

Also, the 64-bit 177.80 driver is what I'm using, and it is working very well.  I installed it using the downloaded driver from Nvidia.  Obviously you need to make sure you have installed the kernel-headers-$(uname -r) and build-essential packages first, and do the installation from a tty console with the X server shut down.

I haven't checked it without Compiz running, but with Compiz glxgears give me 8000 - 9000 fps, under Kubuntu 8.10, kernel 2.6.27-7, for whatever that is worth, running a 1600 x 1200 desktop.

---

### Post by wagb278 on 2008-10-16
OK, I am willing to try the compile. Just what do I need to download to make this happen?

I presume I need to do some "getting" - but what?

If anyone knows why my system --> Administration --> Hardware drivers is empty I welcome ideas. What Software Source is supposed to include the Nvidia drivers?

An interesting item - I just installed Ubuntu 8.04 on an old computer (32-bit P-III) that happens to have a Nvidia card. That install asked if I wanted to use the Nvidia Legacy driver which it located and installed correctly. Why would a 64-bit version of Ubuntu 8.04 not do the same?  I compared the repositories enabled on both installations and they both have restricted repositories enabled.

Thanks for all the help people.

---

### Post by wagb278 on 2008-10-18
I tried EnvyNG again and this time elected to use the Manual Select Driver option. It installed the 173.14.12 driver without error. I believe I now have a working video card that Ubuntu knows about.

I guess I miss-understood the "Manually Select Driver" in EnvyNG. It should say Manually select and install.

In System -- Preferences -- Appearance (Visual Options): I enabled the third option (extra) and it took. I now have nice visual effects; not a big deal - but nice.

Then I installed Google Earth, that being one application I like to use that had problems without an appropriate video driver. That too is working just fine. 

I still do not have an entry in Third Party Drivers under System -- Administration.  I would expect to see something there for the Nvidia card, but I'm not complaining. 

In summary I have:
  Linux version 2.6.24-21-generic 
  MSI nVidia Geforce 9600 GT OC 512mb 
  Mobo: Intel DP35DP with Quad Core-2 Q6600 2.4GHz and 4GB RAM

All is working just fine. Thanks to all the help from the community. I will make this thread solved.

---

### Post by grondinmf on 2008-10-28
> **phlembob said:**
> [https://help.ubuntu.com/community/Bi...erHowto/Nvidia](https://help.ubuntu.com/community/Bi...erHowto/Nvidia)

[http://ubuntuguide.org/wiki/Ubuntu:H...ricted_drivers](http://ubuntuguide.org/wiki/Ubuntu:H...ricted_drivers)

or just

alt & f1 = console

then

sudo /etc/init.d/gdm stop

sudo sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run

Do not download the kernel module, just say no if nvidia is asking..

after that install, configure your xorg.conf..(nv to nvidia)

And start gdm again

sudo /etc/init.d/gdm start

but i rather would go with envyng because it makes your life easier.. i think..

and maybe someone is posting a detailed how to.. or a better link
:guitar:

I was able to get the driver installed using these steps. but i run into the same problem i had when i used linux before vista came out(i have been using vista since it came out and finally got tired of it so i back to linux) wich is that after i restart X(GDM) it will work compiz works and vdo card is detected properly but as soon as i reboot the machine the driver does not load i have no vdo and ubuntu starts in low-vga mode. if i got back to console and do these steps again it will work again but how can i avoid having to install the driver every time. it's probably a change in the x config i'm just not sure what. any ideas?

Edit: Should Mention that i did try envyng but it did not seem to work. Compiz efects would not work and vdo card not properly detected. i have a gforce 7900

---

### Post by TeXtonyx on 2008-10-29
The instructions I read were to install build-essential
apt-get install build-essential
make sure the dependencies are met.
When the Nvidia process wants to connect to the internet
I think you can say yes, that will fail, and then the
process offers to compile locally and that is what
build-essential is for. 

I've also seen instructions to use chmod on the downloaded Nvidia
driver: -Type "chmod u+x NVIDIA-Linux-x86-177.80-pkg1.run" (without ")

---

### Post by grondinmf on 2008-10-29
i actually got it to work....i was assuming that when i said yes to the final question of configuring X that it was actually doing it...seems it was not cause i downloaded the nvidia xconfig utility and ran that and now it's working great. right after installing the dirver then did a reboot.(had to reinstall ubuntu monday night cause it was all messed up from me trying every wich way to get this driver to work right)

---

