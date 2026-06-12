---
title: "Installing and Configuring MOL Killed My Internet."
date: 2006-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by AlphaMack on 2006-04-24
I installed and configured MOL according to this Wiki entry:
[https://wiki.ubuntu.com/MacOnLinuxHowtoDapper?highlight=%28on%29%7C%28Mac%29%7C%28Linux%29](https://wiki.ubuntu.com/MacOnLinuxHowtoDapper?highlight=%28on%29%7C%28Mac%29%7C%28Linux%29)

Please help me get my connection back.  I suspect it has something to do with dhcpd and /etc/default/dhcp.

The punchline?  I can connect just fine in MOL.  Just not on the rest of the machine (i.e. Ubuntu).  Something is hijacking the connection until MOL starts up.


Where do I go to troubleshoot?  I've spent enough time on this.

---

### Post by AlphaMack on 2006-04-25
Answer was under my nose the entire time without me realizing it.

Firestarter was the culprit.


Even though FS was still automagically starting up, prior to installing MOL and dhcpd etc. it was still working.  So something has changed the FS needs to let through.

---

### Post by AlphaMack on 2006-04-27
I know I'm talking to myself in this thread, but a followup.

I just gave up.  Uninstalled MOL, dhcpd, dnsmasq, and ipmasq...

And whattayaknow?  Everything is back to normal again.  I'm immediately online upon booting and logging in again.

One of those up above is responsible for two days of hair pulling and agonizing.  My bet is on dhcpd.

---

### Post by AlphaMack on 2006-04-28
Solved.  For now.

At a slight cost of security:

$ sudo dpkg-statoverride --update --add root root 4755 /etc/init.d/ipmasq
$ sudo dpkg-statoverride --update --add root root 4755 /etc/ipmasq
$ sudo dpkg-statoverride --update --add root root 4755 /sbin/iptables

Then add '/etc/init.d/ipmasq restart' to my list of startup items in my Sessions control panel.

I now have connectivity for both Ubuntu and MOL.

Anyone with a better idea than this? Of course, I can always undo root access.

---

### Post by Entity on 2006-04-28
Hi, I don't use Firestarter, but I know that after installing MOL and configuring the network to let MOL access the internet just like explained on the Wiki. I was unable to ping anything upon reboot (wireless connection).

In order to solve this problem I simply disabled the dhcpd, dnsmasq and ipmasq on system startup.

sudo update-rc.d -f dnsmasq remove
sudo update-rc.d -f ipmasq remove
sudo update-rc.d -f dhcpd remove *(maybe it's dhcp and not dhcpd)*

So now these services only start when MOL are started. Hope it helps.

---

