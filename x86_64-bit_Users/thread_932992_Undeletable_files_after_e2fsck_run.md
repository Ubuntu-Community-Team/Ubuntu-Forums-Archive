---
title: "Undeletable files after e2fsck run"
date: 2008-09-29
forum: x86 64-bit Users
---

### Post by rbock on 2008-09-29
Hi,

on one of my servers there was an incompatibility between the raid controller and the disks. This lead to some damage in the file system. After a firmware update, the incompatibility is supposed to be resolved. 

Problems remain, though:
After running e2fsck -y cleaned up some multiply claimed blocks, I have a bunch of weird files, which even root cannot delete:

# ls -l
total 48
-rwsr-S--t 1 50414826 3732079024 49152 2007-09-15 08:52 00000000_0000_AXY_ALC_002.txt

# rm 00000000_0000_AXY_ALC_002.txt
rm: cannot remove `00000000_0000_AXY_ALC_002.txt': Operation not permitted

# chown root:root 00000000_0000_AXY_ALC_002.txt
chown: changing ownership of `00000000_0000_AXY_ALC_002.txt': Operation not permitted

# chmod a+w 00000000_0000_AXY_ALC_002.txt
chmod: changing permissions of `00000000_0000_AXY_ALC_002.txt': Operation not permitted

:confused:

Any ideas how I could get rid of such files? There are quite a few of them.

Formatting the disk and copying everything back from the mirror would be a last resort, but this takes about a day of downtime for the machine (5TB of data in many millions of files).


Thanks and regards,

Roland

---

