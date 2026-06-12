---
title: "&quot;Major&quot; problems with 7.04 64bit"
date: 2007-09-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by GumbyX on 2007-09-04
I am going to try and get some help with this problem one last time before I just give up and switch back to 32bit Ubuntu. I am currently having programs and my entire 64bit system crash at random times during the day. This has been going on for about a month, a week or so after installed it.  I will be doing stuff (usually related to listening to music or browsing the web) and the system just seems to 'hang'. Sometimes I can move my mouse, recently I cannot. My USB keyboard gives no response, and I have to do a hard shutdown. Sometimes GNOME will just die, and restart, bring me to a garbled log-in screen. I am not sure if this the machines fault, the Linux Kernel having problems with my setup, or  software issues (have been using uPure64 repository and Automatix for easy installs). I just need to try and salvage this install or give up and start over (and I HATE to give up).

I am running a AMD 64X2 3800+ processor with an ATI (offical) PCI-E graphics card. I have read (here) that for some reason there are issues with this chipset, but nothing like what I am running into. If someone can help me out, I'd appreciate it. I am getting really pissed at the lost work (this happened 4 times in one hour this weekend). I did not have any problems with 7.04 32bit and am getting ready to switch back. I like using a 64bit OS (for me it actually runs faster with the stuff I do), but if its running WORSE then Vista, something is DEF wrong.

Thanks ahead of time for the help.

---

### Post by ajaygautam on 2007-09-04
This sounds like faulty RAM / fauly hardware.

Ubuntu's live / install CD provides memory test. That should be a good place to start.

I highly recommend that you run the memory test. For best results, I say leave the mem test running overnight.

Ajay

---

### Post by jso2897 on 2007-09-04
The guy you want to seek out goes by the handle "Kilz". He seems to have forgotten more than anybody else knows about 64bit issues.  He knows about the work-arounds, and can steer you to scripts and wrappers and fixes that have worked for a lot of people. But yeah, first do what ajaygautam said - if you are having any memory issues, that has to get fixed first.

---

### Post by GumbyX on 2007-09-04
> **ajaygautam said:**
> This sounds like faulty RAM / fauly hardware.

Ubuntu's live / install CD provides memory test. That should be a good place to start.

I highly recommend that you run the memory test. For best results, I say leave the mem test running overnight.

Ajay

I don't think it can be a memory problem: I have had this PC for over two years now running Windows with no problems. I think I will try the test, but I don't think it will come up with anything. Thanks for the info though.

---

### Post by jso2897 on 2007-09-04
> **GumbyX said:**
> I don't think it can be a memory problem: I have had this PC for over two years now running Windows with no problems. I think I will try the test, but I don't think it will come up with anything. Thanks for the info though.

Not necessarily. I had a Windows box that was having all kinds of memory issues. I loaded Ubuntu - no more issues. I had another Windows box that was working fine - switched to Ubuntu, and memory glitches out the gazoo.
The best reason to do it is peace of mind. Once you've done it, you can put the issue out of your mind and proceed to seek the real solutions.:)

---

### Post by GumbyX on 2007-09-04
> **jso2897 said:**
> Not necessarily. I had a Windows box that was having all kinds of memory issues. I loaded Ubuntu - no more issues. I had another Windows box that was working fine - switched to Ubuntu, and memory glitches out the gazoo.
The best reason to do it is peace of mind. Once you've done it, you can put the issue out of your mind and proceed to seek the real solutions.:)

Dang...... Now I am worried. Looks like I will be doing this tonight. Would the mem test be on the 64bit alt. installer?

