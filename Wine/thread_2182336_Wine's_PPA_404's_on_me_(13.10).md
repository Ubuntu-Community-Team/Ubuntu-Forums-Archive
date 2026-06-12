---
title: "Wine's PPA 404's on me (13.10)"
date: 2013-10-20
forum: Wine
---

### Post by Monsuco on 2013-10-20
I'm on Kubuntu 13.10 (64-bit) and I can't seem to get wine installed. Per their instructions, I punched the PPA into Synaptic (I prefer it to Muon) and refreshed my repositories. I get this
```
Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/dists//ubuntu/saucy/binary-amd64/Packages  404  Not Found
Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/dists//ubuntu/main/binary-amd64/Packages  404  Not Found
Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/dists//ubuntu/saucy/binary-i386/Packages  404  Not Found
Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/dists//ubuntu/main/binary-i386/Packages  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.
```

I've never had this problem before and Wine worked out well on 13.04. The version of Wine in the Ubuntu repositories is obsolete so I want to use modern versions and I loathe the idea of compiling from source every time there's an update so I'd like to just get the repository working. Any thoughts on what I could do?

---

### Post by Toz on 2013-10-21
Which instructions did you follow? Using:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
```
...works fine here.

---

### Post by Monsuco on 2013-10-21
> **Toz said:**
> Which instructions did you follow? Using:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
```
...works fine here.

Oddly... that worked. I wonder why adding through synaptic failed but adding through the CLI worked.

Thank you.

---

### Post by monkeybrain20122 on 2013-10-21
> **Monsuco said:**
> Oddly... that worked. I wonder why adding through synaptic failed but adding through the CLI worked.

Thank you.

That seems to be a general problem for any ppa. I started a thread here
[http://ubuntuforums.org/showthread.php?t=2181813&page=2&p=12821745#post12821745](http://ubuntuforums.org/showthread.php?t=2181813&page=2&p=12821745#post12821745)

---

