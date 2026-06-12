---
title: "Deleting Temp or excess files to regain disk space?"
date: 2008-09-11
forum: x86 64-bit Users
---

### Post by Lee05162004 on 2008-09-11
Hi. I'm new to Linux although I'm not completely new but I was just wondring if anyone can point me to files or folders I can safely delete to regain some disk space. I'm just referring to temp files or .deb packages that may be left over after they are installed. Thanks for the help.

---

### Post by jpkotta on 2008-09-11
> **Lee05162004 said:**
> Hi. I'm new to Linux although I'm not completely new but I was just wondring if anyone can point me to files or folders I can safely delete to regain some disk space. I'm just referring to temp files or .deb packages that may be left over after they are installed. Thanks for the help.

Get rid of cached packages:
```
sudo aptitude clean
```

I like to clean out old kernels.  Run
```
dpkg -l "*linux*" | grep ^i | grep image 
```
to see if you have extra kernels sitting around.  You can safely remove any old kernels, if you know the current one works.  ```
uname -a
```will tell you what the current kernel is.  linux-image-generic is a metapackage for the latest kernel, you probably don't want to remove that if it's installed.

---

### Post by jlc on 2008-09-11
```
$ sudo apt-get clean
```
```
$ sudo apt-get autoclean
```

How large is your hard drive?  
How large is / (root) and do you use other file systems? 
Do you install a lot of useless programs?

---

### Post by Lee05162004 on 2008-09-13
> **jlc said:**
> ```
$ sudo apt-get clean
```
```
$ sudo apt-get autoclean
```

How large is your hard drive?  
How large is / (root) and do you use other file systems? 
Do you install a lot of useless programs?

My hard drive is 100gb and I have an 80gb external hard drive too. What do you consider useless programs?

---

### Post by jlc on 2008-09-13
180GB and your running out?

Having duplicate programs like banshee and rhythmbox when you only need one.

---

