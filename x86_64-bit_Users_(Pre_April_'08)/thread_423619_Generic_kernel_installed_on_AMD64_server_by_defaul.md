---
title: "Generic kernel installed on AMD64 server by default?"
date: 2007-04-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by pressureman on 2007-04-26
I've recently overseen the installation of two ubuntu server installs (feisty, amd64), on an AMD64 box and an EM64T box, and on both boxes I noticed that they had linux-image-generic (ie, a desktop kernel) installed by default.

I installed an i386 ubuntu server inside vmware, and noticed it had linux-image-server installed by default, as I'd expect.

Previous installs of ubuntu server on real hardware (dapper, amd64) have also always installed linux-image-server.

Is this perhaps a bug in the amd64 server installer script, or is it doing some kind of hardware check and deciding that linux-image-generic is best for me?!?

---

### Post by kuja on 2007-04-29
That's really odd. You sure you used the server disk? If not, I'd file a bug if I were you.

---

### Post by pressureman on 2007-04-29
> **kuja said:**
> That's really odd. You sure you used the server disk? If not, I'd file a bug if I were you.

Yes, definitely server CD, otherwise I'd have a nice bloated (but pretty) GNOME desktop on my VMware servers... ;-)

I know it's odd, I thought I was going crazy myself, but so far two installs have been like that. Admittedly, the installs were done by two other separate individuals, but I trust that they know what they're doing.

I'll do a third install myself today on an Intel EM64T Pentium.

---

### Post by pressureman on 2007-04-29
I've just completed an install of Feisty server amd64 on a 64 bit Intel Pentium D, and noticed that the installer was running 2.6.20-15-generic. It also installed that kernel to hard disk...

It's very strange, because according to the ubuntu-server.seed file on the CD, it should be forcing the server kernel:

```

# Always install the server kernel.
d-i base-installer/kernel/override-image    string linux-amd64-server
# Only install basic language packs. Let tasksel ask about tasks.
d-i pkgsel/language-pack-patterns   string
# No language support packages.
d-i pkgsel/install-language-support boolean false

```

I'm surprised other people haven't noticed yet...

:confused:

---

### Post by geakMonkey on 2007-05-01
Hello,

I isntalled Ubuntu 6.06 LTS server cd a few months ago. I have been trying to figure out why I have a K-7 kernel  image. Is this issue similar? How can I get my AMD64 kernel image?

Thx

---

### Post by pressureman on 2007-05-01
> **geakMonkey said:**
> Hello,

I isntalled Ubuntu 6.06 LTS server cd a few months ago. I have been trying to figure out why I have a K-7 kernel  image. Is this issue similar? How can I get my AMD64 kernel image?

Thx

If you have a K7 kernel, it sounds like you used the 32 bit installer.

---

### Post by Kilz on 2007-05-02
> **geakMonkey said:**
> Hello,

I isntalled Ubuntu 6.06 LTS server cd a few months ago. I have been trying to figure out why I have a K-7 kernel  image. Is this issue similar? How can I get my AMD64 kernel image?

Thx

As said above it looks like you installed the i386 or 32bit version. The only way is to do an complete install of the amd64 version of the server install. You can not upgrade versions from 32 to 64 bit. If you have hard drive room, you could create a separate partition, install the new server. Mount the old partition to a folder in the new install. Then copy any data files to the new server.
Server installs should always be 64bit if you have 64bit hardware imho. There is little downside since you wont be installing media players or browser plugins. You will then get the most out of your hardware.

---

### Post by sillyVM on 2007-08-23
I have recently installed two Ubuntu server 7.04 64-bit, and it uses generic kernel by default. 
```
 
Linux XXX.XXXXXXXX.com 2.6.20-15-generic #2 SMP Sun Apr 15 06:22:36 UTC 2007 x86_64 GNU/Linux

```


so i did this 
```

sudo apt-get install linux-backports-modules-2.6.20-15-server linux-headers-2.6.20-15 linux-headers-2.6.20-15-server linux-image-2.6.20-15-server

```
reboot
now it's the right kernel

To me, this 2.6.20-15-server kernel should be default. and I did install the 64bit server version.

---

### Post by Butthead on 2007-08-23
And what exactly is the matter with running the amd64-generic kernel?  It shows two CPU cores being detected when I run the "top" command on my Athlon X2 CPU? :confused:

---

### Post by pressureman on 2007-08-23
> **Butthead said:**
> And what exactly is the matter with running the amd64-generic kernel?  It shows two CPU cores being detected when I run the "top" command on my Athlon X2 CPU? :confused:

The main difference is that the generic kernels use cfq scheduler, whereas the server kernels use deadline.

Also, HZ=250 in in generic, HZ=100 in server kernels.

---

### Post by Butthead on 2007-08-24
So, basically what you are saying is if you are planning on running a server, it behooves you to use the K7 kernel, right. :confused:

The "generic" kernel is okay for a plain vanilla desktop rig (as (non-technical me) understands it), capiche? :confused:

Do I get a smiley star? :KS

---

### Post by pressureman on 2007-08-24
K7 is a 32-bit CPU, not 64-bit.

This thread is discussing/questioning why the -generic kernel is installed by default with amd64-server install, whereas -server kernel is installed by default on i386-server install.

The -generic kernels are tuned for desktop / multimedia use, where you want foreground apps to be responsive and desktop environments to be snappy.

The -server kernels are intended to give a more rounded performance, trading off snappiness in exchange for all tasks getting more or less equal scheduling priority. Also bear in mind that a lot of servers will be console mode, so they don't need the kernel tuning that a desktop gui might.

---

### Post by Butthead on 2007-08-25
Ah, okay, thanks!  Very good explanation! :)

---

