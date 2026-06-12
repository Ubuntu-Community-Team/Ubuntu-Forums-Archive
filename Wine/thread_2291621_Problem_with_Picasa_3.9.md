---
title: "Problem with Picasa 3.9"
date: 2015-08-21
forum: Wine
---

### Post by Malcolm_Brown on 2015-08-21
Problem with Picasa 3.9


I have a Toshiba Satellite Pro C50-A-1K9 running Ubuntu 14.04 LTE 64 bit.


I installed Wine and Picasa 3.9.140 (Build 239) for Linux


I have partitioned my hard disk and my pictures are stored on a partition called '/dev/sda4' which is formatted as NTFS (hopefully to assist recognition by Windows programs!).


Under the Picasa menu option {Tools, Folder Manager} only two drives are listed - drive C: (the Wine drive) and Z: (the Ubuntu system drive).  The partition /dev/sda4 does not appear.


How can I get Picasa to read in my pictures from the other partition?  It would be a pity to have to copy the whole lot (80Gb) over to drive Z: or C: 


Any suggestions would be appreciated.


Thanks.


Malcolm

---

### Post by oldfred on 2015-08-21
Are you mounting the NTFS partition with fstab?
I used to have photos in NTFS partition when still booting XP. But now in ext4 partition. Picasa worked with both, except now for upload to Google which we do not use.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[URL="https://help.ubuntu.com/community/Fstab"]https://help.ubuntu.com/community/Fstab

[/URL]
 [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

   For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

      
 ** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD

     
[       ]("https://help.ubuntu.com/community/Fstab")
 ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

    [URL="https://help.ubuntu.com/community/Fstab"]
[/URL]

---

### Post by ajgreeny on 2015-08-21
Is the partition mounted at boot by the system?

I don't use Picasa or wine, but if the ntfs partition is mounted in the ubuntu system it should appear in the mountpoint folder which will be either where you set it to mount in /etc/fstab or somewhere in /media if you mount it by clicking on the partition icon in the file manager.

I have also moved this thread to the wine forum where I think you will get better help.

EDIT:
Ah-ha!  Ninja'd by oldfred, who I suspect knows more about this than I do, so follow him and his thoughts.

---

