---
title: "[Device Driver issue] What the H3ll is wrong with Ubuntu?"
date: 2009-02-27
forum: x86 64-bit Users
---

### Post by 9812713 on 2009-02-27
I have tested the following distributions on two 64 bit computers:

Ubuntu 8.04 (64 Bit) - confirmed working
Ubuntu 8.10 (64 Bit) - doesn't work
Ubuntu 9.04 (64 Bit) - doesn't work

I do realize that the 9.04 version is still Alpha. With 8.04 everything  worked fine with all my hardware, except for my Wacom tablet. I wanted to upgrade to 8.10 when it was released and it did not work. I am now trying 9.04 and sure enough it does not work?

What seems to be happening, is the LIVE cd boots up OK, and "Connects" and gets an address from DHCP. However nothing network works. I unplug the LAN cable, and then the Ethernet adapter will not get a IP after I unplug it. 

The two NIC's that I am having problems with are:

t3g on my Acer Travelmate 5720 
r8169 on my white box computer with an ASUS M2V-VM Motherboard.

Why can't ubuntu correct this problem once and for all .. Do I need to buy Canonical a 64 Bit computer? what gives.

two releases, two useless versions to me.

W.

---

### Post by whoop on 2009-02-27
Well in 8.10 network-manager was update with some new technology, I had problems with it as well (I could not set a static ip).

If I understand your post correctly everything seems to work but you cannot do any internet related stuff.

Does pinging do anything? have you tried in terminal:
```

ping www.google.com

```
if that fails try:
```

ping 64.233.183.104

```

Just wondering what the output of those two entries are...

---

### Post by whoop on 2009-02-27
maybe completely unrelated but have you read these:
[http://ubuntuforums.org/showthread.php?t=843398](http://ubuntuforums.org/showthread.php?t=843398)
[http://ubuntuforums.org/showpost.php?p=4210510&postcount=6](http://ubuntuforums.org/showpost.php?p=4210510&postcount=6)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286489](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286489)

[http://ubuntuforums.org/showthread.php?t=261065](http://ubuntuforums.org/showthread.php?t=261065)

---

### Post by 9812713 on 2009-02-27
Ping replies:

ubuntu@ubuntu:~$ ping [www.google.ca](www.google.ca)
ping: unknown host [www.google.ca](www.google.ca)

ubuntu@ubuntu:~$ ping 64.233.183.104
connect: Network is unreachable

I need to review the material included in other forums when the time permits. 

Really bad that Ubuntu "Out of Box" experience isn't just plug and pray any more.

W.

---

### Post by Yellow Pasque on 2009-02-27
Please boot the 8.10 LiveCD and load Ubuntu "without changes". After it loads, fire up a terminal. Use *ifconfig -a* to confirm that your interface is "eth0".

Now, we'll try downing the interface, reloading the driver module, and bringing it back up with DHCP.
```
sudo ifdown eth0
sudo modprobe -r r8169   #or t3g depending on what sytem you're using
sudo modprobe r8169
sudo ifup eth0
sudo dhclient
```

Also, you might want to verify your router setup and the integrity of the LAN cable you're using.

> Why can't ubuntu correct this problem once and for all... two releases, two useless versions to me
You're free to use something else. Ubuntu is a nice distro, but if it doesn't work, either try something else or work harder to resolve the issue. You probably didn't pay  anything for Ubuntu, so no use in getting frustrated with it.

---

