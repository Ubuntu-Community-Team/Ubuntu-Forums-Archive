---
title: "koctave launch issues"
date: 2006-09-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by brent09 on 2006-09-24
I've installed koctave and octave2.1 and kdebase through Synaptic.  Octave works properly when launched through the terminal.  But koctave, I have doubts about it.  When I launch koctave through the terminal I get the following:

```
brent@brents-amd:~$ koctave
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file kOctaveui.rc
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file editorui.rc
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file editorui.rc
Uh oh.. can't write data..


```

After all of that koctave does seem to run properly.  I tested basic mathematical and matrix operations and it checks out.  I just want to know what all those error messages are about and what I need to do to eliminate them.

---

### Post by jsgosselin on 2007-04-11
Hi!

I have the same problem. Did you solved the problem since you posted here? Does Koctave wors well anyway if this problem is not solved?

Thanks JS

---

### Post by majestros on 2007-04-24
installing kdebase with synaptic solved my problem, koctave works fine now.  

After I noticed someone posting their error messages from the terminal, I ran it from the terminal and my errors specifically mentioned "do you have kdebase installed correctly?"

After installing kdebase and its associated packages, it works fine.

---

### Post by bjtaylor01 on 2007-10-03
Installed kdebase as well as posted above, everything works fin. 

Note: If you want to use octave2.9 with your koctave you just have to click on settings => Configure Koctave => User path

Should be set to:
/usr/bin/octave

Change to:
/usr/bin/octave2.9

Restart your octave and now it will be working with the 2.9 instead.

---

