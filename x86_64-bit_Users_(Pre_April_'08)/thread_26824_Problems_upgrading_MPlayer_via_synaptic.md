---
title: "Problems upgrading MPlayer via synaptic"
date: 2005-04-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by makis on 2005-04-14
Hi all!

I tried update my MPlayer via synaptic, and I received the following message:

[B]  mplayer:
  Depends: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is to be installed
  Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed[/B]

As a newbie, I had the very fine idea of uninstalling the previous edition of MPlayer from my system and then installing the new one!!

As you can imagine I couldn't because of the same error!

It is clear that the new version of MPlayer needs some new editions of the libraries which are not yet supported by Ubuntu!! I try to find and install them but there are nowhere!

Additionally, I cannot install any previous versions of MPlayer! In fact, as far as I can see, Ubuntu changed quite soon the edition of MPlayer without supporting it with its new dependancies!!

Does anybody know what to do with that dependancies, and --most important-- why Ubuntu does not provide any immediate support in such crirical things??

thank you!

Makis

---

### Post by rwabel on 2005-04-14
same for me here, I guess we just need to wait until the dependency is resolved

---

### Post by dusu on 2005-04-14
Hi,
I think I had the same problem, but I'm not sure I remember how I cured it :(
I think (though not sure and anyone can correct me if I'm wrong) that everything got fixed once I added the backports to my sources.list

---

### Post by makis on 2005-04-15
Thx for your response my friends!

I have added the backports to my sources.list, which is the following:

[B]## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://cyberspace.ucla.edu/marillat/](http://cyberspace.ucla.edu/marillat/) unstable main

#deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main
#deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main

#deb [http://debian-amd64.alioth.debian.org/pure64](http://debian-amd64.alioth.debian.org/pure64) sid main contrib non-free

# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted
[/B]

I am proud of my list  \\:D/ , I think has everything!

Anyway, I have concluded that, as rwabel said, we have to wait. But I have also to say that this is a bad policy: Ubuntu shows us the honey but we cannot eat it!

It would be preferable if they add upgrades only when they have incorporated their upgraded dependencies.

Makis

---

