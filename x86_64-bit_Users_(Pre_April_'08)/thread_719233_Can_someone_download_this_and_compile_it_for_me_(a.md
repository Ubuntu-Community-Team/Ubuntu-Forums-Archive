---
title: "Can someone download this and compile it for me (and state how you did it)?"
date: 2008-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by s3a on 2008-03-08
Can someone download this and compile it for me (and state how you did it)?

[http://linux.dell.com/files/ubuntu/modem-drivers/hsf/](http://linux.dell.com/files/ubuntu/modem-drivers/hsf/)

Please do this, otherwise I can't use my 64-bit OS!

*hsfmodem-7.60.00.18x86_64oem.tar.gz*

---

### Post by Kilz on 2008-03-08
> **s3a said:**
> Can someone download this and compile it for me (and state how you did it)?

[http://linux.dell.com/files/ubuntu/modem-drivers/hsf/](http://linux.dell.com/files/ubuntu/modem-drivers/hsf/)

Please do this, otherwise I can't use my 64-bit OS!

*hsfmodem-7.60.00.18x86_64oem.tar.gz*

install alien
```
sudo apt-get install alien
```

Download the 64bit rpm file
[http://linux.dell.com/files/ubuntu/modem-drivers/hsf/hsfmodem-7.60.00.18x86_64oem-1.x86_64.rpm](http://linux.dell.com/files/ubuntu/modem-drivers/hsf/hsfmodem-7.60.00.18x86_64oem-1.x86_64.rpm)

Open terminal navigate to the directory with the rpm file and enter
```
 sudo alien hsfmodem-7.60.00.18x86_64oem-1.x86_64.rpm
```

Double click on the deb file this creates to install.

---

### Post by whoop on 2008-03-08
I have not tried it myself because the lack of necessity ;-) But I found this link:
Looks like it does what you need:
[http://backports.ubuntuforums.com/showthread.php?t=617363](http://backports.ubuntuforums.com/showthread.php?t=617363)

---

### Post by s3a on 2008-03-09
> **Kilz said:**
> install alien
```
sudo apt-get install alien
```

Download the 64bit rpm file
[http://linux.dell.com/files/ubuntu/modem-drivers/hsf/hsfmodem-7.60.00.18x86_64oem-1.x86_64.rpm](http://linux.dell.com/files/ubuntu/modem-drivers/hsf/hsfmodem-7.60.00.18x86_64oem-1.x86_64.rpm)

Open terminal navigate to the directory with the rpm file and enter
```
 sudo alien hsfmodem-7.60.00.18x86_64oem-1.x86_64.rpm
```

Double click on the deb file this creates to install.

Can I do that process under a 32-bit environment because if not then it's impossible because I have no internet on my 64-bit environment and this is the driver for my winmodem.

---

### Post by Rhubarb on 2008-03-09
I've converted the rpm package into a deb file for you the same way Kilz has done it.
I'll host this file for half an hour or so.

Grab it here:
Edit:  Removed because of limited bandwidth on my behalf.

---

### Post by s3a on 2008-03-09
Microsoft is giving free 5 gb storage so im gona make an account or wtv is needed and then put things in there and give account stuff so others can benefit 2 ;) (free for me as well :D) Thx for that file!

---

### Post by s3a on 2008-03-12
That file actually didn't work and I'll just make an email in which I will attach and send files to myself and give the password openly on formes for people to get files (it won't actually be my real email).

---

### Post by rmtatum on 2008-03-12
There's lot of places to get free file storage.  Mashable has a huge list of storage site.
[URL="http://mashable.com/2007/07/28/online-storage/"]
ONLINE STORAGE: 80+ File Hosting and Sharing Sites[/URL]

Also launchpad allows you to post packages of free (libre) software.

[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

---

### Post by s3a on 2008-03-23
I like skydrive more since its part of my already existing email address that I also use for MSN messenger. And I'm still internet-less on 64-bit, so can someone please help me?

---

### Post by Martje_001 on 2008-03-23
```
wget http://linux.dell.com/files/ubuntu/modem-drivers/hsf/hsfmodem-7.60.00.18oem.tar.gz
tar -xzf hsfmodem-7.60.00.18oem.tar.gz
cd hsfmodem-7.60.00.18oem
sudo make install
sudo hsfconfig
```
It's all in the README :)

---

### Post by helliewm on 2008-03-23
For a newbie README files can sometimes be a foreign language:) Its only now I am confident with them. Sometimes you need a Ladybird Reading Book:) Simple cut and paste instructions.

Helen

---

