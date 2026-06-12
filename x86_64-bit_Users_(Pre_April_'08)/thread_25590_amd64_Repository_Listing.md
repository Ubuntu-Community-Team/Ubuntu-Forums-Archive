---
title: "amd64 Repository Listing"
date: 2005-04-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by joshuapurcell on 2005-04-10
Does anyone have a list of working amd64 repositories? Here is my current /etc/apt/sources.list:
> ## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe main restricted

# Security
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe main restricted

# Multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
The ones that are commented out above are ones that I receive errors from. If anyone has some other repositories that I can add to this list that would be great.

---

### Post by c_dog on 2005-04-10
You might waht to check or uncheck  your US archive lines again. I haven't any problems with the binary repos you have checked off. Add the videolan for marrillat site for Mplayer,VLC and deCSS stuff. No action yet for 64-bit backports.```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted
deb file:/var/cache/apt-build/repository apt-build main

deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.

deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

# deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
# deb ftp://ftp.nerim.net/debian-marillat/ testing main

# deb http://debian-amd64.alioth.debian.org/pure64 sid main contrib non-free

deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

#deb http://download.videolan.org/pub/videolan/debian sid main
deb-src http://download.videolan.org/pub/videolan/debian sid main

# deb http://ubuntu-bp.sourceforge.net/ubuntu/ hoary-backports main universe
```

---

### Post by Muchacho_Gasolino on 2005-04-10
here is my list:

```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview amd64 Binary-1 (20041020)]/ unstable main restricted 

deb http://archive.ubuntu.com/ubuntu/ hoary main restricted 
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hoary universe 
deb-src http://archive.ubuntu.com/ubuntu/ hoary universe 

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted

deb http://cyberspace.ucla.edu/marillat/ unstable main
```

they all work fine for me

c_dog: with your marillat repository address, I had trouble, meaning i had absolutely no packages listed from that respository. I checked his site, and it said that the amd64 repo had a different address. It is the last line in my file above, and it has worked great so far

---

### Post by joshuapurcell on 2005-04-11
Thanks guys, you rock.

---

