---
title: "Help! My kids deleted the Radeon video driver . . ."
date: 2009-04-22
forum: x86 64-bit Users
---

### Post by holatte on 2009-04-22
We're trying Ubuntu on the new HP 64-bit comp (tried to do Fedora 10, but even with an expert on the Fedora Forums walking us through, it still wouldn't recognize the video card).

The video card is Radeon 4350.

I got home last night to discover that my 7 & 9 year old had gotten out of bed and ended up deleting the video driver (the qualifications of the babysitter are for another venue entirely).

I reinstalled it, but now when I boot up all I can see is the Ubuntu logo on the top 5th of the screen, distorted. I can boot in recovery mode, but have no idea what to do from there.

When I did my tech support training, the only Linux training I got was installing/troubleshooting Red Hat 4 (6 was the current version at the time; go figure).  Just fyi. (I did have an instructor in one of my introductory software classes have us do a dual-boot with XP and Mandrake, but that's all we did with it.)  ---I'm posting this on my business laptop (which they aren't allowed to touch at all); the desktop is used by the family and for them to log into their internet-based school.

All help is appreciated.

---

### Post by 3Miro on 2009-04-22
Apart from the babysitter, there are some other interesting questions. How is it possible for someone to unistall a video driver without the password, or is it that you have only one account and everyone in the household knows the password. For future advice (especially when there are kids in the family), create another account. That is one account for you (and maybe other adults) that will do administration on the computer and one account for general family use. The second will not have superuser privileges an therefore will be kids safe.

For the driver, well I don't know much about drivers and setting, but you can now try to uninstall it properly, reboot to make sure it is working and then install it again.

---

### Post by bgerlich on 2009-04-22
Post the contents of the file /var/log/Xorg.0.log and the output of a console command lshw.

---

### Post by holatte on 2009-04-22
> **bgerlich said:**
> Post the contents of the file /var/log/Xorg.0.log and the output of a console command lshw.

That file: /var/log/Xorg.0.log  shows nothing, as in, there's nothing in it.

lshw shows only part of the information and I can't scroll back up to the top.  Here's what is showing:

```


        bus info: scsi@4:0.0.0
        logical name:  /dev/sdc
*-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@4:0.0.1
       logical name:  /dev/sdd
*-disk-2
       description: SCSI disk
       physical id:  0.0.2
       bus info: scsi@4:0.0.2
       logical name:  /dev/sde
*-disk:3
      description: SCSI Disk
      physical id: 0.0.3
     bus info: scsi@4:0.0.3
     logical name:  /dev/sdf
*-network DISABLED
      description:  Wireless interface
      physical id: 1
      logical name:  wlan0
      serial:  00:22:5f:3e:e1:e5
      capabilities:  ethernet physical wireless
      configuration: broadcast=yes  multicast=yes  wireless=IEEE 802.11bg

```

---

### Post by holatte on 2009-04-22
Just did   lshw -short     and it still cut a bunch of stuff off.

It's an AMD quad-core processor with 6G of RAM and 1T hard drive---I know it cut that off, although don't think it's going to help solve this issue. Then again, that's why I'm asking, eh?

---

### Post by agathian on 2009-04-22
when you boot in regular mode and get distorted display.. type ctrl-alt-f1, all simultaneously. it will take you to the text console. login and from there you collect the X long, lshw, etc.. and post here..

-A

---

### Post by Sef on 2009-04-23
> For future advice (especially when there are kids in the family), create another account. That is one account for you (and maybe other adults) that will do administration on the computer and one account for general family use. The second will not have superuser privileges an therefore will be kids safe.

To create a second account without admin powers:

System > Administration > Users and Groups > Unlock > Add User

---

