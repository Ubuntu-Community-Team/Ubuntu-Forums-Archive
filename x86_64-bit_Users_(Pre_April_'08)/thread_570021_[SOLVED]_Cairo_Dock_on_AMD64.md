---
title: "[SOLVED] Cairo Dock on AMD64?"
date: 2007-10-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by RavanH on 2007-10-07
Has anyone got Cairo Dock running on AMD64?

If so: could you please tell me how / which version / which Ubuntu?

TIA :)
--ravan

EDIT: I'm talking about [http://developer.berlios.de/projects/cairo-dock/](http://developer.berlios.de/projects/cairo-dock/) ... or are there other places to get .deb releases?

---

### Post by Neilguy on 2007-10-27
This might help.
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by fabounet on 2007-10-29
there are no packages for 64bits cause nobody ever made it yet.
maybe you can try with the --force-architecture option of dpkg to force the installation of the 32bits pakage
the other solution is to compile it from the sources.

---

### Post by Inxsible on 2007-10-29
yeah you might have to use the 32 bit. or you can compile from source. I use Avant Window Navigator and I too compiled from source for my 64 bit Gutsy.

---

### Post by RavanH on 2007-11-01
UPDATE:

I failed compiling from source (see [http://developer.berlios.de/forum/message.php?msg_id=40418](http://developer.berlios.de/forum/message.php?msg_id=40418)) so I installed the latest 32bit package with --force-architecture and then copied all the dependencies manually to /usr/lib32/ ....

Tedious work but after that, cairo-dock works FINE :)

It seems installation should be much easier when using getlibs to do the dependencies for you: [http://ubuntuforums.org/showpost.php?p=3674689&postcount=67](http://ubuntuforums.org/showpost.php?p=3674689&postcount=67)

[Getlibs]("http://ubuntuforums.org/showthread.php?t=474790") is surely one of the best AMD64 problem solvers out there!!! [ *It should really be promoted into the repositories and activated by default, I think* ]

--ravan

---

