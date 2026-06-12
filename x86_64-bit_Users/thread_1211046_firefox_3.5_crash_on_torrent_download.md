---
title: "firefox 3.5 crash on torrent download"
date: 2009-07-12
forum: x86 64-bit Users
---

### Post by chocolatecheerios on 2009-07-12
I installed firefox 3.5 from the ubuntu repository via apt-get to replace 3.0. Browsing works, file downloads work, but torrent downloads do not. Whenever I click to download a torrent the browser segfaults. In firefox 3.0 I could choose the application to handle torrents (qbittorrent), but there's no selection available for 3.5. I cleared my firefox user profile with -profilemanager, but that didn't help. Ideas?

---

### Post by -=hazard=- on 2009-07-12
Firefox 3.5 is the one called shiretoko I am using it now and just tested to download a torrent and works fine, I can even choose the aplication to download with.

---

### Post by lordofallhearts on 2009-07-12
The Firefox in ubuntu repositories is still in testing, thats why its not upgrading thru automatic updates
3.5 will be launched officially with KarmicKoala 9.10.

So I suggest you to install via 
[http://www.1earthadventures.com/2009/07/01/the-net-now/installing-firefox-3-5-tar-bz2-on-ubuntu-9-04/](http://www.1earthadventures.com/2009/07/01/the-net-now/installing-firefox-3-5-tar-bz2-on-ubuntu-9-04/)

---

### Post by chocolatecheerios on 2009-07-12
> **lordofallhearts said:**
> The Firefox in ubuntu repositories is still in testing, thats why its not upgrading thru automatic updates
3.5 will be launched officially with KarmicKoala 9.10.

So I suggest you to install via 
[http://www.1earthadventures.com/2009/07/01/the-net-now/installing-firefox-3-5-tar-bz2-on-ubuntu-9-04/](http://www.1earthadventures.com/2009/07/01/the-net-now/installing-firefox-3-5-tar-bz2-on-ubuntu-9-04/)

I see. I tried the official package, but my internet connection wouldn't work anymore despite whatever good network settings being in place. I'll stick with 3.0 for now.

---

### Post by sanderj on 2009-07-12
> **chocolatecheerios said:**
> I see. I tried the official package, but my internet connection wouldn't work anymore despite whatever good network settings being in place. I'll stick with 3.0 for now.

Haha, same here! With the official Firefox 3.5 (running on Ubuntu 64-bit), DNS-resolving was not working, and I could only access pages via their IP-address. :-(

The shireteko (or something like that), installed as "firefox-3.5" or "firefox3.5", is OK for me.

---

### Post by chocolatecheerios on 2009-07-12
> **sanderj said:**
> Haha, same here! With the official Firefox 3.5 (running on Ubuntu 64-bit), DNS-resolving was not working, and I could only access pages via their IP-address. :-(

The shireteko (or something like that), installed as "firefox-3.5" or "firefox3.5", is OK for me.

Now that you gave me an idea where to look I got this fixed by going into about:config and flipping the switch for **network.dns.disableIPv6** to be **true**.

---

