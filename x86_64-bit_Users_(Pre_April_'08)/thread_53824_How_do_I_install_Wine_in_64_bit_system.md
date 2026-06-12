---
title: "How do I install Wine in 64 bit system?"
date: 2005-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Navyblue on 2005-08-02
I get this when doing apt-get:

```

navyblue@PC:~$ sudo apt-get install wine
Password:
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

```

I have enabled the universe and multiverse repositories.

I can't install through Synaptic too.

Thanks in advance. :)

---

### Post by marwans on 2005-08-02
[QUOTE=Navyblue]I get this when doing apt-get:

```

navyblue@PC:~$ sudo apt-get install wine
Password:
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

```

I have enabled the universe and multiverse repositories.

I can't install through Synaptic too.

Thanks in advance. :)[/QUOTE]
 [http://www.ubuntuforums.org/showthread.php?t=48905&highlight=wine](http://www.ubuntuforums.org/showthread.php?t=48905&highlight=wine)

you can't install wine in ubuntu for amd64 yet. in fact, not only wine, a lot more packages are not available yet. since this version of ubuntu is not yet fully supported, you can try using ubuntu i386 version

ciao,
marwan

---

### Post by Navyblue on 2005-08-02
Thanks for the info.

So there is no way even to run it in 32 bit mode under 64 bit Ubuntu?

---

### Post by Lord Illidan on 2005-08-02
Try downloading wine as sourcecode and compile it on your system.

[Here are the links to the code](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449)

---

### Post by DRF on 2005-08-02
I've yet to hear of WINE working properly when compiled from source on a 64bit version of Ubuntu. The most common way to get 32bit programs to work is with a chroot. (but as I don't use it I can't say how easy or effective it is).

Here us a link to a thread in this forum on setting up chroot enviroments. (Basicly it's like installing a 32bit operating system inside a 64bit operating system)
[http://www.ubuntuforums.org/showthread.php?t=24575](http://www.ubuntuforums.org/showthread.php?t=24575)

Daniel

---

### Post by Navyblue on 2005-08-02
[QUOTE=DRF]I've yet to hear of WINE working properly when compiled from source on a 64bit version of Ubuntu. The most common way to get 32bit programs to work is with a chroot. (but as I don't use it I can't say how easy or effective it is).

Here us a link to a thread in this forum on setting up chroot enviroments. (Basicly it's like installing a 32bit operating system inside a 64bit operating system)
[http://www.ubuntuforums.org/showthread.php?t=24575](http://www.ubuntuforums.org/showthread.php?t=24575)

Daniel[/QUOTE]

Hi Daniel,

After setting up the Synaptic to work in 32 bit mode, can I still run it in 64 bit mode?

Thanks for the info btw. :)

---

### Post by DRF on 2005-08-03
I'm fairly sure that you still run programs in 64bit by default, just using the 32bit chroot install for those programs that won't work in 64bit. I think that the 32bit programs will be installed in the /chroot/ directory (unless you choose to name it something other than /chroot) then using a command (I think dchroot) you can switch back and forth between 32bit and 64bit.

I don't use chroot personally so you would probably be better looking for some more specific details in a chroot thread in the forum. (as I might well anwser more technical questions on chroot wrong)

Daniel

---

### Post by Navyblue on 2005-08-03
[QUOTE=DRF]I'm fairly sure that you still run programs in 64bit by default, just using the 32bit chroot install for those programs that won't work in 64bit. I think that the 32bit programs will be installed in the /chroot/ directory (unless you choose to name it something other than /chroot) then using a command (I think dchroot) you can switch back and forth between 32bit and 64bit.

I don't use chroot personally so you would probably be better looking for some more specific details in a chroot thread in the forum. (as I might well anwser more technical questions on chroot wrong)

Daniel[/QUOTE]
 Thanks. I will look into that.

---

### Post by tseliot on 2005-08-03
[QUOTE=Navyblue]Hi Daniel,

After setting up the Synaptic to work in 32 bit mode, can I still run it in 64 bit mode?

Thanks for the info btw. :)[/QUOTE]
If you follow the HOWTO you will install another synaptic, it won't touch yours.
At the end of the process you will have synaptic (64bit) and synaptic32. It's not that hard. Check it out

---

### Post by Navyblue on 2005-08-03
[QUOTE=tseliot]If you follow the HOWTO you will install another synaptic, it won't touch yours.
At the end of the process you will have synaptic (64bit) and synaptic32. It's not that hard. Check it out[/QUOTE]

Ok... Thanks. :

---

