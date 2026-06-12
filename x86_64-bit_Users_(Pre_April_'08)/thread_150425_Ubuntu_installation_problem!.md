---
title: "Ubuntu installation problem!"
date: 2006-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by PsychoSync on 2006-03-26
Hello

Here is my problem : I tried to install Breezy Badger on my Mac, everything went fine until the 1st reboot of the installation process. Ubuntu does not start! It gets stuck at the Yaboot screen.

The error:

Please wait, loading kernel ...
/pci@80000000/mac-io@10/ide@20000/disk@0:8, /boot/vmlinux: Input/output error

I'm downloading the LiveCD so i can access my HD to find/edit ?something? to repair the problem, though I am new at Linux so i don't know what to look for and what the commands are, could someone please help me?

Thanks for your time.

---

### Post by PsychoSync on 2006-03-26
Please help! I succeded in mounting the ext3 file system, I'm pretty sure all i have to do is edit "yaboot.conf" to point it to the right partitions and/or device but i don't know what settings to put. Is there a command that can list the entire HD config and give you guys info about what to edit?

---

### Post by veritygold on 2006-03-26
Sorry i can't help you but i am having a similar problem. I just get a black screen. I have to cut off power and restart manually. I have a toshiba notebook and running Breezy Badger also.

---

### Post by PsychoSync on 2006-03-26
I booted the Ubuntu CD just to see the exact details of the patitions on my HD.

It looks like this:

IDE master (hda) - 40.0 GB WDC ....

    #1       23.2 kB            Apple
    #2                          Macintosh
    #3                          Macintosh
    #4                          Macintosh
    #5                       Patch partition
    (here comes the Ubuntu stuff i believe)
    #6       1.0 MB      boot
    #8      12.4 GB      ext3
    #10    20.4 GB     fat32
    #9      474 MB      swap
    #7      6.5 GB       hfs+
           
Can someone tell me what should be in the yaboot.conf?

(this is an example)

boot=/dev/hda2
device=/pci@f4000000/ata-6@d/disk@0:
partition=4
root=/dev/hda4
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda3

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="quiet splash"

And one more thing, i know how to edit the "yaboot.conf" file but there is one more thing i must do after... ybin? i don't know how to use it.

Thanks.

---

### Post by grazie on 2006-03-26
It would help if you could post your actual yaboot.conf, fstab and the output of```
# sudo mac-fdisk -l
```Boot your machine with a LiveCD and in a terminal (Applications -> Accessories -> Terminal)```

# sudo mkdir /mnt/tmp
# sudo mount /dev/hda8 /mnt/tmp
```You can then output```
# cat /mnt/tmp/etc/yaboot.conf
# cat /mnt/tmp/etc/fstab
```If you only have an InstallCD enter **rescue** at the **boot:** prompt and select **/dev/discs/disc0/part8** when prompted. To output yaboot.conf and fstab```
# cat /etc/yaboot.conf
# cat /etc/fstab
```Note, in rescue mode don't use sudo.

---

