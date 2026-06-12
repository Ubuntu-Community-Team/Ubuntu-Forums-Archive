---
title: "yahoo messenger on gutsy 64"
date: 2007-12-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by dralokyn on 2007-12-09
generally, i'm happy using pidgin, but i got used to chatting with my family with webcam and voice. pidgin simply isn't up to the task. the official yahoo messenger linux version is very old, and also hasn't been maintained so the dependencies are unresolvable. i saw somewhere that there was a program called gyachi, but i can't resolve its dependencies, either. i'm not set on using the official yahoo messenger, but i would like to know if there are any options that will allow me to use cam and voice. and, you know, i'd prefer native-64 applications, but i'll consider any suggestions. thanks!

---

### Post by loell on 2007-12-10
when you say voice, i bet you mean pc to pc call. kopete and gyachi both offers yahoo webcam function and gyachi's voice chat refers only to public room voice chat which is not ideal for family use, you might wanna consider skype 2 beta for linux.

but what i would  like to recommend is [Mebeam.com]("http://www.mebeam.com") its a flash base voice and webcam chat service, that both you and your family and friends don't even need to register , you are just going to have to agree on the room name to use. or just create your room and give them the invitation link via any IM. :)

---

### Post by VvWolverinevV on 2008-02-22
Is there no way to get into Yahoo! chat rooms on 64-bit Gutsy?

---

### Post by novice599 on 2008-04-17
im a linux newbie , i just followed the guide how to install skype 2.0 on amd64

here [http://ubuntuforums.org/showthread.php?t=474790]("http://ubuntuforums.org/showthread.php?t=474790") and [http://sudan.ubuntuforums.com/showthread.php?t=432295]("http://sudan.ubuntuforums.com/showthread.php?t=432295")

using dpkg force all , getlibs command & some common sense
i was able to install yahoo messenger on my ubuntu gutsy amd64 using this command
download [http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
& ymessenger deb installer
then type 

sudo dpkg -i --force-all skype-install ymessenger_1.0.4.0.1_i386.deb
sudo getlibs /usr/bin/ymessenger

it will ask if you  if you want to continue Y/n ?
choose Y

then when all is done type ymessenger
then i got error like it lacks filename.so.1 

so i use command  getlibs filename.so.1

i kept on typing getlibs filename.*.*

until when i type ymessenger and finally it opens

ill try it over the next couple of days then post again how i installed YM complete with screenshots.. but be warned ym 1.4 is so outdated :(

---

