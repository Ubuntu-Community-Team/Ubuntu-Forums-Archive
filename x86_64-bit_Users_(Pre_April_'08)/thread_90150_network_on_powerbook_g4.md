---
title: "network on powerbook g4"
date: 2005-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by gig37 on 2005-11-14
I have installed 5.10 on powebook but cannot connect to internet (installed on a pc and no problem). NIC is there I can ping and get replies from google but when I try to web browse nothing or when I connect to updates nothing. I have 3 PC,s on same router and no problems except firefox will not work on any of them but konquerer does,
Hope someone can help

---

### Post by ssam on 2005-11-14
i'm assuming this is wired ethernet. (the airport extreme does not work under linux, [yet]("http://ubuntuforums.org/showthread.php?t=89113"))

this is unlikly to be powerpc specific, its easy to get a network misconfigured.

give this a try [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643) more than likely it will help, but if not we should be able to get you working.

---

### Post by gig37 on 2005-11-14
Thanks

ok going through what is says on link

---

### Post by gig37 on 2005-11-14
results

eth0: no auto negotiation 100baseTx-FD, link ok

eth0    Link encap:Ethernet  HWaddr 00:03:93:9B:E1:62
          inet addr:192.168.0.2  Bcast:192.168.0.255 Mask:255.255.255.0
          inet6 addr: fe80::203:93:fe9b:e162/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2922 (2.8 KiB)  TX bytes:2863 (2.7 KiB)
          Interrupt:41 Base address:0xf400

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0        0.0.0.0         255.255.255.0    U     0      0        0 eth0
0.0.0.0              192.168.0.1    0.0.0.0            UG    0      0        0 eth0

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=255 time=3.01 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=255 time=0.903 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=255 time=0.897ms

--- 192.168.0.1 ping statistics ---
16 packets transmitted, 16 received, 0% packet loss, time 1501ms

ping to 209.98.65.1 fails with packets filtered


ping to 209.98.65.1 is successfull

ping [www.mpr.org](www.mpr.org) is succesful

as far as I can see all working

---

### Post by gig37 on 2005-11-14
I can connect this side of roter ok. PPc cannot web browse through router but PC,s can on same router wireless or hard wired

---

### Post by ssam on 2005-11-14
could it be a problem at the web browser level?

can you install lynx or epithany or dillo on the powerpc.

does synaptic work?

maybe a ipv6 problem, there are howtos somewhere for disabling ipv6, that might help.

---

### Post by gig37 on 2005-11-14
[http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)

Followed above thread after a search. Did change in firefox now that is browsing the internet but update still not working even after disabling ipv6 i the file

---

### Post by ssam on 2005-11-14
just to check, did you reboot after modifying /etc/modprobe.d/aliases ?

---

### Post by gig37 on 2005-11-14
Yes rebooted

---

### Post by gig37 on 2005-11-14
error message when doing update

W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages (


/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-powerpc_Packages) - stat (2 No such file or directory)

---

### Post by ssam on 2005-11-14
synaptic can sometimes give scarey messages for little reason. can you press reload in synaptic and see if that fixes it.

otherwise it may be that there is something wrong with your sources list, but this seems unlikely if you have not made any changes.

---

