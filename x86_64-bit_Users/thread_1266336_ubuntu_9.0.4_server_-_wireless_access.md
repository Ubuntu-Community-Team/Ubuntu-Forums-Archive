---
title: "ubuntu 9.0.4 server - wireless access"
date: 2009-09-14
forum: x86 64-bit Users
---

### Post by jim001 on 2009-09-14
Hi

I am trying to use wireless connection on ununtu 9.0.4 server (no GUI tools). It fails consistently. It works fine from Vista though. I tried to resolve this issue with kernel build 2.6.31 and it still fails. 

Here is normal steps of commands I run from console. 

$ sudo ifconfig wlan0 up/down
$ sudo iwconfig wlan0 essid linksys
$ sudo dhclient wlan0

Attached files contain logs. Please help me resolve this issue(stuck with this issue for 2 days. 

Thanks
Jim

---

### Post by Bachstelze on 2009-09-14
Isn't your network encrypted?

---

### Post by jim001 on 2009-09-14
No - if you look at scan log, it says "encryption off"

---

### Post by theZoid on 2009-09-14
I would install Ceni and use that to connect...it's available for Debian.

---

### Post by jim001 on 2009-09-14
ok - let me check out ceni.

I get the following errors while running sudo dhclient wlan0

[  277.662296] wlan0: direct probe to AP 00:1c:10:32:94:61 try 1
[  277.860083] wlan0: direct probe to AP 00:1c:10:32:94:61 try 2
[  278.060049] wlan0: direct probe to AP 00:1c:10:32:94:61 try 3
[  278.260046] wlan0: direct probe to AP 00:1c:10:32:94:61 timed out

Can anyone tell me what's problem?

thanks
jim

---

### Post by x22 on 2009-09-15
here's what I use (in rc.local)

ifconfig wlan0 up
iwconfig wlan0 essid 2236_bg
iwconfig wlan0 channel 11
iwconfig wlan0 mode managed
#iwconfig wlan0 key 1234567890
#iwconfig wlan0 key open
dhclient wlan0 2>&1>/dev/null

substitute your values

---

### Post by jim001 on 2009-09-16
I am able to access wireless from one public location. However I get this time out errors from another location(a totally different access point and router).

All I get is "link not ready and direct probe to AP: timed out" errors - I need to go in deep and why is this error comping up especially when Vista works without any issue on the same access point. 

Vista must be doing something special which ubuntu does not do - I thought linux is powerful in terms of dealing with this issues from debug perspective

Is there any way to debug this on ubuntu?

thanks

---

