---
title: "/Home folder structurally different in 64 bit compared to 32 bit?"
date: 2009-03-20
forum: x86 64-bit Users
---

### Post by Crowd Control on 2009-03-20
Hi there,

So I have been running Ubuntu now for some months, since Vista became increasingly flawed. I am still a big newbie to this OS and computers in general, but thanks to this forum I could bypass most troubles up to now.
Now I had no troubles whatsoever in Hardy, but as of Intrepid I have had some troubles with Wine, loading apps and the desktop content doesn't load every time. 

Now I am not looking for any solutions to the above problems (yet), I thought it may be because I am running on a 64 bit system, whilst 32 bit will suffice anyway. 

During install it was suggested to make a separate partition for /home which I did and by now there is so much content on it, that a backup is not possible anymore in any easy way. But!! that might not have to be a problem. 
I want to try out 32 bit Intrepid (on separate partition first) and see if my system runs better. If that is the case I will keep on using it and format the 64 bit partition. 
Now here is the question:

- Can I access the existing /home folder from the 32 bit version?
- Is this /home folder structurally different from 32 bit, since it was handled with a 64 bit system?

I might have more questions depending on answers to these questions. 

Many thanks in advance.

Grtz CC

---

### Post by D3ath on 2009-03-20
> **Crowd Control said:**
> 
- Can I access the existing /home folder from the 32 bit version?
- Is this /home folder structurally different from 32 bit, since it was handled with a 64 bit system?


You could just save the /home folder on a external hdd then reload with the new install of the 32 bit. There is no difference in the file system. Now accessing the files from the 64bit while in the 32bit that i don't know never tried it. But i wouldn't see why not.

---

### Post by Crowd Control on 2009-03-20
Thanks for your quick answer. Problem is that I don't have a HDD (which is why I said that backup won't be possible in an easy way). I guess if I *did* back it up on an external HDD the problem would remain: a 64 bit system handling the files in question. 
I guess I can at least try and install the 32 bit and make it my third boot partition. But I am still curious if the files already stored with 64 bit lose access speed or something alike by a 32 bit system.

---

### Post by D3ath on 2009-03-20
> **Crowd Control said:**
> Thanks for your quick answer. Problem is that I don't have a HDD (which is why I said that backup won't be possible in an easy way). I guess if I *did* back it up on an external HDD the problem would remain: a 64 bit system handling the files in question. 
I guess I can at least try and install the 32 bit and make it my third boot partition. But I am still curious if the files already stored with 64 bit lose access speed or something alike by a 32 bit system.
 
