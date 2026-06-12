---
title: "Karmic - Aptitude very slow to start downloading from server"
date: 2009-10-29
forum: x86 64-bit Users
---

### Post by nelox on 2009-10-29
I'm loving my shiny new installation of Karmic with all its improvements, however one problem has cropped up:

After entering:

```
james@crumpet:~$ sudo apt-get update
0% [Connecting to mirror.internode.on.net]
```

It hangs at the "Connecting to" server for 20 seconds before returning any hits. This behaviour occurs with every server choice. Yes, I tried them all.

Previously with Jaunty, the server response was almost immediate.

I'm sure there must be something amiss with my setup. Any ideas?

---

### Post by dvlchd3 on 2009-10-29
9.10 just came out.  The repos are being overloaded by everyone doing exactly what you are doing.

It is true, we ALL need MORE bandwidth....:D

---

### Post by nelox on 2009-11-06
> **dvlchd3 said:**
> 9.10 just came out.  The repos are being overloaded by everyone doing exactly what you are doing.

It is true, we ALL need MORE bandwidth....:D

It's been a week now and the load on servers has abated, however my problem persists.

What do I need to do in order to troubleshoot this please?

---

### Post by dcstar on 2009-11-06
> **nelox said:**
> It's been a week now and the load on servers has abated, however my problem persists.

What do I need to do in order to troubleshoot this please?

[LIST=1]
[*]Look in your software sources for any old version entries.
[*]Ping the repository sites to see how quickly they respond.
[/LIST]

---

### Post by nelox on 2009-11-07
> **dcstar said:**
> [LIST=1]
[*]Look in your software sources for any old version entries.
[*]Ping the repository sites to see how quickly they respond.
[/LIST]

Here is my sources list. All seems to be in order there.

```
james@crumpet:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ karmic main restricted
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ karmic-updates main restricted
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ karmic universe
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ karmic universe
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ karmic-updates universe
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ karmic multiverse
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ karmic multiverse
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ karmic-updates multiverse
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ karmic-security main restricted
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ karmic-security main restricted
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ karmic-security universe
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ karmic-security universe
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ karmic-security multiverse
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ karmic-security multiverse

```

Here are the results of pinging each of the repository sites configured.

```
james@crumpet:~$ ping -c 10 archive.canonical.com
PING archive.canonical.com (91.189.90.142) 56(84) bytes of data.
64 bytes from archive.canonical.com (91.189.90.142): icmp_seq=1 ttl=44 time=325 ms
64 bytes from archive.canonical.com (91.189.90.142): icmp_seq=2 ttl=44 time=325 ms
64 bytes from archive.canonical.com (91.189.90.142): icmp_seq=3 ttl=44 time=325 ms
64 bytes from archive.canonical.com (91.189.90.142): icmp_seq=4 ttl=44 time=325 ms
64 bytes from archive.canonical.com (91.189.90.142): icmp_seq=5 ttl=44 time=325 ms
64 bytes from archive.canonical.com (91.189.90.142): icmp_seq=6 ttl=44 time=325 ms
64 bytes from archive.canonical.com (91.189.90.142): icmp_seq=7 ttl=44 time=325 ms
64 bytes from archive.canonical.com (91.189.90.142): icmp_seq=8 ttl=44 time=325 ms
64 bytes from archive.canonical.com (91.189.90.142): icmp_seq=9 ttl=44 time=324 ms
64 bytes from archive.canonical.com (91.189.90.142): icmp_seq=10 ttl=44 time=325 ms

--- archive.canonical.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9011ms
rtt min/avg/max/mdev = 324.951/325.294/325.830/0.737 ms

``````
james@crumpet:~$ ping -c 10 mirror.internode.on.net
PING mirror.internode.on.net (150.101.135.3) 56(84) bytes of data.
64 bytes from mirror.internode.on.net (150.101.135.3): icmp_seq=1 ttl=58 time=38.7 ms
64 bytes from mirror.internode.on.net (150.101.135.3): icmp_seq=2 ttl=58 time=38.6 ms
64 bytes from mirror.internode.on.net (150.101.135.3): icmp_seq=3 ttl=58 time=39.2 ms
64 bytes from mirror.internode.on.net (150.101.135.3): icmp_seq=4 ttl=58 time=39.4 ms
64 bytes from mirror.internode.on.net (150.101.135.3): icmp_seq=5 ttl=58 time=39.0 ms
64 bytes from mirror.internode.on.net (150.101.135.3): icmp_seq=6 ttl=58 time=39.7 ms
64 bytes from mirror.internode.on.net (150.101.135.3): icmp_seq=7 ttl=58 time=39.2 ms
64 bytes from mirror.internode.on.net (150.101.135.3): icmp_seq=8 ttl=58 time=39.2 ms
64 bytes from mirror.internode.on.net (150.101.135.3): icmp_seq=9 ttl=58 time=38.8 ms
64 bytes from mirror.internode.on.net (150.101.135.3): icmp_seq=10 ttl=58 time=38.7 ms

--- mirror.internode.on.net ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9013ms
rtt min/avg/max/mdev = 38.694/39.107/39.741/0.359 ms
```

---

