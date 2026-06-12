---
title: "web videos not working"
date: 2008-06-26
forum: x86 64-bit Users
---

### Post by eruheru on 2008-06-26
Hey all,
I am currently running version 8.01 on a 64 bit system. I am having problems with web videos especially youtube. often instead of the video player loading, there is just a gray box. I believe I have all of the plugins needed for firefox, so I am unsure why this is happening. 
Thanks

---

### Post by aheckler on 2008-06-26
Which plugin are you using? Adobe's, Gnash, or Swfdec?

---

### Post by markbuntu on 2008-06-28
Do you have nspluginwrapper?
flash will not play in firefox on 64 without that.

---

### Post by onering on 2008-06-28
I had the same problem.  I think it may have been after some system updates.

Try typing these lines in at a terminal window, one at a time.  It will reload the flash wrapper.

sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0/plugins/

---