Sorry 64 bit is something i personally don't know about. I did find this page though.
[http://www.unix.org/whitepapers/64bit.html](http://www.unix.org/whitepapers/64bit.html)
maybe that could help.

---

### Post by 3Miro on 2009-03-20
I was dual booting 32 - 64 bit form months, there is no problem or whatsoever. The file system is exactly the same, the only issue is that a the apps for one wouldn't probably run on the other.

I suppose now you have something liek part 1- /, part 2 - swap, part 3 /home. You need to make another partition (and I don't know what is the best way to do it, I partitioned my hard rive for both 32 and 64bit before I installed anything). The you install the new 32-bit version on that 32-bit partition (both / and /home would be on the same partition). Then when you go to Places you will be able to see and access both 32-bit and 64-bit.

Backing up files on an external hard drive is also an option, there is no difference in the 64 vs 32 bit file system itself. However, if you have both, you need to have separate / and /home folders, you don't want to mix 32 and 64 bit apps and probably setup files.

---

### Post by D3ath on 2009-03-20
> **3Miro said:**
> I was dual booting 32 - 64 bit form months, there is no problem or whatsoever. The file system is exactly the same, the only issue is that a the apps for one wouldn't probably run on the other.

I suppose now you have something liek part 1- /, part 2 - swap, part 3 /home. You need to make another partition (and I don't know what is the best way to do it, I partitioned my hard rive for both 32 and 64bit before I installed anything). The you install the new 32-bit version on that 32-bit partition (both / and /home would be on the same partition). Then when you go to Places you will be able to see and access both 32-bit and 64-bit.

Backing up files on an external hard drive is also an option, there is no difference in the 64 vs 32 bit file system itself. However, if you have both, you need to have separate / and /home folders, you don't want to mix 32 and 64 bit apps and probably setup files.

I totally agree. Its a good investment to have a external HHD. For 100$ you can one well over 100gig. just saying.

---

### Post by Yellow Pasque on 2009-03-20
> I thought it may be because I am running on a 64 bit system, whilst 32 bit will suffice anyway.

Why would you assume those problems are caused by running a 64-bit system? New users tend to blame "64-bit" for all of their problems even if they don't have a good reason to believe it. Here's a great example: [http://ubuntuforums.org/showthread.php?t=1095337](http://ubuntuforums.org/showthread.php?t=1095337)

Also, if you can't back data up, resizing partitions on your hard disk should be a last resort (unless you're not too fond of your data).

---

### Post by Crowd Control on 2009-03-20
Like I said, it might be based on nothing. But on the other hand, all the suggested benefits of 64 do not really apply to me, so I might find 32 bit easier for my system. If 32 bit turns out to be better than 64 in the long run, why not make the switch? I am in no hurry to format my 64 bit partition anyway. Time will tell what is best. 

Taking all your advice in consideration I will try and see what 32 bit will bring me. But as far as I understand 64 bit handling of files does not make a structural difference (haven't read that linky from D3ath yet though).

---

### Post by dcstar on 2009-03-22
> **Crowd Control said:**
> 
.........
- Can I access the existing /home folder from the 32 bit version?
- Is this /home folder structurally different from 32 bit, since it was handled with a 64 bit system?
.........

You cannot boot different **release** versions (32 or 64 bit is irrelevant) because the Gnome version is different and file structures will not match.

Booting a later version will cause problems when you boot back to the old version using a shared /home folder with some apps.

---

### Post by Crowd Control on 2009-03-22
That means in order for dual booting, I need the exact same release version of my current 64 bit version (8.10)?

---

### Post by 3Miro on 2009-03-22
> **Crowd Control said:**
> That means in order for dual booting, I need the exact same release version of my current 64 bit version (8.10)?

I wouldn't do it that way. Even with an exactly the same versions of Ubuntu, there might be different things in /home (like references to /lib vs /lib32 vs /lib64). Make one partition for the 32-bit systema nd use it for both / and /home. That is my advice.

If you have two separate /home folders you can dual boot anything (any versions of Ubuntu, Kubuntu or non Ubuntu Linux in general).

---

### Post by Crowd Control on 2009-03-22
I guess it's slightly more complicated (imo). The current layout is like this:

sda1: Grub
sda2: Swap
sda3: /
sda4: /home 

sdb1: Win partition 1
sdb2: Win partition 2

Now I assigned the bulk of my space to sda4. It is in this folder where not only all my personal preferences are held, but also most of my data is in (series, movies, etc). Sda3 is where the filesystem of 64 bit is installed (and still has about 10 GB left), sda4 has about 150 GB left.

Now most logically I tried to reassign the size of sda4 to just a few GB above it's current amount and hoped it would have the remaining 150 GB unassigned, so I could install the 32 bit Ubuntu there. Unfortunately the partitioning seemed to freeze at 50% of the process. 

The installation of the 64 bit system was somewhat easy as that system is also physically seperated from my Windows partition. Now without being able to back up most of my data (the approximately 320 GB of sda4), how do I proceed? I only care about the data, not the apps (as I have very little installed).

Should I try to edit my partitionsize again? Or from another existing partition maybe?

---

### Post by 3Miro on 2009-03-22
IMO before you mess with partitions you should always backup your data. IMO resizing a partition is always very risky and unfortunately I don't know enough about it to help. As long as the files on the system can be read, you should be able to boot from a live CD and read your data and back it up to a new an external drive or something.

---

### Post by Crowd Control on 2009-03-22
Yeah, but it can't be that an external (or another for that matter) HDD would be the only option. It seems I had the partitioning freeze two times already, However, I did manage to get the 150 GB free ( :/ ), it's a dead part below sda4. Strange, but it's the essential step to get things going now. I just double checked and all the data of both HDD's and all partitions still work and are accessible.
It wasn't possible to install 32 bit, though. I couldn't edit the freed 150 GB in any way, not even the necessary formatting. Seems like I got a rogue 150 GB now.

---

### Post by ahbart on 2009-03-22
@Crowd Control
Sounds to me you're complicating things by creating a seperated partition to make a dualboot 32bit/64bit. I thought you just wanted to switch to 32bit?

If so. 
- Boot from a ubuntu 32bit live cd.
- mount your home partition sda4
- rename the directory with your username on that partition.
- install 32bit ubuntu and use, without! format, sda4 on /home
- Use the same username.
- start your new system

- copy the content (the things you want to keep) of you renamed (old) user directory (/home/old) to you new one (home/username). Like Documents and some settings in .gnome2, .gconf and .local, etc.

In this way you minimise the risks of loosing data. And you have a claen user directory.

---

### Post by Crowd Control on 2009-03-23
> **ahbart said:**
> @Crowd Control
Sounds to me you're complicating things by creating a seperated partition to make a dualboot 32bit/64bit. I thought you just wanted to switch to 32bit?

If so. 
- Boot from a ubuntu 32bit live cd.
- mount your home partition sda4
- rename the directory with your username on that partition.
- install 32bit ubuntu and use, without! format, sda4 on /home
- Use the same username.
- start your new system

- copy the content (the things you want to keep) of you renamed (old) user directory (/home/old) to you new one (home/username). Like Documents and some settings in .gnome2, .gconf and .local, etc.

In this way you minimise the risks of loosing data. And you have a claen user directory.

Aaarrgggh! This was exactly the info I needed.... :-|

Darn, it's too late though. I cut my losses and deleted more than half of what I got (not a real loss, but still). I transferred the remains to my Windows partition and reformatted the full HDD with the 64 bit Ubuntu....

Ah well can't be helped and more of a clean start than this is not possible. Still thanks for your sollution.

---

