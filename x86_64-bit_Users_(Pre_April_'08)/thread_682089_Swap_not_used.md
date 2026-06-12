---
title: "Swap not used"
date: 2008-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by High_Yield on 2008-01-29
Hi-

I have a new AMD x2 4600+ running 1 gig of 800 mhz RAM.
Also I have a swap partition set up, all partitions using ext3.

Now:
-  I always run the sys monitor to keep track of things and have never seen the swap file used - ever!  This is fine by me but I decided to test if it worked today by loading many programs.  When the memory got full, the PC simply ground to a near halt - mouse glitchyt, 5 minutes between click events, it was awful.  And never did I see the swap used.
- I opened GParted to make sure my swap was "OK" and noticed that all the other partitions except the SWAP have a "Padlock" icon next to them.

So:
A) Why is my swap not being used ?
B) What does the "Padlock Icon" mean in GParted, and also why not padlock for my swap.

- b

---

### Post by logos34 on 2008-01-29
the lock means a partition is mounted.

try

**sudo swapon -a**

How is it listed in /etc/fstab?

maybe replace the 'UUID=' with **/dev/<partition> **

---

### Post by prince_niceguy on 2008-01-29
also check in the following file /etc/sysctl.conf is there a parameter of

vm.swapiness

if yes, make it around 50 and then reboot your comp or run the following command

sudo sysctl -p

that should make sure that swap is being used if there is need.

---

### Post by Kilz on 2008-01-29
> **High_Yield said:**
> Hi-

I have a new AMD x2 4600+ running 1 gig of 800 mhz RAM.
Also I have a swap partition set up, all partitions using ext3.

Now:
-  I always run the sys monitor to keep track of things and have never seen the swap file used - ever!  This is fine by me but I decided to test if it worked today by loading many programs.  When the memory got full, the PC simply ground to a near halt - mouse glitchyt, 5 minutes between click events, it was awful.  And never did I see the swap used.
- I opened GParted to make sure my swap was "OK" and noticed that all the other partitions except the SWAP have a "Padlock" icon next to them.

So:
A) Why is my swap not being used ?
B) What does the "Padlock Icon" mean in GParted, and also why not padlock for my swap.

- b

I use conky and never see swap used either.  I now have 2 gb , but when I had 1gb it was never used. I think next time I install I am going to remove it, or make it real small.

---

### Post by NightwishFan on 2008-01-29
My system is a little weaker than the first posters.
AMD Athlon 64 x2 3800+
895mb ram etc
128mb integrated Nvidia

I can run every app i have (all the open office, games, movies playing) and i still get consistant compiz cube and water effects, My swap is hardly used. There might be some other issue.

---

### Post by High_Yield on 2008-01-30
> **logos34 said:**
> the lock means a partition is mounted.

try

**sudo swapon -a**

How is it listed in /etc/fstab?

maybe replace the 'UUID=' with **/dev/<partition> **

I get this from your  swapon command:
<
swapon: cannot canonicalize /dev/disk/by-uuid/835da321-231c-42d4-ad67-df0a7923be48: No such file or directory
swapon: cannot stat /dev/disk/by-uuid/835da321-231c-42d4-ad67-df0a7923be48: No such file or directory
>

I have not yet looked at the other file..   I have also seen, briefly as the PC comes out of standy, a message to the effect of "swap is not turned on"...

Will look at fstab in a bit (son wants to play with a puzzle...)

- B

---

### Post by High_Yield on 2008-01-30
Here's the contents of my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ab3de36e-5cfa-48df-b0e9-085c4274caf4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=73842526-0035-477f-8a9f-7980e716c698 /home           ext3    defaults        0       2
# /dev/sda6
UUID=6BD7BAD84657A4A1 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=835da321-231c-42d4-ad67-df0a7923be48 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


Any help is appreciated - B

---

### Post by utUtu on 2008-01-30
> **High_Yield said:**
> I get this from your  swapon command:
<
swapon: cannot canonicalize /dev/disk/by-uuid/835da321-231c-42d4-ad67-df0a7923be48: No such file or directory
swapon: cannot stat /dev/disk/by-uuid/835da321-231c-42d4-ad67-df0a7923be48: No such file or directory
>

I have not yet looked at the other file..   I have also seen, briefly as the PC comes out of standy, a message to the effect of "swap is not turned on"...

Will look at fstab in a bit (son wants to play with a puzzle...)

- B

That's the reason your 'swap' is not used.  You don't have a valid swap partition.  The problem is the UUID is wrong in your fstab.  To find the correct UUID, use blkid.

Pls post the results of this command -  free -m

---

### Post by High_Yield on 2008-01-30
Thanks all.

