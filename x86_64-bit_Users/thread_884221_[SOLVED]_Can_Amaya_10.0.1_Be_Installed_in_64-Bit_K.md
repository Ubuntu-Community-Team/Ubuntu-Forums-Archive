---
title: "[SOLVED] Can Amaya 10.0.1 Be Installed in 64-Bit Kubuntu?"
date: 2008-08-08
forum: x86 64-bit Users
---

### Post by Anlace on 2008-08-08
Greetings,

I would love to use Amaya 10.0.1 in my shiny new installation of 64-bit Kubuntu but when I try to install the downloaded file (amaya_10.0.1-0ubuntu1_i386.deb or amaya_wx-10.0.1-1_i386.deb) I get Error: Wrong architecture 'i386'.  I could not find a 64-bit installation file for Amaya, does anyone know where I might find one or how I might make this install work?

I wish the repositories had version 10.0.1, I found 9.55 only and there has been significant improvements made since that release.

Thanks for any assistance!

---

### Post by Kilz on 2008-08-08
> **Anlace said:**
> Greetings,

I would love to use Amaya 10.0.1 in my shiny new installation of 64-bit Kubuntu but when I try to install the downloaded file (amaya_10.0.1-0ubuntu1_i386.deb or amaya_wx-10.0.1-1_i386.deb) I get Error: Wrong architecture 'i386'.  I could not find a 64-bit installation file for Amaya, does anyone know where I might find one or how I might make this install work?

I wish the repositories had version 10.0.1, I found 9.55 only and there has been significant improvements made since that release.

Thanks for any assistance!

Where are you downloading it from?

---

### Post by Anlace on 2008-08-09
Got it from the Amaya web site at [http://www.w3.org/Amaya/User/BinDist.html](http://www.w3.org/Amaya/User/BinDist.html)

I did have this package installed in 32-bit Kubuntu 8.04.1 and loved working with the program.  I would really like to be able to do that in 64-bit Kubuntu as well.

I see that Debian has the package for 64-bit in Experimental ([http://packages.debian.org/search?keywords=amaya](http://packages.debian.org/search?keywords=amaya)), is there any way to get that package for 64-bit Kubuntu?

---

### Post by Anlace on 2008-08-09
I downloaded Amaya and Amaya-data from the Debian site:

amaya from [http://packages.debian.org/experimental/amd64/amaya/download](http://packages.debian.org/experimental/amd64/amaya/download)
amaya-data from [http://packages.debian.org/experimental/all/amaya-data/download](http://packages.debian.org/experimental/all/amaya-data/download)

I installed amaya-data first and then amaya.  So far it's working great.

---

### Post by Kilz on 2008-08-09
> **Anlace said:**
> I downloaded Amaya and Amaya-data from the Debian site:

amaya from [http://packages.debian.org/experimental/amd64/amaya/download](http://packages.debian.org/experimental/amd64/amaya/download)
amaya-data from [http://packages.debian.org/experimental/all/amaya-data/download](http://packages.debian.org/experimental/all/amaya-data/download)

I installed amaya-data first and then amaya.  So far it's working great.

Sometimes Debian packages work on Ubuntu because Ubuntu is based on Debian. If you do find some problem the packages can be uninstalled.

---

### Post by Anlace on 2008-08-09
That was exactly my thought too, I'm just happy that so far all is good and that it was so easy to do.

---

### Post by Loki.Satyr on 2008-12-09
> **Anlace said:**
> I downloaded Amaya and Amaya-data from the Debian site:

amaya from [http://packages.debian.org/experimental/amd64/amaya/download](http://packages.debian.org/experimental/amd64/amaya/download)
amaya-data from [http://packages.debian.org/experimental/all/amaya-data/download](http://packages.debian.org/experimental/all/amaya-data/download)

I installed amaya-data first and then amaya.  So far it's working great.

Using Ubuntu 8.04 I had to install via Synaptic libwxbase2.8.7.1, then manually install these packages:

[http://packages.debian.org/unstable/all/amaya-doc/download](http://packages.debian.org/unstable/all/amaya-doc/download)
[http://packages.debian.org/unstable/amd64/amaya/download](http://packages.debian.org/unstable/amd64/amaya/download)
[http://packages.debian.org/unstable/all/amaya-data/download](http://packages.debian.org/unstable/all/amaya-data/download)
[http://packages.debian.org/sid/amd64/libraptor1/download](http://packages.debian.org/sid/amd64/libraptor1/download)
[http://packages.debian.org/lenny/libwxgtk2.8-0](http://packages.debian.org/lenny/libwxgtk2.8-0)
[http://packages.debian.org/lenny/amd64/libwxgtk2.8-0/download](http://packages.debian.org/lenny/amd64/libwxgtk2.8-0/download)

---

### Post by ushimitsudoki on 2008-12-11
I filed a bug about an issue I had with amaya. Simple fix and I think it may be related to Nvidia binary drivers?

Here it is: [https://bugs.launchpad.net/ubuntu/+source/amaya/+bug/304299](https://bugs.launchpad.net/ubuntu/+source/amaya/+bug/304299)

---

