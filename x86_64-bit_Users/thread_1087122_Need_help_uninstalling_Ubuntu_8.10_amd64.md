---
title: "Need help uninstalling Ubuntu 8.10 amd64"
date: 2009-03-04
forum: x86 64-bit Users
---

### Post by acer8930 on 2009-03-04
Hello,
I installed Ubuntu 8.10 amd64 on my Acer Aspire 8930 x64 laptop. I found the experience lacking from the 32bit version. So I wanted to uninstall. My HDD is partitioned in half, C:\ and D:\. I installed Ubuntu to D:\ because their is a lack of space on my C:\. 

When I click the Uninstall-Ubuntu.exe, nothing happens. Not even a process opens up in Task Manager.

Does anyone have a remedy for this or an alternate way to uninstall Ubuntu?

Thanks.

---

### Post by philinux on 2009-03-04
I assume you used wubi to install by the sound of it. In that case goto add/remove programmes or whatever it's called now from the control panel and uninstall from there.

---

### Post by acer8930 on 2009-03-04
Yes I did use Wubi. Same thing happens from the control panel. Nothing. No errors or anything. When I tried running it in Safe Mode, the process showed up for less then a second, then disappeard. :(

---

### Post by 3Miro on 2009-03-04
You are installing Ubuntu, sorry to hear that.

You can just go to the drive mager of whatever other OS you are using and simply repartition your HD to remove the Ubuntu partition. The only problem you might have (and please be careful), if Windows is the only other partition that you have, you will probably be unable to boot afterwards. 

If you have another Ubuntu, you might have to edit the grub menu file, but other than that it should be fine.

In the case of Windows, I am not sure how to fix the problem. There must be some way to "fix" the windows boot-loader to take over in stead of Grub, I don't know how.

---

### Post by acer8930 on 2009-03-04
Well, this was using the "Install in Windows" option, so my D:/ (the second partition most laptops come with now, it is NTFS), there is just D:/ubuntu.

So I installed it within Windows, and am supposed to be able to uninstall within Windows too. But the uninstaller does not run. it works on me Desktop computer, which is 32bit, and that may be the problem. I could just delete the folder but I'm not sure what repercussions that might have (registry files) and I would have to figure out the whole boot loader thing. As far as I know it is not using the GRUB Loader, as it looks like the standard "Choose your OS" screen.

I'm having the same problem as here:
[http://ubuntuforums.org/showthread.php?t=864676](http://ubuntuforums.org/showthread.php?t=864676)

But I'm running Vista Home Premium x64 and I tried updating the Wubi uninstaller like I've read, but the same problem occurs.

---

### Post by 3Miro on 2009-03-04
Hm, I have never seen anything. Someone more knowledgeable might be able to help.

Registry could be fixed either manually (which is pain) or using some registry purge software. If you get a Choose OS option on the bootloader, then you might be using Grub. The again Windows supports dual boot (but I have only seen it as a choice between 2 versions of windows).

Sorry, this is out of my expertise and I don't want to tell you something that can potentially damage your system (i.e. erase an important file or mess up the registry or bootloader).

---

### Post by marcelkoopman on 2009-03-05
C:\ and D:\ are drive letters, not partitions.
A partition has a location like /dev/hda2 or /dev/sda1.

---

### Post by acer8930 on 2009-03-05
> **marcelkoopman said:**
> C:\ and D:\ are drive letters, not partitions.
A partition has a location like /dev/hda2 or /dev/sda1.

I'm guessing that that was directed at me but I know. I'm running Windows Vista, and I installed Ubuntu WITHIN Windows with the Wubi installer. 
I don't know if you're familiar with that. I does not partition my HDD. It came prepartitioned like most laptops do now. C:/ for Windows and Program Files, and D:/ just for storing data.

I believe I fixed it. I edited the Windows BCD and removed the Ubuntu option, then I moved the D:/ubuntu folder somewhere else and tried it. Then I ran a registry cleaner. So far it worked. No errors or anything and Ubuntu is not a boot option. 

I was looking forward to learning some Linux, but I guess I'll have to wait till College.

---

