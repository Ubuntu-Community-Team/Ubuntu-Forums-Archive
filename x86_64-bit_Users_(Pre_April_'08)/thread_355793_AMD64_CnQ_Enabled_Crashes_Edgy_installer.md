---
title: "AMD64 CnQ Enabled Crashes Edgy installer"
date: 2007-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by dogson on 2007-02-07
Im using an AMD64 3200+ on a MSI neo4-f nforce4 motherboard. I have Cool n Quiet enabled in bios to save power. When i tried installing the Edgy 64bit Desktop the installer just crashed before even booting into X. I think it has something to do with the Cool n Quiet and the kernel. because if i disable CnQ in bios it installs fine. Anyone have edgy running with CnQ enabled and the generic kernel?

---

### Post by Xion on 2007-02-08
What version were you installing? 64bit or 32? I have a AMD64 3200+ and am having difficulty installing Edgy as well. I've tried the 64bit version and 32.. both hang on the black ubuntu loading screen, with the little bar going left and right. I'll try disabling CnQ..

Oh, and Dapper works fine on here. (It's what I'm using now.) I thought a clean install would work, since the upgrade didn't. But we'll see.

---

### Post by John.Michael.Kane on 2007-02-08
This is just a guess,and something that has worked for me YMMV. 

Keep CnQ disabled till you finish installing edgy. once it is installed run the update manager this will grab all your updates a kernel being one of them.

 After the machine is rebooted log back in allowing the updates to take affect. 

Next reboot,and enter the bios turn CnQ back on. you should now be able to shut down or restart without issue.

Side note: Theres currently a kernel issue right now so you may have to wait to try this. [http://www.ubuntuforums.org/announcement.php?f=73](http://www.ubuntuforums.org/announcement.php?f=73)

---

### Post by dogson on 2007-02-08
> **Xion said:**
> What version were you installing? 64bit or 32? I have a AMD64 3200+ and am having difficulty installing Edgy as well. I've tried the 64bit version and 32.. both hang on the black ubuntu loading screen, with the little bar going left and right. I'll try disabling CnQ..

Oh, and Dapper works fine on here. (It's what I'm using now.) I thought a clean install would work, since the upgrade didn't. But we'll see.

It was the 64bit version of Edgy, Dapper worked fine for me to. Ill try to enable CnQ now that ill installed Edgy if it dosnt work or crashes i just compile a 2.6.19 vanilla kernel from kernel.org

---

### Post by midde on 2007-02-11
Have you tried the AMD Linux drivers for CnQ? Link: 
[http://www.amd.com/us-en/Processors/TechnicalResources/0,,30_182_871_13118,00.html](http://www.amd.com/us-en/Processors/TechnicalResources/0,,30_182_871_13118,00.html)

---

### Post by dogson on 2007-03-20
> **midde said:**
> Have you tried the AMD Linux drivers for CnQ? Link: 
[http://www.amd.com/us-en/Processors/TechnicalResources/0,,30_182_871_13118,00.html](http://www.amd.com/us-en/Processors/TechnicalResources/0,,30_182_871_13118,00.html)


No drivers are needed, the kernel should support it "out of the box"
it is the Ubuntu 64bit kernel that contain some kind of bug.

---

