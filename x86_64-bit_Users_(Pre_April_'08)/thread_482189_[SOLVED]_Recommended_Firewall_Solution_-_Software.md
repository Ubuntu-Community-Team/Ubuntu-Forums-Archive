---
title: "[SOLVED] Recommended Firewall Solution - Software"
date: 2007-06-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-06-23
Does anyone have any suggestions for a software firewall.  I'm running behind a router with it's internal firewall enabled but I would like a software fire wall as well (GUI).

Thanks...

---

### Post by nike984 on 2007-06-23
[http://ubuntuforums.org/showthread.php?t=159661&highlight=7z+incorrect+command+line](http://ubuntuforums.org/showthread.php?t=159661&highlight=7z+incorrect+command+line)

It's not GUI, but you have the advantage to setup your own firewall by youself,
and you can have whatever function you want.

---

### Post by darknightuk on 2007-06-23
try this [http://www.fs-security.com/](http://www.fs-security.com/)

---

### Post by jamesford on 2007-06-23
firestarter is probably what u want but ive found it totally useless. in any case u got a built in invisible firewall called iptables. it does the job

---

### Post by Cappy on 2007-06-23
Actually, firestarter is a gui for iptables. It makes it very easy to allow specific ports to open when you need it =)
If you don't actually need to host anything, I would just leave it alone since iptables is enabled by default =)

Software firewalls are a good idea though ... routers aren't firewalls, an actual hacker can get by them. They do stop worms/pings/script kiddies though which is 99.9% of home annoyances.

---

### Post by crjackson on 2007-06-23
> **Cappy said:**
> Actually, firestarter is a gui for iptables. It makes it very easy to allow specific ports to open when you need it =)
If you don't actually need to host anything, I would just leave it alone since iptables is enabled by default =)

Software firewalls are a good idea though ... routers aren't firewalls, an actual hacker can get by them. They do stop worms/pings/script kiddies though which is 99.9% of home annoyances.

Okay, so if I'm understanding this correctly, I basically already have a firewall running by default and I only need to tinker with it to open a port (say for my ftp server?).  Did I get this right?  

And to make adjustments using a GUI front end, just install firestarter?

---

### Post by jamesford on 2007-06-23
that is spot on

---

### Post by crjackson on 2007-06-23
EXCELLENT! I was already protected and didn't even know it...:D

---

### Post by jamesford on 2007-06-23
u can always test ur firewall for example here [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by crjackson on 2007-06-23
> **jamesford said:**
> u can always test ur firewall for example here [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Great thanks.  I'll do that this weekend.

---

### Post by crjackson on 2007-06-23
> **jamesford said:**
> u can always test ur firewall for example here [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Okay, so it says I faild stealth because of port 113 is closed.  Do I need to fix this?

---

### Post by Mr_bleu on 2007-06-23
Are you running a router?  If so you can forward the port.  [http://www.firewallreporting.com/linksysalert.htm](http://www.firewallreporting.com/linksysalert.htm)
I have a dlink.  You can google port 113 and find a bunch of info.  I've had mine stealthed for 2 yrs in windows, can't get this thing stealthed completely in linux.  My laptop's responding to ping requests but all ports are stealthed.

---

### Post by crjackson on 2007-06-23
> **Mr_bleu said:**
> Are you running a router?  If so you can forward the port.  [http://www.firewallreporting.com/linksysalert.htm](http://www.firewallreporting.com/linksysalert.htm)
I have a dlink.  You can google port 113 and find a bunch of info.  I've had mine stealthed for 2 yrs in windows, can't get this thing stealthed completely in linux.  My laptop's responding to ping requests but all ports are stealthed.

Actually my Linksys just died a few days ago and I got a cheap Buffalo router.  The setup interface sucks and it's hard to do anything with it.  I wish I had just bought another Linksys.  It'll take me 2 days to figure that out.  I'll have to wait until I have a day off and some Gin to fight with this thing.

You wouldn't believe how hard it was just getting the Wired connection to work on this thing.  The only good thing I can say so far is that it has a good strong wireless signal that never drops any of my laptops.  The Linksys ALWAYS dropped the laptops and sometimes the desk tops several times a day...

---

### Post by penguin007 on 2007-06-25
This script will drop all unsolicited incoming packets but allow outgoing traffic to innitiate connections. Note you must run it as root (i.e. sudo)

Air tight for home users on a single PC.


# Check that user is root
if [ "`whoami`" != "root" ]; then
   echo
   echo "** Error **"
   echo "You need to be 'root'"
   echo
exit
fi
iptables --flush
iptables --flush -t nat
iptables --policy INPUT DROP
iptables --policy OUTPUT DROP
iptables --policy FORWARD DROP
iptables -A OUTPUT -j ACCEPT -o lo
iptables -A INPUT -j ACCEPT -i lo
iptables -A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

---

### Post by fakie_flip on 2007-06-25
The firewall is there by default but not configured to block anything. If you want to configure easily, you can use firestarter.

---

### Post by Corbelius on 2007-06-25
[http://www.shorewall.net/](http://www.shorewall.net/)

---

### Post by moore.bryan on 2007-06-25
*i can't find one better than pectol's [ubuntu-firewall]("http://rob.pectol.com/content/view/2/1/")...*

---

### Post by crjackson on 2007-06-25
Okay thanks - I'll look at all of them.

---

### Post by crjackson on 2007-06-25
> **fakie_flip said:**
> The firewall is there by default but not configured to block anything. If you want to configure easily, you can use firestarter.

Does firestarter have to be launched for it to be actively protecting?  In other words, when I exit out of firestarter, did I just lose my firewall configuration?  Should it be running minimized all the time to protect my system?

---

### Post by fakie_flip on 2007-06-25
> **crjackson said:**
> Does firestarter have to be launched for it to be actively protecting?  In other words, when I exit out of firestarter, did I just lose my firewall configuration?  Should it be running minimized all the time to protect my system?

I'm pretty sure it does not have to be open all the time for it to be working because there is a firestarter service that starts up when your computer starts up.

close firestarter and do this command. you will see that the the firestarter service is still running.

ps -ef | grep firestarter

if you want to make sure it is protecting your computer when its not open, then go to a different computer and scan your ip with nmap.

sudo apt-get install nmap

sudo nmap 192.168.1.100

replace that ip with the ip of your computer on the lan. try uninstalling firestarter and then scanning your computer from a different computer on the lan. now you should see lots of stuff opened. that shows that firestarter is working.

---

