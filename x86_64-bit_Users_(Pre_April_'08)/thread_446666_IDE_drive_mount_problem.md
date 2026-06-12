---
title: "IDE drive mount problem"
date: 2007-05-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by moza on 2007-05-17
[SIZE="4"]hi folks

i have two drives.one that has the ubuntu on it and it is sata and the other is the original IDE and linux cant see it at all..........when i look on the volume manager i cant see it and on windows i can see it well......so how can i fix that?[/SIZE]

---

### Post by kuja on 2007-05-17
Maybe it's not just mounted. The first master IDE hard disk would be /dev/hda. The first Sata master would /dev/sda. To see if it's really seeing them, try running this command in a terminal:

ls /dev/[sh]d*

---

### Post by John.Michael.Kane on 2007-05-17
If the other drive is blank 
```
sudo aptitude install gparted
```

Format the drive to ext3 or the file system of your choice
```
gksudo gparted
```

NextRun:
```
sudo fdisk -l
```

The output should be something like this example.
```
/dev/hda5 1276 2388 8940141 83 Linux
```

create a mount point
sudo mkdir /media/**storage** the bold name can be anything you want

Backup your /etc/fstab file:
```
sudo cp /etc/fstab /etc/fstab_backup
```

Edit your /etc/fstab file:
```
sudo nano /etc/fstab
```

Add this line: **Note make sure hda5 is changed to match your drives hda number**
```
/dev/hda5 /storage ext3 defaults 0 0
```

Save the file, and exit.

Now run:
```
sudo mount -a
```

You need to give it the proper permissions.
```
sudo chown -R marie:marie /storage
``` change marie to your user name.

Set final permissions
```
sudo chmod -R 755 /storage
```

You golden.

Credit to [psychocats]("http://www.psychocats.net/ubuntu/index") for the drive mount info.


If the drive is ntfs based. this should help
[**ntfs-3g how to**]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntsf-3g")

---

### Post by moza on 2007-05-17
then problem is that i cant rformat it it has my work.......and most of it are ntfs...and it is not founf in  ls /dev/[sh]d*

---

### Post by John.Michael.Kane on 2007-05-17
> **moza said:**
> then problem is that i cant rformat it it has my work.......and most of it are ntfs...and it is not founf in  ls /dev/[sh]d*


Then these are your options.

1) [Guide to mount windows partitions]("http://www.psychocats.net/ubuntu/mountwindows")

2) use the ntfs3g guide linked in the other post

3) Off load the data to another form of media using the live cd.

---

### Post by tza on 2007-05-17
easy stuff first - is the additional drive enabled in the system BIOS (Setup Menu at boot screen)?

I run a dual-boot Dell machine and had to do this when I installed the new drive for ubuntu.

Hope the easy stuff helps.

---

### Post by moza on 2007-05-18
look i can see it on windows.........but not on ubuntu and i think i read it on fedora

---

### Post by John.Michael.Kane on 2007-05-18
> **moza said:**
> look i can see it on windows.........but not on ubuntu and i think i read it on fedora

Theres two guides given to mount ntfs drives.


Also it would help if you posted the output . 
```
sudo fdisk -l
```

---

