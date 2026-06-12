---
title: "[SOLVED] Rhythmbox, gnome-games-data Errors"
date: 2008-10-18
forum: x86 64-bit Users
---

### Post by chrism66 on 2008-10-18
All right for the last several months every time I run synaptic, I get the following error message. Anyone have a clue on how to resolve these issues? Tried un-installing these packages but it does not allow me to do it.

[PHP]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gnome-games-data (1:2.22.3-0ubuntu2) ...
Warning: /usr/share/gconf/schemas/aisleriot.schemas could not be found.
Warning: /usr/share/gconf/schemas/blackjack.schemas could not be found.
Warning: /usr/share/gconf/schemas/glchess.schemas could not be found.
Warning: /usr/share/gconf/schemas/glines.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnect.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnibbles.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnobots2.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnometris.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnomine.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnotravex.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnotski.schemas could not be found.
Warning: /usr/share/gconf/schemas/gtali.schemas could not be found.
Warning: /usr/share/gconf/schemas/iagno.schemas could not be found.
Warning: /usr/share/gconf/schemas/mahjongg.schemas could not be found.
Warning: /usr/share/gconf/schemas/same-gnome.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing gnome-games-data (--configure):
 subprocess post-installation script returned error exit status 2
Setting up rhythmbox (0.11.5-0ubuntu8) ...
Warning: /usr/share/gconf/schemas/rhythmbox.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing rhythmbox (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 gnome-games-data
 rhythmbox
E: Sub-process /usr/bin/dpkg returned an error code (1)[/PHP]

---

### Post by chrism66 on 2008-10-18
Found resolution [here]("http://ubuntuforums.org/showthread.php?t=872174&highlight=gconf-schemas%3A+error%3A+file+(un)register.")

---

