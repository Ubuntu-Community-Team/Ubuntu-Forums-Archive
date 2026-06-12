---
title: "RAID 0 setup chrashes when GRUB shall install"
date: 2008-07-01
forum: x86 64-bit Users
---

### Post by slope on 2008-07-01
I used the alternate xubuntu CD to set up software raid.
I first watched the screencast video for raid [screencasts.ubuntu.com/20070910_installing_ubuntu_part_2_968x544.html]("screencasts.ubuntu.com/20070910_installing_ubuntu_part_2_968x544.html") and it seemed easy.
I strted out setting it up and it all runned like a charm. After I was done with the partioning and raid configure my disks looked like this:

```

RAID0 device #0 1.5 TB Software RAID device
      #1 1.5 TB F ext3          /
SCSI1 (0,0,0) (sda) - 750.2 GB ATA ST3750330NS
      #1 primary  745 GB K raid 
      #2 primary  5.2 GB F swap         swap
SCSI2 (0,0,0) (sdb) - 750.2 GB ATA ST3750330NS
      #1 primary  745 GB K raid 
      #2 primary  5.2 GB F swap         swap 

```

From what I understand it should all be correct like this and I just continued the process. It all went nice until I tried to install GRUB. It just would not install. I tried LILO as well but same result, no install of LILO either. 

Here is the error message I get:
```

Unable to install GRUB in (hd0)
Executing 'grub-install  (hd0)' failed.
This is a fatal error.

```

I'll tried LILO hoping for the best but I got error from LILO also:

```

LILO installation failed
Running "/sbin/lilo" failed with error code "1".

```

Could it be that GRUB do not see this raid 0, so installer does not know where to write the bootsector or what it is called. Do I maybe need to do something else to get a boot sector?

Is ther anything that might cause the GRUB error?

Possible that raid 0 is impossible to boot from?
Maybe there are some hardware issues to my motherboard? [Asus P5N E SLI]

Have anyone solved a problem like this before? Is there something that I can do manually for the install to complete?


Btw: This is a clean install so I do not need to worry about data on the disks. It is a new install of xubuntu 8.04 64 Bit

---

### Post by slope on 2008-07-01
Hmm. Seems I can continue the istallation without GRUB/LILO. There is an option to go on with installation without bootloader.

```

               Continue without bootloader
                 No bootloader installed

You will need to boot manually with the /vmlinuz kernel on partition 
/dev/md0 and root=/dev/md0 passed as kernel argument

```

I am sure this is a good tip ;-) except I do not understand what it means or how I should boot manually. How can I solve this manually?

Searching the web I find various comments on what will work and what not. Getting really confused here.

See this:
[Setting up software Raid]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/") 

> 
D Webber Says:
July 15th, 2007 at 3:36 pm

Grub is &#8220;RAID aware&#8221; to the extent it can boot from a RAID 1 mirror (but apparently no other RAID level).


I am getting confuesed here. Must I really either go and buy an expensive raid controller card or go back to running Windows :confused: for having a working Raid 0?

---

### Post by slope on 2008-07-02
Bump

Surely someone must be able to give me pointers here? 
What do I do next?
Doable at all in Linux or switchback to windows?

---

### Post by slope on 2008-07-02
Could I maybe use a live CD and boot from CD. Then start a terminal and manually create a MBR and install GRUB into that MBR?

Maybe its possibel to run gparted or similar tool to fix this?

---

### Post by saru411 on 2008-07-02
Every time I build a software raid array on my machine it installs Lilo. From what I remember Grub doesn't support Raid booting(this might just be RAID5 though). I would scrape you current partitions, make a /(which means root), /swap(about double your ram capacity), and /Home(this is where your files shall live meaning if you ever have to reinstall you can keep this partition and not have to reload your data, although i always recommend backups). Make sure you are using the ALT CD not the Live CD. from there it should be rather simple. Also, make sure your HDD's that you plan on making an array with are of the same make and model. Different manufactures have different specs meaning your drives function differently and can corrupt your RAID array. To be honest this isn't a 64bit issue, it's an installation issue.

---

### Post by slope on 2008-07-03
Thx. So I will go with LILO then. Great. Now I know GRUB will not work so I can stop that battle. :)

> Also, make sure your HDD's that you plan on making an array with are of the same make and model. Different manufactures have different specs meaning your drives function differently and can corrupt your RAID array.

Not sure I agree with you on this one. This used to be the deal with raid years ago. Nowadays it seems that there is consensus to choose different producers of disks for raids. Stay within the same size if possible but that is solely to avoid waisting diskspace. The thought is that erray out of similar disks can actually fail totally if there is an ie production error withing say one particular disk. If you then have a 10 disk array not even raid 5 or 6 will help you. When enough disks die dataloss is a fact. 

If there is another school of thought in Linux world do not know.

---

### Post by slope on 2008-07-07
I did a partial solving of this matter. 
When I struggled for so long setting up and boot ing from raid 0 I decided to run /boot + /root from disc on no-raid.

Cause i am to use vmware and guests I will need speed for /home as well as /tmp /swap. 
I ended up running 2 disks in raid 0 and put my /home directory there.
On a forth drive I put /swap in the beginning and /temp on the end. Thought being that most of the writing/reading from/to disk will actually accour from the vmware folder in /home. Raid 0 was the choice for home.

Having /tmp/swap rather on a singel drive then in a raid 0 along with home should in theory give me weaker performance but I have been advised to do it this way so for now at least I have.

---

