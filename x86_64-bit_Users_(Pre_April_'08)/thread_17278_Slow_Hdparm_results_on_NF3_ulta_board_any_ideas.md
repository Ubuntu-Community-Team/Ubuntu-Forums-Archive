---
title: "Slow Hdparm results on NF3 ulta board any ideas?"
date: 2005-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by arnage on 2005-02-27
Hdparm  test results are slow only gettin around  [COLOR=DarkOrange] buffered disk reads:   94 MB in  3.05 seconds =  30.80 MB/sec [/COLOR]

the follow is the setting im using.

/dev/hda:
 multcount    =  1 (on)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 81964302336, start = 0

My mainboard is an MSI NF3 ULTRA and my HD is IDE Maxtor 80GB 6Y080L0
ext 3 volume 

lspci |grep IDE
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)

kernel 2.6.10 ubuntu.

Thanks for any help, i just find things slow to open from hard disk.

---

### Post by Pluk on 2005-02-27
lspci |grep IDE
0000:00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)

 hdparm -tT /dev/hda
/dev/hda:
 Timing cached reads:   2096 MB in  2.00 seconds = 1046.59 MB/sec
 Timing buffered disk reads:  130 MB in  3.02 seconds =  43.00 MB/sec

# hdparm -i /dev/hda
/dev/hda:

 Model=WDC WD1200BB-00DWA0, FwRev=15.05R15, SerialNo=WD-WCAEK1268972
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=74
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=234441648
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: device does not report version:

 * signifies the current active mode

# hdparm /dev/hda
/dev/hda:
 multcount    = 16 (on)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 120034123776, start = 0


My multcount is 16 maybe thats the problem?
although changing it here to 1 didnt suffer performance
You can set it with: hdparm -m /dev/hdX 16

Are you using an 80-conductor IDE/ATA cable? if not performance would be max ATA33, if im not mistaken. 

Btw im using an homebrewed 2.6.10-amd64 kernel and FAT32 on /dev/hda.

---

### Post by arnage on 2005-02-27
Changed cable to a nice rounded one at now its
172 MB in  3.02 seconds =  56.89 MB/sec
which is fantastic

Thanks.

---

### Post by maxwell1500 on 2007-02-24
Ubuntu is really weird and there is nothing you can do with hdparm that is going to make a difference, I had the same trouble.  To fix this problem like I did rebuild a new kernel such as 2.6.20.  I got the full speed I expected from ubuntu.  I never had trouble with any other distro except ubuntu, but I like ubuntu and I am going to stick with it through better or worse.  Ubuntu does not come with everything to build a new kernel so look at [http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835) for the best way to build a kernel because ubuntu is a little different and I need to use this because everytime I built a kernel for ubuntu the normal way I always end up with kernel panic when I boot.  Good luck and this will work, I don't know what performance you are looking for or expect but it will improve my hdparm -t improved by 25 percent to what it should have been.  Fedora had no trouble the first time to get the right speed, but ubuntu is just a little weird.  But there are also other advantages of building kernels so good luck and use a newer kernel than whatever is listed on the website.  Sincerely some linux guy(Max Krone).

---

