---
title: "WLAN on zv5000 AMD64 Unbuntu 64bit"
date: 2006-10-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by logicgate on 2006-10-07
Hello everyone. I have been trying and trying to activate my wlan in ubuntu 64bit on my HP zv5000 laptop.

I downloaded the ndiswrapper
sudo apt-get install ndiswrapper-utils
then installed the drivers that came with the laptop but doesn't work. The system tells me "invalid drivers":

logicgate@logicgate-laptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!
netbc564        invalid driver!


These are the ones I have installed so far:

bcmwl5.inf
netbc564.inf

Both don't work in my Ubuntu 64bit. I don't know what to do or what drivers to use. I would appreciate some help. thnx in advance

---

### Post by logicgate on 2006-10-07
Nobody has any information that can help???

---

### Post by logicgate on 2006-10-07
whats the point of this threads, if no one helps!!

---

### Post by dmn_clown on 2006-10-07
You didn't give much information for anyone to help you.  However two things spring to mind, you need to use the 64 bit wireless drivers (if they exist, google is your friend here) and have you tried the broadcom driver that is now in the kernel?

---

### Post by logicgate on 2006-10-07
I don't get it.

I removed the acx
I installed the headers
Installed the GCC
Installed the ndiswrapper-utils through apt-get
Then installed the drivers to the ndiswrapper both bcmwl5.inf and netbc564.inf but no dice but not getting the invalid drivers anymore, because the GCC was installed.

Also notice that I get this msg
 bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
when I check the "sudo dmesg"

It seams that, that error is from the wlan manager that comes with the OS trying to activate the wlan device.

Now I get the ndiswrapper showing the drivers are installed and HW present and in the log shows that it gets activated just fine.

---

### Post by logicgate on 2006-10-07
> **dmn_clown said:**
> You didn't give much information for anyone to help you.  However two things spring to mind, you need to use the 64 bit wireless drivers (if they exist, google is your friend here) and have you tried the broadcom driver that is now in the kernel?

And I apologize I didn't mean to be rude... im just frustrated.

---

### Post by logicgate on 2006-10-07
Anyone any ideas??

This is the list of modules notice that ndiswrapper doesnt have anything assigned

root@logicgate-laptop:/home/logicgate# sudo lsmod
Module                  Size  Used by
rfcomm                 44512  0
l2cap                  29376  5 rfcomm
bluetooth              58244  4 rfcomm,l2cap
ppdev                  10760  0
powernow_k8            12480  0
cpufreq_userspace       8544  1
cpufreq_stats           7624  0
freq_table              5888  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2688  0
cpufreq_ondemand        9128  0
cpufreq_conservative    10408  0
video                  18248  0
tc1100_wmi              8520  0
sony_acpi               6548  0
pcc_acpi               15488  0
hotkey                 13128  0
dev_acpi               14724  0
container               5696  0
button                  8288  0
acpi_sbs               24024  0
battery                11656  1 acpi_sbs
ac                      6600  1 acpi_sbs
i2c_acpi_ec             6400  1 acpi_sbs
dm_mod                 62536  1
md_mod                 76152  0
ipv6                  298240  10
ndiswrapper           223488  0 ---------------------------> nothing assigned
sr_mod                 19108  0
sbp2                   27204  0
lp                     14464  0
af_packet              27020  4
pcmcia                 45728  0
joydev                 12544  0
tsdev                   9600  0
bcm43xx               126668  0 ----------------------------> this bastard gives me the problems with the initialization (gnome lan manager)
ieee80211softmac       32000  1 bcm43xx
ieee80211              38664  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7872  1 ieee80211
yenta_socket           29964  2
rsrc_nonstatic         14016  1 yenta_socket
pcmcia_core            47396  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           37928  1
snd_ac97_codec        109820  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            58784  0
snd_mixer_oss          19968  1 snd_pcm_oss
snd_pcm               104008  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              28424  1 snd_pcm
snd                    68000  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              12640  1 snd
pcspkr                  3016  0
snd_page_alloc         13328  2 snd_intel8x0,snd_pcm
psmouse                39748  0
8139cp                 26112  0
8139too                31168  0
mii                     7104  2 8139cp,8139too
parport_pc             40176  1
parport                43532  3 ppdev,lp,parport_pc
nvidia               5432600  0
i2c_nforce2             8640  0
shpchp                 50720  0
pci_hotplug            32592  1 shpchp
serio_raw               9156  0
i2c_core               26048  3 i2c_acpi_ec,nvidia,i2c_nforce2
evdev                  13888  2
ext3                  145616  1
jbd                    70312  1 ext3
ide_generic             2176  0
ohci1394               36684  0
ieee1394              368472  2 sbp2,ohci1394
ehci_hcd               35592  0
ohci_hcd               23044  0
usbcore               146556  4 ndiswrapper,ehci_hcd,ohci_hcd
ide_cd                 35104  0
cdrom                  40568  2 sr_mod,ide_cd
ide_disk               18880  3
generic                 6724  0
amd74xx                16496  0 [permanent]
sata_nv                11972  0
libata                 84960  1 sata_nv
scsi_mod              159928  3 sr_mod,sbp2,libata
thermal                15884  0
processor              29160  2 powernow_k8,thermal
fan                     5832  0
capability              6536  0
commoncap               9088  1 capability
vga16fb                14480  1
cfbcopyarea             4544  1 vga16fb
vgastate                9792  1 vga16fb
cfbimgblt               3584  1 vga16fb
cfbfillrect             5184  1 vga16fb
fbcon                  42496  72
tileblit                3520  1 fbcon
font                    9344  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3136  1 bitblit

