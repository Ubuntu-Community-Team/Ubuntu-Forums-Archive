---
title: "PyLOTRO error"
date: 2011-12-21
forum: Wine
---

### Post by gardengxc on 2011-12-21
I installed pylotro and lord of the rings online but when I run it I get the following errors,

err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Turbine\\The Lord of the Rings Online\\lotroclient.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Turbine\\The Lord of the Rings Online\\lotroclient.exe" failed, status c0000135

I've re-installed it and patched it but the same errors persist.

---

### Post by ergo-proxy on 2011-12-21
Make sure pylotro recognized your lotro installation.

---

### Post by gardengxc on 2011-12-21
ok I just updated wine to 1.3 and now I've got a black screen.

new error 

err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xf74a30a6
wine client error:9: write: Bad file descriptor

---

### Post by Faffin on 2011-12-21
Have you installed directX and visual c with winetricks? Have you installed the vendor drivers for your video card?

---

### Post by gardengxc on 2011-12-22
No on direct x and c yes on drivers

just as a note My graphics card is a EVGA GeForce 8600 gts.

---

### Post by Faffin on 2011-12-23
[http://lorebook.lotro.com/wiki/LOTRO_under_Linux_and_Mac_OS/X](http://lorebook.lotro.com/wiki/LOTRO_under_Linux_and_Mac_OS/X)

You need directx & c. Link to guide above.

---

### Post by gardengxc on 2011-12-23
Still a black screen but no more errors printed out.

I'm going to try something if I can figure out how. TF2 gave me some problems till I with it in directx 8.

Edit: not an option

---

