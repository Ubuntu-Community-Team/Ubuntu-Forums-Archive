---
title: "version of wine that will work with battle.net"
date: 2007-11-24
forum: Wine
---

### Post by Tyke91 on 2007-11-24
If someone has battle.net working with wine (I don't expect any graphics, just the black screen + words is fine) can you please tell me the version of wine that you use?

---

### Post by Tyke91 on 2007-11-24
I guess nobody has gotten starcraft battle.net to work on wine at all?

seriously. I know I've done it before, but it was a long time ago and I don't know which version of wine I was using at the time (hell, it wasn't even the latest version for the time)

---

### Post by Ripichip on 2007-11-25
For warcraft 3 work great 0.9.45

---

### Post by Tyke91 on 2007-11-25
thank you

---

### Post by pizpot on 2008-02-08
I ran into this last night.

To downgrade wine, uninstall it:

sudo apt-get remove wine

Then get wine 9.45 for ubuntu 7.04 (even though you are at 7.10 don't fret) from here:

i386:
[http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine-dev_0.9.45~winehq0~ubuntu~7.04-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine-dev_0.9.45~winehq0~ubuntu~7.04-1_i386.deb)

Then run that, then go into Synaptic and lock the version so it does not upgrade by clicking System->Administration->Synaptic Package Mager and searching for wine, selecting "wine" in the list, and clicking Package->Lock Version

Tada, now you can join Battlenet and play warcraft3 or the war3 demo till you are blue in the face. :-)

---

