---
title: "Installation Woes"
date: 2005-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by radiotalent on 2005-11-29
**The lead-in**

I'm attempting to install Ubuntu 5.10 AMD64 on the computer I picked up at the Best Buy Black Friday sales...  I had been running standard Ubuntu (5.10) on an IBM PC, but it developed enough hardware issues that it was time to upgrade.  The computer is the eMachines T6414, I've added a DLink DWL-520 (D) ethernet card (which I imagine I'll have to use NDISWrapper to get up and running) and a 40 GB hard drive (which was my old HD).  I've already resized the Windows partition and added a FAT32 for a Windows/Linux share on the 160GB drive the eMachine came with.  My goal is to install Ubuntu on the 40GB drive.


**The problem portion**

When trying to install the installation hangs right after this section
----
OHCI 1394 loaded successfully
PCI [Success]

Running /etc/hotplug/usb.rc
:48.8888482] ohci.hcd 0000:00:b.1:unlinmkk after no IRQ? controller is probably using the wrong IRQ
-----

I've tried booting the machine with an older Ubuntu live disc and it hangs, as well as an older Knoppix live disc, and the current Knoppix live disc (4.02).  I am able to boot Knoppix if I use the NoUSB modifier, which leads me to believe that there is some conflict there...but it is well beyond my ability to trouble shoot (still a Linux newbie that can accurately follow instructions).  I've tried disabling the Onboard LAN but that has not helped (which I thought was a bit of a longshot).  Any ideas?  Should I try and disable more items via the BIOS or is this a known problem with a known (or even unknown) solution.


**Machine decription** (taken from the eMachines website and edited for clarity)

eMachines T6414
    * AMD Athlon™ 64 3200+ Processor (512KB L2 Cache, 2.0GHz, 2000 MHz FSB)
    * ATI RS482 Chipset
    * 512 MB DDR (2x256MB) SDRAM, 400MHz Dual Channel
    * 160 GB HDD (7200 RPM, 2MB cache)
    * 16x DVD±RW Multi Format Double Layer drive
    * 8-in-1 Digital Media Manager (Secure Digital (SD), Smart Media, Micro Drive, Memory Stick, Memory Stick PRO, Compact Flash, Multimedia Card, USB 2.0)
    * ATI Radeon® Xpress 200 (PCI-Express®) (128MB DDR Shared Video) Memory
    * AC '97 Audio, Dolby 5.1 (6-Channel)
    * 10/100 Mbps integrated Ethernet LAN
    * 56K ITU V.92 ready Fax/Modem
    * Standard multifunction keyboard, 2-button wheel mouse
    * 7 USB 2.0 Ports (2 in front, 1 in Media Reader, 4 in back), 2 IEEE 1394, 1 VGA External Connector, 1 Parallel, 2 PS/2, 5 audio ports (2 in front, 3 in back)

And I'm using a E17T4 TFT LCD monitor.


Thanks for any help or thoughts you can offer.

---

### Post by amohanty on 2005-11-29
Most probably this:
* 8-in-1 Digital Media Manager (Secure Digital (SD), Smart Media, Micro Drive, Memory Stick, Memory Stick PRO, Compact Flash, Multimedia Card, USB 2.0)
is the root cause.

Brute force approach:
Try opening the box and removing the connection of the front panel '8-in-1 Digital Media Manager' from the mobo and then installing it.

If you are hesitant to do that, when the machine boots up enter the BIOS setup and either change the IRQs by hand or disable USB hub for now.

HTH
AM

---

### Post by jvictor on 2005-11-29
Looks like a prob with the USB Hot Plug system.. try amohantys suggestion. I'd prefer the 2nd suggestion though :-)

---

### Post by radiotalent on 2005-11-29
I was leaning towards a problem with the 8 in 1 but figured I was just jumping to conclusions since it was unfamiliar to me.  Not sure if physically disconnecting the reader is an easy option or not...I'll check when I get back home to the machine.

Would it be reasonable to assume that after I get Ubuntu installed I'll be safe to reconnect the 8 in 1 / re-enable the USB hub?  Or is it likely something I'll have to live without?

Thanks for the quick replys and the suggestions...I'll hopefully get into the machine tonight (or Wednesday) and post the results.

---

### Post by amohanty on 2005-11-29
> Would it be reasonable to assume that after I get Ubuntu installed I'll be safe to reconnect the 8 in 1 / re-enable the USB hub? Or is it likely something I'll have to live without?

Since it is an IRQ conflict problem, there are mainly two possible solutions if you want to  use the reader:

1. In the BIOS change the IRQ settings. The downside is that if you dont know what exactly you are doing you might end up with some other IRQ conflict.
Also some BIOS' allow you to setup IRQs based on an OS type (Win95, WinNT, other etc). See if changing it to other helps.

2. Move the connector to another USB slot on the mobo. Usually mobos have more than one USB connectors.

To read more about IRQs and how they work go here:
[http://www.webopedia.com/TERM/I/IRQ.html](http://www.webopedia.com/TERM/I/IRQ.html)
[http://en.wikipedia.org/wiki/IRQ](http://en.wikipedia.org/wiki/IRQ)
[http://www.pcguide.com/ref/mbsys/res/irq/num.htm](http://www.pcguide.com/ref/mbsys/res/irq/num.htm)

HTH
AM

---

### Post by radiotalent on 2005-12-01
**Update**

For the time being I was able to get the installation done by disconnecting the cable from the motherboard.  After a quick overview, I didn't see any other place to connect it so I was unable to just move the cable.  Installation went fine.  I'm at a new blockade involving the display, but thats a problem for another thread.

As far as a more long term solution...I didn't see a section in the BIOS (Phoenix Technologies 6.00 PG) to setup the IRQs based on OS, but I'll poke around some more.  I'll investigate switching around the IRQs more in the BIOS to have a solution that makes everyone happy.

Thanks again for the help thusfar.

---

