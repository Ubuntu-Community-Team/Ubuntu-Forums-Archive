---
title: "root file system not responding"
date: 2008-12-12
forum: x86 64-bit Users
---

### Post by ddevore on 2008-12-12
I am using 8.10 64bit on a HP dv9000 laptop and have a problem where the root file system stop responding. When I got to work and unpacked my laptop the last two mornings I have found that the root filesystem has stopped responding. I first tried to access the root file system via nautilus and after not responding for a while I went to a terminal screen and tried "ls /" which never responded.

Specifics of the computer:
Ubunut 8.10 64bit
HP dv9000 laptop (AMD dual core 64 bit)
The root partition is on the second HD first partition (sdb) and is ext3
I only have 2 partitions (aside from the swap) root and home both ext3
Power Settings:
On AC Power: never sleep, blank screen upon closing the lid.
On Battery Power: sleep after 20 mins, suspend when lid is closed, shutdown when battery power is critically low. 


I notice the problem after unpacking the laptop in the morning. I close the lid usually before unplugging it. 

If there is anything else you would like to know please let me know.

---

### Post by lensman3 on 2008-12-12
What happens with the "df" command?  Do you see your all partitions?  What does the file "more /etc/mtab" have in it?  Do you see all your partitions?

If you do a "du -a /", how far does it proceed before it hangs?  

If you can get to root, you might try "/sbin/fdisk -l /dev/sda".  This will list the partitions and it just might give you an idea as what is wrong.  This behavior is as if a network disk is missing and the network then hangs.  I have had something like this happen with nfs.

What does "dmesg" report? You might have to run it as "dmesg | more" because out 2000 lines will be dumped from the kernel message queue.

Good luck.

---

### Post by ddevore on 2008-12-20
This happened on another computer, my desktop. It is also running Ubuntu 8.10 64 bit desktop version. The same thing happened. I was using gnome commander and went to the root directory and it froze. Wanting to check another way I went and checked in a terminal and it froze. I pulled this thread up on my laptop and went through the commands in the previous reply and this is what I found: 

df -> froze part of the way through
du -a / -> executed what appeared to be fine tell about half way through it and it froze for a couple of seconds and finally continued. When it continued the terminal and gnome commander freed up also.

I started working through the commands to try and see what happened and found that df actually froze when trying to query the NSF drives, which are also mapped and used on my laptop. So what appears to be happening is this. 

Both computers have the same NSF drive off my server running Ubuntu 6.04 32bit server. 

Desktop: It appears that the NSF drive went to sleep or something and stopped responding making the query of the NSF drive to hang causing any ls command on the root to freeze. 

Laptop: I was running the laptop on my network where the NSF drive is available and when I tried to perform a ls on the root when it wasn't available anymore it froze. 

It appears that if a NFS drive is mounted and becomes unavailable that it will hang a command that is trying to perform an action on it. 

Though this is annoying it does not appear to be a fatal error and can be recovered from, though it might require a reboot, I would like a solution for if this happens again. Once the problem is found I tried to unmount it which didn't work. I got an error device is busy.

---

### Post by albinootje on 2008-12-20
> **ddevore said:**
> 
Both computers have the same NSF drive off my server running Ubuntu 6.04 32bit server. 


What exactly did you actually mount over NFS ?

If i have my /home mounted over NFS, and the NFS-server becomes unreachable for some reason, then the whole desktop is unavailable.

---

### Post by ddevore on 2008-12-20
I am mounting a /data basically a backup/share drive. If /home is an NFS drive it would make since that the desktop would become unusable since the desktop is based on your home directory.

What brought mine back was doing the du -a and it started responding once it reached the /data directory. So if you could do try to do alt-f1 to open a terminal and attempt du -a /home. I don't know if this will work because the terminal will likely try to open in the home directory.

---

### Post by albinootje on 2008-12-20
> **ddevore said:**
> I am mounting a /data basically a backup/share drive. If /home is an NFS drive it would make since that the desktop would become unusable since the desktop is based on your home directory.

