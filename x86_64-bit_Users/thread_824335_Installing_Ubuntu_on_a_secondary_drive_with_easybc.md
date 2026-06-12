---
title: "Installing Ubuntu on a secondary drive with easybcd"
date: 2008-06-10
forum: x86 64-bit Users
---

### Post by devonharlan on 2008-06-10
So Basically I am new to Linux. I tried dual booting with Ubuntu installed on the secondary sata drive in my laptop. I wasn't sure how to configure Grub. When i restarted I got error 17. I was able to fix the MBR with the vista recovery Cd. I want to try and install again only using Easybcd but I am not sure how to go about doing this. Any help would be much appreciated.

---

### Post by Kilz on 2008-06-10
> **devonharlan said:**
> So Basically I am new to Linux. I tried dual booting with Ubuntu installed on the secondary sata drive in my laptop. I wasn't sure how to configure Grub. When i restarted I got error 17. I was able to fix the MBR with the vista recovery Cd. I want to try and install again only using Easybcd but I am not sure how to go about doing this. Any help would be much appreciated.

Since its a windows based boot cd, you may have better luck getting answers [on the Easybcd forums.]("http://neosmart.net/forums/")

---

### Post by meierfra. on 2008-06-10
EasyBcd uses Grub to boot Ubuntu.  So  I suggest to let us help you solve your Grub problem. But we would need some information:

Does the Grub menu appear at boot up?

Boot from the Ubuntu Live CD. Open a terminal (Applications->Accessories->Terminal) and post output of

```
sudo fdisk -l
```
(l is a lowercase L)

Then go to "Places->Computer". One of icons is for your Ubuntu partition. Double click it. Go to /boot  and then /boot/grub. That folder contains the file "menu.lst". Post the  content of "menu.lst"

---

### Post by devonharlan on 2008-06-11
The problem is I don't know where to install grub when I install ubuntu. I've tried putting it on hd0,0 that didn't work so i tried putting it on the same partition as ubuntu which is the second partition of the secondary drive. they all just keep giving me grub errors at startup. so i have to load up vista with the disk and rewrite my mbr. Then i open easy bcd and set it to install grub on the same drive that i installed on. when i reboot i can go into grub but it just says error loading neolinux please insert disk o something like that.

---

### Post by meierfra. on 2008-06-11
If you post the information I requested I can show you  how to setup Grub correctly, without  overwriting the MBR on the Vista drive.

Do your bios allow you to change the boot order of the hard drives?

---

### Post by devonharlan on 2008-06-12
I have to reinstall ubuntu first.

---

### Post by meierfra. on 2008-06-12
> I have to reinstall ubuntu first.

Why? Did you delete Ubuntu?

---

### Post by devonharlan on 2008-06-12
Yaeh I had to do some figitting with my partion table. I am going to install again tomorow and i am almost certain that I can change the boot order on my bois. So i would change it to the drive that has linux on it to boot first. Then set the partion i installed on as the root?

---

### Post by meierfra. on 2008-06-12
> So i would change it to the drive that has linux on it to boot first.
Yes


>  Then set the partion i installed on as the root?

I'm not sure what you mean.  If you are using manual partitioning,  mount the Ubuntu partition at "/". If you have a seperate /home partition mount it at "/home".  I would NOT  use seperate "/boot" partition. 


Also at step 7 of the installation, click on "advanced". This will let you choose the location for the "boot loader". Choose  the hard drive  Ubuntu is on.  So for example if Ubuntu is on  partition /dev/sdb3, then choose  "/dev/sdb". 

Once the installation is done, don't reboot immediately. Instead check whether "menu.lst" is correct:


```
mkdir ubuntu
sudo mount -t ext3 /dev/sdb3 ubuntu
cd ubuntu/boot/grub
sudo cp menu.lst menu.lst.bu
gksudo gedit menu.lst
```

(Of course in place of /dev/sdb3 use the partition ubuntu us on)

Look for the line


# groot=(hd?,?)

If the first number is not 0 change it to 0.

look for

title ubuntu ....
root (hd?,?)

again if the the first number is not 0, change it to zero.

To the same thing with the next two titles (recovery and memtest)

Save the file.

Now reboot and you should be able to boot into Ubuntu.

---

### Post by devonharlan on 2008-06-12
Right as i got to the end of the installation i got this message
"Executing 'grub-install /dev/sdb' failed.

This is a fatal error."
So what did I do wrong?

---

