---
title: "HELPPP!!!!!   : broadcom wireless issue"
date: 2007-06-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by atararx on 2007-06-14
Hi,
I just got my new HP Dv6000z laptop and I am having a problem with the wireless.

cpu : amd turion 64-x2  TL-56
wireless card : bcm4310

grub kernel args : 
```
[
title           Ubuntu, kernel 2.6.20-16-lowlatency
kernel          /boot/vmlinuz-2.6.20-16-lowlatency root=UUID=4bff3917-1b8f-40bd-af5d-aa2d496eba6c ro quiet noacpi noapic nolapic nosmp splash
/CODE]

The preinstalled drivers did not work (bcm43xx), Hence, I googled my problem and found the ndiswrapper way.

I installed ndiswrapper 

[CODE]
driver version:        1.38
vermagic:       2.6.20-16-lowlatency SMP preempt mod_unload

```

I then proceeded and set up ndiswrapper

```

$ ndiswrapper -l
bcmwl6 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)

```

I blacklisted the bcm43xx

But my wireless still does not work.

Here is my dmesg output

```

[ 1004.979995] usbcore: deregistering interface driver ndiswrapper
[ 1004.980589] ndiswrapper (ntoskernel_exit:282): object ffff81000cd28a30 type 2 was not freed, freeing it now
[ 1006.841327] ndiswrapper version 1.38 loaded (preempt=yes,smp=yes)
[ 1006.878212] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[ 1006.878448] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 1006.878597] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[ 1006.878744] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 1006.878933] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 1006.879102] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 1006.879261] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[ 1006.879435] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 1006.879603] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 1006.879775] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 1006.879941] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[ 1006.880098] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 1006.880319] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 1006.880482] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 1006.880634] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 1006.880800] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[ 1006.880957] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 1006.881142] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 1006.881299] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 1006.881461] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 1006.881693] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 1006.881849] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[ 1006.882103] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[ 1006.882270] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[ 1006.882440] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 1006.882595] ndiswrapper (load_sys_files:216): couldn't prepare driver 'bcmwl6'
[ 1006.883300] ndiswrapper (load_wrap_driver:118): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'
[ 1006.893878] usbcore: registered new interface driver ndiswrapper

```

I tried installing the latest ndiswrapper drivers but still got the same error.
Is this something to do with the SMP kernel module? ( I set nosmp by following the instructions on [https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)) )

I was unable to find a solution to my problem.
Can someone please help me out?

Thanks

---

### Post by Kobalt on 2007-06-14
First of, you have twice the "noapic" option in your boot line, I think one should suffice :) Then, I've got one of those dv6000 laptop and I only need "noapic nolapic" options to get it workig nicely. Finally, the bcmwl6 drivers did not work with ndiswrapper. I use the good old bcmwl5 and it runs smoothly. You might want to try with this one...

---

### Post by RS3York on 2007-06-14
Unfortunately, "the pre-installed drivers" for bcm43xx are not complete by themselves.

Did you try to use the bcm43xx-fwcutter package before you blacklisted it the native drivers?
I have a bcm4318 wireless card in my Compaq/HP and the firmware file the fwcutter package downloads once you give it permission works great for me, in both 64-bit (Gutsy Testing) & 32-bit (Fiesty Stable) Ubuntu.

Perhaps the situaition is different with the 4310 working with native drivers (versus the 4318 ) but the bcm43xx driver is guaranteed not to work out of the box because Broadcom won't allow Ubuntu/Canonical to distribute the necessary firmware on the install disc.

---

### Post by Mr_bleu on 2007-06-14
Off topic here, but I saw RS3's signature...
"GIMP should really change it's name to GINP in the tradition of WINE & LAME.

GIMP (GINP) Is Not Photoshop."

It's free, why would someone complain about a free program like wine or Gimp? NOthing better to do? I like linux and the Ubuntu community.  Maybe he could write a better photo program and give it out for free.

---

### Post by atararx on 2007-06-15
RS3York  :   I did install the bcm43xx-fwcutter packages. It did not work for me.(As you said, it works for 4318 but I dont think that it is compatible with mine)


Kobalt  :  slight difference, noacpi and noapic. the last 3 alphabets are jumbled in these.
I did try to get the old bcmwl5 files. When I used them, my system did not boot. It got stuck at about 20% of the kubuntu bar. I had to remove it to get my computer to boot again. I am not quite sure why this happens. 
Further, I think that I will have better luck if I can some how manage to get hold of the winXP .exe instead of the vista ones. I am not able to find a winXP 64 bit one (I searched HP , HP/compaq)

Thanks for the responses. Hopefully we can resolve this issue. I am just dying to get my laptop mobile.

---

