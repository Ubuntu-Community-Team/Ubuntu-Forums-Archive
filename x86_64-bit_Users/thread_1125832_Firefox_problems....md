---
title: "Firefox problems..."
date: 2009-04-14
forum: x86 64-bit Users
---

### Post by yarjar on 2009-04-14
I think most of the problems have to do with JavaScript. What's odd is that the problems randomly occur, and then stop occurring days later, without me changing any settings. Then, they'll come back again at a random date.

The symptoms are as such:
- Can't log into Facebook; I click the login button and my mouse cursor just sets to waiting, never resolves
- Random JavaScript functions on some sites don't work
- Can't post in certain vB forums; it tells me I don't have enough characters, even when I put in a full message. For some reason, posting on here works.

Any help would be appreciated. I might try compiling Firefox myself to see if that fixes it. But that's supposed to be what packages are for...

---

### Post by jbrown96 on 2009-04-15
> **yarjar said:**
> I think most of the problems have to do with JavaScript. What's odd is that the problems randomly occur, and then stop occurring days later, without me changing any settings. Then, they'll come back again at a random date.

The symptoms are as such:
- Can't log into Facebook; I click the login button and my mouse cursor just sets to waiting, never resolves
- Random JavaScript functions on some sites don't work
- Can't post in certain vB forums; it tells me I don't have enough characters, even when I put in a full message. For some reason, posting on here works.

Any help would be appreciated. I might try compiling Firefox myself to see if that fixes it. But that's supposed to be what packages are for...

You might try to install the official java version if you haven't. I'm not sure of the exact package, but there is a meta-package (package that installs lots of other packages) that installs most of the proprietary stuff one could need (media codecs, flash, java, fonts, etc). Depending on where you live (like the US) this may be illegal because you're supposed to pay for the codecs, so beware, but you can download it with ```
sudo apt-get install ubuntu-restricted-extras
``` You could also try to find the exact java package in Synaptic (System--->Administration). Search for java and install. Make sure to restart firefox.

I doubt compiling firefox would help. Java is a plugin

---

### Post by glotz on 2009-04-15
JavaScript is not Java...

---

### Post by yarjar on 2009-04-15
Lol, problem seems to have gone away overnight. Everything works again. I'll be back in a few days/weeks I guess.

---

