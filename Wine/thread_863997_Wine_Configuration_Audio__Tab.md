---
title: "Wine Configuration Audio  Tab"
date: 2008-07-19
forum: Wine
---

### Post by SoberWarlock on 2008-07-19
When launching Winecfg I get an error under Audio Tab. Here's what it says:

> *******@********:~$ winecfg
fixme:jack:JACK_drvLoad error loading the jack library libjack.so.0, please install this library to use jack


I don't know how to install the libjack. Please hep :confused:

---

### Post by lightstream on 2008-07-19
You don't need that library, unless you want to use the 'JACK driver'. You should still be able to use the other audio drivers, eg Alsa, OSS.

---

### Post by hexxa on 2008-07-19
Have you try 
apt-cache search libjack ?

**[COLOR="Red"]apt-get install libjack0[/COLOR]**

---