Also, if there are memory problems, HP is going to hear it from me....... :( But of course its not under ANY warranties anymore........ And I have no money to buy more mem.
........
......
I hate being a poor college student.

---

### Post by ExcessNeo on 2007-09-04
> **GumbyX said:**
> Dang...... Now I am worried. Looks like I will be doing this tonight. Would the mem test be on the 64bit alt. installer?.

Should be accessable under GRUB when you boot up.

memtest86 (normally the 3rd option down).

---

### Post by rsambuca on 2007-09-04
Obviously there are many many different potential causes for your symptoms, but I agree that checking your RAM is the logical first step.  It could also be heat issues.  Is this a laptop or a desktop PC?

---

### Post by GumbyX on 2007-09-04
> **rsambuca said:**
> Obviously there are many many different potential causes for your symptoms, but I agree that checking your RAM is the logical first step.  It could also be heat issues.  Is this a laptop or a desktop PC?

Desktop. I clean off the air intakes every few weeks to prevent overheating.

I plan on doing the mem scan when I leave for work today. Should be done by the time I get home. Hopefully its not the mem and just a software issue. A clean install can fix the software stuff.

ExcessNeo, thanks for giving me the heads up. I never look at GRUB often, so I never noticed the memory test being there.

---

### Post by jso2897 on 2007-09-04
> **ajaygautam said:**
> This sounds like faulty RAM / fauly hardware.

Ubuntu's live / install CD provides memory test. That should be a good place to start.

I highly recommend that you run the memory test. For best results, I say leave the mem test running overnight.

Ajay

Question, Ajay: How long does it take to run the ENTIRE memtest sequence, and how many tests are involved? I confess I have never run it all the way to completion myself - any machine I've had that passed the first hour or so has proved free of memory-type problems.

---

### Post by Jouke74 on 2007-09-04
To me it sound more like a video card or motherboard problem from the things you describe. 
(I am running 64 bit on an AMD 4200 X2, Asus ATI X1600Pro without any issues).

If it is hardware issues, you might be looking for them for quite some time. Any information in the system logs when things go down (if you are able to read them)?

Otherwise I would suggest to try and run a live DVD / CD for a while. Surfing the internet should be no problem and listening to music as well. If this also crashes you can exclude your current install. If not a reinstall might be an idea first before starting swapping hardware.

---

### Post by jso2897 on 2007-09-04
> **Jouke74 said:**
> To me it sound more like a video card or motherboard problem from the things you describe. 
(I am running 64 bit on an AMD 4200 X2, Asus ATI X1600Pro without any issues).

If it is hardware issues, you might be looking for them for quite some time. Any information in the system logs when things go down (if you are able to read them)?

Otherwise I would suggest to try and run a live DVD / CD for a while. Surfing the internet should be no problem and listening to music as well. If this also crashes you can exclude your current install. If not a reinstall might be an idea first before starting swapping hardware.

Good point, and a question occurs to me - are you getting a "beep code" when your pc fails to boot up? And if so, can you describe it(how many beeps, long and short)?

---

### Post by Yellow Pasque on 2007-09-04
> **GumbyX said:**
> I am running a AMD 64X2 3800+ processor with an ATI (offical) PCI-E graphics card. I have read (here) that for some reason there are issues with this chipset, but nothing like what I am running into.

Exactly what chipset/mobo would that be? What model HP do you have and what hardware have you added/modified?

---

### Post by GumbyX on 2007-09-04
Did the RAM check. Did it for about 7 horus, came up OK on all 20 tests it ran.

> **Temüjin said:**
> Exactly what chipset/mobo would that be? What model HP do you have and what hardware have you added/modified?

here is the link to the HP Spec sheet:
[HP Pavilion a1250n Spec]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00485646&lc=en&cc=us&dlc=en&product=1127366&lang=en")

Summary:
Board: MSI MS-7184
Chip: Athlon 64 X2 3800+ 2.0 GHz

Added a ATI Radeon x700Pro 256MB PCI-E

Here's hoping its something like a screwed up driver or something :crosses fingers:.

PS To those asking about beep codes, it doesn't beep. It does boot, but sometimes is just crashes.

PSS OH!! Looks like my warrenty is still good. :-D If its a hardware issue, I can get another rmachine still!!  Wonder if I should see what I can get for it..... : thinks about it:

---

### Post by Kilz on 2007-09-04
> **GumbyX said:**
> Did the RAM check. Did it for about 7 horus, came up OK on all 20 tests it ran.



here is the link to the HP Spec sheet:
[HP Pavilion a1250n Spec]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00485646&lc=en&cc=us&dlc=en&product=1127366&lang=en")

Summary:
Board: MSI MS-7184
Chip: Athlon 64 X2 3800+ 2.0 GHz

Added a ATI Radeon x700Pro 256MB PCI-E

Here's hoping its something like a screwed up driver or something :crosses fingers:.

PS To those asking about beep codes, it doesn't beep. It does boot, but sometimes is just crashes.

PSS OH!! Looks like my warrenty is still good. :-D If its a hardware issue, I can get another rmachine still!!  Wonder if I should see what I can get for it..... : thinks about it:

Are you running the ati drivers from ATI or Ubuntu? If you have the ATI ones installes what is the results of ```
fglrxinfo
```

---

### Post by -SpaZ on 2007-09-04
If you can't figure out what's wrong, there is just a minimal performance boost from 32 to 64 bit.

---

### Post by Kilz on 2007-09-04
> **-SpaZ said:**
> If you can't figure out what's wrong, there is just a minimal performance boost from 32 to 64 bit.

Do you count 30% as minimal? Some applications can have up to a 30% performance increase.

---

### Post by GumbyX on 2007-09-04
> **Kilz said:**
> Are you running the ati drivers from ATI or Ubuntu? If you have the ATI ones installes what is the results of ```
fglrxinfo
```

Actually, neither? This is what I get when I type "fglrxinfo" in terminal:
```
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
Make sure you have the 'restricted' component enabled
bash: fglrxinfo: command not found
```

I guess I am running the standard Ubuntu ATI drivers. Take it I should be installing the xorg fglrx drivers? For some reason I remember that I had problems with the ATI drivers when I first installed 7.04 64bit.......

I never noticed that xorg-driver-fglrx wasn't installed..... maybe it IS a graphic card driver issue.....

PS
> **Kilz said:**
> Do you count 30% as minimal? Some applications can have up to a 30% performance increase.
Ya that is why I want to stick with 64bit if I can.

---

### Post by -SpaZ on 2007-09-04
> **Kilz said:**
> Do you count 30% as minimal? Some applications can have up to a 30% performance increase.

_Some_ applications can have _up to_ a 30% boost.

---

### Post by Kilz on 2007-09-04
> **-SpaZ said:**
> _Some_ applications can have _up to_ a 30% boost.

Yep some as in cd rippers, video editing, backing up DVD's, 3d modeling. I know blenders 64bit version defiantly gets 30%. Then there is the overall faster feel and responsiveness that you get. There have been numerous posts from people after switching on the difference. Of course with the 32bit version you hobble your hardware and get a whopping 0% improvement.

---

### Post by GumbyX on 2007-09-04
> **Kilz said:**
> Yep some as in cd rippers, video editing, backing up DVD's, 3d modeling. Then there is the overall faster feel and responsiveness that you get. There have been numerous posts from people after switching on the difference. Of course with the 32bit version you hobble your hardware and get a whopping 0% improvement.

The video editing is where I need the help, which is why I am trying to stick with 64bit.

Anyway, would any of you recommends trying to install xorg-fglrx-driver or not?

---

### Post by Kilz on 2007-09-04
> **GumbyX said:**
> The video editing is where I need the help, which is why I am trying to stick with 64bit.

Anyway, would any of you recommends trying to install xorg-fglrx-driver or not?

Its worth a shot, but be warned ATI graphics drivers are a royal pain.  [This is how I got them installed.]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.40.4_Driver_Manually")

---

### Post by GumbyX on 2007-09-04
> **Kilz said:**
> Its worth a shot, but be warned ATI graphics drivers are a royal pain.  [This is how I got them installed.]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.40.4_Driver_Manually")

That is the walkthrough I tried before, and I couldn't get the system to boot (got past GRUB, but crashed when loading GNOME). :( It turned out that I had to use the drivers included in Ubuntu. I have to use the ati fglrx drivers on my laptop to get stuff to work, and have used this guide before. Here is a link to that [post]("http://ubuntuforums.org/showthread.php?t=488270").

---

### Post by Kilz on 2007-09-04
> **GumbyX said:**
> That is the walkthrough I tried before, and I couldn't get the system to boot (got past GRUB, but crashed when loading GNOME). :( It turned out that I had to use the drivers included in Ubuntu. I have to use the ati fglrx drivers on my laptop to get stuff to work, and have used this guide before. Here is a link to that [post]("http://ubuntuforums.org/showthread.php?t=488270").

You could also try [Envy to install them]("http://albertomilone.com/nvidia_scripts1.html"). I  have heard a few good things about it , and it will install ati drivers.

---

### Post by Jouke74 on 2007-09-05
Well faulty memory is excluded thus far...

To cut the usual 32 vs 64 bit discussion: He wants to save his current install. If he has to reinstall he can decide then...

ATI FGLRX driver. My install of this driver did work. No envy, no other obscure scripts. Simply go to the ubuntu restricted drivers menu in Gnome under administration. Open the restricted drivers program. Tick on your proprietary ATI drivers, wait for the download (you must be connected to the internet). This will install the FGLRX drivers and acompanying files services & libraries. It is not the newest FGLRX driver, but this one is tested and working with Ubuntu Feisty. (You will cripple your Ubuntu a bit because these drivers do not allow for direct 3D accelaration in combination with compiz + XGL). 

Probably after the first reboot it will give you a black screen. This is because the Xorg.conf file is not adjusted by fglrx yet. Simply reboot again and now it will probably work.

Another side point is that with your X700 you SHOULD be fine with the free UBuntu ATi drivers also... so probably it will not make much difference. But at least you can try.

---

### Post by GumbyX on 2007-09-05
> **Jouke74 said:**
> Well faulty memory is excluded thus far...

To cut the usual 32 vs 64 bit discussion: He wants to save his current install. If he has to reinstall he can decide then...

ATI FGLRX driver. My install of this driver did work. No envy, no other obscure scripts. Simply go to the ubuntu restricted drivers menu in Gnome under administration. Open the restricted drivers program. Tick on your proprietary ATI drivers, wait for the download (you must be connected to the internet). This will install the FGLRX drivers and acompanying files services & libraries. It is not the newest FGLRX driver, but this one is tested and working with Ubuntu Feisty. (You will cripple your Ubuntu a bit because these drivers do not allow for direct 3D accelaration in combination with compiz + XGL). 

Probably after the first reboot it will give you a black screen. This is because the Xorg.conf file is not adjusted by fglrx yet. Simply reboot again and now it will probably work.

Another side point is that with your X700 you SHOULD be fine with the free UBuntu ATi drivers also... so probably it will not make much difference. But at least you can try.

So if I use the ubuntu ATI FLGRX drivers, I won't be able to use Beryl or Compiz? That's not what I wanted to hear (been using Beryl since its release). Any other suggestions before I go do that?

PS Just thought of this: Would it work with AIGLX ? If so, I can still happily use Beryl (believe that is what I am using now actually).

Update: When I try to run the restricted driver manager, it says my hardware doesn't need any restriced drivers. After checking xorg.conf, I think it is already installed. Here is what I found in xorg.conf

```
Section "Device"
	Identifier	"ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSecti
```

I am a bit out of it right now (its 5 AM on my side of the world and can't get sleep), so I am not sure of this, but I think that is the standard Ubuntu ati driver. So I think I don't think it is the graphics driver, unless my card REALLY hates 
AIGLX.

Any other ideas guys?

BTW Thanks for trying to help me out. Last time I came by looking for help I didn't get any responses, so its nice to be able get some help with this.

---

### Post by Jouke74 on 2007-09-05
Your info says that you are using the free Ubuntu ATI (supporting AIGLX) driver for your card, and you are very right in keeping this the way it is. The FGLRX driver will not be installed by Ubuntu because, you  really don't want to use it, unles there is no alternative (like with my X1600 videocard). FGLRX cripples your current abilities drastically as AIGLX is not supported. 

(((If you would install the FGLRX driver. You subsequently need to install the XGL server to run Compiz (beryl I never tried). It will work, but with serious limitations.)))

The real problem, hanging your system, however remains... 
Did you try to run the Ubuntu live desktop cd for a while? This should be the disk you installed with, unless you used the alternate install cd? and what happened there? 

And what is the output of the following terminal commands when running your current system:

Lsmod

and

dmesg

---

### Post by GumbyX on 2007-09-05
> **Jouke74 said:**
> Your info says that you are using the free Ubuntu ATI (supporting AIGLX) driver for your card, and you are very right in keeping this the way it is. The FGLRX driver will not be installed by Ubuntu because, you  really don't want to use it, unles there is no alternative (like with my X1600 videocard). FGLRX cripples your current abilities drastically as AIGLX is not supported. 

(((If you would install the FGLRX driver. You subsequently need to install the XGL server to run Compiz (beryl I never tried). It will work, but with serious limitations.)))

The real problem, hanging your system, however remains... 
Did you try to run the Ubuntu live desktop cd for a while? This should be the disk you installed with, unless you used the alternate install cd? and what happened there? 

And what is the output of the following terminal commands when running your current system:

Lsmod

and

dmesg

lsmod:
```
Module                  Size  Used by
binfmt_misc            14604  1 
rfcomm                 45352  0 
l2cap                  28160  5 rfcomm
bluetooth              62468  4 rfcomm,l2cap
nfs                   263384  0 
vboxdrv              1631872  0 
nfsd                  266920  17 
exportfs                7808  1 nfsd
lockd                  73136  3 nfs,nfsd
sunrpc                184392  12 nfs,nfsd,lockd
ppdev                  11272  0 
radeon                126368  3 
drm                   103464  4 radeon
ipv6                  307456  10 
powernow_k8            16480  1 
cpufreq_userspace       6176  0 
cpufreq_powersave       3072  0 
cpufreq_conservative     9736  0 
cpufreq_ondemand       10640  1 
cpufreq_stats           8416  0 
freq_table              6336  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
dev_acpi               17028  0 
sony_acpi               7064  0 
pcc_acpi               15616  0 
tc1100_wmi              9224  0 
video                  19080  0 
container               6144  0 
button                 10016  0 
ac                      6920  0 
sbs                    17856  0 
i2c_ec                  6912  1 sbs
battery                12040  0 
asus_acpi              19756  0 
dock                   11992  0 
backlight               8448  1 asus_acpi
fuse                   51888  3 
lp                     15048  0 
joydev                 12928  0 
snd_atiixp             23572  1 
snd_ac97_codec        117848  1 snd_atiixp
ac97_bus                3968  1 snd_ac97_codec
snd_pcm_oss            49408  0 
snd_pcm                92808  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          19840  1 snd_pcm_oss
usb_storage            80448  0 
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
usbhid                 29088  0 
libusual               22184  1 usb_storage
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
hid                    34048  1 usbhid
usblp                  16768  0 
serio_raw               9092  0 
psmouse                43536  0 
ide_cd                 35104  0 
cdrom                  40744  1 ide_cd
snd                    68904  12 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         11792  2 snd_atiixp,snd_pcm
parport_pc             40104  1 
parport                43404  3 ppdev,lp,parport_pc
shpchp                 37404  0 
pci_hotplug            36228  1 shpchp
pcspkr                  4736  0 
af_packet              27020  4 
k8temp                  7552  0 
i2c_piix4              11148  0 
i2c_core               26496  2 i2c_ec,i2c_piix4
sbp2                   26628  1 
evdev                  13056  4 
tsdev                  10112  0 
8139cp                 27776  0 
ext3                  143760  1 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
sg                     40616  0 
sd_mod                 25092  5 
atiixp                  8208  0 [permanent]
ohci1394               38088  1 
ieee1394              369784  2 sbp2,ohci1394
8139too                30976  0 
mii                     7424  2 8139cp,8139too
ohci_hcd               24196  0 
ehci_hcd               37004  0 
sata_sil               15112  2 
ata_generic            10628  0 
usbcore               154416  7 usb_storage,usbhid,libusual,usblp,ohci_hcd,ehci_hcd
libata                137000  2 sata_sil,ata_generic
scsi_mod              166968  5 usb_storage,sbp2,sg,sd_mod,libata
generic                 6532  0 [permanent]
thermal                16912  0 
processor              34952  2 powernow_k8,thermal
fan                     6536  0 
fbcon                  44416  0 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0 
commoncap               9472  1 capability

```

dmesg:
```
[    0.000000] Linux version 2.6.20-16-generic (root@king) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Aug 30 23:16:15 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] Command line: root=UUID=b14b7660-36d0-40ac-9b8f-a6707310530a ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fef3000 - 000000003ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261872) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 HP-CPC                                ) @ 0x00000000000f85a0
[    0.000000] ACPI: RSDT (v001 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fef3040
[    0.000000] ACPI: FADT (v002 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fef30c0
[    0.000000] ACPI: SSDT (v001 HP-CPC POWERNOW 0x00000001  LTP 0x00000001) @ 0x000000003fef6d80
[    0.000000] ACPI: SRAT (v001 HP-CPC HAMMER   0x00000001 AMD  0x00000001) @ 0x000000003fef6f80
[    0.000000] ACPI: MCFG (v001 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fef7080
[    0.000000] ACPI: MADT (v001 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fef6cc0
[    0.000000] ACPI: DSDT (v001 HP-CPC AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] SRAT: PXM 0 -> APIC 0 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 1 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 0-a0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] SRAT: Node 0 PXM 0 0-40000000
[    0.000000] Entering add_active_range(0, 0, 159) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261872) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Bootmem setup node 0 0000000000000000-000000003fef0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   261872
[    0.000000] On node 0 totalpages: 261775
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1086 pages reserved
[    0.000000]   DMA zone: 2857 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3524 pages used for memmap
[    0.000000]   DMA32 zone: 254252 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000f0000
[    0.000000] Nosave address range: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 257109
[    0.000000] Kernel command line: root=UUID=b14b7660-36d0-40ac-9b8f-a6707310530a ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   24.285330] Console: colour VGA+ 80x25
[   24.285907] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.286737] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   24.286841] Checking aperture...
[   24.286844] CPU 0: aperture @ 0 size 32 MB
[   24.298264] No AGP bridge found
[   24.308073] Memory: 1019912k/1047488k available (2218k kernel code, 27188k reserved, 1162k data, 304k init)
[   24.386039] Calibrating delay using timer specific routine.. 3983.70 BogoMIPS (lpj=7967401)
[   24.386095] Security Framework v1.0.0 initialized
[   24.386102] SELinux:  Disabled at boot.
[   24.386125] Mount-cache hash table entries: 256
[   24.386268] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   24.386271] CPU: L2 Cache: 512K (64 bytes/line)
[   24.386274] CPU 0/0 -> Node 0
[   24.386276] CPU: Physical Processor ID: 0
[   24.386277] CPU: Processor Core ID: 0
[   24.386298] SMP alternatives: switching to UP code
[   24.386583] Early unpacking initramfs... done
[   24.681075] ACPI: Core revision 20060707
[   24.690065] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   24.741189] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   24.781237] Using local APIC timer interrupts.
[   24.831435] result 12436886
[   24.831437] Detected 12.436 MHz APIC timer.
[   24.833738] SMP alternatives: switching to SMP code
[   24.833819] Booting processor 1/2 APIC 0x1
[   24.842394] Initializing CPU#1
[   24.919729] Calibrating delay using timer specific routine.. 3982.50 BogoMIPS (lpj=7965009)
[   24.919736] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   24.919738] CPU: L2 Cache: 512K (64 bytes/line)
[   24.919740] CPU 1/1 -> Node 0
[   24.919742] CPU: Physical Processor ID: 0
[   24.919744] CPU: Processor Core ID: 1
[   24.919824] AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[   24.923746] CPU 1: Syncing TSC to CPU 0.
[   24.925530] CPU 1: synchronized TSC with CPU 0 (last diff -76 cycles, maxerr 544 cycles)
[   24.925540] Brought up 2 CPUs
[   24.925584] Disabling vsyscall due to use of PM timer
[   24.925587] time.c: Using 3.579545 MHz WALL PM GTOD PM timer.
[   24.925589] time.c: Detected 1989.899 MHz processor.
[   25.956124] migration_cost=243
[   25.956492] Time:  6:04:10  Date: 08/05/107
[   25.956531] NET: Registered protocol family 16
[   25.956613] ACPI: bus type pci registered
[   25.956620] PCI: Using configuration type 1
[   25.969199] ACPI: Interpreter enabled
[   25.969202] ACPI: Using IOAPIC for interrupt routing
[   25.969816] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.969821] PCI: Probing PCI hardware (bus 00)
[   25.969918] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   25.970875] Boot video device is 0000:01:00.0
[   25.971326] PCI: Transparent bridge - 0000:00:14.4
[   25.971365] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.989057] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.989257] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.989455] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.989653] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.989848] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11)
[   25.990047] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11)
[   25.990242] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11), disabled.
[   25.990439] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   25.990774] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   25.992902] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.992913] pnp: PnP ACPI init
[   25.995318] pnp: PnP ACPI: found 10 devices
[   25.995379] PCI: Using ACPI for IRQ routing
[   25.995382] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.995393] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   25.995489] NET: Registered protocol family 8
[   25.995491] NET: Registered protocol family 20
[   25.995993] pnp: 00:01: ioport range 0x228-0x22f has been reserved
[   25.995996] pnp: 00:01: ioport range 0x40b-0x40b has been reserved
[   25.996000] pnp: 00:01: ioport range 0x4d6-0x4d6 has been reserved
[   25.996003] pnp: 00:01: ioport range 0xc00-0xc01 has been reserved
[   25.996006] pnp: 00:01: ioport range 0xc14-0xc14 has been reserved
[   25.996009] pnp: 00:01: ioport range 0xc50-0xc52 has been reserved
[   25.996011] pnp: 00:01: ioport range 0xc6c-0xc6d has been reserved
[   25.996014] pnp: 00:01: ioport range 0xc6f-0xc6f has been reserved
[   25.996338] PCI: Bridge: 0000:00:02.0
[   25.996341]   IO window: e000-efff
[   25.996345]   MEM window: fdd00000-fddfffff
[   25.996348]   PREFETCH window: d0000000-dfffffff
[   25.996352] PCI: Bridge: 0000:00:14.4
[   25.996356]   IO window: d000-dfff
[   25.996363]   MEM window: fdc00000-fdcfffff
[   25.996368]   PREFETCH window: fde00000-fdefffff
[   25.996383] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   25.996435] NET: Registered protocol family 2
[   26.052174] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   26.052389] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   26.053505] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   26.054052] TCP: Hash tables configured (established 131072 bind 65536)
[   26.054056] TCP reno registered
[   26.068228] checking if image is initramfs... it is
[   26.651890] Freeing initrd memory: 6824k freed
[   26.656649] audit: initializing netlink socket (disabled)
[   26.656664] audit(1188972250.288:1): initialized
[   26.656854] VFS: Disk quotas dquot_6.5.1
[   26.656873] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   26.656921] io scheduler noop registered
[   26.656923] io scheduler anticipatory registered
[   26.656925] io scheduler deadline registered
[   26.656939] io scheduler cfq registered (default)
[   26.707503] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   26.707521] assign_interrupt_mode Found MSI capability
[   26.707525] Allocate Port Service[0000:00:02.0:pcie00]
[   26.732216] Real Time Clock Driver v1.12ac
[   26.732256] Linux agpgart interface v0.102 (c) Dave Jones
[   26.732259] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.732836] mice: PS/2 mouse device common for all mice
[   26.733428] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.733582] input: Macintosh mouse button emulation as /class/input/input0
[   26.733616] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   26.733620] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   26.733931] PNP: No PS/2 controller found. Probing ports directly.
[   26.736882] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.736889] serio: i8042 AUX port at 0x60,0x64 irq 12
[   26.736993] TCP cubic registered
[   26.737003] NET: Registered protocol family 1
[   26.737134] ACPI: (supports S0 S1 S3 S4 S5)
[   26.737179]   Magic number: 7:539:63
[   26.737297] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   26.737368] Freeing unused kernel memory: 304k freed
[   27.916918] Capability LSM initialized
[   28.009241] ACPI: Processor [CPU0] (supports 8 throttling states)
[   28.009258] ACPI: Processor [CPU1] (supports 8 throttling states)
[   28.484803] SCSI subsystem initialized
[   28.491097] libata version 2.20 loaded.
[   28.597581] sata_sil 0000:00:12.0: version 2.2
[   28.597611] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
[   28.597697] ata1: SATA max UDMA/100 cmd 0xffffc20000004080 ctl 0xffffc2000000408a bmdma 0xffffc20000004000 irq 22
[   28.597729] ata2: SATA max UDMA/100 cmd 0xffffc200000040c0 ctl 0xffffc200000040ca bmdma 0xffffc20000004008 irq 22
[   28.597744] scsi0 : sata_sil
[   28.599750] usbcore: registered new interface driver usbfs
[   28.600094] usbcore: registered new interface driver hub
[   28.600464] usbcore: registered new device driver usb
[   28.602593] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   28.604068] 8139too Fast Ethernet driver 0.9.28
[   28.610344] ieee1394: Initialized config rom entry `ip1394'
[   29.072550] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   29.084974] ata1.00: ATA-7: HDT722525DLA380, V44OA80A, max UDMA/100
[   29.084977] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   29.096955] ata1.00: configured for UDMA/100
[   29.096969] scsi1 : sata_sil
[   29.567961] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   29.595557] ata2.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[   29.595562] ata2.00: ATA-7: WDC WD1600AAJS-55PSA0, 05.06H05, max UDMA/133
[   29.595565] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   29.605203] ata2.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[   29.605207] ata2.00: configured for UDMA/100
[   29.605313] scsi 0:0:0:0: Direct-Access     ATA      HDT722525DLA380  V44O PQ: 0 ANSI: 5
[   29.606008] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-5 05.0 PQ: 0 ANSI: 5
[   29.606696] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   29.606714] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   29.606983] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[   29.607045] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe02c000
[   29.607057] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.608230] usb usb1: configuration #1 chosen from 1 choice
[   29.608423] hub 1-0:1.0: USB hub found
[   29.608433] hub 1-0:1.0: 8 ports detected
[   29.615999] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   29.619913] sda: Write Protect is off
[   29.619915] sda: Mode Sense: 00 3a 00 00
[   29.623909] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.627910] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   29.627979] sda: Write Protect is off
[   29.627981] sda: Mode Sense: 00 3a 00 00
[   29.631974] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.631977]  sda: sda1 sda2
[   29.641188] sd 0:0:0:0: Attached scsi disk sda
[   29.643879] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[   29.643893] sdb: Write Protect is off
[   29.643895] sdb: Mode Sense: 00 3a 00 00
[   29.643916] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.643975] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[   29.643983] sdb: Write Protect is off
[   29.643985] sdb: Mode Sense: 00 3a 00 00
[   29.643997] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.644002]  sdb: sdb1 sdb2 < sdb5 >
[   29.687542] sd 1:0:0:0: Attached scsi disk sdb
[   29.691059] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   29.691080] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   29.716062] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   29.716081] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   29.716105] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[   29.716124] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfe02e000
[   29.779816] usb usb2: configuration #1 chosen from 1 choice
[   29.779843] hub 2-0:1.0: USB hub found
[   29.779856] hub 2-0:1.0: 4 ports detected
[   29.887675] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   29.887695] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   29.887721] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[   29.887739] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfe02d000
[   29.927420] Attempting manual resume
[   29.927424] swsusp: Resume From Partition 8:21
[   29.927426] PM: Checking swsusp image.
[   29.927654] PM: Resume from disk failed.
[   29.951603] usb usb3: configuration #1 chosen from 1 choice
[   29.951632] hub 3-0:1.0: USB hub found
[   29.951644] hub 3-0:1.0: 4 ports detected
[   29.958085] EXT3-fs: INFO: recovery required on readonly filesystem.
[   29.958089] EXT3-fs: write access will be enabled during recovery.
[   30.059637] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[   30.059879] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   30.059912] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   30.059929] ATIIXP: chipset revision 0
[   30.059931] ATIIXP: not 100% native mode: will probe irqs later
[   30.059952]     ide0: BM-DMA at 0xf800-0xf807, BIOS settings: hda:pio, hdb:pio
[   30.059985]     ide1: BM-DMA at 0xf808-0xf80f, BIOS settings: hdc:pio, hdd:pio
[   30.059999] Probing IDE interface ide0...
[   30.060589] eth0: RealTek RTL8139 at 0xffffc20000032000, 00:13:d3:55:a3:04, IRQ 20
[   30.060592] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   30.068977] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   30.578714] usb 2-1: new full speed USB device using ohci_hcd and address 2
[   30.606476] kjournald starting.  Commit interval 5 seconds
[   30.606490] EXT3-fs: sdb1: orphan cleanup on readonly fs
[   30.630730] Probing IDE interface ide1...
[   30.634379] ext3_orphan_cleanup: deleting unreferenced inode 5934522
[   30.636587] ext3_orphan_cleanup: deleting unreferenced inode 5934521
[   30.648340] ext3_orphan_cleanup: deleting unreferenced inode 5934519
[   30.656497] ext3_orphan_cleanup: deleting unreferenced inode 5934518
[   30.663342] EXT3-fs: sdb1: 4 orphan inodes deleted
[   30.663344] EXT3-fs: recovery complete.
[   30.696372] EXT3-fs: mounted filesystem with ordered data mode.
[   30.777554] usb 2-1: configuration #1 chosen from 1 choice
[   31.086109] usb 3-2: new full speed USB device using ohci_hcd and address 2
[   31.290927] usb 3-2: configuration #1 chosen from 1 choice
[   31.370284] hdc: HP DVD Writer 740b, ATAPI CD/DVD-ROM drive
[   31.597513] usb 3-4: new full speed USB device using ohci_hcd and address 3
[   31.798308] usb 3-4: configuration #1 chosen from 1 choice
[   32.157361] hdd: IDE-DVD DROM6216, ATAPI CD/DVD-ROM drive
[   32.218473] ide1 at 0x170-0x177,0x376 on irq 15
[   32.221691] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 21
[   32.275033] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fdcfd000-fdcfd7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   33.559364] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[   33.836552] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0001a3940006147f]
[   33.836684] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[0010dc0000b7ac42]
[   39.867928] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   40.367923] scsi2 : SBP-2 IEEE-1394
[   41.328772] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   41.382469] ieee1394: sbp2: Logged into SBP-2 device
[   41.382584] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[   41.383437] scsi 2:0:0:0: Direct-Access     WDC WD32 00JB-00KFA0      0.01 PQ: 0 ANSI: 0
[   41.384000] SCSI device sdc: 625142448 512-byte hdwr sectors (320073 MB)
[   41.384207] sdc: Write Protect is off
[   41.384209] sdc: Mode Sense: 03 00 00 00
[   41.384659] sdc: got wrong page
[   41.384663] sdc: assuming drive cache: write through
[   41.385140] SCSI device sdc: 625142448 512-byte hdwr sectors (320073 MB)
[   41.385412] sdc: Write Protect is off
[   41.385415] sdc: Mode Sense: 03 00 00 00
[   41.385987] sdc: got wrong page
[   41.385991] sdc: assuming drive cache: write through
[   41.386030]  sdc: sdc1
[   41.386980] sd 2:0:0:0: Attached scsi disk sdc
[   41.387032] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   41.471510] NET: Registered protocol family 17
[   41.553194] input: PC Speaker as /class/input/input1
[   41.613120] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.618185] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.680970] parport: PnPBIOS parport detected.
[   41.681015] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   41.766194] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   41.766202] Uniform CD-ROM driver Revision: 3.20
[   41.770424] hdd: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[   42.016279] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
[   42.016297] usbcore: registered new interface driver usblp
[   42.016300] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   42.221013] usbcore: registered new interface driver libusual
[   42.227910] usbcore: registered new interface driver hiddev
[   42.251703] Initializing USB Mass Storage driver...
[   42.283375] input: Logitech USB Receiver as /class/input/input2
[   42.283418] input: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:13.1-2
[   42.288466] input: Logitech USB Receiver as /class/input/input3
[   42.288596] input,hiddev96: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.1-2
[   42.288664] scsi3 : SCSI emulation for USB Mass Storage devices
[   42.288729] usbcore: registered new interface driver usb-storage
[   42.288732] USB Mass Storage support registered.
[   42.288897] usbcore: registered new interface driver usbhid
[   42.288900] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   42.288980] usb-storage: device found at 3
[   42.288982] usb-storage: waiting for device to settle before scanning
[   42.351446] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   42.568471] lp0: using parport0 (interrupt-driven).
[   42.672488] fuse init (API version 7.8)
[   42.726086] Adding 3004112k swap on /dev/disk/by-uuid/5ac1181b-12b7-4a91-a7a8-ee8bf004bf9d.  Priority:-1 extents:1 across:3004112k
[   42.892292] EXT3 FS on sdb1, internal journal
[   46.942426] No dock devices found.
[   47.031059] input: Power Button (FF) as /class/input/input4
[   47.031370] ACPI: Power Button (FF) [PWRF]
[   47.047253] input: Power Button (CM) as /class/input/input5
[   47.047509] ACPI: Power Button (CM) [PWRB]
[   47.093984] ibm_acpi: ec object not found
[   47.137133] Using specific hotkey driver
[   47.226928] pcc_acpi: loading...
[   47.283259] usb-storage: device scan complete
[   47.290123] scsi 3:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   47.295334] scsi 3:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   47.302103] scsi 3:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   47.307318] scsi 3:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   47.329126] sd 3:0:0:0: Attached scsi removable disk sdd
[   47.329173] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   47.338960] sd 3:0:0:1: Attached scsi removable disk sde
[   47.339004] sd 3:0:0:1: Attached scsi generic sg4 type 0
[   47.349112] sd 3:0:0:2: Attached scsi removable disk sdf
[   47.349155] sd 3:0:0:2: Attached scsi generic sg5 type 0
[   47.358937] sd 3:0:0:3: Attached scsi removable disk sdg
[   47.358991] sd 3:0:0:3: Attached scsi generic sg6 type 0
[   47.702435] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (version 2.00.00)
[   47.722554] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x8
[   47.722558] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xa
[   47.722561] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   61.203159] NET: Registered protocol family 10
[   61.203271] lo: Disabled Privacy Extensions
[   65.435278] [drm] Initialized drm 1.1.0 20060810
[   65.462701] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   65.463061] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   66.297700] ppdev: user-space parallel port driver
[   66.643658] [drm] Setting GART location based on new memory map
[   66.644114] [drm] Loading R300 Microcode
[   66.644147] [drm] writeback test succeeded in 1 usecs
[   67.596076] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   67.743181] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   67.743679] NFSD: starting 90-second grace period
[   68.684078] vboxdrv: Trying to deactivate NMI watchdog permanently...
[   68.684083] vboxdrv: Successfully done.
[   69.242676] Bluetooth: Core ver 2.11
[   69.242729] NET: Registered protocol family 31
[   69.242731] Bluetooth: HCI device and connection manager initialized
[   69.242734] Bluetooth: HCI socket layer initialized
[   69.257879] Bluetooth: L2CAP ver 2.8
[   69.257882] Bluetooth: L2CAP socket layer initialized
[   69.260401] Bluetooth: RFCOMM socket layer initialized
[   69.260414] Bluetooth: RFCOMM TTY layer initialized
[   69.260416] Bluetooth: RFCOMM ver 1.8
[   74.081405] eth0: no IPv6 routers present
[  382.442126] APIC error on CPU0: 00(40)
[  844.783701] APIC error on CPU0: 40(40)
[ 1278.086887] APIC error on CPU0: 40(40)