### Post by atararx on 2007-06-15
Kobalt, do you think that you can give me a link / file with the winXP bcmwl5 driver? I am really hoping that it will work for me.

Did you get a webcam with your dv6000? I have not managed to get mine working. I tried out the linux-uvc driver but I seem to be missing an intermediate step in setting up my webcam.

The remote that came with my laptop worked out of the box :) . I was quite elated when I saw that working.

---

### Post by atararx on 2007-06-15
with the latest ndiswrapper (1.47) and the bcmwl5 module from 
[ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp33009.exe](ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp33009.exe)

```

[  402.747960] ndiswrapper version 1.47 loaded (smp=yes)
[  402.766190] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[  402.767916] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[  402.768418] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 10 (level, low) -> IRQ 10
[  402.768577] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  402.773833] ndiswrapper (NdisWriteErrorLogEntry:192): log: C000138D, count: 1, return_address: ffffffff88b2be7e
[  402.773855] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x10e
[  402.773936] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[  402.773971] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[  402.774027] ndiswrapper (mp_halt:258): device ffff81002b796500 is not initialized - not halting
[  402.774039] ndiswrapper: device eth%d removed
[  402.774089] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[  402.774164] ndiswrapper: probe of 0000:03:00.0 failed with error -22
[  402.780524] usbcore: registered new interface driver ndiswrapper
```

Do you know how to fix this?

---

### Post by Ayuthia on 2007-06-15
Have you checked out this site:

[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))

It has a list of dv6000 models along with the driver that they used.  Hope this helps.

**Sorry!  I did not see your link at the bottom of your first post.  Please disregard my post**

---

### Post by Kobalt on 2007-06-15
> **atararx said:**
> 
Kobalt  :  slight difference, noacpi and noapic. the last 3 alphabets are jumbled in these.

Sorry guys, my eyes betrayed me...

---

### Post by RS3York on 2007-06-15
> **Mr_bleu said:**
> Off topic here, but I saw RS3's signature...
"GIMP should really change it's name to GINP in the tradition of WINE & LAME.

GIMP (GINP) Is Not Photoshop."

It's free, why would someone complain about a free program like wine or Gimp? NOthing better to do? I like linux and the Ubuntu community.  Maybe he could write a better photo program and give it out for free.

Lol, you and I are actually getting to the same point.  Unfortunately now I can see how my signature can be interpreted the way you read it.

My intent is not to say GIMP != Photoshop therefore GIMP is terrible.  Rather my intent is to say that GIMP is not Photoshop therefore don't go to GIMP thinking that you're going to get Photoshop OSS Edition.  Unfortunately GIMP often isn't given a clean slate to prove itself on its own merits.  I suppose LAME is a bad example since it's more of a joke, perhaps I should use WINE & GNU instead since those acronyms are ultimately about getting a common misconception adjusted.

I always find it curious that participants are so often referred to as "he" in many online forums.  I suppose that could be mostly due to a hole in English though - it's either "he" or "she", "they" is technically wrong and "Xe" doesn't exist at all.

Anyway, back on topic...

The file that atararx downloaded from HP seems eligible since it contains 64-bit XP drivers.  The text file that goes with it lists that the drivers are for laptop models: HP Compaq nx6315 & HP Compaq nx6325.

The Nx6315 uses a Broadcom 4311 as per this page (ref: [http://h18000.www1.hp.com/products/quickspecs/12479_div/12479_div.HTML]("http://h18000.www1.hp.com/products/quickspecs/12479_div/12479_div.HTML"))

So that could be the reason why the drivers you downloaded could not initialize your hardware.
From what I have read you did the right things with ndiswrapper, but since I haven't used it in the last some months I can't verify from recent experience.

The only other thing I would venture to suggest is to try with the standard kernel rather than the lowlatency version.  Perhaps it's a bug in Fiesty's lowlatency kernel.  I'm sure you have your reasons for using that kernel (I know DAW work is much improved with it) but it's at least another angle to investigate.

If Kobalt & atararx have the same model and Kobolt's wireless works...then we just need to isolate what's different between them.  So...hopefully they have the same model.

---

### Post by atararx on 2007-06-17
RS3York : 

> The only other thing I would venture to suggest is to try with the standard kernel rather than the lowlatency version. Perhaps it's a bug in Fiesty's lowlatency kernel. I'm sure you have your reasons for using that kernel (I know DAW work is much improved with it) but it's at least another angle to investigate.

Well, honestly, I dont have a clue about what I am doing. I am trying anything and everything I see. How I got the low latency kernel, I have no idea. It just appeared to have appeared.

I will try switching my kernel. (I have a feeling that I got that kernel when I used envy to install my nvidia driver. None of the other methods I tried worked for that. Envy managed to fix it. But now I have other problems like being unable to see my other tty terminals. I can however type in them and I know that it takes input (I can login and do a shutdown -r now ;)  ))

Thanks

---

### Post by atararx on 2007-06-17
no success. I switched back to the generic kernel but I still got the same errors with bcm43xx driver.

I tried ndiswrapper again, I get : 
[  585.363658] ndiswrapper version 1.47 loaded (smp=yes)
[  585.382777] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[  585.384526] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[  585.384954] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 9
[  585.384961] PCI: setting IRQ 9 as level-triggered
[  585.384964] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 9 (level, low) -> IRQ 9
[  585.385006] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  585.390257] ndiswrapper (NdisWriteErrorLogEntry:192): log: C000138D, count: 1, return_address: ffffffff88b2980e
[  585.390263] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x10e
[  585.390275] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[  585.390281] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[  585.390292] ndiswrapper (mp_halt:258): device ffff81001842e500 is not initialized - not halting
[  585.390299] ndiswrapper: device eth%d removed
[  585.390307] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[  585.390317] ndiswrapper: probe of 0000:03:00.0 failed with error -22
[  585.395149] usbcore: registered new interface driver ndiswrapper


