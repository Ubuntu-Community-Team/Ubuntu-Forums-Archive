---
title: "Steam freeze when downloading"
date: 2007-12-19
forum: Wine
---

### Post by noamh on 2007-12-19
Hi all,

I seem to have a new problem with steam:

1. It used to run just fine on 7.04
2. ever since I moved to 7.10 I am unable to download new games. When I try to install a game, the interface comeup and said "downloading 2%" and I actually see some network activity. However, after couple of minutes, steam just freeze and I have to kill-9 it.

I tried several wine version from 0.9.47 to 0.9.51 , played with the virtual desktop, tried nice -19 and many other twicks, but none had any effect.

Any ideas would be greatly appreciated!

---

### Post by upbeat.linux on 2007-12-20
As lame as it sounds try uninstalling steam, restarting, and then reinstalling Steam.

You may wish to edit your registry and set the default font to something other than  Tahoma.ttf. I can't find it right now, but there's a post detailing how to modify the default font Steam uses. It might be a registry tweak or simply copying another font to tahoma.ttf.

Ensure that firestarter/iptables/moblock are not blocking steam Updates

Also, change your Ubuntu graphic settings back to Metacity.....

---

### Post by noamh on 2007-12-20
Thanks upbeat. I have tried many many things, including searching through the various posts, but nothing apear to help.

I tried:
uninstalling wine
using different wine version from 0.9.47 to 0.9.51
reinstalled Steam
played with the process priority (nice) on steam.exe and the wine server
tweaked the /etc/sysctl.conf file
played with the windows version, emulated desktop, sound driver .....

I realy can't think of anything else other than going back to 7.04.

Again, the problem only happens when steam is trying to download a game (the updates are downloading fine).

---