```

I used to get warning messages about APIC on boot, but since a kernel update, I no longer saw it, so I thought it was fixed. Guess not. Anyone know how I investigate these APIC errors in more detail?

About the live cd: I can't use the AMD64 live cd on my pc. For some reason it will not boot. It is a known issue with my graphics card. There used to be a thread about this problem/

---

### Post by GumbyX on 2007-09-05
I think this got lost underneath the day's posts. I am still in need of help if anyone can help me out. Would appreciate it.

---

### Post by JBAlaska on 2007-09-06
I remember seeing a bug report about this problem (Or one very similar) that seemed to be cured by adding the kernel boot option "irqpoll" in grub.

I did some checking around and found the original thread [Here](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/66900), The resolution is near the bottom of the thread.
Hope this helps or points you in the right direction

---

### Post by Jouke74 on 2007-09-06
Yep, add the NOACPI to grub might also be an option.

---

### Post by GumbyX on 2007-09-06
> **Jouke74 said:**
> Yep, add the NOACPI to grub might also be an option.

NOACPI caused Ubuntu to not load at all last time I tired it. Thanks for the heads up though. Might try it again and see what happens.

@JBAlaska:
Thanks for pointing me in the right direction. Looks like it might be a BIOS issue. Also, if I add " irqpoll" to the boot options in GRUB, that might work too. I am going to try it right now and see what happens. Also going to check the HP website to see if there is a BIOS upgrade that I can install.

Update: Looks like there is a BIOS update. Looks like I'll be booting into WIndows to install it later. Going to try this " irqpoll" GRUB option first though

Update: irqpoll caused a kernel panic.
Upgraded BIOS here is the results of dmesg

```
[    0.000000] Linux version 2.6.20-16-generic (root@king) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Aug 30 23:16:15 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] Command line: root=UUID=b14b7660-36d0-40ac-9b8f-a6707310530a ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fef3000 - 000000003ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261872) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 HP-CPC                                ) @ 0x00000000000f8650
[    0.000000] ACPI: RSDT (v001 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fef3040
[    0.000000] ACPI: FADT (v002 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fef30c0
[    0.000000] ACPI: SSDT (v001 HP-CPC POWERNOW 0x00000001  LTP 0x00000001) @ 0x000000003fef6f40
[    0.000000] ACPI: MCFG (v001 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fef7140
[    0.000000] ACPI: MADT (v001 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fef6e80
[    0.000000] ACPI: DSDT (v001 HP-CPC AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003fef0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261872) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003fef0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   261872
[    0.000000] On node 0 totalpages: 261775
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1086 pages reserved
[    0.000000]   DMA zone: 2857 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3524 pages used for memmap
[    0.000000]   DMA32 zone: 254252 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000f0000
[    0.000000] Nosave address range: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 257109
[    0.000000] Kernel command line: root=UUID=b14b7660-36d0-40ac-9b8f-a6707310530a ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   35.695160] Console: colour VGA+ 80x25
[   35.695740] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   35.696569] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   35.696673] Checking aperture...
[   35.696677] CPU 0: aperture @ 20000000 size 32 MB
[   35.696678] Aperture too small (32 MB)
[   35.708100] No AGP bridge found
[   35.717910] Memory: 1019912k/1047488k available (2218k kernel code, 27188k reserved, 1162k data, 304k init)
[   35.795872] Calibrating delay using timer specific routine.. 3983.57 BogoMIPS (lpj=7967156)
[   35.795929] Security Framework v1.0.0 initialized
[   35.795935] SELinux:  Disabled at boot.
[   35.795959] Mount-cache hash table entries: 256
[   35.796102] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   35.796105] CPU: L2 Cache: 512K (64 bytes/line)
[   35.796107] CPU 0/0 -> Node 0
[   35.796110] CPU: Physical Processor ID: 0
[   35.796111] CPU: Processor Core ID: 0
[   35.796131] SMP alternatives: switching to UP code
[   35.796418] Early unpacking initramfs... done
[   36.090861] ACPI: Core revision 20060707
[   36.099851] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   36.151035] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   36.191082] Using local APIC timer interrupts.
[   36.241279] result 12436789
[   36.241281] Detected 12.436 MHz APIC timer.
[   36.243570] SMP alternatives: switching to SMP code
[   36.243652] Booting processor 1/2 APIC 0x1
[   36.252015] Initializing CPU#1
[   36.329351] Calibrating delay using timer specific routine.. 3981.79 BogoMIPS (lpj=7963585)
[   36.329358] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   36.329360] CPU: L2 Cache: 512K (64 bytes/line)
[   36.329363] CPU 1/1 -> Node 0
[   36.329364] CPU: Physical Processor ID: 0
[   36.329366] CPU: Processor Core ID: 1
[   36.329446] AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[   36.333369] CPU 1: Syncing TSC to CPU 0.
[   36.335364] CPU 1: synchronized TSC with CPU 0 (last diff -76 cycles, maxerr 544 cycles)
[   36.335374] Brought up 2 CPUs
[   36.335416] Disabling vsyscall due to use of PM timer
[   36.335419] time.c: Using 3.579545 MHz WALL PM GTOD PM timer.
[   36.335421] time.c: Detected 1989.884 MHz processor.
[   37.366041] migration_cost=247
[   37.366409] Time:  7:54:24  Date: 08/06/107
[   37.366448] NET: Registered protocol family 16
[   37.366530] ACPI: bus type pci registered
[   37.366537] PCI: Using configuration type 1
[   37.379286] ACPI: Interpreter enabled
[   37.379289] ACPI: Using IOAPIC for interrupt routing
[   37.379906] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   37.379910] PCI: Probing PCI hardware (bus 00)
[   37.380011] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   37.380968] Boot video device is 0000:01:00.0
[   37.381420] PCI: Transparent bridge - 0000:00:14.4
[   37.381459] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   37.399480] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   37.399706] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   37.399929] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   37.400151] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   37.400371] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11)
[   37.400594] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11)
[   37.400814] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11), disabled.
[   37.401036] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   37.401390] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   37.403664] Linux Plug and Play Support v0.97 (c) Adam Belay
[   37.403676] pnp: PnP ACPI init
[   37.406114] pnp: PnP ACPI: found 10 devices
[   37.406176] PCI: Using ACPI for IRQ routing
[   37.406179] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   37.406190] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   37.406287] NET: Registered protocol family 8
[   37.406289] NET: Registered protocol family 20
[   37.406801] pnp: 00:01: ioport range 0x228-0x22f has been reserved
[   37.406804] pnp: 00:01: ioport range 0x40b-0x40b has been reserved
[   37.406807] pnp: 00:01: ioport range 0x4d6-0x4d6 has been reserved
[   37.406810] pnp: 00:01: ioport range 0xc00-0xc01 has been reserved
[   37.406813] pnp: 00:01: ioport range 0xc14-0xc14 has been reserved
[   37.406816] pnp: 00:01: ioport range 0xc50-0xc52 has been reserved
[   37.406819] pnp: 00:01: ioport range 0xc6c-0xc6d has been reserved
[   37.406821] pnp: 00:01: ioport range 0xc6f-0xc6f has been reserved
[   37.407120] PCI: Bridge: 0000:00:02.0
[   37.407123]   IO window: e000-efff
[   37.407127]   MEM window: fdd00000-fddfffff
[   37.407130]   PREFETCH window: d0000000-dfffffff
[   37.407134] PCI: Bridge: 0000:00:14.4
[   37.407138]   IO window: d000-dfff
[   37.407144]   MEM window: fdc00000-fdcfffff
[   37.407150]   PREFETCH window: fde00000-fdefffff
[   37.407164] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   37.407219] NET: Registered protocol family 2
[   37.446027] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   37.446242] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   37.447357] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   37.447904] TCP: Hash tables configured (established 131072 bind 65536)
[   37.447908] TCP reno registered
[   37.462078] checking if image is initramfs... it is
[   38.044920] Freeing initrd memory: 6824k freed
[   38.049685] audit: initializing netlink socket (disabled)
[   38.049699] audit(1189065264.272:1): initialized
[   38.049888] VFS: Disk quotas dquot_6.5.1
[   38.049908] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   38.049956] io scheduler noop registered
[   38.049958] io scheduler anticipatory registered
[   38.049960] io scheduler deadline registered
[   38.049974] io scheduler cfq registered (default)
[   38.101355] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   38.101374] assign_interrupt_mode Found MSI capability
[   38.101377] Allocate Port Service[0000:00:02.0:pcie00]
[   38.125997] Real Time Clock Driver v1.12ac
[   38.126037] Linux agpgart interface v0.102 (c) Dave Jones
[   38.126040] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   38.126590] mice: PS/2 mouse device common for all mice
[   38.127165] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   38.127317] input: Macintosh mouse button emulation as /class/input/input0
[   38.127351] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   38.127354] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   38.127662] PNP: No PS/2 controller found. Probing ports directly.
[   38.130603] serio: i8042 KBD port at 0x60,0x64 irq 1
[   38.130610] serio: i8042 AUX port at 0x60,0x64 irq 12
[   38.130716] TCP cubic registered
[   38.130727] NET: Registered protocol family 1
[   38.130857] ACPI: (supports S0 S1 S3 S4 S5)
[   38.130904]   Magic number: 7:100:925
[   38.130976]   hash matches device ptyxa
[   38.131023] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   38.131099] Freeing unused kernel memory: 304k freed
[   39.310408] Capability LSM initialized
[   39.394867] ACPI: Processor [CPU0] (supports 8 throttling states)
[   39.394883] ACPI: Processor [CPU1] (supports 8 throttling states)
[   39.855667] usbcore: registered new interface driver usbfs
[   39.855692] usbcore: registered new interface driver hub
[   39.859816] usbcore: registered new device driver usb
[   39.860655] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   39.860695] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   39.860712] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   39.860834] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   39.860856] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfe02e000
[   39.931209] usb usb1: configuration #1 chosen from 1 choice
[   39.931236] hub 1-0:1.0: USB hub found
[   39.931249] hub 1-0:1.0: 4 ports detected
[   39.999022] 8139too Fast Ethernet driver 0.9.28
[   40.006147] ieee1394: Initialized config rom entry `ip1394'
[   40.039594] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   40.039616] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   40.039648] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[   40.039707] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe02c000
[   40.039719] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   40.039803] usb usb2: configuration #1 chosen from 1 choice
[   40.039830] hub 2-0:1.0: USB hub found
[   40.039837] hub 2-0:1.0: 8 ports detected
[   40.146968] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   40.146987] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   40.146998] ATIIXP: chipset revision 0
[   40.147000] ATIIXP: not 100% native mode: will probe irqs later
[   40.147009]     ide0: BM-DMA at 0xf800-0xf807, BIOS settings: hda:pio, hdb:pio
[   40.147024]     ide1: BM-DMA at 0xf808-0xf80f, BIOS settings: hdc:pio, hdd:pio
[   40.147034] Probing IDE interface ide0...
[   40.718103] Probing IDE interface ide1...
[   41.065665] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   41.264497] usb 1-1: configuration #1 chosen from 1 choice
[   41.457657] hdc: HP DVD Writer 740b, ATAPI CD/DVD-ROM drive
[   42.244731] hdd: IDE-DVD DROM6216, ATAPI CD/DVD-ROM drive
[   42.305900] ide1 at 0x170-0x177,0x376 on irq 15
[   42.310036] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   42.310056] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   42.310221] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[   42.310240] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfe02d000
[   42.372781] usb usb3: configuration #1 chosen from 1 choice
[   42.373031] hub 3-0:1.0: USB hub found
[   42.373045] hub 3-0:1.0: 4 ports detected
[   42.482841] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[   42.483740] eth0: RealTek RTL8139 at 0xffffc20000074000, 00:13:d3:55:a3:04, IRQ 20
[   42.483742] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   42.483784] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 21
[   42.535420] SCSI subsystem initialized
[   42.543039] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fdcfd000-fdcfd7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   42.549286] libata version 2.20 loaded.
[   42.552098] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   42.553730] sata_sil 0000:00:12.0: version 2.2
[   42.553760] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
[   42.553834] ata1: SATA max UDMA/100 cmd 0xffffc2000003e080 ctl 0xffffc2000003e08a bmdma 0xffffc2000003e000 irq 22
[   42.553865] ata2: SATA max UDMA/100 cmd 0xffffc2000003e0c0 ctl 0xffffc2000003e0ca bmdma 0xffffc2000003e008 irq 22
[   42.553880] scsi0 : sata_sil
[   42.580205] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   42.580214] Uniform CD-ROM driver Revision: 3.20
[   42.585112] hdd: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[   43.023428] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   43.035854] ata1.00: ATA-7: HDT722525DLA380, V44OA80A, max UDMA/100
[   43.035857] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   43.047773] ata1.00: configured for UDMA/100
[   43.047857] scsi1 : sata_sil
[   43.111225] usb 3-2: new full speed USB device using ohci_hcd and address 2
[   43.316062] usb 3-2: configuration #1 chosen from 1 choice
[   43.518848] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   43.547073] ata2.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[   43.547080] ata2.00: ATA-7: WDC WD1600AAJS-55PSA0, 05.06H05, max UDMA/133
[   43.547083] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   43.559604] ata2.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[   43.559608] ata2.00: configured for UDMA/100
[   43.562893] scsi 0:0:0:0: Direct-Access     ATA      HDT722525DLA380  V44O PQ: 0 ANSI: 5
[   43.566887] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-5 05.0 PQ: 0 ANSI: 5
[   43.572921] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   43.572935] sda: Write Protect is off
[   43.572937] sda: Mode Sense: 00 3a 00 00
[   43.572952] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.573005] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   43.573013] sda: Write Protect is off
[   43.573015] sda: Mode Sense: 00 3a 00 00
[   43.573027] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.573030]  sda: sda1 sda2
[   43.585805] sd 0:0:0:0: Attached scsi disk sda
[   43.586780] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[   43.590648] sdb: Write Protect is off
[   43.590650] sdb: Mode Sense: 00 3a 00 00
[   43.594644] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.598640] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[   43.598765] sdb: Write Protect is off
[   43.598767] sdb: Mode Sense: 00 3a 00 00
[   43.602761] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.602764]  sdb: sdb1 sdb2 <<6>usb 3-4: new full speed USB device using ohci_hcd and address 3
[   43.647203]  sdb5 >
[   43.647278] sd 1:0:0:0: Attached scsi disk sdb
[   43.651516] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   43.651543] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   43.823437] usb 3-4: configuration #1 chosen from 1 choice
[   43.825541] usbcore: registered new interface driver hiddev
[   43.828110] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0001a3940006147f]
[   43.828232] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[0010dc0000b7ac42]
[   43.829486] input: Logitech USB Receiver as /class/input/input1
[   43.829503] input: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:13.1-2
[   43.834541] input: Logitech USB Receiver as /class/input/input2
[   43.834600] input,hiddev96: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.1-2
[   43.834744] usbcore: registered new interface driver usbhid
[   43.834751] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   43.835077] usbcore: registered new interface driver libusual
[   43.838884] Initializing USB Mass Storage driver...
[   43.838967] scsi2 : SCSI emulation for USB Mass Storage devices
[   43.839031] usbcore: registered new interface driver usb-storage
[   43.839034] USB Mass Storage support registered.
[   43.839161] usb-storage: device found at 3
[   43.839163] usb-storage: waiting for device to settle before scanning
[   43.905546] Attempting manual resume
[   43.905550] swsusp: Resume From Partition 8:21
[   43.905552] PM: Checking swsusp image.
[   43.905801] PM: Resume from disk failed.
[   43.971942] kjournald starting.  Commit interval 5 seconds
[   43.971954] EXT3-fs: mounted filesystem with ordered data mode.
[   43.993290] scsi3 : SBP-2 IEEE-1394
[   45.005383] ieee1394: sbp2: Logged into SBP-2 device
[   45.005489] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[   45.006189] scsi 3:0:0:0: Direct-Access     WDC WD32 00JB-00KFA0      0.01 PQ: 0 ANSI: 0
[   45.006643] SCSI device sdc: 625142448 512-byte hdwr sectors (320073 MB)
[   45.006862] sdc: Write Protect is off
[   45.006864] sdc: Mode Sense: 03 00 00 00
[   45.007341] sdc: got wrong page
[   45.007344] sdc: assuming drive cache: write through
[   45.007838] SCSI device sdc: 625142448 512-byte hdwr sectors (320073 MB)
[   45.008085] sdc: Write Protect is off
[   45.008087] sdc: Mode Sense: 03 00 00 00
[   45.008586] sdc: got wrong page
[   45.008588] sdc: assuming drive cache: write through
[   45.008592]  sdc: sdc1
[   45.009400] sd 3:0:0:0: Attached scsi disk sdc
[   45.009435] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   48.837197] usb-storage: device scan complete
[   48.843157] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   48.849147] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   48.855139] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   48.861129] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   48.871149] sd 2:0:0:0: Attached scsi removable disk sdd
[   48.871184] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   48.881128] sd 2:0:0:1: Attached scsi removable disk sde
[   48.881155] sd 2:0:0:1: Attached scsi generic sg4 type 0
[   48.891125] sd 2:0:0:2: Attached scsi removable disk sdf
[   48.891154] sd 2:0:0:2: Attached scsi generic sg5 type 0
[   48.901101] sd 2:0:0:3: Attached scsi removable disk sdg
[   48.901127] sd 2:0:0:3: Attached scsi generic sg6 type 0
[   52.680677] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   54.648850] NET: Registered protocol family 17
[   54.847347] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   55.010166] input: PC Speaker as /class/input/input3
[   55.149131] parport: PnPBIOS parport detected.
[   55.149185] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   55.153539] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   55.233628] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   55.474824] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
[   55.474842] usbcore: registered new interface driver usblp
[   55.474850] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   55.570268] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   55.778907] lp0: using parport0 (interrupt-driven).
[   55.882964] fuse init (API version 7.8)
[   55.937401] Adding 3004112k swap on /dev/disk/by-uuid/5ac1181b-12b7-4a91-a7a8-ee8bf004bf9d.  Priority:-1 extents:1 across:3004112k
[   56.102974] EXT3 FS on sdb1, internal journal
[   60.386005] No dock devices found.
[   60.477651] input: Power Button (FF) as /class/input/input4
[   60.477913] ACPI: Power Button (FF) [PWRF]
[   60.501281] input: Power Button (CM) as /class/input/input5
[   60.501326] ACPI: Power Button (CM) [PWRB]
[   60.529037] ibm_acpi: ec object not found
[   60.570848] Using specific hotkey driver
[   60.659384] pcc_acpi: loading...
[   61.022287] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (version 2.00.00)
[   61.037899] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x8
[   61.037904] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xa
[   61.037907] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   65.575033] NET: Registered protocol family 10
[   65.575153] lo: Disabled Privacy Extensions
[   78.570983] [drm] Initialized drm 1.1.0 20060810
[   78.598417] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   78.598814] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   79.406206] ppdev: user-space parallel port driver
[   79.754338] [drm] Setting GART location based on new memory map
[   79.754715] [drm] Loading R300 Microcode
[   79.754745] [drm] writeback test succeeded in 1 usecs
[   80.678034] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   80.828714] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   80.829198] NFSD: starting 90-second grace period
[   81.790756] vboxdrv: Trying to deactivate NMI watchdog permanently...
[   81.790761] vboxdrv: Successfully done.
[   82.352982] Bluetooth: Core ver 2.11
[   82.353034] NET: Registered protocol family 31
[   82.353036] Bluetooth: HCI device and connection manager initialized
[   82.353040] Bluetooth: HCI socket layer initialized
[   82.362477] Bluetooth: L2CAP ver 2.8
[   82.362481] Bluetooth: L2CAP socket layer initialized
[   82.392318] Bluetooth: RFCOMM socket layer initialized
[   82.392330] Bluetooth: RFCOMM TTY layer initialized
[   82.392332] Bluetooth: RFCOMM ver 1.8
[   83.933161] eth0: no IPv6 routers present
[  110.628461] APIC error on CPU0: 0
```

