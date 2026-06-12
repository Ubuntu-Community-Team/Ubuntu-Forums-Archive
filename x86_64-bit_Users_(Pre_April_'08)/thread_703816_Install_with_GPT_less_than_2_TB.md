---
title: "Install with GPT less than 2 TB"
date: 2008-02-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by sportster3 on 2008-02-21
I have 2 identical servers (except for the number of drives).  One with a RAID array of 4TB and the other with an array of 1.2TB.  

For the server with 4TB I used gparted LiveCD to setup the array with a GPT label with the partitions I wanted ( /, swap, and a big data partition).  I then installed the 64bit version of 7.10 server and everything is working fine.

On the server with 1.2TB I tried the same thing and I end up with an MBR (msdos label) on the drive after the install is finished.  Am I missing something?  Does the installer automatically determine the disk label by how big it is?  I want the 1.2TB disk to be GPT so that 1-2 years from now I can easily expand it past 2TB.

---

### Post by Yfrwlf on 2008-03-06
> **sportster3 said:**
> I have 2 identical servers (except for the number of drives).  One with a RAID array of 4TB and the other with an array of 1.2TB.  

For the server with 4TB I used gparted LiveCD to setup the array with a GPT label with the partitions I wanted ( /, swap, and a big data partition).  I then installed the 64bit version of 7.10 server and everything is working fine.

On the server with 1.2TB I tried the same thing and I end up with an MBR (msdos label) on the drive after the install is finished.  Am I missing something?  Does the installer automatically determine the disk label by how big it is?  I want the 1.2TB disk to be GPT so that 1-2 years from now I can easily expand it past 2TB.

Did you reboot your 4TB server and check to make sure the files were OK?  I was getting corrupt files after using GPT and heard GPT wasn't supported in the Ubuntu server kernels.

---

### Post by sportster3 on 2008-03-06
I rebooted the server a couple times when I was expanding the array.  I'll try again when the server is not busy and let you know.

---

### Post by Yfrwlf on 2008-03-06
> **sportster3 said:**
> I rebooted the server a couple times when I was expanding the array.  I'll try again when the server is not busy and let you know.

If you've rebooted once before after putting some files on there, and they were fine after the reboot, I imagine they still are.

About your problem, I'm afraid I can't really suggest much other than to make sure you installed things the same way, especially created the partitions and selected them manually to be installed to.  If they are the same servers then there should be no difference.  Since the only difference was the size of the array, if this keeps happening with the <2TB array having problems, while the >2TB array does not (you could even add drives to the failing one to see if it starts failing after it goes above 2TB), maybe there IS some bug and in that case why don't you use an MSDOS label type for the <2TB since it supports it, and see what happens.

---

### Post by sportster3 on 2008-03-10
I rebooted the 4TB server and didn't come back up.  I stuck the install CD in, went into recovery mode, reinstalled grub, and it came back up fine.  I had to do that once before when I changed some BIOS settings.  I'll reboot it again later to see if I have to do it every time.

---

### Post by Yfrwlf on 2008-03-11
> **sportster3 said:**
> I rebooted the 4TB server and didn't come back up.  I stuck the install CD in, went into recovery mode, reinstalled grub, and it came back up fine.  I had to do that once before when I changed some BIOS settings.  I'll reboot it again later to see if I have to do it every time.

To my knowledge the only BIOS settings I can think of that would make a difference is changing the boot order.  Obviously if you change the boot order it won't be able to find grub anymore.

---

### Post by sportster3 on 2008-04-04
I rebooted the 4TB server again today without any problems at all.  The <2 TB I'm just going to install on a small disk and put the data on the array.  That way I can have the boot be MBR and the data be GPT

---

