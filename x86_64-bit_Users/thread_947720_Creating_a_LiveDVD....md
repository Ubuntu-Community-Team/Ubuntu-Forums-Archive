---
title: "Creating a LiveDVD..."
date: 2008-10-14
forum: x86 64-bit Users
---

### Post by Cariboo1938 on 2008-10-14
Hello all Ubuntu amd64 fans...

In May I installed Ubuntu 8.04-amd64 and until now I downloaded all the updates (lots, I stopped counting}.
Now I want to give this System to a friend and I learned that there is the program 'Remaqstersys' to create an *.iso image which I could burn to DVD.
I installed the package and tried the 'Dist' option (backup without personal data /home) but I got no iso-image created.
Instead I got the message that the squashfs is to big (>4GB)
I checked with --->System --->Administration --->System Monitor and found that the system (without /home) only uses 2.9GB.

Can anybody tell me what to do, please!

---

### Post by philinux on 2008-10-14
Make sure you delete all trash including root /

---

### Post by Cariboo1938 on 2008-10-15
Yes, finally I got it...

The mistake was that I assumed, when creating the 'Dist' option (backup without personal data /home) , the /home directory will be excluded automatically. This is not the case.

I had to go to: 
---Applications --->Accessories --->Disk Usage Analyzer and open 
---'Edit' -->Preferences and 
---un-check /home/owner directory.

Then my 'Total file system usage' was just 4 GB.

Checking --->System --->Administration --->System Monitor 
gives not the correct file system usage!

I got the Dist.iso file and md5sum file created and I burned the DVD and now I'm writing this from the custom 'Ubuntu8.04-amd64-LiveDVD'

Thanks to all those wonderful people doing excellent work! =D>

---

