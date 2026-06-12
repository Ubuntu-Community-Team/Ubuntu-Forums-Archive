---
title: "vmware-player, How to increase vm disk size? ubuntu host XP guest OS"
date: 2007-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by manjo on 2007-03-02
Hi,

I installed vmware-player and XP pro guest OS, when I created the virtual disk I gave it only 6G, but that is quickly filling up, how can I increase the size of my virtual disk from 6G to say 15G ? 

I am on AMD64 feisty herd4 system. 

Thanks a ton. 
manjo

---

### Post by manjo on 2007-03-02
Here is what I did:

I created a virtual disk of 15GB:

qemu-img create -f vmdk disk2.vmdk 15G Formating 'disk2.vmdk', fmt=vmdk, size=15728640 kB


Edited the xp.vmx file as follows:

ide0:0.present = "TRUE"
ide0:0.filename = "WindowsXPPro.vmdk"
ide0:1.present = "TRUE"
ide0:1.fileName = "disk2.vmdk"
ide0:1.writeThrough = "TRUE"

as far as I understand ide has (0:0, 0:1, 1:0 1:1), 0:0 is my primary disk, 1:0 is my cdrom drive so I created 0:1 as my 2nd HDD. Now uninstalled all the programs from primary disk and installed them on 2nd disk. For this I had to go to XP, disk manager utility, and format the new drive (15GB) as NTFS (I had created my primary as FAT, but FAT & NTFS seems to live happily). I could probably add another disk at another time of another XGB to store my data files etc... but that is for later. Now my space problem is solved. 

Primary: 6GB (FAT)
Secondary: 15GB (NTFS)

Looks like everything is happy now, I have not rebooted my XP yet... just keeping fingers crossed hopefully nothing breaks.

---

