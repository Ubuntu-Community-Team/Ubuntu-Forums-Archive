---
title: "unable to update packages: authentication error"
date: 2008-09-21
forum: x86 64-bit Users
---

### Post by malrost on 2008-09-21
There are a number of packages I am unable to update, either via the package manager or apt-get upgrade. (I generally try to use Synaptic as much as possible, apt-get when necessary, and build from source only as a last resort.)

The update manager gives me the message "error authenticating some packages", while 'apt-get upgrade' says "The following packages have been left back", then lists these same packages:

```

libgtk-vnc-1.0-0
libnm-glib0
libnm-util0
libvlc2
libvlccore0
network-manager
network-manager-gnome
vlc
vlc-nox
vlc-plugin-pulse
wpasupplicant

```

I've tried troubleshooting on my own, and believe that it is either a repository problem, my sources.list file or lack of the proper authentication key. Here's what I've tried:

[LIST]
[*]I first tried switching the depository server from US to Main (which recently helped with a different issue on my laptop) to no avail. 

[*]My attempts to manually fix my sources.list file have not worked. 

[*]I am not sure how to track down what public key I need or how to get it. (IOW I've installed add-apt-key, but what key do I need, and how/where do I get it?)
[/LIST]
I realized that my assessment of the cause of my authentication errors may of course be entirely wrong. But if not, here's my uncommented /etc/apt/sources.list

```
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

deb http://archive.ubuntu.com/ubuntu hardy-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu hardy-backports restricted main universe multiverse

deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security multiverse

deb http://ppa.launchpad.net/psyke83/ubuntu hardy main
deb-src http://ppa.launchpad.net/psyke83/ubuntu hardy main

```

---

### Post by malrost on 2008-09-21
I think I solved my problem but it seems like such a kludgey hack: I just tried apt-get install for each package individually. Where apt-get upgrade failed, apt-get install worked.

Any idea what was happening here?

---

### Post by kisiyel on 2008-11-07
I had similar issue, same logic but in a different method "aptitude" solved my problem (I accepted the solution what aptitude suggested).

---

