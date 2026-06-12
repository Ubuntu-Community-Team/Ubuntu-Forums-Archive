---
title: "wengo amd64 problem."
date: 2006-06-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by CyberAngel on 2006-06-12
Please take a look on [that thread]("http://www.ubuntuforums.org/showthread.php?t=190413").

Has anyone else using dapper 64bit faced this issue with wengophone or we are only two??? 8-[ 

Has anyone to propose a workaround or something?

Thanks.

---

### Post by Kilz on 2006-06-12
[QUOTE=CyberAngel]Please take a look on [that thread]("http://www.ubuntuforums.org/showthread.php?t=190413").

Has anyone else using dapper 64bit faced this issue with wengophone or we are only two??? 8-[ 

Has anyone to propose a workaround or something?

Thanks.[/QUOTE]
Are you using the classic or the beta? I did get the beta to open up on my desktop, but I had to manualy add 2 lib files. I have an account, but no one on it as I just signed up, so I cant test it 100%.
[ Download the .deb file.]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fe%2Fe2fsprogs%2Flibuuid1_1.38-2ubuntu2_i386.deb&md5sum=d3cc48790db605a4eebbbf5e44769521&arch=i386&type=main") 
Make sure you have dpkg-dev installed with synaptic. 
Extract the .deb with the archive manager, inside the extract the data archive to your Desktop. 
Open a terminal 
```
sudo cp ~/Desktop/lib/* to /lib32
```
Start the beta wit the wengophone.sh and it will set itself up.

---

### Post by henriquemaia on 2006-06-12
[quote=Kilz]Are you using the classic or the beta? I did get the beta to open up on my desktop, but I had to manualy add 2 lib files. I have an account, but no one on it as I just signed up, so I cant test it 100%.
[ Download the .deb file.]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fe%2Fe2fsprogs%2Flibuuid1_1.38-2ubuntu2_i386.deb&md5sum=d3cc48790db605a4eebbbf5e44769521&arch=i386&type=main") 
Make sure you have dpkg-dev installed with synaptic. 
Extract the .deb with the archive manager, inside the extract the data archive to your Desktop. 
Open a terminal 
```
sudo cp ~/Desktop/lib/* to /lib32
``` Start the beta wit the wengophone.sh and it will set itself up.[/quote]

Thanks for this advice. I have tried it and now at least wengo does not crash, but I don't have sound (incoming or outgoing).

---

### Post by CyberAngel on 2006-06-12
Just after I posted this thread I tried to make the [beta]("http://download.wengo.com/wengophone/beta/WengoPhone-2.0-beta2-linux-bin-x86.tar.bz2") work (by extracting a few 32bit libs into /usr/lib32) and yes, it works. But it is 32bit. What about the 64bit version.
It was asking about libasound.so.2 and one or two more (I don`t remember exactly) Not the libuuid you mentioned above.

After that I moved wengophone folder to /opt/wengophone and made an executable script to load it.

```
#!/bin/bash

export LD_LIBRARY_PATH=/opt/wengophone
/opt/wengophone/qtwengophone
```

---

### Post by Kilz on 2006-06-12
[QUOTE=CyberAngel]Just after I posted this thread I tried to make the [beta]("http://download.wengo.com/wengophone/beta/WengoPhone-2.0-beta2-linux-bin-x86.tar.bz2") work (by extracting a few 32bit libs into /usr/lib32) and yes, it works. But it is 32bit. What about the 64bit version.
It was asking about libasound.so.2 and one or two more (I don`t remember exactly) Not the libuuid you mentioned above.

After that I moved wengophone folder to /opt/wengophone and made an executable script to load it.

```
#!/bin/bash

export LD_LIBRARY_PATH=/opt/wengophone
/opt/wengophone/qtwengophone
```[/QUOTE]

You may have already added it somehow. Is there a 64 bit version? I couldnt find it when I looked.

---

### Post by CyberAngel on 2006-06-12
[QUOTE=Kilz]You may have already added it somehow. Is there a 64 bit version? I couldnt find it when I looked.[/QUOTE]

It is on the repos (not the last version though) but that is why I started this post. I get a segmentation fault if I apt-get the 64bit version from the repositories.

Has anyone else tried this package??

```
sudo apt-get install wengophone
```

---

### Post by usenix on 2006-06-14
Tried the 64-bit package via apt-get too.

Same crash here.

best wishes usenix

---

### Post by CyberAngel on 2006-06-14
[QUOTE=usenix]Tried the 64-bit package via apt-get too.

Same crash here.

best wishes usenix[/QUOTE]

So I think that wengophone amd64 might be a corrupted package...

---

### Post by Kilz on 2006-06-14
[QUOTE=CyberAngel]So I think that wengophone amd64 might be a corrupted package...[/QUOTE]
I looked at a few sites for a 64 bit .deb and couldn't find it. I looked at the main site and couldn't find a source tarball to compile one from.
I downloaded the package to take a look at it. It says version .99, that's the classic version. Only the Linux classic version is only up to .958. You may want to keep using the new beta over the classic model, it will have more features the web site says. The Beta starts at version 2.0 so we can be sure that the package in the repositories is the classic.

---

### Post by guyjohnston on 2006-11-08
Hi, I've had exactly the same problem trying the amd64 package from the repositories on Dapper and Edgy. Wengo crashes when I try to sign in, or sometimes straight away. Also it's the classic version, when version 2.0 has been properly released now. I've tried installing the package from the Wengo site for the classic and next generation versions, but both have an error saying they're not compatible with the amd64 kernel.

---

