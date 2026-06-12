---
title: "Hamachi isn't working in 64 bit"
date: 2007-06-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by fakie_flip on 2007-06-26
Can anyone help me get Hamachi working? I don't know how to debug this problem. Here's what I've done to get it working. I first tried as a non root user. I also tried downloading it again.

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
Nevermind, I got it working. Problem solved.

---

### Post by jazzysmith on 2007-07-16
I'm having a prob with this as well but not the same one. After running:
sudo make install
I try sudo tuncfg
and the error is:
unable to execute: /sbin/tuncfg no such file or directory

I checked and it is there! what's happening?

J.

---

### Post by fakie_flip on 2007-07-17
copy and paste from the terminal

---

### Post by p2im0 on 2008-04-10
Ahh, I have just run into this same issue and after several hours searching the corners of the interwebs I've found a solution.

It all seems to lie within **ia32-libs** for 64 bit Ubuntu systems.  I now am able to run tuncfg on a headless Gutsy 7.10 (x64) server.  Previously I was receiving this error:

```
$ sudo tuncfg
sudo: unable to execute /sbin/tuncfg: No such file or directory
```

Now I'm stealing this information from the one website that helped: **[http://www.computechgroup.com/?p=360](http://www.computechgroup.com/?p=360)**

```
#install decompressor
sudo apt-get install upx-ucl-beta
#x64 bit users only - execute the next line
sudo apt-get install ia32-libs
```

The key part is the ia32-libs package.

Hope this helps someone out there!
Good luck!

-P2

---

### Post by go_beep_yourself on 2008-07-04
Exactly what 32 bit lib does Hamachi need in a 64 bit Linux? I'm using Fedora 9 64-bit now. I do not have a package ia32-libs, but I can install any 32 bit lib package through the package manager just like I can for 64 bit packages. Here's what I am getting.

[PHP][chris@localhost ~]$ sudo tuncfg
[chris@localhost ~]$ rm -rf .hamachi/
[chris@localhost ~]$ hamachi-init 
Initializing Hamachi configuration (/home/chris/.hamachi). Please wait ..

  generating 2048-bit RSA keypair .. ok
  making /home/chris/.hamachi directory .. ok
  saving /home/chris/.hamachi/client.pub .. ok
  saving /home/chris/.hamachi/client.pri .. ok
  saving /home/chris/.hamachi/state .. ok

Authentication information has been created. Hamachi can now be started with
'hamachi start' command and then brought online with 'hamachi login'.

[chris@localhost ~]$ hamachi start
Starting Hamachi hamachi-lnx-0.9.9.9-20 .. ok
[chris@localhost ~]$ hamachi login
Logging in ....>..... failed
[chris@localhost ~]$ sudo ifconfig ham0 up
[chris@localhost ~]$ sudo hamachi login
Logging in ....>..... failed[/PHP]

I saw something on the forum about the firewall not allowing udp packets as a problem. I didn't know if that was my problem or not, but I went ahead and disabled the firewall by flushing iptables. Still I have the same results and ever once in a while, this error appears also.

[chris@localhost ~]$ sudo hamachi start
04 07:30:19.469 [   0] [ 3502] tap: bad response 00007f00
04 07:30:19.469 [   0] [ 3502] Failed to configure tap device to use 5.224.253.29/4278190080

I'm seriously started to get frustrated at things not working even though I am very experienced with Linux, but I'd probably pull my hair out if I had to switch completely back to Windows. I hope someone will reply to this.

---

