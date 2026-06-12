---
title: "flash player issues, going from 64bit beta to 32bit"
date: 2008-12-20
forum: x86 64-bit Users
---

### Post by Oblivio_Freak on 2008-12-20
Ok, so basically I've been having a lot of issues with 64-bit flash beta and now places like youtube, the video window just goes blank and wont even load. I'm tired of these issues so I want to install 32-bit flash instead, only I can hardly ever find a place to download it at and then when I finally did find one it told me I couldn't because I have the wrong architecture. And yes I checked to make sure it was .deb  >.<

I don't even know where to start, so I'm open to all advice. Thank you. :)

---

### Post by cariboo on 2008-12-20
First I would suggest that you check to see if you've got the flash plugin installed in the correct place, it should be in /usr/lib/mozilla/plugins, I've been using the plugin since it came out and have had no problems at all.

If you do want to downgrade to the 32bit plugin, make sure you remove the 64bit plugin first, then use either Synaptic or the command line to install the ubuntu-restricted-extras. THis will install the flashplugin-nonfree and it's dependencies.

Jim

---

### Post by Oblivio_Freak on 2008-12-20
> **cariboo907 said:**
> If you do want to downgrade to the 32bit plugin, make sure you remove the 64bit plugin first, then use either Synaptic or the command line to install the ubuntu-restricted-extras. THis will install the flashplugin-nonfree and it's dependencies.

Jim


How do I remove it? I'm a new user to ubuntu so I'm still getting used to the changes in all, also I already have the flashplugin-nonfree.

---

### Post by Vadi on 2008-12-21
Go to your home folder, press ctrl+h, then find a folder "mozilla" and "plugins" inside it. Is there a libflashplayer.so file in it?

---

