---
title: "Forgetful Network Settings"
date: 2008-02-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pyre_Vulpimorph on 2008-02-19
Hello! I'm luvin' Ubuntu, but I *gasp* have a problem with the Network Settings Manager.

You see, in order to connect to the internet, I must use the DNS addresses that Earthlink gave me to use; with "Roaming Mode Enabled". These work fine, and I saved these settings as location, "dsl settings".  This works great, and I get a reliable 155-165 KB/s connection

The problem is that whenever I reboot my computer, or even "Hibernate", the network manager always forgets my settings.  I have to go to System--->Administration--->Network, re-enter my admin passord, and re-enable the location "dsl settings" and click APPLY.

Every. Time. I. Reboot.

Needless to say, I'm getting slightly annoyed. ESPECIALLY since there is a user account that does not have admin privilages and I am needed to babysit that user just so he can access the internet.

Please tell me I just an ex-Microserf dork who can't navigate Linux.   <_<

](*,)]

---

### Post by CRCarl on 2008-02-20
Yea, that is kinda buggy. This thread addresses the issue and provides a workaround. - 
[URL="http://ubuntuforums.org/showthread.php?t=407621"]
http://ubuntuforums.org/showthread.php?t=407621[/URL]

---

### Post by Pyre_Vulpimorph on 2008-02-20
Ugh! No avail.

Thank you, **CRCarl** for that link, but altering "dhclient.conf" didn't help me after reboot.
I added the appropriate DNS addresses under "#prepend domain-name-servers" but still nothing happened after I saved the changes and rebooted.

I have thus removed my modifications and returned the file to its original state.

:(

---

### Post by CRCarl on 2008-02-20
Opps - Did you leave the "#" at the beginning of the line? That is the start of a comment indicator. My line looks like this - 

```
prepend 208.67.222.222 208.67.220.220
```

after that lets restart networking, just because - 
```

sudo /etc/init.d/networking restart
```

You should not have to reboot. Remember in any .conf file, the "#" character indicates the start of a comment and those lines are ignored. 

Let me know. 

Craig

---

### Post by Pyre_Vulpimorph on 2008-02-21
OK, I'm getting nowhere.  All I want to do is boot up Ubuntu and *immediately* connect with Firefox, without monkeying with network settings.  That is, of course, the point of rebooting after using gedit to alter the conf file.

Here is the file in its original state.

==============================================================
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
===============================================================

Originally, the "prepend" line says:

**#prepend domain-name-servers 127.0.0.1;**

So I changed it to say:

**#prepend domain-name-servers 207.69.188.185, 207.69.188.186;**

After restart/reboot; I could not connect.  So I tried your advice and input this:

**#prepend 207.69.188.185 207.69.188.186;**

Failure.  After restart/reboot, I still had to go to the Network Manager and re-enable my saved location to access the internet and make this post.

*sigh* Am I doing something wrong?  I believe I'm following your help the way you intended, Craig, but maybe I misunderstood something.  Are you telling me to remove the "#" before "prepend"?  Am I making a punctuational error? (  ,  .  ;  :  )

I am very grateful for the help you are giving me, but I'm at a loss.

](*,)                #-o              ](*,)               [-o<

---

### Post by Yellow Pasque on 2008-02-21
> *sigh* Am I doing something wrong? .. Are you telling me to remove the "#" before "prepend"?
YES, THAT IS EXACTLY WHAT HE'S TELLING YOU!
**Do not put the '#' symbol in front of the line unless you want that line to be an inactive "comment" line**

---

### Post by Pyre_Vulpimorph on 2008-02-21
All right, all right; while I may be a moron, there is no need for you to shout.  :-s

In any case, removing the "#" before "prepend" didn't help anything.

In their exactness, I tried these lines, sudo-restarting after each mod:

**prepend domain-name-servers 207.69.188.185, 207.69.188.186;**
**prepend domain-name-servers 207.69.188.185 207.69.188.186**
**prepend 207.69.188.185, 207.69.188.186;**
**prepend 207.69.188.185 207.69.188.186**

