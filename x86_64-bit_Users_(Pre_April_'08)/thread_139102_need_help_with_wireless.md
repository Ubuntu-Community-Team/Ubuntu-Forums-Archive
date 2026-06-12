---
title: "need help with wireless"
date: 2006-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by otake-tux on 2006-03-03
I compiled ndiswrapper 1.7 and I have the broadcom drivers for my chipset but for some reason I can't connect nor can my laptop detect wireless networks.  

I have a turion 64 bit ACER 5004WLMi with the following broadcom chipset:
 14e4:4318

Any help would be much apreciated.

---

### Post by anacron on 2006-03-03
if you type iwconfig, is your wireless detected?
are the drivers ok? did you modprobe ndiswrapper etc?

in any case, what you could try is [this]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29")

also check if you can find any networks with iwlist scan
if it founds something your drivers are probably working, so you can check other possible problems.

wireless troubleshooting guide should help you quite much, if you can't figure someting out, then post again, someone will help :)

---

### Post by otake-tux on 2006-03-03
[QUOTE=anacron]if you type iwconfig, is your wireless detected?
are the drivers ok? did you modprobe ndiswrapper etc?

in any case, what you could try is [this]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29")

also check if you can find any networks with iwlist scan
if it founds something your drivers are probably working, so you can check other possible problems.

wireless troubleshooting guide should help you quite much, if you can't figure someting out, then post again, someone will help :)[/QUOTE]

```
iwconfig

[lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

the drivers say driver present and hardware present and yes I did modprobe ndiswrapper.  However iwlist scan returns :

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

wlan0     No scan results

```

---

### Post by otake-tux on 2006-03-03
```
 ping -c 4 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.042 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.027 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.029 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.022 ms

```

```
 ping -c 4 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.035 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.025 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.023 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.018 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.018/0.025/0.035/0.007 ms
iamgod@Ubuntu-Linux:~$ ping -c 4 <192.168.1.11>
bash: syntax error near unexpected token `newline'
iamgod@Ubuntu-Linux:~$ ping -c 4 192.168.1.11
PING 192.168.1.11 (192.168.1.11) 56(84) bytes of data.

--- 192.168.1.11 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2998ms

```

```
 ping -c 4 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.103 icmp_seq=2 Destination Host Unreachable
From 192.168.0.103 icmp_seq=3 Destination Host Unreachable
From 192.168.0.103 icmp_seq=4 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2999ms
, pipe 3
iamgod@Ubuntu-Linux:~$ ping -c 4216.239.57.99
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
            [-M mtu discovery hint] [-S sndbuf]
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination

```

I dont know what to make out of some of these results...

---

### Post by amd-64 on 2006-03-03
Try this 

sudo ifup wlan0 
Also make sure your wireless is on. It should start receiving with the orange led blinking. 
[ Take a look at this thread]("http://ubuntuforums.org/showpost.php?p=581811&postcount=18")

---

