---
title: "Samba died. Desperate!"
date: 2006-07-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-07-15
I have two computers: A Windows 2000 desktop (192.168.1.100) and a Linux laptop (192.168.1.101). The last time I used file sharing was about a week ago. Everything worked as usual. Today, neither can even ping the other. As far as I can tell, samba died. I have fiddled for the past couple of hours, but no joy. I can open Nautilus and go to Network Servers and it shows "Windows Network." But when I click on "Windows Network" I get nothing. Previously it showed all the shares I had created on the Windows desktop. Now, nothing.

The GUI is not helping. I need some command line things to troubleshoot this. Unfortunately, I am relatively new to Linux, plus I have never known anything about how networking functions.

---

### Post by Sonofmoog on 2006-07-15
Before anyone can troubleshoot your problem, we need more information:

1) Run ifconfig and post the output here ..
2) The IP's assigned to your two machines by DHCP or static?
3) Do you use a router, and if so, have you tried to access it via IP?    Your IP address will be in your documentation.  Open Firefox and type the IP, and see if you can connect ..
4) Open a console and type testparm to see if your smb.conf is loaded without errors ..
5) If you have firewalls on both boxes, you need to check them for access.  In Windows, be sure it says "Windows firewall is configured to allow sharing this folder over the network"
6) You've tried accessing the Windows box from Ubuntu; what do you see when you try to access the Ubuntu box from My Network Places?
7) Try nmblookup <Windows PC name> substituting the name of your Windows PC, and report back
8- Do the obvious:  make sure everything is plugged in and turned on ..
9) Go to System, Administration, Services and make sure samba is running ..

---

### Post by John Jason Jordan on 2006-07-16
> **Sonofmoog said:**
> Before anyone can troubleshoot your problem, we need more information:

1) Run ifconfig and post the output here ..
2) The IP's assigned to your two machines by DHCP or static?
3) Do you use a router, and if so, have you tried to access it via IP?    Your IP address will be in your documentation.  Open Firefox and type the IP, and see if you can connect ..
4) Open a console and type testparm to see if your smb.conf is loaded without errors ..
5) If you have firewalls on both boxes, you need to check them for access.  In Windows, be sure it says "Windows firewall is configured to allow sharing this folder over the network"
6) You've tried accessing the Windows box from Ubuntu; what do you see when you try to access the Ubuntu box from My Network Places?
7) Try nmblookup <Windows PC name> substituting the name of your Windows PC, and report back
8- Do the obvious:  make sure everything is plugged in and turned on ..
9) Go to System, Administration, Services and make sure samba is running ..
OK, first, here is the output from ifconfig:

jjj@Devil5:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:03:03:86
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe03:386/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:75655 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:102486709 (97.7 MiB)  TX bytes:2915698 (2.7 MiB)
          Interrupt:185 Base address:0x6800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14041 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:608500 (594.2 KiB)  TX bytes:608500 (594.2 KiB)
jjj@Devil5:~$

Normally there would also be a wireless as eth1, but it does not activate at home because I don't have wifi here. I just use ethernet, which goes to the switch, router, and cable modem. I'm writing this on the Linux computer (a laptop), and throughout this time I have had no problem going to the internet.

I don't know where the documentation for the router is, but as I recall I changed its IP address when I was installing it, so the documentation wouldn't help. Unfortunately, I don't recall what I set it to. I can, however, ping the DNS servers for Comcast.

Here are the results from testparm:

jjj@Devil5:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
jjj@Devil5:~$

The Ubuntu computer has firestarter, and it is just as it was when I installed Dapper (a fresh, clean install on a new partition). The Windows computer has Sygate, which hasn't been changed in ages. I am sure it is not the firewall on the Windows computer. 

If I go to Places > Network Server I get a window showing Windows Network. It says everything about Windows Network is "unknown" -- no owner, permissions, etc. If I click on Windows Network I get a blank windows. (Previously clicking on Windows Network displayed the shares on the Windows computer.)

Nmblookup gives me:

jjj@Devil5:~$ nmblookup Devil4
querying Devil4 on 192.168.1.255
name_query failed to find name Devil4
jjj@Devil5:~$

The Linux laptop is Devil5; the Windows desktop is Devil4.