None of these modifications allowed me to connect to the internet after restart/reboot.  I still have to monkey with the Network Manager and re-enable my saved location.

.......I sure hope this bug is fixed in Hardy Heron...........

---

### Post by Yellow Pasque on 2008-02-21
> **Pyre_Vulpimorph said:**
> All right, all right; while I may be a moron, there is no need for you to shout.  :-s

Sorry, I get a little excited some times.:oops:

---

### Post by CRCarl on 2008-02-23
So it sounds like something else might be the issue. (not DNS) 

After you reboot, without changing the network configuration in any way can you - (attach the output)

```
ping 207.69.188.185
```

What about 

```
 tracepath gestas.net
```

and finally what is the output of 

```
ifconfig
```

Temüjin - Patience my friend, once upon a time you were a newbie too.

---

### Post by Pyre_Vulpimorph on 2008-02-24
Ok, I have absolutely NO IDEA what just happened, but I rebooted, accessed the conf file to make sure the "prepend" line was the way I wanted it, sudo-restarted the network, and ran the "ping", "tracepath", and "ifconfig" like you said, got some results......and the internet worked right away.

??????????????

I mean, I'm thrilled that FireFox connected to the net without me going to the Network Manager, but I don't know why.  Was it sheer dumb luck?!  I honestly don't know what I did different.

Anyway, these were the results of those tests:

===============================================================
dillon@koontz-linux64-pc:~$ ping 207.69.188.185
PING 207.69.188.185 (207.69.188.185) 56(84) bytes of data.
64 bytes from 207.69.188.185: icmp_seq=1 ttl=245 time=29.1 ms
64 bytes from 207.69.188.185: icmp_seq=2 ttl=245 time=27.9 ms
64 bytes from 207.69.188.185: icmp_seq=3 ttl=245 time=27.5 ms
64 bytes from 207.69.188.185: icmp_seq=4 ttl=245 time=28.4 ms
64 bytes from 207.69.188.185: icmp_seq=5 ttl=245 time=27.7 ms
64 bytes from 207.69.188.185: icmp_seq=6 ttl=245 time=27.8 ms
64 bytes from 207.69.188.185: icmp_seq=7 ttl=245 time=27.6 ms
64 bytes from 207.69.188.185: icmp_seq=8 ttl=245 time=27.2 ms
64 bytes from 207.69.188.185: icmp_seq=9 ttl=245 time=26.8 ms
64 bytes from 207.69.188.185: icmp_seq=10 ttl=245 time=28.4 ms
64 bytes from 207.69.188.185: icmp_seq=11 ttl=245 time=28.2 ms
64 bytes from 207.69.188.185: icmp_seq=12 ttl=245 time=26.9 ms
64 bytes from 207.69.188.185: icmp_seq=13 ttl=245 time=27.0 ms
64 bytes from 207.69.188.185: icmp_seq=14 ttl=245 time=27.8 ms
64 bytes from 207.69.188.185: icmp_seq=15 ttl=245 time=27.9 ms
64 bytes from 207.69.188.185: icmp_seq=16 ttl=245 time=27.1 ms
64 bytes from 207.69.188.185: icmp_seq=17 ttl=245 time=27.6 ms
64 bytes from 207.69.188.185: icmp_seq=18 ttl=245 time=27.7 ms
64 bytes from 207.69.188.185: icmp_seq=19 ttl=245 time=27.5 ms
64 bytes from 207.69.188.185: icmp_seq=20 ttl=245 time=27.4 ms
64 bytes from 207.69.188.185: icmp_seq=21 ttl=245 time=27.0 ms
64 bytes from 207.69.188.185: icmp_seq=22 ttl=245 time=27.5 ms
64 bytes from 207.69.188.185: icmp_seq=23 ttl=245 time=27.6 ms
64 bytes from 207.69.188.185: icmp_seq=24 ttl=245 time=27.5 ms
64 bytes from 207.69.188.185: icmp_seq=25 ttl=245 time=27.6 ms
64 bytes from 207.69.188.185: icmp_seq=26 ttl=245 time=28.1 ms
64 bytes from 207.69.188.185: icmp_seq=27 ttl=245 time=27.5 ms
64 bytes from 207.69.188.185: icmp_seq=28 ttl=245 time=27.4 ms
64 bytes from 207.69.188.185: icmp_seq=29 ttl=245 time=27.0 ms
64 bytes from 207.69.188.185: icmp_seq=30 ttl=245 time=28.1 ms
64 bytes from 207.69.188.185: icmp_seq=31 ttl=245 time=27.4 ms
64 bytes from 207.69.188.185: icmp_seq=32 ttl=245 time=26.8 ms
64 bytes from 207.69.188.185: icmp_seq=33 ttl=245 time=28.1 ms
64 bytes from 207.69.188.185: icmp_seq=34 ttl=245 time=27.5 ms
64 bytes from 207.69.188.185: icmp_seq=35 ttl=245 time=26.9 ms
64 bytes from 207.69.188.185: icmp_seq=36 ttl=245 time=26.9 ms
64 bytes from 207.69.188.185: icmp_seq=37 ttl=245 time=27.8 ms
64 bytes from 207.69.188.185: icmp_seq=38 ttl=245 time=27.4 ms
64 bytes from 207.69.188.185: icmp_seq=39 ttl=245 time=27.2 ms
64 bytes from 207.69.188.185: icmp_seq=40 ttl=245 time=27.3 ms
64 bytes from 207.69.188.185: icmp_seq=41 ttl=245 time=28.1 ms
64 bytes from 207.69.188.185: icmp_seq=42 ttl=245 time=27.3 ms
64 bytes from 207.69.188.185: icmp_seq=43 ttl=245 time=28.1 ms
64 bytes from 207.69.188.185: icmp_seq=44 ttl=245 time=27.6 ms

