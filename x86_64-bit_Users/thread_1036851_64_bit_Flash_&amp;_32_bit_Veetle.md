---
title: "64 bit Flash &amp; 32 bit Veetle"
date: 2009-01-11
forum: x86 64-bit Users
---

### Post by jonno on 2009-01-11
I had the 32 bit Veetle plugin working on my AMD64 Mythbuntu 8.10 system 0just fine using the instruction described in [this thread]("http://www.veetle.com/forums/viewtopic.php?f=7&t=99").
At the time I had 32bit Flash 10 plugin installed and working fine with nspluginwrapper at the same time.
I then upgraded to the 64 bit Flash 10 alpha and it worked just fine. I think all I did was to put the .so into the ~/.mozilla/plugins directory and remove the flashplugin-nonfree package through Synaptic.

However, now the Veetle plugin no longer seems to work and I get the following errors when opening a Veetle site from Firefox in the terminal:
```
firefox -url http://www.veetle.com/viewChannel.php?cid=48cb03bd8ab18
LoadPlugin: failed to initialize shared library
/home/jonno/.mozilla/plugins/libveetle-core-plugin.so
[/home/jonno/.mozilla/plugins/libveetle-core-plugin.so: wrong ELF class:
ELFCLASS32]
LoadPlugin: failed to initialize shared library
/home/jonno/.mozilla/plugins/libveetle-player-plugin.so
[/home/jonno/.mozilla/plugins/libveetle-player-plugin.so: wrong ELF
class: ELFCLASS32]
LoadPlugin: failed to initialize shared library
/opt/real/RealPlayer/mozilla/nphelix.so
[/opt/real/RealPlayer/mozilla/nphelix.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library
/home/jonno/.mozilla/plugins/libveetle-core-plugin.so
[/home/jonno/.mozilla/plugins/libveetle-core-plugin.so: wrong ELF class:
ELFCLASS32]
LoadPlugin: failed to initialize shared library
/home/jonno/.mozilla/plugins/libveetle-player-plugin.so
[/home/jonno/.mozilla/plugins/libveetle-player-plugin.so: wrong ELF
class: ELFCLASS32]
LoadPlugin: failed to initialize shared library
/opt/real/RealPlayer/mozilla/nphelix.so
[/opt/real/RealPlayer/mozilla/nphelix.so: wrong ELF class: ELFCLASS32]
Waiting on accept...
VLC media player 0.9.11 Janus
Veetle remote control interface initialized. Type `help' for help.
Connecting back to port 50261.
Done!
Reparent: 50331650
parentwin: returned 0 (no error)
```

Does anyone have any idea how to resolve this?

---

