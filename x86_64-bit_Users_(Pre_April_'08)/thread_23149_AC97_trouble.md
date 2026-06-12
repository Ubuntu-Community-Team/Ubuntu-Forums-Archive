---
title: "AC97 trouble"
date: 2005-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by Execc on 2005-03-31
first time i use ubuntu/any linux os

here's my lsmod

Module                  Size  Used by
nls_cp437               7296  0
isofs                  36172  0
udf                    78088  0
ipv6                  252960  6
proc_intf               4484  0
freq_table              4872  0
cpufreq_userspace       5456  0
cpufreq_ondemand        7340  0
cpufreq_powersave       2304  0
af_packet              22412  2
video                  18824  0
sony_acpi               6928  0
pcc_acpi               13696  0
button                  7840  0
battery                11528  0
container               5248  0
ac                      5768  0
uhci_hcd               32800  0
ohci_hcd               21384  0
ehci_hcd               31620  0
i2c_viapro              8716  0
i2c_core               23960  1 i2c_viapro
r8169                  20872  0
shpchp                 95528  0
pci_hotplug            33240  1 shpchp
pcspkr                  4088  0
floppy                 62320  0
md                     46592  0
evdev                  10368  0
dm_mod                 59608  1
tsdev                   8704  0
capability              5896  0
commoncap               9344  1 capability
rtc                    13064  0
psmouse                21260  0
mousedev               12764  1
parport_pc             39496  1
lp                     12784  0
parport                39436  2 parport_pc,lp
ide_cd                 42760  0
cdrom                  41384  1 ide_cd
ext3                  133264  0
jbd                    57520  1 ext3
ide_generic             1792  0
via82cxxx              14128  1
ide_disk               19584  3
ide_core              143748  4 ide_cd,ide_generic,via82cxxx,ide_disk
unix                   28736  727
thermal                15756  0
processor              26560  1 thermal
fan                     5384  0
fbcon                  36512  0
font                    9088  1 fbcon
bitblit                 5632  1 fbcon
vesafb                  7616  0
cfbcopyarea             4352  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             4224  1 vesafb



actived multiverse/universe..

still no sound.. and the cdplayer wont even start the title(any title)

Regards

---

### Post by Execc on 2005-03-31
actually, it hasnt found my sound card at all.. :o) got a REALtek AC'97

---

### Post by Execc on 2005-04-01
someone delete this thread, ive managed to get the sound working.

---

### Post by cabu on 2005-04-01
Rather than deleting the thread, why don't you explain how you got it to work. The information may help someone out in the future if they do a search and find this thread.

---

### Post by DutchLau on 2005-05-03
Yes PLEASE tell us how you got it working!


I have the SAME problem!  :-|

---

