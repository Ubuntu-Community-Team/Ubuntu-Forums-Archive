---
title: "DMA with nforce4"
date: 2005-06-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by jenik on 2005-06-05
I know there are several threads devoted to this topic, but whatever i do, it just doesn't work - i.e. cannot set DMA to on for my DVD drive.

my fstab:
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       /home           ext3    defaults        0       2
/dev/sda3       /windows        vfat    defaults        0       0
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0  	auto	ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/etc/modules:
AMD74xx
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
rtc
sbp2
sr_mod
nvidia

hdparm.conf:
#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/cdrom {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
	dma = on
}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}

hdparm is set S29 in /etc/rcS.d

I am sure there is some stupid mistake on my part but just cannot figure it out.
thanks

--------------------------------------------------
Ahtlon64 3000+
MSI K8N nForce4 SLI
GeForce 6200 128

---

### Post by drummer on 2005-06-05
Hi, I had similar problems (I have nforce3) and did what you did. I enabled DMA with ```
sudo hdparm -d1 /dev/hdb
``` >> You didn't say in your post if you tried this, if this successfully enables DMA, you can try what I've written next. <<

but on rebooting it never kept the settings even though i told it to (with the -k1 flag). I also tried uncommenting the settings in hdparm.conf but that slowed boot time down like there was no tomorrow, 'Starting Enterprise Volume Management System' hung for a couple minutes before deciding to proceed, so I commented the lines out again.

