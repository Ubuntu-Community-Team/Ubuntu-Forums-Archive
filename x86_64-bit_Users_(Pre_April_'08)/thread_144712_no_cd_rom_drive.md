---
title: "no cd rom drive"
date: 2006-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by robo_creeler on 2006-03-14
I'm trying to install ubuntu on my powerbook but the cd drive is dodgy.  I have another powerbook at my disposal.  is there any way I can indstall ubuntu onto powerbookA by running the installer on powerbookB.  via ethernet or something?  can I run the installer off an iPod?

thanks, stevfen.

---

### Post by Rxke on 2006-03-18
You may try netbooting, and then installing from the powerbook you setup as server. I don't know of any Ubuntu-PPC specific info about that, but I succesfully did it once, using a howto from Debian (which I can't find anymore...) But NetBSD could maybe give you a clue?

[http://www.netbsd.org/Ports/macppc/faq.html#boot-net](http://www.netbsd.org/Ports/macppc/faq.html#boot-net)

---

### Post by robo_creeler on 2006-03-22
thanks, will check this out soon, sounds promising.

---

### Post by jdp on 2006-03-22
Depending on the madels of Powerbook you are using, you may be able to put one into FireWire Target Disk Mode and conenct it to the other as if it were an external drive.

---

### Post by bodyguard on 2006-03-24
I am dealing with similar problem today. I’ve got 2 iMacs with broken CD-ROM drive. I have tried booting from USB CD with no luck. But with netboot I succeeded. Here is my way:
1. Read ubuntu PPC manual ("doc" folder on CD or from [http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-powerpc/current/doc/manual/en/]("http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-powerpc/current/doc/manual/en/"))
Especially paragraphs: 
4.5.2 **apt-get dhcpd **(copy manual to /etc/dhcpd.conf, change IP’s then type **/etc/init.d/dhcpd start**)
4.5.3 **apt-get in.tftpd** (**in.tftpd -l -s /tftpbootdir**) 
4.5.4 Rather go for dapper netboot files at [http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-powerpc/current/images/powerpc/netboot/]("http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-powerpc/current/images/powerpc/netboot/")
You can try to do the server side of install by booting from Live-CD.
2. Do as sad above (literally - "servername" is a good name for a temporary server - do not change anything but IP's )
3. Connect the server and client with HUB or a crossover cable. (just two of them - you can reconnect to Internet after you boot the client) 
4. Turn on the client and hold down Option+Command+O+F until white screen appears saying you may release them
5. At the "0>" prompt type 
```
0> boot enet:0,yaboot
```
and press Enter
 
If everything goes right you should end up with yaboot boot prompt - pressing Enter will do.
 
Troubleshooting:
1. If nothing happens for 120s and boot prompt comes back try to disable firewall on server (**iptables –F** will do)
2. I can’t boot breezy that way but dapper works for now.

---

