---
title: "serious problem"
date: 2009-09-27
forum: x86 64-bit Users
---

### Post by thundaraptor on 2009-09-27
My computer just froze up after I tried to watch a movie.  This has happened in the past but of late has happened with much less frequency.  When it happens, I have to reboot with gparted to fix the disk.  Normally, it doesn't seem to effect the system.  This time, it erased everything I had inside mozilla thunderbird including the lighting parameters, ie all my servers were deleted out.  luckily for me, i use imap so the servers will have all my mail still.  i have been ignoring this problem with the computer freezing because in the past, it didn't seem like anything major was happening other than a major inconvenience to me.  now, if this is going to facilitate damage to things internal to the system, i really need to figure out and I don't know what is happening.  can someone direct me to understanding how to trouble shoot this?  thanks.  

for the record, I have a custom box that i build.  amd 2.6 ghz chip with asus motherboard and ati hd 4670 dual head card setup in big desktop mode with ubuntu jaunty 64 bit.

---

### Post by QIII on 2009-09-28
Are you using ext4?

---

### Post by thundaraptor on 2009-09-28
I am not certain, what is the command to check this?

---

### Post by QIII on 2009-09-28
Although it is not likely that you are using ext4 in Jaunty, I don't know how you set up your partitions.  ext4 was a bit unstable early on with Jaunty, and errors in file transfers that were interrupted were wreaking havoc on the disk.  Wiping out big chunks of data, causing OS errors, etc.

```
sudo fdisk -l
``` 

should give us a peek at the disk format.

That is a small "ell", not a "one".

---

### Post by thundaraptor on 2009-09-28
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e7930

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            3368      120238   938766307+  83  Linux
/dev/sda2          120239      121601    10948297+   5  Extended
/dev/sda3               1        3367    27045396   83  Linux
/dev/sda5          120239      121601    10948266   82  Linux swap / Solaris

Partition table entries are not in disk order

```

I have had an interesting go with the partitions.  Originally, I had just the main 1tb partition.  I installed a copy of jaunty 64 on it and also installed a regular non 64 jaunty on the same partition.  Eventually, I deleted out randr in the 64 bit version which pretty much made that system defunct.  So I decided to create a 25 gb partition to have the main OS on.  I theoretically wiped both partitions, although not sure how effective it was, then reinstalled jaunty 64 on the 25 gb partition and told the system to own a directory on the 975 gb partition to keep all my data inside. that way if the os dumped again, I wouldn't have quite as much to worry about. 

My explanations of 975/25 are not exact when you look at the table above.  Those numbers were just my intentions and the only way I know to articulate.  

Thanks

---

### Post by QIII on 2009-09-28
Bah!  I was thinking fdisk would specify ext3/4.

I think you will actually have to look at /etc/fstab.

Sorry, I'm not at my Ubuntu machine...

---

### Post by thundaraptor on 2009-09-28
i went into gparted and it says

dev/sda3  ext 2
dev/sda1  ext 2
dev/sda2  extended
dev/sda5  linuxswap

---

### Post by falconindy on 2009-09-28
ext4 shouldn't be an issue with Jaunty. Stability issues were supposedly resolved in the 2.6.28 kernel, which Jaunty uses. I used to get hard freezes somewhat irregularly. Sometimes twice a day, and sometimes only one every 2-3 days. Not to alarm you, but ever since I had a hard drive crash on me 2 weeks ago, the freezes have gone away.

---

### Post by thundaraptor on 2009-09-28
when I had my two displays in clone mode, and before i had the hard drive partitioned it was super stable.  plus, this always crashes in relation to accessing a video file so I think it has something to do with a video card/driver conflict. somewhere but like a monkey with no opposable thumbs, i am not skilled enough to solve this.

---

### Post by oboedad55 on 2009-09-28
You can use the partition editor to see what file systems you have.

---

### Post by thundaraptor on 2009-09-28
it totally just crashed again.  it almost always happens when I am opening a movie file.  this one was an avi.  the wierd thing is that sometimes it is flawless and other right as I go to open the movie file, the entire system freezes.  maybe there is a serious ubuntu guru out there who can answer this mystery.  i would almost pay money for it cause i know my two non thumb hands aren't going to figure it out...

---

### Post by oboedad55 on 2009-09-28
> **thundaraptor said:**
> it totally just crashed again.  it almost always happens when I am opening a movie file.  this one was an avi.  the wierd thing is that sometimes it is flawless and other right as I go to open the movie file, the entire system freezes.  maybe there is a serious ubuntu guru out there who can answer this mystery.  i would almost pay money for it cause i know my two non thumb hands aren't going to figure it out...

Well, I don't know if there are any serious gurus here. Most of us are just clowning around. If you want to pay for support, here you go: 
[http://www.ubuntu.com/support/services](http://www.ubuntu.com/support/services)

---

### Post by QIII on 2009-09-29
Which player are you using?

Try a different one and see if you get the same issue.

Also, try unplugging one of your monitors and adjusting your graphics controller so it's not running in big desktop mode.

Try to run the movie in a couple of different players again.

Let's see if we can rule out the player or the video set up.

We may get down to seeing if it is the ATI driver for your card, or if the mode you are using is causing issues.

Troubleshooting is more often a process of elimination than anything else.

---

