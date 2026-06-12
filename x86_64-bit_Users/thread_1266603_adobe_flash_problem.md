---
title: "adobe flash problem"
date: 2009-09-14
forum: x86 64-bit Users
---

### Post by tony06 on 2009-09-14
after i upgrade firefox 3.0.14 to 3.5.3 in ubuntu 9.04 x 64 firefox cheap telling my that i must instal adobe but in provius version adobe flash it was working and anador problem seems that after i upgrade firefox the defult programs in ubuntu ar chenged how can i get back ubuntu programs default with firefox 3.5 exeption? sorry for my bad english but pls i need help i am noob in ubuntu switched from windows

---

### Post by scrooge_74 on 2009-09-14
check the plugins directories, most likely the new version points its plugin directory to a different place which makes it not find flash

---

### Post by tony06 on 2009-09-14
> **scrooge_74 said:**
> check the plugins directories, most likely the new version points its plugin directory to a different place which makes it not find flash
      how i do that?

---

### Post by scrooge_74 on 2009-09-14
My case, so you can use as guide, Im using Debian 5.0 so my browser is iceweasel (firefox under another name), plugins are in:

/usr/lib/iceweasel/plugins

files there are just links to real files somewhere else

in old firefox installs you had to manually link stuff (example java)

so you could go check if there is a /usr/lib/firefox-version/plugins and if you have directories for the old and new version you may find that the new version dont have the links
you could then copy and put them in the correct place

---

### Post by tony06 on 2009-09-14
> **scrooge_74 said:**
> My case, so you can use as guide, Im using Debian 5.0 so my browser is iceweasel (firefox under another name), plugins are in:

/usr/lib/iceweasel/plugins

files there are just links to real files somewhere else

in old firefox installs you had to manually link stuff (example java)

so you could go check if there is a /usr/lib/firefox-version/plugins and if you have directories for the old and new version you may find that the new version dont have the links
you could then copy and put them in the correct place
   in /usr/lib/ no firefox-version/plugins folder or directories :confused:

---

### Post by scrooge_74 on 2009-09-14
try to uninstall and reinstall flash, I think that will be faster

---

### Post by tony06 on 2009-09-14
> **scrooge_74 said:**
> try to uninstall and reinstall flash, I think that will be faster
I just installed flashplugin-nonfree via synaptic and it  didn't work

---

### Post by tony06 on 2009-09-15
any suggestion??

---

### Post by tony06 on 2009-09-15
this is the comand line i used what i do wrong  ???   if [[ ! -f /usr/bin/firefox ]]; then sudo apt-get update && sudo apt-get install firefox; fi && if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox

---

### Post by scrooge_74 on 2009-09-15
you never removed the original one from what I can see and you moved the pluggins and a few other stuff.

I dont know but I would just go and remove all stuff and start all over again

---

### Post by michael37 on 2009-09-15
Try to remove package flashplugin-nonfree and install package flashplugin-installer from multiverse.

P.S. Works well for 32-bit, consult [thread="1259102"]64-bit board for 64-bit solutions[/thread].

---

### Post by tony06 on 2009-09-16
any suggestion?? pls help

---

### Post by scrooge_74 on 2009-09-16
If Im not mistaken the flash 32 bit from Adobe website works I read somewhere the 32 bit works on 64 and I know it does cause I have a friend running 64 bit and we installed flash on that one

---

### Post by bosbeemer on 2009-09-16
> **tony06 said:**
> how i do that?
The plugins directory is in two places.

1. your home directory $HOME/.mozilla/plugins
2. /usr/lib/mozilla-firefox/plugins

You can also check .. 
/usr/lib/mozilla/plugins

btw, go to [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) to get flashplayer for 64 bit Ubuntu. This would only work if you are running 64 bit firefox though.

---

### Post by tony06 on 2009-09-18
i manage to go back to 3.0.14   sudo rm /usr/bin/firefox && sudo dpkg-divert --rename --remove /usr/bin/firefox && sudo rm -r /opt/firefox thx all for all suggestion

---

