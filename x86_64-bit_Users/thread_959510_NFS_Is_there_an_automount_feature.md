---
title: "NFS: Is there an automount feature?"
date: 2008-10-26
forum: x86 64-bit Users
---

### Post by xandones on 2008-10-26
I have both Ubuntu 8.04 and Win XP PRO SP3 on the same machine. 
I have no problem in using my files in the NFS system, but it's very boring to wait for the Rhythmbox 0.11.5 to search for my music files. Is there a way to avoid repeating the search for files?

---

### Post by cariboo on 2008-10-26
Have a look here:

[http://www.arsgeek.com/2006/11/01/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable-with-ntfs-3g/](http://www.arsgeek.com/2006/11/01/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable-with-ntfs-3g/)

This should help with your problem.

I assume you meant NTFS and Not NFS, if you did mean NFS look here:

[http://ubuntu-tutorials.com/2006/10/20/network-file-system-nfs-ubuntu-606-610/](http://ubuntu-tutorials.com/2006/10/20/network-file-system-nfs-ubuntu-606-610/)

Jim

---

### Post by xandones on 2008-11-07
What I really want is to make Linux automount my NTFS partitions before login. In other words: I want to keep the icon that appears after I open the partitions for the first time. I'm posting this because I had a lot of problems with broken packages, so I would like to avoid installing stuff until I be a bit less noob.:popcorn:

---

### Post by cariboo on 2008-11-07
I'm not sure if this mounts the drive before you log in, but give it a try, in a terminal type:

```
sudo gedit /etc/hal/fdi/policy/preferences.fdi
```

and chenge the following line:

```
<merge key="storage.automount_enabled_hint" type="bool">false</merge>
```

to this:

```
<merge key="storage.automount_enabled_hint" type="bool">true</merge>
```

This will mount your internal drives automagically.

Jim

---

### Post by Funnnny on 2008-11-08
Thanks, I have to edit /etc/fstab and it works fine. But your way is quicker :D

---

### Post by xandones on 2008-12-05
If your NTFS partition isn't mounting, try using Checkdisk with both checking options enabled. It worked for me... ):P

---

