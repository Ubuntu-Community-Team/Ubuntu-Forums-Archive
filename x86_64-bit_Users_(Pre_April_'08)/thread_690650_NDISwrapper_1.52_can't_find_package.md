---
title: "NDISwrapper 1.52 can't find package"
date: 2008-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by breimer273 on 2008-02-07
OK So I followed these directions:
[https://help.ubuntu.com/community/WifiDocs/NdiswrapperOnAMD64](https://help.ubuntu.com/community/WifiDocs/NdiswrapperOnAMD64)

But when I run the:
```
sudo apt-get install build-essential dh-make gcc-3.4 fakeroot linux-headers-'uname -r'
```

I get this:
```
bill@Calvin:~$ sudo apt-get install build-essential dh-make gcc-3.4 fakeroot linux-headers-'uname -r'
[sudo] password for bill:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package dh-make
bill@Calvin:~$ 

```

I get this same error when installing cabextract. I do not have internet access in ubuntu, thus the reason for installing ndiswrapper. So do I have to download the packages from somewhere or what?

---

### Post by Ort on 2008-02-08
Thank you for asking, having the same issue myself.

---

### Post by Jouke74 on 2008-02-08
I think that is a bug in the package list of Ubuntu. Or, you did not enable the repositories (unlikely). However, the package is on-line in the Ubuntu Gutsy repositories. Download the "ALL" (means 32 and 64 bit) Debian file from here, by clicking on "all". It will then show a list of mirror sites. Choose a mirror and start the download. Install it, by clicking on the debian package in your download directory.

[http://packages.ubuntu.com/gutsy/devel/dh-make](http://packages.ubuntu.com/gutsy/devel/dh-make)

Then continue with the next steps (and give me a big thank you :-) ).

---

### Post by breimer273 on 2008-02-08
OK I will give you a big thank you if and when it works! Hopefully it does. And I don't know how to enable the repositories so that could be the problem. And do you know anything about the cabextract problem? But thanks for the help so far.

---

### Post by breimer273 on 2008-02-08
> **Jouke74 said:**
> I think that is a bug in the package list of Ubuntu. Or, you did not enable the repositories (unlikely). However, the package is on-line in the Ubuntu Gutsy repositories. Download the "ALL" (means 32 and 64 bit) Debian file from here, by clicking on "all". It will then show a list of mirror sites. Choose a mirror and start the download. Install it, by clicking on the debian package in your download directory.

[http://packages.ubuntu.com/gutsy/devel/dh-make](http://packages.ubuntu.com/gutsy/devel/dh-make)

Then continue with the next steps (and give me a big thank you :-) ).

OK well I thanked you too soon. I downloaded what you said double clicked on it to install it and it came up with a box then said something like not suitable dependencies debmake or something like that. How do I fix that?

---

### Post by Jouke74 on 2008-02-11
Ah I forgot (I assume you use Ubuntu Gutsy AMD64): 

You don't have internet and that's why things go wrong... ](*,)

1. Insert the Ubuntu install CDrom (!!!!)
2. Open a terminal.
3. Use the commands:

> sudo apt-get update

> sudo apt-get install build-essential dh-make gcc-3.4 fakeroot linux-headers-'uname -r' **cabextract**

Now it will probably install all and work.

If dependencies are not met, then it means that the program you are trying to install (dh-make) requires some other programs and/or libraries which are not present or have the wrong version numbers. With dh-make the problem is that debmake is not installed which is part of build-essential.

Another option is by the way to install Ndiswrapper through synaptic, instead of building Ndsiwrapper 1.52 from scratch yourself. Is the current Ndiswrapper from the repositories giving you problems? You can do this by installing Ndiswrapper with the command:

> sudo apt-get ndiswrapper-utils-1.9 ndiswrapper-common

But please use one version only, the build yourself or the one from the repositories!

"Cabextract" is also a program in the synaptic repsoritory. You need that to extract files from windows CAB archives. In this case the windows driver files of your wireless card.

---

### Post by breimer273 on 2008-02-11
OK Now you really do deserve the thanks. But I figured out that I needed to be connected to the internet. So I found another wireless card and see if it would work and it did so i got everything I needed installed now but thank you very much for the help.

---

