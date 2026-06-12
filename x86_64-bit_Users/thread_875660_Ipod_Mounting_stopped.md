---
title: "Ipod Mounting stopped"
date: 2008-07-31
forum: x86 64-bit Users
---

### Post by hasaang on 2008-07-31
I have an 80gb Ipod Classic (the newest one) and it used to mount fine but now it wont work at all. I keep on getting an error message saying it wont mount. After searching around in the forums I found the only way for it to work is if I run 

sudo modprobe -r ehci_hcd

however this makes it loose usb 2.0 support and the speeds of transfers slow down to a crawl. Is there anything I can do to keep the same speed. Any help will be greatly appreciated.. Thanks

---

### Post by soxs on 2008-07-31
First reboot to get the module loaded again, you just unloaded.
{you can do this by ```
modprobe <modulname>
``` instantly}

you may try to force mount it.

Create a folder somewhere (preferabli at $HOME/Desktop), named "xyz":
```
mkdir $HOME/Desktop/xyz
```

mount it: 
Note:
check now if sda2 is a fs partition, your os is running on or some other internal stuff, don't use that one in the following

An iPod has 2 partitions sda1=firmware sda2=music
You will have to try sda2 sdb2 sdc2 sdd2 sde2
```
sudo mount /dev/sdb2 $HOME/Desktop/xyz
```


After doing that, you can backup your music via gtkpod (```
sudo apt-get install gtkpod
```)

Now clear any data from your iPod (aka reset to factory state) and select your language and you should be fine again, unless you changed some mount options.

So you may first post the output of:
```
cat /etc/fstab
```
```
cat /etc/mtab
```
```
ls -Al /media
```

---

### Post by hasaang on 2008-07-31
Unfortunate I cant force mount it keeps on saying that it does not exist. The only one that gave a response was sda2 but it says I must specify the filesystem type

---

### Post by hasaang on 2008-07-31
never mind I figured out the mount was sdc1

Thanks a lot for your help problem solved. Amazing how quickly this was resolved you guys always impress!

---

### Post by soxs on 2008-07-31
> **hasaang said:**
> never mind I figured out the mount was sdc1

Thanks a lot for your help problem solved. Amazing how quickly this was resolved you guys always impress!

There is a "Thank you" Button, use it when you feel like^^

---

