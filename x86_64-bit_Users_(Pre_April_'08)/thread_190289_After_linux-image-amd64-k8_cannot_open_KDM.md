---
title: "After linux-image-amd64-k8 cannot open KDM"
date: 2006-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by CyberAngel on 2006-06-06
Hi, After I am installing the specific for my processor kernel (linux-image-amd64-k8 ) the system loads and it hangs just before kdm loads up. I can login normally to the terminals (tty1-tty6) at this point but It can`t open the X!!

My last 20 lineson syslog are the following:
```
Jun  6 10:16:41 aurora kernel: [   58.942812] Bridge firewalling registered
Jun  6 10:16:41 aurora kernel: [   58.947884] eth0: Promiscuous mode enabled.
Jun  6 10:16:41 aurora kernel: [   58.948064] device eth0 entered promiscuous mode
Jun  6 10:16:41 aurora kernel: [   58.948891] bridge: can't decode speed from eth1: 65535
Jun  6 10:16:41 aurora kernel: [   58.948986] device eth1 entered promiscuous mode
Jun  6 10:16:41 aurora kernel: [   58.950099] br0: port 1(eth0) entering learning state
Jun  6 10:16:41 aurora anacron[4874]: Anacron 2.3 started on 2006-06-06
Jun  6 10:16:41 aurora anacron[4874]: Normal exit (0 jobs run)
Jun  6 10:16:41 aurora /usr/sbin/cron[4899]: (CRON) INFO (pidfile fd = 3)
Jun  6 10:16:41 aurora /usr/sbin/cron[4900]: (CRON) STARTUP (fork ok)
Jun  6 10:16:41 aurora /usr/sbin/cron[4900]: (CRON) INFO (Running @reboot jobs)
Jun  6 10:16:45 aurora kdm: :0[5343]: IO Error in XOpenDisplay
Jun  6 10:16:45 aurora kdm[5274]: X server for display :0 terminated unexpectedly
Jun  6 10:16:45 aurora kdm[5274]: Display :0 cannot be opened
Jun  6 10:16:45 aurora kdm[5274]: Unable to fire up local display :0; disabling.
Jun  6 10:16:51 aurora kernel: [   66.624495] eth0: no IPv6 routers present
Jun  6 10:16:51 aurora kernel: [   66.710388] br0: no IPv6 routers present
Jun  6 10:16:56 aurora kernel: [   68.848196] br0: topology change detected, propagating
Jun  6 10:16:56 aurora kernel: [   68.848199] br0: port 1(eth0) entering forwarding state
Jun  6 10:17:01 aurora /USR/SBIN/CRON[5372]: (root) CMD (   run-parts --report /etc/cron.hourly)

```

As you can see it has some errors about kdm.

What might be wrong???
With the linux-image-amd64-generic kernel, the system is funtioning properly (Now I am posting from the same machine with the problem)

---

### Post by RAOF on 2006-06-06
I would guess the following:
1) You have installed the **nvidia-glx** package, and are using the nVidia drivers.
2) You installed the **linux-image-2.6.15-23-amd64-k8** package.
3) You *didn't* install the **linux-restricted-modules-2.6.15-23-amd64-k8** package.

The solution is to install the **linux-amd64-k8** package.  This installs the latest -k8 kernel, **and** the associated -restricted-modules.

The reason why you don't have X would be that the nVidia graphics driver relies on a kernel module found in the -restricted-modules package.  When you get the new image without the new -restricted-modules, the nVidia driver can't load.

---

### Post by CyberAngel on 2006-06-06
OK that was the problem :)
I had not installed the restricted modules. Now everything it`s OK.

Thanks!

BTW how did you guessed about nvidia-glx?? :)

---

### Post by jdong on 2006-06-06
[QUOTE=CyberAngel]OK that was the problem :)
I had not installed the restricted modules. Now everything it`s OK.

Thanks!

BTW how did you guessed about nvidia-glx?? :)[/QUOTE]

Look down at your signature.

BTW, when installing the kernel, install the linux metapackage, not the linux-image metapackage, and you won't run into this problem (linux-amd64-k8), as the linux metapackage pulls in restricted modules and other kernel dependencies.

---

### Post by McHenry on 2006-10-09
I have a similar message being logged in /var/log/messages however I am not running an amd processor. As your solution relates to a kernel upg maybe the following will be relevent.

root@declan:/etc/postfix# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-server
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@declan:/etc/postfix#

The original message logged in /var/log/messages is:
Oct 7 13:24:29 declan kernel: [42949388.140000] Bridge firewalling registered
Oct 7 13:24:29 declan kernel: [42949388.150000] bridge: can't decode speed from eth0: 65535
Oct 7 13:24:29 declan kernel: [42949388.150000] device eth0 entered promiscuous mode
Oct 7 13:24:29 declan kernel: [42949388.150000] device tap0 entered promiscuous mode
Oct 7 13:24:29 declan kernel: [42949388.200000] br0: port 2(tap0) entering learning state
Oct 7 13:24:29 declan kernel: [42949389.500000] tg3: eth0: Link is up at 100 Mbps, full duplex.
Oct 7 13:24:29 declan kernel: [42949389.500000] tg3: eth0: Flow control is on for TX and on for RX.
Oct 7 13:24:29 declan kernel: [42949389.500000] br0: port 1(eth0) entering learning state
Oct 7 13:24:29 declan kernel: [42949403.200000] br0: topology change detected, propagating
Oct 7 13:24:29 declan kernel: [42949403.200000] br0: port 2(tap0) entering forwarding state
Oct 7 13:24:29 declan kernel: [42949404.500000] br0: topology change detected, propagating
Oct 7 13:24:29 declan kernel: [42949404.500000] br0: port 1(eth0) entering forwarding state
Oct 7 13:24:29 declan kernel: [42949405.850000] NET: Registered protocol family 10
Oct 7 13:24:29 declan kernel: [42949405.850000] lo: Disabled Privacy Extensions
Oct 7 13:24:29 declan kernel: [42949405.850000] IPv6 over IPv4 tunneling driver

Thanks...

---

### Post by jdong on 2006-10-09
The server kernel does not come with many of the restricted modules, as it was not designed for server use. Your /var/log/messages output has nothing to do with the OP's circumstances.. yours just shows a bridge interface being constructed.

---

### Post by McHenry on 2006-10-09
Ok, so the following simply indicate the bridge being constructed and are not an error to worry about ?

Oct 7 13:24:29 declan kernel: [42949388.150000] bridge: can't decode speed from eth0: 65535
Oct 7 13:24:29 declan kernel: [42949388.150000] device eth0 entered promiscuous mode
Oct 7 13:24:29 declan kernel: [42949388.150000] device tap0 entered promiscuous mode

Thanks

---

### Post by jdong on 2006-10-09
Unless you are having some kind of networking difficulty, I would not lose any sleep over those messages :)

---

### Post by McHenry on 2006-10-10
I'm not experiencing any problems however would you advise if they are normal messages or an indication of somethng that, although may not be causing any problems I am aware of, is not 100% ?

Thanks

---

### Post by jdong on 2006-10-10
They're likely normal.

---

