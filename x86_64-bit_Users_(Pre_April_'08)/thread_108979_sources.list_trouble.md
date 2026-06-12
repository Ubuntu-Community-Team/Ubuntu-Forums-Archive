---
title: "sources.list trouble"
date: 2005-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by kurokikaze on 2005-12-27
Hi. I'm running Ubuntu AMD64. I've replaced the original /etc/apt/sources.list with the following one, but it doesn't work. 

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted

## INTERNATIONAL HOSTS ##

# Ubuntu supported packages (packages)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu supported packages (sources)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages (packages)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Ubuntu community supported packages (sources)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Ubuntu backports project (packages)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Ubuntu backports project (sources)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## ITALIAN HOSTS ##

# Ubuntu supported packages (packages)
#deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy main restricted
#deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-updates main restricted


# Ubuntu supported packages (sources)
#deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy main restricted
#deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-updates main restricted

# Ubuntu community supported packages (packages)
#deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy universe multiverse

# Ubuntu community supported packages (sources)
#deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy universe multiverse

# Ubuntu backports project (packages)
#deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

Do you see something wrong or the servers are simply down?

---

### Post by amohanty on 2005-12-28
Can you post the output of > apt-get update

---

### Post by kurokikaze on 2005-12-28
[QUOTE=amohanty]Can you post the output of[/QUOTE]

Here it is the output:

> Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Impossible to connect to security.ubuntu.com:80 (1.0.0.0), connection time limit reached

W: Impossible to check the source packages list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)

These are just 2 cases, but the output is the same for each line of my sources.list file

I'm behind a router, but I don't think there's something wrong with this because all of the urls are simple http addresses and I can reach the Internet.

Any suggestion?

---

### Post by amohanty on 2005-12-28
Can hit this in firefox:
[http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)

AM

---

### Post by kurokikaze on 2005-12-28
[QUOTE=amohanty]Can hit this in firefox:
[http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)

AM[/QUOTE]

Yes, I can use the "manual" mode, but it's a little bit frustrating. Ironically, five minutes ago apt-get update worked, but now it's dead again.

I think I'll look for the .deb file manually. Thanks for the help.

---

### Post by amohanty on 2005-12-28
What does:

> nslookup security.ubuntu.com

return
AM

---

### Post by kurokikaze on 2005-12-28
Don't worry. I discovered the servers were down. Now everything works great!

---

