---
title: "Installing hud-lite on Ubuntu x64"
date: 2009-02-20
forum: x86 64-bit Users
---

### Post by knight187 on 2009-02-20
I had a hard time finding information on this so I wanted to post it somewhere so maybe it would help others. For those that don't know hud-lite is a click to dial application for sip accounts connected to asterisk / trixbox phone systems

Install Deps
  sudo apt-get install linux32 ia32* rpm wget

NOTE: I have found with jaunty that installing all the ia32 libs will break your synaptic, I fixed mine by running "apt-get remove ia32-archive" after running the above command.

choose sun java 32bit (ia32)
  sudo update-alternatives --config java

download hud-lite rpm for linux
  wget [http://www.hudlite.org/uploads/hud-lite-1.1.1170-1.i386.rpm](http://www.hudlite.org/uploads/hud-lite-1.1.1170-1.i386.rpm)

install hud-lite
  sudo rpm -ivh --nodeps hud-lite-1.1.1170-1.i386.rpm

run hud-lite
  /usr/fonality/hud-lite/start_HUD.sh

Cheers All.

---

