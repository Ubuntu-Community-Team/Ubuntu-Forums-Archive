---
title: "boot problem!!!"
date: 2007-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by pope8 on 2007-11-10
I've spent the last 2 days trying to sort this problem out.. but with no luck (tried probably 20 "how-to" guides).

**Problem:**

**1.  **I installed a fresh copy of Gutsy (64-bit desktop) on a new hp dv9608ca (dv9000) laptop ( [http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c01162047&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c01162047&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN) ).  

**2.  **I fixed all of the small issues (wifi card, graphics) and had everything working correctly.  Booted fine into desktop countless times.

**3.  **I then did a complete system update from the GNOME update manager (with all update options/sources enabled).

**4.  **After the update and a restart my laptop kicked me to a busybox shell with the following error:

Check root= botarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/... does not exist.  Dropping to a shell!

Busybox ...
Enter 'help' ...

(initramfs)

**5.  **The directory /dev/disk/by-uuid does not exist, and neither does any of the "sda drives" in /dev (ex. sda1 = ntsf windows, sda2 = ext3 ubuntu /, sda3 = swap) or /etc/fstab...  

**6.  **When I reboot multiple times, sometimes it will load into the desktop, but mostly it will attempt to load my drive and then pop out to this shell after sitting for a min or two.  

**7.  **I can load everytime using the recovery option in grub.  at the root prompt I can see /dev/disk/by-uuid/ with all the disk's, fstab, etc.  I can type exit which will bring my to the log-in screen, and I can log into my user account and everything works.  All my boot files (boot/grub/menu.lst, fstab, proc) match, but for some reason, it just won't load normally.  

**8.  **I've re-installed fresh 3 times and each time after I do a system update, it does this same thing.  I've tried different boot command options that fixed "sort of similiar" problems with other people, but no luck for me.  Any help would be appreciated.

---

### Post by pope8 on 2007-11-10
**NOTE:**  after I posted this... I was given the same error while booting with the recovery option in grub.  I restarted 4 times in a row after it began to hang at the same spot (while running a "loading cdrom" of sorts command).. finally it loaded to the root command line.  So it seems both options produce the same error, just one more frequently.

**CONTENTS:**
**/etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=5680f094-dac1-41ef-84aa-8c14777cc967 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=13CD1F3724A9EAA1 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=b9c9b6f4-3a48-4175-842f-b46f8a63f615 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

**/boot/grub/menu.lst**
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5680f094-dac1-41ef-84aa-8c14777cc967 ro noapic apic=off irqpoll noirqdebug
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5680f094-dac1-41ef-84aa-8c14777cc967 ro single noapic apic=off irqpoll noirqdebug
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

#dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

**ls /dev/disk/by-uuid**
pope8@michaelnb:~$ ls /dev/disk/by-uuid
13CD1F3724A9EAA1                      b9c9b6f4-3a48-4175-842f-b46f8a63f615
5680f094-dac1-41ef-84aa-8c14777cc967

