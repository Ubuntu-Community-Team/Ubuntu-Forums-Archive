---
title: "An help with AMD 64 X2 - ASUS A8N-E - ASUS X1600 PCI EX"
date: 2006-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by mschievano on 2006-04-16
I am expecting lot of problems after the migration from classic AMD 32 and AGP card to AMD 64 X2 , Asus A8N-E , and Asus X1600 512 Mb pci-ex video card.

It stands that after 2 days of various :twisted: , now i'm writing from linux

Now, i find those difficulties:

[LIST=1]
[*]the motherboard have a CD with Linux drivers inside: i'm not able to install those drivers totally
[*]The ATI driver wont work with Xorg 7, so the screen start only with VESA driver
[*]I'm non able to understand when I can consider this installation finished...
[/LIST]

Plus, there are also this problems:
[LIST]
[*]The AMD 64 sources are poor in paragon with the 32 bit. So a lot of packages doesn't exist for AMD 64 pure (flash, java). ](*,) 
[*]For libdvdcss2 I used the compilation from the source (and this work). For this , wiki guide help: [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
[*]My sources.list doesn't satisfate me... 
[/LIST]

Sources.list :
```

# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

#dapper 6 (sources, GPG key: 437D05B5)
deb http://it.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

# Dapper 6 src (sources, GPG key: 437D05B5)
deb-src http://it.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

#standard 5.10
deb http://it.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

#other applications

#wine
deb http://wine.sourceforge.net/apt/ binary/

#kde
deb http://kubuntu.org/packages/kde35 breezy main

#openoffice
deb http://people.ubuntu.com/~doko/OOo2 ./
deb http://apt.bxlug.be ooo/ # packages additionels pour openoffice

#win32cod
deb-src ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

#PLF
# Penguin Liberation Front (packages)
# binary amd64 non abilitati
#deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free 
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

```

Can someone help me? :-k 

Happy Easter

---

### Post by mschievano on 2006-04-22
with little step the distro grown every day.

I find java:
[http://192.18.108.139/ECom/EComTicketServlet/BEGIN0D78D430B040F982FA85C0171675DEE0/-2147483648/1444358727/1/682154/682130/1444358727/2ts+/westCoastFSEND/jre-1.5.0_06-oth-JPR/jre-1.5.0_06-oth-JPR:26/jre-1_5_0_06-linux-amd64.bin](http://192.18.108.139/ECom/EComTicketServlet/BEGIN0D78D430B040F982FA85C0171675DEE0/-2147483648/1444358727/1/682154/682130/1444358727/2ts+/westCoastFSEND/jre-1.5.0_06-oth-JPR/jre-1.5.0_06-oth-JPR:26/jre-1_5_0_06-linux-amd64.bin)

I use vesa driver instead of ati driver (waiting for a stable version that work with xorg 7 and X1600)

I use the kernel 2.6.15-20-amd64-k8 #1 SMP PREEMPT that made the integrated soundcard work.

---

