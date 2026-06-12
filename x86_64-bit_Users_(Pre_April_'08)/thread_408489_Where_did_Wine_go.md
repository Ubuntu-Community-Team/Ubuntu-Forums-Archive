---
title: "Where did Wine go?"
date: 2007-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by SpoZen on 2007-04-13
Hi, i used the application Simple64 and installed Wine, everything went fine ( i think).

The problem is that i can't start wine, it says: exec: 29: /usr/bin/wine: not found

Didn't it install at all? 

Heres the install output: 
```
 Done
Downloading http://ubuntu.secs.oakland.edu/pool/main/libx/libxxf86dga/libxxf86dga1_1.0.0-0ubuntu3_i386.deb ...
 Done
Enabling/Updating Repositories...
 Done
Downloading and Installing Dependencies
Läser paketlistor... Färdig
Bygger beroendeträd         
Reading state information... Färdig
Läser utökad tillståndsinformation      
Initierar pakettillstånd... Färdig  
Bygger taggdatabas... Färdig        
Ingen kandidatversion hittades för lib32asound2
Inga paket kommer att installeras, uppgraderas eller tas bort.
0 paket uppgraderade, 0 nyinstallerade. 0 att ta bort och 0 inte uppgraderade.
Behöver hämta 0B arkiv. Efter uppackning kommer 0B diskplats att användas.
Skriver utökad tillståndsinformation... Färdig
 Done
Installing Wine...
dpkg - varning, ignorerar problem då --force använts:
 paketarkitekturen (i386) matchar inte systemets (amd64)
(Läser databasen ... 106532 filer och kataloger installerade.)
Förbereder att ersätta wine 0.9.34~winehq0~ubuntu~6.10-1 (med .../wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb) ...
Packar upp ersättande wine ...
Ställer in wine (0.9.34~winehq0~ubuntu~6.10-1) ...
ldconfig: /usr/lib32/libXxf86dga.so.1 is not a symbolic link
```

What am i doing wrong? Btw, i am using feisty.

---

### Post by Nechi on 2007-04-13
Hi
I tried to install a certain program on my 64-bit system the other day using Synaptics and I got a message saying something like NEEDS WINE BUT IT'S UNINSTALLABLE, and the installation aborted, so I presume Wine can't be installed on this architecture.

---

### Post by SpoZen on 2007-04-13
> **Nechi said:**
> Hi
I tried to install a certain program on my 64-bit system the other day using Synaptics and I got a message saying something like NEEDS WINE BUT IT'S UNINSTALLABLE, and the installation aborted, so I presume Wine can't be installed on this architecture.

It is an 32bit application, thats why you have to use a script/application to force it to install on a 64bit system.

---

### Post by xopher on 2007-04-13
wine got installed allright, but it tells you it couldn't install lib32asound2, try installing ia32-libs-sdl instead, as it should get lib32asound2 as a dependency. You can also check if wine is installed by: ```
dpkg -l | grep wine
```

Oh, and wine won't work without ia32-libs ;)

---

### Post by SpoZen on 2007-04-13
Thanks, it works now just got a small error when i ran the config, i dont think it makes anydiffrence i got wine desktop working. 

```
err:module:load_builtin_dll failed to load .so lib for builtin L"msxml3.dll": libxslt.so.1: wrong ELF class: ELFCLASS64

```

Thanks again :D !

---