### Post by devonharlan on 2008-06-12
To add more info I installed on dev/sdb1 and "/". i had successfully switched the boot order in bios.

---

### Post by Kilz on 2008-06-12
> **devonharlan said:**
> Right as i got to the end of the installation i got this message
"Executing 'grub-install /dev/sdb' failed.

This is a fatal error."
So what did I do wrong?

Set the drive you want to install ubuntu to to boot first before installing anything. I had to open my brothers computer and change the master and slave drives around. Some let you do it in the bios.

---

### Post by meierfra. on 2008-06-12
> Set the drive you want to install ubuntu to to boot first before installing anything.

The OB already did that.

> 
So what did I do wrong?

I don't think it is your fault.

Lets' see whether "menu.lst" got create and what's in your grub folder:

```
mkdir ubuntu
sudo mount -t ext3 /dev/sdb1 ubuntu
ls ubuntu/boot/     ( This lists all the file in your boot folder)
ls ubuntu/boot/grub  ( This lists all the file in your grub folder)

```

**If the grub folder contains the "stage2" file**

```
sudo grub 
```
and at the "grub>" prompt

```
find /boot/grub/stage2
```
(this should "return (hd1,0)"

Still at the "grub>" prompt:

```
root (hd1,0)
setup (hd1)
quit
```

**If the grub folder contains "menu.lst":**

 Edit "menu.lst" like I told you in my previous post.

**In any case: ** 

Post the output of all the commands and also the contents of "menu.lst"

Boot from the Ubuntu drive

I don't have much hope that  this will be successful, mostly I'm trying to gather some information, so that I can figure out what is going on.

---

### Post by devonharlan on 2008-06-12
so this is what i get
"ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sdb1 ubuntu
ubuntu@ubuntu:~$ ls ubuntu/boot/
abi-2.6.24-16-generic         initrd.img-2.6.24-16-generic.bak
config-2.6.24-16-generic      memtest86+.bin
grub                          System.map-2.6.24-16-generic
initrd.img-2.6.24-16-generic  vmlinuz-2.6.24-16-generic
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ ls ubuntu/boot/grub
default     e2fs_stage1_5  jfs_stage1_5    reiserfs_stage1_5  stage2
device.map  fat_stage1_5   minix_stage1_5  stage1             xfs_stage1_5
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd1,0)
root (hd1,0)
grub> setup (hd1)
setup (hd1)"
After I entered the setup command i got grub error 17: cannot mount selected partition.

---

### Post by devonharlan on 2008-06-12
I ran all the commands and this is what i got

"ubuntu@ubuntu:~$ mkdir ubuntu 
ubuntu@ubuntu:~$ sudo mount -t est3 /dev/sdb1 ubuntu 
mount: unknown filesystem type 'est3' 
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sdb1 ubuntu 
ubuntu@ubuntu:~$ ls ubuntu/boot/ 
abi-2.6.24-16-generic         initrd.img-2.6.24-16-generic.bak 
config-2.6.24-16-generic      memtest86+.bin 
grub                          System.map-2.6.24-16-generic 
initrd.img-2.6.24-16-generic  vmlinuz-2.6.24-16-generic 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ ls ubuntu/boot/grub 
default     e2fs_stage1_5  jfs_stage1_5    reiserfs_stage1_5  stage2 
device.map  fat_stage1_5   minix_stage1_5  stage1             xfs_stage1_5 
ubuntu@ubuntu:~$ sudo grub 
Probing devices to guess BIOS drives. This may take a long time. 

       [ Minimal BASH-like line editing is supported.   For 
         the   first   word,  TAB  lists  possible  command 
         completions.  Anywhere else TAB lists the possible 
         completions of a device/filename. ] 
grub> root (hd1,0) 
root (hd1,0) 
grub> setup (hd1) 
setup (hd1) 

Error 17: Cannot mount selected partition 
grub>" 


Upon startup there is no grub at all. It see's there is nothing on the first disk the boots the second.

---

### Post by meierfra. on 2008-06-12
Try 

```
sudo grub
root (hd1,0)
setup (hd1,0)
quit
```

(this won't help you booting Ubuntu, but I want to see whether you get the same error message)


Is there any chance that  the MBR  of your  external drive is  write-protected? Check your bios.


Get supergrub (see my signature) See whether it lets you boot into Ubuntu:   

Choose "!LINUX! (1) AUTO" at the first screen after booting from the SuperGrub CD.

If that did not work, press "c"  and type

```
 find /boot/grub/stage2
```

(press "esc"to get back to the regular screen)

You might also explore some of the other options in supergrub.

---

### Post by devonharlan on 2008-06-12
this is the result of the terminal commands

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd1,0)
root (hd1,0)
grub> setup (hd1,0)
setup (hd1,0)