**cat /proc/modules**
pope8@michaelnb:~$ cat /proc/modules
ipv6 317192 10 - Live 0xffffffff88a68000
af_packet 28172 4 - Live 0xffffffff88a60000
rfcomm 47656 2 - Live 0xffffffff88a53000
l2cap 28672 11 rfcomm, Live 0xffffffff88a4b000
bluetooth 63876 4 rfcomm,l2cap, Live 0xffffffff88a3a000
ppdev 11272 0 - Live 0xffffffff88a36000
powernow_k8 16608 1 - Live 0xffffffff88a30000
cpufreq_conservative 9608 0 - Live 0xffffffff88a2c000
cpufreq_stats 8160 0 - Live 0xffffffff88a29000
cpufreq_ondemand 10896 1 - Live 0xffffffff88a25000
freq_table 6464 3 powernow_k8,cpufreq_stats,cpufreq_ondemand, Live 0xffffffff88a22000
cpufreq_powersave 3072 0 - Live 0xffffffff88065000
cpufreq_userspace 6048 0 - Live 0xffffffff88a1f000
ac 7304 0 - Live 0xffffffff88a1c000
button 10400 0 - Live 0xffffffff88a18000
container 6400 0 - Live 0xffffffff88a15000
video 21140 11 - Live 0xffffffff88a0e000
battery 12424 0 - Live 0xffffffff88a09000
sbs 21520 0 - Live 0xffffffff88a02000
dock 12264 0 - Live 0xffffffff889fe000
ndiswrapper 241312 0 - Live 0xffffffff889c2000
sbp2 27144 0 - Live 0xffffffff889ba000
parport_pc 41896 0 - Live 0xffffffff889ae000
lp 15048 0 - Live 0xffffffff889a9000
parport 44172 3 ppdev,parport_pc,lp, Live 0xffffffff8899d000
joydev 13440 0 - Live 0xffffffff88998000
snd_hda_intel 337192 1 - Live 0xffffffff88944000
snd_pcm_oss 50048 0 - Live 0xffffffff88936000
snd_mixer_oss 20096 1 snd_pcm_oss, Live 0xffffffff88930000
snd_pcm 94344 2 snd_hda_intel,snd_pcm_oss, Live 0xffffffff88917000
snd_seq_dummy 5380 0 - Live 0xffffffff88914000
snd_seq_oss 36864 0 - Live 0xffffffff8890a000
snd_seq_midi 11008 0 - Live 0xffffffff88906000
snd_rawmidi 29824 1 snd_seq_midi, Live 0xffffffff888fd000
uvcvideo 52228 0 - Live 0xffffffff888ef000
snd_seq_midi_event 9984 2 snd_seq_oss,snd_seq_midi, Live 0xffffffff888eb000
snd_seq 62496 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xffffffff888da000
snd_timer 27272 2 snd_pcm,snd_seq, Live 0xffffffff888d2000
ide_cd 35488 0 - Live 0xffffffff888c8000
cdrom 41768 1 ide_cd, Live 0xffffffff888bc000
snd_seq_device 10260 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xffffffff888b8000
nvidia 7013492 36 - Live 0xffffffff88206000 (P)
compat_ioctl32 11136 1 uvcvideo, Live 0xffffffff88202000
videodev 31360 1 uvcvideo, Live 0xffffffff881f9000
v4l1_compat 15364 2 uvcvideo,videodev, Live 0xffffffff881f4000
v4l2_common 21888 3 uvcvideo,compat_ioctl32,videodev, Live 0xffffffff881ed000
serio_raw 9092 0 - Live 0xffffffff881e9000
sdhci 21004 0 - Live 0xffffffff881e2000
psmouse 45596 0 - Live 0xffffffff881d5000
pcspkr 4608 0 - Live 0xffffffff881d2000
k8temp 7680 0 - Live 0xffffffff881cf000
mmc_core 33416 1 sdhci, Live 0xffffffff881c5000
snd 69288 11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xffffffff881b3000
soundcore 10272 1 snd, Live 0xffffffff881af000
i2c_core 30208 1 nvidia, Live 0xffffffff881a6000
shpchp 38300 0 - Live 0xffffffff8819b000
pci_hotplug 36612 1 shpchp, Live 0xffffffff88191000
snd_page_alloc 12560 2 snd_hda_intel,snd_pcm, Live 0xffffffff8818c000
evdev 13056 6 - Live 0xffffffff88187000
ext3 146576 1 - Live 0xffffffff88162000
jbd 69360 1 ext3, Live 0xffffffff88150000
mbcache 11272 1 ext3, Live 0xffffffff8814c000
sg 41384 0 - Live 0xffffffff88140000
sd_mod 32512 4 - Live 0xffffffff88137000
amd74xx 17328 0 [permanent], Live 0xffffffff88131000
ide_core 141200 2 ide_cd,amd74xx, Live 0xffffffff8810d000
ahci 27012 3 - Live 0xffffffff88103000
ohci1394 38984 0 - Live 0xffffffff880f6000
ieee1394 109528 2 sbp2,ohci1394, Live 0xffffffff880da000
ata_generic 9988 0 - Live 0xffffffff880d4000
libata 138928 2 ahci,ata_generic, Live 0xffffffff880b1000
scsi_mod 172856 4 sbp2,sg,sd_mod,libata, Live 0xffffffff88085000
forcedeth 55048 0 - Live 0xffffffff88074000
ehci_hcd 40076 0 - Live 0xffffffff88067000
ohci_hcd 25092 0 - Live 0xffffffff8805d000
usbcore 161584 5 ndiswrapper,uvcvideo,ehci_hcd,ohci_hcd, Live 0xffffffff88034000
thermal 16528 0 - Live 0xffffffff8802e000
processor 36232 2 powernow_k8,thermal, Live 0xffffffff88024000
fan 6920 0 - Live 0xffffffff88021000
fuse 52528 3 - Live 0xffffffff88013000
apparmor 47008 0 - Live 0xffffffff88006000
commoncap 9472 1 apparmor, Live 0xffffffff88002000

