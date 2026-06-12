---
title: "Can't install wine1.5.11"
date: 2012-08-20
forum: Wine
---

### Post by lost_guadelenn on 2012-08-20
When I try to install wine I get this:

```
 sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Ok, trying wine1.5:

```
sudo apt-get install wine1.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.5 : Depends: wine1.5-i386 (= 1.5.11-0ubuntu1)
           Recommends: winetricks but it is not going to be installed
E: Unable to correct problems, you have held broken packages
```

Ok, trying winetricks:

```
 sudo apt-get install winetricks
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  pax rpm librpmbuild2 librpmsign0 ncurses-term
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libcapi20-3 libgif4:i386 libmpg123-0 wine-gecko1.4 wine-gecko1.4:i386
  wine1.4 wine1.4-amd64 wine1.4-common wine1.4-i386:i386
Recommended packages:
  gettext:i386
The following packages will be REMOVED:
  alien debhelper gettext google-earth-stable intltool-debian lsb-core
  po-debconf
The following NEW packages will be installed:
  libcapi20-3 libgif4:i386 libmpg123-0 wine-gecko1.4 wine-gecko1.4:i386
  wine1.4 wine1.4-amd64 wine1.4-common wine1.4-i386:i386 winetricks
0 upgraded, 10 newly installed, 7 to remove and 0 not upgraded.
Need to get 72.6 MB of archives.
After this operation, 133 MB of additional disk space will be used.

```

Wait! It depends on wine1.4?! Is it ok?

How can I install wine1.5?

---

### Post by cbanakis on 2012-08-20
Did you try adding the wine ppa to your software sources?

ppa.launchpad.net/ubuntu-wine/ppa/ubuntu

---

### Post by lost_guadelenn on 2012-08-20
Of course I did.
I had no problems upgrading wine for past year until today.

---

### Post by cbanakis on 2012-08-20
Maybe the server that the ppa points to is down?

I too never had problems.

I just do it through the software center though.
(Too lazy for command line, if I have a choice)

---

### Post by cbanakis on 2012-08-20
All working fine on my end.

Looks like you need to install 1.4 first.

I just installed from the software center, then added the ppa, and did a software update.

---

### Post by DoktorSeven on 2012-08-20
Apparently the wine1.5-i386 package for 1.5.11 (which wine1.5 depends on) hasn't been made available yet and is breaking the dependency.  Doing a policy query shows only 1.5.10 for it:

```

apt-cache policy wine1.5-i386
wine1.5-i386:i386:
  Installed: 1.5.10-0ubuntu1~pulse19+build4
  Candidate: 1.5.10-0ubuntu1~pulse19+build4
  Version table:
 *** 1.5.10-0ubuntu1~pulse19+build4 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status

$ apt-cache policy wine1.5
wine1.5:
  Installed: 1.5.10-0ubuntu1~pulse19+build4
  Candidate: 1.5.11-0ubuntu1
  Version table:
     1.5.11-0ubuntu1 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main amd64 Packages
 *** 1.5.10-0ubuntu1~pulse19+build4 0
        100 /var/lib/dpkg/status

```

So apparently we're going to have to wait until they fix/update the PPA.

EDIT/UPDATE: Indeed, the PPA is updated now and 1.5.11 should be available.

---

### Post by texasboy2084 on 2012-08-20
I ran into this problem this morning, seems that the ppa has been updated now.

---

