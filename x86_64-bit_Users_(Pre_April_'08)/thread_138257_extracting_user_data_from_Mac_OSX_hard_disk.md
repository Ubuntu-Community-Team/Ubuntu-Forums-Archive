---
title: "extracting user data from Mac OSX hard disk"
date: 2006-03-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by magicfab on 2006-03-01
Hello,

My brother's Mac G4 recently died and I'd like to recover the data on the hard disk and burn to DVD so he can read it on his new Powerbook. I am not sure what formats to use when backing up / burning the info, hoping anyone here could help me.

The drive mounts OK in Ubuntu (using 5.10), I can see under Users/daniel all his info is there, but it's 30GB of stuff. What are the essentials I should keep ? I've also noticed some files/folders icons have a red cross icon on the top right corner and a lock on the bottom right corner - can't seem to read those, including for example AddressBook.data in Users/daniel/Libreary/Applications Support/AddressBook. How to solve this ?

In any case it's going to be several dozen GBs of data. What would be the best archival method to let him access directly the data from several DVDs without having to copy to hard disk first ? This may seem naive but I am thinking there must be something better than just direct file-to-DVD burning.

After the data has been recovered, what would be the best way to "clean it" but leave it usable for someone with a compatible mac ?

Thank for any advice on this.

---

### Post by ssam on 2006-03-01
just copying the files onto the disk should be fine. you could put them in a tar.gz archive if you wanted, mac os x can open those fine. compressed files are more vunerable to corruption if the disk gets scratched, so i'd recommend not compressing.

if you brother is planing reinstall all his applications on a new mac then you should only need to back up his personal data. this will all be in /Users . If he wants to avoid the hassle of reinstalling all his software you could back up /Applications aswell. he may still need to put in all the serial numbers again.

the red crosses mean that you dont have permission to read the files. if you're brother does not mind losing permission information you could change the permissions to something that you can read. maybe this thread will help [http://ubuntuforums.org/showthread.php?t=123785](http://ubuntuforums.org/showthread.php?t=123785)

wait untill he is happy with the dvds before you wipe the drive. if you want to do this securly you can zero all the bits. (if you are very paranoid then you can overwrite the disk with random bits several times). first you have to find out what device it is. run
```
mount
```
and see if you can spot which is the hfs disk. then get the bit on that line that looks like /dev/hdb2 or /dev/sda1. take the number off and run
```
sudo fdisk -l /dev/hdb
```
where you put in the device you got above. this will list the partitions on that disk so that you can double check that its the right one.

now unmount the disk
```
sudo umount /dev/hdb
```
and zero it
```
sudo dd bs=1024 if=/dev/zero of=/dev/hdb
```
but please make sure you put the right device in other wise you might wipe the wrong disk

---