Looks like the BIOS upgrade solved about 3 of those APIC errors. One left though. Going to have to see if I still have the crashing errors. If I do, I am at a loss of what to do other then reinstall and hope it was a software issue.

---

### Post by Jouke74 on 2007-09-06
What worries me actually, but I don't have a solve for it, is that only CPU0 has an APIC error.

Why would CPU1, which is the same processor not have this problem? 
Are you actually using both cores?

Another straw to grasp here: Maybe you could try to disable cool n quiet in the BIOS?

---

### Post by GumbyX on 2007-09-06
> **Jouke74 said:**
> What worries me actually, but I don't have a solve for it, is that only CPU0 has an APIC error.

Why would CPU1, which is the same processor not have this problem? 
Are you actually using both cores?

Another straw to grasp here: Maybe you could try to disable cool n quiet in the BIOS?

To be honest, I never thought of that. It is a bit odd...

Anyway I am not sure if there is such an option in the BIOS, but I will check tonight. Heading out for work now. Thanks for the heads up though.

Update: I am happy that since the BIOS update, I have not had my PC crash on me yet. I am still going to look into that extra APCI error, but things are looking good at the moment.

---

### Post by GumbyX on 2007-09-11
And now I am back. :( After 4 days of no problems, the crashes have started up again. Two in the last hour. :( I am very much pissed by this, but I am running late for work, so I cannot investigate it that much anymore. Here are the results of dmesg:

```
 [    0.000000] Linux version 2.6.20-16-generic (root@king) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Aug 30 23:16:15 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] Command line: root=UUID=b14b7660-36d0-40ac-9b8f-a6707310530a ro quiet
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fef3000 - 000000003ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261872) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 HP-CPC                                ) @ 0x00000000000f8650
[    0.000000] ACPI: RSDT (v001 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fef3040
[    0.000000] ACPI: FADT (v002 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fef30c0
[    0.000000] ACPI: SSDT (v001 HP-CPC POWERNOW 0x00000001  LTP 0x00000001) @ 0x000000003fef6f40
[    0.000000] ACPI: MCFG (v001 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fef7140
[    0.000000] ACPI: MADT (v001 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000003fef6e80
[    0.000000] ACPI: DSDT (v001 HP-CPC AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003fef0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261872) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003fef0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   261872
[    0.000000] On node 0 totalpages: 261775
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1086 pages reserved
[    0.000000]   DMA zone: 2857 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3524 pages used for memmap
[    0.000000]   DMA32 zone: 254252 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000f0000
[    0.000000] Nosave address range: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 257109
[    0.000000] Kernel command line: root=UUID=b14b7660-36d0-40ac-9b8f-a6707310530a ro quiet
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   32.717548] Console: colour VGA+ 80x25
[   32.718129] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   32.718958] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   32.719062] Checking aperture...
[   32.719065] CPU 0: aperture @ 0 size 32 MB
[   32.730485] No AGP bridge found
[   32.740299] Memory: 1019912k/1047488k available (2218k kernel code, 27188k reserved, 1162k data, 304k init)
[   32.818257] Calibrating delay using timer specific routine.. 3983.68 BogoMIPS (lpj=7967378)
[   32.818314] Security Framework v1.0.0 initialized
[   32.818320] SELinux:  Disabled at boot.
[   32.818344] Mount-cache hash table entries: 256
[   32.818487] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   32.818490] CPU: L2 Cache: 512K (64 bytes/line)
[   32.818493] CPU 0/0 -> Node 0
[   32.818495] CPU: Physical Processor ID: 0
[   32.818496] CPU: Processor Core ID: 0
[   32.818516] SMP alternatives: switching to UP code
[   32.818803] Early unpacking initramfs... done
[   33.113518] ACPI: Core revision 20060707
[   33.122506] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   33.173694] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   33.213742] Using local APIC timer interrupts.
[   33.263939] result 12436692
[   33.263941] Detected 12.436 MHz APIC timer.
[   33.265956] SMP alternatives: switching to SMP code
[   33.266037] Booting processor 1/2 APIC 0x1
[   33.274976] Initializing CPU#1
[   33.352317] Calibrating delay using timer specific routine.. 3982.93 BogoMIPS (lpj=7965860)
[   33.352323] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   33.352325] CPU: L2 Cache: 512K (64 bytes/line)
[   33.352328] CPU 1/1 -> Node 0
[   33.352330] CPU: Physical Processor ID: 0
[   33.352331] CPU: Processor Core ID: 1
[   33.352411] AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[   33.356327] CPU 1: Syncing TSC to CPU 0.
[   33.357746] CPU 1: synchronized TSC with CPU 0 (last diff -76 cycles, maxerr 544 cycles)
[   33.357756] Brought up 2 CPUs
[   33.357798] Disabling vsyscall due to use of PM timer
[   33.357800] time.c: Using 3.579545 MHz WALL PM GTOD PM timer.
[   33.357803] time.c: Detected 1989.868 MHz processor.
[   34.388541] migration_cost=245
[   34.388896] Time:  8:54:51  Date: 08/11/107
[   34.388934] NET: Registered protocol family 16
[   34.389017] ACPI: bus type pci registered
[   34.389024] PCI: Using configuration type 1
[   34.401781] ACPI: Interpreter enabled
[   34.401784] ACPI: Using IOAPIC for interrupt routing
[   34.402401] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   34.402406] PCI: Probing PCI hardware (bus 00)
[   34.402507] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   34.403465] Boot video device is 0000:01:00.0
[   34.403917] PCI: Transparent bridge - 0000:00:14.4
[   34.403956] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   34.421973] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   34.422199] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   34.422422] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   34.422644] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   34.422864] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11)
[   34.423086] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11)
[   34.423307] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11), disabled.
[   34.423529] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   34.423880] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   34.426144] Linux Plug and Play Support v0.97 (c) Adam Belay
[   34.426155] pnp: PnP ACPI init
[   34.428585] pnp: PnP ACPI: found 10 devices
[   34.428646] PCI: Using ACPI for IRQ routing
[   34.428649] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   34.428660] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   34.428755] NET: Registered protocol family 8
[   34.428757] NET: Registered protocol family 20
[   34.429272] pnp: 00:01: ioport range 0x228-0x22f has been reserved
[   34.429275] pnp: 00:01: ioport range 0x40b-0x40b has been reserved
[   34.429277] pnp: 00:01: ioport range 0x4d6-0x4d6 has been reserved
[   34.429280] pnp: 00:01: ioport range 0xc00-0xc01 has been reserved
[   34.429283] pnp: 00:01: ioport range 0xc14-0xc14 has been reserved
[   34.429286] pnp: 00:01: ioport range 0xc50-0xc52 has been reserved
[   34.429288] pnp: 00:01: ioport range 0xc6c-0xc6d has been reserved
[   34.429291] pnp: 00:01: ioport range 0xc6f-0xc6f has been reserved
[   34.429585] PCI: Bridge: 0000:00:02.0
[   34.429588]   IO window: e000-efff
[   34.429592]   MEM window: fdd00000-fddfffff
[   34.429595]   PREFETCH window: d0000000-dfffffff
[   34.429599] PCI: Bridge: 0000:00:14.4
[   34.429603]   IO window: d000-dfff
[   34.429609]   MEM window: fdc00000-fdcfffff
[   34.429615]   PREFETCH window: fde00000-fdefffff
[   34.429629] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   34.429683] NET: Registered protocol family 2
[   34.476380] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   34.476594] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   34.477704] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   34.478252] TCP: Hash tables configured (established 131072 bind 65536)
[   34.478255] TCP reno registered
[   34.492429] checking if image is initramfs... it is
[   35.076868] Freeing initrd memory: 6824k freed
[   35.081632] audit: initializing netlink socket (disabled)
[   35.081646] audit(1189500891.280:1): initialized
[   35.081836] VFS: Disk quotas dquot_6.5.1
[   35.081856] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   35.081903] io scheduler noop registered
[   35.081905] io scheduler anticipatory registered
[   35.081907] io scheduler deadline registered
[   35.081920] io scheduler cfq registered (default)
[   35.131690] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   35.131709] assign_interrupt_mode Found MSI capability
[   35.131712] Allocate Port Service[0000:00:02.0:pcie00]
[   35.156209] Real Time Clock Driver v1.12ac
[   35.156252] Linux agpgart interface v0.102 (c) Dave Jones
[   35.156254] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   35.156828] mice: PS/2 mouse device common for all mice
[   35.157417] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   35.157569] input: Macintosh mouse button emulation as /class/input/input0
[   35.157605] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   35.157609] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   35.157918] PNP: No PS/2 controller found. Probing ports directly.
[   35.160882] serio: i8042 KBD port at 0x60,0x64 irq 1
[   35.160887] serio: i8042 AUX port at 0x60,0x64 irq 12
[   35.160995] TCP cubic registered
[   35.161005] NET: Registered protocol family 1
[   35.161082] ACPI: (supports S0 S1 S3 S4 S5)
[   35.161129]   Magic number: 7:581:927
[   35.161201]   hash matches device ptyxc
[   35.161248] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   35.161334] Freeing unused kernel memory: 304k freed
[   35.320116] Capability LSM initialized
[   35.357553] ACPI: Processor [CPU0] (supports 8 throttling states)
[   35.357567] ACPI: Processor [CPU1] (supports 8 throttling states)
[   35.771217] usbcore: registered new interface driver usbfs
[   35.771244] usbcore: registered new interface driver hub
[   35.793884] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   35.793907] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   35.793919] ATIIXP: chipset revision 0
[   35.793921] ATIIXP: not 100% native mode: will probe irqs later
[   35.793930]     ide0: BM-DMA at 0xf800-0xf807, BIOS settings: hda:pio, hdb:pio
[   35.793944]     ide1: BM-DMA at 0xf808-0xf80f, BIOS settings: hdc:pio, hdd:pio
[   35.793954] Probing IDE interface ide0...
[   35.806774] usbcore: registered new device driver usb
[   35.807594] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   35.876144] 8139too Fast Ethernet driver 0.9.28
[   35.886470] ieee1394: Initialized config rom entry `ip1394'
[   36.370038] Probing IDE interface ide1...
[   37.109577] hdc: HP DVD Writer 740b, ATAPI CD/DVD-ROM drive
[   37.896637] hdd: IDE-DVD DROM6216, ATAPI CD/DVD-ROM drive
[   37.957805] ide1 at 0x170-0x177,0x376 on irq 15
[   37.961553] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   37.961571] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   37.961694] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   37.961715] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfe02e000
[   38.024196] usb usb1: configuration #1 chosen from 1 choice
[   38.024221] hub 1-0:1.0: USB hub found
[   38.024240] hub 1-0:1.0: 4 ports detected
[   38.132074] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   38.132092] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   38.132121] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   38.132137] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfe02d000
[   38.195938] usb usb2: configuration #1 chosen from 1 choice
[   38.195962] hub 2-0:1.0: USB hub found
[   38.195972] hub 2-0:1.0: 4 ports detected
[   38.299944] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   38.299962] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   38.299988] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   38.300045] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe02c000
[   38.300057] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   38.300161] usb usb3: configuration #1 chosen from 1 choice
[   38.300184] hub 3-0:1.0: USB hub found
[   38.300190] hub 3-0:1.0: 8 ports detected
[   38.407781] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[   38.408454] eth0: RealTek RTL8139 at 0xffffc20000032000, 00:13:d3:55:a3:04, IRQ 20
[   38.408457] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   38.408519] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 21
[   38.459634] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   38.461735] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fdcfd000-fdcfd7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   38.474377] SCSI subsystem initialized
[   38.480148] libata version 2.20 loaded.
[   38.484009] sata_sil 0000:00:12.0: version 2.2
[   38.484042] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
[   38.484133] ata1: SATA max UDMA/100 cmd 0xffffc20000048080 ctl 0xffffc2000004808a bmdma 0xffffc20000048000 irq 22
[   38.484168] ata2: SATA max UDMA/100 cmd 0xffffc200000480c0 ctl 0xffffc200000480ca bmdma 0xffffc20000048008 irq 22
[   38.484185] scsi0 : sata_sil
[   38.494671] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   38.494681] Uniform CD-ROM driver Revision: 3.20
[   38.499017] hdd: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[   38.954974] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   38.963445] ata1.00: ATA-7: HDT722525DLA380, V44OA80A, max UDMA/100
[   38.963449] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   38.975397] ata1.00: configured for UDMA/100
[   38.975404] scsi1 : sata_sil
[   39.446385] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   39.471375] ata2.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[   39.471379] ata2.00: ATA-7: WDC WD1600AAJS-55PSA0, 05.06H05, max UDMA/133
[   39.471382] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   39.483011] ata2.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[   39.483019] ata2.00: configured for UDMA/100
[   39.483114] scsi 0:0:0:0: Direct-Access     ATA      HDT722525DLA380  V44O PQ: 0 ANSI: 5
[   39.483464] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-5 05.0 PQ: 0 ANSI: 5
[   39.489319] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   39.489335] sda: Write Protect is off
[   39.489337] sda: Mode Sense: 00 3a 00 00
[   39.489350] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.489406] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   39.489413] sda: Write Protect is off
[   39.489415] sda: Mode Sense: 00 3a 00 00
[   39.489426] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.489431]  sda: sda1 sda2
[   39.503742] sd 0:0:0:0: Attached scsi disk sda
[   39.503922] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[   39.503932] sdb: Write Protect is off
[   39.503934] sdb: Mode Sense: 00 3a 00 00
[   39.503947] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.503990] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[   39.503998] sdb: Write Protect is off
[   39.504000] sdb: Mode Sense: 00 3a 00 00
[   39.504012] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.504015]  sdb: sdb1 sdb2 < sdb5 >
[   39.546685] sd 1:0:0:0: Attached scsi disk sdb
[   39.550004] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   39.550026] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   39.634136] usb 2-2: new full speed USB device using ohci_hcd and address 2
[   39.747595] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0001a3940006147f]
[   39.747737] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[0010dc0000b7ac42]
[   39.775471] Attempting manual resume
[   39.775475] swsusp: Resume From Partition 8:21
[   39.775477] PM: Checking swsusp image.
[   39.775719] PM: Resume from disk failed.
[   39.792303] EXT3-fs: INFO: recovery required on readonly filesystem.
[   39.792307] EXT3-fs: write access will be enabled during recovery.
[   39.832969] usb 2-2: configuration #1 chosen from 1 choice
[   39.912675] scsi2 : SBP-2 IEEE-1394
[   40.141525] usb 2-4: new full speed USB device using ohci_hcd and address 3
[   40.342379] usb 2-4: configuration #1 chosen from 1 choice
[   40.648909] usb 1-2: new full speed USB device using ohci_hcd and address 3
[   40.853741] usb 1-2: configuration #1 chosen from 1 choice
[   40.855832] usbcore: registered new interface driver libusual
[   40.859291] Initializing USB Mass Storage driver...
[   40.859358] scsi3 : SCSI emulation for USB Mass Storage devices
[   40.859420] usb-storage: device found at 3
[   40.859422] usb-storage: waiting for device to settle before scanning
[   40.859434] usbcore: registered new interface driver usb-storage
[   40.859436] USB Mass Storage support registered.
[   40.869605] usbcore: registered new interface driver hiddev
[   40.877718] input: Logitech USB Receiver as /class/input/input1
[   40.877733] input: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:13.0-2
[   40.882981] input: Logitech USB Receiver as /class/input/input2
[   40.883346] input,hiddev96: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-2
[   40.883362] usbcore: registered new interface driver usbhid
[   40.883365] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   40.924995] ieee1394: sbp2: Logged into SBP-2 device
[   40.925095] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[   40.925834] scsi 2:0:0:0: Direct-Access     WDC WD32 00JB-00KFA0      0.01 PQ: 0 ANSI: 0
[   40.926311] SCSI device sdc: 625142448 512-byte hdwr sectors (320073 MB)
[   40.926548] sdc: Write Protect is off
[   40.926551] sdc: Mode Sense: 03 00 00 00
[   40.926982] sdc: got wrong page
[   40.927030] sdc: assuming drive cache: write through
[   40.927537] SCSI device sdc: 625142448 512-byte hdwr sectors (320073 MB)
[   40.927736] sdc: Write Protect is off
[   40.927738] sdc: Mode Sense: 03 00 00 00
[   40.928191] sdc: got wrong page
[   40.928236] sdc: assuming drive cache: write through
[   40.928284]  sdc: sdc1
[   40.945328] sd 2:0:0:0: Attached scsi disk sdc
[   40.945375] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   43.196202] kjournald starting.  Commit interval 5 seconds
[   43.196246] EXT3-fs: recovery complete.
[   43.199282] EXT3-fs: mounted filesystem with ordered data mode.
[   45.855585] usb-storage: device scan complete
[   45.861525] scsi 3:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   45.867512] scsi 3:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   45.873503] scsi 3:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   45.879497] scsi 3:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   45.889514] sd 3:0:0:0: Attached scsi removable disk sdd
[   45.889549] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   45.899492] sd 3:0:0:1: Attached scsi removable disk sde
[   45.899520] sd 3:0:0:1: Attached scsi generic sg4 type 0
[   45.909477] sd 3:0:0:2: Attached scsi removable disk sdf
[   45.909506] sd 3:0:0:2: Attached scsi generic sg5 type 0
[   45.919468] sd 3:0:0:3: Attached scsi removable disk sdg
[   45.919497] sd 3:0:0:3: Attached scsi generic sg6 type 0
[   51.463390] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   52.993062] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   53.055202] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   53.103142] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   53.215675] input: PC Speaker as /class/input/input3
[   53.277752] NET: Registered protocol family 17
[   53.331373] parport: PnPBIOS parport detected.
[   53.331422] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   53.432376] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
[   53.432392] usbcore: registered new interface driver usblp
[   53.432396] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   53.624827] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   53.766943] lp0: using parport0 (interrupt-driven).
[   53.854323] fuse init (API version 7.8)
[   53.888791] Adding 3004112k swap on /dev/disk/by-uuid/5ac1181b-12b7-4a91-a7a8-ee8bf004bf9d.  Priority:-1 extents:1 across:3004112k
[   54.049340] EXT3 FS on sdb1, internal journal
[   54.358879] NET: Registered protocol family 10
[   54.358991] lo: Disabled Privacy Extensions
[   57.463849] No dock devices found.
[   57.524599] input: Power Button (FF) as /class/input/input4
[   57.524625] ACPI: Power Button (FF) [PWRF]
[   57.524662] input: Power Button (CM) as /class/input/input5
[   57.524677] ACPI: Power Button (CM) [PWRB]
[   57.567180] ibm_acpi: ec object not found
[   57.613359] Using specific hotkey driver
[   57.706938] pcc_acpi: loading...
[   57.970081] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (version 2.00.00)
[   57.970474] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x8
[   57.970479] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xa
[   57.970482] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   64.837333] ppdev: user-space parallel port driver
[   65.032008] [drm] Initialized drm 1.1.0 20060810
[   65.051106] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   65.051460] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   66.057135] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   66.166202] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   66.183746] NFSD: starting 90-second grace period
[   66.198720] [drm] Setting GART location based on new memory map
[   66.199057] [drm] Loading R300 Microcode
[   66.199090] [drm] writeback test succeeded in 1 usecs
[   66.846330] vboxdrv: Trying to deactivate NMI watchdog permanently...
[   66.846334] vboxdrv: Successfully done.
[   67.308838] Bluetooth: Core ver 2.11
[   67.308889] NET: Registered protocol family 31
[   67.308891] Bluetooth: HCI device and connection manager initialized
[   67.308895] Bluetooth: HCI socket layer initialized
[   67.328063] Bluetooth: L2CAP ver 2.8
[   67.328067] Bluetooth: L2CAP socket layer initialized
[   67.330594] Bluetooth: RFCOMM socket layer initialized
[   67.330611] Bluetooth: RFCOMM TTY layer initialized
[   67.330613] Bluetooth: RFCOMM ver 1.8
[   74.670697] eth0: no IPv6 routers present

