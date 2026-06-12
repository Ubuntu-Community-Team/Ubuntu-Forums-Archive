---
title: "apt-mirror on 64bit Dapper - 32bit downloads"
date: 2007-04-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by vdpollm on 2007-04-02
Hi there,

I have installed Ubuntu Server 6.06 LTS (amd64) and am in the process of creating a local mirror with apt-mirror.

If I stick to a standard ubuntu sources.list, like the one below, the apt-mirror process runs and starts to build the mirror.:
"
deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
"

However, I plan to point my workstations to the above mirror, and to make the transition as painless as possible from Windows, i need to install some applications from"

"
#deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free
#deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free

#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen
"

But, because this is a 64bit version of the distro, I get an error message:
"theli.free.fr/packaes///dists/dapper/listen binary-amd64/packages.gz: No such file or directory
apt-mirror: can't oen indesx in porceed_index_gz at /usr/bin/apt-mirror line 36. "

I want to be able to mirror the 32bit versions of the software from the above repo's, so that my users that don't have internet accesss can get updates automatically - and also to save on bandwidth, etc - we are talking about 500 users here.

I thought of one option, and that is create a virtual Ubuntu 6.06 LTS Desktop, run apt-mirror on just those repo's that won't work, and copy the udpates to the original server - however, this is would not be as elegant as doing it all from one server.

Any ideas would be appreciated.

Regards

Marc van der Poll:confused:

---

### Post by isdal on 2007-10-25
if the repositories you mention have 64 and 32 bit binaries you can add the architecture when you specify the sources:

# edgy
deb-i386 [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) edgy main restricted universe multiverse
deb-i386 [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) edgy-updates main restricted universe multiverse
deb-i386 [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) edgy-backports main restricted universe multiverse
#deb-i386 [http://ubuntu.cs.utah.edu/ubuntu/](http://ubuntu.cs.utah.edu/ubuntu/) edgy-security main restricted universe multiverse
#deb-i386 [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) edgy-proposed main restricted universe multiverse

deb-amd64 [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) edgy main restricted universe multiverse
deb-amd64 [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) edgy-updates main restricted universe multiverse
deb-amd64 [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) edgy-backports main restricted universe multiverse
#deb-amd64 [http://ubuntu.cs.utah.edu/ubuntu/](http://ubuntu.cs.utah.edu/ubuntu/) edgy-security main restricted universe multiverse
#deb-amd64 [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) edgy-proposed main restricted universe multiverse

If they don't you will have to build from source which can be a bit annoying on 500 clients...

// Tomas

---

