---
title: "Gateway ping working but no internect access"
date: 2009-08-20
forum: x86 64-bit Users
---

### Post by skravoof on 2009-08-20
Hi There,
I am new to linux, I have installed ubuntu 9.04 on my xp system with dual boot. Everything working fine however, I am unable to connect to internet. I can ping the gateway but cant access internet. See below. thanks in advance
Regards,
Ravoof
 
 
 
 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
address 149.171.187.66
netmask 255.255.255.0
network 149.171.187.0
broadcast 149.171.187.255
gateway 149.171.187.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 149.171.187.1
 
^Cravoof@Ravoof:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:24:81:1a:92:1e 
inet addr:149.171.187.66 Bcast:149.171.187.255 Mask:255.255.255.0
inet6 addr: fe80::224:81ff:fe1a:921e/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:99 errors:0 dropped:0 overruns:0 frame:0
TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100 
RX bytes:9873 (9.8 KB) TX bytes:3904 (3.9 KB)
Memory:f0000000-f0020000 
 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:5 errors:0 dropped:0 overruns:0 frame:0
TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:319 (319.0 B) TX bytes:319 (319.0 B)
 
ravoof@Ravoof:~$ ping 149.171.187.1
PING 149.171.187.1 (149.171.187.1) 56(84) bytes of data.
64 bytes from 149.171.187.1: icmp_seq=1 ttl=255 time=0.566 ms
64 bytes from 149.171.187.1: icmp_seq=2 ttl=255 time=0.823 ms
64 bytes from 149.171.187.1: icmp_seq=3 ttl=255 time=0.594 ms
64 bytes from 149.171.187.1: icmp_seq=4 ttl=255 time=0.529 ms
64 bytes from 149.171.187.1: icmp_seq=5 ttl=255 time=0.715 ms
^C
--- 149.171.187.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3996ms
rtt min/avg/max/mdev = 0.529/0.645/0.823/0.110 ms
ravoof@Ravoof:~$ route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
149.171.187.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
0.0.0.0 149.171.187.1 0.0.0.0 UG 100 0 0 eth0

---

### Post by kixome on 2009-08-20
have you tried pinging outside your network? ping yahoo.com

---

### Post by kixome on 2009-08-20
Did you enable the firewall? I have had problems with ufw and firestarter blocking my browsers although configured correctly

Do you have more than one computer on the network? ip conflict possibly? Other than that it looks as though everything is correct.

---

### Post by skravoof on 2009-08-20
pinging from terminal didnt work. come as 
ping:unknown host yahoo.com.
I had noticed the mask is when i put ifconfig command 255.255.255.0, which is supposed to be 255.255.255.128 as per network setting. Is that the problem. 
Thanks in advance

---

### Post by kixome on 2009-08-20
I do belive you've found it. I think it is trying to operate on the wrong subnet.

---

### Post by kixome on 2009-08-20
sudo ifconfig eth0 ip-address netmask

---

### Post by skravoof on 2009-08-20
The subnet mask that I gave in system>preferences>network connections is 255.255.255.128 however, when I tried ifconfig its showing 255.255.255.0? any suggestions Thanks in advance

---

### Post by kixome on 2009-08-20
sudo ifconfig eth0 <ip-address> netmask 255.255.255.128

, this should set your subnet mask

also i was wondering, does your info have to be set manually? can you not use dhcp?

---

### Post by skravoof on 2009-08-20
Subnet mask is fixed but ping yahoo.com didnt work.

---

### Post by kixome on 2009-08-20
what about using dhcp? are you able to or not? do you have to set this manually in xp?

---

### Post by skravoof on 2009-08-20
I am not sure what dhcp is? u mean dns address? if yes its fine I checked in network connections. if dns and dhcp is different how can check it? All i used in xp is  ipaddres, dns address, wns addres, gateway addres.
Thanks in advanced

---

### Post by kixome on 2009-08-20
OK answer these

do you have to enter the info manually in xp?

