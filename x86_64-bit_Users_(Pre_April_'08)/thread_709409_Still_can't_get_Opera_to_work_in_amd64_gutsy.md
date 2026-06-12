---
title: "Still can't get Opera to work in amd64 gutsy"
date: 2008-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by breaking on 2008-02-27
I prefer Opera over Firefox, and I've tried just about everything but since I'm a newb, I'm sure I'm doing something wrong.

I've already tried this:
[http://ubuntuforums.org/showpost.php?p=1167982&postcount=62](http://ubuntuforums.org/showpost.php?p=1167982&postcount=62)

But when I execute the last step, I get this: 
```
cp: target `/usr/lib32/' is not a directory: No such file or directory

```

It's not letting me make that folder to add 32bit libraries.  Any help?:confused:

---

### Post by Bad_Byte on 2008-02-27
Did you download the qt-static version?.

I downloaded the 'other/static deb' and it installed and works smooth (with the exception of flash).

---

### Post by Trindol on 2008-02-27
Not to point out the obvious...but you know there are 64-bit debs of Opera 9.50 available right? It's not perfect but definitely useable now that plugins are more or less fixed. Flash works with the script posted in this forum by Kilz.

[http://snapshot.opera.com/unix/snapshot-1823/x86_64-linux/](http://snapshot.opera.com/unix/snapshot-1823/x86_64-linux/)

---

### Post by Cappy on 2008-02-27
You need to
```
sudo apt-get install ia32-libs
```

You should install that anyway.

Also that thread you are following is outdated anyway. Getlibs can install 32-bit libraries much easier and as mentioned there is a native 64-bit version now.

---

### Post by breaking on 2008-02-27
> **Trindol said:**
> Not to point out the obvious...but you know there are 64-bit debs of Opera 9.50 available right? It's not perfect but definitely useable now that plugins are more or less fixed. Flash works with the script posted in this forum by Kilz.

[http://snapshot.opera.com/unix/snapshot-1823/x86_64-linux/](http://snapshot.opera.com/unix/snapshot-1823/x86_64-linux/)

I've already tried that.  It doesn't function.  But, I'll try it again right now just in case I was being an **** at the time.

Okay, when I try installing it says```
ERROR: Dependency is not satisfiable: libqt3-mt
```

So, I tried the suggestion of trying:
```
sudo apt-get install ia32-libs
```

Here's what I got from that:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ia32-libs has no installation candidate
```

Neither Opera packages will install.  I am at a loss.

---

### Post by breaking on 2008-02-27
Fantastic.  Now I don't even have the privileges to rename or manipulate any of the files/folders on my desktop. :roll:  So much for "bug free" linux.

---

### Post by zubrug on 2008-02-27
after you
sudo dpkg -i opera and get the libqt3 error 
do a 
sudo apt-get -f install

enjoy

---

### Post by breaking on 2008-02-29
I'd try that if I could access files.  It doesn't seem like I have the privileges to access my desktop so I can't download files to it or open them or edit them in any way.  Can anyone help me with that?  I don't recall doing anything that would restrict my user.

EDIT: Nevermind that.  I just made a new administrator account and just deleted the old one.  I have no clue why that happened but that seemed to have fixed that problem.  Now back to the Opera problem. :D

---

### Post by elarella on 2008-03-12
Here's the latest snapshot of Opera for Gutsy 64 bit.  It is very stable for my needs, so far and I am able to use Adobe Flash 9 r115 with it.  Matter of fact, I am on it right now.  :guitar:

[http://snapshot.opera.com/unix/snapshot-1834/x86_64-linux/](http://snapshot.opera.com/unix/snapshot-1834/x86_64-linux/)

---