What finally worked was creating an init script like the one here: [http://ubuntuforums.org/showthread.php?t=28805&page=2&pp=10&highlight=hdparm+dma+init+script](http://ubuntuforums.org/showthread.php?t=28805&page=2&pp=10&highlight=hdparm+dma+init+script).
Fist I did ```
sudo gedit /etc/init.d/cdroms_dma
```and added to the new file: ```
#! /bin/sh
# /etc/init.d/cdroms_dma
#

# Carry out specific functions when asked to by the system
case "$1" in
  start)
    echo "Enable DMA for /dev/hda ..."
    hdparm -d 1 /dev/hda
    sleep 1
    echo "Enable DMA for /dev/hdb ..."
    hdparm -d 1 /dev/hdb
    echo "DONE!"
    ;;
  stop)
    echo "Disable DMA for /dev/hda ..."
    hdparm -d 0 /dev/hda
    sleep 1
    echo "Disable DMA for /dev/hdb ..."
    hdparm -d 0 /dev/hdb
    echo "DONE!"
    ;;
  *)
    echo "Usage: /etc/init.d/cdroms_dma {start|stop}"
    exit 1
    ;;
esac

exit 0

``` then ```
sudo chmod +x /etc/init.d/cdroms_dma
``` and finally```
sudo update-rc.d cdroms_dma defaults
```
Now that script turns DMA on each time the computer boots and off when it shuts down. Has worked flawlessly for me so far.

---

### Post by jenik on 2005-06-05
thanks for the extensive reply, unfortunately i can't set DMA even using hdparm  (operation not permitted (yes, using sudo...)). Searched the web quite thoroughly and found things about including the AMD74xx driver, setting DMA on in hdparm.conf and renaming S07hdparm to S29hdparm. all done but to no avail...

---

### Post by jenik on 2005-06-06
just to provide more info:

honza@jtruka:~$ sudo hdparm -v /dev/hda
Password:

/dev/hda:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

honza@jtruka:~$ lsmod
Module                  Size  Used by
udf                    83400  1
proc_intf               4420  0
freq_table              4872  0
cpufreq_userspace       5456  0
cpufreq_ondemand        7596  0
cpufreq_powersave       2176  0
video                  18760  0
sony_acpi               6864  0
pcc_acpi               13568  0
button                  7776  0
battery                11400  0
container               5120  0
ac                      5640  0
ipv6                  268512  9
ohci1394               35460  0
saa7134               113864  0
video_buf              25092  1 saa7134
v4l2_common             7744  1 saa7134
v4l1_compat            13572  1 saa7134
soundcore              11360  1 saa7134
i2c_core               24664  1 saa7134
ir_common               5828  1 saa7134
videodev               12160  1 saa7134
forcedeth              18880  0
amd74xx                15472  1
ehci_hcd               33604  0
ohci_hcd               22408  0
floppy                 65456  0
pcspkr                  4024  0
nls_iso8859_1           5504  1
nls_cp437               7232  1
vfat                   14464  1
fat                    42624  1 vfat
md                     48768  0
dm_mod                 63768  1
capability              5832  0
evdev                  10688  0
commoncap               9536  1 capability
tsdev                   8768  0
nvidia               4569404  12
sbp2                   27016  0
ieee1394              385496  2 ohci1394,sbp2
rtc                    13320  0
psmouse                22412  0
mousedev               13148  1
parport_pc             40648  1
lp                     13104  0
parport                40844  2 parport_pc,lp
ide_generic             1728  0
ide_disk               20800  0
ide_cd                 45192  1
ide_core              150276  4 amd74xx,ide_generic,ide_disk,ide_cd
ext3                  140560  2
jbd                    61104  1 ext3
mbcache                 9160  1 ext3
sr_mod                 18468  0
cdrom                  43304  2 ide_cd,sr_mod
sd_mod                 18584  5
sata_nv                 9860  8
libata                 55560  1 sata_nv
scsi_mod              143448  4 sbp2,sr_mod,sd_mod,libata
unix                   30016  670
thermal                15692  0
processor              26432  1 thermal
fan                     5256  0
fbcon                  38688  0
font                    8960  1 fbcon
bitblit                 5888  1 fbcon
vesafb                  7680  0
cfbcopyarea             4288  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             4288  1 vesafb

honza@jtruka:~$ lspci
0000:00:00.0 Memory controller: nVidia Corporation: Unknown device 005e (rev a3)0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0050 (rev a3)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0052 (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 005a (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 005b (rev a3)
0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 0053 (rev a2)
0000:00:07.0 IDE interface: nVidia Corporation: Unknown device 0054 (rev a3)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 0055 (rev a3)
0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 005c (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation: Unknown device 0057 (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:06.0 Multimedia controller: Philips Semiconductors SAA7134 (rev 01)
0000:01:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
0000:01:0d.0 Multimedia audio controller: Creative Labs SB Audigy LS
0000:05:00.0 VGA compatible controller: nVidia Corporation: Unknown device 014f (rev a2)

---

### Post by drummer on 2005-06-06
Sorry, I don't think I can be of much more help.. all that info looks similar to what I've got. Although the default IO_support on my drive is 32-bit and i think it's set to 1, even with DMA disabled. (??)

Perhaps you could check if the drive supports DMA, it might not if it's old .. or maybe needs a firmware upgrade? I'm no expert with all this, just conveying what I already know. Another good source of information is the #ubuntu IRC channel on irc.freenode.net .. good luck getting DMA running.

---

### Post by jenik on 2005-06-06
yeah, i changed the 32 IO support to 1 in hdparm.conf but dma is still off...the drive is brand new samsung DVD-RW... not completely sure about BIOS settings as they do not allow for explicit DMA setting, just auto

---

### Post by ::DoGG:: on 2005-06-06
For dvd and crdom drives i strongly recommend You to turn the scsi emulation. Since 2.6 kernels (as you can see in dosc) don`t really need it, but some applications seems to work better witk ide-scsi module. 
Put  the following line in your /boot/grub/menu.lst file, in the line when You pass the parameters to kernel:
```
hdc=ide-scsi 
```
Assuming that your dvd drive is a hdc device.
That did the trick form me on nForce.

---

### Post by jenik on 2005-06-06
ok, did that and there is no change whatsoever.... ](*,)  any ideas?

---

### Post by Jarz Corp on 2005-06-08
It probably isn't a good idea to write AMD74xx on a system that is case sensitive.

Try correcting that before paniccing and trying all kinds of complicated stuff.

amd74xx works super perfect on my nv4 board

---

### Post by crashemup on 2005-06-09
What I had to do with my system was add the chipset module to /etc/modules before the ide crap. After you reboot you should be able to hdparm the drive hdparm -c3 -d1 /dev/hda,hdb,hdc whatever

---

### Post by joekr on 2005-06-09
[QUOTE=Jarz Corp]It probably isn't a good idea to write AMD74xx on a system that is case sensitive.

Try correcting that before paniccing and trying all kinds of complicated stuff.

amd74xx works super perfect on my nv4 board[/QUOTE]

Exactly, replace AMD74xx with amd74xx and it should work thereafter.

---

### Post by whiskybar on 2005-06-10
Okay, several things.

One, to find out if amd74xx is loaded, use (I have nForce3 though)
lsmod | grep -i amd

You should find something like 
amd74xx                15280  1
ide_core              143748  4 ide_cd,ide_generic,ide_disk,amd74xx
The thing is to make sure ide_cd is using amd74xx...

Two, if you could have found this among the loaded modules, load it manualy by
modprobe amd74xx.

Three, enable the DMA by the aforementioned hdparm -d1 /dev/hdb. There is no use tweaking /etc/modules or /etc/hparm before you got it working from the command line.

Four, just a tip, call update-pciids to update the list for your lspci.

---

### Post by jenik on 2005-06-10
thanks guys for the replies, but although I admit it should be amd74xx in /etc/modules my posts on the previous page show (at least I think so) that the correct module is indeed loaded and working. they also show I cannot enable dma by hdparm command.

---

