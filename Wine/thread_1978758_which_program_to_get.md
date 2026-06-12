---
title: "which program to get?"
date: 2012-05-12
forum: Wine
---

### Post by War Tribe on 2012-05-12
I'm trying to decide which software from the ubuntu software center to get in order to install wine on my laptop. the choices are: microsoft windows compatibility lay (meta-package), wine windows program loader and winetricks. i just want to get wine on my laptop because apparently my bank's website does not like chrome for linux or firefox for linux and so i need to install internet explorer (ugh!) or firefox for windows in order to use a feature that is on their website. which package should i get or should i just go to winehq.com and get the package that they offer? thanks!!

---

### Post by MG&amp;TL on 2012-05-12
All of them, IMHO.

Usually one package (I think the packagename is "wine") will install all of these as dependencies.

As it is, I suggest the "meta-package" one. Metapackages exist to automatically install lots of packages.

---

### Post by whatthefunk on 2012-05-12
Install "wine" and youll get everything you need.

---

### Post by houseworkshy on 2012-05-12
If you do put wine in when you open it for the first time you will see that it has access to root ( / ).  I'd recomend removing that.  It's there so it can open a file from anywhere in your system, which may be handy but wine is a good emulator and, especially online, it just as good at catching malware.  It will create a virtual hidden drive in /home anyway called .wine, if you bung installers there and run them from there they'll work fine.  Wine really doesn't need root access to run.

For such important communications I'd be a tad wary of window explorer, haven't used if for years so may be out of date but it used to leak something dreadful.  Try ringing your bank and asking which browsers are compatable, there are many browsers.
[https://en.wikipedia.org/wiki/List_of_web_browsers](https://en.wikipedia.org/wiki/List_of_web_browsers)

---

### Post by whatthefunk on 2012-05-12
> **War Tribe said:**
> i just want to get wine on my laptop because apparently my bank's website does not like chrome for linux or firefox for linux and so i need to install internet explorer (ugh!) or firefox for windows in order to use a feature that is on their website. which package should i get or should i just go to winehq.com and get the package that they offer? thanks!!

Just thought of something else.  With Opera browser, you can edit site preferences so that Opera will tell sites that it is Internet Explorer.  Its worked for me in the past.  Might be worth a try.

---

### Post by oldos2er on 2012-05-12
Moved to Wine.

---

