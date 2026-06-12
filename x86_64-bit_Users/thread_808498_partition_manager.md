---
title: "partition manager"
date: 2008-05-26
forum: x86 64-bit Users
---

### Post by gordon3056 on 2008-05-26
How do I get partition manager working its not in my menu but I think its on the system

---

### Post by philinux on 2008-05-26
It's in the System>Admin menu but you have to enable it in prefs>main menu.

---

### Post by gordon3056 on 2008-05-26
Thank you

---

### Post by adi_8079 on 2008-06-02
If it's not there, try:
```
sudo apt-get install gparted
```

---

### Post by aboud on 2008-06-15
ah thanks, now i have it working.. but it dosen't do so much.. it just show information about partitions even thou i try 
sudo gparted 

any idea?

---

### Post by kevmitch on 2008-06-15
You generally need to have a partition unmounted to do anything to it. If you want to do anything terribly radical to your system partitions you'll probabaly need to use a boot CD so the OS that's doing the partition rearranging isn't on the partitions you're trying to rearrange. 

If on the other hand, you're just resizing your /home partition or something, you can probably get by by doing the following (Ubuntu makes this rather tricky since you can't just login as root):

1. Create a user who's home directory isn't in /home:
```

adduser admin --home /admin

```
2. Log out all users
3. Log in as admin
4. Unmount /home
```

umount /home

```
5. Now run gparted.

---

### Post by Sef on 2008-06-16
> If on the other hand, you're just resizing your /home partition or something, you can probably get by by doing the following (Ubuntu makes this rather tricky since you can't just login as root):


**Back up** your data before attempting any reparitioning.  It will reformat (write over) the partition.

---

### Post by tubbygweilo on 2008-06-16
Gparted when used from the System > Administration > Partition Editor will as stated only work on unmounted partitions but if you download, burn and boot with a [Gparted Live CD]("http://sourceforge.net/project/showfiles.php?group_id=115843") you can then amend your system which will now be unmounted. As suggested by other please backup data and read the [instructions]("http://gparted.sourceforge.net/faq.php"), look through the [screen shots]("http://gparted.sourceforge.net/screenshots.php") and have a bit of a think prior to doing the deed.

---

