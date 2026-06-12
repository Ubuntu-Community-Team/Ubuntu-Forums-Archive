---
title: "Broken package (libnetfilter-queue-dev) -- help!"
date: 2007-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by paul_banks on 2007-05-27
I recently installed moblock, using the following steps:

sudo dpkg -i libnfnetlink0_0.0.14-1.1_amd64.deb
sudo dpkg -i libnfnetlink-dev_0.0.14-1.1_amd64.deb
sudo dpkg -i libnetfilter-queue_0.0.11-1.1_amd64.deb
sudo dpkg -i libnetfilter-queue-dev_0.0.11-1.1_amd64.deb
sudo dpkg -i moblock-nfq_0.8-10_amd64.deb

moblock works, as far as I can tell, but I've got a broken package now. Auto-updates won't work now, either. Synaptic manager tells me that libnetfilter-queue-dev is broken, but when I try to reinstall it, it tells me I have to install libnetfilter-queue1 as well. Fine by me, but I get the following error when I try to install both:

E: /var/cache/apt/archives/libnetfilter-queue1_0.0.12-1_amd64.deb: trying to overwrite `/usr/lib/libnetfilter_queue_libipq.so.1.0.0', which is also in package libnetfilter-queue

I'm very new to Ubuntu, so I'm afraid to proceed on my own here... I tried the official moblock thread, but couldn't find anything about broken packages. Can I just unistall and then re-install these packages, or would that cause me more grief? Thanks!

---

### Post by moma on 2007-05-27
Download the problematic Ubuntu packages from packages.ubuntu.com. Do this
1) Browse to [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

2) Search for "libnetfilter-queue" and download it (the .deb) package.
Example: the search will send you to [http://packages.ubuntu.com/feisty/libs/libnetfilter-queue1](http://packages.ubuntu.com/feisty/libs/libnetfilter-queue1)
Click the "amd64" link (you obviously run 64 bits system) and download the .deb package from the nearest mirror.

On the same way, search and download "libnetfilter-queue-dev" and other problematic packages.

Download all packages to the same folder and 
issue following command to install them (the .debs).
$[COLOR="SeaGreen"] sudo dpkg -i  *deb [/COLOR]

In many cases Ubuntu will calm down after this illusion. In any case, [COLOR="SandyBrown"]no harm done[/COLOR] as [cylons]("http://en.wikipedia.org/wiki/Cylon_%28Battlestar_Galactica%29") use to say it.

---

### Post by PierceUK on 2007-07-15
Hi just to say i had the exact same problem after installing moblock.

followed your advice but to no avail.

i used the package manager to show the broken package and just removed it.

package manager is now happy but not sure if moblock is.....

---

### Post by jamesford on 2007-07-15
in feisty u dont need all the packages supplied on that page, you only need the following, in this order:
libnfnetlink0_0.0.14-1.1_amd64.deb
libnetfilter-queue_0.0.11-1.1_amd64.deb
moblock-nfq_0.8-10_amd64.deb

the rest are probably autimaticly installed as dependencies

before installing that u should probably uninstall all the moblock related packages previously installed including the broken ones iirc

---