**cat /proc/cmdline**
pope8@michaelnb:~$ cat /proc/cmdline
root=UUID=5680f094-dac1-41ef-84aa-8c14777cc967 ro single noapic apic=off irqpoll noirqdebug

**ls /dev | grep sda**
pope8@michaelnb:~$ ls /dev | grep sda
sda
sda1
sda2
sda3

---

### Post by pope8 on 2007-11-10
--*DOES NOT FIX PROBLEM*--

it seems with boot options "noapic nolapic" that I am able to load to my desktop with no errors.  I've only tested this on about 6 boots.. but it hasn't stumbled yet.. so crossing fingers.

---

### Post by pope8 on 2007-11-10
*incomplete until I have enough time to finish this*

**-message me for help with problems regarding this laptop in the mean time-**

---

### Post by hangfire on 2007-11-20
Check for BIOS settings for changes.

I once had a Intel 865 based M/B that died the way all 865 M/B's die, from getting a USB hot-plug the caused an internal fault.

After that, Windows refused to boot, and Linux would only boot with the noapic option. However it ran slow. I recycled it and upgraded to a $99 newegg special (AMD3400+ and M/B).

I would strongly encourage you to run some HP diagnostics, and consider exercising the warranty.

-HF

---

### Post by pope8 on 2007-11-20
My windows partition boots fine every time.. Ubuntu (Gutsy), however, does not.  I've worked around with "noapic, apic=off, etc etc", but it boots once every 10-20 resets (sometimes it will just boot fine, but without wifi).  No matter the commands I use at boot, it will sometimes boot ok, sometimes hang (at different spots, though usually at the same one), etc, etc.  When it loads, and wifi is working (almost always when it loads), everything runs great.. I wish I had the time to try and solve this more then 30-60 mins a day... but I'm flooded with work..

---

### Post by Jouke74 on 2007-11-21
- This may sound absurd on a new laptop, but check your drive (all partitions) for file system errors? 
- Check if the CDROM station is present / loaded under windows and if it is working.
- The problem might be that one of your drives is not connected well in the laptop.
- And you could try a new install of Ubuntu because some files are messed up as a last resort.

---

### Post by pope8 on 2007-11-21
checked filesystems.. both checked out fine.. cd drive works completely in windows on all boots.  I had previously did 3 re-installations on the linux partition.. 2 different downloads and 3 burns of the distro image.. I'm confused as to what to do now..

---

### Post by Jouke74 on 2007-11-21
Hmm. I assume you already ran the memtest too? The only thing I can think of is to try and run the Live CD for a while. Does that hang / wants to boot? If it boots, are your drives recognized correctly? Probably they will be unfortunately. 

Can you try to run "dmesg" in the terminal if you did not do so yet?

Another crazy idea might be to downgrade your kernel to a lower (available) version. Because some piece of hardware does not like running with the current kernel.

Grasping straws here...

---

### Post by pope8 on 2007-11-22
Here is the dmesg log:

[http://cs.uwindsor.ca/~pope8/dmseg.txt](http://cs.uwindsor.ca/~pope8/dmseg.txt)

I was thinking of recompiling the kernel,, though I've never attempted to do that before.  This is after a good boot, with wifi working (using the ndiswrapper on a dell bcm3123 driver because i couldn't get the restricted driver to work... I did fresh installs on 2 other systems and they work flawlessly.. This problem is really annoying.  I flashed the bios with the latest version then ran the memtest.. was good..

---

### Post by Jouke74 on 2007-11-22
I can't find anything strange except this: 
[   25.728275] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   25.728450] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   25.730170] ACPI Exception (thermal-0311): AE_BAD_DATA, No critical threshold [20070126]

