---
title: "Picasa for Linux + SimpleViewer problem (some access restrictions)"
date: 2008-08-04
forum: Wine
---

### Post by blashyrkh on 2008-08-04
Hey

Downloaded Picasa for Linux, and installed it with no problems. 
Downloaded SimpleViewer XML script (it is to be copied into a folde called web/templates in the Picasa folder), but it's here I ran into trouble.

It turns out that Picasa for Linux, installs Wine by it self but in it's own folder (.Picasa), and I can't access the folder where I'm supposed to put my templates.

I tried the command:

```
$ sudo chown -R myname:myname .picasa
```

I got some luck, I can now insert my templates into the .Picasa folder, but I still have no access to the sub-folder /web/templates 

I tried ```
sudo chown -R myname:myname .picasa/drive_c/Program Files/Picasa2/web/templates
``` with no luck :confused:

anyone got a suggestion to solve this?

NOTE: I did the first command on .wine and can copy into every directory there with no problems. seems odd to me.

---

### Post by gjoellee on 2008-08-04
I am no expert at this, but you can try this:
```
 gksudo chown -R myname:myname .picasa 
```
or do it as root:
```
su -
```
```
 gksudo chown -R myname:myname .picasa 
```

---

### Post by blashyrkh on 2008-08-05
> **gjoellee said:**
> I am no expert at this, but you can try this:
```
 gksudo chown -R myname:myname .picasa 
```
or do it as root:
```
su -
```
```
 gksudo chown -R myname:myname .picasa 
```

No that didn't help, I get an "invalid option" og gksudo and "Authentication failure" on the su part :(

---

### Post by marco500 on 2008-10-27
Hi, i just managed to copy the simple viewer template to the picasa directory. 
i became su by way of:

```
sudo su 
```

and changed the ownership of the templates folder, then i just pasted the new template into that folder, it worked nicely. don't forget to exit the su mode

---

