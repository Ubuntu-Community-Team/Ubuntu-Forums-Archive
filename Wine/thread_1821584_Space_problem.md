---
title: "Space problem"
date: 2011-08-09
forum: Wine
---

### Post by spyshower on 2011-08-09
Hello guys,

I am trying to install an application that has a size of about 1.8 GB.
In the installation path I specify a disk (which I found out they are the folders in wine/dosdevices/) but it says I don't have enough space. 

After quite sometime I changed the name of dosdevices to dosdevices1 and made a new dosdevices symlink so that it directs to a hard disk with plenty of free space (it has the installation of my Windows 7 by the way). When I tried to install the application again, it says that "123 MB required / 67.2 GB available". However, when I click install I get an out of space error:

"C:/ - Disk size: 200 GB - Disk space %s required / %s avaiable: 67.2 GB - Required: 123 MB - Remaining: 0 bytes"

I would really appreciate some help here.


PS: I don't know why it says 123 mb since the app is big.
PS2: I guess that the error occures because it calculates my root or home directory when I press install; the problem is I don't know if I do (or where to check it).

---

