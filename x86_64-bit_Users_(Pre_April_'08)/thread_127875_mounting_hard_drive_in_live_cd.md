---
title: "mounting hard drive in live cd"
date: 2006-02-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by crakkajakka15 on 2006-02-10
hey whats up first time poster and newlinux user. heres my issue i mounted my mac hard drive "hda3" now my issue is that i want to listen to my itunes music but everytime i click on the folder where they are stored it says i dont have permission to acces them, is there a way around this......please help
thanks
Todd

---

### Post by ssam on 2006-02-10
i think the easiest way is to boot into mac os x. do get info on you music folder. go to the permission section, and make sure anyone can read them. then click the apply to subfolders (i can't remeber the exact name of it) button.

you next problem may be getting them to play in ubuntu. unless they are all in ogg or wave format you'll need to install a codec. it think you need gstreamer0.8-mad for mp3 and gstreamer0.8-faad for aac. you can install them from synaptic. see [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) for more details

---

