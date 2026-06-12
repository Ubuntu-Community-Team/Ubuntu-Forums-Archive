---
title: "4GB of RAM installed only 2.9 showing"
date: 2009-05-06
forum: x86 64-bit Users
---

### Post by derekc4 on 2009-05-06
On the the gnome system monitor it says I only have 2.9GB of RAM while I am certain I have 4. Why does this happen? And how can I fix it? I spent a lot of money on this laptop and want to use all of its power. Thank you.

---

### Post by fballem on 2009-05-06
> **derekc4 said:**
> On the the gnome system monitor it says I only have 2.9GB of RAM while I am certain I have 4. Why does this happen? And how can I fix it? I spent a lot of money on this laptop and want to use all of its power. Thank you.

It sounds like you may have installed the 32-bit version of ubuntu. Any 32-bit system (linux or windows) will only be able to address a maximum of 3 GB of RAM.

To test this, use an application called Sysinfo. I access this from Applications > System Tools > Sysinfo.

If it's not there, then install it from Synaptic (System > Administration > Synaptic Package Manager). You can search for sysinfo and install it.

My screenshot is below, showing that I have the 64-bit version of ubuntu installed. I think that when you run yours, you will find that it's the 32-bit version. Please note that I have clicked Details to open up the bottom part of the screen.

If your processor supports it, you will need to install the 64-bit version.

Hope this helps,

---

### Post by derekc4 on 2009-05-06
It says 4.3.3 i486. Is that 32 bit?

---

### Post by Yellow Pasque on 2009-05-07
> **derekc4 said:**
> It says 4.3.3 i486. Is that 32 bit?
Yes.

The best way to check what version of Ubuntu you have installed is:
```
uname -m
```
If you're running 64-bit Ubuntu, it will return "x86_64"; if you're running 32-bit Ubuntu, it will return "i686" or something else.

---

### Post by fballem on 2009-05-07
> **Temüjin said:**
> Yes.

The best way to check what version of Ubuntu you have installed is:
```
uname -m
```
If you're running 64-bit Ubuntu, it will return "x86_64"; if you're running 32-bit Ubuntu, it will return "i686" or something else.

It does look like you are running 32-bit, using Sysinfo. You may wish to open a terminal and copy and paste the following code into it:

```

uname -m

```

Ths should confirm that you are running 32-bit. If you are running 64-bit, then it will say x86_64. If it says anything else, then you are running 32 bit.

To solve the problem:

1) download the 64-bit version of ubuntu 9.04 from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download), making sure that you select the 64-bit version for download.
2) copy the downloaded file to a CD.
3) save any data to an _external drive_. For me, this includes the visible contents of my home directory and a backup of my Evolution files. If you need more information, let us know and we'll provide more details.
4) do a clean installation of ubuntu 64-bit. You cannot upgrade from 32-bit to 64-bit - it must be a clean installation.
5) restore your data from the external drive.

Hope this helps,

---

