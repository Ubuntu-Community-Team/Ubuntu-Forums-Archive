---
title: "Divx Video"
date: 2005-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by vital_101 on 2005-10-26
I'm a relative newbie to ubuntu, and I have a question or two. 

I download some shows that I like to watch off of the internet via bit torrent.  They are in an AVI format (it's divx).  I tried to open the file in Kaffiene and Totem, but it wouldn't open.  I'm assuming I need the proper codecs installed, but I have no clue about where to get them or how to install them.  If someone could give me the step by step process I need to get this working, that would be greatly appreciated.

---

### Post by JuanC on 2005-10-26
Try [VLC](http://www.videolan.org)

---

### Post by vital_101 on 2005-10-26
I get this after I add the proper repositories to sources.list

Failed to fetch [http://download.videolan.org/pub/videolan/debian/dists/sarge/main/binary-amd64/Packages.gz](http://download.videolan.org/pub/videolan/debian/dists/sarge/main/binary-amd64/Packages.gz)  404 Not Found [IP: 138.195.130.74 80]
Reading package lists... Done
W: Couldn't stat source package list [http://download.videolan.org](http://download.videolan.org) sarge/main Packages (/var/lib/apt/lists/download.videolan.org_pub_videolan_debian_dists_sarge_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by tehwa on 2005-10-26
Make sure you have all the required codecs.

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies)

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

These wont require you to change your repos. 

For straightforward information on these things, the first link is gold, gold I tells ya.

---

### Post by tehwa on 2005-10-26
Also, VLC is in the repositories (graphics::universe). You should be able to search for it in Synaptic with the standard Ubuntu repos enabled.

See [http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

---

### Post by snowjunkie on 2005-10-26
[QUOTE=tehwa]Also, VLC is in the repositories (graphics::universe). You should be able to search for it in Synaptic with the standard Ubuntu repos enabled.[/QUOTE]

Are you able to install it along side Totem without any problems?

---

### Post by vital_101 on 2005-10-26
all problems fixed.  Thanks everyone

---

