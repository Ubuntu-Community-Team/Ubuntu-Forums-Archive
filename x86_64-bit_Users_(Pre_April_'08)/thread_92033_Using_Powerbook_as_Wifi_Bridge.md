---
title: "Using Powerbook as Wifi Bridge"
date: 2005-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by tsd_arc on 2005-11-18
Hey,

I'm planning to use a old Celeron (333Mhz) box as a server for different things. Since my network sitiuation is kinda weird, I have to use my PowerBook (10.4.3, Airport) as a Wifi Bridge for connecting the ubuntu box to my AirPort Express Station. I've alredy enabled internet sharing (AirPort -> Internal Ethernet) in the system preferences, but got no clue how to go on. The ethernet connection (direct, via crossover cable) between the box and the PowerBook works fine. I'm able to share files via samba, and control the box via vnc.

thanks, arc

---

### Post by matthew on 2005-11-18
Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=76346](http://ubuntuforums.org/showthread.php?t=76346)

It isn't an identical situation, but it's pretty close. I think it will give you what you need, or at the very least give you enough info to know what to try next.

---

### Post by tsd_arc on 2005-11-18
Well... I alredy did. But I couldnt find a file like /etc/resolv.conf on my powerbook, so I thought it's the wrong way.

---

### Post by matthew on 2005-11-18
Are you currently able to connect to the internet (i.e. with your web browser) from the Powerbook?

---

### Post by tsd_arc on 2005-11-18
Yeah. I'm writing this on it.

---

### Post by matthew on 2005-11-18
Huh...are you using DHCP or a static IP?

---

### Post by tsd_arc on 2005-11-18
The wifi connection PowerBook -> AirPort Express uses DHCP, the ethernet connection PowerBook -> ubuntubox static IP.

---

### Post by matthew on 2005-11-18
Okay. What we need to do is figure out where the information that is usually in /etc/resolv.conf is being stored on your computer. I've never seen it put anywhere else so I'm not entirely sure where to look. My first instinct is that it should be in a file in the /etc directory. If you have a few minutes take a look in that directory at the various files there and see if maybe it has a different name (again, I've never seen this, but who knows?). 

I noticed you are in Hamburg--perhaps you installed in German? I find it hard to believe that would make any difference, though. By the way, I've been to the fish market there in Hamburg and had a great time.

Meanwhile I will do some digging and try to figure out another way to find the information.

---

### Post by tsd_arc on 2005-11-18
hah, I found it. It was in /private/var/run ... but theres only one line in it:
```

nameserver 10.0.1.1

```
That is the ip of the airport express station, i think. So what to do now?

big thanks, btw. ;D

---

### Post by matthew on 2005-11-18
It's okay that there's only one line...the one that is there has the information we need.

Judging from how you referred to the how-to I wrote I'm guessing you probably made it up to step 4 earlier. If that is true all you should need to do is create a file on the old Celeron computer called /etc/resolv.conf with this as its contents:
```
 nameserver 10.0.1.1
``` Look through the howto again and double check all the steps as needed.

If for some reason you can't get it running post a follow-up here.

Oh! I thought of another place to look for the nameserver information if what you found doesn't work. I have no expreiece with Apple stuff, but I presume you can connect to the router and change/explore its settings. Somewhere in there it should have a listing of DNS settings it is using.

EDIT: one more place I found on my computer. /var/run/dhclient.x.leases (where x corresponds to your primary ethernet interface, in my case eth1). You have to read through that file a bit to find what you want, though.

---

### Post by tsd_arc on 2005-11-18
Hm, i cannot try it out now.. its a bit late here in germany (~ 23:30), and the server is located in another apartment. I'm too tired to go there now. I'll try it out tomorrow.

/var/run/dhclient.x.leases doesn't exist. 

I've found this in the Airport Management Utility:

---

### Post by matthew on 2005-11-18
Get some rest. When you are back you will find some good news.

The information we needed was in your attached image where it says "Current Primary DNS Server" and "Current Secondary DNS Server."

When you make the /etc/resolv.conf on the Celeron desktop use this as its contents:
```
nameserver 213.191.74.11
nameserver 213.191.92.82
```
That should get you up and running.

---

### Post by tsd_arc on 2005-11-19
Damn. It doesnt work. When I try to open google in firefox, it says "looking up google.com" instead of "google.com cannot be found" but nothing else happens. Maybe I have to add a search server in the resolv.conf, like in the how-to? (If so, how can I find it out?)

thanks anyway.

Edit: Ah, after about 15min firefox aborts with the "google.com cannot be found" message.

Shall I post screenshots of my whole network configuration? Maybe i did something wrong (I'm actually new to networking and linux.)

---

### Post by matthew on 2005-11-19
[quote=tsd_arc]Damn. It doesnt work. When I try to open google in firefox, it says "looking up google.com" instead of "google.com cannot be found" but nothing else happens. Maybe I have to add a search server in the resolv.conf, like in the how-to? (If so, how can I find it out?)

thanks anyway.

Edit: Ah, after about 15min firefox aborts with the "google.com cannot be found" message.

Shall I post screenshots of my whole network configuration? Maybe i did something wrong (I'm actually new to networking and linux.)[/quote]
Hmm... Yeah, go over the how to again from start to finish and make sure you have each step completed. If it still doesn't work go ahead and post your configuration info here. 

I have a couple of weaknesses here in that I have no experience on Apple equipment, and I've never seen DHCP set up and working on Linux without it creating a /etc/resolv.conf file so I'm starting to feel a little shaky. Anyway, the best bet if I can't help you get it going is for someone else to see it with a fresh perspective.

---

### Post by tsd_arc on 2005-11-19
AIEEK!
IT WORKS! :D 
I don't know why, but it works. I've gone through the settings for the 5th time, and now it works, yeeha! :D Big thanks for your help. :D

---

### Post by matthew on 2005-11-19
[quote=tsd_arc]AIEEK!
IT WORKS! :D 
I don't know why, but it works. I've gone through the settings for the 5th time, and now it works, yeeha! :D Big thanks for your help. :D[/quote]
Yay!!! Glad I could be of service. Have fun with your new toy!

---

### Post by tsd_arc on 2005-11-19
hm.. theres one more problem. After a Reboot the resolv.conf is empty (well, there are 2 comment lines, but nothing else) although i've installed resolvconf and added the stuff from the how-to to the end of /etc/network/interfaces:
```

iface eth0 inet static
dns-nameservers 213.191.74.11 213.191.92.82

```

any idea?

---

### Post by matthew on 2005-11-19
The /etc/resolv.conf file is recreated on each reboot. You didn't mention whether the problem was on te laptop or on the desktop that connects through it.

On the laptop the file should already be created automatically since you are using DHCP. Since that connection was already working I will assume that the problem is not here. Please correct me if this is wrong.

On the desktop is seems that for some reason all the information is not where it needs to be. Try this. Here is the full /etc/network/interfaces from my desktop that attaches through my laptop. Compare it to yours and modify the specific IP's as needed to fit your setup.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
    script grep
    map eth0

# The primary network interface
iface eth0 inet static
    address 192.168.2.103
    netmask 255.255.255.0
    network 192.168.2.0
    broadcast 192.168.2.255
    gateway 192.168.2.102
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 68.2.16.30

```

---

### Post by tsd_arc on 2005-11-19
Yeah, now everything runs perfect. Like I said, im new to linux, so I made a mistake with the configuration. Sorry for that and a big thanks again for your help.

---

### Post by matthew on 2005-11-19
Hey, no problem and no apology necessary. I've been there. Take heart, it does get easier with time. I'm just glad we got it working for you.

---

### Post by Rxke on 2005-11-21
Just found out about this topic, nice one! :D

Begs to become a How-to (hinthint)

---

