---
title: "Flash Player = DEAD"
date: 2009-03-24
forum: x86 64-bit Users
---

### Post by Hydrothrax on 2009-03-24
Flash player 10 DIED on me about a week ago, and only showed a blank, white screen. I've tried every method of reinstalling/fixing/etc. of Flash Player 10 I could find, but to no avail! It's driving me nuts! Any help would be appreciated :)

Note: I run Ubuntu 8.10 64-bit

---

### Post by cariboo on 2009-03-24
How did you install Flash? I would suggest downloading flash from [here]("http://labs.adobe.com/downloads/flashplayer10.html"). Next extract it by double-clickin the fil you just downloaded. Make sure you remove libflashplayer.so from /usr/lib/mozilla/plugins, then copy the new file to that location. For me the easiest way is in a terminal, but you can use nautilus to accomplish the same thing. Press Alt-F2 and type:

```
gksu nautilus
```

The above command will start the file manager as root allow you to delete and copy files to directories you don't have permissions for.

Jim

---

### Post by lavinog on 2009-03-24
uninstall flash before installing the 64bit alpha

The problem you are experiencing should be fixed by what cariboo907 said.
Even though it is in the alpha stage, I have found it to be a huge improvement over the 32bit flash that comes with ubuntu.
here is a thread that goes into more detail:
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by Hydrothrax on 2009-03-25
I reinstalled Flash this time with the scripts [of course after uninstalling it again] but still nothing.

I'm starting to think that the problem isn't flash, but firefox/swiftfox. Is it possible that my browser isn't recognizing Flash 10 anymore?

---

### Post by Yellow Pasque on 2009-03-25
Enter about:plugins in the URL bar to see whether firefox recognizes Flash.
Another trick is to start firefox in the terminal and navigate to a site with Flash content. If there are errors, firefox should spit out detailed output in the terminal.

---

### Post by jeegiz on 2009-03-25
what is your libasound2 version? I had similar issues with libasound2 newer version installed from some ppa repository. 

My issue was solved by reverting to 1.0.17 libasound2 version.

---

### Post by lavinog on 2009-03-26
> **Hydrothrax said:**
> I reinstalled Flash this time with the scripts [of course after uninstalling it again] but still nothing.

I'm starting to think that the problem isn't flash, but firefox/swiftfox. Is it possible that my browser isn't recognizing Flash 10 anymore?

If you are using the flash in the repositories, you are using 32bit flash with a 64bit wrapper...it has issues.
Using the 64bit flash fixes alot of issues, but you have to manually install it.

---

### Post by gila_monster on 2009-03-27
Out of curiosity, Hydrothrax, what version of Firefox/Swiftfox are you using?

---

### Post by Hydrothrax on 2009-03-27
> **lavinog said:**
> If you are using the flash in the repositories, you are using 32bit flash with a 64bit wrapper...it has issues.
Using the 64bit flash fixes alot of issues, but you have to manually install it.

Manually installing it is ok with me. Do you have a link to the file?

> **gila_monster said:**
> Out of curiosity, Hydrothrax, what version of Firefox/Swiftfox are you using?

Swiftfox 3.0.4 I think >>

---

### Post by gagnon88 on 2009-03-27
I have experienced the same problem but it was just a problem about Firefox not finding the suitable libraries. Here is the code I use to fix this:
```
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

```

Then restart Firefox.

---

### Post by lavinog on 2009-03-27
> **Hydrothrax said:**
> Manually installing it is ok with me. Do you have a link to the file?

[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install)

Read this thread:
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by cfurlin on 2009-03-30
> **Hydrothrax said:**
> Flash player 10 DIED on me about a week ago, and only showed a blank, white screen. I've tried every method of reinstalling/fixing/etc. of Flash Player 10 I could find, but to no avail! It's driving me nuts! Any help would be appreciated :)

Note: I run Ubuntu 8.10 64-bit

Did you recently update your copy of FF?

I have the "World Wide Web (Multiverse) binary of Flash installed and everytime Update Manager updates FF, I have to unintall it and then reinstall it to get it working again. Takes about 10 seconds. Easy fix.

---

### Post by philinux on 2009-03-30
Flash on 64 is so easy now.

However

sudo updatedb
then
locate libflashplayer.so

Remove any flash

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
Download to desktop

Double click tar file to unpack the libflashplayer.so file. It only needs to be put in ~/.mozilla/plugins
This folder needs to created if not in existance.

No need for sudo or symlinks.

---

### Post by jayanramesh on 2009-03-31
Dear buddy
 You had better go to this link [> http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml")
to install flash player 10 .And there  step by step instructions are given by Softpedia.This is the better choice to resolve your problem.
Thank you.

---

