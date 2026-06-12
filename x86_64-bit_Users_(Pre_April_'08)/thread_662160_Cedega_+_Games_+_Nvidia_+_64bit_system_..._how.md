---
title: "Cedega + Games + Nvidia + 64bit system ... how ?"
date: 2008-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by ODF on 2008-01-08
I did some search ... installed some things. Some people say that i need ia32-libs-sdl so I tried it.

I gave a shot with envy and an other one without it. Well i tryed many things and I think i should consider a 32bit system.

Anybody here is running games with his 64bit system ?

My card is a 8800GTS and I wanted to play games like TF2, Guildwars, Oblivion ... Bioshock ... wich are completely running fast in windows with AI on.

---

### Post by Kilz on 2008-01-08
> **ODF said:**
> I did some search ... installed some things. Some people say that i need ia32-libs-sdl so I tried it.

I gave a shot with envy and an other one without it. Well i tryed many things and I think i should consider a 32bit system.

Anybody here is running games with his 64bit system ?

My card is a 8800GTS and I wanted to play games like TF2, Guildwars, Oblivion ... Bioshock ... wich are completely running fast in windows with AI on.

Cedega is a proprietary application. When you pay for it, part of that payment entitles you to get [support on their forums.]("http://www.cedega.com/forum/") Might as well use it since you paid for it. Cedega does work on 64bit.

---

### Post by Cappy on 2008-01-08
You should install
```
sudo apt-get install ia32-libs libc6-i386 libc6-dev-i386 lib32z1 lib32z1-dev lib32asound2
```

Bioshock doesn't work on wine btw. All of the other games you mentioned do. You can check what you need to run games  on [http://appdb.winehq.org/](http://appdb.winehq.org/)

If you need more help you should mention what the problem is. Running cedega from a terminal will give you an error output if it won't start.
```
./cedega
```
if you change directory to the directory cedega is installed in

---

