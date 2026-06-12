---
title: "Hamachi/ghamachi problem"
date: 2007-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by OsakaWilson on 2007-06-10
When I try to run ghamachi (./ghamachi) it briefly pops up then disappears and I get the message:

Aborted (core dumped)

Anyone know what's wrong?

I'm on an AcerAspire 5100 Laptop with a 64bit processor running Feisty.

---

### Post by dutchman72 on 2007-06-11
It might be the version you are using. My friends and I are using Hamachi to play lan games from our houses without all the traveling needed. We noticed with the latest update that no matter what was done it wouldn't function.

Try going back one version and seeing if that works. (Btw, that version DOES work. They all run windows, but I use linux to join them and have no issues.)

---

### Post by fabertawe on 2007-06-13
Are you using the latest version? **[Beta 0.8.1]("http://www.penguinbyte.com/software/ghamachi/")** works for me, I was having crashes with the previous version.

Paul

---

### Post by Pengwyn44 on 2007-06-15
I am running Ubuntu 7.04 and had a problem with gHamachi which worked OK on 6.06.
The latest download of gHamachi 0.8.1 however does work.

---

### Post by fakie_flip on 2007-06-26
Is this a problem with 64 bit? I think so. Hamachi worked fine in 32 bit. I do have all the 32 bit library packages installed too.

Here's what I've done to get it working. I first tried as a non root user. I also tried downloading it again.

```
chris@ubuntu:~/Desktop$ sudo su -
Password:
root@ubuntu:~# cd /home/chris/Desktop/
root@ubuntu:/home/chris/Desktop# tar -xf hamachi-0.9.9.9-20-lnx.tar.gz 
root@ubuntu:/home/chris/Desktop# cd hamachi-0.9.9.9-20-lnx
root@ubuntu:/home/chris/Desktop/hamachi-0.9.9.9-20-lnx# ls
CHANGES  LICENSE          LICENSE.openssl  Makefile  tuncfg
hamachi  LICENSE.openssh  LICENSE.tuncfg   README
root@ubuntu:/home/chris/Desktop/hamachi-0.9.9.9-20-lnx# make install

Copying hamachi into /usr/bin ..
Creating hamachi-init symlink ..
Compiling tuncfg ..
Copying tuncfg into /sbin ..

Hamachi is installed. See README for what to do next.
root@ubuntu:/home/chris/Desktop/hamachi-0.9.9.9-20-lnx# hamachi start
26 12:44:36.309 [   0] [ 6461] tap: connect() failed 2 (No such file or directory)
root@ubuntu:/home/chris/Desktop/hamachi-0.9.9.9-20-lnx# 
```

---

### Post by fakie_flip on 2007-06-26
Okay, problem solved. Hamachi is working fine.

---

### Post by OsakaWilson on 2007-06-27
Thanks everyone for the replies. I had a motherboard meltdown and am still using another machine. I'll put your info/advice to work when I get it running again.

---

### Post by lazyart on 2007-06-27
Beta 0.8.1 gives me this message:```
ghamachi: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
```
Although the file does exists.  On my 32bit Feisty it runs like a champ.  I am still connected to my VLAN via command line, but the graphical frontend doesn't launch.

---

### Post by fakie_flip on 2007-06-29
have you done

sudo apt-get install ia32-libs*

If you don't know how to deal with these problems and don't want to learn, you should be using the 32 bit Ubuntu.

---

### Post by shoofy on 2007-07-02
> **fakie_flip said:**
> Okay, problem solved. Hamachi is working fine.

I'm getting the same problem. How did you solve it?

EDIT: Never mind, I solved it too. I ran 'sudo tuncfg' and then it worked.

---

### Post by badder on 2007-07-04
i get the beta version 0.8.1 and and worked here

---

### Post by fakie_flip on 2007-07-15
> **lazyart said:**
> Beta 0.8.1 gives me this message:```
ghamachi: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
```
Although the file does exists.  On my 32bit Feisty it runs like a champ.  I am still connected to my VLAN via command line, but the graphical frontend doesn't launch.

You must have the 32 bit libgtk-x11-2.0.so.0 because Hamachi is in 32 bit.

---

### Post by fakie_flip on 2007-07-15
I solved my problem by going into the tuncfg directory and running sudo make install.

---

