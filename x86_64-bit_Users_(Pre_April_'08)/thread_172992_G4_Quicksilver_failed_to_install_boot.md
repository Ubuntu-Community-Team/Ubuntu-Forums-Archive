---
title: "G4 Quicksilver failed to install boot"
date: 2006-05-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mukke on 2006-05-09
Ok
 I have a G4 933 with an internal HD 250G running macosx and a external Firewire 80G HD (LaCie porsche) formated Linux.

 So i downloaded both disk images (iso's) from the ubuntu site. Burned both on a cd with Disk Utility. I keep the Install cd in my drive. I copy 4 files (read somwhere in the help) to my root of my 250G HD

 Ok i restart my mac with c-key down he reads the install cd and we are started , i set up all things like english language belgian keyboard, i erase my ext.HD (sda) completly and install continues, untill it wants to install boot. It sais 'Warning: System might not bootable etc, i gotta boot manual with /boot/vmlinux /dev/sda3 with arg. root=/dev/sda3.

First i had no clue but i thought maybe in OF. so i startup in alt-commad-f-o nd type boot /boot/vmlinux /dev/sda3 root=/dev/sda3 . I guessed that would be booting like they said. Hmmmm apearantly not. Then i started browsing fora. I tried   'boot 1:4,yaboot' wich errored a bit. Then i saw i only had to replace the x so i tried  'boot hd:1,yaboot' , no luck either.

If i boot with option-key down i see my 2 disks but the 80G disk has still the osx icon on it.

I'm hoping some1 could help me with my problem. I need it cause i need to test alot of things in a linux envroiment different then unix on mac osx cause it's not always the same. Anyway can some1 say how i have to solve this ?

---

### Post by Mukke on 2006-05-10
10h later and still it refuses to work.
I found some iformation i needed here:
[http://macubuntu.blogspot.com/2005/11/nailed-howto-install-bootable-mac.html](http://macubuntu.blogspot.com/2005/11/nailed-howto-install-bootable-mac.html)

The doc seemsed very helpfull to me , everything worked like it suposed to be. Thank you basscakes , whoever u are. But then at oe of the last steps , i reboot , type "boot fw/node/sbp-2/disk@0:2,yaboot".
Bam i get a blackscreen , i supose it's the linux boot screen again and yes it is. Now it sais "linux:3,/vmlinux Unable to open. Invalid device." I know what it means but how do i solve it ?

I also tried to start up with my alt-key down again and supresely enough i now see my FW disk with a linux icon. I clicked on it. I come in the yaboot console but b4 i can type l (lower:L) or linux, i get trown back to the screen where i could select the 2 disk (like where u get when u hold alt-key down while booting).

Any1 with a solution or who can point me out what i am doing wrong?

---

### Post by ivansv on 2006-05-10
ubuntu is looking for an Apple_Bootstrap partition which is only 819200bytes at start of the hard drive, you may have wiped it out when you partitioned. go back and repartition creating the bootstrap partiition first and then reinstall.

---

### Post by Mukke on 2006-05-10
U could be right
if i look into Disk Utility i only see 2 partitions
is there a way to partition the disk tru terminal under osx ?
cause i'm not very good ad that stage and how do i exactly call the partitions
btw my disk is 80.026.361.856 bytes

---

### Post by farruinn on 2006-05-10
This is what I would try: reformat the external harddrive with disk utility in OS X. Then, reinstall linux on that drive. This time, don't delete/reformat all the partitions, just the large hfs one. That way the partition stuff that OS X put on the disk will remain intact.

Note, I've never installed ubuntu on a firewire disk, but that's how I'd go about it.

---

### Post by Mukke on 2006-05-10
like this ?
[IMG]http://avatars.belgianmacgamers.be/diskutility.png[/IMG]

---

### Post by Mukke on 2006-05-10
i could put the drive in may mac tho but i can't keep it there. Cause i have just got a 2nd drive out but he's gonna come back.

---

### Post by ivansv on 2006-05-10
wish i could help you further but frankly don't know how. apple is like windows, windows hides the system files, apple doesn't let you become a super user and you may need to be su to do these things from the terminal. i've setup my mac and will dual boot my x86 laptop and work ubuntu that way.
there is a post here where the fellow uses parted from ubuntu to resize and partition, maybe that will help you.you still need to create the Apple_Bootstrap partition or ubuntu will not dual boot.

---

### Post by jdp on 2006-05-10
Ahem.  OS X includes **fdisk** which give this output:

```
[baraka:~] jon% fdisk
usage: fdisk [-ieu] [-f mbrboot] [-c cyl -h head -s sect] [-S size] [-r] [-a style] disk
        -i: initialize disk with new MBR
        -u: update MBR code, preserve partition table
        -e: edit MBRs on disk interactively
        -f: specify non-standard MBR template
        -chs: specify disk geometry
        -S: specify disk size
        -r: read partition specs from stdin (implies -i)
        -a: auto-partition with the given style
        -d: dump partition table
        -y: don't ask any questions
        -t: test if disk is partitioned
`disk' is of the form /dev/rdisk0.
auto-partition styles:
  boothfs     8Mb boot plus HFS+ root partition (default)
  bootufs     8Mb boot plus UFS root partition
  hfs         Entire disk as one HFS+ partition
  ufs         Entire disk as one UFS partition
  dos         Entire disk as one DOS partition
  raid        Entire disk as one 0xAC partition
[baraka:~] jon% 
```

Unless you are logged in as root (not just an account with admin privs) you'll need to use **sudo** to do anything useful with **fdisk**.

---

