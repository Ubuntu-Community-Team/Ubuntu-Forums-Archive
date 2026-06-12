---
title: "2 harddisks...PLEASE HELP"
date: 2005-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by nicomazi on 2005-10-13
hi all,
i got 2 harddisks on my comp. one 10GB and another 40GB. on 1st one i got Breezy installed...second one i can't find??!!!i intended to use 40GB disk as my storage for music, photos etc. but i can't find it. i go to places->computer and it's not there?!!!...all cd-roms are there, floppy, universal card-reader...but not my HD!! during clean install of breazy i had both disks formated with reisor, following mount points i used:
for disk1: /root followed by /swap. disk2: /local/home
please help me to get my sorage disk back.....i got to save stuff
thnx

---

### Post by Vulpus on 2005-10-13
Seems to me your 2nd hard drive isnt mounted!

Have a look here and see if it helps:

[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by efpc2003 on 2005-10-13
OR:
[http://www.guia-ubuntu.org/hoary/doku.php?id=administracion:windows&amp;rev=1127695498#como_montar_desmontar_una_particion_windows_fat_al_arrancar_y_permitir_a_usuarios_comunes_leer_escribir](http://www.guia-ubuntu.org/hoary/doku.php?id=administracion:windows&amp;rev=1127695498#como_montar_desmontar_una_particion_windows_fat_al_arrancar_y_permitir_a_usuarios_comunes_leer_escribir)

ADD this line at the end of fstab file...

/dev/hda1       /media/windows    vfat    gid=100,umask=0007,fmask=0117,utf8 0       0

where "media/windows" is the folder where you mount the hard disk

---

### Post by ssam on 2005-10-13
are you a mac user or a windows user?
is there existing data on the 40gb drive you want to keep?
do you want to reformat the 40gb drive?

if you type at a terminal

```
sudo fdisk -l /dev/hdb
```

and put in your pass word, what is the output?

its a fairly simple thing to solve if we know what your set up is.

---

### Post by nicomazi on 2005-10-14
[QUOTE=ssam]are you a mac user or a windows user?
is there existing data on the 40gb drive you want to keep?
do you want to reformat the 40gb drive?

if you type at a terminal

```
sudo fdisk -l /dev/hdb
```

and put in your pass word, what is the output?

its a fairly simple thing to solve if we know what your set up is.[/QUOTE]

ppc 
no data to keep
i wouldn't mind reformating if i have to
output: parameters of my disk (40gb, heads, cilinders...etc)
if it's that simple please tell me how
yhnx

---

### Post by ssam on 2005-10-14
i recoment downloading gparted from synaptic (system -> menu -> synaptic) you may need to enable the universe ([AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto"))

now open gparted (application -> system tools -> gparted). now you can select the 40gb drive which should be called /dev/hdb (hda is first ide drive, hdb second, etc. cd drives are usually first on second ide bus, making them hdc).

delete its existing partition, and make a new one, ext3 is probably the best format, although you will need to download some extra software in mac os x if you ever want to read it from there.

now if that all goes smoothly we need to tell ubuntu how and where to mount the drive. in linux drives are mounted onto a folder in your main file system. we need to make a folder. /media/data would be a resonable thing to call it.

open up a terminal (application -> Accessories -> terminal) and type

```
cd /media
```

this moves you to the folder media. now to create a subfolder

```
sudo mkdir data
```

the sudo bit gives you root priviliges, which you need as your normal user wont have write permission here. you will be asked for your password. now we have made the mount point we need to tell linux to mount the disk.

```
sudo cp /etc/fstab /etc/fstab.backup
```

ok that was to make a back up of the filesystem table, just in case something goes wrong. now to edit it

```
sudo gedit /etc/fstab
```

now please be careful in here, you will notice it has several lines refereing to things like/dev/hda1. the one more thing you need to know about disk names, is that a number refers to the partitions. /dev/hda3 is the third partition on hda.

we need to add a new line with <file system>,<mount point>,<type>,<options>,<dump> and <pass> seperated by spaces or tabs. put the new line at the bottom. this should work

```
/dev/hdb1   /media/data    ext3    defaults   0     0
```

now save and close the file.

now to test that it worked. type at the terminal

```
sudo mount /media/data
```

this should mount the data drive. there should be no error messages type

```
mount
```

to check a list of what is mounted.

now we need to make sure your user has write access to the disk.

```
cd /media/data
sudo chown $USER:$USER .
```

the $USER will be interpreted as your username by the terminal. this changes the ownership of the drive to you.

now you can navigate to /media/data in nautilus and save files there.

let us know if it works

sam

---

### Post by virgule on 2005-10-14
Greating from a fellow Mac user... :)
You mentionned **/local/home** is assigned to disk 2. You want just** /home**.
Since I dont know what is what and who is who I'll suggest you start over and make sure you assign **/home** to the 40g and the rest (**/** and **swap**) to the 10G drive.  This will give you 40g of 'personal' space and 10G for Ubuntu packages and friends.  Im sure you will be pleased with this setup :)

---

