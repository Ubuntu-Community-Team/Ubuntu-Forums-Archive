---
title: "Oracle 10g R2 on 7.10 Gutsy"
date: 2008-03-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rico010 on 2008-03-21
Have someone successfully installed Oracle 10g R2 on Ubuntu 7.10 Gutsy Gibbon 64 bit ?

I'm trying to install it currently. I've tryed almost 5 or 6 manuals installed all libraries and 32 bit compatibility libraries which were mentioned in that manuals. But still got errors with linking approximately at 83 % of installation progress. :) i even have 4 gcc editions installed 3.3, 3.4, 4.1, 4.2. Still nothing.

If anyone have succefully did it.. i need some help.

Thanks.

---

### Post by jespdj on 2008-03-21
I have recently installed Oracle 10g XE (Express Edition) on a laptop with 64-bit Hardy alpha 6. It wan't too difficult. There was only one 32-bit library which I had to install: [libaio1](http://packages.ubuntu.com/hardy/libaio1). I downloaded the .deb for i386 and installed it with --force-architecture:
```
sudo dpkg -i --force-architecture libaio1_0.3.106-5ubuntu2_i386.deb
```
Then I installed the Oracle .deb the same way:
```
sudo dpkg -i --force-architecture oracle-xe-universal_10.2.0.1-1.0_i386.deb
```
And it works.

I don't know if it's exactly the same for Gutsy and a non-XE version of Oracle, but I hope this is useful to you.

---

### Post by Rico010 on 2008-03-21
Thank a lot for your reply. I appreciate that. But the problem is that XE is not suitable for me.
I need Enterprise Edition. If someone have successful experience with EE i could post the list of libraries that i've installed. May be i do something wrong or just haven't installed something... must be so.

I've really stuck. Any help is appreciated.

---

### Post by Unnicknamed on 2008-03-22
I know you asked for the 10g version. But I succesfully installed the 11g.

[http://www.pythian.com/blogs/654/installing-oracle-11g-on-ubuntu-linux-710-gutsy-gibbon](http://www.pythian.com/blogs/654/installing-oracle-11g-on-ubuntu-linux-710-gutsy-gibbon)

This is the guide I used. Hope it helps you in some way. I'm on amd64 too.

---

### Post by mmilkin on 2008-03-28
Ok idk if this will help you but i had many many many problems getting oracle 10g running on gutsy.  My install would just stop during console startup however i finally I got around some of my problems of installing oracle by installing 2.3 patch.  If you are just starting to use oracle i would not even let the installer configure the db till after you apply the patch.

Now im hitting another problem, Im having text search problems with this release that my friend using Gentoo is not seeing.  Has any one seen any problems with oracle 10g EE in terms of text search.

---

