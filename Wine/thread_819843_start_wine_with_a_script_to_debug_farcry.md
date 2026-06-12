---
title: "start wine with a script to debug farcry"
date: 2008-06-05
forum: Wine
---

### Post by nutpants on 2008-06-05
in order to run farcry and not have the scroll wheel on the mouse cause a crash i have to ....

 cd FarCry/Bin32
  winedbg FarCry.exe
  Wine-dbg>b *0x37001342
  Wine-dbg>cont



how do i do this from a script so that i dont have to type it in every time?

also the mouse works fine in the menus but does not work in the game itself unless i go to options>>>controls>>>>set defaut each and every time i play the game.. is there a way around this?
thanks for the help..
this is my first game under wine.
ubuntu 8.04
wine 1.0rc3

nutz
(and yes i have been to the winedb site which is where i found the workarounds)

---

### Post by cogadh on 2008-06-05
```
#!/bin/sh
cd ~/.wine/drive_c/Program\ Files/FarCry/Bin32
winedbg FarCry.exe
Wine-dbg>b *0x37001342
Wine-dbg>cont
```

---

### Post by nutpants on 2008-06-05
i tried that with  it changed to match my directory

#!/bin/sh
cd /opt/win/farcry/Bin32
winedbg FarCry.exe
b *0x37001342
cont




 ./dbfarcry 
WineDbg starting on pid 0017
0x7b8773a2: movl	%esi,0x0(%esp)
Wine-dbg>

(which is where it stalls waiting for me to type something)

maybe its possible to echo the info "b *0x37001342" to the prompt"Wine-dbg>"
and then the "cont" command after

but im clueless on how to do it

nutz

---

