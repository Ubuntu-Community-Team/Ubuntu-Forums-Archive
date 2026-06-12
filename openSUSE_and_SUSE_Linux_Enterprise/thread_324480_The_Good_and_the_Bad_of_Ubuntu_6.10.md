---
title: "The Good and the Bad of Ubuntu 6.10"
date: 2006-12-23
forum: openSUSE and SUSE Linux Enterprise
---

### Post by jott27 on 2006-12-23
Ubuntu 6.10 is a great distro. It has many features that makes it easy for new users to migrate to Linux. For the experienced user there are a few of these 'good' features that actually make life a little bit more difficult.
The shortcoming of not being able to have a 'root' login has been discussed often enough, that by now everybody should be convinced that it is not needed. I get by quite easily by using 'sudo' and a root enabled filebrowser like FileRunner.
Very recently my display screen switched to 640x480 mode (VGA) for some unknown reason.
Here is my beef no1: 
No modern type distribution should have internal capability to support this mode. Once you are in this mode it is next to impossible to get out of it. The action buttons are mostly off screen and not accessible. Changing the resolution requires root permission, and even if you manage to reach the selection button, it still did not permit me to change the resolution. I ended up re-installing the system.
Beef no2:
I like to experiment with different distros. For this porpose I have 2 Hard Drives with currently 5 operating systems on them. Once in a while I crash with the need to reboot. Ubuntu 6.10 automatically had all my partitions mounted (/etc/fstab). Rebooting with this setup takes only a few seconds less than forever! Each partition is fs checked !!!
Beef no3:
The installation CD does not have any 'repair' or not even a 'update' function (Maybe someone will prove me wrong here). SuSE 10.1 to the rescue! Would be nice to have it in  Ubuntu too.
Beef no4:
The popularity of Ubuntu has the nasty side effect that installing software via apt-get (synapsis) will quite frequently time out Somewhere there might be a config that controls the timeout time, but not knowing where it is, makes installation a very tidious affair.
Enough of this rant. Future distros will get better and better and will frustrate users like me by not having anything to complain anymore.

Merry Christmas

---

### Post by agger on 2006-12-24
I don't know the answer to your questions, but I do have one myself:

Why is this post in the SUSE forum? It's not SUSE related at all.

---

### Post by ComplexNumber on 2006-12-24
whats more, they STILL haven't fixed the gconf-editor bug. i temporarily installed ubuntu 6.10 the other day. one of the first thigs i do is to change the panel so that the auto-hide delay is zero. so i fired up gconf-editor and change the values. result: no change. this bug was in dapper and breezy too.

---

### Post by jott27 on 2006-12-24
You wrote:
[HTML]   Why is this post in the SUSE forum? It's not SUSE related at all.[/HTML]
It only marginally falls into the SuSE category by pointing out the superiority of SuSE with respect to Updating and Repair. But more to the point, it was my first post to this forum and I was desparately searching for a button to let me post. It was by accident that in the SuSe category I found a 'post' button.
It would be nice if the maintainer of this forum would make it a bit easier to find a 'post' button on the top heading of the forum page. So all what I can do is to appologize for having used up your valuable time in reading a post in the wrong category. By the way, why did you read it ??

---

### Post by xabbott on 2006-12-25
> **jott27 said:**
> ...
Here is my beef no1: 
No modern type distribution should have internal capability to support this mode. Once you are in this mode it is next to impossible to get out of it. The action buttons are mostly off screen and not accessible. Changing the resolution requires root permission, and even if you manage to reach the selection button, it still did not permit me to change the resolution. I ended up re-installing the system.

You could have opened a terminal session to edit xorg.conf, boot into recovery mode,  booted from the live cd mounted the drive,etc. 

> **jott27 said:**
> 
Beef no2:
I like to experiment with different distros. For this porpose I have 2 Hard Drives with currently 5 operating systems on them. Once in a while I crash with the need to reboot. Ubuntu 6.10 automatically had all my partitions mounted (/etc/fstab). Rebooting with this setup takes only a few seconds less than forever! Each partition is fs checked !!!

You choose which partitions you want mounted during the install.

Side note, Agger probably read you post looking for something SUSE related....


> **jott27 said:**
> 
Beef no3:
The installation CD does not have any 'repair' or not even a 'update' function (Maybe someone will prove me wrong here). SuSE 10.1 to the rescue! Would be nice to have it in  Ubuntu too.
Beef no4:
The popularity of Ubuntu has the nasty side effect that installing software via apt-get (synapsis) will quite frequently time out Somewhere there might be a config that controls the timeout time, but not knowing where it is, makes installation a very tidious affair.
Enough of this rant. Future distros will get better and better and will frustrate users like me by not having anything to complain anymore.

Merry Christmas

Are you certain you were timing out on official repos? Maybe you just had bad luck  cause I've never experienced problems with time outs.

With all that said, the beauty of Linux is choice. So when one distro doesn't work out there is another. I personally use Arch and Debian/Ubuntu. I've yet to try Suse 10, the last RPM based distro I used was Suse 8.

---

### Post by jott27 on 2006-12-25
> **xabbott said:**
> You could have opened a terminal session to edit xorg.conf, boot into recovery mode,  booted from the live cd mounted the drive,etc. 
I probably could have, but not knowing this left me with very few alternatives. Are you also saying that if I edit the xorg.conf file by deleting all references to 640x480 I would never be able to accidentally ending up with this antiquated resolution?? This is just super!!! 

> 
You choose which partitions you want mounted during the install.

This choice is easily overlooked and also assumes you know the consequences ahead of time. The choice should not be there in the first place! Mounting a partition should be a deliberate action performed by a individual user and should not be a global affair!

> 
Side note, Agger probably read you post looking for something SUSE related....
I am glad he did.

> 
Are you certain you were timing out on official repos? Maybe you just had bad luck  cause I've never experienced problems with time outs.
The more recent a distro is, the more often you run into this problem. Too many people accessing the source.
Is there actually a place where one can extend the time out ??

> 
With all that said, the beauty of Linux is choice. So when one distro doesn't work out there is another. I personally use Arch and Debian/Ubuntu. I've yet to try Suse 10, the last RPM based distro I used was Suse 8.
There are so many distros out, each providing some new twist one way or another. It is rewarding to explore them, one cannot fail to learn somehing. If it would not for this, I would still use the first issue of Mandrake. It did all the things I need for my day to day needs.

---

