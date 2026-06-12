---
title: "How do I unload usb and wireless modules on suspend with 1.2 mhz G4 iBook?"
date: 2006-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by krrh on 2006-01-02
The subject line says it all.  I assume there is a method involving a script to unload modules on suspend and re-load them on resume, but I am unsure where in the system these scripts exist.

Could someone point me in the right direction?  Any help is appreciated.

---

### Post by nicodds on 2006-01-03
[QUOTE=krrh]
Could someone point me in the right direction?  Any help is appreciated.[/QUOTE]

You could take a look to /etc/pbbuntons.conf and its manual page.

Nico

---

### Post by callipeo on 2006-01-03
You may want to create a script like this in /etc/power/scripts.d/:

------------------------------------------------------------------------------------------------------------
#!/bin/sh

# source configuration
. pmcs-config

case "$1" in
  suspend)
      modprobe -r <your_module>
    ;;
  resume)
      modprobe <your_module>
    ;;
esac
--------------------------------------------------------------------------------------------------------

and then link it in /etc/power/event.d/. Take a look at /etc/power/scripts.d/skeleton if you need something more sophisticated.

---

