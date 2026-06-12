---
title: "How2: Install wine in one step (+info)"
date: 2007-11-26
forum: Wine
---

### Post by Sockerdrickan on 2007-11-26
Hi everyone, this is how to install WINE in one step:

Don't know if you are using 32bit or 64bit Ubuntu?
{
    1. Do a uname -m in a terminal
    2. a) If it returns i686 you should go with 32BIT WINE 
    2. b) If it returns x86_64 you should go with 64BIT WINE
}

Get the deb file for your Ubuntu version / processor type
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
When you got the file, double click it and press install!
Congratulations. You have WINE and can now run winecfg in a terminal to set up some basic options.

Latest version is 0.9.49

Bye!
:guitar:

---

### Post by machoo02 on 2007-11-26
Or...you could just add the WineHQ repository following the instructions [here]("http://winehq.org/site/download-deb"), and always have the latest and greatest version of Wine as soon as it's ready!

---

### Post by Sockerdrickan on 2007-11-26
Yes that can be done too, but it's nowhere near the ease of just clicking a deb
*aah*

---

### Post by t3h_h4ck3r on 2007-11-26
WHAT IF YOU DONT HAVE INTERNET ON YOUR LINUX MACHINE?!?!?!?!? i am running Gutsy 7.10 and I downloaded wine onto my7 uncles winxp computer and put in on a jumpdrive and brought it to my linux machine. I know to try to run the wineinstall tool but it keeps opening as a text file?! How do I make it *not do this!?*

---

### Post by Sockerdrickan on 2007-11-26
You download the deb file as a I said and open it with a double click!

---

### Post by karth on 2007-11-27
You should at least specify why a .deb file "opens and installs by itself" when double-clicked; the system has to know which app to use to achieve that.

In Ubuntu it's dpkg, and it's GUI Gdebi, but for some reason, the association with .deb files and Gdebi might be broken on some systems: previous messing with apps, repos, specific system changes, etc...

Therefore, if Ubuntu refuses to recognize any type of file, one should check which app was designed to handle it (if there was one), and check if that association is correctly setup in the linux box.

As for a personnal note, it becomes a lot more tricky when there's no internet. Nowadays, so many things are so tightly related to the network... You'll have to be brave :)

---

