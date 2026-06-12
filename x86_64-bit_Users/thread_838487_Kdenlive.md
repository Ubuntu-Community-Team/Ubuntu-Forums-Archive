---
title: "Kdenlive"
date: 2008-06-23
forum: x86 64-bit Users
---

### Post by Ataris on 2008-06-23
I've downloaded the Kdelive source, but I noticed that you need three other programs for it to run, K3B, dvdauthor, and Xine. I downloaded the dvdauthor source, but I don't know how to get the QT library or the other requirements for K3b, and I don't understand how to get Xine either.

Can someone please give me a SIMPLE (NOT the wiki) guide on how to install Kdenlive for Ubuntu 8.04. I am SO confused.

PS

If the other programs for Kdenlive aren't necessary, I don't want them, because I won't be using DVDs with my work.

---

### Post by pixel :-) on 2008-06-23
sudo apt-get install kdenlive

be aware that if you are under gnome,it will download a tone of libraries.Also be warned that this program is still very crachy.

If you really whant to compile it your self that's an other story.

---

### Post by Ataris on 2008-06-23
How big are the libraries in question here? I have dialup internet.

---

### Post by pixel :-) on 2008-06-23
i don't know how big,it must be tens of megabites.

apt-get, tells you what extra stuff it will download and there total size ,and asks you if you want to proceed.You can stop the download with "ctl+c".If you rerun the above command, it will take in to account what's already downloaded, including partial downloads.So you can spread the download over time,no need to download all at once.

These are core kde libraries,so if you install other kde apps,they will be a lot thiner installs, because a lot of dependencies will be already satisfied.

---

### Post by kuja on 2008-06-24
> **Ataris said:**
> How big are the libraries in question here? I have dialup internet.

Probably big enough to take you a few nights, easy.

If you're still interested in compiling from source, I'd recommend reading this: [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

Afterwards, make sure you have the source repositories turned on in your sources.list, update, and make good use of the "apt-get build-dep" command, which fetches build dependencies for applications that have a source package in the repository. ie: to get the build deps for k3b, you would "sudo apt-get build-dep k3b". 

If when compiling it complains about a missing library, make use of the apt-file command (sudo apt-get install apt-file if you don't have it) to figure out what package has it and get it, if it wasn't obvious by the filename (generally searching for the plaintext of the filename gives you good results, then you just install the -dev package that looks like a good candidate and see).

Wow, that was a lot of typing, hope it was worth my time :)

---

### Post by Ataris on 2008-06-24
Thanks guys, that helped a lot.

---

