---
title: "Need to set permission for folders on Windows disc"
date: 2007-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by BightningLug on 2007-10-25
I have all my music files stored on my Windows harddrive. I used 'gksudo nautilus' to open a file manager and create links the the specific folders I need and moved the links to the home folder of my user account. This works fine until I log out or reboot, then I have to open that drive again and enter my password. The link remians in my home folder where I placed it, but it is disabled. Opening a file manager again and entering my password resolves the issue. If I don't do these things first all my music files get removed from Rhythmbox as it says they are not found. I've tried setting the owner and group properties on the folders in question but as soon as I select a different user or group it immediatly returns to "root" as the user/group.

So, my question is: How do I set the permission to specific folders on my Windows disc so that the links will work and I won't have to reimport all my music files each time I log in and startup Rhythmbox?

---

### Post by dcstar on 2007-10-27
> **BightningLug said:**
> I have all my music files stored on my Windows harddrive. I used 'gksudo nautilus' to open a file manager and create links the the specific folders I need and moved the links to the home folder of my user account. This works fine until I log out or reboot, then I have to open that drive again and enter my password. The link remians in my home folder where I placed it, but it is disabled. Opening a file manager again and entering my password resolves the issue. If I don't do these things first all my music files get removed from Rhythmbox as it says they are not found. I've tried setting the owner and group properties on the folders in question but as soon as I select a different user or group it immediatly returns to "root" as the user/group.

So, my question is: How do I set the permission to specific folders on my Windows disc so that the links will work and I won't have to reimport all my music files each time I log in and startup Rhythmbox?

You must ensure that your Windows disk is listed in your /etc/fstab file so it is mounted on start-up.

Install the **pydsm** package, and then you can use **System-Administration-Storage Device Manager** to set this up for you.

---

