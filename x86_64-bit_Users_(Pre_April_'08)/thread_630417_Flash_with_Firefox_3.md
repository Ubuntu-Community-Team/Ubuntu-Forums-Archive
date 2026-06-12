---
title: "Flash with Firefox 3"
date: 2007-12-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Corey on 2007-12-03
I got firefox v3.0a8 from the repoes. It won't however play flash. I've previously installed flash for firefox 2 with no trouble. How can I get Gran Paradiso to play flash too?

Thanks,
Corey

---

### Post by sirdilznik on 2007-12-03
Have you tried reinstalling flashplugin-nonfree afterwards?

If that fails you may have to make to link to the flash plugin yourself, manually.

---

### Post by Corey on 2007-12-03
Yeah I tried that. No dice :( How would I go about manually linking it?

---

### Post by sirdilznik on 2007-12-03
Hmmm....  I haven't had to manually link plugins in ubuntu before, but browsing through the directories I see a link: /usr/lib/firefox/plugins/flashplugin-alternative.so that links to /etc/alternatives/firefox-flashplugin (which in turn links to another file).  You would need to set up something just like that but in the plugins directory of your gran paridiso install (wherever that is, I don't have it installed)

---

### Post by ExBuM on 2007-12-03
> **sirdilznik said:**
> Hmmm....  I haven't had to manually link plugins in ubuntu before, but browsing through the directories I see a link: /usr/lib/firefox/plugins/flashplugin-alternative.so that links to /etc/alternatives/firefox-flashplugin (which in turn links to another file).  You would need to set up something just like that but in the plugins directory of your gran paridiso install (wherever that is, I don't have it installed)

I'm having the same issue as well. How do you link those plugins?

---

### Post by sirdilznik on 2007-12-03
> **ExBuM said:**
> I'm having the same issue as well. How do you link those plugins?

Open up a file manager to the source directory (where the plugin you are linking to is located) and either a split view or another instance of the file manager to the directory where you want to link to.  Drag the file from one to the other.  I use ROX-Filer and in Rox when I drag the file a popup comes up asking whether I want to move, copy, or link the file.  I haven't used konqueror or nautilus for some time (I stay away form nautilus like the plague), but I'm sure they have similar functionality.

Edit:  The file managers opened will have to have root privileges thus you will need to use sudo to open them.  ie:
```
sudo rox
```

---

### Post by utUtu on 2007-12-03
> **ExBuM said:**
> I'm having the same issue as well. How do you link those plugins?

open up a terminal

cd to where your gran-paradiso plugins directory is.  I'm guessing it should be /usr/lib/grand-something/plugins
Then at the command line

sudo ln -s /usr/lib/firefox/plugins/* .  <<= that's a period after the space

that's it.

Open your browser, and then at the url, type about:plugins
That would show all of your plugins
Then finally go to youtube.com, and enjoy

:guitar:


the about':'plugins above shud be 'about' + colon + 'plugins'.  Looks like the forum mistook it ':p' to be a smiley.

---

### Post by ExBuM on 2007-12-04
I got it to work by copying the plugins folder over to firefox-3.0 :]

---

### Post by sirdilznik on 2007-12-04
> **ExBuM said:**
> I got it to work by copying the plugins folder over to firefox-3.0 :]

Not the cleanest solution, but I'm glad it worked for you.:cool:

---

### Post by uBeer on 2008-01-06
> **utUtu said:**
> open up a terminal

cd to where your gran-paradiso plugins directory is.  I'm guessing it should be /usr/lib/grand-something/plugins
Then at the command line

sudo ln -s /usr/lib/firefox/plugins/* .  <<= that's a period after the space

that's it.

Open your browser, and then at the url, type about:plugins
That would show all of your plugins
Then finally go to youtube.com, and enjoy

:guitar:


the about':'plugins above shud be 'about' + colon + 'plugins'.  Looks like the forum mistook it ':p' to be a smiley.

The folder to browse to is actually /usr/lib/firefox-3.0/
In there you can make a folder 'plugins' and then cd to it and execute the command above. Worked fine for me!
Thanks a lot!

---

