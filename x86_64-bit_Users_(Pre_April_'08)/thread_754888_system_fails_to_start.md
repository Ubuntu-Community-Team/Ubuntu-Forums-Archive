---
title: "system fails to start"
date: 2008-04-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by sanjeevan on 2008-04-14
i installed kde. then after i restarted the next day. it didn't start so i started using the terminal mode. it starts the automatic file check (fsck) and failes.
This is partial output:

```

* An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the 
root filesystem mounted in read-only mode.

* The root filesystem is currently mounted in read-only mode. 
A maintenance  shell will now be started.
After performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system. 

```

This is common to me because if normal ubuntu doesn't start it do that. After that the system usually restarts and everything works. But now it shows the following:

```

bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found

```

---

### Post by gsmanners on 2008-04-14
You should check your /etc/fstab. In fact, you should probably post it here for reference.

---

### Post by sanjeevan on 2008-04-14
i remeber after intalling kde, i tried this thread.
[http://ubuntuforums.org/showthread.php?t=203093](http://ubuntuforums.org/showthread.php?t=203093)

it wasn't successfull so i just turned off. then it stopped working next time i turn it on.
this is what cat /etc/fstab shows. sorry about the spacing and stuff.

```

#/etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
     proc                  /proc                  proc    defauls        0            0
# /dev/sda6
UUID=6f683075-90b7-4cdb-a640-23d12cc6d3d6 /                  ext2 defaults,errors=remount-r 0 1
# /dev/sda1
UUID=BC3AD68E3AD64554 /media/sda1 ntsf defaults,umask=007,grid=46 0
1
# /dev/sda2
UUID=9E70DCD770DCB6ED /media/sda2 ntsf defauls,umask=007,grid=46,0
1
# /dev/sda4
UUID=4C6AE30E6AE2F41C /media/sda4 ntsf defauls,umask=007,grid=46,0
1
# /dev/sda5
UUID=7484648C846452A2 /media/sda5 ntsf defauls,umask=007,grid=46,0
1
/dev/hda   /media/cdrom0    udf,iso9660 user,noauto,exec 0             0

```

that's the output.
sorry if there is any errors since i had to see the console output and manually enter. thanks.

---

### Post by gsmanners on 2008-04-15
You're really using ext2 for your root partition? I wouldn't be too surprised if it was corrupted. Maybe a backup and reinstall is in order.

---

### Post by sanjeevan on 2008-04-15
how do i backup the drivers? that's the biggest problem for me. it took me long time to get vide and audio installed and working. otherwise, yeah.

---

### Post by gsmanners on 2008-04-16
Maybe Ubuntu isn't right for you if you have to worry about things like that. Everything should "just work" with maybe a little tweaking or installing a package from the repos.

---

### Post by Yellow Pasque on 2008-04-16
I would suggest a reinstall with the Kubuntu 8.04 beta.

What video and audio device do you have?

---

### Post by sanjeevan on 2008-04-17
> **gsmanners said:**
> Maybe Ubuntu isn't right for you if you have to worry about things like that. Everything should "just work" with maybe a little tweaking or installing a package from the repos.

pretty much why i installed ubuntu. i suck at it.

don't worry about the audio and video. i will try to fix it. thanks.

---