And even that is doubtfull that it is the problem...
If you tried all the options of ACPI IRQ polling etc. I really don't know what's left to try.

---

### Post by pope8 on 2007-11-22
I've tried different boot options, in some different combos.. the problem is.. one set will work for 2-3 boots, then the same error.. i'll reboot, try it again.. same error.. change the boot options.. it'll other load or give me the error.. It's random to whether it will boot or not.  I would love to fix this asap.. I'm always on my computer programming and when I move from location to location and have to shut down.. the 10 mins of restarting is a pain in the ****..

---

### Post by ledm01 on 2007-12-20
POPE8, same problem here, I bought this laptop at Best Buy (DV9608ca), and the boot problem started right after the update manager picked up 110 updates after a fresh install. Other than that, my only problem is getting into a hidden network with an SSID. If I broadcast the SSID, my wireless connection works fine. 

Have you found a solution for the boot problem yet ?

---

### Post by pope8 on 2007-12-20
The more I researched the problem, the more the problem pointed to an AMD issue.  It seems that hp laptops with AMD chipsets are not supported at all by Ubuntu.  You'd do well to restore your laptop and to return it.  I was 11 days outside the extended 30 day return policy for holiday hours (normally 14 - also best buy).. and I decided to stay clear of laptops with amd cores.

I dumped the restore partition on the laptop and never made a copy, and they weren't going to exchange the laptop on the grounds of not being able to restore it for resale.  I made the point that they could grab another floor model and make a copy of the backup partition easily, so they got the `geek squad`to do that for me and exchanged it.  

I grabbed the dv9638 for a little more money and haven`t had a single problem.  I stayed clear of the amd chipset and the broadcom wireless.  This laptop has an intel wirelessN card, which works out of the box with G based routers, and will be fully supported with N in the next few months (you can patch yourself manually and it works fine).  The nvidia 8600m is a huge jump from the 7150m, and it has a combo HD/dvd-burner. It features dual 160 sata hard drives (320gb which makes dual booting great). If you are going to dual boot.. it already comes with vista ultimate 64-bit. I mean.. I could go on and on.. point is.. everything was supported great once I jumped ship to the Intel chipset.

I suppose you could wait around on a fix (assuming one every materializes), but I spent over a month trying to get it to load.  You`ll find that fiesty is much the same.  All the things that work in Gutsy, don`t in fiesty.  The boot problem finally got me.  I could spend 10 mins a day trying to boot my laptop over and over, wasted time.  If you are smart, do the exchange soon.  (also note:  there are lots of posts on problems with hp.. none specific to this problem though.. almost isolated to this model.. but good luck and let me know what you decided to do)

---

### Post by ledm01 on 2007-12-20
Thank you for the advice, fortunately, I bought this laptop 4 days ago, so I don't see any problem in getting an exchange. Il try this out.

---

### Post by hangfire on 2007-12-20
delete

---

### Post by ledm01 on 2007-12-26
Ok, I have a workaround for this problem, it works 100% of the time for me. I noticed that if I entered the grub menu by pressing ESC and then pressed 'b' to boot the kernel after a few seconds, it did not hang on me anymore. 

So I simply edited the /boot/grub/menu.lst and disabled the HIDDENMENU option, and adjusted the timeout to 15 seconds.

---

### Post by ImALittleTeaPot on 2007-12-27
I've been having the same problem as you.  What exactly do you do after entering the grub menu?

thanks.

---

### Post by ledm01 on 2007-12-30
Press ESC to get the grub menu, select the kernel you want to load if you have mutliple ones, then press `e` to edit the options, but do not edit anything, just wait a few seconds. Then press `b`.

I have not investigated why we have to give it a delay, but mine works all the time now. Look at my previous post to edit the menu.lst file to get this going automatically, and adjust the delay so it works all the time on your machine.

---