I ran the "blkid" command you suggested, copied the GUID from sda2(my swap), pasted it into fstab replacing the old guid and rebooted.  The swap "appears" to be on now.  If I run free -m I see a "swap" line.  Also - in GParted I see a "padlock" icon next to the swap partition - so I guess it's found and mounted.

So thanks all !!!!
 
For what it's worth tho:
1) what is the "blkid" command ? (Any neat-o information appreciated)
2) I think "swapon" should run automatically I would hope?  How can I check to see that it is in fact running ?

- B

---

### Post by prince_niceguy on 2008-01-30
For what it's worth tho:
> **High_Yield said:**
> 
1) what is the "blkid" command ? (Any neat-o information appreciated)

blkid is to get the disk id for the partitions on the disks. Normally /dev/sdaXX or /dev/hdaXX is fine in /etc/fstab. However, ubuntu prefers using bulkid, I am not sure why. So, blkid can be used instead of /dev/sdaXX or /dev/hdaXX in the /etc/fstab.
> **High_Yield said:**
> 
2) I think "swapon" should run automatically I would hope?  How can I check to see that it is in fact running ?

- B
Just reboot your computer, if it is there in /etc/fstab, then your swap will become ON on the start of your comp.

After reboot, run the command free or top and it should give value of swap being used.

---

### Post by utUtu on 2008-01-30
> **High_Yield said:**
> Thanks all.

I ran the "blkid" command you suggested, copied the GUID from sda2(my swap), pasted it into fstab replacing the old guid and rebooted.  The swap "appears" to be on now.  If I run free -m I see a "swap" line.  Also - in GParted I see a "padlock" icon next to the swap partition - so I guess it's found and mounted.

So thanks all !!!!
 
For what it's worth tho:
1) what is the "blkid" command ? (Any neat-o information appreciated)
2) I think "swapon" should run automatically I would hope?  How can I check to see that it is in fact running ?

- B

you can always get some help/info by passing the param --help.
Or you can use man *command*

---

### Post by High_Yield on 2008-01-31
> **prince_niceguy said:**
> For what it's worth tho:

blkid is to get the disk id for the partitions on the disks. Normally /dev/sdaXX or /dev/hdaXX is fine in /etc/fstab. However, ubuntu prefers using bulkid, I am not sure why. So, blkid can be used instead of /dev/sdaXX or /dev/hdaXX in the /etc/fstab.

Just reboot your computer, if it is there in /etc/fstab, then your swap will become ON on the start of your comp.

After reboot, run the command free or top and it should give value of swap being used.

When you say "It is there" - I assume you mean the swapon command when I asked about.
So I ran a ```
cat /etc/fstab | grep 'swapon'
``` and it returned nothing.  I guess I was asking about what/where runs the swapon command during bootup?

Thanks  -B

---

### Post by prince_niceguy on 2008-01-31
> **High_Yield said:**
> When you say "It is there" - I assume you mean the swapon command when I asked about.
So I ran a ```
cat /etc/fstab | grep 'swapon'
``` and it returned nothing.  I guess I was asking about what/where runs the swapon command during bootup?

Thanks  -B
run the following command

> more /etc/fstab|grep swap

If it returns a row with /UUID.... then it means the swap entry is already present in the fstab. Swap is loaded during the boot process, if an entry is present in /etc/fstab.

you do not need to run swapon in that case. It would be mounted when the files systems from /etc/fstab are mounted by the boot process.

---

### Post by Yellow Pasque on 2008-02-01
You can also confirm your swap is working with a: ```
free -m
```
or
```
dmesg | grep swap
```

```
dan@harvest:~$ sudo dmesg | grep swap
[   31.924932] Adding 5662872k swap on /dev/sda5.  Priority:-1 extents:1 across:5662872k
dan@harvest:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1888        549       1339          0         23        299
-/+ buffers/cache:        226       1662
Swap:         5530          0       5530

```

---

### Post by gmjs on 2008-05-11
I'm having similar problems under Ubuntu 7.04, only my system refuses to use swap even when down to only 7MB RAM free.

**# free -m**

```
             total       used       free     shared    buffers     cached
Mem:           503        495          7          0         13        303
-/+ buffers/cache:        178        324
Swap:         1004          0       1004
```

I've added the swap partition to fstab (/dev/sda6  swap  swap  defaults 0 0).

I don't know what I'm doing wrong.  I really noticed a slow-down recently, but can't think of anything I've done to affect this.

The only thing that I'm doing that might be a problem (I don't know enough about how swap partitions work) is sharing this swap partition with another Linux distro on another partition (it seemed silly to make a new one when I'll never be using both distros at once - probably a bad idea).

Does anyone have any ideas?  I'm stuck!

There's less free RAM than in Windows!

---

