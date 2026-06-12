---
title: "Exaile &amp; gstreamer-plugins-bad 0.10.5"
date: 2007-08-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by dn* on 2007-08-19
In order to get some advanced features of Exaile's SVN versions you need gstreamer-plugins-bad 0.10.5 installed but for the life of me I cannot find an AMD64 deb or repo and installing from source has thus far been problematic. 

I was wondering if anyone had any luck getting the new plugin set working. Also, as a side - python-daap is require to get DAAP working with Exaile, anyone with amd64 got it working?

---

### Post by John.Michael.Kane on 2007-08-19
> **dn* said:**
> In order to get some advanced features of Exaile's SVN versions you need gstreamer-plugins-bad 0.10.5 installed but for the life of me I cannot find an AMD64 deb or repo and installing from source has thus far been problematic. 

I was wondering if anyone had any luck getting the new plugin set working. Also, as a side - python-daap is require to get DAAP working with Exaile, anyone with amd64 got it working?

Compile from source.
[GStreamer]("http://gstreamer.freedesktop.org/download/")
[GStreamer Bad Plug-ins 0.10.5]("http://gstreamer.freedesktop.org/releases/gst-plugins-bad/0.10.5.html")

Or

Try grabbing it, and all needed dependencies from here.
[gstreamer0.10-plugins-bad]("http://packages.ubuntu.com/gutsy/libs/gstreamer0.10-plugins-bad")

---

### Post by dn* on 2007-08-21
ok i went the way of install the gutsy debs, and that worked a charm. but in the process i had to do -f install which i think messed with some of my packages. anyway, i started with nspluginwrapper for flash on amd64 firefox but ran into a lot of dependency issues (basically it wouldn't install because the feisty libc6 etc. etc. wasn't there). so i've just tried to downgrade libc6 which went ok, but now everytime i do -anything- with apt-get i get this:

> damien@alisa:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  gstreamer0.10-plugins-bad: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed
  libasound2: Depends: libc6 (>= 2.6) but 2.5-0ubuntu14 is installed
  libfreebob0: Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is installed
  libgcc1: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed
  libglib2.0-0: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed
  libgstreamer-plugins-base0.10-0: Depends: libc6 (>= 2.6) but 2.5-0ubuntu14 is installed
  libgstreamer0.10-0: Depends: libc6 (>= 2.6) but 2.5-0ubuntu14 is installed
  libjack0: Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is installed
  libmms0: Depends: libc6 (>= 2.6) but 2.5-0ubuntu14 is installed
  libmusicbrainz4c2a: Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is installed
  liboil0.3: Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is installed
  libstdc++6: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed
  libxml2: Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is installed
  python-daap: Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is installed
E: Unmet dependencies. Try using -f.

using -f install again tries to remove pretty much all the packages on my computer. is there any way of downgrading back to the default feisty packages?

---

### Post by dn* on 2007-08-21
I resolved the issue by downloading all the packages I had 'gusty'ified and putting them all in one folder (for me this was Feisty). Once they were all there I did:

```
sudo dpkg -i --force-all *.deb
```

apparently doing force-all can be dangerous, especially on libc6, but i've had no issues so far. gonna try the good old fashion manual compile of gstreamer now!

---

