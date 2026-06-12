---
title: "Mounting a second disk in SuSe"
date: 2007-06-06
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Boris-- on 2007-06-06
Is it possible to mount my Ubuntu drive in SuSe? I'm a newbie and am trying out a few distros. And another thing, is it possible to transfer my firefox settings between the two distros? Thanks in advance.

---

### Post by Nekiruhs on 2007-06-06
sure it is 
```
mount ext3 /dev/??? /media/???
```Where ??? is the partition designation for Ubuntu (Usually, hda?, sda? ? is a number).
You could also symbolic link the two firefox profile:
```
rm -r ~/.mozilla
ln -s /media/WhereYouMountedItAbove /home/YourUserNameOnUbuntu/.mozilla
```
From in SuSe. (assuming you want to use your Ubuntu settings in SuSe)

---

