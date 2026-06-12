---
title: "ATI X200 Laptop No Sound"
date: 2006-03-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by michiganbroadband on 2006-03-18
Greetings,

I have been running Ubuntu 5.1 for several months on my laptop and have in that
time not been able to figure out why I have no sound.
Done a number of searches here and on Google all which have not led to a solution so far.

The module(s) seems to be loaded (atiixp) and the system seems to 'think' all is well however I cannot hear any sound.
This is a laptop, speakers are of course just fine and work in Windows.
It seems as if sound *is* working but the mixer portion may not be even though
mixer controls all look and move normally...

Any softwre that makes sound says it playing sound but no sound makes
it to the speakers.

XMMS aplay system sound play test button,
Heck even catting binaries to /dev/dsp don't make any sound.

I checked all of the basics that I know to check.
Any pointers greatly appreciated! sound on this beast would really
be nice!

Thanks,

Steve


---|---


root@lappy:/usr/lib/openoffice2/share/gallery/sounds# aplay horse.wav
Playing WAVE 'horse.wav' : Signed 16 bit Little Endian, Rate 11025 Hz, Mono
root@lappy:/usr/lib/openoffice2/share/gallery/sounds# (nothing heard)

tried software mixers on desktop and alsamixer all turned up full.

lspci:

lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5951
0000:00:02.0 PCI bridge: ATI Technologies Inc: Unknown device 5a34
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 10)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 01)
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 4378 (rev 01)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5653
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
0000:02:04.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
0000:02:04.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
0000:02:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)



lsmod:

Module                  Size  Used by
rfcomm                 37168  0
l2cap                  24328  5 rfcomm
bluetooth              48964  4 rfcomm,l2cap
powernow_k8            10512  0
cpufreq_userspace       5584  1
cpufreq_stats           5896  0
freq_table              5384  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2432  0
cpufreq_ondemand        7212  0
cpufreq_conservative     8236  0
pcmcia                 28556  4
video                  17416  0
tc1100_wmi              8200  0
sony_acpi               6296  0
pcc_acpi               13696  0
hotkey                 10696  0
dev_acpi               14980  0
i2c_acpi_ec             6528  0
i2c_core               22936  1 i2c_acpi_ec
button                  7968  0
battery                10760  0
container               5248  0
ac                      5768  0
ipv6                  246400  6
af_packet              22668  4
pcspkr                  4176  0
hostap_pci             51996  0
hostap                109456  1 hostap_pci
orinoco_pci             7808  0
orinoco                35980  1 orinoco_pci
hermes                  8192  2 orinoco_pci,orinoco
ohci1394               32844  0
yenta_socket           24460  2
rsrc_nonstatic         12160  1 yenta_socket
pcmcia_core            49928  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_atiixp             21792  1
snd_ac97_codec         87000  1 snd_atiixp
snd_pcm_oss            51232  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                91020  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              24200  1 snd_pcm
snd                    55784  8 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10912  1 snd
snd_page_alloc         11408  2 snd_atiixp,snd_pcm
shpchp                 87976  0
pci_hotplug            28008  1 shpchp
dm_mod                 54904  1
tsdev                   8960  0
evdev                  10496  0
sr_mod                 17188  0
sbp2                   24328  0
scsi_mod              143984  2 sr_mod,sbp2
ieee1394              101880  2 ohci1394,sbp2
rtc                    13448  0
psmouse                27908  0
mousedev               12260  1
parport_pc             36328  0
lp                     13576  0
parport                38540  2 parport_pc,lp
md                     43904  0
ext3                  127632  1
jbd                    54960  1 ext3
thermal                15120  0
processor              25684  2 powernow_k8,thermal
fan                     5384  0
8139too                26496  0
8139cp                 21248  0
mii                     6144  2 8139too,8139cp
ehci_hcd               31752  0
ohci_hcd               20228  0
ide_cd                 40608  0
cdrom                  36520  2 sr_mod,ide_cd
ide_disk               17152  3
ide_generic             1920  0
atiixp                  6544  1
ide_core              148932  4 ide_cd,ide_disk,ide_generic,atiixp
unix                   28728  739
vesafb                  9252  0
capability              6152  0
commoncap               8448  1 capability
vga16fb                12288  1
vgastate                9216  1 vga16fb
softcursor              2944  2 vesafb,vga16fb
cfbimgblt               3200  2 vesafb,vga16fb
cfbfillrect             4736  2 vesafb,vga16fb
cfbcopyarea             4352  2 vesafb,vga16fb
fbcon                  36480  72
tileblit                2944  1 fbcon
font                    9216  1 fbcon
bitblit                 5760  1 fbcon

