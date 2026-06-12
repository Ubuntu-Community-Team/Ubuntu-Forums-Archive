---
title: "gnome-panel problems."
date: 2005-11-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by tigrez on 2005-11-25
I don't know why, the gnome-panel is crashing every time. I've tried to reinstall panel, data, ecc with apt, but the error is persistent. Launcing in terminal gnome-panel as normal user I have this result:

(gnome-panel:8254): Gtk-CRITICAL **: gtk_icon_theme_lookup_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed

** (gnome-panel:8254): WARNING **: Error in parse: Errore alla riga 30: Il carattere '%' non è valido all'interno di un nome di entità

If I launch gnome-panel as root, I don't have error. I think there is an applet that do something wrong, but I don't installed anything new last time... 
Where I can find the panels configuration? 


This is the last piece of /var/log/user.log

Nov 25 14:01:26 localhost gconfd (tigre-7491): L'indirizzo "xml:readonly:/etc/gconf/gconf.xml.defaults" è stato risolta ad una fonte di configurazione in sola lettura in posizione 3
Nov 25 14:01:26 localhost gconfd (tigre-7491): L'indirizzo "xml:readonly:/usr/share/gconf/local.defaults" è stato risolta ad una fonte di configurazione in sola lettura in posizione 4
Nov 25 14:01:26 localhost gconfd (tigre-7491): L'indirizzo "xml:readonly:/usr/share/gconf/cdd.defaults" è stato risolta ad una fonte di configurazione in sola lettura in posizione 5
Nov 25 14:01:26 localhost gconfd (tigre-7491): L'indirizzo "xml:readonly:/usr/share/gconf/debian.defaults" è stato risolta ad una fonte di configurazione in sola lettura in posizione 6
Nov 25 14:01:26 localhost gconfd (tigre-7491): L'indirizzo "xml:readonly:/var/lib/gconf/defaults" è stato risolta ad una fonte di configurazione in sola lettura in posizione 7
Nov 25 14:01:36 localhost gconfd (tigre-7491): L'indirizzo "xml:readwrite:/home/tigre/.gconf" è stato risolto ad una fonte di configurazione scrivibile in posizione 0
Nov 25 14:12:33 localhost gconfd (root-8420): Inizializzazione (versione 2.12.0), pid 8420, utente 'root'
Nov 25 14:12:33 localhost gconfd (root-8420): L'indirizzo "xml:readonly:/etc/gconf/gconf.xml.mandatory" è stato risolta ad una fonte di configurazione in sola lettura in posizione 0
Nov 25 14:12:33 localhost gconfd (root-8420): L'indirizzo "xml:readonly:/usr/share/gconf/local.mandatory" è stato risolta ad una fonte di configurazione in sola lettura in posizione 1
Nov 25 14:12:33 localhost gconfd (root-8420): L'indirizzo "xml:readwrite:/root/.gconf" è stato risolto ad una fonte di configurazione scrivibile in posizione 2
Nov 25 14:12:33 localhost gconfd (root-8420): L'indirizzo "xml:readonly:/etc/gconf/gconf.xml.defaults" è stato risolta ad una fonte di configurazione in sola lettura in posizione 3
Nov 25 14:12:33 localhost gconfd (root-8420): L'indirizzo "xml:readonly:/usr/share/gconf/local.defaults" è stato risolta ad una fonte di configurazione in sola
lettura in posizione 4
Nov 25 14:12:33 localhost gconfd (root-8420): L'indirizzo "xml:readonly:/usr/share/gconf/cdd.defaults" è stato risolta ad una fonte di configurazione in sola lettura in posizione 5
Nov 25 14:12:33 localhost gconfd (root-8420): L'indirizzo "xml:readonly:/usr/share/gconf/debian.defaults" è stato risolta ad una fonte di configurazione in sola lettura in posizione 6
Nov 25 14:12:33 localhost gconfd (root-8420): L'indirizzo "xml:readonly:/var/lib/gconf/defaults" è stato risolta ad una fonte di configurazione in sola lettura
in posizione 7
Nov 25 14:12:33 localhost gconfd (root-8420): L'indirizzo "xml:readwrite:/root/.gconf" è stato risolto ad una fonte di configurazione scrivibile in posizione 0

"L'indirizzo ... è stato risolto ad una fonte di configurazione scrivibile in posizione .."
Mean: "The address ... is solved in configuration point writable in position ..."
and "in sola lettura" indicate "read-only"

Thanks to all!

---

### Post by aysiu on 2005-11-26
If it works for root but not user, the cleanest way to solve the problem may be to create a new user and use that user instead of the one you originally created (you can copy over a couple of key config files to the new user--email, for example).

---

### Post by tigrez on 2005-11-26
I've create the new user, copied all stuff from old home directory to new home, and it work. Anyway there are some think as firefox stuff that's not copied, where I can find this? And some other gnome configuration?

---

