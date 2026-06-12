---
title: "Outlook 2010 crashes on incoming email"
date: 2012-12-06
forum: Wine
---

### Post by webandart on 2012-12-06
Hello,

I have succesfully installed office 2010 on my 32bit 12.10 ubuntu. I am using Wine 1.5.16 with PlayOnLinux 4.1.1.

Everything seems fine except from the fact that Outlook, after it connects to to mail server and downloads incoming email, it crashes! I can send ok though.  

The error log is attached. Any ideas?

Thanks.

---

### Post by dmccort on 2013-01-06
I'm getting pretty much the exact same message. 
Only difference is my version of Playonlinux (4.1.8).
WINE version is the same as yours and using Outlook 2010.
As soon as it does a "Send/Receive" it crashes the same as yours.
The only thing I can think of is the PST file. 
Maybe it's having trouble accessing it. 
Mine is on a windows 7 partition and is the same data file I use when I'm using Windows. Was hoping to share the one datafile. 
Maybe WINE doesn't like accessing that partition due to access rights or something? 
I noticed when installing games through Playonlinux/WINE I had to copy the setup files to my local Linux partition before it would work...gave me errors during installation until I did.
I'd rather not have a separate PST file, otherwise it defeats the purpose of having Outlook on Linux in the first place.
Thoughts anyone?

---

### Post by puebloan on 2013-01-07
Same problem. But I haven't searched for a solution because I don't think Outlook has ever worked on wine.

---

### Post by ahmedvolks on 2013-03-14
> **puebloan said:**
> Same problem. But I haven't searched for a solution because I don't think Outlook has ever worked on wine.

I think that outlook PST file is not ready for write on it. Because the problem happen when it start download the msgs.

---

### Post by Mark Phelps on 2013-03-16
Outlook doesn't work well in Wine -- see the details on the linked page:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=25161]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=25161")

---