Kernel:

cat /proc/version
Linux version 2.6.12-10-amd64-generic (buildd@crested) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Thu Dec 22 10:56:42 UTC 2005


cat interrupts
           CPU0
  0:    8946863    IO-APIC-edge  timer
  1:      17571    IO-APIC-edge  i8042
  8:          0    IO-APIC-edge  rtc
 12:     242076    IO-APIC-edge  i8042
 14:      51103    IO-APIC-edge  ide0
 15:      78998    IO-APIC-edge  ide1
 16:      83490   IO-APIC-level  eth1
 17:      12341   IO-APIC-level  ATI IXP
 18:          0   IO-APIC-level  eth0
 19:          1   IO-APIC-level  ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb3, yenta
 20:          0   IO-APIC-level  yenta
 21:       5475   IO-APIC-level  acpi, ohci1394
NMI:       1083
LOC:    8944962
ERR:         19
MIS:          0

System updates:

root@lappy:/proc# apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [43.6kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4130B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [13.4kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Fetched 89.4kB in 1s (50.2kB/s)
Reading package lists... Done
root@lappy:/proc# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by michiganbroadband on 2006-03-22
Tried a number of things since my last post and still have not gotten anywhere with this....

A RedHat user reported he needed to click the checkmark under
'external amplifier' in the mixer, I tried this and it made absolutely 
no difference...

Still looking for any pointers in the right direction,

Steve
:confused:

---

### Post by michiganbroadband on 2006-03-23
Boy!

Just thought I'd reply to myself again.....

If I'm in the wrong place for this question please send me some guidance!

I'd really like to get the sound working on my laptop if possible.....
I tried a bunch of the usual things including booting with the latest Knoppix
Live CD which everyone always tries in these types of situations....
and I get thesame problem there....

Linux 'thinks' the sound is working but nothing can be heard in the speakers.

Still looking for pointers!:rolleyes: 

Thanks!

Steve

---

### Post by michiganbroadband on 2006-03-27
Still desiring help on this, am I in the correct place to ask for it?

Steve

---

### Post by duality on 2006-03-28
try typing "alsamixer" in terminal and make sure that nothings on mute.

---

### Post by michiganbroadband on 2006-03-28
Thanks for the reply, I have been very curious as to why nobody
has replied on this one.. 
It's very nice to hear from somebody Thanks!

My problem is not a level adjust or something muted at the controls.
Anyhow I am stil greatly in need of figuring out why I don't have sound...
It's not that simple.... nothing is muted, I've read all the docs I have been able to find and I have spent hours googling for any clues....

This post if carefully read also states that I tried alsamixer and that the
levels are turned all the way up :-)

Take care & thanks!

Steve

---

### Post by mdmarmer on 2006-03-28
Which laptop do you have?

Which Ubuntu are you running?

I have HP L2000 and I have no sound problems with any distro

One thing to check -- do you have headphone sound?

There is a known bug with AC97 especially on laptops where headphone sense switch and possibly other switches come up on when they are supposed to be off -- chec k this in mixer switch settings

A newer version of alsa could fix this, but maybe not

Mike

---

### Post by ThaRabbit on 2006-03-31
I just managed to solve this problem on my laptop, the problem lies with the alsadriver 1.0.9 package.. there's a fault in them concerning this audiochip.

Here's what to do:
1. Be sure you have the linux-headers installed
2. Download this file (wget [http://www.alsa-project.org/alsa/ftp/driver/alsa-driver-1.0.10.tar.bz2](http://www.alsa-project.org/alsa/ftp/driver/alsa-driver-1.0.10.tar.bz2))
3. Extract the file (tar -xvf alsa-driver-1.0.10.tar.bz2
4. Enter the directory (cd alsa-driver-1.0.10)
5. Configure the sources (./configure --with-kernel=/usr/src/linux-headers-2.6.12-10-amd64-generic --with-cards=atiixp)

**NOTE**
the kernel= should point to your headers, check the directory name for your system (could be that you have xxxxamd64-k8 or something different)

6. make
7. make install (as root)

Reboot your system, this should fix your trouble. If still no sound from your speakers then check if your laptops microphone jack is providing sound. Also, in the mixer, you can try to enable the external amplifier.

For more information: 
[http://craig.copi.org/computers/ms-1013/#sound](http://craig.copi.org/computers/ms-1013/#sound)

As you can see I chose to grab the drivers from the alsa project site rather than edit my repositories to get them from the dapper repositories. imho the better option.

---

### Post by michiganbroadband on 2006-04-16
Thanks!!!

I've been away for a few weeks.
I will give this a shot!
Take care,

Steve

---

