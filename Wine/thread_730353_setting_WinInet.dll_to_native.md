---
title: "setting WinInet.dll to native"
date: 2008-03-20
forum: Wine
---

### Post by Garmuar on 2008-03-20
I am installing 12 sky for my son on ubuntu using wine.  I Got everything installed and followed these steps posted on wine AppDB:

First you need these DLLs: [http://neocomy.net/files/dlls-12sky.zip](http://neocomy.net/files/dlls-12sky.zip)

Copy both DLLs into your system32 Directory, usually

wget [http://neocomy.net/files/dlls-12sky.zip;unzip](http://neocomy.net/files/dlls-12sky.zip;unzip) dlls-12sky.zip -d ~/.wine/drive_c/windows/system32/;rm dlls-12sky.zip

Now open winecfg Add Launcher.exe and set wininet.dll to native.
	
I did everything except the last line.  I added Launcher.exe in winedfg, but how do you set wininet.dll to native.  I'm not sure I understand what he is talking about.

Thanks.

---

### Post by happyhamster on 2008-03-21
- Under the libraries tab, you can select wininet to load as a native dll (select and choose 'Add', then choose 'Edit' to see the options). Personally I always do it from the terminal like this:

WINEDLLOVERRIDES="wininet.dll=n" wine program.exe

- Or if I want to disable debug-messages:

WINEDEBUG=-all WINEDLLOVERRIDES="wininet.dll=n" wine program.exe

[http://www.winehq.org/site/docs/wineusr-guide/x543#AEN877](http://www.winehq.org/site/docs/wineusr-guide/x543#AEN877)

---

### Post by Garmuar on 2008-03-21
Thanks for the pointers H.H.

I get what he was saying now.

---

### Post by hooah212002 on 2008-04-09
Ok, Ive done everything. I copied the DLL files, set wininet to native, but the game wont even launch....

---