$ cat /proc/interrupts
           CPU0       CPU1
  0:     322498      13924    XT-PIC-XT        timer
  1:       4931        182    XT-PIC-XT        i8042
  2:          0          0    XT-PIC-XT        cascade
  5:      13899       1610    XT-PIC-XT        libata
  7:      60870    1066385    XT-PIC-XT        ehci_hcd:usb2
  8:          0          0    XT-PIC-XT        rtc
  9:       7732       1171    XT-PIC-XT        acpi
 10:     135971       8817    XT-PIC-XT        eth0, HDA Intel
 11:     318577      21796    XT-PIC-XT        ohci_hcd:usb1, ohci1394, sdhci:slot0, nvidia
 12:     259571      12977    XT-PIC-XT        i8042
 14:       3651        679    XT-PIC-XT        ide0
NMI:          0          0
LOC:     336310     336292
ERR:    1027872

$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)


Help please .... I am dying to get my wireless working.

---

### Post by firecat53 on 2007-06-18
Well, let me try for you  :)

0. "sudo aptitude install build-essential linux-kernel-headers" (ummmm, I hope I remembered everything for compiling....we may have to tweak this list if I forgot something.)
1. Make sure you have "blacklist bcm43xx" at the end of /etc/modprobe.d/blacklist
2. "sudo aptitude purge ndiswrapper"  -- 
3. "sudo rm -rf /etc/ndiswrapper" -- if it's not there, don't worry
4. Download the bcmwl5 driver for your card. Extract this someplace and keep everything they give you in that directory!
5. Download the latest ndiswrapper source from ndiswrapper.sourceforge.net
6. "tar zxf ndiswrapper*gz"
7. "cd ndiswrapper*"
8. "make" -- if there are any errors, it's probably because I forgot to have you install something important :)
9. "sudo make install"
10. "sudo ndiswrapper -i ~/bcmwl5_directory/bcmwl5.inf"
11. "sudo ndiswrapper -l"  -- make sure this lists something like bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)
12. "sudo modprobe ndiswrapper"
13. "lsmod |grep ndis" -- should give you something like: ndiswrapper           222464  0 
                                        usbcore               135728  7 ndiswrapper,visor,usbserial,r5u870,ehci_hcd,ohci_hcd

You should have a working wireless card now. I never had any luck with stock Ubuntu ndiswrapper or bcm43xx drivers. 

Let me know if I forgot anything!  I've got a dv6000 (6058 cl), so I think it's somewhat similar.
Good luck!
Scott

---

### Post by atararx on 2007-06-18
Scott, 
> 11. "sudo ndiswrapper -l" -- make sure this lists something like bcmwl5 : driver installed
 device (14E4:4311) present (alternate driver: bcm43xx)

I think that therein lies the problem I have
lspci -n : 
03:00.0 0280: 14e4:4312 (rev 02)

and
lspci | grep -i broadcom
03:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 02)

if you see, one is 4312, one is 4310  and if I install bcm43xx, it registers as 4311. I dont think that the drivers are able to recognize my card correctly. Do you know any way to coax them to do so?

Apart from that, the command I followed and the results I got are exactly like yours. Everything is okay until the final step where I do a modprobe nidswrapper. eth1 never shows up.

[ 585.390299] ndiswrapper: device eth%d removed

Any ideas?

Thanks a billion for helping me

---

