---
title: "Root Question Newer to ubuntu"
date: 2009-08-15
forum: x86 64-bit Users
---

### Post by xinjiapo2703 on 2009-08-15
Read lots and lots of post as I am using the amd64 system and I am having problems with firefox, (going away from video and coming back and its grayed out), and opera(where it plays sound but not video). 

now i have read through most of the tutorials but when i utilise the command gksudo nautilus command to get into root, it shows me the root folder but it only allows me a link to the desktop. so when i go and click to the folder system i am no longer in root any more as i try to overwrite the plugin file for mozilla/opera and it says I do not have access.

I have searched for the answer and believe i have found out how to do it but since no tutorial addresses the issue I am having, this is why I must ask.

Thank you

---

### Post by Philotus on 2009-08-15
I'm not entirely sure why your root access through nautilus isn't working. 
What version of flash are you using? The 64 bit alpha from adobe or the 32bit version from the repositories (which work through the ndiswrapper)?

Maybe now is a good time to explore the file system using bash commands?```

# Refresh your location tool
sudo updatedb
# Then locate your flash plugin
locate libflashplayer.so

```

---

### Post by grappler on 2009-08-15
If you just want to watch video, the latest version of firefox (3.5) has inbuilt video support without the use of a flash plugin. 

[http://lifehacker.com/5306169/install-firefox-35-on-ubuntu-with-one-command](http://lifehacker.com/5306169/install-firefox-35-on-ubuntu-with-one-command)

---

### Post by Philotus on 2009-08-15
Hey Grappler,
I'm pretty sure the Firefox 3.5 video support is through html5 and doesn't include flash (just Ogg Theora, Ogg Vorbis, and WAV format media when embedded appropriately).

I don't think there are many websites that have gone this route yet, but we can hope!

---