Error 17: Cannot mount selected partition
grub> 


And this is what i got in super grub

when i choose !LINUX! (1) Auto
I got Error 15 : file not found
So i went and entered the code (twice for good measure)
And got Error 27 : Unrecognized command

---

### Post by devonharlan on 2008-06-12
Out of all that it did do something. It wouldn't boot at all at startup it just had the dash in the upper corner. I had to go into bios and filp flop the drives to boot into windows. I forgot to do the mnue.lst deal that you asked me to do awhile ago. Would that make any difference?

---

### Post by meierfra. on 2008-06-12
> I forgot to do the mnue.lst deal that you asked me to do awhile ago. Would that make any difference?

No. since you never reached the Grub menu, this does  make any difference.


I really don't understand what is going on.


Try this. Boot from the SuperGrub Disk

Super Grub Disk (No Help)
English Super Grub Disk
Advanced
Gnu/Linux (Advanced)
Fix Boot of Gnu/Linux (Grub)
Manually Restore Grub in Hard Disk (MBR)
Manually Restore Grub in Hard Disk (MBR)
Choose your Ubuntu Drive (If you pick the wrong one, you should notice it at the next step and you can go back to correct it)
Choose your Ubuntu Partition
Choose your Ubuntu Drive (same one as above)
Press "c" and then type reboot.

Again I'm pretty sure this will not work. I expect that at the place where you are supposed to pick your Ubuntu drive, your Ubuntu drive does not show up.

This would mean that your bios are not able to access your Ubuntu drive.
Are there any setting in the bios you could  change?

If none of this works, you might have to  create a boot partition for Ubuntu on the other drive.

---

### Post by meierfra. on 2008-06-12
You might also read the first few posts in this thread:

[Grub Error 17]("http://ubuntuforums.org/showthread.php?t=442945")

---

### Post by devonharlan on 2008-06-12
I'll give that a try.
Here is what i got from the super grub
set out_device+(hd0)
set out_hd+hd0
set out_linux_letter+a
set out_lide_hd+hda
set out_lscsi_hd+sda
set out_hard_hd=hd0
hack
set aux_hd=hd0
root (hd1,0)
  Filesystem type unkown, partition type ox7
setup (hd0)
error 17 : cannot mount selected partition


the unkown file system is what makes me wonder if the installation is completely screwed. Do you think i should burn a new live cd and try to completely reinstall?

---

### Post by meierfra. on 2008-06-12
> the unkown file system is what makes me wonder if the installation is completely screwed. Do you think i should burn a new live cd and try to completely reinstall?

 I don't really have any better suggestion, so you might as well try that. 
You might also consider  to install Ubuntu on your Windows drive.
Did you had a look at your bios?

---

### Post by devonharlan on 2008-06-12
Yeah I did what was suggested on th error 17 thread. After the computer loads bios it just goes to a blimking dash in the corner. 
So when i reinstall I will insatll on /dev/sdb1 partition and put grub on /dev/sdb and have the second disk load first. Hopefully that will work. Oh and should i just reformat my drive from windows or just do it while i install ubuntu?

---

### Post by meierfra. on 2008-06-12
> Oh and should i just reformat my drive from windows or just do it while i install ubuntu?

I would let Ubuntu do it.

---

### Post by devonharlan on 2008-06-12
Sounds good I am going to install right now

---

### Post by devonharlan on 2008-06-12
I got that same grub fatal error again. It was a brand new cd so something else must be the problem.

---

### Post by meierfra. on 2008-06-12
The only other suggestion I have is to either install Ubuntu on the Windows drive, or at least create a small boot partition on the Windows drive. The easiest way to do this:

Use Visa Disk Management to shrink you  Vista Partion by 300MB.
Use Gparted or Vista Disk Managemen to create a ext3 partition  from the 300MB.

Reinstall  Ubuntu. But choose manual partitioning. Mount the new 300MB partition at /boot and sdb1 at /.   Install Grub to /dev/sda (should be the default). 

If it fails you will have to  fix the MBR again. (Easiest way: SuperGrub, pick "Win->MBR Win" at the first screen)

---

### Post by devonharlan on 2008-06-12
I'll try that. If it fails I'll just install on the disk w/ vista.

---