dillon@koontz-linux64-pc:~$ tracepath gestas.net
 1:  192.168.0.199 (192.168.0.199)                          0.249ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                            asymm  2   2.416ms 
 2:  192.168.1.1 (192.168.1.1)                              0.834ms pmtu 1492
 3:  dist1-vlan60.frsn02.pbi.net (66.122.172.66)           41.835ms 
 4:  151.164.189.12 (151.164.189.12)                       43.017ms 
 5:  ex1-p10-0.eqsjca.sbcglobal.net (151.164.191.66)      asymm  7  50.810ms 
 6:  Equinix-SJO.Peer1.net (206.223.116.30)               asymm  8  50.460ms 
 7:  oc48-po4-0.sj-mkp2-dis-1.peer1.net (216.187.88.197)  asymm  8  52.115ms 
 8:  oc48-po6-0.sj-mkp16-dis-1.peer1.net (216.187.88.133) 126.597ms 
 9:  gig6-0.sea-dis-a.peer1.net (216.187.88.201)          asymm 10  70.429ms 
10:  oc48-po6-0.van-hc21e-dis-1.peer1.net (216.187.88.213)  74.351ms 
11:  oc48-po0-0.tor-151f7-cor-2.peer1.net (216.187.114.138) asymm 15 120.684ms 
12:  oc48-po4-0.nyc-telx-dis-2.peer1.net (216.187.115.126) asymm 17 131.514ms 
13:  oc48-po3-0.nyc-75bre-dis-1.peer1.net (216.187.115.134) asymm 17 131.917ms 
14:  216.187.115.162 (216.187.115.162)                    asymm 17 133.505ms 
15:  services.squarespace.com (69.28.242.163)             asymm 17 132.677ms reached
     Resume: pmtu 1492 hops 15 back 17 

dillon@koontz-linux64-pc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:09:B0:BF:D8  
          inet addr:192.168.0.199  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:feb0:bfd8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48347 (47.2 KB)  TX bytes:69504 (67.8 KB)
          Interrupt:23 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:576 (576.0 b)  TX bytes:576 (576.0 b)
================================================================

Obviously my internet connection is working.... even if I have no clue what I did to make it work!

My "prepend" line in the conf file simply read:
**prepend domain-name-servers 207.69.188.185, 207.69.188.186;**

Wow, am I a clueless dork or what?
D'oh  !!!

---

