---
title: "d-link adsl router"
date: 2005-06-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by lgl on 2005-06-19
Hi,
   I have just bought a d-link adsl route so that my two machines can share my internet connection. I bought d-link dsl604t kit that included a wireless usb stick and cradle. I have set it all up and mostly works.

Windows machine has the stick to wirelessly connect to the router and works fine.
ubuntu machine has an ethernet connection to the router and is connected but will not connect to the Internet. I know it is connected because I can ping it and get on its configuration web page. When I try to use mozilla to go on the net I get can't find errors. 

Could someone tell me how to set up Ubuntu to properly connect through this router.

Thanks lg

---

### Post by skylark on 2005-06-21
Hi

I dont have your modem but I think this might work:

On your Ubuntu machine, look at /etc/network/interfaces
Under the section: "# The primary network interface" make sure there is a line at the bottom like "gateway <ip address of your router>" where <ip address of your router> is something like 192.168.0.xx.
Also look at /etc/network/options. It should contain the followind 3 lines:
ip_forward=no
spoofprotect=yes
syncookies=no

---

### Post by lgl on 2005-06-21
Have got it to work now by interfaces looking like:
   iface eth0 inet dhcp

and thats it. It seems to be running slow and has been giving me timeout errors. Would the gateway line help this. I am going to go to my provider and find out as many settings as I can and see if any of them need tweaking.

Thanks Leon

---

### Post by lgl on 2005-06-24
wasn't router it was Firefox.

[http://forums.mozillazine.org/viewtopic.php?t=258042](http://forums.mozillazine.org/viewtopic.php?t=258042) for the answer

---

