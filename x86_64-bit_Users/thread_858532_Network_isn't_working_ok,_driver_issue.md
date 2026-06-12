---
title: "Network isn't working ok, driver issue ?"
date: 2008-07-13
forum: x86 64-bit Users
---

### Post by pikul on 2008-07-13
Hey guys, im starting to get sad, my internet conexion its not working at its fullest, max donwload speed its supossed to be 30 - 32 kbps, on vista i always get it like this, i dont know why its not working in ubuntu, is really weird cause when a download starts it goes 30 kbps but after maybe 15 or 20 seconds it goes down to 20 - 21, i know its not much but thats not the only problem i have, pages take to long to load, i was thinking it could be a driver issue cause this also happends to me on Fedora 8 and 9 :confused: i tried X86 and X86_64 versions, if so its there a way to install the driver a have on windows??? maybe like people does with wireless :confused: heres a little info you may want to know:

Ethernet conexion
02:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

I did try with a lot of download servers, and with a lot of pages, on windows they all download at full speed :lolflag: 

I found this on /var/log/messages

```
Jul 13 14:04:12 Pikuls-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 13 14:04:14 Pikuls-desktop kernel: [   61.854138] NET: Registered protocol family 17
Jul 13 14:04:18 Pikuls-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul 13 14:04:18 Pikuls-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 13 14:04:18 Pikuls-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 13 14:04:18 Pikuls-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jul 13 14:04:19 Pikuls-desktop kernel: [   67.142623] NET: Registered protocol family 10
Jul 13 14:04:19 Pikuls-desktop kernel: [   67.142920] lo: Disabled Privacy Extensions
Jul 13 14:24:09 Pikuls-desktop -- MARK --
Jul 13 14:44:09 Pikuls-desktop -- MARK --
```

and this on /var/log/user.log

```
Jul 13 14:04:09 Pikuls-desktop dhcdbd: Started up.
Jul 13 14:04:12 Pikuls-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 13 14:04:18 Pikuls-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul 13 14:04:18 Pikuls-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 13 14:04:18 Pikuls-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 13 14:04:18 Pikuls-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
```

I dont know what it means :(  thanks :KS

---

### Post by pikul on 2008-07-14
Nobody ???? :(

---

