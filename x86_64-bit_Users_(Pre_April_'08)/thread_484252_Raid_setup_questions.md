---
title: "Raid setup questions"
date: 2007-06-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by xskull on 2007-06-25
Hello everyone, 

I have recently added another hard drive and I am want to setup 2 of the drives with RAID 1. The only RAID setup I have ever done was with a hardware controller at the office and it seemed to work pretty easily. Linux just took the hardware and ran with it. 

However, with no controller I'm a bit confused using software RAID features. I have read a few posts on the site and the following guides: 

1. [http://www.ubuntu-in.org/wiki/SATA_RAID_Howto#Enable_the_RAID_array]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto#Enable_the_RAID_array")
2. [https://help.ubuntu.com/community/FakeRaidHowto#head-6c678090b3e4d34bdf19fc5cc561b691e8c928c2]("https://help.ubuntu.com/community/FakeRaidHowto#head-6c678090b3e4d34bdf19fc5cc561b691e8c928c2")
3.[ http://users.piuha.net/martti/comp/ubuntu/raid.html]("http://users.piuha.net/martti/comp/ubuntu/raid.html")

Now the drives in questions have 2 partitions. They are both SATA drives and are using an nvidia chipset which is set to RAID1. Both of drives are naturally the same size for RAID 1. At first I was using dmraid and gparted to create and format the partions as instructed in guide 1. Then I noticed webmin was using mdadm which I could basically do the same thing. My first question is which program is preferred or better off to use in the long run? 

I went with webmin, because it was a little easier for me to use. While I'm not totally new to linux, I am still a bit hesitant when it comes to changing things like fstab, etc to mount the drive at boot for example. 

From webmin I created 2 RAID devices /dev/md0 and /dev/md1. md0 is one of the partitions on both of the drives and md1 is the other. Then I just mounted the drives and let webmin do the rest of the work. So my next question is if I set everything up correctly or at least is there a step that I may not have mentioned that I should be preforming?  

So everything appears to be okay, if I run say df I get the following: 

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1            112507072   2671688 104120264   3% /
varrun                  497516       152    497364   1% /var/run
varlock                 497516         4    497512   1% /var/lock
udev                    497516       132    497384   1% /dev
devshm                  497516         0    497516   0% /dev/shm
lrm                     497516     21540    475976   5% /lib/modules/2.6.15-28-amd64-generic/volatile
/dev/hdb1            192292124 116490596  66033608  64% /storage_bin
/dev/md0             403806688   7887396 375407100   3% /projects
/dev/md1              76912416    278624  72726784   1% /archive

```


Now for my next questions. What are some good commands or things that I can run to check on the RAID and see if there are any problems or if both drives are sync properly? And lets say in the event that I mess up my Ubuntu install (which I have done in the past ;) ), do I just follow the steps again to restore the array or will the data be lost? 

Thanks for any assistance!

---

### Post by kuja on 2007-06-27
In the long run, unless you plan on os hopping to something non-linux, you're better off with mdadm. 
If you've got it setup, mounted, and apparently working there's nothing else you'll have to do.
I recommend checking out [tldp's](http://tldp.org/HOWTO/Software-RAID-HOWTO.html) article on RAID, it has a wealth of information on managing mdadm raid arrays.

---

### Post by diesel1 on 2007-06-27
> 

Now for my next questions. What are some good commands or things that I can run to check on the RAID and see if there are any problems or if both drives are sync properly? And lets say in the event that I mess up my Ubuntu install (which I have done in the past ;) ), do I just follow the steps again to restore the array or will the data be lost? 

Thanks for any assistance!

Try cat /proc/mdstat

Also if/when you reinstall, just install mdadm package(might be there already) and you just need to mount the /dev/md0 device somewhere.
Diesel1.

---

### Post by xskull on 2007-06-29
Thanks for the replies. I just wanted to make sure that I wasn't forgetting or overlooked anything before I moved all the data back to the drives since this was my first software RAID setup. Otherwise no, I just plan on using the system as a file and development server so no major OS changes or reinstalls unless I really screw something up :D 

Thanks again.

---

