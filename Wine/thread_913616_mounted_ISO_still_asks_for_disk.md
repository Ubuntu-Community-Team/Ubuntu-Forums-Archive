---
title: "mounted ISO still asks for disk"
date: 2008-09-07
forum: Wine
---

### Post by Greenbean209 on 2008-09-07
Well I bought a Diablo 2 iso online it consisted of 3 disk ISO's I mounted the first one "install disk" using this code

```
 sudo  mount -o loop '/home/john/Desktop/Diablo II + Expansion + Latest Patch [[1.12] [nocd]]/Diablo II - Install Disc.iso' /media/iso
```

it mounted and the I opened it up and clicked on install and it said please insert install Disk. Did I mount it wrong? is there someway i can fool the computer into thinking that it is in the CD drive? And does anybody here have any experience with Diablo or installing games from and ISO? 

Thanks in advanced

---

### Post by Darkade on 2008-09-07
I have the same problem installing Need For Speed Most Wanted. But I think it's more like an autentification thing, it's like the game is making sure that you have an original copy of the game. However if there's a fix to this I'd really like to know

---

### Post by lakersforce on 2008-09-08
I recently opened a post about the same subject. Apparently it is not possible to eject mounted iso's in wine. (Not even with the wine eject command and everything configured in winecfg).

The solution to this is to copy all of the cd's into each-other. If that does not work, burn and use wine eject.

---

### Post by Greenbean209 on 2008-09-08
I checked that post and thats not my problem. My problem is that my already mounted iso is asking for its self. Oh yah on your post you said it was asking for a new disk. it should be fine if you unmounted the one in use because if you think about it... if you had a game that required 3 disks and you had to have the previous disk in to continue on the new one that would require you to have 2 CD drive right. so that seem illogical to require 2 disk drives. For example if you had a laptop then you are extremely limited. But back to my problem... I need to fool the program into thinking there is a disk inserted in my disk drive. I've heard stories of this particular game being mounted and installed successfully on windows using daemon tools but i can't get daemon tools to install. it think its just not compatible with Linux. I'm trying to avoid burning because that would require me to got to the library to use there burner and I'm not sure if they have ISO burning software.

---

### Post by viktor4124 on 2008-09-20
Hey,

I had a similar problem recently, which was solved the following way. Let's hope it will work for you too:

Wine manages a directory $HOME/.wine/dosdevices where symbolic links for mapping Windows-drives to locations in your filesystem are held. Just enter the directory in a terminal and examine it yourself (ls -l command).

There are links that have one colon (e.g. E:) which are refering to the mapping directory in your filesystem, and there drive-letters followed by two colons, which are used to point to a actual physical device (e.g. D: -> /dev/cdrom).
So I not only tried to loop-mount my iso and bind it to drive E:, but also to bind the "physical drive" E:: to the iso itself, so that the windows software may find the cd's serial and stuff. And guess what, it worked ;-) at least for me

```

$ sudo mount -o loop /home/viktor/image.iso /mnt/iso
$ cd $HOME/.wine/dosdevices
$ ln -s /mnt/iso e:
$ ln -s /home/viktor/image.iso e::
$ wine explorer

```

unfortunately I somehow couldn't start the software with
```

wine /mnt/iso/setup.exe

```
I had' to use wine explorer, navigate to drive E: and start setup.exe by double-clicking it.

good luck.

---