What brought mine back was doing the du -a and it started responding once it reached the /data directory. So if you could do try to do alt-f1 to open a terminal and attempt du -a /home. I don't know if this will work because the terminal will likely try to open in the home directory.

I just gave a real-life example of what i've seen in the past.
It would only come back to live the moment the NFS-server was reachable again. :|

---

### Post by ddevore on 2008-12-27
Is there any solution to this problem? If I am on my laptop I may not have the /data nsf drive available and in that case it will never wake up, I have to reboot in this case.

---

### Post by albinootje on 2008-12-27
> **ddevore said:**
> Is there any solution to this problem? If I am on my laptop I may not have the /data nsf drive available and in that case it will never wake up, I have to reboot in this case.

Temporarily comment out your nfs share line in /etc/fstab after booting in the "recovery mode" is an idea.
Or manually mount the NFS share after a boot.

How exactly are you using NFS on your machine ?

At work I'm using autofs + NFS + samba.
Maybe that setup is better for your scenario.

---

### Post by ddevore on 2008-12-27
I am mounting it in fstabs so it mounts automatically. The problem isn't that it tries to mount upon bootup. If it is not available at bootup then it fails and all is fine. If the drive is available at bootup it boots just fine. The problem is that if I take the laptop off the network without shutting it down. In this case the NFS drive is no longer available and it locks up any command that tries to use it. Rebooting fixes the problem but I want to see if there is a way to unmount the drive once I am off the network. If I try to unmount it this is what I get

ddevore@holiday:~$ sudo umount /data
umount.nfs: Server failed to unmount 'foundation:/data'
umount.nfs: /data: device is busy
umount.nfs: Server failed to unmount 'foundation:/data'
umount.nfs: /data: device is busy

Rebooting is not always convenient.

---

### Post by albinootje on 2008-12-27
> **ddevore said:**
> I am mounting it in fstabs so it mounts automatically. The problem isn't that it tries to mount upon bootup. If it is not available at bootup then it fails and all is fine. If the drive is available at bootup it boots just fine. The problem is that if I take the laptop off the network without shutting it down. In this case the NFS drive is no longer available and it locks up any command that tries to use it. Rebooting fixes the problem but I want to see if there is a way to unmount the drive once I am off the network. If I try to unmount it this is what I get

ddevore@holiday:~$ sudo umount /data
umount.nfs: Server failed to unmount 'foundation:/data'
umount.nfs: /data: device is busy
umount.nfs: Server failed to unmount 'foundation:/data'
umount.nfs: /data: device is busy

Rebooting is not always convenient.

Okay, so you want to suspend your laptop, right ?
Make sure you close down all application that use /data before you try the unmount of /data
This command can help finding out what application is still using /data in case it's unclear :
```

lsof | grep -i "/data"

```

---

### Post by ddevore on 2008-12-27
This would be great but the lsof command freezes also.

This is a real pain..

---

### Post by albinootje on 2008-12-27
> **ddevore said:**
> This would be great but the lsof command freezes also.

This is a real pain..

$ man umount

> 
       -f     Force unmount (in case of an unreachable NFS system).  (Requires kernel 2.1.116 or later.)


---

### Post by ddevore on 2009-01-02
The force option works as long as I kill all processes that are showing as using /data in a ps -aef | grep /data 


Is this a bug? 
Is there a way to have a smarter NFS?
Would this require an enhancement request to fix?

Thanks for all the help.

---

### Post by albinootje on 2009-01-02
> **ddevore said:**
> The force option works as long as I kill all processes that are showing as using /data in a ps -aef | grep /data 


Is this a bug? 
Is there a way to have a smarter NFS?
Would this require an enhancement request to fix?


Don't know. 
But you have the choice between the kernel- and the userland NFS server software, both available in the Ubuntu repositories.

nfs-user-server - User space NFS server
nfs-kernel-server - support for NFS kernel server

Perhaps the other one works better with this ?
There's also others :
[http://freshmeat.net/projects/nfs-ganesha/](http://freshmeat.net/projects/nfs-ganesha/)

GL!

---

