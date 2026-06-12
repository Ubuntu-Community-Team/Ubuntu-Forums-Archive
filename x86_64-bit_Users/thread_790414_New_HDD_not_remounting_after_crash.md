---
title: "New HDD not remounting after crash"
date: 2008-05-11
forum: x86 64-bit Users
---

### Post by Keldek on 2008-05-11
Hello again. I've run into a bit of a sticky problem here...

First and foremost, the important info:

Ubuntu 8.04 x86_64 using ubuntu studio desktop
Firefox 3 Beta 5 with ubufox stuff installed
added 4th hdd, encrypted.

Ok, so I'm browsing the web looking for an answer to something I completely forgot, which ended up leading me to this site: [http://ubuntuguide.org](http://ubuntuguide.org) ; which, as you may know defaults to the Gutsy guide.

As soon as I tried to open the tab to view this guide, my screen went blank, and ultimately resulted as an automatic reboot.

Now, when I reboot, my newest hdd (/dev/sdd1) will not auto mount. I'ts almost as if it's not being seen in my /etc/fstab file. I also didn't see any messages, error or otherwise, regarding this drive. When I was setting this drive up I made a typo and when the system tried to mount it during boot up, it flagged an error message, in which I had to press "Ctrl + D" to continue. I received no such error or prompt this time around.

I can manually mount the disk however, by following these steps:

```
sudo cryptsetup luksOpen /dev/sdd1 /dev/mapper/sdd1_crypt
```

enter the luks passphrase, then

```
sudo mount /dev/mapper/sdd1_crypt /mnt/work
```

The mount actually takes a little longer than it used to, I'd say 30 seconds to 1 minute; as opposed to almost instant when I initially set the disk up.

So i double check everything, and it all seems in order.

The entry in my /etc/fstab for this particular device is as follows:

```
/dev/mapper/sdd1_crypt   /mtn/work   ext3   defaults   0   0
```

But it will no longer mount on reboot after this crash.

I should add that yes, it was mounting fine on reboot prior to this crash, so that's not an issue there.

I'm at a loss as to why the disk is no longer remounting, and am hoping someone out there could point me in the right direction.

Thanks in advance.

Edit: I should also note that I am 100% sure it was trying to view the ubuntuguide.org site that lead to the crash. I had the problem a while ago when I installed the base system, and thought I got rid of the problem but alas, it's back :(

Edit 2: fsck shows the device as clean:
```
keldek@System-X:~$ sudo fsck.ext3 /dev/mapper/sdd1_crypt
e2fsck 1.40.8 (13-Mar-2008)
/dev/mapper/sdd1_crypt: clean, 121750/18317312 files, 52483214/73258143 blocks

```

---

### Post by Keldek on 2008-05-11
Issue resolved.

Somehow the entry in /etc/crypttab for /dev/sdd1 was removed when the system crashed/rebooted.

Edit: Now to find out why ubuntuguide.org is making my system crash :lolflag:

---

