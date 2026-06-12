---
title: "problem with graphics card?"
date: 2013-01-15
forum: Wine
---

### Post by 1forhlol on 2013-01-15
Hey I'm new to Ubuntu/Linux and im having trouble with my video card set up. It says my graphics are VESA: Redwood Standard. I'm having trouble while playing games but im not sure what the problem is exactly. 
[IMG]http://i.imgur.com/Rd41o.jpg?1[/IMG]

---

### Post by Mark Phelps on 2013-01-15
We can't help without first knowing the make and model video card/chipset.  If you don't know, open a terminal, enter "lspci" (without the quotes) and look for the line containing "VGA".  Post that information back here.

---

### Post by 1forhlol on 2013-01-15
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (external gfx0 port A)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (PCI express gpp port A)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (PCI express gpp port E)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
02:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
04:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Redwood PRO [Radeon HD 5500 Series]
04:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Redwood HDMI Audio [Radeon HD 5000 Series]
05:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Redwood PRO [Radeon HD 5500 Series]
05:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Redwood HDMI Audio [Radeon HD 5000 Series]

---

### Post by 1forhlol on 2013-01-15
Typed in what you said and this is what i got ^^. Any help would be much appreciated!

---

### Post by rrich1974 on 2013-01-15
you better use ubuntu 12.04 to install proprietary driver for your ati card. it does not work on 12.10 anymore. only hd 6xxx works on 12.10. 
the opensource driver is still in its infancy for your card.

---

### Post by 1forhlol on 2013-01-15
do i have to just reinstall a whole new ubuntu partition to do that? or is there a way without losing all my updates and setup progress?

edit: My ubuntu is actually 12.04 already so now i really am lost.

---

### Post by 1forhlol on 2013-01-15
I also have an ASUS HD7750 video card. would that be easier to install? it's a better video card i was just having trouble with it also.

---

### Post by Cheesemill on 2013-01-15
> **rrich1974 said:**
> you better use ubuntu 12.04 to install proprietary driver for your ati card. it does not work on 12.10 anymore. only hd 6xxx works on 12.10. 
the opensource driver is still in its infancy for your card.
Not true.

It was the 2/3/4xxx series of cards that were dropped for 12.10.
The 5xxx cards still have full support from the ATI closed source driver.

---

### Post by 1forhlol on 2013-01-15
what about the 7750 i talked about? do i just get the drivers from ati's site since it's close sourced?

---

### Post by Cheesemill on 2013-01-15
You shouldn't have to download the drivers from the ATI site, you should instead use the built-in application to install them.

Just go to System Settings > Additional Drivers

---

### Post by 1forhlol on 2013-01-15
I installed the ASUS HD 7750 video card and then ran the propriety drivers. It says i have the ATI?AMD proprietary FGLRX graphics driver. But under system settings>graphics it's blank. Also ran the lspci one more time for the new card. 


03:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
04:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 683f
04:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device aab0

gah this is not working!

---

### Post by Cheesemill on 2013-01-15
There is a bug in the System Settings application meaning it always shows the graphics as 'Unknown', don't pay any attention to it.

If the Additional Drivers application says you have the closed source drivers installed then you do.

What game are you having issues with? If it's a Windows game running under Wine then you may have better luck getting help if you ask for this thread to be moved to the Wine sub-forum instead of here in Absolute Beginners.

---

### Post by 1forhlol on 2013-01-15
Yea it's Diablo 3 and i'm running it through Wine. Could we move this thread? thanks for the help!

---

### Post by nothingspecial on 2013-01-15
*Thread moved to **Wine**.*

---

### Post by rrich1974 on 2013-01-16
as far as i remember, in 12.10 you dont have additional drivers. you must choose the driver from software source.

---

### Post by Lightning Dragon on 2013-01-16
I was looking at the image you provided. I'm not see anything wrong, looks like it is running? Might be this will help you for WINE. They might show something that could help set you up.

[http://www.iheartubuntu.com/2012/05/install-diablo-3-on-ubuntu.html](http://www.iheartubuntu.com/2012/05/install-diablo-3-on-ubuntu.html)
[http://sixgun.org/gaming-diablo3/](http://sixgun.org/gaming-diablo3/)
[http://www.youtube.com/watch?v=InQNW6WFb3U](http://www.youtube.com/watch?v=InQNW6WFb3U)
[http://www.youtube.com/watch?v=FInth5Fdg2M](http://www.youtube.com/watch?v=FInth5Fdg2M)

_**After**_ you have your drivers installed (as it looks like you have done), it should work. But some people have had issues in WINE installs and have those same issues vanish in POL installs.

So, that said, have you tried PlayOnLinux yet? [I am looking at the install directory they have and Diablo 3 is listed there]("http://postimage.org/image/8qaz52x75/") (< click that). If you can't get the above to work, then you should try POL and install that way. I have seen games works very well in POL, so it is worth a shot.

[http://www.evilcodingmonkey.com/2012/05/15/playing-diablo-3-on-ubuntu-made-very-easy/](http://www.evilcodingmonkey.com/2012/05/15/playing-diablo-3-on-ubuntu-made-very-easy/)
[SIZE=1]
*Though **some** people recommend not playing this game in either Wine or POL because they are getting banned--maybe. See this thread for the discussion just in case;

[http://ubuntuforums.org/showthread.php?t=2082281](http://ubuntuforums.org/showthread.php?t=2082281)[/SIZE]

---

