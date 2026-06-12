---
title: "Copied from CD..."
date: 2008-05-18
forum: x86 64-bit Users
---

### Post by DachaArh on 2008-05-18
I have 8.04 installed via easy install and I wanted to ask this.
Why I have this problem?
When I copy something from DVD in my home folder thst copied folder is locked for editing.
Is there any way to copy from cd to avoid this ?

thanks 

I tried to copy with nautilus with sudo, and then I can edit these Folders and delete them but folder still has locked icon ...

---

### Post by garyedwardjohnston on 2008-05-18
Right click folder

Properties > Permissions

---

### Post by Kilz on 2008-05-18
> **DachaArh said:**
> I have 8.04 installed via easy install and I wanted to ask this.
Why I have this problem?
When I copy something from DVD in my home folder thst copied folder is locked for editing.
Is there any way to copy from cd to avoid this ?

thanks 

I tried to copy with nautilus with sudo, and then I can edit these Folders and delete them but folder still has locked icon ...

The reason it is locked, is that files on a cd/dvd are read only. When you copy them you also copy their permissions, which is read only.

---

### Post by DachaArh on 2008-05-18
thanks alot mates ;)

I just realized that I copied alot of folders from one DVD, and they have alot of sub-folders and sub-sub folders, And when I try to edit permissions for main folder, it does not aply to sub folders and files.
Is there any way to edit permissions for all at once?

---

### Post by xinix on 2008-05-19
If you use the -R option with chown, chmod it should include all subfolders

---

### Post by pixel :-) on 2008-05-21
I don't remember for gnome.But in kde theres a "apply changes to all subfolders and their contents" option ,just at the botom of the the permission tab in the properties window.The command line works too of coarse :)

---

### Post by wdaniels on 2008-05-21
> **pixel :-) said:**
> I don't remember for gnome.But in kde theres a "apply changes to all subfolders and their contents" option ,just at the botom of the the permission tab in the properties window.

There is the same in Gnome with "Apply Permissions to Enclosed Files" button.

---

