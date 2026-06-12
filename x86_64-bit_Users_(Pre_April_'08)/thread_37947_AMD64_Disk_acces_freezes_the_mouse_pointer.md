---
title: "AMD64 Disk acces freezes the mouse pointer"
date: 2005-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by ricardo06 on 2005-05-29
Hello,
ijust installed the ubuntu 5.04 On my new H/W
AMD athlon 64 3500+ 
Mother board is a TUL XPRESS 200P 

I am surprisedd ti see that disks acces completely freezes th mousse motion making it almost impossible to work when downloading to HD or doing any heavy disk acces. Curently downloading at 100kB/s is very hard whille on my old K6 450 Mz it is almoste unoticed.
I think it it has something to do with DMA access ??

Thanks for helping.

Ubuntu looks great. I am currently downloading Kubuntu....


Richard

---

### Post by FluffyElmo on 2005-05-29
I haven't seen anything like this myself, are you using SATA or IDE drives?

For DMA, try hdparm to check the settings. For instance if your drive is */dev/hda*, then *sudo hdparm /dev/hda* will show your current settings. *sudo hdparm -d1 /dev/hda* will enable DMA. 

hdparm generally doesn't work with SATA drives though, search this forum for more on that if you are using SATA.

---

### Post by ricardo06 on 2005-05-29
Thanks for your reply. Below is what I get. 
I suppose the only way to check IDE/SATA is to open the box and check the connectors ?


[COLOR=Blue]/opt# sudo hdparm /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 20023/255/63, sectors = 164696555520, start = 0
root@ricardo:/opt# sudo hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
[/COLOR]

As you can see dma is OFF and setting it 'On' is rejected.

I'll do more investigations.

Richard

---

### Post by FluffyElmo on 2005-05-29
If it's showing up as /dev/hda then it probably IDE. My SATA drive shows up as /dev/sda.

Two thoughts you might want to investigate, first check your BIOS settings to make sure they are picking up the drive correctly and have DMA and 32bit access enabled.

Second, what modules are listed in */etc/modules* (*sudo gedit /etc/modules* to edit). Your board uses an ATI chipset (ATI RADEON® XPRESS 200P), which I am not familiar with. However I use a VIA chipset and had to add a line for it (via82cxxx) explicitly at the top of the list before the ide_generic entry to enable full support for my drives.

You may have to do the same for your chipset. It may be worth a search to see if others are using 64bit Linux with this chipset successfully. ATI also has a Linux x64 driver for this board but it may only be for the integrated graphics portion. May still be worth investigating.

---

### Post by ricardo06 on 2005-05-29
I looked into the BIOS and it shows :
Vendor : HDS722516LAT80
SIze : 164.7 GB
LBA Mode; Enabled
Block mode : 16 sectors
PIO Mode : 4
ASYNC DMA : MultiWordDMA-2
Ultra DMA : Ultra DMA-5
S.M.A.R.T : Supported

The SATA section says : Disabled.

And the :/etc/modules 

[COLOR=Blue]# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
rtc
sbp2
sr_mod

[/COLOR]

So it it is consistent. I suppose there is a list of modules somewhere in the system and i will have a look at it.

I have posted a questions on a forum about a succesfull installation of X86_ on this board. But still nothing. 
I am relatively new to facing that kind of problem. 

So your help is really helpfull

Richard

---

### Post by FluffyElmo on 2005-05-29
Your BIOS settings look fine. I'd say it's a problem with chipset support. My /etc/modules (bottom) looks almost the same as yours but with my chipset specific module at the top. If I remove the top line I end up in the same situation you're in.
 
Try installing the ATI x64 driver for the Xpress 200P here, it may have support for the disk controller as well as graphics. 
[https://support.ati.com/ics/support/KBList.asp?folderID=1016](https://support.ati.com/ics/support/KBList.asp?folderID=1016)

Edit: Sorry, the link doesn't seem to work! Go to: [http://support.ati.com](http://support.ati.com) and navigate to: ATI Customer Care > Drivers and Software > Linux > Linux x86_64 > Motherboards with ATI Graphics >

If that doesn't work you may want to drop a note to ATI support. They do claim Linux support for this chipset: "Support for Microsoft® Windows® XP, Windows® 2000, and Linux" so they may be able to help.
[http://www.ati.com/products/radeonxpress200p/specs.html](http://www.ati.com/products/radeonxpress200p/specs.html)

Good Luck, having been in this situation before I know how frustrating this can be  :(

/etc/modules:
```
via82cxxx
sr_mod
psmouse
mousedev
rtc
ide-cd
ide-disk
ide-generic
sbp2
lp
```

---

### Post by ::DoGG:: on 2005-05-29
try pass the ide-disk dma=1 option while loading ide-disk module, that helped me .

---

### Post by rsw on 2005-05-29
the ati xpress 200 chipset is not recommended for use with linux. I suspect their ide module is going to be about as terrible as their fglrx-embarrasment....

---

### Post by NickB on 2005-05-29
The atiixp module did the trick for me.

Nick

---

### Post by ricardo06 on 2005-05-31
Hello all,

Thanks for your help I have tried what you kindly suggested but still Nothing. The info that i have gathered so far is that the chipset (ati sb400) is problematic and most probably no yet fully supported by any Linux distro. 
I have posted questions to the linux-ide  organisation and other forums like kerneltrap.org and i hope i can some day tell you all that its solved.
Richard

---

### Post by NickB on 2005-06-02
You need at least 2.6.11.  atiixp in previous kernels does not work.

HTH,
Nick

---

### Post by tseliot on 2005-06-04
[QUOTE=NickB]You need at least 2.6.11.  atiixp in previous kernels does not work.

HTH,
Nick[/QUOTE]

Hi, I've got the same problem as Ricardo06 (and the same motherboard chip as well).

What's this "atiixp" you're talking about? And how did it solve your problem?

---

### Post by NickB on 2005-06-04
atiixp is the ide driver for the ATI chipset.  It's not in the kernel Documentation tree yet, but it seems to work well enough for me (as of 2.6.11).

Nick

---

### Post by tseliot on 2005-06-04
Thanks for the answer. By the way I've installed i386 2.6.11 kernel (k7 version doesn't work on my AMD 64 3500+) and I solved the problem, the mouse cursor doesn't freeze any more.

There's one more annoying problem. The entire system freezes randomly now. Maybe if I installed the patch for the kernel I would solve the problem. Or should I just install Ubuntu 64bit?

What do you think?

---

### Post by tseliot on 2005-06-04
The main problem was that Ubuntu (even with kernel 2.6.11 in gnome system monitor) recognises only 800MB of Ram out of my 2GB. Would the patch I find in synaptic fix it?

---

### Post by FluffyElmo on 2005-06-04
EDIT: Sorry! Just noticed that you were running Ubuntu32 (k7 should have tipped me off;))...so the following probably wasn't much help.

I've read elsewhere that the generic Ubuntu amd64 kernel has problems with more than 900mb of RAM. The k8 kernel doesn't have this problem and should work with your system (k7~=Athlon32, k8=Athlon64).

However my k8 kernel is currently at version 2.6.10, so if you need 2.6.11 then you may have to rebuild the kernel? I'd try the k8 kernel in Synaptic first though to see how it works for you.

---

### Post by tseliot on 2005-06-04
I can't find any k8 kernel (multiverse repositories are enabled). What's the link?

---

### Post by FluffyElmo on 2005-06-04
The k8 kernel is in the 64bit repositories. Sorry, I didn't realize you were running 32bit.

---

### Post by tseliot on 2005-06-04
I'm downloading UBUNTU for AMD 64. I should install it and then put the k8 kernel with synaptic. Is that right? Would this fix the problem? 

And which kernel version?

I'm asking this just because I've already installed several distros 20 times this week.

---

### Post by FluffyElmo on 2005-06-04
I'm not sure if it will work, you have a very new chipset which may not be all that well supported. But if you're installing distros  :?... 

I'd try installing, updating your generic kernel to the newest version and then the atiixp module. If you experience lock-ups then try the latest k8 kernel. If you want a 2.6.11+ k8 kernel though, you may have to try the Breezy repositories.

---

### Post by tseliot on 2005-06-04
Thanks, I'll try. However Mandriva 2005 LE worked (but it disconnected from the Internet after 2 minutes :???: ).

By the way I tried Xandros, Ubuntu, Kubuntu, Fedora core 3, Mandriva, and, except for Mandriva, the mouse pointer freezed very often. The system hangs only in Ubuntu when I use it with 2.6.11 kernel. 

I'll make you know if K8 kernel solves every problem.

---

### Post by tseliot on 2005-06-04
Ok, I've installed Ubuntu 64bit and 2.6.12 kernel for K8(with breezy repositories). It runs fast, it doesn't hang but when I access my CD-reader (both of them) and try to copy something to my harddisk the pointer slows down.

I could try atiixp but I don't know where to download it. Can you help me please?

---

### Post by nandhu on 2005-06-06
[QUOTE=ricardo06]Hello all,

Thanks for your help I have tried what you kindly suggested but still Nothing. The info that i have gathered so far is that the chipset (ati sb400) is problematic and most probably no yet fully supported by any Linux distro. 
I have posted questions to the linux-ide  organisation and other forums like kerneltrap.org and i hope i can some day tell you all that its solved.
Richard[/QUOTE]

Hi, 

I've got the similar problem. Though I've not tried. I just found out (literaly couple of hours before), that there is an ATI Driver for X200 series.
Go to this link. Who knows it might be of help. If it works for you, please post a line here and so we can also be benefitted. 

[http://support.ati.com/ics/support/...ticketID=822344](http://support.ati.com/ics/support/...ticketID=822344)

Hope this helps. If not let me know, i can email you the driver.

---

### Post by NickB on 2005-06-06
[QUOTE=tseliot]I could try atiixp but I don't know where to download it. Can you help me please?[/QUOTE]
If you're using 2.6.12, then chances are it got automatically loaded at boot.  See dmesg.

Nick

---

### Post by FluffyElmo on 2005-06-06
tseliot: Glad to hear that everything is (almost!) working. Ubuntu doesn't enable DMA on removable disks by default, and this is probably causing your last problem. 

For example, if your CD/DVD was /dev/hdc, *sudo hdparm /dev/hdc* will show your current settings and you can enable dma with: *sudo hdparm -d1 /dev/hdc*. 

Hope this helps...

---

### Post by tseliot on 2005-06-07
For Nandhu: the link didn't work but I managed to find two drivers:

ATI Proprietary Linux x86_64 Driver for XFree86 / X.Org Version 8.12.10
and
ATI Proprietary Linux x86_64 Driver 8.13.3 for Radeon Xpress 200 Series

I can try both of them. Thanks, I'll write the results.


For everyone: System monitor says it's using 50% of my CPU even if I'm not doing anything, without any application running. 

What's the problem?

Moreover my download speed is half of that I have on XP.

---

### Post by FluffyElmo on 2005-06-07
What processes are using the CPU? System monitor has a processes tab that can be sorted by cpu %, or you can just use top.

---

### Post by tseliot on 2005-06-08
At first the process sucking up all my CPU was gam_server. Then I updated it to 1.0 (from Breezy's repositories) and gam_server didn't use my CPU any more. However there's something (which is not shown in System monitor that takes about 50-56% of my CPU. I don't know what to do.

---

### Post by FluffyElmo on 2005-06-08
Odd, I've never experienced that so am probably out of my depth. Maybe try running the system monitor as root (*sudo gnome-system-monitor*) to see if any other processes show up?

I might think it was power saving related (*powernowd*) but if that was the case you wouldn't see 50% CPU usage, your CPU would just be clocked low.

---

### Post by NickB on 2005-06-08
My clock was running at 2x the normal speed, which accounts for a lot of strange things, including the CPU monitor showing a baseline of 50% usage.  Upgrade to 2.6.12, and put no_timer_check as a bootparam.

Nick

---

### Post by tseliot on 2005-06-08
I've looked for bootparam in google but I can't find anything useful. Could you explain me how to do what you said with bootparam, please? 

I'm sorry if I'm always asking you (all of you) questions but I have used linux for few months (and I'm studying for many exams in this period).

Thanks for your patience

---

### Post by NickB on 2005-06-08
The best way is to edit /boot/grub/menu.lst and look for these lines:

```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro console=tty0 no_timer_check vga=791
```

The kopt line is what you're interested in.  Just add no_timer_check to the end and run update-grub (as root, of course).

Nick

---

### Post by tseliot on 2005-06-09
Thanks, this worked like a charm!

I also noticed that all the lines in my hdparm begin with #. So I think they are disabled. I'll have to write from a scratch. Otherwise all the transfers from Cd-reader will continue to be slow (and to freeze my mouse pointer)

If you could post your hdparm.conf so I could use it as a model for mine in order not to bother you with my questions any more... at least for a while   :smile: 

Thanks in advance.

---

### Post by NickB on 2005-06-09
I only added to mine:

/dev/cdrom {
        dma = on
        interrupt_unmask = on
        io32_support = 0
}

You could do something similar for /dev/dvd or /dev/hdc or whatever your drive is.

Nick

---

### Post by tseliot on 2005-06-11
This doesn't seem to work on my PC  ](*,) 

The whole system slows down during files tranfer from my cdreaders.

---

### Post by tseliot on 2005-06-12
I've noticed that if I use the command "hdparm -d1" I can enable DMA on my Cdreader and it solves the problem. However when I restart my computer it returns to default settings and I have to launch the command again.

Is there a way to make it remember the settings (hdparm.conf doesn't seem to work)?

---

### Post by NickB on 2005-06-12
/etc/hdparm.conf is the only way I know to initialize the settings at boot other than rolling your own script.  There should be a link in /etc/rcS.d/S07hdparm to /etc/init.d/hdparm, so it gets initialized even if you're booting to single user mode.

Check the syntax of your /etc/hdparm.conf file and make sure you don't have anything that might not parse correctly.  If you're having trouble with the /etc/hdparm.conf syntax, you could aways try moving aside the current file and make a new one with only the following lines:

```
command_line {
       hdparm -q -d1 <device name>
}
```
Good luck,
Nick

---

### Post by ricardo06 on 2005-06-12
Hello all,

I have a solution for the xpress200P mobo (ATI chipsets) + slow disk acces. I downloaded and installed kernel 2.6.11.1 from ubuntu universe repositoriy. dma now WORKS on both ide hdd anf cdrom.
I am not sure the distribution will be 100% operational because the modules are still in 2.6.10.5 but i can use my machine in a very comfortable way.

Now i tried to read a video from a dvd and... didn't work at all

hopefully there is an ubuntu release with 2.6.11 to come soon.  


Richard

---

### Post by tseliot on 2005-06-17
Thanks for the help. I'll find a way to make it work, and eventually I'll post it.

Thanks again

---

