---
title: "VPN and 64 bit.. problem?"
date: 2008-11-06
forum: x86 64-bit Users
---

### Post by Takano on 2008-11-06
Do you think that the problem is 64bit?

I have installed kubuntu intrepid 64bit version.

It's seem that i can establish a connection to the VPN (pureVPN.com), but if i check my IP in internet it isn't changed.
I used KVpnc.

This is the syslog of KVpnc


```

Nov  5 00:37:40 chriest-laptop pppd[6611]: no device specified and stdin is not a tty
Nov  5 00:37:40 chriest-laptop pppd[6612]: no device specified and stdin is not a tty
Nov  5 00:37:40 chriest-laptop pppd[6613]: no device specified and stdin is not a tty
Nov  5 00:38:13 chriest-laptop kernel: [  764.635731] PPP generic driver version 2.4.2
Nov  5 00:38:13 chriest-laptop kernel: [  764.683216] PPP MPPE Compression module registered
Nov  5 00:38:13 chriest-laptop pppd[6677]: pppd 2.4.4 started by root, uid 0
Nov  5 00:38:13 chriest-laptop pptp[6681]: anon log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Nov  5 00:38:13 chriest-laptop pppd[6677]: Using interface ppp0
Nov  5 00:38:13 chriest-laptop pppd[6677]: Connect: ppp0 <--> /dev/pts/3
Nov  5 00:38:13 chriest-laptop pptp[6694]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Nov  5 00:38:13 chriest-laptop pptp[6694]: anon log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Nov  5 00:38:13 chriest-laptop pptp[6694]: anon log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Nov  5 00:38:14 chriest-laptop pptp[6694]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Nov  5 00:38:14 chriest-laptop pptp[6694]: anon log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply. 
Nov  5 00:38:14 chriest-laptop pptp[6694]: anon log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 64293).
Nov  5 00:38:14 chriest-laptop pptp[6694]: anon log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Nov  5 00:38:14 chriest-laptop pptp[6694]: anon log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Nov  5 00:38:14 chriest-laptop pptp[6694]: anon warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Nov  5 00:38:15 chriest-laptop pppd[6677]: CHAP authentication succeeded: ^JAuthentication Successful.^J
Nov  5 00:38:15 chriest-laptop pppd[6677]: CHAP authentication succeeded
Nov  5 00:38:15 chriest-laptop kernel: [  767.029305] PPP BSD Compression module registered
Nov  5 00:38:15 chriest-laptop kernel: [  767.117881] PPP Deflate Compression module registered
Nov  5 00:38:15 chriest-laptop pppd[6677]: Cannot determine ethernet address for proxy ARP
Nov  5 00:38:15 chriest-laptop pppd[6677]: local  IP address 192.168.10.44
Nov  5 00:38:15 chriest-laptop pppd[6677]: remote IP address 192.168.10.2

```

My ifconfig after the connection

```

eth0 Link encap:Ethernet HWaddr 00:1a:80:26:74:20
	inet addr:192.168.1.101 Bcast:192.168.1.255 Mask:255.255.255.0
	inet6 addr: fe80::21a:80ff:fe26:7213/64 Scope:Link
	UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
	RX packets:10321 errors:0 dropped:0 overruns:0 frame:0
	TX packets:9559 errors:0 dropped:0 overruns:0 carrier:0
	collisioni:0 txqueuelen:1000
	Byte RX:11293100 (11.2 MB) Byte TX:1386149 (1.3 MB)
	Interrupt:16

lo Link encap:Loopback locale
	inet addr:127.0.0.1 Mask:255.0.0.0
	inet6 addr: ::1/128 Scope:Host
	UP LOOPBACK RUNNING MTU:16436 Metric:1
	RX packets:168 errors:0 dropped:0 overruns:0 frame:0
	TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
	collisioni:0 txqueuelen:0
	Byte RX:8400 (8.4 KB) Byte TX:8400 (8.4 KB)

ppp0 Link encap:Point-to-Point Protocol
	inet addr:192.168.10.39 P-t-P:192.168.10.2 Mask:255.255.255.255
	UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1400 Metric:1
	RX packets:13 errors:0 dropped:0 overruns:0 frame:0
	TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
	collisioni:0 txqueuelen:3
	Byte RX:258 (258.0 B) Byte TX:112 (112.0 B)

```	

The command route before to connect on VPN

```

Kernel IP routing table 
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.1.0 * 255.255.255.0 U 1 0 0 eth0 
link-local * 255.255.0.0 U 1000 0 0 eth0 
default . 0.0.0.0 UG 0 0 0 eth0 

```

The command route after to connect on VPN

```

Kernel IP routing table 
Destination Gateway Genmask Flags Metric Ref Use Iface 
69.65.42.32 . 255.255.255.255 UGH 0 0 0 eth0 
192.168.10.2 * 255.255.255.255 UH 0 0 0 ppp0 
192.168.1.0 * 255.255.255.0 U 1 0 0 eth0 
link-local * 255.255.0.0 U 1000 0 0 eth0 
default . 0.0.0.0 UG 0 0 0 eth0 

```

Please Help Me![/QUOTE]

---

