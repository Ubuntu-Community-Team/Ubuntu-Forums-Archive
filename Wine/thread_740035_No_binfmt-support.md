---
title: "No binfmt-support"
date: 2008-03-30
forum: Wine
---

### Post by sharkbite1414 on 2008-03-30
I don't have my Ubuntu PC on the internet (I only have dial-up at the moment) and have download wine from a windows PC. I have tried installing it but it says:

Error: binfmt-support not satisfiable

Help please!!!:)

---

### Post by happyhamster on 2008-03-30
You probably need the package "binfmt-support" (version 1.1.2 or higher).

For wine 0.9.58 the dependencies are (dpkg -s wine):

> 
Depends: binfmt-support (>= 1.1.2), libasound2 (>> 1.0.14), libaudio2, libaudiofile0 (>= 0.2.3-4), libc6 (>= 2.6-1), libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35), libgl1-mesa-glx | libgl1, libglu1-mesa | libglu1, libgphoto2-2 (>= 2.4.0), libgphoto2-port0 (>= 2.4.0), libice6 (>= 1:1.0.0), liblcms1 (>= 1.15-1), libldap2 (>= 2.1.17-1), libsm6, libx11-6, libxau6, libxext6, libxml2 (>= 2.6.29), libxslt1.1 (>= 1.1.20), libxt6, libxxf86vm1

So, you can try checking if you have those packages installed, and download those that aren't when you do have internet access.

Good luck.

---

### Post by hyperair on 2008-03-30
Do this: 
```
sudo dpkg --force-depends -i <path to wine.deb>
```

then:
```
apt-get install -f --print-uris > ~/packages_to_download.txt
```

Bring ~/packages_to_download.txt on thumbdrive to some other computer with an internet connection. Download all of them. Copy them into /var/cache/apt/archives (as root). Then run:
```
sudo apt-get install -f
```

It should complete fine. =)

---

