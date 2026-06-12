---
title: "Ubuntu 7.10 doesn't recognize the windows xp pro partition"
date: 2008-03-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by vligu on 2008-03-01
Hello,
well im a new bie to Linux and i just installed Ubuntu 7.10 at a 2GB RAM, AMD 3800+ 64bits machine. I have now a dual boot machine one of those OS is win xp pro. Since i installed ubuntu i cant see my win xp pro partition. It seems that it doesn't recognize it. I use a reifers file system to ubuntu. So i can't access win xp pro from ubuntu neither to see that partition. I have been a linux user before and i had ubuntu 6.10 and everything was perfect. I was able to access win xp pro before, offcourse not to write on it but read only. Can anyone pls help me?
Thanks for any help!

---

### Post by logos34 on 2008-03-01
Does fdisk see it?

**sudo fdisk -l**

Maybe you just need to add a mount point or tweak it.  Install the** ntfs-config** gui and reconfigure XP partition:
[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by vligu on 2008-03-01
well i dont use a terminal to see it, i just use the GNOME environment and i go to places and there is no a partition like windows. I mean i have a swap partition a / part. and a /home partition, but the win xp part. is hiden. At previous version i mean Ubuntu 6.10 after installation the windows partition was detected automatically (read only) but now it doesnt.

---

### Post by logos34 on 2008-03-01
Could you possibly have accidently installed ubuntu over it?  

Fdisk output or **sudo gparted** will show your total disk space and whether it's still there.

---

### Post by vligu on 2008-03-01
well maybe bc i had a live cd but it wasnt so good so i took a new one and did the job. And the when i installed ubuntu the gpart detects the partition but now i cant access it.

---

### Post by Yellow Pasque on 2008-03-01
you need to mount it. You'll need to know the /dev/ path you got from the fdisk command. You'll also need a directory to mount to, so:
```
cd /media
sudo mkdir windisk
sudo chmod 777 windisk
sudo mount -t ntfs-3g -o rw,auto,exec,user,uid=1000 /dev/<path>  /media/windisk
```
To mount it every time you start your computer, you need to add an entry in /etc/fstab (*sudo gedit /etc/fstab*)
```
/dev<path>  /media/windisk    ntfs-3g  rw,auto,exec,user,uid=1000   0   0
```

---

### Post by C. Wizard on 2008-03-02
fstab file in K/Ubuntu is unlike anything I've seen in other linux distributions and I found my XP partition mounted as /media/sda1
You might look for it there.
Good luck.

---

### Post by hodge24 on 2008-03-02
This may sound like a bit of a dumb/obvious suggestion, but also make sure that windozzze has shut down cleanly - if it hasn't, then Ubuntu won't mount the partitions. Sometimes my XPoo will not shut down correctly, and when I boot into Ubuntu, I can't see the XPoo partition. I just have to reboot into XPoo and make sure it shuts down cleanly :)

---

### Post by Yellow Pasque on 2008-03-02
> **hodge24 said:**
> This may sound like a bit of a dumb/obvious suggestion, but also make sure that windozzze has shut down cleanly - if it hasn't, then Ubuntu won't mount the partitions. Sometimes my XPoo will not shut down correctly, and when I boot into Ubuntu, I can't see the XPoo partition. I just have to reboot into XPoo and make sure it shuts down cleanly :)
This can be overcome by mounting with the force option, but it would be best to shut down cleanly as you said.

---

