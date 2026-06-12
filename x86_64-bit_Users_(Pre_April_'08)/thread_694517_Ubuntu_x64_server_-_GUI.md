---
title: "Ubuntu x64 server - GUI?"
date: 2008-02-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by bigbro on 2008-02-12
Hello.

I am using ubuntu server x64 7.10, but can't get GUI for it... becouse it's more easy for me to manage my server with GUI.
With i386 ubuntu server version 7.10 I've manage to get xubuntu-desktop with 'apt-get xubuntu-desktop' and it's working fine, but in x64 bit version I can't find it.
I use:

apt-get install ubuntu-desktop
apt-get install xubuntu-desktop
apt-get install xubntu-desktop
apt-get install kde

but it said that can't find it. 
I am new in linux. 
Any solutions? 

Thanks in advance.

---

### Post by Kilz on 2008-02-12
That meta package is available. A meta package is one that pulls other packages, so just downloading it wont solve your issue. I have a feeling that your /etc/apt/sources.list needs to be edited to enable the repositories. Right now I bet its pulling from the cd, it will ask that you install the cd when you go to install things. But since the server disk doesn't have a desktop package there is nothing to pull.
Use 
```
sudo nano /etc/apt/sources.list
``` to edit the file. Remove the # from lines that start with deb like this
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
save the file, then ```
sudo apt-get update
```
Then try
apt-get install xubuntu-desktop

But if you only use the desktop a little consider using icewm as a desktop. Its real low on resource use and has a lot going for it. Its what I use on my server.
[This link is for low memory systems]("https://help.ubuntu.com/community/Installation/LowMemorySystems"), but it has good instructions. [This page will help]("https://help.ubuntu.com/community/IceWM") install rox, the filer.

---

### Post by ptn107 on 2008-02-12
Installing the [k,x]ubuntu-desktop metapackages is overkill for just a gui on the server.  A better alternative is just installing theses components (you don't need all the desktop software those metapackages pull in).

```
sudo apt-get install xserver-xorg xfonts* gnome
```

---

### Post by ikonia on 2008-02-12
if you wanted a desktop gui - why install the server version, the desktop version works just as good for hosting server based services.

---

### Post by Kilz on 2008-02-12
> **ikonia said:**
> if you wanted a desktop gui - why install the server version, the desktop version works just as good for hosting server based services.

The thing is, for a server, a Desktop install is a HUGE waste of resources. They eat up ram and hard drive space. A server is mainly used to serve or offer content to other computers. I have a small server, it has a desktop, but it uses Icewm and I dont have the desktop on unless I am using it. Gnome or KDE would be a huge waste.

---

