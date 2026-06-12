---
title: "Installing Ubuntu with 4GB of RAM"
date: 2007-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by ynv on 2007-03-04
Hey all,
I'm newbie to this forum, however have experience with Ubuntu. 

I have recently bought a new computer with the following spec:
Inter Core2 Due e6600 (Conroe)
Asus P5B (775, Intel P965, DDRII 800....)
4 (identical) RAM sticks, each TwinMOS DDRII 800Mhz 1GB TwiSTER

Anyway, to my point.....
4GB of RAM for desktops is not as easy to install as I thought.

When I disable the memory remap at my BIOS, both my BIOS, the Ubuntu 32bit, and the Ubuntu 64bit, identify 3008MB, which is reseanable...(since the higher 1GB stick is overridden by my other devices).
However, when I have set the memory remapping at the BIOS, the BOIS identify all 4096MB but the 32bit and 64bit only recognize 2GB of my RAM.
For the 32bit, it might be reasonable since probably the BIOS remap the 2 higher GB of address to 4GB...6GB, and the processor probably cannot get there. (I have even tried to compile the 32bit kernel with the "extended memory ... 64GB" flag, but still no good).

At first I thought that it might be an hardware issue. 
I have tried memtest for few huors, and all seems fine.
I have also updated my BIOS to the most recent available (ver. 1102).
I have tried all most any distribution that I could think of (32bit and 64bit).
Until..., I have tried Gentoo 64bit which is the only one that has recognized 3.8GB...
(I think Fedore Core 6 had also been successful, but it has some other problem with my spec)

