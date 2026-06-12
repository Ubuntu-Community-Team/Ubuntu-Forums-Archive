---
title: "forgot command line code for installing debs, force arch"
date: 2008-05-01
forum: x86 64-bit Users
---

### Post by miesnerd on 2008-05-01
Hey,
I have a 64 bit Ubuntu 8.04 install.
I downloaded the first beta of OOo 3.0.
Its in multiple debs, arch is i386.
How do I install all the debs with one line, and force arch?

Thanks.

EDIT: its 64 bit linux, not 65 bit. lol.

---

### Post by Yellow Pasque on 2008-05-01
I don't quite understand what you're trying to do. Whether you want to run the 32-bit or 64-bit version of the program, you still need a deb that's compatible with the amd64 architecture so the program can install correctly. If one is not available, then you have a few options. You can either build from source with the gcc-multilib and ia32 libraries and -m32 flag or run a 32-bit chroot environvment (not recommended in most cases).

My question to you is: why are you trying to run a 32-bit version of the program?

---

### Post by miesnerd on 2008-05-01
Right.
My understanding was that OOo only released the beta as 32 bit, not as 64 bit.
I know it can easily be done, because I did the same thing with the alpha a few months ago.
I want to install a bunch of debs together, that need to be installed together, so I cant just double click each one.

i know there is an option for -forcearch or -forceinstall or something like that.

---

### Post by Yellow Pasque on 2008-05-01
Can you link me to the project's page? A search of OOo is difficult.

---

### Post by Grishka on 2008-05-01
sudo dpkg -i --force-architecture

---

### Post by steveneddy on 2008-05-01
> **Grishka said:**
> sudo dpkg -i --force-architecture

actually it's

```



sudo dpkg --force-architecture -i **PackageName.deb**

```

to install 32 bit software on 64 bit machines

---

### Post by rmtatum on 2008-05-02
[http://www.google.com/search?q=force+architecture+apt&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=force+architecture+apt&ie=UTF-8&oe=UTF-8)
;)

---

### Post by miesnerd on 2008-05-02
> **steveneddy said:**
> actually it's

```



sudo dpkg --force-architecture -i **PackageName.deb**

```

to install 32 bit software on 64 bit machines

right, except I want it to install all the .debs in one folder.
What else needs to be in there?
Thanks for help people. I wish I could have gotten back faster, cuz i remembered the dpkg -i part..

---

### Post by jocko on 2008-05-02
> **Temüjin said:**
> Can you link me to the project's page? A search of OOo is difficult.
Why would it be difficult? This is the first result from google (for those that don't know the address of openoffice.org... well it's the same as the name):
[http://www.openoffice.org/](http://www.openoffice.org/)

---

### Post by Yellow Pasque on 2008-05-02
> **jocko said:**
> Why would it be difficult? This is the first result from google (for those that don't know the address of openoffice.org... well it's the same as the name):
[http://www.openoffice.org/](http://www.openoffice.org/)
Oh, I did not realize that OOo = OpenOffice.

---

### Post by Grishka on 2008-05-02
> **miesnerd said:**
> right, except I want it to install all the .debs in one folder.
What else needs to be in there?
Thanks for help people. I wish I could have gotten back faster, cuz i remembered the dpkg -i part..

```
$ sudo dpkg -i --force-architecture ~/folder/*
```

---

### Post by miesnerd on 2008-05-03
> **Grishka said:**
> ```
$ sudo dpkg -i --force-architecture ~/folder/*
```

thanks man. That worked. Now all I have to do is try to remember where in /opt/ it installs the shotcut to make program start.

EDIT:
Nevermind. I got it-- its "/opt/ooo-dev3/program/soffice" to get the program to open to the initial screen once its installed.
OpenOffice rocks.

---