---

### Post by brainfry on 2006-10-08
This gave me a brain tumor of a headache for a couple of weeks but I finally sorted it yesterday and I'm using a wireless connection while writing this.
I'm running an HP dv5046ea with a Turion 64 and the (infamous) bcm4318 wireless card.
Ok, I've read allsorts of threads on the subject and tried to implement certain aspects from most of them.
I first updated the system after a clean install and booted the new kernel 2.6.15-27amd64-generic. 
I blacklisted the bcm43xx driver that came with the system by adding```
blacklist bcm43xx
```in the blacklist file
```
sudo gedit /etc/modprobe.d/blacklist
```and then rebooted. I checked the network settings didn't list any wireless devices and then installed ndiswrapper-utils with Synaptic followed by the 64 bit drivers I got from a thread on planet AMD [http://www.planetamd64.com/index.php?showtopic=21723](http://www.planetamd64.com/index.php?showtopic=21723)
```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l (to make sure they installed)
sudo ndiswrapper -m (which said 'adding alias wlan0 to /etc/modprobe.d/ndiswrapper)
```At this point the wireless light came on. I opened network, System>Admin>Network and added my ssid and wep key to the wlan0 settings, saved, closed and rebooted. I had to use wep because I haven't got wpa_supplicant to work yet, next on my list though along with 3d acceleration on my ATI Mobility radeon 200m (if possible)
On reboot, the wireless card is listed as eth1 even though it was wlan0 before reboot. It works though so I'm not complaining. It's as good as it was in windows :D
And thats it. It worked for me, it may work for you, hopefully it will. It means I can have a decent OS on here for a change.
Hope this helps.

---

### Post by dmn_clown on 2006-10-08
As of kernel 2.6.17.rc1 the bcm43xxx driver is in the kernel you still need to extract the firmware from the windows driver, I believe it has more features than are available through ndiswrapper.  They reverse engineered it as Broadcom seems to be afraid of the American FCC*.


*Of course the same wireless chipset exists in one of the lynksys routers that is running the Linux kernel so they _DID_ write a GNU/Linux driver they just didn't release it to the community.

---

### Post by logicgate on 2006-10-08
Didn't work. The blacklist actually got rid of the driver loading and it showing on the Network list of devices. But for some reason every driver I've installed into the machine does not want to work. I've done the driver that comes with system (standard 32bit), the netbc564.inf version and the one that you provided (bcmwl5.inf 64bit version) but that one doesn't show that the hardware is present only shows tha the driver is present. I'm so frustrated with this.

I also got this message when I used the 32bit drivers

[   42.895926] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[   43.006380] ndiswrapper (check_nt_hdr:149): Windows driver is not 64-bit; bad magic: 010B
[   43.006386] ndiswrapper (load_sys_files:218): couldn't prepare driver 'bcmwl5'
[   43.006789] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

---

### Post by brainfry on 2006-10-09
Thats a weird one then as it's the driver I'm using to view this site. I did get it working after a fresh install though so not sure if that helped in as much as I'd not tried anything else.

