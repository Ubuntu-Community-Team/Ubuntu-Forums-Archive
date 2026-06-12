---
title: "Fix and Play apple tralilers Jaunty"
date: 2009-05-17
forum: x86 64-bit Users
---

### Post by Siggma on 2009-05-17
Apparently apple changed the way it initiates HD video playback recently and it's incompatible with totem. Karmic repo has a later version of totem that works fine for playing HD trailers, at least for me. This guide assumes you know how to remove totem packages. You don't need to remove the current packages, these are newer versions that supercede the older Jaunty versions. However, if things don't work as expected you can remove the listed totem packages below first.

Tested to work on both x86 and amd64 Jaunty distributions. I was unable to get totem-xine to work correctly but I'm sure it's an error on my part.

First, TEMPORARILY add the karmic (unstable branch) repo below to the bottom of /etc/apt/sources.list
```
gksu gedit /etc/apt/sources.list
```
Add this line:
```
deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) karmic main universe
```

Upgrade totem packages
```

sudo apt-get update
sudo apt-get install totem-gstreamer totem totem-plugins totem-plugins-extra totem-mozilla
gksu gedit /etc/apt/sources.list #Scroll to bottom and delete the karmic line
sudo apt-get update

```

[COLOR="DarkRed"]Be sure to remove the line from your /etc/apt/sources.list or your updates will be all messed up.[/COLOR]

Reload Firefox and play an HD trailer (if you're box and internet are fast enough) from [apple.com/trailers]("http://apple.com/trailers")
Then eat more: :popcorn:
-Tom

---

