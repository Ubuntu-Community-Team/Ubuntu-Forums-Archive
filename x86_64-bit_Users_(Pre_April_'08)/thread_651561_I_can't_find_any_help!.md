---
title: "I can't find any help!"
date: 2007-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by sholo20 on 2007-12-27
Hi I'm new to linux (Ubuntu 7.10) up to now i was able to solve every problem i encounter by searching this forum. this time i have a problem to which i can't find a solution. Whenever i inster a dvd the system will log me off and goes back to the main login page. the last thing i was doing before this happened was trying to set wine to recognize dvd device on dvd decrypter. i followed a few "how to" and nothign worked. i finally gave up and decided to try k9 or other linux software to back up movies. before i tried that i decided to watch a movie. and, well, the system log me off. I was able to watch movies before. I followed the "how to" on how to play encrypted dvds and everything was fine. please let me know what info you all need to help me.
I have a gateway labtop AMD Turion mobile technology 64bits. 1.5gb ram and i'm running the 64 bit edition of ubuntu 7.10.
I really like linux. I will never go back to a world full of Gates and Windows.:lolflag:

---

### Post by Yellow Pasque on 2007-12-27
What does your /etc/fstab look like?
Also, can you post *lshw -C disk* info for the dvd drve

---

### Post by sholo20 on 2007-12-29
fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=e66df8a1-ae73-49d9-893f-59c946e0a9fe /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=715bc83b-2685-4c81-ac1c-1b0633ab2c53 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

lshw -C disk
  *-disk                  
       description: ATA Disk
       product: HTS421280H9AT00
       vendor: Hitachi
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: HA3OA70S
       serial: HKA540AMHL0PVF
       size: 74GB
       capacity: 74GB
       capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
       configuration: apm=off mode=udma5 smart=on
  *-cdrom
       description: DVD writer
       product: HL-DT-ST DVD-RW GWA-4082N
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: CG03
       serial: M0067544306
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r
       configuration: mode=udma2 status=ready
     *-disc
          physical id: 0
          logical name: /dev/hdc

another thing. I just realize that any video that i play will do the same. (log me out and go back to login page)

---

### Post by Yellow Pasque on 2007-12-29
> /dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

Ah, you should change the noauto to auto. Also, change the udf,iso9660 to auto. Now, when you put a CD/DVD in you should be able to mount it with ```
mount -a
```

---

### Post by sholo20 on 2007-12-29
I know i sound like an idiot but how do i change it to auto? 'cause i went on to change it manually and it said that i don't have permission to do so. the fist one you said to change to auto i see that i should change noauto for auto but the second part you also said to change to auto and i'm not quite sure which part to change. little more detail will help me. maybe if you think like a retard i will be able to understand you better. thanks in advance.

---

### Post by Yellow Pasque on 2007-12-29
No problem. Type this in a terminal:
```
sudo gedit /etc/fstab
```

Make the line look like this:
```
/dev/hdc /media/cdrom0 auto user,auto,exec 0 0
```

---

### Post by sholo20 on 2008-01-01
that did not help me. and i think is not the dvd rom. it must be the video card or something else because the system will log me off even if i just try to play an avi or any source of video format. does anyone have any ideas? Thanks :(

---

### Post by John.Michael.Kane on 2008-01-01
> **sholo20 said:**
> that did not help me. and i think is not the dvd rom. it must be the video card or something else because the system will log me off even if i just try to play an avi or any source of video format. does anyone have any ideas? Thanks :(

You may want to start your troubleshooting with the last things you were doing, and looking over your post it would be installing/editing  wine/dvd decrypter.  Eg: have you tried to uninstall wine/k3b/dvd decrypter., and any other items you added before the issues of dvd playback started.

Also you also should have included the howto's: you followed in your post as this would aid users in trying help troubleshoot your issues.

---

### Post by sholo20 on 2008-01-01
Sorry and thank you all for your help. I figure out the main problem. I have one of those video cards that are in the black list. I followed a "how to" to make the 3d acceleration work. everything was fine but then i went on and configure the card to the max of its performance. this was causing ubuntu to log me out everytime i tried to play a video. so i set the settings back to normal and now can insert a dvd and play a video without the system logging me off. but now I have the problem were i can't see the video i only get sound. but I seen plenty posts on this issue. i will try to follow them.  Thank you all. :)

---

