---
title: "Google Earth on Gutsy (Tribe 5) AMD64"
date: 2007-09-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Emblem Parade on 2007-09-27
Lots of people have trouble with this, but I got it to work pretty easily, with Compiz Fusion (NVIDIA) working and all! Good thing, too, because this was the 64-bit deal breaker for me. And, no, I refuse to use Automatix. Mileage may vary...

```

sudo aptitude install make-googleearth-package
cd ~
wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
make-googleearth-package
sudo dpkg -i --force-architecture googleearth[tab]

```

(press TAB at the end there to get the correct filename for the version)

Thanks to [Sysadmin's Diary]("http://blog.irwan.name/?p=103") for the tip!

---

### Post by dabl on 2007-09-27
That looks like the hard way, to me.  Here's how I do it:

Go to Medibuntu here: [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)

Click the "Repo How-To" tab and add the repo and key for your version (might need to cheat a little and use the Feisty repo for Gutsy, for a couple of weeks).

Open Synaptic or Adept Manager and "refresh" the package list.

Mark the Google Earth package for installation, and apply.  Accept their license.

Spin the globe and watch smoke come out of your graphics card!  :lolflag:

---

