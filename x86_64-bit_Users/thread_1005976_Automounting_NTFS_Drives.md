---
title: "Automounting NTFS Drives"
date: 2008-12-08
forum: x86 64-bit Users
---

### Post by CapTlnsano on 2008-12-08
Quick question that I can't find any other previous posts address: 

I'm simply trying automount an NTFS partition at startup because i'm sick of manually doing it every time. 

The device I want to mount is at: 

sdb

partitons 5-7:

/dev/sdb5/Data   mounted at /media/Data
/dev/sdb6/Games-Apps  mounted at /media/Games-Apps
/dev/sdb7/Music-Movies mounted at /media/Music-Movies

I'm sure there's a smarter way of mounting devices, just havnt found it, so if anyone has a better way lemme know. 

Anyway, I had thought it might be as simple as using the session manager and just feeding commands in such as:

sudo mkdir /media/Data && sudo mount /dev/sdb5/Data 

Yea, while i don't get any errors, i don't get any results either. Because these are NTFS partitions do i need to specify the file system type? I donno, like i said - easy one, i'd appreciate the pointer.

---

### Post by albinootje on 2008-12-08
The problem with NTFS-formatted partitions is that sometimes they're labeled "dirty" by MS-Windows. In that case you can't mount them automatically in Linux with the default options.

Try : man ntfs-3g 
and read the examples part and the bit about the "force" option.

Another option is to install the package ntfsprogs and use the ntfsfix
tool from that to fix that.

from the ntfsfix manual page :

ntfsfix  is  a  utility  that  fixes  some common NTFS problems.  ntfsfix is NOT a Linux version of chkdsk.  It only repairs some fundamental NTFS
       inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows.

       You may run ntfsfix on an NTFS volume if you think it was damaged by Windows or some other way and it cannot be mounted.

---

### Post by CapTlnsano on 2008-12-08
Thanks, Al. I'll give it a go and see what happens. I'll post with an update either way.

---

### Post by tjandracom on 2008-12-09
[QUOTE="CapTlnsano"]I'm simply trying automount an NTFS partition at startup because i'm sick of manually doing it every time. [/QUOTE]

then you have to edit file /etc/fstab

add every partition you want to mount everytime your computer starts.
it should look like this:

```

/dev/sdb5   /media/Data          ntfs  defaults   0    0
/dev/sdb6   /media/Games-Apps    nffs  defaults   0    0
/dev/sdb7   /media/Music-Movies  ntfs  defaults   0    0

```

for information, please read:
```
man fstab
```

---

### Post by tentaro on 2009-04-29
[I]I added the drive I wanted to fstab and when I restarted it seemed to automount but when using File Manager, I couldn't open the drive up and see the folders inside. The thing is this is my media drive and I can access it and mount it with File manager but I would prefer since my music, pics and wallpapares are on that drive that it would just be mounted from the start so I don't have to mount it then go into each program and reassign the drive and folder to get the wallpaper slideshow or pic viewer or amarok to recognize the media again. It's kind of annoying.

Plus another question is:

If when I mount it normally it has a folder under media tehn why is everything telling me to create a folder under /mnt? Just wondering if that is the difference and can I automount to the media dir? [/I]

---

### Post by joey-elijah on 2009-04-29
There is a simple GUI way to auto-mount NTFS partitions called 'NTFS Configuration editor' and you'll find it in Add/remove. You just make sure your NTFS drive is unmounted/ejected, run it, select it. done.

I use it on an NTFS drive and it works flawlessly.

---

### Post by tentaro on 2009-04-29
Thanks for the quick reply but I decided to try one more time to vi the fstab and now I am good. I used the existing dir in the media folder I had already been mounting too instead of making a new one in /mnt folder and it works great my pics and wallpapers all come up when I log in and now I just have to rescan my music one last time.

I just love this community. I can't say it enough.

---