Your last suggestion revealed something very interesting. In System > Administration > Services Samba was listed, but the checkbox in front of it was not checked. I checked it and then on OK. Unfortunately, that didn't help. Still not able to see the shares on the Windows computer.

It might have become unchecked when I (earlier) uninstalled and reinstalled Samba. And when I reinstalled I get an error message:

"E: /var/cache/apt/Archives/Samba_3.0.22-1Ubuntu3.1_amd64.deb:
subprocess new pre-removal script returned error exit status 102"

This error message occurred at the command line after "sudo apt-get remove samba" and "sudo apt-get install samba." I don't know what the error message means, but evidently there is something wrong with Samba.

Thanks for your suggestions -- all good ideas. Hopefully the results will reveal what the problem is.

---

### Post by Sonofmoog on 2006-07-16
As I read what you've seen, it appears to me that your network is up and running.  Your problem is that the samba daemon does not appear to be starting at boot.  There is a command line script I ran when loading Samba, but I no longer recall what that was.  I did, however, find some very good information here:

[http://www.ubuntuforums.org/archive/index.php/t-19280.html](http://www.ubuntuforums.org/archive/index.php/t-19280.html)

Here is the command to start the daemon:

```
sudo /etc/init.d/samba start
```

HTH

---

### Post by Kulgan on 2006-07-16
I had problems with samba right from the start, during updates for some strange reason. Like system updates, or updating and installing packages in Synaptic. It reads 
"E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb: subprocess new pre-removal script returned error exit status 102", then I would get a message telling me that not all updates had been applied. I didn't think much about it, untill I came home today, got the update notice, and find out that the software index is broken...  I have no idea how that relates to a lan-manager!

When I open synaptic it says that I have a broken package - samba. The system updater, which is the one that insists that the software index is messed up, tells me to update via synaptic or run "sudo apt-get install -f" - which also gives an error after I accept the changes.

Are our cases related?

-K

---

### Post by John Jason Jordan on 2006-07-16
> **Kulgan said:**
> Are our cases related?
I don't know if they are related, but I do know that if you go into Synaptic and uninstall samba using the "uninstall configurations as well" option, then reinstall it, it will eliminate that error message.

I accomplished that, but still could not see the Windows computer. However, since then I discovered that the latest Update installed a new kernel option, but Grub still listed only the original two. In other words, I had three kernel options, but was not booting into the latest one.

I am not at home, but when I get there I am going to try again. I'm also going to install a plain installation in an unused partition, apply all updates to it, and see if it works.

---

### Post by John Jason Jordan on 2006-07-16
> **John Jason Jordan said:**
> I am not at home, but when I get there I am going to try again. I'm also going to install a plain installation in an unused partition, apply all updates to it, and see if it works.
OK, back at home. The new, fresh installation of Dapper-64 into an new partition is able to see the Windows desktop just fine. I installed all the upgrades to it so it would match my main installation, and it still has no problem seeing the files on the Windows desktop.

Rebooted to the main installation of Dapper-64 and started poking around at stuff. I noticed in System > Administration > Firestarter that I had not tried looking at Firestarter. I clicked on it, a window popped up, and there was a big button to disable Firestarter. I did so. And then I opened Nautilus and told it to go to Network Servers. It found the Windows desktop and had no problem seeing all the files on it. Yay!

So after all this screwing around the problem was Firestarter the whole time. To fix it I went into Firestarter > Policy tab and added the IP address of the Windows desktop as an address to allow incoming data from. Firestarter is now happily running and I can still get files to and from the Windows desktop. Problem resolved!

---

### Post by Kulgan on 2006-07-17
Tricky little bugger, had to be something simple, didn't it... 

> go into Synaptic and uninstall samba using the "uninstall configurations as well" option, then reinstall it, it will eliminate that error message.

Tried that, but it is the samba package itself that is "damaged". wondering if I shouldn't just reinstall ubuntu?
The thing is that it was always like that (I used a v5 CD, then upgraded). It would be nice to avoid doing that, however. Any ideas?

---

### Post by Kulgan on 2006-07-17
actually, forget that, fixed it .

---

### Post by Sonofmoog on 2006-07-17
](*,)

---

