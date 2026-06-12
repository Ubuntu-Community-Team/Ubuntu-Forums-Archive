---
title: "Access of Windows files"
date: 2008-04-19
forum: Wine
---

### Post by vtt on 2008-04-19
Is it possible to access real Windows files from a program running under Wine?
I didn't find a way to define Windows disks from the Wine configurator.

Thank you for your help.

---

### Post by prshah on 2008-04-19
> **vtt said:**
> Is it possible to access real Windows files from a program running under Wine?
I didn't find a way to define Windows disks from the Wine configurator.


Yes, you can access your windows files using Wine. WINE creates a .wine directory in your home directory (~). Inside this is a dosdevices folder. Within this are all your drive letters for use in WINE sessions; c:, d:, etc.

so you can create a link, say f: to your windows partition say /media/sda1 as follows:

```

ln -s /media/sda1 ~/.wine/dosdevices/f:
```

Note the absence of sudo. You don't need sudo in this case.

Also, z: is already defined to map to your "/". So you can also access your windows files by z:\media\sda1 without the need for the above commands.

---

### Post by vtt on 2008-04-20
Thank you for the information.

I created 2 links:
  ln -s /media/sda5 ~/.wine/dosdevices/d:
  ln -s /media/sda6 ~/.wine/dosdevices/e:
and I added drives d: and e: in the Wine config. OK

When I try to open a file within a program running under Wine I only have the choice of the "official" drives A:, B: C: home H:, home Y: and Z: but not the D: and E: drives. What is wrong? Should I do something else?

Thank you for listening.

---

### Post by prshah on 2008-04-20
> **vtt said:**
> 
I created 2 links:
  ln -s /media/sda5 ~/.wine/dosdevices/d:
  ln -s /media/sda6 ~/.wine/dosdevices/e:
and I added drives d: and e: in the Wine config. OK
When I try to open a file within a program running under Wine I only have the 

EITHER create the symlinks (ln -s) command -or- set it up in the Wine config. Don't do both.

---

### Post by vtt on 2008-04-21
First, I restored my Ubuntu 7.10 in order to have a clean Wine 0.9.56.

In Wineconf (only) I defined 2 drives d: and e:   does not work. In Dosdevices i noticed 2 icons for my disks with an X (broken link). I deleted the 2 drives in Wineconf.

I defined 2 symlinks with ln -s (different drives) but with the same result in dosdevices. What's wrong? Thanks for your help.

---

### Post by prshah on 2008-04-21
> **vtt said:**
> 
I defined 2 symlinks with ln -s (different drives) but with the same result in dosdevices. What's wrong? Thanks for your help.

I guess you're doing something wrong; works fine for me. Take a look at the attached screenshots and check the commands;

---

### Post by vtt on 2008-04-22
Hello,

Thank you for your kind help.

I made exactly the same as your example (for several Windows partitions and addresses) but with ls the new devices are displayed in red (broken link) instead of blue. The devices appear in the Wine config but they are useless.

It's curious, my Windows disks are correctly identified with the command fdisk -l but it seems they are not recognized by Wine. Is it necessary to do something special to make Wine recognize them?

Any idea?

---

### Post by prshah on 2008-04-22
> **vtt said:**
> Hello,
It's curious, my Windows disks are correctly identified with the command fdisk -l but it seems they are not recognized by Wine. Is it necessary to do something special to make Wine recognize them?


Maybe the drives are not mounted? Why not post here the exact command you are giving?

---

### Post by vtt on 2008-05-05
> **prshah said:**
> Maybe the drives are not mounted? Why not post here the exact command you are giving?

Sorry for not having answered earlier: I have been away for one week! Here are the commands given:

clav@clav1:~$ sudo fdisk -l
Disque /dev/sda: 500.1 Go, 500107862016 octets
255 heads, 63 sectors/track, 60801 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x57b557b5

Périphérique Amorce    Début         Fin      Blocs    Id  Système

/dev/sda1   *           1        1045     8393931    c  W95 FAT32 (LBA)
/dev/sda2            1438       60801   476841330    f  W95 Etendu (LBA)
/dev/sda5            1438        2221     6297448+   b  W95 FAT32
/dev/sda6            2614       24153   173020018+   b  W95 FAT32
/dev/sda7           24154       55484   251666226    b  W95 FAT32
/dev/sda8           55485       60801    42708771    b  W95 FAT32

[email]clav@clav1:~/.wine[/email]/dosdevices$ ln -s /media/sda5 d:
[email]clav@clav1:~/.wine[/email]/dosdevices$ ln -s /media/sda6 e:
[email]clav@clav1:~/.wine[/email]/dosdevices$ ls -la
total 8
drwxr-xr-x 2 clav clav 4096 2008-05-05 15:50 .
drwxr-xr-x 4 clav clav 4096 2008-05-05 15:37 ..
lrwxrwxrwx 1 clav clav   10 2008-04-21 18:03 c: -> ../drive_c
lrwxrwxrwx 1 clav clav   11 2008-05-05 15:50 d: -> /media/sda5
lrwxrwxrwx 1 clav clav   11 2008-05-05 15:50 e: -> /media/sda6
lrwxrwxrwx 1 clav clav    1 2008-04-21 18:03 z: -> /

However c: and d: appear in red instead of blue and are listed as "broken link". From Ubuntu I can access those drives /media/sda5 and sda6 without any problem.

Any clue? Thank you for your support.

---

