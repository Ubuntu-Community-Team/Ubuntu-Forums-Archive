---
title: "Not Enough Space on C:"
date: 2008-08-21
forum: Wine
---

### Post by Rainagul on 2008-08-21
Hi.

Well ive been using wine for some games such as Silkroad Online and other and it works nicely.
However recently i wanted to install TF2 aswell.
I managed to install steam with no problem, but now when i try to install TF2 it gives me an error saying not enough disk space left.
So i checked my wine Cdrive thing and it said 3.2gigs left.
How is that? I have a ton of space left on my C drive, at least 100gigs.

Is there any way to increase the space or anything? Thanks :)

---

### Post by aoanla on 2008-08-21
The mixing of terminology here implies to me that you're using a dual boot system, yes? And you mean your windows partition when you talk about your C: drive having 100Gb free?

Or do you mean that there is 100Gb free on /home ?

Wine creates a "fake" C drive in /home/*your_username*/.wine/drive_c
and pretends, to Windows apps, that this is a real partition. This is for both security and other reasons. It is this "C drive" that things in Wine are talking about. 
Now, if you actually mean that your /home directory has 100Gb free and Wine is still claiming that it only has 3.2 Gb free, that's another matter entirely...

---

### Post by Rainagul on 2008-08-21
Yes im talking about my windows partition having 100gigs left.
Its the fake C drive that only has 3.2gigs left. 
The fake C drive is the one that i want to make bigger, so i can install TF2.

---

### Post by aoanla on 2008-08-21
How did you install Ubuntu? 

Can you give me the output of
df -h
in a terminal?

It is possible to resize partitions on the harddisk so that the partition the fake C drive is on is larger (and hence, the space reported by wine is larger), however this can be a little technical, and there is a small risk of  dataloss (especially if you have to shrink another partition to get free space to expand into). How technically inclined are you feeling?

Otherwise, it may be possible to symlink a subdirectory of the wine "C drive" directory to point to something on (for example) your Windows partition - it would then have a lot more space to play with. I'm not sure how Wine would regard this, as far as the amount of free space it would think it had, though.

---

### Post by Rainagul on 2008-08-21
I used Wubi to install Ubuntu.
Im not sure but i have a small suspicion that because when i installed Ubuntu i only selected 10G for the C space, thats all its giving me. But im not sure. 
As for the output of that command here it is.

> Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G  6.1G  6.2G  50% /
varrun               1007M  116K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M   48K 1007M   1% /dev
devshm               1007M   12K 1007M   1% /dev/shm
lrm                  1007M   44M  963M   5% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       13G  6.1G  6.2G  50% /home/michael/.gvfs
/dev/scd0             4.4G  4.4G     0 100% /media/cdrom0

---

### Post by aoanla on 2008-08-21
Aha.
Since you're using Wubi, it's really easy for you to change the space accessible to Ubuntu, and hence Wine.
Wubi *doesn't* partition your harddisk - instead, it uses a file as a virtual partition, which Ubuntu runs in. It is this file which is limited in size.

Luckily, this also means that increasing the space you have available is as simple as getting Wubi to grow the disk-file.

Follow the instructions for <i>How do I resize the virtual disks?</i> on this link: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

I'd advise using the second method (moving your /home to a separate virtual disk), and, since you have 100Gb+ free on the harddisk, use a value of at least 30000 (about 30Gb).

---

### Post by Rainagul on 2008-08-21
Cool thanks for the link.
However, i enter this command line in terminal
> sudo sh wubi-add-virtual-disk /home 15000
And it says : sh: Can't open wubi-add-virtual-disk.

This is wierd as i downloaded wubi-add-virtual-disk.
Is there somewhere special where i have to put this or?

---

### Post by aoanla on 2008-08-21
If you downloaded it to your Desktop,

cd Desktop

(otherwise, if it went to your home directory, don't bother)

then

chmod +x wubi-add-virtual-disk

(this adds the "executable" property to the file, for you and no-one else)

then

sudo sh ./wubi-add-virtual-disk /home 30000

(for a 30Gb home)

The ./ should ensure that Ubuntu looks for the file in the current directory.

---

### Post by Rainagul on 2008-08-21
Thanks It worked! 
And how do you know so much about what to do xD 
I would not know where to start :p

Thanks so much

---

