---
title: "ASUS A8N with nforce/realtek. No sound"
date: 2006-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Xell on 2006-04-13
Is there anybody who have acctually managed to get any sound out of this (or similar) ? I have been struggeling with this for too long now, and any tip on how to resolv this all end ut in errors not explained anywhere I can find. 

I seriously need help to debug this. I am reasonably noob so any questions for output, please inform on how to produse them ;)

Unfortunately, if I cannot resolve this within reasonable time I will have to toss out Ubuntu for Fedora, because then I at least know I will have sound, and no sound is not an option.

---

### Post by djroadrash on 2006-04-14
hi all i got a similar problem with an asus p5rd1-vm  motherboard, it has the realtek (rtl8201clphy) 10/100 LAN (had problems with 5.10 to get it recognized, it works out of the box on dapper flight 5 for amd 64), but the audio in the on board card for the asus mobo is not coming out of the speakers, from the manual: adi1986a 6 channel hi-def audio CODEC (works on xp) and i can see the card but i cant hear anything.  

```
$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc:
Unknown device 5a33 (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown
device 5a3f
0000:00:19.0 PCI bridge: ALi Corporation M5249 HTT to
PCI Bridge
0000:00:1b.0 Ethernet controller: ALi Corporation
M5263 Ethernet Controller (rev  50)
0000:00:1c.0 USB Controller: ALi Corporation USB 1.1
Controller (rev 03)
0000:00:1c.1 USB Controller: ALi Corporation USB 1.1
Controller (rev 03)
0000:00:1c.2 USB Controller: ALi Corporation USB 1.1
Controller (rev 03)
0000:00:1c.3 USB Controller: ALi Corporation USB 2.0
Controller (rev 01)
0000:00:1d.0 0403: ALi Corporation High Definition
Audio/AC'97 Host Controller
0000:00:1e.0 ISA bridge: ALi Corporation PCI to LPC
Controller (rev 31)
0000:00:1e.1 Bridge: ALi Corporation M7101 Power
Management Controller [PMU]
0000:00:1f.0 IDE interface: ALi Corporation M5229 IDE
(rev c7)
0000:00:1f.1 RAID bus controller: ALi Corporation ULi
5287 SATA (rev 02)
0000:01:05.0 VGA compatible controller: ATI
Technologies Inc: Unknown device 5a6 1
$ lsmod
Module                  Size  Used by
ipv6                  300416  12
rfcomm                 45600  0
l2cap                  30464  5 rfcomm
bluetooth              59268  4 rfcomm,l2cap
radeon                116768  0
drm                    95656  1 radeon
cpufreq_userspace       9184  0
cpufreq_stats           8264  0
freq_table              6464  1 cpufreq_stats
cpufreq_powersave       3328  0
cpufreq_ondemand        9768  0
cpufreq_conservative    10984  0
video                  18824  0
tc1100_wmi              9096  0
sony_acpi               7060  0
pcc_acpi               14848  0
hotkey                 13768  0
dev_acpi               15364  0
container               6272  0
button                  8864  0
acpi_sbs               24600  0
battery                12296  1 acpi_sbs
ac                      7176  1 acpi_sbs
i2c_acpi_ec             7040  1 acpi_sbs
nls_cp437               8320  1
ntfs                  101376  1
af_packet              28172  2
dm_mod                 63176  1
md_mod                 76792  0
rtc                    16760  0
parport_pc             40816  1
lp                     15040  0
parport                44172  2 parport_pc,lp
tsdev                  10240  0
usbhid                 43040  0
i2c_ali1535             9604  0
shpchp                 51360  0
pci_hotplug            33168  1 shpchp
i2c_ali15x3             9988  0
i2c_core               26624  3
i2c_acpi_ec,i2c_ali1535,i2c_ali15x3
psmouse                40452  0
snd_hda_intel          21664  1
snd_hda_codec         167624  1 snd_hda_intel
serio_raw               9732  0
snd_pcm_oss            59424  0
snd_mixer_oss          20608  1 snd_pcm_oss
snd_pcm               104712  3
snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              29064  1 snd_pcm
uli526x                20372  0
snd                    68576  8
snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              13216  1 snd
snd_page_alloc         13968  2 snd_hda_intel,snd_pcm
evdev                  14464  1
ext3                  145936  1
jbd                    70952  1 ext3
ide_generic             2816  0
ohci_hcd               23684  0
ehci_hcd               34568  0
usbcore               145980  4
usbhid,ohci_hcd,ehci_hcd
sata_uli                9988  0
libata                 67344  1 sata_uli
scsi_mod              159992  1 libata
ide_disk               19456  4
ide_cd                 35744  0
cdrom                  41144  1 ide_cd
generic                 7300  0
alim15x3               13980  0 [permanent]
thermal                16524  0
processor              29224  1 thermal
fan                     6408  0
capability              7176  0
commoncap               9728  1 capability
vga16fb                14864  1
cfbcopyarea             5120  1 vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4224  1 vga16fb
cfbfillrect             5760  1 vga16fb
fbcon                  43136  72
tileblit                4096  1 fbcon
font                    9984  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
```

a little word to Xell:
be patient and if you like ubuntu or any other linux distro people will help u and if the hardware is not supported it will be in the near future in most cases. have u tried dapper?, it could have support for your card already, if not, if you really have to get on line or what ever needs like sound and such, i guess u could go back to fedora or xp, or just load a livecd of other distros and see if it works, but do come back to ubuntu and check in the future ( if not available now) for the newest patches and kernels, they will get all hardware working. they are working on it
thanx
:) djroadrash

---

### Post by mschievano on 2006-04-14
asua a8n-e here.
sound comes from front speaker, but not from rear (there isn't the surround volume like in the 32 bit version of dapper).
I'm now trying to have an internet connection stable (eth0 comes down randomnly)

---

### Post by djroadrash on 2006-04-15
an update
so i played with alsamixer and turned all nobs on, also i ran a script from the asus motheboard cd (dunno what it did), the mobo has linux drivers but they are on rpms so could not use them, dont think there was one for the sound though, i saved the settings for alsamixer and tried xmms with a radio station, it was very loud and some music came on but it died right away, then no more sound, but i rebooted and the drums for login came on. then the initial sounds at boot came on too, but it was dirty and had a very high pitch. the cd works but has really bad sound, its dirty and with the high pitch. no internet radio though, so i got some sound but it is obviously configured wrong.
any ideas?
djroadrash.:)

---

### Post by djroadrash on 2006-04-15
so i got the sound to work, i did a lot of things so i guess a combination of stuff will do it.
i think what did it was a full apt-get dist-upgrade. i started with a apt-get update, then a apt-get upgrade, like i said on the post above. the system got a little unstable and i figured why not, so i did control-alt-f1 and did the apt-get dist-upgrade on root. halted the computer and went to sleep, next morning sound is better than xp pro. i dont have the equipment to check if surround sound works but am pretty happy. the next thing i noticed is that the screensaver is not working, all that happens is a black screen, i imagine it has something to do with the radeon xpress 200 working correctly?. but maybe is just a bug?, that is next.
dj:) roadrash

---

