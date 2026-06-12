---
title: "gDesklets problems installing in x86-64"
date: 2008-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by JoshuaRL on 2008-02-18
Okay, it installs fine.  But whenever I try to run it, the daemon can't be found.  Any ideas?

I've tried sudo dpkg -i --force-all package_name.deb
It doesn't work.

I found an AMD64bit deb [here,](http://www.mirrorservice.org/sites/ftp.debian.org/debian/pool/main/g/gdesklets/) but it didn't work.  It said that libc6 was an unsatisfiable dependency.

I tried to use getlibs to get libc6.  That worked just fine, and the i386 gDesklets installed without problems.  But it doesn't work.

And so I figured that I'd try to install the AMD64 deb since I'd installed libc6.  Nope, didn't work.

Anybody have any ideas?

---

### Post by Cappy on 2008-02-18
Try
```
sudo getlibs /usr/bin/gdesklets
```

You need to post what error you get when you run ```
gdesklets
``` from the terminal.

Why aren't you using gdesklets from the repos?

---

### Post by findus on 2008-02-18
Isn't the version of python the issue here?

See here:

[http://ubuntuforums.org/showthread.php?t=582721&highlight=gdesklets](http://ubuntuforums.org/showthread.php?t=582721&highlight=gdesklets)

I installed the correct python version, changed the necessary files and it works perfectly with the gdesklets versions in the repos.

HTH

Fin

EDIT: It's post #8in the above link that worked for me!

---

### Post by JoshuaRL on 2008-02-18
> **Cappy said:**
> Try
```
sudo getlibs /usr/bin/gdesklets
```

You need to post what error you get when you run ```
gdesklets
``` from the terminal.

Why aren't you using gdesklets from the repos?

I'll try that when I get back home.  I tried the one from the repos and it had the same issue.  I looked for it at packages.ubuntu.com and I thought it was x86 only.  But I may be wrong.

---

### Post by JoshuaRL on 2008-02-18
> **findus said:**
> Isn't the version of python the issue here?

See here:

[http://ubuntuforums.org/showthread.php?t=582721&highlight=gdesklets](http://ubuntuforums.org/showthread.php?t=582721&highlight=gdesklets)

I installed the correct python version, changed the necessary files and it works perfectly with the gdesklets versions in the repos.

HTH

Fin

EDIT: It's post #8in the above link that worked for me!

Sweet, I'll try that if the getlibs one doesn't work. 

 I appreciate that guys, don't know how I missed that in all my Googling and forum searches.

---

### Post by Yellow Pasque on 2008-02-18
Yeah, that's a good thread. I was going to dig it up, but findus beat me to it (thanks, findus).

---

### Post by JoshuaRL on 2008-02-19
Just in case anyone was wondering, I got this from the terminal:

```

joshua@ubuntu64:~$ gdesklets
Starting gdesklets-daemon...
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.

```
Thats after getlibs

Trying python fix next.

---