---

### Post by logicgate on 2006-10-09
Here is the msg with the other drivers installed (64bit version drivers)

[   46.295712] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[   46.401938] ndiswrapper (check_nt_hdr:149): Windows driver is not 64-bit; bad magic: 010B
[   46.401945] ndiswrapper (load_sys_files:218): couldn't prepare driver 'bcmwl5'
[   46.402402] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

---

### Post by logicgate on 2006-10-09
Please help! I'm gona reinstall ubuntu and try your method step by step and see where it takes me.

---

### Post by brainfry on 2006-10-10
I've been frantically trying to find the thread I followed to get this working (forgot to make a note of it before reinstalling and went from memory. Thankfully I remembered what to do! Kicked myself as I've always made notes when I've run into trouble ](*,))
If I do stumble across the thread, I'll post it back here but those were the steps I took and it's worked like a dream since Saturday. Not actually booted into *doze since :D
GOOD LUCK

---

### Post by brainfry on 2006-10-10
Ok, I found a site that lists the same steps as me however after running
  sudo ndiswrapper -m they change the alias in /etc/modprobe.d/ndiswrapper to eth1 instead of wlan0. I'm gonna try it and see what happens although this is working fine with it still being named wlan0 in that file.
Basically, follow what I did and cross yer fingers and hopefully, it'll be all good.

---

### Post by brainfry on 2006-10-10
Changed to alias eth1 in /etc/modprobe.d/ndiswrapper and it messed with my wireless so changed it back to wlan0. Don't know why it's wlan0 in that file and eth1 in network settings and iwconfig but as it works, I ain't messin with it again.

---

### Post by brainfry on 2006-10-10
.....you see, this is where my username came from. This is just frying my brain. Since messing round with the alias, the wireless card is now listed as wlan0 instead of eth1 (?)  Still working though so all is good. :mrgreen:

---

### Post by Fully216 on 2006-10-10
logicgate, it helps if you know what chipset your wireless card you are using.  For example, I have the Broadcom 4306, which uses the netbc654 while the airforce one uses another.  

It sounds like you still need to find the right driver for your particular chipset.  This is going to take google and/or searching this (and other) forum(s).  I know I found my driver on this forum.

You might also try these treads for help and background.  Also notice that the drivers are posted on some of these pages and can also be found from the hp website, which is the one I would try first.

Broadcom 4306 - [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)
Broadcom 4311 - [http://ubuntuforums.org/showthread.php?t=266088](http://ubuntuforums.org/showthread.php?t=266088)
Broadcom 43xx - [https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx)
fwcutter - [http://ubuntuforums.org/showthread.php?t=193903](http://ubuntuforums.org/showthread.php?t=193903)

---

### Post by logicgate on 2006-10-11
I was able to activate FINALY!!! Just shows as eth1 instead of wlan0. Where at a moment showed as wlan0 then returned again to be eth1. Just a few minutes ago it had stopped working so Im not sure what the frank is wrong with it.

---

### Post by floring on 2006-10-12
HI all,

I understand your frustration ! I've been there for 2 months (mostly long nights !!!) scratching my head how to make my Compaq Presario V3030 CA work (duo-core AMD 64 Turion X2 using a broadcom 4311 chipset for WLAN). Useless to say that I am not a linux newbie and this is my 3rd laptop running linux but never ever found it so challenging to make it work !

Bottom line, the ONLY way I was able to bring wifi up was by using (buying) the linuxant's driverloader.Their piece a sw is a ndiswrapper that loads windoze broadcom drivers; On this occasion I found out that Broadcom drivers  provided by ACER or even Broadcom .. DID NOT WORK FOR ME !! Bottom line, if you can afford 20$, do it and save yourself from a lot of pain !

Also I had to disable ndiswrapper (I run ubuntu Edgy-KNOT3 a.ka.64bit) by blacklisting it as well as blacklisting the bcm43xx kernel modules built-in.
I downloaded from HP's site the Windows drivers (SP33011A ) after trying a lot of other sets of drivers out there and nothing worked !! not even the drivers on linuxant's webpage did not work for me !! I am not saying that this is the only way to do it, just this is how it worked for me.

As for WPA2 (wpa_supplicant) linuxant does provide it too. Not saying that it's the perfect solution out there but at least it was the only one that worked for me. Give it a shot, good luck and all the best !

---

