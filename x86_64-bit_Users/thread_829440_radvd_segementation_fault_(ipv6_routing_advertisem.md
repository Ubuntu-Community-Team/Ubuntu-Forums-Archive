---
title: "radvd segementation fault? (ipv6 routing advertisement daemon)"
date: 2008-06-14
forum: x86 64-bit Users
---

### Post by Julius on 2008-06-14
I'm trying to set up my pc to act as as an ipv6 router to my 'local network'. I'm using a tunnel from tunnelbroker.net to get an addr/network.

All the other hosts on my network are windows though, I'm not sure if windows vista is configured to listen to ipv6 router advertisements but I bet it is since ipv6 is enabled by default.

I have successfully configured this ubuntu box as a router, but it only works if I manually set the ipv6 addresses on the other hosts. They're even 'pingable' from the outside world, so it's cool (and uncool at the same time :P) that they're totally accessible from the outside world like IP was always meant to be.

Anyway, radvd doesn't seem to work. 
```

Setting up radvd (1:1.0-2ubuntu1) ...
Starting radvd: [Jun 15 01:41:56] radvd: Segmentation fault
failed.

```

(I have an /etc/radvd.conf file, that's why apt-get automatically attempts to run it when it is installed).


I can't even compile radvd 1.1 since I get an error somewhere that seems it has more to do with an error on a .c file than a dependency problems.

Anybody successfully running radvd on amd64 ubuntu?

---

### Post by felker2 on 2008-06-15
Are you starting radvd as root (thus: "sudo radvd")? When starting as a normal user, I get a segfault too:

```

sander@ubuntu804:~$ radvd
[Jun 15 09:38:34] radvd: Segmentation fault
sander@ubuntu804:~$

```

BTW: How did you get a address range (not just an address) from broker.freenet6.net? 
And is your IPv6 connection stable on Ubuntu? My tun disappears a few times a day, after which I have to call "sudo tspc" again.

---

### Post by Julius on 2008-06-15
I didnt get an address from freenet6 I think. I got it from [www.tunnelbroker.net](www.tunnelbroker.net). I also got one from sixxs.net but I have to have the "link" up for a week to be able to request a subnet, whereas I got mine from tunnelbroker.net right away.

I'm still toying a bit with it. FOr sixxs.net I run aiccu (apt-get aiccu, then the configuration will require your password). Aiccu is great because it automatically updates your ipv4 end of the tunnel in case it changes.

I just set the tunnel up using the commands that tunnelbroker provides. Then I discovered that any datagrams aimed at my subnetwork were delivered to this box (and obviously discarded), so I set this box up as a router, and then assigned an ip to a vista box on my local network. SO that PC is now accessible from the outside world too. 
What I would want though is for ubuntu to send those router advertisements so that the vista pcs get an IP automatically.

---