### Post by Ayuthia on 2007-06-18
By any chance, do you know which dv6000z you have?  If not, the name might be on the HP sticker under your laptop.  It would be listed right above the Warranty:.  Also, does your laptop have the wireless switch and if it does, has it ever lit up?  

I ask this because I ran through a list of drivers that actually worked and didn't realize it until I stopped using the network manager on KDE.  I ended up having to use ifconfig to see if eth1/wlan0 was installed and iwconfig to connect.  I am just curious if the bcm43xx driver changed the light or not.  

Do you still have Windows on your laptop?  If so, does it list your wireless as a 4310?

---

### Post by Ayuthia on 2007-06-18
Have you tried using the drivers from sp33008?  I saw that you tried sp33009.  I looked at another website: [http://www.ianbmacdonald.com/wordpress/debian-linux-on-dv9000z/](http://www.ianbmacdonald.com/wordpress/debian-linux-on-dv9000z/) and saw that he has a 4310 also.  He links over to another site that found that he was trying 32-bit drivers instead of 64-bit so his weren't working for awhile.

---

### Post by Ayuthia on 2007-06-18
Here is what I found at the ndiswrapper website which shows that the card name is 4310 and the chipset is 4312.  It also gives other driver options also. 

#
Card Name: Broadcom Corporation BCM4310 UART (rev 01)

    *
      Ndiswrapper version: 1.23 (need version ndiswrapper 1.31 on Mandriva 10.2 on HP Pavilion dv9001)
    *
      Chipset name: Broadcom BCM4312
    *
      PCIID: 14e4:4312
    *
      Windows driver location: [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe) This file can be extracted with cabextract and contains both 32 bits and 64 bits files. (Try: ndiswrapper -i bcmwl5.inf)
    *
      Using Gentoo AMD64 Kernel Version 2.6.17 on a HP Pavilion dv2000 / Mandriva 10.2 AMD64 Kernel 2.6.15 on HP Pavillion dv9001
    *
      Other: For DV6000 (and maybe others) use [ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe) (resolves random oopses)
    *
      Using ndiswrapper version 1.41 with [ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe) on DV 6000z on Ubuntu 2.6.15-28-k7 #1 SMP PREEMPT Thu Feb 1 16:36:09 UTC 2007 i686 GNU/Linux

---

### Post by atararx on 2007-06-18
so, should I downgrade from ndiswrapper 1.47 to 1.3x ? 
I will try out your suggestions and let you know how it went.

I don't know what you mean by "what kind of dv6000" laptop.
Mine is a dv6000z, amd turion 64 x2  TL-56.

I do have a wireless switch and it does turn from orange to blue every time. 

This forum rocks. Thanks a lot for the help.

---

### Post by Ayuthia on 2007-06-18
If it does go blue, you should go to the terminal and type iwconfig to see if any wireless cards appear.  Sometimes ndiswrapper shows the cards as wlan0 or eth1.  

As for if you should go back to a prior version, I am not for sure.  I would think that the current version would work.  If you have run out of options, you definitely can try.  It does seem that you are getting closer though.

---

### Post by atararx on 2007-06-18
It worked !!!!!!!!!!!!!!!!

Ayuthia : Thanks a lot. I did not have to downgrade my ndiswrapper. I just used the files you suggested -  and viola, wireless was up and running.


I would like to thank everyone here who helped me out. You guys rock. I am finally free. 

Special thanks : 

Kobalt   -  the person who helped me first
RS3York - the guy with the interesting sig 
firecat53  -  with the detailed list of what to do
Ayuthia  - with the magic post.


Thanks a bunch.
Here have some popcorn :popcorn:
:D

---

### Post by Ayuthia on 2007-06-18
[QUOTE=atararx;2868093]so, should I downgrade from ndiswrapper 1.47 to 1.3x ? 

I don't know what you mean by "what kind of dv6000" laptop.
Mine is a dv6000z, amd turion 64 x2  TL-56.

Sorry,  I thought that there were various models of the dv6000z.  Mine is a dv6338se, but by the monitor, it displays dv6000.

I am not for sure if you ever did rmmod bcm43xx or not prior to the ndiswrapper install.  They say that sometimes if you don't, the driver might not install.

Before you try the other options, if the blue light is on, check iwconfig to see if any devices are available.

**I typed this before I saw that you got it working.  I'm glad that worked!**

---

### Post by atararx on 2007-06-18
I didn't know that there existed any dv6000 beyond the 6000z (amd) and 6000t (intel).

I just knew that I wanted an hp pavilion laptop. I went to their website, saw the 6000z and knew that it was the one I wanted. (well I did look at some others but they failed in comparison with the 6000z for one reason or the other)

I got a pretty good deal on it though. $750 with taxes (I got student  discount for it).


Thanks once again for your help.

---

