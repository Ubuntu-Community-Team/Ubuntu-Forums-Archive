---
title: "compiz is not working because of dbus"
date: 2007-02-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by JvdS45 on 2007-02-26
Hi,

While I try to start compiz i get an message that dbus is not working, while i start compiz i got these message. Compiz is not running. The dbus plugin cannot be activated unless compiz is running.
Do I miss here something because dbus is working but where is that plugin?:( 

thanks if someone can help me :-)

---

### Post by RAOF on 2007-02-26
What version of Compiz (run "compiz --version")?
What is the output of running
```
compiz --replace gconf
```
in a terminal?

---

### Post by dacool25 on 2007-04-12
i'm having the same problem, and when i do that i get > inotify_add_watch: No such file or directory


---

### Post by skoiffman on 2008-03-27
> **dacool25 said:**
> i'm having the same problem, and when i do that i get

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0221 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
Window manager warning: Failed to load theme "ClearlooksAlternative": Failed to find a valid file for theme ClearlooksAlternative

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'CompizSettings_general'


Is there any solution to this....?? I tried reinstalling but no luck....same problem, even if get the manager to work...it wont do anything....

---

### Post by fironfrenzy on 2008-07-18
i have the same problem it worked yesterday even my emerald worked but when i restart i get a message at login about user file ....677. avyways i get this message when i type in --replace gconf. 


Detected PCI ID for VGA: 00:02.0 0300: 8086:2772 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :20.0

i did this yesterday and it seemed to work .

---

