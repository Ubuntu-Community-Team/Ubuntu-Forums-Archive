---
title: "need help with a game in wine please..."
date: 2008-05-03
forum: Wine
---

### Post by amyfan on 2008-05-03
every time i play Deus Ex in wine when i close the game and restart it a while later it goes super fast how can i fix this from doing that?



im running 64bit gnome hardy and wine .60

---

### Post by sweldon on 2008-05-03
try to change you FPS ratio it should slow down the game, but I personnally don't know how to do it but I think it is under you video card driver settings.

---

### Post by amyfan on 2008-05-03
i see screen resolution but it is as low as it can go..

---

### Post by sweldon on 2008-05-03
what video card are you using? The FPS is frame per second not resolution. This is normally the thing you need to change in order to speeed up / slow down any game.

---

### Post by amyfan on 2008-05-03
not exactly sure how or where to find what vid card i got but i did this in term i hope it helps you some...
```
:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

```

---

### Post by sweldon on 2008-05-03
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)
try checkin your redgistry using this guide above . to access your registry go to terminal and enter this
sudo wine regedit

---

### Post by amyfan on 2008-05-03
the link u gave me im kind of lost on it. 
no idea how to do all that but here is outlook of the sudo wine regedit
```
:~$ sudo wine regedit
wine: /home/doug/.wine is not owned by you

```

---

### Post by sweldon on 2008-05-03
> **amyfan said:**
> the link u gave me im kind of lost on it. 
no idea how to do all that but here is outlook of the sudo wine regedit
```
:~$ sudo wine regedit
wine: /home/doug/.wine is not owned by you

```

try this method 
enter this into terminal
su
"then your password "
"then"
wine regedit

---

### Post by amyfan on 2008-05-03
when i do "su" in term i get ```
su: Authentication failure

``` after i enter the password....

---

### Post by amyfan on 2008-05-03
i did do this sudo -i that made me root@doung:~$wine regedit
```
wine: created the configuration directory '/root/.wine'
Could not load Mozilla. HTML rendering will be disabled.
wine: configuration in '/root/.wine' has been updated.


```


i have the box opened now what do i look up in it or do in the box....

---

### Post by sweldon on 2008-05-03
> **amyfan said:**
> i did do this sudo -i that made me root@doung:~$wine regedit
```
wine: created the configuration directory '/root/.wine'
Could not load Mozilla. HTML rendering will be disabled.
wine: configuration in '/root/.wine' has been updated.


```


i have the box opened now what do i look up in it or do in the box....

make sure  registry looks normal then exit it and in terminal enter  :
wineprefixcreate
then reboot and try the game again

---

### Post by amyfan on 2008-05-03
in the box on the right it sayes "value not set"

---

### Post by amyfan on 2008-05-03
i done what you said and now i get this error when i try to load the game.....

---

### Post by amyfan on 2008-05-03
and my other game hangs in a black screen in wine........ i hear music if i move mouse around i can hear the noise of the mouse moving over stuff...

---

### Post by sweldon on 2008-05-03
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3775](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3775)
read the bottom of this page it will help ^

---

### Post by amyfan on 2008-05-03
hmm ok so where do i find a .deb of wine .15? and will it fix the last error i got?

---

### Post by amyfan on 2008-05-03
ok i installed .36 is the farthest i can go back in amd64bit and it still installed .61 everything was working almost fine till u gave me that code to type then it all messed up..

---

### Post by ajackson on 2008-05-04
> **sweldon said:**
> sudo wine regedit
DO NOT DO THIS.

There is no need to run wine as root, until very recently even the wine devs said it was a bad thing (now they are of mixed opinions).

To run regedit all you need to type in a terminal is
```
regedit
```

---

### Post by amyfan on 2008-05-04
what exactly am i supposed to do with the sudo wine regedit
then the regedit code  ?

---

### Post by amyfan on 2008-05-04
i have tried to remove wine .61 i had compiled but the code i do it sayes blah blah cant remove wine and now i have no folder to cd into with wine.61 but it is still installed on my computer .....

---

### Post by amyfan on 2008-05-06
ok i fixed the wine prob by duel booting with xp home for gaming only .

---

