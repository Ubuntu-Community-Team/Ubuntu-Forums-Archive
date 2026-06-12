---
title: "Path of Exile failed to call WineMenuBuilder.exe"
date: 2012-01-18
forum: Wine
---

### Post by kanazky on 2012-01-18
Ubuntu 12.04
FGLRX - Catalyst 11.12-2
Unity Desktop - AwesomeWM

Pastebin: [http://pastebin.com/38PPrfXk](http://pastebin.com/38PPrfXk)

Launched by: wine / playonlinux

installed packages: Dx9, Dx11, vc2008 vc2005

Err: 

> 
[POL_Wine] Message: Running wine-1.3.37 Client.exe
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
err:wineboot:ProcessRunKeys Error running cmd L"C:\\windows\\system32\\winemenubuilder.exe -a -r" (2)
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
err:seh:raise_exception Unhandled exception code e0000001 flags 0 addr 0x7b83b362
[POL_Wine] Message: Wine return: 1


Anyone have any ideas?

---

### Post by Kevin McCready on 2012-07-10
I had similar problem and solved it by find the program in my folders, then 
right-click on it, choose "Run with", and choose "Wine".

---

