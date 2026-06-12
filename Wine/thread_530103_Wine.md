---
title: "Wine"
date: 2007-08-20
forum: Wine
---

### Post by mellamopobrede on 2007-08-20
I am following a howto on linuxgamers.net and i cant seem to get past this part.

Change to the location where the WineCVS.sh is lying and start it with:

sh WineCVS.sh

The script downloads with wget a archiv defaults.tar.gz with the need install scripts. After that you should see its installation menu.

Select a profile ... follow the steps...

I dont know how to get the defaults.tar.gz.
It says

poorav@poorav:~$ wget a archiv defaults.tar.gz
--00:22:12--  [http://a/](http://a/)
           => `index.html'
Resolving a... failed: Name or service not known.
--00:22:12--  [http://archiv/](http://archiv/)
           => `index.html'
Resolving archiv... failed: Name or service not known.
--00:22:12--  [http://defaults.tar.gz/](http://defaults.tar.gz/)
           => `index.html'
Resolving defaults.tar.gz... failed: Name or service not known.

FINISHED --00:22:12--
Downloaded: 0 bytes in 0 files

Anyone please help!

---

### Post by Sammi on 2007-08-20
It seems that script is looking for files on the web that it can't find. Either the connection is down or the files are not there.

Can you post a link to the page where the guide is located?

---

### Post by Hairy_Palms on 2007-08-20
link us to the HOWTO, maybe we can help some more,

---

### Post by cogadh on 2007-08-20
Just a silly question, but is there a particular reason you are trying to compile Wine from source? Its really much easier to just install the precompiled binaries.

---

### Post by mellamopobrede on 2007-08-20
I got it to work :)  Thanks for your help guys!

---

### Post by hikaricore on 2007-08-20
Something is seriously wrong with the script.

This:

```
wget a archiv defaults.tar.gz
```

Will never work.  Like ever.  Wget downloads files from servers (websites) and through this command it's being pointed at the following: **a**, **archiv**, and **defaults.tar.gz** which as you can obviously see are not valid hostnames.  O.o

---

### Post by Sammi on 2007-08-20
> **mellamopobrede said:**
> I got it to work :)  Thanks for your help guys!That's great, but come on. You can't just awaken our curiosity, and then not tell us how you fixed it.  It's not fair. I want to know :-k

---

