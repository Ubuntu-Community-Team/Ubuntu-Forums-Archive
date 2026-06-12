---
title: "apt-get?"
date: 2005-09-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tux_army on 2005-09-01
I'm not really familiar with this feature SUSE had it but i've never used it. 

Anyways i tried using apt-get to get gstreamer0.8-mad, i've google quite a bit and i've found that i need gstreamer0.8-mad to get mp3 support. However, everytime i try to use apt-get to get gstreamer0.8-mad i always get this message
> 
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer0.8-mad

So where else can i get it? I even tried using the Ubuntu official guide and tried getting apt-get install gstreamer0.8-plugin but i get the same message for every software that i tried to use apt-get.

Does Ubuntu have an official webpage for it's softwares? that way i can probably use wget instead.

Thanks in advance!

---

### Post by Kuolio on 2005-09-01
Check out ubuntu wiki, here is a quick link to restricted formats on wiki: [RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) 


Be sure to read through: [wiki user documentation](https://wiki.ubuntu.com/UserDocumentation)

---

### Post by izmaelis on 2005-09-01
There are no right ropesitories listed in you /etc/apt/sources.list.
Check [Ubuntu Guide](http://ubuntuguide.org) about how to add extra repositories.

---

### Post by DJ_Max on 2005-09-01
[QUOTE=Tux_army]I'm not really familiar with this feature SUSE had it but i've never used it. 

Anyways i tried using apt-get to get gstreamer0.8-mad, i've google quite a bit and i've found that i need gstreamer0.8-mad to get mp3 support. However, everytime i try to use apt-get to get gstreamer0.8-mad i always get this message


So where else can i get it? I even tried using the Ubuntu official guide and tried getting apt-get install gstreamer0.8-plugin but i get the same message for every software that i tried to use apt-get.

Does Ubuntu have an official webpage for it's softwares? that way i can probably use wget instead.

Thanks in advance![/QUOTE]
 You wouldn't be able to use wget, wget will just download the file. It won't update your database, calculate dependencies, etc..
gstreamer0.8-mad is in the universe, make sure you have it enabled. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by Tux_army on 2005-09-01
Thanks for the tips and links - that work out perfectly.
 
Now off to try and get my sound working.

---