```

Looks as if the APCI errors are gone, other then the one I see on boot (will post what it is later). I am starting to rethink a reinstall or just going back to 32bit. : sigh: This will require some looking into later today. If anyone can help me out, I would appreciate it.

PS Like the last times, when the "crash" happens, the screen freezes, but for some reason I am able to still move the mouse. The keyboard no longer responds though. Today it happened when I was downloading pictures and opening a new tab in Swiftweasel. Take from that what you will.

---

### Post by Jouke74 on 2007-09-11
I have to agree with a new install, but I sincerly hope that indeed will make a difference.

Best wishes, Jouke.

---

### Post by GumbyX on 2007-09-12
> **Jouke74 said:**
> I have to agree with a new install, but I sincerly hope that indeed will make a difference.

Best wishes, Jouke.

Did the reinstall. Didn't fix anything. But it helped me find the problem. Its Beryl. For some reason, it causing the problems I described. It happened to me right after I installed beryl in 32bit, so I know that has to be the problem. How to solve it, other then NOT install Beryl, is beyond me. Sadly, I lost my old install, which i will require me to get off my *** and do it AGAIN. But, at least I can stick with 64bit.

I am going to try installing compiz-fuzion and see if that causes the same type of problem. If it does, I need to find a way to get XGL on this thing, as I am starting to think its a problem with AGILX, the open-source ATI drivers, and my graphics card.  Or just give up on beryl/compiz till I can fix this problem.

Now to go back and REINSTALL, again,bit. And hope I will be able to get my desktop back again. (I moved my home folder to another partition, which has saved me some headaches of lost files and settings, but comes with its own problems.)

---

### Post by Jouke74 on 2007-09-13
I was already afraid of that (Ubuntu is not windows). Anyway it is good to know that you found the problem. If you need a stable system I suggest that you run without Compiz and Beryl. Both of them can still have severe flukes, and if it is costing you your work and time I don't think it is worth it (but that's me). If you are going to do ATI + FGLRX + XGL + Compiz I am willing to help again.

---

### Post by GumbyX on 2007-09-13
> **Jouke74 said:**
> I was already afraid of that (Ubuntu is not windows). Anyway it is good to know that you found the problem. If you need a stable system I suggest that you run without Compiz and Beryl. Both of them can still have severe flukes, and if it is costing you your work and time I don't think it is worth it (but that's me). If you are going to do ATI + FGLRX + XGL + Compiz I am willing to help again.

Thanks.I might try FGLRX + XGL , but when I used the restricted drvers manager, it caused system instability. So i will stick with ATI + AIGLX for now. We will see what happens. This weekend I will have the time to sit and really work with this machine to get it working write. Right now, I know the problem and am able to work around it till I can find a proper solution. But I might take you up on your offer later on (ie This weekend).

---

### Post by YoshiHNS on 2007-09-13
A suggestion. Try a different video card. Either borrow a friends, or buy a cheap one. In the Windows world when i had an ATI video card i had problems with it, mostly drivers related. Never had a problem with any of the GeForce cards i worked. So try getting a GeForce card or using onboard video if there is one.

---

