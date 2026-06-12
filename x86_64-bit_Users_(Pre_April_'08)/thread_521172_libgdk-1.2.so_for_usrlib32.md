---
title: "libgdk-1.2.so for /usr/lib32"
date: 2007-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tiny_D on 2007-08-09
Hi,

I'am searching for way to install libgdk-1.2.so 32bit on an x86_64 Kubuntu system.

I had install the ia32 package and the ia32-lib-gtk, without success.

Anybody a hint to resolve my problem?

---

### Post by Kilz on 2007-08-09
> **Tiny_D said:**
> Hi,

I'am searching for way to install libgdk-1.2.so 32bit on an x86_64 Kubuntu system.

I had install the ia32 package and the ia32-lib-gtk, without success.

Anybody a hint to resolve my problem?

There would be, but after a search libgdk-1.2.so isnt included in any 32bit packages. I cant even find it in 64bit packages. It doesnt appear to be a Ubuntu file. If it were we could use dpkg -x somedebname.deb to extract it. Then copy it to /usr/lib32 .

---

### Post by Cappy on 2007-08-09
You can use getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Install getlibs like this:
```

cd /tmp
wget -q http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs
chmod +x getlibs
sudo mv getlibs /usr/bin
cd ~

```

Now you can install the 32-bit libgdk-1.2.so.0
```

sudo getlibs -32 libgdk-1.2.so.0

```

If you are trying this for a 32-bit binary that will not run you can also try
```

sudo getlibs /path/to/binary

```

---

### Post by Kilz on 2007-08-09
Cappy, will getlibs even find the file if it isnt in the Ubuntu repositories?

---

### Post by Cappy on 2007-08-09
That file is in the repos. What happened was that Tiny_D thought the .0 in **libgdk-1.2.so**.0 wasn't important when he posted it. Typing it in google showed me the correct name of the library has ".0" on the end.
 
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libgdk-1.2.so.0&searchmode=searchfiles&case=insensitive&version=feisty&arch=amd64](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libgdk-1.2.so.0&searchmode=searchfiles&case=insensitive&version=feisty&arch=amd64)

But to your actual question, no, getlibs will only use the Ubuntu repos (to make sure that all of the libraries are compatible with a user's Ubuntu distro).

---

### Post by Tiny_D on 2007-08-09
Great it works!

Thanks everybody, Cappys howto works fine!

---