what isp, and/or router are you connecting through? (tell me the brand of modem and or router you are using. belkin 2wire etc

why do you have to set these manually (because of isp<internet service provider> or because of how the network is setup?

is there more than on computer on your network?

after this give me the results of ipconfig in xp.

---

### Post by skravoof on 2009-08-20
I am in university, my pc is part of big network. So I have to enter all the address manually and I dont use any modem. my ipconfig in xp results something like
ipaddress........:149.171.187.66
subnetmask....:255.255.255.128
Default Gateway:149.171.187.1
Regards,
ravoof

---

### Post by kixome on 2009-08-20
what version of ubuntu. ethernet or wireless

did your university give you this information to connect?

---

### Post by skravoof on 2009-08-20
ubuntu 9.04, and its ethernet connection

---

### Post by kixome on 2009-08-20
what about the last question, did your university give you this info <ip adress and so forth?

---

### Post by skravoof on 2009-08-20
Yes. I got all the addres from them. One more thing I noticed whenever I restarted my pc the subnetmask reset it reself to 255.255.255.0 instread of 255.255.255.128. Same thing happened if I restart the network interface with command line.
Thanks in advance

---

### Post by kixome on 2009-08-20
sudo gedit /etc/resolv.conf 

add the lines

name server <ipaddress of dns server>

---

### Post by kixome on 2009-08-20
my suggestion is to repost this I am at a loss

---

### Post by sanderj on 2009-08-20
> **skravoof said:**
> 
Everything working fine however, I am unable to connect to internet. I can ping the gateway but cant access internet. 


What exactly do you mean by "cant access internet."? No webbrowsing, no ping to name, no ping to IP address? What error message.


Anyway: Most basic and most clarifying first step with netwerk problems is always:

```

mtr -n 40.50.60.70

```

What's the output of that?


FYI: the number of hops will make a lot clear.

---

### Post by skravoof on 2009-08-24
mtr -n 40.50.60.70 gives me nothing. I cant see any thing under host colume or any other colume. Back to question, I can ping the gateway but I cant access internet.

---

### Post by sanderj on 2009-08-24
> **skravoof said:**
> mtr -n 40.50.60.70 gives me nothing. I cant see any thing under host colume or any other colume. Back to question, I can ping the gateway but I cant access internet.

Well, that is the answer to your question ... if mtr does not give you anything (so: even not a first hop), your OS does not know the default gateway. Maybe you can ping that gateway by a manual ping, but your OS does not know it's the default gateway.

I believe you had already posted your routing table. Here's mine for comparision:

```
ubuntu@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.2.254   0.0.0.0         UG    0      0        0 wlan0
ubuntu@ubuntu:~$
```


See my first hop of mtr: it's the default gateway.

```
ubuntu@ubuntu:~$ mtr -r -c 1 -n 40.50.60.70
HOST: ubuntu                      Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 192.168.2.254                 0.0%     1    1.3   1.3   1.3   1.3   0.0
  2. 192.168.1.254                 0.0%     1    2.6   2.6   2.6   2.6   0.0
  3. 82.169.27.254                 0.0%     1   20.0  20.0  20.0  20.0   0.0
  4. 195.241.4.186                 0.0%     1   21.8  21.8  21.8  21.8   0.0
  5. 195.241.4.54                  0.0%     1   21.4  21.4  21.4  21.4   0.0
  6. 193.172.66.193                0.0%     1   25.8  25.8  25.8  25.8   0.0
  7. 195.190.227.223               0.0%     1   25.0  25.0  25.0  25.0   0.0
  8. 134.222.231.234               0.0%     1  115.1 115.1 115.1 115.1   0.0
  9. 134.222.228.10                0.0%     1  108.8 108.8 108.8 108.8   0.0
 10. 134.222.226.53                0.0%     1  108.2 108.2 108.2 108.2   0.0
 11. 4.53.112.53                   0.0%     1  108.5 108.5 108.5 108.5   0.0
 12. 4.68.17.62                    0.0%     1  118.8 118.8 118.8 118.8   0.0
 13. 4.69.134.145                  0.0%     1  110.5 110.5 110.5 110.5   0.0
 14. 4.69.132.69                   0.0%     1  127.9 127.9 127.9 127.9   0.0
 15. 4.69.138.165                  0.0%     1  128.8 128.8 128.8 128.8   0.0
 16. 4.71.251.26                   0.0%     1  122.3 122.3 122.3 122.3   0.0
 17. 206.246.181.41                0.0%     1  128.6 128.6 128.6 128.6   0.0
 18. 206.246.181.10                0.0%     1  130.9 130.9 130.9 130.9   0.0
 19. ???                          100.0     1    0.0   0.0   0.0   0.0   0.0
ubuntu@ubuntu:~$ 
```

---

### Post by dcstar on 2009-08-26
> **skravoof said:**
> Hi There,
I am new to linux, I have installed ubuntu 9.04 on my xp system with dual boot. Everything working fine however, I am unable to connect to internet. I can ping the gateway but cant access internet. See below. thanks in advance
Regards,
Ravoof

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
address 149.171.187.66
netmask 255.255.255.0
network 149.171.187.0
broadcast 149.171.187.255
**gateway 149.171.187.1**
.......

That IP address belongs to a University in N.S.W Australia. Universities firewall all connections, you will **not** get direct Internet access. Ask them for the appropriate proxy settings that everybody has to use.

---

