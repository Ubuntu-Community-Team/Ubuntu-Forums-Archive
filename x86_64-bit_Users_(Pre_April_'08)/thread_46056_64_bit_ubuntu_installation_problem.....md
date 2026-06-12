---
title: "64 bit ubuntu installation problem...."
date: 2005-07-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by cherian thomas on 2005-07-03
hi all,
        i have an amd 64 bit 939 pin system(system specs given below). recently i tried to install ubuntu.everthing works during the installation but when the system boots up it get stuck at the spash screen. i cant even go to the cli terminals.ive been a regular dian sarge user but i cudnt get to fix this issue. moreover when i checked ubuntu forums ive noticed that many have the same problem but no solns posted.
    the same happens for the 64 bit live cd, the 386 live and installtions cds too.
    i hope somebody out there caan help me with the issue.
        moreover if somebody has anything to advice me on installing 64 bit os(linux) plz do post
 
 
 
 

<<< System Summary >>>
--------------------------------------------------------------------------------
 
  < Processor >
    Model:                         AMD Athlon(tm) 64 Processor 3000+
    Speed:                         1.79GHz
    Model Number:                  3000 (estimated)
    Type:                          Standard
    L2 On-board Cache:             512kB ECC Synchronous, Write-Back, 16-way set,
                                    64 byte line size
 
  < Mainboard >
    Bus(es):                       ISA X-Bus PCI USB FireWire/1394
    MP Support:                    1 CPU(s)
    MP APIC:                       No
    System BIOS:                   Phoenix Technologies, LTD 6.00 PG
    Mainboard:                     MS-7093
    Total Memory:                  447MB DDR-SDRAM
 
  < Chipset 1 >
    Model:                         Micro-Star International Co Ltd (MSI) ??? 
                                   (5950)
    Front Side Bus Speed:          1x 199MHz (199MHz data rate)
 
  < Chipset 2 >
    Model:                         Advanced Micro Devices (AMD) Athlon 64 / 
                                   Opteron HyperTransport Technology 
                                   Configuration
    Front Side Bus Speed:          2x 995MHz (1990MHz data rate)
    Total Memory:                  512MB DDR-SDRAM
    Memory Bus Speed:              2x 199MHz (398MHz data rate)
 
  < Video System >
    Monitor/Panel:                 Samsung Samtron 40Bn
    Adapter:                       ATI RADEON Xpress 200 Series
 
  < Physical Storage Devices >
    Removable Drive:               Floppy disk drive
    Hard Disk:                     ST320413A (19GB)
    Hard Disk:                     ST380817 AS SCSI Disk Device (75GB)
    CD-ROM/DVD:                    SONY DVD-ROM DDU1622 (CD 40X Rd) (DVD 5X Rd)
 

  < Peripherals >
    Serial/Parallel Port(s):       1 COM / 1 LPT
    USB Controller/Hub:            Standard OpenHCD USB Host Controller
    USB Controller/Hub:            Standard OpenHCD USB Host Controller
    USB Controller/Hub:            USB Root Hub
    USB Controller/Hub:            USB Root Hub
    FireWire/1394 Controller/Hub:  VIA OHCI Compliant IEEE 1394 Host Controller
    Keyboard:                      Standard 101/102-Key or Microsoft Natural PS/
                                   2 Keyboard
    Mouse:                         PS/2 Compatible Mouse
 
  < MultiMedia Device(s) >
    Device:                        Realtek AC'97 Audio
 

  < Power Management >
    AC Line Status:                On-Line
 

  < Network Services >
    Adapter:                       Realtek RTL8139/810x Family Fast Ethernet NIC
 
<<< Sound Card Information >>>
--------------------------------------------------------------------------------
 
<< Wave Input Devices (Recording) >>
<< Realtek AC97 Audio >>
  < General Information >
    Device Name:                   Realtek AC97 Audio
    Manufacturer:                  Microsoft
    Version:                       5.10
    Product ID:                    101 / 1
 
  < Specific Wave Information >
    Maximum Standard Sampling Bits:16-bit
    Maximum Standard Sampling Rate:96kHz
    Channels:                      65535
 

  < Specific Wave Information >
    Maximum Standard Sampling Bits:16-bit
    Maximum Standard Sampling Rate:44kHz
    Channels:                      2
 
<< Wave Output Devices (Playback) >>
<< Realtek AC97 Audio >>
  < General Information >
    Device Name:                   Realtek AC97 Audio
    Manufacturer:                  Microsoft
    Version:                       5.10
    Product ID:                    100 / 1
 
  < Specific Wave Information >
    Maximum Standard Sampling Bits:16-bit
    Maximum Standard Sampling Rate:96kHz
    Channels:                      65535
 
  < Device Capabilities >
    Pitch Control:                 No
    Playback Rate Control:         No
    Synchronous Operation:         No
    Sample Accurate Position Infor:Yes
    Volume Control:                Yes
    Balance Control:               Yes
 

  < Specific Wave Information >
    Maximum Standard Sampling Bits:16-bit
    Maximum Standard Sampling Rate:44kHz
    Channels:                      2
 
  < Device Capabilities >
    Pitch Control:                 No
    Playback Rate Control:         No
    Synchronous Operation:         No
    Sample Accurate Position Infor:Yes
    Volume Control:                Yes
    Balance Control:               Yes
 
<< MIDI Output Devices (Playback) >>
<< Microsoft GS Wavetable SW Synth >>
  < General Information >
    Device Name:                   Microsoft GS Wavetable SW Synth
    Manufacturer:                  Microsoft
    Version:                       5.10
    Product ID:                    102 / 1
 
  < Specific Synthesizer Information >
    Device Type:                   Special
    Voices:                        48
    Notes:                         48
    Channels:                      16
 
  < Device Capabilities >
    Patch Caching:                 No
    Stream Support:                No
    Volume Control:                Yes
    Balance Control:               Yes
 

  < Specific Synthesizer Information >
    Device Type:                   MIDI Mapper
    Channels:                      16
 
  < Device Capabilities >
    Patch Caching:                 No
    Stream Support:                Yes
    Volume Control:                Yes
    Balance Control:               Yes
 
<< Mixer Devices (Mixing) >>
<< Realtek AC97 Audio >>
  < General Information >
    Device Name:                   Realtek AC97 Audio
    Manufacturer:                  Microsoft
    Version:                       5.10
    Product ID:                    104 / 1
 
  < Volume Control Line Information >
    Type:                          Speakers
    Channels:                      2
    Line is Active:                Yes
    Line is Disconnected:          No
    Source Line:                   No
 
  < Recording Control Line Information >
    Type:                          Wave Input
    Channels:                      1
    Line is Active:                Yes
    Line is Disconnected:          No
    Source Line:                   No
 

 

-- 
 
With regards and concern,
Cherian
----------------------------------------------------------------------------------------------------------------------------------------
Version: 3.1
gcs d+ s+:+ a-- C++ ULUP+L+++E- W++ N++ K- w++ O- M-- V- Y+ PGP++ X+ tv- b+ G++ e++ h-- r++ z? 
----------------------------------------------------------------------------------------------------------------------------------------

---

### Post by DancingSun on 2005-07-03
I'm new to Linux and Ubuntu, this is just my 4th day, actually. That being said,  I've successfully installed a dual boot configuration with Windows XP then Ubuntu AMD64.

My hunch is that your hardware might be causing some troubles, since this happens across the board even with the 32-bit Ubuntu installation.

>  < Chipset 1 >
Model: Micro-Star International Co Ltd (MSI) ???
(5950)
Front Side Bus Speed: 1x 199MHz (199MHz data rate)

< Chipset 2 >
Model: Advanced Micro Devices (AMD) Athlon 64 /
Opteron HyperTransport Technology
Configuration
Front Side Bus Speed: 2x 995MHz (1990MHz data rate)
Total Memory: 512MB DDR-SDRAM
Memory Bus Speed: 2x 199MHz (398MHz data rate)

I don't quite understand why you have 2 chipsets here?  Moreover, why is there one even with a "Front-side Bus"?  Althon 64s have built-in memory controllers, so the front-side is not necessary

Is [this](http://www.msi.com.tw/program/products/mainboard/mbd/pro_mbd_detail.php?UID=639) the motherboard you got?  If so, I think it **might** be your integrated video that's causing the problem.  I am not sure.

If you have any add-on cards, make sure you remove them and try booting the computer via the Live CD.  If this works, then one of the add-on cards may be the cause of your problem.

The ATi chipsets are fairly new, you might want to do some search regarding your chipset (ATI® Radeon XPRESS 200 Chipset) and Ubuntu and/or Linux.  I am using NVidia's nForce4 Ultra chipset, and had no problems installing Ubuntu.

---

### Post by cherian thomas on 2005-07-03
ya thats the mobo...thats rite msi rs480 with integretd ati xpress 200...

---

### Post by killerfish on 2005-07-03
I had the exact same issue.  I'm betting the open source ATI driver is causing you issue.  I have an nVidia card and Ubuntu tried to use the opensource 'nv' driver by default.  Net, I had to switch it from the 'nv' driver to the 'vesa' driver until I could install the closed source nVidia driver.

To fix:
1. At login prompt press CTL-Alt-F1 to get a terminal prompt
2. Login
3. Type: **sudo nano /etc/X11/xorg.conf**
4. Arrow down to find the device section for your video card.  
5. Change the driver line to say: **Driver    vesa**
6. Save & Quit: I think it's Ctl-O then Ctl-X
7. Switch back to graphical login: **ALT-F7**
8. Restart X: **CTL-ALT-Backspace**
9. Login and see if it works.. If so, install binary ATI drivers (I think it's fglrx).

Hope this helps
KF

---