Sorry for being a cry baby, But I don't want Gentoo 64bit.... I love my Ubuntu 32bit and for the sake of 4GB (or 3.8GB) of RAM I'm willing to compromise for Ubuntu 64bit (I can also compromise on Xubuntu 64bit too - which is the one I'm trying now).

Please... help......

ynv.

---

### Post by ynv on 2007-03-04
maybe I should also add that when I boot to Ubuntu 64bit with the usual default Grub parameters, the kernel freezes at:
[COLOR="Red"] * Starting kernel event manager...
........
[   53.691604] Modules linked in: ...... [some modules]
freeze[/COLOR]

only when I add to grub kernel paramenters "mem=4096M", Ubuntu is successfuly initiated (with 2GB RAM....)

(and Xubuntu 64bit was not successful too)

anyone...?
help......

ynv.

---

### Post by jms1989 on 2007-03-04
Maby I can help here. It's not a software problem, it has something to do with the motherboard, the PCI cards, and the momory banks.

I attached a chart of the "Recommended memory configurations" for the ASUS motherboards. I use ASUS P4R800-V Deluxe motherboard, if that helps. (The chart came from the user guide; pg. 2-11.)
 
-- jms1989

---

### Post by ynv on 2007-03-05
Thanks for the replay jms1989.
At first, as I described, I too thought it was a hardware issue. However, after playing with it a bit, reading the manual, testing the memory, and seeing that all of the memory is identified by the BIOS, there is no reason why Ubuntu should not recognize the memory as well.

The thing that really ended my doubts whether there is an hardware issue or not, was that Gentoo64 did successfully recognized 3.8GB. If Gentoo(Linux)64 can do it, there is no reason why Ubuntu64 shouldn't. (from that point on, there is no reason to touch the hardware, it is definitely software/distribution issue)

Which leads me to my next idea,
Is there (maybe) a way to use the Gentoo64 kernel together with the Ubuntu distribution?
Is it possible or am too babbling?
Are they identical kernels? (identical up to versioning delta)

Or, maybe I could somehow export the Gentoo64 default compiling configuration and use them to recompile Ubuntu64?

Thanks jms1989!
Any help will be appriciated....

---

### Post by John.Michael.Kane on 2007-03-06
I can't understand why this would be as ubuntu64 should be able to address 4gb or more or memory,however. you can try to recompile a kernel with the option for using 4GB or more of memory.

[http://www.ubuntuforums.org/showthread.php?t=56835&highlight=kernel](http://www.ubuntuforums.org/showthread.php?t=56835&highlight=kernel)
[http://www.ubuntuforums.org/showthread.php?t=311158&highlight=kernel](http://www.ubuntuforums.org/showthread.php?t=311158&highlight=kernel)

---

### Post by ynv on 2007-03-06
Thanks SD-Plissken.
I have tried compiling the Ubuntu64 to more closely fit my specs, and it doesn't even have the configuration flag "extended memory...".
This flag was probably removed from the Ubuntu64 configuration options. This is reasonable, if all were fine ](*,) 

Thanks.
Any other suggestions?

---

### Post by joshuapurcell on 2007-03-07
I'm not sure what the problem could be on this other than some BIOS option not set correctly. I remember having to disable one option in the BIOS called 'Memory Hole Remapping' in order for 4GB to show up for me, but after that this is what Feisty herd5 64-bit shows:
```
joshua@desktop:~/downloads$ more /proc/meminfo 
MemTotal:      4052328 kB
MemFree:        398696 kB
Buffers:         28060 kB
Cached:        2710940 kB
SwapCached:          0 kB
Active:        1645844 kB
Inactive:      1435692 kB
SwapTotal:     4194296 kB
SwapFree:      4194296 kB
Dirty:               0 kB
Writeback:           0 kB
AnonPages:      342336 kB
Mapped:          89472 kB
Slab:           530900 kB
SReclaimable:   495272 kB
SUnreclaim:      35628 kB
PageTables:      13944 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   6220460 kB
Committed_AS:  1123948 kB
VmallocTotal: 34359738367 kB
VmallocUsed:     52544 kB
VmallocChunk: 34359685115 kB
```

We have very different motherboards and different CPUs, but this shows that the default configuration of the Feisty 64-bit kernel should see 4GB if the BIOS is configured properly. Here's a link to a thread I made on another forum which has some posts regarding 4GB of memory in Ubuntu (both 32-bit and 64-bit):
[http://www.phoronix.net/forums/showthread.php?t=567](http://www.phoronix.net/forums/showthread.php?t=567)

Here's some comparisons on how much memory different operating systems see on my hardware:
Feisty 64-bit: 4052328K
Edgy 64-bit: 4047512K
Edgy 32-bit: 3369216K
WinXP 32-bit: 3406252K

I may update my signature to include hardware information since nearly every post I make is related to hardware configuration, but here is my sig from another forum for now:

[size=1]**Ubuntu Feisty Herd5 64-bit on DFI LanParty UT nF590 SLI-M2R/G**
**[color=#D23800]CPU:[/color]**AMD Athlon64 X2 5200+ Windsor 2612MHz | **[color=#D23800]Cooler:[/color]**Zalman CNPS9500 AM2 | **[color=#D23800]RAM:[/color]**4x 1GB OCZ Gold PC2 8000
**[color=#D23800]Video:[/color]**1x eVGA 8800GTS 500MHz 640MB | **[color=#D23800]Display:[/color]**Acer AL2423Wdr 24" Widescreen | **[color=#D23800]Sound:[/color]**Chaintech AV-710
**[color=#D23800]Disk:[/color]**2x Seagate Barracuda 7200.10 320GB SATA 3Gb/s | **[color=#D23800]PSU:[/color]**Antec True Power Trio 650W | **[color=#D23800]Case:[/color]**Antec P180[/size]

---

### Post by shirsch on 2007-03-07
I'm pulling my hair out over this exact issue.  I have an ASUS P5B Deluxe with 4GB of memory (2x2GB) and a Conroe 6600 2.4GHz CoreDuo.

Edgy x86_64 kernel boots and runs with remapping disabled, but is wasting approx. $145.00 worth of DDR2 memory.  With remapping enabled, it hangs at the same place every time.  Tried fiddling with various iommu and swiotlb flags, which changes the freeze to some interesting panics.

Before throwing the motherboard out the window, is there any hope that a newer kernel would work?

---

### Post by ynv on 2007-03-07
Hey shirsch,
(sorrily for you) its nice to know that there is someone in my club.
Few suggestion from what I have learned so far.
try booting grub with "mem=4096M" so it will recognize the exact amount of memory you have.
Ubuntu will then boot OK, but probably will recognize only 2GB of RAM (at least to get things going).

joshuapurcell, thanks for the help,
I have few suspect as far as the BIOS configuration.
The first one is "Memory remapping" which probably should be enabled (but in order to work with at least 3GB, it is currently disabled).
The second suspect which I'm not sure for is "Plug and Play O/S".
According to the documentation, "yes" will let the os plug and play devices (and probably allocate addresses).
Currently I have set it to "yes", but I'm not sure what is its effect (if it effects at all).
It is obviously a distribution issue which cannot identify something in the hardware.

I have just tried upgrading to feisty. The system is thrown at boot time. I can see from the error call stack that it has something to do with ide setup for some pci device. I have read somewhere that edgy had some issue with the jMicron chip (on the Asus motherboard). The fix probably wasn't ported right to feisy. But still from the Built-in prompt (BusyBox) I can see that it only identifies 2GB of RAM (/proc/meminfo).

Help, anyone...

---

### Post by devnu11 on 2007-03-07
I feel your pain!  I have been attempting to install Edgy and Feisty on a P5B and have reached the same error's which you have.  I made a post about my similar setup a few minutes ago.  I haven't tried Gentoo yet but Debian installed nicely.  It's becoming more difficult to find a setup which is not 64 bit.  Unfortunately 64bit is currently the way pc's are going.  I would think 64 bit would be more of a priority given the hardware being sold.  I saw there were some problems with Edgy and core2duo 965 chipsets but I figured a month or so and that would be remedied.  It's getting to the point where if I could find a mobo which would take my memory (picked out mine from Asus specs) and a few users have been able to successfully install Edgy, I would Ebay the P5B.  I have come to enjoy Ubuntu quite a lot and would like to stay with it.

---

### Post by ynv on 2007-03-08
Thanks for the support devnu11, I see that my club is starting to grow.

OK,
I have successfully installed Feisty64.
The problem was with the JMicron chip which is a (very) known issue and there are many bug reports for that issue. After disabling it, still ubuntu still cannot find my RAM.

However, I did find some interesting.
After playing a bit with the BIOS and trying configure the SATA as "AHCI" and not as "IDE" (I have no clue what "AHCI" says) ubuntu hangs at the end of booting trying to launch my X server. I think it hangs while having a problem detecting my mouse. When breaking from the X server setup it gives me an error in X server launch and gives me a simple tty.
The interesting thing is that in that skinny booting the "more /proc/meminfo" shows 3.8GB!
How can I boot ubuntu without starting an X server?

any other suggestion.... anyone....

---

### Post by shirsch on 2007-03-08
Ok, found some real valuable information on the web:

[http://myweb.facstaff.wwu.edu/~riedesg/sysadmin1138/2006/12/opensuse-102-on-asus-p5b-deluxe.html](http://myweb.facstaff.wwu.edu/~riedesg/sysadmin1138/2006/12/opensuse-102-on-asus-p5b-deluxe.html)

The real magic bullet was blacklisting intel_agp.  In short, the P965 chipset is being incorrectly identified as G965 (with video) and the intel agp gart driver blows up with PCI remapping engaged.  After I added it to the blacklist, Edgy booted up without incident and sees all 4GB!

The issues with the Jmicron chipset seem to come and go with kernel revisions.  For whatever reason (luck?), the 2.6.17-11-generic kernel can properly deal with it  - and with the networking.

More to come as I fight my way through...

---

### Post by ynv on 2007-03-09
It (partially) worked!!!!\\:D/ \\:D/ \\:D/ \\:D/ 
shirsch your a guineas!

to sum it all up:
1. add to /etc/modprobe.d/blacklist a line 'blacklist intel_agp'
2. reboot
3. In the 'BIOS -> MAIN -> IDE Configuration' configure the 'SATA Configuration' to Enhanced, and 'Configure SATA as' to IDE.
4. In the 'BIOS -> Advanced -> Onboard Devices Configuration' I have disabled the 'JMicron SATA/PATA Controller'
5. And of course enable the 'Memory Remap Feature' at 'BIOS -> Advanced -> Chipset -> North Bridge Configuration'
6. boot...
This will identify 3.8GB of RAM!!! [-o< [-o< 

As for step 4:
This is still an issue...I have tried all possible configurations, and it still doesn't work, probebly the driver intel_agp was supposed to fix it, but now this driver is at the blacklist...
The good news are that this is at much lower priory for me for now, since other computers at my network can handle DVD burnning and reading for now.

THANKS shirsch!!!!  [-o< [-o<

---

### Post by shirsch on 2007-03-09
Genius?  Hardly... Just bloody-minded about searching Google.

What version of Ubuntu are you trying to use?  What kernel?  I didn't have to make any of the changes to the Jmicron controller.  My DVD drive "just worked".  One difference is that my disks are on a 3ware RAID controller, so I'm not using any of the built-in SATA features.

The intel_agp driver is for use with Intel graphic chipsets.  It has nothing to do with the drive controller.  I was able to install the proprietary Nvidia driver and it works just fine without the blacklisted driver (does anyone know if the AGP GART support is required on PCI-E motherboards? I suspect it is not).

From reading posts on the net, I get the impression that Jmicron support has come and gone over several kernel versions.  Perhaps the stock 2.6.17-11-generic is one where it's not broken?  To add to the mystery, several folks have reported serious problems with the on-board ethernet, but it's working perfectly for me.  Odd.

---

### Post by ynv on 2007-03-09
I think they need to add Googling to the IQ tests.

My DVD is connected to the motherboard, so it probably is depending on the JMicron.
After shifting versions to find out what the problems are, I gave a try to Ubuntu Feisty 7.04 (kernel 2.6.20-9-generic), and sticked with it.
Probably feisty has something to do with the failed support to JMicron, but I prefer to wait for fixes for that.
And the on-board ethernet is working perfectly for me too...

Thanks anyway...

---

### Post by shirsch on 2007-03-09
The kernel you're running is one of the ones reported to have problems with the Jmicron controller.  I have a PATA DVD drive connected to the motherboard on my box.   The Feisty install CD does not see it.  Edgy does, as does Fedora 6.

I think the kernel developers understand all the issues, so I imagine later 2.6.20x and 2.6.21 kernels will work out-of-the-box.  This is what we get for being "bleeding edge" :) 

I do have to say that this box (E6600 Core Duo + 4GB of memory + 3ware RAID controller w/ 3x SATA II drives) really screams!

---

### Post by rsgooch on 2007-03-09
I have this board and after looking at all your problems and solutions I have managed to get Ubuntu Edgy 64 bit install and recognized 4GB of ram.  I ran the install on a cd running on the jmicron controller.  The key is to download the 64bit Alternative iso it has support for the jmicron controller and the install ran fine from there.  I did have the problem of the  system hanging at boot but as the previous posters noted by adding the "blacklist intel_agp" to the /etc/modprobe.d/blacklist file this is resolved. So the steps I took were:

1. download the Alternative 64bit install iso and burn to a disk I found this in the get Ubuntu when you select a mirror there is an option for "Other installation options" you will find the 64 bit alternative iso there.

2. Set the BIOS 'Memory Remap Feature' at 'BIOS -> Advanced -> Chipset -> North Bridge Configuration to "enabled"

3. Boot from the cd and follow the normal install steps, however when prompted to remove the disk and reboot.  press ALT+F2 this will open a new terminal window. press any key to get a prompt.

4 find the root by typing "df" top show you all mounted partitons mine was llisted as /target.  type "nano /target/etc/modprobe.d/blacklist"  to edit the blacklist and add "blacklist intel_agp" to the end of the file and CTRL+X to exit and press Y to save changes .  

5. press ALT+F1 to get back to the install screen and reboot your computer. 

You should now have a your Asus P5B running with 64bit Ubuntu.  I would like to thank:
YNV, and shirsch for their input which help me solve the hanging at boot problem.  

As a side note: I have a winmodem installed in my pc and the install hung at WVDIAL it appears that this is a known problem and by pressing ALT+F2 and going to a terminal I was able to kill the wvdialconf process and continue on with the install

Later,
rsgooch

---

### Post by shirsch on 2007-03-10
What's so odd is that I've had no problems at all booting the Edgy installer - no need for newer JMicron drivers.  One possible difference is that the only block device attached to the motherboard is a Sony PATA DVD.  The disks are all attached to a 3ware 96504LP RAID controller.

---

### Post by raidensix on 2007-03-14
I tried the blacklist and the memory remap but every time I add the other 2GB is hangs during boot. The Ubuntu spash screen will show for a bit then goes to a blank screen with the cursor on the upper left. I'm using an Asus P5B-VM with a Core 2 Duo 6400. Does the 4GB have to be there when installing or can it be added later on?

---

### Post by raidensix on 2007-03-15
Turns out that it's just extremely slow in booting. I get this error after some time in the blank screen:

hda_intel: azx_get_response timeout, switching to single_cmd mode

and the system eventually boots after about 10 mins. Even then, when I log in (which again takes minutes to get the desktop display), the system is very sluggish. Everything takes minutes to start up and the CPU utilization runs high (>60%). Anyone ever encounter this ?

---

### Post by shirsch on 2007-03-15
What happens if you edit the boot command line to show the detailed progress?  Change 'quiet splash' to 'noquiet'.  This will at least show you what it's trying to do when it hangs up.

Also, sorry if this is obvious, but you _did_ rebuild the initram image after blacklisting intel_agp, correct?  And, to be clear, this is an installed system that otherwise works correctly?

I'm continuing to have good success with my box.  One oddity, though.  The built-in speedstep management just cannot get things right.  I had to go into the BIOS and disable speedstep completely to get both cores running at full clip.

---

### Post by raidensix on 2007-03-15
I  re-installed the OS and followed what rsgooch did. System is fine with 2GB. Do I need to rebuild the kernel ?

---

### Post by shirsch on 2007-03-16
I doubt you need to rebuild the kernel, just the initramfs image.  I could probably be of more help if you answered the questions in my last message.

---

### Post by raidensix on 2007-03-16
I've rebuilt the initramfs but it had the same behavior. Anyway, this is a working system that works fine unless I add in the other 2 GB. I have tried the noquiet boot and from what I can tell (aside from the azx_get_response timeout), it's just slow in loading/doing everything.

---

### Post by galileux on 2007-04-26
Hi all
Fairly new to Ubuntu and also to this forum.
However here is my experience:

My setup is similar to the toubled ones:

SETUP
- Intel dual core Conroe e6600
- Asus P5B (plain)
- 4 GB of RAM

PROCEDURE
- Used Feisty "ubuntu-7.04-alternate-amd64.iso" CD
- Had to use the CD boot option "agp=off" to be able to install from the CD (it hung up otherwise).
- Initially disabled the BIOS northbridge expansion, after install, to get into feisty (no boot otherwise).
- Added the famous "blacklist intel_agp" line to the "/etc/modprobe.d/blacklist" file (had trouble finding this file, in some posts the path and filename were different).
- Re-enabled the north bridge expansion in the BIOS.

RESULTS
Feisty now boots and sees 3.8 GB under System>Administration>System Monitor>System
Network seems ok.
Not tested the onboard sound yet.

My question: is it OK to see 3.8 GB and not 4 in the system properties?
Any suggestions to further optimize the system at these early stages of installation?

Thanks
Galileux

---

### Post by shirsch on 2007-04-26
> **galileux said:**
> 
PROCEDURE
- Used Feisty "ubuntu-7.04-alternate-amd64.iso" CD
- Had to use the CD boot option "agp=off" to be able to install from the    CD (it hung up otherwise).


Nice tip on the agp=off setting!  I ended up doing a text-mode install due to the hang.  I sure wish the kernel folks would fix the Intel chipset support.  Underlying problem is that it thinks all P965 chipsets have a graphics capability and tries to load the agpgart support.

> RESULTS
Feisty now boots and sees 3.8 GB under System>Administration>System Monitor>System

My question: is it OK to see 3.8 GB and not 4 in the system properties?


I just checked and my box reports 3.84GB.  Probably some of the address space is being used for device IO.  Never noticed that before.

---

### Post by joshuapurcell on 2007-04-26
The whole reason I moved from 32-bit to 64-bit was because I was getting a memory total of something less than 4GB. See my post above for specific details on what memory totals I had under different OSes.

I think it's odd that not at least 99% of the 4GB of memory shows up in a 64-bit OS. Did you check if the BIOS option labeled **Memory Hole Remapping** is available, and if so then if it increases the amount of memory available in the OS when changed?

---

### Post by jespdj on 2007-04-27
Is this problem something that only happens when you have 4 GB RAM?

I have a Core 2 Duo E6600 on an Asus P5B Deluxe (Intel P965) with 2 GB RAM and my DVD drive on the JMicron controller and Feisty-64 just works, no need for special kernel parameters.

I'm not at my PC right now so I can't check if it's falsely detecting AGP.

Ubuntu 6.06 (Dapper) doesn't work on this system because of a kernel bug (it doesn't recognise the JMicron controller). (I don't remember if 6.10 (Edgy) worked or not...).

---

### Post by galileux on 2007-04-27
> **joshuapurcell said:**
> The whole reason I moved from 32-bit to 64-bit was because I was getting a memory total of something less than 4GB. See my post above for specific details on what memory totals I had under different OSes.

I think it's odd that not at least 99% of the 4GB of memory shows up in a 64-bit OS. Did you check if the BIOS option labeled **Memory Hole Remapping** is available, and if so then if it increases the amount of memory available in the OS when changed?

I will check that BIOS option at next reboot :-)
Meanwhile, here is a piece of my output from meminfo for feisty 64-bit

galileux@Europa:~$ more /proc/meminfo
MemTotal:      4031024 kB
MemFree:       3337708 kB

Joshua, what value do you get if you go under

System>Administration>System Monitor>System    ?

(Further to my previous post: Onboard sound is loud and clear  on the P5B board)

---

### Post by shirsch on 2007-04-27
> **jespdj said:**
> Is this problem something that only happens when you have 4 GB RAM?


Yes.  Although those of us seeing issues have additionally enabled memory hole remapping, I'm not sure that would affect matters with 2GB installed.

> 
I have a Core 2 Duo E6600 on an Asus P5B Deluxe (Intel P965) with 2 GB RAM and my DVD drive on the JMicron controller and Feisty-64 just works, no need for special kernel parameters.


See above.  Doubtful that you'd see the problems we're discussing.

> 
I'm not at my PC right now so I can't check if it's falsely detecting AGP.


With no real memory between 2GB and the 4GB line, it wouldn't matter if it did.  

> 
Ubuntu 6.06 (Dapper) doesn't work on this system because of a kernel bug (it doesn't recognise the JMicron controller). (I don't remember if 6.10 (Edgy) worked or not...).

Edgy required an ugly workaround.  Something about BIOS options and boot options (I never tried it myself).

---

### Post by shirsch on 2007-04-27
> **galileux said:**
> 

Meanwhile, here is a piece of my output from meminfo for feisty 64-bit

galileux@Europa:~$ more /proc/meminfo
MemTotal:      4031024 kB
MemFree:       3337708 kB


That's essentially what I get as well:

hirsch@duo:~$ more /proc/meminfo
MemTotal:      4030960 kB

> 
(Further to my previous post: Onboard sound is loud and clear  on the P5B board)

Give thanks for small favors :-).

---

### Post by joshuapurcell on 2007-04-29
> **galileux said:**
> I will check that BIOS option at next reboot :-)
Meanwhile, here is a piece of my output from meminfo for feisty 64-bit

galileux@Europa:~$ more /proc/meminfo
MemTotal:      4031024 kB
MemFree:       3337708 kB

Joshua, what value do you get if you go under

System>Administration>System Monitor>System    ?

(Further to my previous post: Onboard sound is loud and clear  on the P5B board)

I'll find out when I'm back by my computer later today.

---

### Post by joshuapurcell on 2007-04-29
> **galileux said:**
> Joshua, what value do you get if you go under

System>Administration>System Monitor>System    ?

Memory shows 3.9 GB on the System tab of the System Monitor, which is the same as the amount given in /proc/meminfo (4052284 kB).

---

### Post by galileux on 2007-04-29
Thanks Joshua, well I think that's essentially it.
We are getting our (almost) 4 GB addressed on feisty.
It was a bit troublesome, but I'm glad I didn't have to go buy an Intel MB to get it done.
Cheers

---

### Post by sonnet on 2007-05-11
HiI read all the post but I didnt understand if anyone was able to make recognize the 4gb with the 32bit version.
I want install ubuntu studio that is only 32 bit version for the moment and anyway I prefer to install 32bit os to dont get problem with codecs.
I have an asus p5b deluxe wifi but I disabled the jmicron controller as I dont need it (my optical drives are sata).

---

### Post by shirsch on 2007-05-11
> **sonnet said:**
> HiI read all the post but I didnt understand if anyone was able to make recognize the 4gb with the 32bit version.
I want install ubuntu studio that is only 32 bit version for the moment 

You will never be able to have 4GB of available memory in 32-bit mode.  The maximum physical address space is 4GB and PCI I/O space will typically use 500-600MB of it.  

>  and anyway I prefer to install 32bit os to dont get problem with codecs.

Yes, I hear you on that one.  However, with a little effort you can get all of the multimedia stuff working in 32-bit Firefox/Swiftfox.  Plenty of discussion on this.

---

### Post by jonah1980 on 2007-05-14
hey guys - i wish i'd found this thread before i bought 4gb RAM and upgraded my pc, i figured it would just work!! now i'm  stuck with a non-booting system and i'm in a real mess, don't like playing with bios too much but disabling the s/w remapping and h/w remapping etc will get me a splash screen that hangs, or with them enabled i get nothing.... what do i do? the bios states i have the 4gb memory working, but the x86 memtest thing on grub menu gives  a load of error, though i don't really believe this as the bios mem check says ok...

arrrgh! can anyone please help? is there something i can add to the grub line or anything to fix this?

---

### Post by jonah1980 on 2007-05-14
just managed to boot SimplyMepis livecd no probs, though did boot very slow. and not sure what memory is detected as don't know where to look in mepis/kde

---

### Post by jonah1980 on 2007-05-14
the only way i can boot at the moment is to remove 1x1gb ram dimm out and leave 3 in there and boot without one, which is awful as again i've got expensive memory sat on my desk that i can't use....

---

### Post by psusi on 2007-05-14
> **shirsch said:**
> You will never be able to have 4GB of available memory in 32-bit mode.  The maximum physical address space is 4GB and PCI I/O space will typically use 500-600MB of it.  


This is not correct.  P3 and newer cpus can use 36 bit physical addresses, known as Paging Address Extensions ( PAE ).  Of course, you still are using 32 bit virtual addresses so any given process can only see 4 GB of memory, including the kernel.

---

### Post by jonah1980 on 2007-05-14
hmm ok so i tried putting a 1gb stick in 1 at a time and did a memtest of each one seperately and found a lot of errors on one, so turns out i've got a faulty module.

the weird thing is i can't find any probs with others, and can boot and operate well with two modules in, but when i add a third and leave one slot empty or put one of my old 512mb modules in the empty fourth slot then the system doesn't seem to go long before hanging. so i don't know whether the 3rd module is faulty or if it's just cos you can't have 3 in or 4 in that aren't the same, can anyoone please advise as i don't know whether to try return just one module or two??

---

### Post by shirsch on 2007-05-14
> **psusi said:**
> This is not correct.  P3 and newer cpus can use 36 bit physical addresses, known as Paging Address Extensions ( PAE ).  Of course, you still are using 32 bit virtual addresses so any given process can only see 4 GB of memory, including the kernel.

Does a PAE-enabled 32-bit kernel support running the kernel in a different mapping from user space?  If not, then you'll still loose part of the last 1GB to PCI mapping.

---

### Post by psusi on 2007-05-14
> **jonah1980 said:**
> hmm ok so i tried putting a 1gb stick in 1 at a time and did a memtest of each one seperately and found a lot of errors on one, so turns out i've got a faulty module.

the weird thing is i can't find any probs with others, and can boot and operate well with two modules in, but when i add a third and leave one slot empty or put one of my old 512mb modules in the empty fourth slot then the system doesn't seem to go long before hanging. so i don't know whether the 3rd module is faulty or if it's just cos you can't have 3 in or 4 in that aren't the same, can anyoone please advise as i don't know whether to try return just one module or two??

Did you try plugging in only one module at a time in the same slot, and running memtest?  If that shows errors on one module, then that's the one to return.

---

### Post by psusi on 2007-05-14
> **shirsch said:**
> Does a PAE-enabled 32-bit kernel support running the kernel in a different mapping from user space?  If not, then you'll still loose part of the last 1GB to PCI mapping.

No, the kernel is mapped into all processes, so as I said, an individual process won't be able to use more than 4 gigs, or even that much, but the system as a whole can.

---

### Post by jonah1980 on 2007-05-15
> **psusi said:**
> Did you try plugging in only one module at a time in the same slot, and running memtest?  If that shows errors on one module, then that's the one to return.

yeah i did this and found one to have a problem. but then i still can't seem to use the three that are ok for long without system crashing/hanging, and if i put one of my old 512mb modules in fourth slot it still hangs. so does this mean two are faulty but only one is showing up, or is it cos they're not paired or something... i'm stuck and not sure whether to send one or two back now

---

### Post by psusi on 2007-05-16
Set the one you know is bad aside, and run memtest with the other 3 modules in and see if it finds any problems after a good hour of burn in.

---

### Post by sonnet on 2007-05-18
> **ynv said:**
> It (partially) worked!!!!\\:D/ \\:D/ \\:D/ \\:D/ 
shirsch your a guineas!

to sum it all up:
1. add to /etc/modprobe.d/blacklist a line 'blacklist intel_agp'
2. reboot
3. In the 'BIOS -> MAIN -> IDE Configuration' configure the 'SATA Configuration' to Enhanced, and 'Configure SATA as' to IDE.
4. In the 'BIOS -> Advanced -> Onboard Devices Configuration' I have disabled the 'JMicron SATA/PATA Controller'
5. And of course enable the 'Memory Remap Feature' at 'BIOS -> Advanced -> Chipset -> North Bridge Configuration'
6. boot...
This will identify 3.8GB of RAM!!! [-o< [-o< 

As for step 4:
This is still an issue...I have tried all possible configurations, and it still doesn't work, probebly the driver intel_agp was supposed to fix it, but now this driver is at the blacklist...
The good news are that this is at much lower priory for me for now, since other computers at my network can handle DVD burnning and reading for now.

THANKS shirsch!!!!  [-o< [-o<

Sorry can anyone explain me step by step how "1. add to /etc/modprobe.d/blacklist a line 'blacklist intel_agp'" as said in this post?
If I do this command from shell or terminal I get "no such file or directory " message.

---

### Post by sonnet on 2007-05-19
> **sonnet said:**
> Sorry can anyone explain me step by step how "1. add to /etc/modprobe.d/blacklist a line 'blacklist intel_agp'" as said in this post?
If I do this command from shell or terminal I get "no such file or directory " message.

Hi ,I was able to add to the blacklist intel_agp and now my system see 3.8gb that is quite fine,but the internet connection now doesn't work anymore.
Does anyone know why?

---

### Post by Caboose Natarajan on 2007-05-20
Hello,

I have been anxiously following this thread. Learnt a lot. I am new to this forum. I've been running ubuntu (from dapper) for about 3 years now.

I recently bought a P5B-VM (not plain) with the Intel G965 video chipset. I also have two twin CORSAIR 2x2048 memory sticks. So a total  of 4x1G memory. I really couldn't install Feisty 64-bit (from live or alternate CD) with the memory-remap enabled in BIOS.

After having some trouble, I just pulled 2 sticks out and managed to install Feisty 64-bit from the Live-CD without any problems. I noticed the 'blacklist intel_agp' in this thread but since I had the integrated video Mobo I thought it wouldn't affect me. 

Well, after the install, I put those 2 sticks back and enabled memory-remap. No dice. The system gives the ubuntu splash screen but no login.. It was hung. I didn't wait long enough to see if there was any problems. I noticed on the ASUS forums that there is a problem with their BIOS. There are a bunch of guys complaining out there (even with the updated BIOS). Please see this link: [http://vip.asus.com/forum/view.aspx?id=20070415195930406&board_id=1&model=P5B-VM&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20070415195930406&board_id=1&model=P5B-VM&page=1&SLanguage=en-us)

Without the memory remap enabled Fiesty 64bit runs fine but with only 2.8GB :(. I even bought an alternate video-card and disabled by internal card and blacklisted intel_agp. No luck.

Anyway, my question is to some of you guys who got things working with 4G: Are you guys noticing these problems or is it only in P5B-VM?? Any info. would help. I am kinda bummed out about this MOBO if it is the cause of a lot of my headache!

---

### Post by ememoho on 2007-05-21
I am suffering the same problem.
I have waited 7.04 as this reason.
I heard before that later of kernel 2.6.19 has been patch 965 chipset problem.
fedora 6 below than 2.6.19
ubuntu 6.10 also below than 2.6.19.
but I don't know why 7.04 doesn't work nice. T.T
I'm stare this post.
help us...:(

---

### Post by pwhite on 2007-05-27
I was finally able to get 32-bit Feisty to recognize 4GB (sysinfo reports 4043MiB) of RAM by rebuilding the kernel after setting "High Memory Support" to 64GB instead of 4GB.

My system is configured as follows:

Intel Core 2 Duo E6600
Asus P5B Deluxe WiFi-AP
2 sets of GSkill F2-6400CL5D-2GBNQ RAM for a total of 4GB.

[Edit] I realize the original post was in the "x86 64-bit Users" forum, but I figured I'd post a reply to this thread since some posters were trying to get 4GB working on a 32-bit install.

---

### Post by hksduhksdu on 2007-07-03
Hi Thank you very much for your info.  I have the following hardware:

E6600
Asus P5B-VM DO
4x1GB OCZ rev2 DDR800

Would like to know how do you enable the High Memory Support in kernel? how do you rebuild kernel in Ubuntu?

Thanks in advance,

Andy

> **pwhite said:**
> I was finally able to get 32-bit Feisty to recognize 4GB (sysinfo reports 4043MiB) of RAM by rebuilding the kernel after setting "High Memory Support" to 64GB instead of 4GB.

My system is configured as follows:

Intel Core 2 Duo E6600
Asus P5B Deluxe WiFi-AP
2 sets of GSkill F2-6400CL5D-2GBNQ RAM for a total of 4GB.

[Edit] I realize the original post was in the "x86 64-bit Users" forum, but I figured I'd post a reply to this thread since some posters were trying to get 4GB working on a 32-bit install.

---

### Post by jonah1980 on 2007-07-04
ok i returned my memory and got 4 new sticks which are working ok and all pass memtest without errors. my system seems to work fine now except it will randomly lock up now, i can't reproduce it sometimes it will lock up after an hour or sometimes a day or ten mins! and i can't move the mouse or anything.... is this because i'm using 4gb, the memory appears to be ok...

---

### Post by rwillia2001 on 2007-07-31
Thanks for the blacklist intel_agp posting!! 

This worked perfectly for me:

 "sudo kate  etc/modprobe.d/blacklist" to edit the blacklist and add "blacklist intel_agp" to the end of the file and CTRL+S, exit. Reset the BIOS 'Memory Remap Feature' at 'BIOS -> Advanced -> Chipset -> North Bridge Configuration to "enabled" (it was disabled to boot and make the file edit).

It now recognises the full 4GB or  4030956KB of RAM. This is an ASUS P5B-E, E6600, Kubuntu Fiesty Fawn 7.04 64 bit.CHEERS!

---

### Post by shirsch on 2007-07-31
Glad things worked out!  I'm VERY surprised that the underlying bug has not been fixed in newer kernels.  It needs to discriminate between the Intel 965 chipset versions - one has video built-in and the other doesn't.  Attempts at probing the non-existant video are what cause things to fail.

Hopefully someday the workaround won't be necessary.

---

### Post by hksduhksdu on 2007-08-01
Hi,

So it's gotta be 64bit Feisty? what's the difference between 64bit and 32bit? I have wireless PCI card and I do encoding/decoding stuff, I've heard that 64bit can't do these...is that right?

Andy

---

### Post by John.Michael.Kane on 2007-08-01
> **hksduhksdu said:**
> 

So it's gotta be 64bit Feisty? what's the difference between 64bit and 32bit?



Yes it has to be 64bit if you want to address four or more GB of memory. 

Have a read.
[Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

> **hksduhksdu said:**
> I have wireless PCI card and I do encoding/decoding stuff, I've heard that 64bit can't do these...is that right?
No thats not right. 64bit can do encoding/decoding among other things.

As stated before in many threads. 

> Anything that can be done on 32bit ubuntu can be  accomplished using 64bit ubuntu, and It's not about is it worth installing 64bit or 32bit as neither one is perfect, and they both come with their bag of issues.

What I would suggest you or any other user wanting to try 64bit ubuntu is to use it for thirty days without rebooting into 32bit ubuntu, and make use of the guide made for 64bit.  This will allow you to see for your self if it's worth it or not.  

In the end it's about the end user being willing to solve whatever issue they come across be it on 32bit ubuntu or 64bit ubuntu or any other distro for that matter.

---

### Post by jolig on 2007-09-11
> **shirsch said:**
> Ok, found some real valuable information on the web:

[http://myweb.facstaff.wwu.edu/~riedesg/sysadmin1138/2006/12/opensuse-102-on-asus-p5b-deluxe.html](http://myweb.facstaff.wwu.edu/~riedesg/sysadmin1138/2006/12/opensuse-102-on-asus-p5b-deluxe.html)

The real magic bullet was blacklisting intel_agp.  In short, the P965 chipset is being incorrectly identified as G965 (with video) and the intel agp gart driver blows up with PCI remapping engaged.  After I added it to the blacklist, Edgy booted up without incident and sees all 4GB!

The issues with the Jmicron chipset seem to come and go with kernel revisions.  For whatever reason (luck?), the 2.6.17-11-generic kernel can properly deal with it  - and with the networking.

More to come as I fight my way through...


Hi !

It worked on my Gigabyte 965P-DS4 motherboard.
The system was successfully running with an 6.10 x86_64 ubuntu and 2GB of RAM.
When I added 2 more GB, the system was freezing at startup.
I added the add the line 'blacklist intel_agp' to /etc/modprobe.d/blacklist and it worked again !

Cool, Thanks !!

---

### Post by shirsch on 2007-09-11
Does anyone know if the Intel 965 chipset bug has been corrected for Gusty?  It's persisted across 6.10 and 7.04.  Since it's not particularly a Ubuntu problem, I'm hoping that the kernel developers have updated the Intel AGP driver to properly distinguish between the P965 and G965 chipsets (the underlying cause of the lockups).

---

### Post by Totzo on 2007-09-13
Hi all,

I followed [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=56835") guide

paying particular attention to the "high memory support"

worked a treat

---

### Post by shirsch on 2007-09-13
To the best of my knowledge, the 4 vs. 64GB issue pertains only to the memory model of a 32-bit kernel.  Still, I'm glad you have things working.

---

### Post by Totzo on 2007-09-13
> **shirsch said:**
> To the best of my knowledge, the 4 vs. 64GB issue pertains only to the memory model of a 32-bit kernel.  Still, I'm glad you have things working.

Sorry, I'm totally off topic! Didn't realise this was in the 64-bit forum, yes I did compile it for a 32-bit system :oops:

---

### Post by zorkerz on 2007-10-24
noones been around here for a while but i thought id give you a shot.
i just installed gutsy 64 bit on a system with 4 gigs of ram but only 3.8 are recognized. The bios sees all 4096 mb just not gutsy.

I know 205 mb is not a huge deal here but it still annoys me that some of my ram is unused. Does anyone know what this is about?

---

### Post by shirsch on 2007-10-24
My system is leaving ~153MB unused.  However, I would stop short of calling it "wasted".   There is probably some address space below the 4GB line reserved for hardware I/O and the like.

As an informal observation, AMD64 systems tend to make fuller use of high memory than the Intel CORE 2 due to their built-in support for IO remapping.

---

### Post by zorkerz on 2007-10-24
Thats interesting I don't really know how this works. If i get it some of my ram may be being reserved for specific hardware rather than being thrown in with majority of the ram for general purposes. It was suggested on another post that my onboard  graphics card intel x3100 (without its own memory?) could have some reserved for it. This seems to be the same idea.

So if this is the case how can I tell what the ram is being reserved for or how can I set how much for specific devices?

---

### Post by psusi on 2007-10-25
You misunderstand a bit.  The hardware does not USE the ram, rather it is addressed AS ram.  For instance, an ethernet card has some on board ram to buffer packets.  The OS can directly read/write packets to/from the card's ram using a range of specific memory addresses that the motherboard routes to the card instead of to actual ram.  If you have 4 gb of actual ram, then some of that ram can not be accessed using any address because some addresses are routed to other hardware instead of ram.  Better motherboards have the ability to take the ram that has been masked by other hardware and remap it so it can be accessed using addresses above 4 gb, but many do not, leaving that ram to go to waste.

---

### Post by zorkerz on 2007-10-25
I should mention that im using 64 bit gutsy. My understanding was that with a 64 bit setup there is a total of 64 gigs of address space which should leave plenty of room for 4 gigs of ram and my hardware to be addressed.

Am I getting the concept?

---

### Post by weichiang on 2007-12-08
Hello folks,

My system would always reboot itself a few seconds after GRUB loads the kernel. Specs are as follows:
[LIST]
[*]O/S: Ubuntu Feisty Fawn Server 64bit
[*]Processor: Intel Q6600
[*]Mobo: Gigabyte GA-P35-DS4 BIOS version F9 (problem exists on the P35 chipset too, not just the P965 chipset)
[*]RAM: 1x2GB(channel 1) 2x1GB(channel 2)
[/LIST]

Managed to solve the problem by:
[LIST=1]
[*]Removing 1GB of RAM (The system would then boot normally)
[*]Adding the "blacklist intel_agp" line to "/etc/modprobe.d/blacklist".
[/LIST]

Thanks a lot to everyone out there who posted their solutions for this 4GB RAM/64bit problem. You guys FTW! :)

---

### Post by shirsch on 2007-12-08
> **weichiang said:**
> Hello folks,

My system would always reboot itself a few seconds after GRUB loads the kernel. Specs are as follows:
[LIST]
[*]O/S: Ubuntu Feisty Fawn Server 64bit
[/LIST]

Managed to solve the problem by:
[LIST=1]
[*]Removing 1GB of RAM (The system would then boot normally)
[*]Adding the "blacklist intel_agp" line to "/etc/modprobe.d/blacklist".
[/LIST]


FWIW, the newer kernels (as used in Ubuntu Gutsy Gibbon - aka 7.10) seem to have fixed the erroneous video detection issue.  It was the first installation where I did not have to stand on my head working around things.

---

### Post by fjgaude on 2007-12-08
> **psusi said:**
> You misunderstand a bit.  The hardware does not USE the ram, rather it is addressed AS ram.  For instance, an ethernet card has some on board ram to buffer packets.  The OS can directly read/write packets to/from the card's ram using a range of specific memory addresses that the motherboard routes to the card instead of to actual ram.  If you have 4 gb of actual ram, then some of that ram can not be accessed using any address because some addresses are routed to other hardware instead of ram.  Better motherboards have the ability to take the ram that has been masked by other hardware and remap it so it can be accessed using addresses above 4 gb, but many do not, leaving that ram to go to waste.

Thanks, man, this makes it clear so there is not much misunderstanding.

---

### Post by nutz on 2007-12-08
I have Memory Hole Remapping enabled in my bois and it shows 3.6gb under Gutsy64. Gutsy 32 showed 2.7gb....

What exactly does the Memory Hole Remapping option do?

---

### Post by nostriluu on 2008-02-02
I hope this is the right thread. I have a p5b-vm with 4GB of RAM. Everything works fine with 2GB of RAM, but with 4GB the system is incredibly slow. The RAM tests fine using memtest.

I can't disable the jmicron controller, but have blacklisted intel_agp. It makes no difference. I have dual boot 32bit gutsy and there is the same problem. Any solutions? Do other boards work well? If so could someone recommend a similar micro-atx board that will work without these problems?

---

### Post by ceefour on 2008-04-25
Related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189269](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189269)

Other thread:
[http://ubuntuforums.org/showthread.php?p=4792462](http://ubuntuforums.org/showthread.php?p=4792462)

---

### Post by fjgaude on 2008-04-25
Both under Gutsy and Hardy my 4GB of RAM shows as such. And the system is fast, fast:

With new Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=24C; under max load, temp=41C, fan=1167 RPM; VCore=1.39/1.38v:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   18948 MB in  2.00 seconds = 9487.52 MB/sec
 Timing buffered disk reads:  644 MB in  3.00 seconds = 214.42 MB/sec
```

My motherboard is Gigabyte GA-P35-DS4. /dev/md32 is raid5, four drives. I can attest that the stock kernels handle 4GB as they should.

Many manufacturers haven't come up to speed with the availability of such large amounts of memory.

---

### Post by acrider on 2008-04-28
I had solved this problem in 7.10 by using the server kernel.  The disadvantage was that I had to compile the nVidia kernel module for that kernel to make it also work with my 7600 graphics card, but I did succeed without too much effort (just a few items in the instructions were out of date).

This weekend I installed 8.04 and once again the generic kernel only recognizes approximately 3 GB of RAM.  So I installed the server kernel and attempted to compile the nVidia kernel module.  However, that failed because the server kernel now includes Xen support which causes an error in the nVidia module compile.  Is there another solution that doesn't involve building a custom kernel?

---

### Post by sprocket12 on 2008-05-02
<(bump!)> I have the *same* problem.  I want a 32-bit kernel with PAE but w/o Xen for the nVidia drivers.  Is there already such a beast?

---

### Post by arang on 2008-05-04
> **sprocket12 said:**
> <(bump!)> I have the *same* problem.  I want a 32-bit kernel with PAE but w/o Xen for the nVidia drivers.  Is there already such a beast?

i agree i have 4gb of ram with gutsy and i had to use the server kernel with the nvidia module manually compiled but the problem now is with hardy i cant do so for the reason explained already, anyone have a solution for this? i really dont want to use 64 bits due to all the trickery needed to use software like skype and others

---

### Post by andydread on 2008-05-18
This is really sad.  Even in Debian one can install the linux-image-bigmem-whatever.xx.xx  I wonder whose brilliant idea it was to only supply server kernels with >3GB support.  Haven't these people heard of *workstations*. What reason would there be not to provide a highend workstation kernel?

It seems the general assumption is that if you have 4GB or more of ram you must be either:- 
1) using a 64 bit CPU so a 64 bit kernel should be used.   The problem.  64bit is not ready so you cannot assume people will use 64bit when flash still does not work and skype etc.   
2) running a server.  

If this is the case then this is a poor assumption and Canonical should know better than that.  

Does anyone have any way around this problem?  As it stands I cant use Compiz with Nvidia-glx-new on any PC with more than 3GB of ram.

---

### Post by hiptoss on 2008-05-21
I'm unable to even install Ubuntu 8.04 x64 on my hardware.  When I boot the cd, after the menu loads I'm presented with the initramfs shell and if I cat casper.log, nothing at all is helpful.  The only message is: 

Unable to find a medium containing a live file system

My hardware is here: [http://global.shuttle.com/product_detail_spec.jsp?PI=638](http://global.shuttle.com/product_detail_spec.jsp?PI=638)

The noteable hardware is e6750 (no overclock) and 4gb of memory.  I've seen earlier posts about blacklists, but I'm not able to even install the OS so I can't get to that point.  Does anyone know a method that I can use to get Ubuntu installed?

Thanks in advance for any assistance.

---

### Post by Eniak on 2008-05-29
I just upgraded my macbook pro's ram from 2gb to 4gb...
I just installed ubuntu 8.04 64 bits and no good... it yet says that I have 3gb... :confused:

It can't b faulty memory cuz os x is reading the 4gb fine

---

### Post by cdbermud on 2008-06-05
> **arang said:**
> i agree i have 4gb of ram with gutsy and i had to use the server kernel with the nvidia module manually compiled but the problem now is with hardy i cant do so for the reason explained already, anyone have a solution for this? i really dont want to use 64 bits due to all the trickery needed to use software like skype and others

This is driving me nuts on my new thinkpad..  cursed thing has 4GB of ram, so I first installed Vista 64 (I need to be able to run Visual Studio for Windows/C++).  Dropped that when I realized it wouldn't allow unsigned drivers and decided to put windows in a VMWare VM and install Ubuntu 8.04.  Actually first installed the x86_64 version, but had too many issues so I installed the i386 version and then upgraded to the server kernel when I realized the desktop didn't have pae support.  Except now I can't install the NVIDIA drivers.. I had no idea that the "server" kernel would push Xen on me.. it doesn't seem to be documented anywhere, and I hardly think that one can assume a server would always use or want Xen w/ all the other virtualization technologies out there.  Probably why even RHEL Server 5 offers a non-Xen kernel version and the Xen Kernel is clearly described as such... ie: uname -r = 2xxxx-**xen**

bleh.. hopefully someone will patch the NVIDIA drivers.. or better yet a Ubuntu supported kernel w/o Xen and w/ large memory support will be released..

---

