---
title: "Changing System Language"
date: 2005-08-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by fistfullofroses on 2005-08-25
Is there a way, after an install, with which I can change the language the OS uses? Say from English to French or German?

---

### Post by John Nilsson on 2005-08-26
[QUOTE=fistfullofroses]Is there a way, after an install, with which I can change the language the OS uses? Say from English to French or German?[/QUOTE]

[Here's](https://wiki.ubuntu.com/LocaleConf) one way to do it. Read the locale manpage to understand the LC_* vars.

---

### Post by DancingSun on 2005-08-26
You need to install the locales using LocaleConf, then these locales will be available in the login screen.  Just choose the language that you want to use, then log in.

---

### Post by fistfullofroses on 2005-08-27
Ok... so I did apt-get install localeconf, and asked me if I would like to manage the locales with debconf, and said yes, and then it asked if I would like to replace the config file with the new one... i said yes... and i even went in synaptic and downloaded the language packs i need... but when I went to the GDM login and tried to select the appropriate language... it said the UTF or something like that for the language was not installed... no idea what to do. Normally I had versions of Linux that were issued in my native language... so... help please.

---

### Post by majed on 2005-09-24
look for de_DE locale under /usr/share/i18n/locales

 # find /usr/share/i18n/locales -name de_DE

if it is there, then you need to put it in /etc/environment

 # sudo gedit /etc/environment

and replace file contents with this:

LANGUAGE="de_DE:de"

LANG=de_DE.UTF-8

save the file and reboot (or maybe just logoff and back in..)

Good luck!

majed

---

