---
title: "Ext4 at 9.04 64 bit"
date: 2009-05-11
forum: x86 64-bit Users
---

### Post by uv2008 on 2009-05-11
Hello,

When installing the 64 bit version of Ubuntu 9.04 I wasn't aware of the ext3/ext4 issue. Since (of course) I would like my computer to run as fast and efficient as possible, I'd be grateful if you could help me with a few questions that I have, some of them may be quite ignorant:

1. On Grub it seems that I have ext3. Is there a way to really check if I have ext3 or ext4?

2. If ext4 is a superior system, then why isn't it the default at the 9.04 installation?

3. What is the most recommended way of upgrading from ext3 to ext4?

Thanks!

---

### Post by lvleph on 2009-05-11
```

blkid 

```
in cli will tell you your type of partitions.

To change to ext4 from ext3
```

sudo tune2fs -O extents,uninit_bg,dir_index /dev/{DEVICE}

```
followed by
```

e2fsck -fD /dev/{DEVICE}

```
I would suggest doing this from a live disk. I did it while the system was mounted and spent the rest of the day fixing things.
You will also have to change /etc/fstab to mount your file systems with the correct type.

EDIT: ext4 has issues with latency, meaning that it doesn't write things to the drive immediately and therefore if the system crashes you can lose all unsaved data. At least, this is my understanding.

---

### Post by pixel :-) on 2009-05-11
> Problems can arise if the system crashes before the actual write occurs. In this situation, users of ext3 have come to expect that the disk will hold either the old version or the new version of the file following the crash. However, the ext4 code in the Linux kernel version 2.6.28 will often clear the contents of the file before the crash, but never write the new version, thus losing the contents of the file entirely.

You are warned. Its always a trade off of performance and security.

---

### Post by uv2008 on 2009-05-11
Thanks guys, it's much clearer now. I think I'll stick with my ext3 at the moment...

---

### Post by whoop on 2009-05-11
howto: ext2/ext3 to ext4
[http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)

---

### Post by Artemis3 on 2009-05-13
> **uv2008 said:**
> Hello,

When installing the 64 bit version of Ubuntu 9.04 I wasn't aware of the ext3/ext4 issue. Since (of course) I would like my computer to run as fast and efficient as possible, I'd be grateful if you could help me with a few questions that I have, some of them may be quite ignorant:

1. On Grub it seems that I have ext3. Is there a way to really check if I have ext3 or ext4?

2. If ext4 is a superior system, then why isn't it the default at the 9.04 installation?

3. What is the most recommended way of upgrading from ext3 to ext4?

Thanks!

I think you missed this: [http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

> [size=4]Switching to ext4 requires manually updating grub[/size]

If you choose to upgrade your / or /boot filesystem in place from ext2 or ext3 to ext4 (as documented on the [ext4 wiki](http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4)), then you must also use the grub-install command after upgrading to Ubuntu 9.04 to reinstall your boot loader. If you do not do this, then the version of GRUB installed in your boot sector will not be able to read the kernel from the ext4 filesystem and your system will fail to boot.

[size=4]Possible data-loss problems resizing ext4[/size]

The resize2fs tool may cause data loss when growing or shrinking ext4 filesystems off-line. See this mail from the upstream maintainer for more details. Unfortunately we became aware of this too late to fix it in Ubuntu 9.04. If you wish to resize an ext4 filesystem using the tools in Ubuntu 9.04, you may be able to work around these problems by first disabling the flex_bg and uninit_bg features (do not attempt this on a mounted filesystem!):

```
tune2fs -O ^flex_bg,^uninit_bg /dev/DEVICE_NAME
e2fsck /dev/DEVICE_NAME
```

However, we still strongly recommend taking significantly more care with backups than usual before attempting to resize an ext4 filesystem.

I think ext4 might be made default in 9.10, when more bugs get squashed.
IMO the most recommended way is to backup all your data and reformat.

---

### Post by ken78724 on 2009-05-13
Can I tell whether I'm using ext4 or ext3 from the BIOS or must I review this with an install disc. Sorry, I was not attentive at the time of the upgrade but believe I had been using ext4 which I set upon install to 8.10. Am scampering hard to solve other minor problems,,,, so if feasible send me an email at__[EMAIL="koymkg@gmail.com"][/EMAIL] <snip> so I come back for your answer. 

Many thanks for the question and the labor extended to all of us.):P

---

### Post by Arup on 2009-05-13
> **ken78724 said:**
> Can I tell whether I'm using ext4 or ext3 from the BIOS or must I review this with an install disc. Sorry, I was not attentive at the time of the upgrade but believe I had been using ext4 which I set upon install to 8.10. Am scampering hard to solve other minor problems,,,, so if feasible send me an email at [email]koymkg@gmail.com[/email] so I come back for your answer. 

Many thanks for the question and the labor extended to all of us.):P

I don't think ext4 was supported in 8.10 kernel so its probably ext3.

---

### Post by ken78724 on 2009-05-15
Arup, 
   You say, "its probably ext3". But, I'd truly like to find out whether I'm running out of an Ext4 partition; let me review for clarification as I installed 9.04 jaunty on two independently installed HDs; am sure one HD was set to Ext 4. It was either on the 80 giB or a 750 giB. So, 
      1) a full install was made on 80 gig HD. But on boot up [after I did not shut down correctly and probably created a cache problem] a grey screen arises on every bootup. So to get "have to work done", I've put this on the back burner & to be solved later for weeks now. Am not asking for assist on this as it has an unrelated issue
      2) On the 750 giB, the upgrade went from 8.04 to 8.10 intrepid after a "visiting linux guru" made a new partition setting one of the partitions /dev/sda4 [625.4 giB] to a JFS filesystem which I believe means Ext4. But I did not verify exactly what happened during the upgrade when the new dev/sda1 was created by me. I saw it for a flash but I can't recall flashes at age 70.

Not a biggie but I'd like to verify whether I'm using the Ext4 the guru created. Many, many thanks Arup for answering me before!!!! ;)

---

### Post by cariboo on 2009-05-15
lvleph gave you the answer to your question open an Applications-->Accessories-->Terminal and type:

```
blkid
```

For some reason in Karmic I have to run the command as root:

```
sudo blkid
```

you should get a result that looks something like this:

```
/dev/sda1: UUID="7451e251-cb09-4cda-b433-a2768d81affe" TYPE="ext4" 
/dev/sdb1: UUID="29994917-63c7-4980-ae46-212ca6ad29cb" TYPE="ext4" 
/dev/sdb2: UUID="7c109a7f-b7fd-402d-aec5-0ee7dd30d37a" TYPE="ext4" 
/dev/sdb3: UUID="bc7912f5-a427-429d-98cd-7b97312c294d" TYPE="swap" 
/dev/sdb5: UUID="e80a1b7b-5113-491f-8f7b-473aeeefa34b" TYPE="ext4" 
/dev/sdb6: UUID="d4240bbc-6108-4a70-bb52-92ca66d86daf" TYPE="ext4" 
```

Note at the end of each line it tells you what file system it is formatted for.

---

