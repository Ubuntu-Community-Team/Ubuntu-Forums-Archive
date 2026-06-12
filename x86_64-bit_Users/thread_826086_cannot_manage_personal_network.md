---
title: "cannot manage personal network"
date: 2008-06-11
forum: x86 64-bit Users
---

### Post by raven on 2008-06-11
I have a home network
specification starting from the DSL modem:


DSL modem 
ISP IP connected to 1st
<router>192.168.1.101>---wireless---<192.168.1.101<client router> gateway 192.168.2.200 connected to linux box

my issue is
I have 2 hard disks one it is installed gutsy and the other hardy amd64 on both

if I want to boot gutsy I just plug the gutsy hard drive
if I want to boot hardy I just plug the hardy hard drive
it is not a dual boot, I physically unplug the hard drives

with gutsy I use to put the IP address in FF of the first router (192.168.1.1) and I used to be able to manage the router,

with hardy it tells me that page cannot be displayed

I unplug the hardy hard drive and plug gutsy I can mange the first router (192.168.1.1)

why with hardy I cannot manage the first router ?

when both OS's are setup the same thing (same IP, same MAC, and almost the same packages

---

### Post by Kilz on 2008-06-12
> **raven said:**
> I have a home network
specification starting from the DSL modem:


DSL modem 
ISP IP connected to 1st
<router>192.168.1.101>---wireless---<192.168.1.101<client router> gateway 192.168.2.200 connected to linux box

my issue is
I have 2 hard disks one it is installed gutsy and the other hardy amd64 on both

if I want to boot gutsy I just plug the gutsy hard drive
if I want to boot hardy I just plug the hardy hard drive
it is not a dual boot, I physically unplug the hard drives

with gutsy I use to put the IP address in FF of the first router (192.168.1.1) and I used to be able to manage the router,

with hardy it tells me that page cannot be displayed

I unplug the hardy hard drive and plug gutsy I can mange the first router (192.168.1.1)

why with hardy I cannot manage the first router ?

when both OS's are setup the same thing (same IP, same MAC, and almost the same packages

Do you have an internet connection in the hardy install? Can you visit this post in its browser?

---

### Post by raven on 2008-06-12
yes, I have internet from both OS's
I'm writing this from hardy

I can even ping my first router 192.168.1.1 and the second router 192.168.2.200
from hardy and gutsy

but if I want to access my router 192.168.1.1 it say this page cannot be displayed
only in hardy ???

---

### Post by Kilz on 2008-06-12
> **raven said:**
> yes, I have internet from both OS's
I'm writing this from hardy

I can even ping my first router 192.168.1.1 and the second router 192.168.2.200
from hardy and gutsy

but if I want to access my router 192.168.1.1 it say this page cannot be displayed
only in hardy ???

You might want to try and disable ipv6 in firefox. Type ```
about:config
``` into the address bar, click ok il be careful, I promise. Type ipv6 in the filter. network.dns.disableIPv6 should show, right click on it and toggle it to true, then restart firefox.

---

### Post by raven on 2008-06-12
I did what you said for the IPV6, but it did not work
same results I get this error:

"Failed to Connect
Firefox can't establish a connection to the server at 192.168.1.1.       

Though the site seems valid, the browser was unable to establish a connection.

    * Could the site be temporarily unavailable? Try again later.
    * Are you unable to browse other sites?  Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browser"


I disabled the firewall before (with firestarter)  but same results

PS: I tried with opera browser just to be sure that it's not FF or any of the addons, sadly I get the same results

---

### Post by raven on 2008-06-14
anybody want to take a crack at this mystery ?

---

### Post by raven on 2008-06-17
I need the help of this community
anybody want to take a shot at this problem

with gutsy I can connect to my home router linksys wrt45g 192.168.1.1
with hardy I cannot connect
even when I'm booting with the same PC (I swap the hard disk)

---

### Post by raven on 2008-06-20
Solved :razz:

---

### Post by cariboo on 2008-06-20
Could you document what you did here to help other users.

Jim

---

### Post by raven on 2008-06-27
cariboo, I did not do anything,
it was fixed with the latest official update a week ago or so
one of the packages fixed the issue (I presume)

this issue even affected my vmware setup, I could not remote to other windows on my network, which are on a different subnets,
now I can remote from 192.168.2.x/24 to 192.168.1.x/24
and manage my routers on differents subnets

---

