---
title: "How to recover from fsck on disk Gusty"
date: 2008-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by ziacles on 2008-04-08
I am in trouble. My Ubuntu Gusty Gibbon HP DV2000 laptop was acting a little funny, and I (dumbly) decided to run fsck (no parms). When fsck said "Warning this is a bad plan! Are you sure? Y/N" I entered Y (dumb yes,) Now the system won;t boot grub error 17 and if I run the liveCD and it logs to syslog "FATAL Module lvm_mod not found." 

File Descriptor 3 left open 
File Descriptor 4 left open  
File Descriptor 5 left open  
File Descriptor 6 left open  
No matching physical volumes found
File Descriptor 3 left open 
File Descriptor 4 left open  
File Descriptor 5 left open  
File Descriptor 6 left open  
No volume groups found

How can I recover from this dumb mistake?

---

### Post by dcstar on 2008-04-09
> **ziacles said:**
> I am in trouble. My Ubuntu Gusty Gibbon HP DV2000 laptop was acting a little funny, and I (dumbly) decided to run fsck (no parms). When fsck said "Warning this is a bad plan! Are you sure? Y/N" I entered Y (dumb yes,) Now the system won;t boot grub error 17 and if I run the liveCD and it logs to syslog "FATAL Module lvm_mod not found." 

File Descriptor 3 left open 
File Descriptor 4 left open  
File Descriptor 5 left open  
File Descriptor 6 left open  
No matching physical volumes found
File Descriptor 3 left open 
File Descriptor 4 left open  
File Descriptor 5 left open  
File Descriptor 6 left open  
No volume groups found

How can I recover from this dumb mistake?

Firstly, run fsck on the partition with the Live CD, then do a forum search for restoring Grub and follow the instructions.

You **might** get back on the air, but you might not.

If you end up losing everything, on your next install create a separate /home partition so at least that data will not be affected by a similar incident.

---

