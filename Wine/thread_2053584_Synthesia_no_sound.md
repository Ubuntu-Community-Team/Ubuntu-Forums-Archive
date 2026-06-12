---
title: "Synthesia no sound"
date: 2012-09-05
forum: Wine
---

### Post by Carlos19 on 2012-09-05
Hi I don't really know much about wine and I am a noob at Ubuntu stuff but I am using wine1.3 and this guy solved the problemI am having with Synthesia
**[http://ubuntuforums.org/showthread.php?t=2013211&highlight=Synthesia+sound](http://ubuntuforums.org/showthread.php?t=2013211&highlight=Synthesia+sound)**
But for some reason I cant install wine1.4? 
When I do "sudo add-apt-repository ppa:ubuntu-wine/ppa" this is what is says:

"Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: "Launchpad PPA for Ubuntu Wine Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1"

And then when I do "sudo apt-get install wine1.4" it says this:

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine1.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'wine1.4' has no installation candidate"

I also try adding in the Software Sources-> Other Software-> Add-> "*ppa:ubuntu-wine/ppa"*

And reload in Synaptic Package Manager it still don't work.

So... I'm stuck with 1.3. Dunno what to do. If someone could give me a Step-by-Step tutorial I would be very happy:).
By the way I am on Ubuntu 11.04 Natty Narwhal - amd64

---

