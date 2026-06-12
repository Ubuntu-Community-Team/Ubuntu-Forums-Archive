---
title: "Help with the need for Drive Speed"
date: 2006-03-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jimtheplanner on 2006-03-30
Hi Guy's

Best advice please, I'm giving Ubuntu a try after using SuSe 10 for the last wee while. I have a 64 Bit AMD 3200, 200GB SATA HD, 1Mb RAM, Pioneer DVR 1100-D & ATI RS482-M Graphics card.

My main problem is the file transfer from DVD/CD to the HD, ripping music can take some 20 mins!! How can I speed this process up?](*,)  Also, I gave Gnomebaker a try to write fom data & it gave up first try? What is the best burning program K3B:confused: 

Any other advice on possible pitfalls would also be appreciated.

Thanks

Jim the Planner...

---

### Post by Stormbringer on 2006-03-30
Sounds as if DMA isn't enabled for your HD and/or DVD-ROM(-Writer) ...

Open a terminal and check if DMA is enabled by issueing:

# sudo hdparm /dev/hda
If Ubuntu isn't installed on hda please replace it with the correct one.

This should give an output like this:

```

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 20023/255/63, sectors = 321672960, start = 0

```

See the "using_dma" line? If it reads "1 (on)" then DMA is enabled for the hard drive. If it reads "0 (off)" it isn't.

Do the same for your optical drives (DVD-ROM, DVD-Writer, ...)

# sudo hdparm /dev/hdb
DVD-ROM

```

/dev/hdb:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)

```

# sudo hdparm /dev/hdc
DVD-Writer

```

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)

```

If DMA isn't enabled there's a config file where you can enable it during system boot ... it's permanent that way.

# sudo gedit /etc/hdparm.conf

At the end of the file simply add the devices on which you want DMA to be enabled by following the example below:

```

# If the hard drive doesn't use DMA automatically
/dev/hda {
        dma = on
}

# Enable DMA for the DVD-ROM
/dev/hdb {
        dma = on
}

# Enable DMA for the DVD-Writer
/dev/hdc {
        dma = on
}

```

Save the file.

To enable DMA without doing an reboot issue a command like this:

# sudo hdparm -d 1 /dev/hdb

Repeat for every other device.


As for GnomeBaker ... it works fine for me (CD(RW), DVD+/-R(RW), DVD-RAM).
I also tried Audio CD to MP3 (192kbps, CBR, Joint Stereo) ripping by using SoundJuicer ... a little slow (max. 7.4X speed on a Athlon 64 3000+) but it works.

Cheers,
Storm.

---

### Post by Jimtheplanner on 2006-03-30
Thanks Stormbringer,

As I have a SATA drive should I look for sda rather than hda?? I'll give your recommendation a try out when I get home tonight.

Just curious - using "Stormbringer" are you a Deep Purple Fan?

Regards

Jim the Planner.....

---

### Post by Stormbringer on 2006-03-30
[QUOTE=Jimtheplanner]
As I have a SATA drive should I look for sda rather than hda??
[/QUOTE]

SATA drives are treated as SCSI devices ... there's no option to enable or disable DMA (at least on my system - VIA K8T800 Chipset, drive is connected to the VIA VT6420 SATA Hostadapter integrated in the VT8237 Southbridge).

It's safe to do a ...

# sudo hdparm /dev/sda

... but if the output is missing the "using_dma" line then the setting isn't available.

In the later case, could you give us a little more info on your system's hardware - maybe this will give some insight.

[QUOTE=Jimtheplanner]
Just curious - using "Stormbringer" are you a Deep Purple Fan?
[/QUOTE]

Kind of. But ... if you ask my friends they will tell you that my nick perfectly fits my personality at times.

Cheers,
Storm.

---

### Post by Jimtheplanner on 2006-03-30
Hi Storm,

I had a go with your instructions & got the following:-

/dev/hda:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

I also tried with the DVD on hdb, hdc & hde. However, all I got back was as per this example:-

james@ubuntu:~$ sudo hdparm /dev/hdb
/dev/hdb: No such file or directory 

Any advice would be most welcome...

Jim the planner

---

### Post by Stormbringer on 2006-03-30
[QUOTE=Jimtheplanner]I had a go with your instructions & got the following:-

/dev/hda:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
[/QUOTE]

So, DMA is disabled on this device. As GETGEO(metry) reports "failed" I assume that this is an optical drive (DVD-ROM or DVD-Writer).

# sudo hdparm -d 1 /dev/hda
to enable DMA.

You may also try ...

# sudo hdparm -d 1 -c 1 -u 1 /dev/hda
-d 1 - enable DMA
-c 3 - set 32-Bit I/O mode
-u 1 - unmask IRQ

...and see if it improves the speed.

Be warned that the later hdparm command may crash your system if the device doesn't support it.

[QUOTE=Jimtheplanner]
I also tried with the DVD on hdb, hdc & hde. However, all I got back was as per this example:-

james@ubuntu:~$ sudo hdparm /dev/hdb
/dev/hdb: No such file or directory 
[/QUOTE]

In this case it's most likely that you don't have any device connected to /dev/hdb, /dev/hdc, ... and so on.

Could you please post your /etc/fstab??? We wouldn't have to make guesses if we would know the devices denoted there.

Storm.

---

### Post by Jimtheplanner on 2006-03-30
Hi Storm,

I dont what I've done :confused: However, I did a copy & paste with your code & restart & bingo:-D 

I can rip music on sound jucer at 6.9x :p 

I'm now going off to try Gnomebaker. Using Suse I was used to K3B so I shall give it a try & see...

I will have other question, but as the are of a differing topic I'll use a new posting.

Storm thank you very much for your help I'm sure that Ubuntu will grow on me & of course that one of the great things with Linux it's always good to try something  new.

Thanks again 

Jim the planner.......

---

