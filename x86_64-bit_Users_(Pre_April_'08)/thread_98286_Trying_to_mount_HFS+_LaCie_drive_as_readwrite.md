---
title: "Trying to mount HFS+ LaCie drive as read/write"
date: 2005-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by reverendlex on 2005-12-02
I have a LaCie Firewire/USB 2.0 disk formatted in HFS+.  I have no problem mounting it, but it only mounts read only.  I've tried unmounting it and using the 

 mount -rw /dev/sdb6 /media/usbdisk -t hfsplus (as root) 
 
which remounts it fine, but read only again. 

Is there something that I'm missing here? Is there some other way to get a HFS disk to be writable?

Thanks for your help

---

### Post by aysiu on 2005-12-03
[http://www.ubuntuforums.org/showthread.php?t=92141](http://www.ubuntuforums.org/showthread.php?t=92141)

---

### Post by tjm on 2005-12-11
I had success with an external firewire drive showing the same behaviour by simply 'chowning' the entire drive as root.

Assuming the volume is mounted at /media/firewire/ I gave it a

```
sudo chown -R username /media/firewire/
```

and voila, it worked.

---

### Post by vjairam on 2007-06-17
OK. That just didnt work. I tried chown -R root /mount/LACIE All I get is an error stating that it is a read only file system.

---

### Post by RAOF on 2007-06-17
Since that other thread is dead, I'll post here.

The Ubuntu kernel (at least as of Feisty) **does** have write support for **non**-journalled HFS+.  If you've got a journalled HFS+ file system, you're out of luck.

Furthermore, the driver will refuse to mount the filesystem read/write if it was not cleanly unmounted (to prevent serious data corruption).  If the drive is ever not cleanly unmounted, you'll need to run a filesystem checker/repairer on it before you'll be able to mount it read/write again.  Unfortunately, the HFS+ filesystem checker isn't actually packaged for Ubuntu (or wasn't last time I checked).  You can download and build the Apple tools -the howto I followed was on the [Gentoo Wiki]("http://gentoo-wiki.com/HOWTO_hfsplus").  You probably want to read that anyway, there's some good information there.  You can ignore all the "adding kernel support" bits though - we've already got the kernel support.

---

### Post by Limpan on 2007-06-19
> **vjairam said:**
> OK. That just didnt work. I tried chown -R root /mount/LACIE All I get is an error stating that it is a read only file system.

I don't think he meant to do it like that. I believe it was this way around ```
chown -R vjairam /mount/LACIE
```

---

### Post by StarFire on 2007-07-26
In order to mount an HFS+ volume, you need to turn journaling off first.  See thread below. Furthermore, install hfsplus and hfsutils.  [http://ubuntuforums.org/showthread.php?p=1405522](http://ubuntuforums.org/showthread.php?p=1405522)  Yours,  StarFire

---

### Post by scubasteve657 on 2008-03-04
You shouldn't need to install hfsplus or hfsutils; they're either installed by default or not necessary.  As long as journalling is disabled and the file system doesn't need to be checked (like, if you are trying to access a Mac as Target Disc that hasn't been shut down properly) then it should work fine.

---

### Post by CpILL on 2008-06-29
OK, so looking at the [Mac support site]("http://docs.info.apple.com/article.html?artnum=107249") about turning Journaling on/off:
> 
To turn journaling on and off using Disk Utility:

   1. Open Disk Utility (located in Applications/Utilities).
   2. Select the volume to enable or disable journaling on.
   3. To enable, click the Enable Journaling button or choose Enable Journaling from the File menu.

      To disable journaling, choose Disable Journaling from the File menu.

Note: In Mac OS X 10.4 and later, press Option to make Disable Journaling visible in the File menu. 

I'm not sure what it means by this last line? What "option" where?!?

So I went on the command line on the Mac with these helpful instructions:
> 
Disabling journaling via diskutil

You can disable journaling from the Terminal application by using diskutil. Follow these steps:

      1. Log in as an Admin user to the server whose disk you want to set up for journaling.
      2. Make sure that no one is using the server.
      3. Open Terminal (/Applications/Utilities/).
      4. Execute the diskutil command, using the disableJournal option and identifying the volume for which you want journaling disabled. To disable journaling for the root volume, for example, you would execute:

      sudo /usr/sbin/diskutil disableJournal /

      To disable journaling for a volume called MyDisk, you would execute:

      sudo /usr/sbin/diskutil disableJournal /Volumes/MyDisk


---

