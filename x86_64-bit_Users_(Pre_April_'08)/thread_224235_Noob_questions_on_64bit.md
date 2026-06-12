---
title: "Noob questions on 64bit"
date: 2006-07-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by fredricsolstad on 2006-07-27
Hi, 
First off I would like you to be patient with me since I am somewhat of a noob when it comes to Linux.. I've run into a couple of problems with Ubuntu 64bit which are: 
Mounting 2 extra harddrives (one PATA (normal IDE) and one SATA) and getting my Brother DCP 115C to work.. 

First off then.. 
Mounting the extra harddrives.. Ubuntu finds them, but does not let me mount them (saying that only Root can do so), so I've tried to mount them using:
```
sudo mount /dev/hdb1 /media/pata2/ 
```  

My FSTAB file looks as follows: 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /pata2          reiserfs   defaults              1 2
/dev/sda1       /sata1          reiserfs   defaults              1 2

``` Like I said, I'm a noob so I have most likely forgotten something.. 

Second, my Brother DCP-115C... 

I've found a smashingly good how-to here on the forums (the one for the MFC210), but my problem is that Brother does not supply any 64-bit versions of Cupswrapper and LPR.. so, I'm wondering if anyone out there has had any success getting a brother multifunction machine working on a 64 bit version of Ubuntu. 

Thanks in advance

---

### Post by Kilz on 2006-07-27
Im not the greatest at mounting things, but maybe we can figure it out. Are you saying the drives do not auto mount? 
It looks like these are the lines for those drives
```

/dev/hdb1       /pata2          reiserfs   defaults       1 2
/dev/sda1       /sata1          reiserfs   defaults       1 2
```

Do the /pata2 and /sata1 directories exist in the file system? They have to be there already for the drives to be mounted there. I see you are trying to mount them to /media/pata2/ manualy. If you want one mounted there automaticly the line would be.

```
/dev/hdb1       /media/pata2          reiserfs   defaults       1 2
```

When I added a drive I just copied the options from the one that was mounted. You might try that.

```
/dev/hdb1  /media/pata2  reiserfs defaults,errors=remount-ro 0       1
```

---

### Post by fredricsolstad on 2006-07-28
Thanks a million for the answer! Im going to try that out at once

---

### Post by BobSongs on 2006-09-23
> **fredricsolstad said:**
> 
Second, my Brother DCP-115C... 

I've found a smashingly good how-to here on the forums (the one for the MFC210), but my problem is that Brother does not supply any 64-bit versions of Cupswrapper and LPR.. so, I'm wondering if anyone out there has had any success getting a brother multifunction machine working on a 64 bit version of Ubuntu.Smashingly good? Cool! I've had that tutorial described in many ways but smashingly? That's very kind. Sounds so British! I say.

I don't have a 64-bit machine. I was "this close" to buying one but opted instead for a MacBook Pro, 32-bit. I think I'll wait a good 3 years before I go 64-bit. You may have to contact Brother about 64-bit drivers and when they're going to roll out. They still don't have the full selection of 32-bit drivers yet.

---

### Post by fredricsolstad on 2006-10-02
> Smashingly good? Cool! I've had that tutorial described in many ways but smashingly? That's very kind. Sounds so British! I say.

Hehe, I do get that alot.. That I sound British. I am however not from the UK, I'm a swede, so I guess I'll have to blame my teachers for the way I sound. Apparently I sound posh when speaking english aswell (according to my wife who has spent a large part of her life in Charlotte, NC).. 

Anyhow.. 

Back to my questions.. I was trying out SuSE 10.1 (I actually bought the box) and found that mounting the second and third harddrive was extreamly simple. I cannot however, no matter how hard I try, get my SATA disk to mount as SATA1 when I boot the machine. And still no joy when it comes to the DCP-115C, I can get it to scan an image, but that is about it. So I'm going to trade my DCP for a HP multi machine that my friend has since HP machines are supposed to "work out of the box" in Ubuntu. 

right.. went off track there again.. 

Anyone that has a couple of harddrives mounted, up and running that want to share their FSTAB with me?

Thanks in advance :)

---

### Post by fabertawe on 2006-10-02
> **fredricsolstad said:**
> Anyone that has a couple of harddrives mounted, up and running that want to share their FSTAB with me?

Thanks in advance :)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>      <options>                          <dump>  <pass>
proc            /proc           proc        defaults                           0       0
/dev/hda2       /               ext3        defaults,errors=remount-ro         0       1
/dev/hda1       /media/hda1     ntfs        defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb1       /media/hdb1     ntfs        defaults,nls=utf8,umask=007,gid=46 0       2
/dev/hdb2       /media/storage  ext3        defaults                           0       2
/dev/hdb3       /media/fat32    vfat        iocharset=utf8,umask=000           0       2
/dev/sda1       /media/sda1     ntfs        defaults,nls=utf8,umask=007,gid=46 0       2
/dev/hda3       none            swap        sw                                 0       0
/dev/hdc        /media/dvdrw    udf,iso9660 user,noauto                        0       0
/dev/hdd        /media/cdrom    udf,iso9660 user,noauto                        0       0
```

sda1 is my SATA drive, if that's any use to you. I use it for multi-track recording under Windows. I dual boot off hda. hdb is my backup drive.

Paul

---

### Post by fredricsolstad on 2006-10-02
> sda1 is my SATA drive, if that's any use to you. I use it for multi-track recording under Windows. I dual boot off hda. hdb is my backup drive.

Paul

Thanks a million! I'm gonna give it a go once I get home from my grandparents on wednesday. I'll keep you posted on the progress. 

Thanks again! :D 

//Fredric

---

### Post by mrehorst on 2006-10-02
I ran into a similar problem and found that the thing that was hanging me up, even though I changed the umask setting, was the "defaults" settings.

'defaults" are defined on man page "mount" (open a terminal and type "man mount".  They are  

defaults
     Use  default  options: rw, suid, dev, exec, auto, nouser, and async.

If I recall correctly, the "nouser" default was a problem.  From the man page::

    nouser  Forbid an ordinary (i.e., non-root)  user  to  mount  the file system.  This is the default.

I corrected the problem by editing out "defaults" and specifically adding all of the default options back in except "nousers".

Of course, I am no expert and have no idea if I have compromised the security of the machine by doing this...

MR

---

### Post by fredricsolstad on 2006-10-02
okay, I'll check that aswell :) 

Thanks for the tip :)

---

