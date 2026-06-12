---
title: "Cant install wine"
date: 2016-05-30
forum: Wine
---

### Post by smsmith050 on 2016-05-30
I have the same problem. I am using Trusty 64 bit. Has anyone solved installing wine issue?
 
```
sudo apt-get install wine ends with this error message
The following packages have unmet dependencies:
 wine : Depends: wine1.6
E: Unable to correct problems, you have held broken packages.
```

Synaptic shows no broken packages.

```
uname -a
Linux Linux 4.2.0-36-generic #42~14.04.1-Ubuntu SMP Fri May 13 17:27:22 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

```
dpkg --print-architecture
amd64
```

```
current.repos.list 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp-edge/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp-edge/ubuntu) trusty main
deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp-edge/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp-edge/ubuntu) trusty main
deb [http://ppa.launchpad.net/philip5/extra/ubuntu](http://ppa.launchpad.net/philip5/extra/ubuntu) trusty main
deb [http://ppa.launchpad.net/philip5/extra/ubuntu](http://ppa.launchpad.net/philip5/extra/ubuntu) trusty main
deb [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) trusty main
```

Installed Trusty 64bit into a virtualbox. Installed wine. It all works. Now I need to find out why wine won't install on my main (host) system. 

```
uname -a
Linux ssmith-VirtualBox 4.2.0-27-generic #32~14.04.1-Ubuntu SMP Fri Jan 22 15:32:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

```
dpkg --print-architecture
amd64
```

```
wine --version
wine-1.6.2
```

---

### Post by howefield on 2016-06-01
Post moved to own thread.

---

