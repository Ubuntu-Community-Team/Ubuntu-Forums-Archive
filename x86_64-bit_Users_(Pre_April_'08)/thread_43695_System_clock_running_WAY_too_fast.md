---
title: "System clock running WAY too fast"
date: 2005-06-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by zue on 2005-06-22
I originally posted this as a reply to an old thread on the Warty forum but I figured this was a more apporopriate place for it, since I'm running 64 bit Hoary and I have a pretty good idea that it's a problem unique to machines with 64 bit chips.

The problem is that my system clock is running more than twice as fast as it should be. (It goes up by a minute every 25sec or so).  I checked my hardware clock using hwclock --show, and that is running at normal speed.

I was directed to the following site by another user:

[http://fedoraforum.org/forum/showthread.php?t=51012](http://fedoraforum.org/forum/showthread.php?t=51012)

I modified /boot/grub/menu.lst as is suggested on that forum and the relevant code now reads:

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro console=tty0 no_timer_check

I added the no_timer_check to the kopt line, and ran update-grub as root, but the system clock is still zooming away oblivious to real time.

Did I miss something?  Should the no_timer_check go somewhere else, or should I maybe try something completely different?  Incidently, the problem persists when I run the live cd for the 32 bit version of Warty. 

Thanks in advance,
Zue

---

### Post by NickB on 2005-06-22
It's in the right place, but you need a 2.6.12 kernel, or else hand patch a 2.6.11 kernel.

Nick

---

### Post by zue on 2005-06-23
[QUOTE=NickB]It's in the right place, but you need a 2.6.12 kernel, or else hand patch a 2.6.11 kernel.

Nick[/QUOTE]


Sweet, thanks.  ...so, could you tell me quickly how to update the kernel or is that something lengthy that I should look up somewhere else first before asking?

Thanks again,
Zue

---

### Post by FrzzMan on 2005-06-23
WoW

64-bit clock run twice as fast than a 32-bit clock...

Coooooooooooooooooooooooool...

---

### Post by tseliot on 2005-06-25
I used Breezy Repositories although someone thinks this shouldn't be done (it worked for me)

---

### Post by Brandon Hoult on 2005-07-06
I seem to be having the same problem as everyone else.  I added the option to my grub menu and updated to the 2.6.12 kernel from breezy, but the clock is still fast.  I disabled apic and that fixed the clock, but my network controller quit working.  Any other ideas?

---

### Post by joekr on 2005-07-06
Are you guys sure the time is passing by faster?  Or is the clock set more than a few hours ahead?  If it's the latter, you may be displaying your time in GMT/UTC mode within your Desktop Environment, **or** your BIOS may be set to a different timezone than you are currently in.

---

### Post by Jet2k5 on 2005-07-06
Sorry I don't know how to help, but I just wanted to state that this is good that this guy is getting fast replies.  Like we were talking about we need to get this forum up and moving with fast technical support :).  

Counting down 2 more weeks until I have my computer ... BTW be ready for my post explaining my hardware and if it's going to work.  I've been doing A  LOT OF GOOGLING and it seems most of my hardware is good to go.  

Keep the questions coming, and answers!

---

### Post by Seth on 2005-07-06
[QUOTE=Jet2k5]Sorry I don't know how to help, but I just wanted to state that this is good that this guy is getting fast replies.  Like we were talking about we need to get this forum up and moving with fast technical support :).  

Counting down 2 more weeks until I have my computer ... BTW be ready for my post explaining my hardware and if it's going to work.  I've been doing A  LOT OF GOOGLING and it seems most of my hardware is good to go.  

Keep the questions coming, and answers![/QUOTE]
 I'm having the same problem 2.6.12 kernel makes my clock advance about 100x too fast. I booted into single and ran 'top' since it had a clock, and things just ZOOM by.

The 2.6.10 kernel does not have this problem.

I'm running a 32-bit machine, so it's not just 64-bit.

---

### Post by FluffyElmo on 2005-07-06
What chipset is everyone running? I don't have this problem, sounds like it could be a BIOS/driver issue?

---

### Post by Brandon Hoult on 2005-07-06
Spent a few more hours looking around and still have not found a solution to the fast clock problem.  Apparently the no_timer_check has been working for most people with the 2.6.12 kernel, but I can't see that it accomplishes anything for me.  I am using a Compaq Presario R4000 notebook, and have managed to get everything else to work except for this.

---

### Post by zue on 2005-07-07
[QUOTE=joekr]Are you guys sure the time is passing by faster?  Or is the clock set more than a few hours ahead?  If it's the latter, you may be displaying your time in GMT/UTC mode within your Desktop Environment, **or** your BIOS may be set to a different timezone than you are currently in.[/QUOTE]

It was definitely going too fast.  When I ran time-admin I could see that the seconds were going by twice as fast as they should be.  The no_timer_check boot paramater and the 2.6.12 kernel fixed it for me.

> What chipset is everyone running? I don't have this problem, sounds like it could be a BIOS/driver issue?

I'm running the ATI RS480 Chipset.

---

### Post by Brandon Hoult on 2005-07-07
One more thing that may be relavent... I am using 32 bit mode (k7 kernel).  Is the no_timer_check option only in the k8 kernel?

---

### Post by Brandon Hoult on 2005-07-07
[QUOTE=Brandon Hoult]One more thing that may be relavent... I am using 32 bit mode (k7 kernel).  Is the no_timer_check option only in the k8 kernel?[/QUOTE]
 Well, just did a grep of the 2.6.12 source tree and it seems that the no_timer_check is only valid for the 64 bit arch.  I was going to avoid 64 bit until it was a little more mature, but if there is no other way to get this to work I suppose I better start re-installing when I finish downloading the 64-bit image.

If anyone knows of another way to fix the clock problem for the 32 bit kernel I would really appreciate some advice before the 64bit image finishes in a couple of hours.  Thanks.

---

### Post by FluffyElmo on 2005-07-07
Some people have mentioned that enabling/disabling apm as well as apic has an effect on this. Since apm doesn't work on 64bit anyways I didn't mention it. 

I think though that with 32bit you'll have to choose between a working clock and a working network card. So 64bit may be a viable option...

---

### Post by Brandon Hoult on 2005-07-08
[QUOTE=FluffyElmo]Some people have mentioned that enabling/disabling apm as well as apic has an effect on this. Since apm doesn't work on 64bit anyways I didn't mention it. 

I think though that with 32bit you'll have to choose between a working clock and a working network card. So 64bit may be a viable option...[/QUOTE]
 Well, I upgraded to the 64-bit version and now everything seems to work.  It may be my imagination, but the computer seems a bit more responsive as well.  I got the 2.6.12 kernel from breezy even though there are numerous posts that this is a bad idea.  I am not sure why this is a problem, so far everything looks good.  Hopefully it will be ok until breezy comes out.

---

### Post by FluffyElmo on 2005-07-08
There are a lot of problems relating to X on Breezy right now. I 'accidentally' updated and it *wasn't* fun. In general, grabbing packages from Breezy right now is a hit or miss affair, in another month the situation will have improved a lot but for now it's best to use the Breezy repositories as a last resort.

Glad you were able to get everything working!

---

### Post by NickB on 2005-07-08
[QUOTE=Brandon Hoult]Well, I upgraded to the 64-bit version and now everything seems to work.  It may be my imagination, but the computer seems a bit more responsive as well.[/QUOTE]
Hehe, not your imagination.  I was even able to compile a custom pre-emptive kernel which was even more responsive.  (WARNING: EXPERIMENTAL for 64-bit, but I have had no problems with it.  Well, that's not true... I've had problems with the ATI drivers, but that may purely be an ATI problem ;)

Nick

---

### Post by locutus42 on 2005-07-09
Brandon,

  I have a Compaq R4000 also and have figured out how to fix the 2x clock problem and the IDE DMA problem( disabled ).

Here's a diff of the io_apic.c file:
/R4000/How-To/Patches/Kernel-timerhack$ diff arch_i386_kernel-io_apic.c arch_i386_kernel-io_apic.cORG
2134d2133
< static int timer_hack = 0;
2169,2171c2168
<               /*if (timer_irq_works()) {
<                */
<               if ((!timer_hack) && timer_irq_works()) {
---
>               if (timer_irq_works()) {
2246,2251d2242
< static int __init timerhack(char *str)
< {
<       timer_hack = 1;
<       return 1;
< }
< __setup("timerhack",timerhack);

you'll then want to add "timerhack" to the #kopt line in /boot/grub/menu.lst and run:
sudo update-grub

The IDE DMA problem requires changes to 2 files: atiixp.c and pci_ids.h. Here are the  diffs:
/R4000/How-To/Patches/Kernel-atiixp$ diff drivers_ide_pci_atiixp.c drivers_ide_pci_atiixp.cORG
344,346c344,345
<       if (!try_module_get(THIS_MODULE))
<               return -ENODEV;
<       /*return ide_setup_pci_device(dev, &atiixp_pci_info[id->driver_data]); djl*/
---
>       if (!try_module_get(THIS_MODULE))
>               return -ENODEV;
352,354c351,352
<       { PCI_VENDOR_ID_ATI, PCI_DEVICE_ID_ATI_IXP200_IDE, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0},
<       { PCI_VENDOR_ID_ATI, PCI_DEVICE_ID_ATI_IXP300_IDE, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0},
<       { PCI_VENDOR_ID_ATI, PCI_DEVICE_ID_ATI_IXP400_IDE, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0},
---
>       { PCI_VENDOR_ID_ATI, PCI_DEVICE_ID_ATI_IXP_IDE, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0},
>       { PCI_VENDOR_ID_ATI, PCI_DEVICE_ID_ATI_IXP2_IDE, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0},

and:

/R4000/How-To/Patches/Kernel-atiixp$ diff include_linux_pci_ids.h include_linux_pci_ids.hORG
346,348c346,347
< #define PCI_DEVICE_ID_ATI_IXP200_IDE  0x4349
< #define PCI_DEVICE_ID_ATI_IXP300_IDE  0x4369
< #define PCI_DEVICE_ID_ATI_IXP400_IDE  0x4376
---
> #define PCI_DEVICE_ID_ATI_IXP_IDE     0x4349
> #define PCI_DEVICE_ID_ATI_IXP2_IDE    0x4369  /* True name not yet sure */

or I could just email you the kernel.deb and headers.deb files generated when I rebuilt the kernel(stock 2.6.10-5 except for above patches and CPU=K7 ).

As far as getting ATI's proprietary driver working goes, I just had to change pci_find_class to pci_get_class in the /lib/modules/fglrx/build_mod/agpgart_be.c file and update the GCC line in the build_mod/make.sh script. Oh, after using "alien" to gen a .deb from the .rpm and using dpkg --force-overwrite -i fglrx-xxxxxxx.deb to install it.

Cheers.

---

### Post by Brandon Hoult on 2005-07-11
> **locutus42]Brandon,

  I have a Compaq R4000 also and have figured out how to fix the 2x clock problem and the IDE DMA problem( disabled ).

Here's a diff of the io_apic.c file:
/R4000/How-To/Patches/Kernel-timerhack$ diff arch_i386_kernel-io_apic.c arch_i386_kernel-io_apic.cORG
2134d2133
< static int timer_hack = 0 said:**
> ); djl*/
---
>       if (!try_module_get(THIS_MODULE))
>               return -ENODEV;
352,354c351,352
<       { PCI_VENDOR_ID_ATI, PCI_DEVICE_ID_ATI_IXP200_IDE, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0},
<       { PCI_VENDOR_ID_ATI, PCI_DEVICE_ID_ATI_IXP300_IDE, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0},
<       { PCI_VENDOR_ID_ATI, PCI_DEVICE_ID_ATI_IXP400_IDE, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0},
---
>       { PCI_VENDOR_ID_ATI, PCI_DEVICE_ID_ATI_IXP_IDE, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0},
>       { PCI_VENDOR_ID_ATI, PCI_DEVICE_ID_ATI_IXP2_IDE, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0},

and:

/R4000/How-To/Patches/Kernel-atiixp$ diff include_linux_pci_ids.h include_linux_pci_ids.hORG
346,348c346,347
< #define PCI_DEVICE_ID_ATI_IXP200_IDE  0x4349
< #define PCI_DEVICE_ID_ATI_IXP300_IDE  0x4369
< #define PCI_DEVICE_ID_ATI_IXP400_IDE  0x4376
---
> #define PCI_DEVICE_ID_ATI_IXP_IDE     0x4349
> #define PCI_DEVICE_ID_ATI_IXP2_IDE    0x4369  /* True name not yet sure */

or I could just email you the kernel.deb and headers.deb files generated when I rebuilt the kernel(stock 2.6.10-5 except for above patches and CPU=K7 ).

As far as getting ATI's proprietary driver working goes, I just had to change pci_find_class to pci_get_class in the /lib/modules/fglrx/build_mod/agpgart_be.c file and update the GCC line in the build_mod/make.sh script. Oh, after using "alien" to gen a .deb from the .rpm and using dpkg --force-overwrite -i fglrx-xxxxxxx.deb to install it.

Cheers.
 I think I saw bits and pieces of these patches when I trying to get the 32 bit kernel to work.  Now that I have the 64bit version working I will probably just stick with it unless you know of any reason not to.  I am actually using the machine as a server for a small advertising business so the video does not need to be accelerated.  Once everything is working I hope to stick it on a shelf, close the lid and forget about it as much as possible.  I have another one similar to this (presario R3000) as my personal workstation.  I have an old version of Mepis on it at the moment but may put Kubuntu on that as well soon... will likely need your patches then.   Thanks.

---

### Post by haplo on 2005-07-13
Hello!

I have a compaq R4000 and all the problems that u post here.

[QUOTE=locutus42]
or I could just email you the kernel.deb and headers.deb files generated when I rebuilt the kernel(stock 2.6.10-5 except for above patches and CPU=K7 ).
[/QUOTE]

Could you send me .deb generated for AMD64? I don't know how to apply the patch, I've downloaded the sources but I can't compile it properly

[QUOTE=locutus42]
As far as getting ATI's proprietary driver working goes, I just had to change pci_find_class to pci_get_class in the /lib/modules/fglrx/build_mod/agpgart_be.c file and update the GCC line in the build_mod/make.sh script. Oh, after using "alien" to gen a .deb from the .rpm and using dpkg --force-overwrite -i fglrx-xxxxxxx.deb to install it.

Cheers.[/QUOTE]

Which line is the "GCC line" in the make.sh script? I can't find it

Thank you very much.

---

### Post by jon_gunnar on 2005-07-13
[QUOTE=FluffyElmo]What chipset is everyone running? I don't have this problem, sounds like it could be a BIOS/driver issue?[/QUOTE]

I'v got a Asus A8N-SLI Deluxe card / nForce4.
Ubuntu AMD64 states that it can't find/access the hardware clock. But most of the time it runs normaly in fact.

---

### Post by GuyveR800 on 2005-07-13
[QUOTE=jon_gunnar]I'v got a Asus A8N-SLI Deluxe card / nForce4.
Ubuntu AMD64 states that it can't find/access the hardware clock. But most of the time it runs normaly in fact.[/QUOTE]
Same here on an Acer Aspire 5024WLMi laptop. I got the system clock running at normal speed by booting the kernel with 'noapic nolapic noapictimer'. APIC was causing lots of errors in 'dmesg' anyway, and apparently it's not needed or beneficial.

---

### Post by FluffyElmo on 2005-07-13
The fast clock speed issue seems to be restricted to ATI motherboard chipsets, Google turns up many posts about it for other distros...not just Ubuntu. These chipsets are new and support will probably catch up eventually.

The "Cannot access the Hardware Clock via any known method." problem is pretty much a cosmetic issue. I've always had it but have never had problems with clock accuracy. 

There is more information on the HW Clock issue in the bug report for it. It is often solved with a BIOS updates or by changing when the clock detection is run (*mv /etc/rcS.d/S18hwclockfirst.sh /etc/rcS.d/S26hwclockfirst.sh*). [https://bugzilla.ubuntu.com/show_bug.cgi?id=1659](https://bugzilla.ubuntu.com/show_bug.cgi?id=1659)

---

### Post by brighton on 2005-07-14
i remember that during the kubuntu64 install the system time setting screen said something about GMT time thats the part i think i screwed up

---

### Post by GuyveR800 on 2005-07-14
[QUOTE=brighton]i remember that during the kubuntu64 install the system time setting screen said something about GMT time thats the part i think i screwed up[/QUOTE]
Nah... That setting just controls if your hardware clock keeps GMT time (and then Ubuntu will compensate for that according to your timezone), or if it keeps your local time. Either setting is fine :)

---

### Post by Flac on 2005-07-15
on the subject of clocks, i've heard a few people mention it but only offhandedly.

 Right now i dual boot winXP pro and ubuntu64-bit, My ubuntu time is always fine, but whenever i boot to ubuntu and then back into windows, windows clock is a few hours off. Anyway to fix this? im assuming ubuntu is interacting with the system clock in a different way then windows is so it causes conflict with the time? I donno...

 Im really new to linux, so if there is a solution to this problem, try to keep it simple for the stupid man? *points to self* :p

thanks for any help/advise that can be offered.

---

### Post by FluffyElmo on 2005-07-15
Windows stores the time in the BIOS as local time. Ubuntu by default stores the time in the BIOS as UMT. So when you go back and forth your clock will be off by the number of hours between your timezone and UMT.

So the trick is to get Ubuntu to store the BIOS time as your local time. Unfortunately I don't know how to do that except at install but at least you should know what to search for?

---

### Post by brighton on 2005-07-15
thanks elmo that sounds about right

now to find the solution, hopefully i just have to do something like edit an etc config file to run in local time

---

### Post by joekr on 2005-07-15
[QUOTE=FluffyElmo]Windows stores the time in the BIOS as local time. Ubuntu by default stores the time in the BIOS as UMT. So when you go back and forth your clock will be off by the number of hours between your timezone and UMT.

So the trick is to get Ubuntu to store the BIOS time as your local time. Unfortunately I don't know how to do that except at install but at least you should know what to search for?[/QUOTE]

If that is indeed the case, I suggest looking for files **/etc/conf.d/clock** or **/etc/conf.d/local** or similar... those are the files which will most likely contain what you all are looking for ;)

---

