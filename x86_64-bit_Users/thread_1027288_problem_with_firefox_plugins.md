---
title: "problem with firefox plugins"
date: 2009-01-01
forum: x86 64-bit Users
---

### Post by p3ta on 2009-01-01
hi all,

everything worked fine up until 1-2 days ago, when i tried to watch a video on youtube and got the "you need latest flash or turn javascript on". Javascript is on, and i had sorted flash a few months ago, with nspluginwrapper i think (i'm not quite sure though, i just remember it was a pain)

at first i thought it could be some mess up from updating firefox 3.0.3 to 3.0.5 or updating from hardy to intrepid. 

i've tried various approaches from browsing around in forums but i think i've only made it worse. Now when i type about:plugins i get nothing.

i probably have conflicting files from all the tinkering these last few days

on top of that i discovered yesterday that Java is not working as well.

i'd appreciate it if someone can point me in the right direction with wiping out all the mess i've probably helped create, and getting my plugins and java to work back from zero

---

### Post by csat on 2009-01-01
> **p3ta said:**
> hi all,



on top of that i discovered yesterday that Java is not working as well.



I am using Swiftweasel that works perfectly along Ubuntu 8.10 64 bits, having no problems  with Java.  Check the link below for some directions on Java.

[http://ubuntuforums.org/showthread.php?t=1011899](http://ubuntuforums.org/showthread.php?t=1011899)

---

### Post by p3ta on 2009-01-01
[QUOTE=

[http://ubuntuforums.org/showthread.php?t=1011899](http://ubuntuforums.org/showthread.php?t=1011899)[/QUOTE]

did that step by step but it didnt work out for me... i've tried all sorts of stuff since yesterday and i'm looking for some instructions on what to do to clean the mess

---

### Post by bumanie on 2009-01-01
Have you considered uninstalling and then reinstalling firefox and starting afresh? As far as the plugins go, you may have to purge them and start afresh with them also. It would help if you could tell us exactly which plugins you have played around with - I assume flash is one of them.

---

### Post by CJ56 on 2009-01-01
Presumably you've checked out Kilz' instructions in the sticky at the top of the forum?

Well worth doing, one line at a time, is

```
sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
```

As Kilz tells us to... This clears out all the gunge from previous installations and sets you up to -

Download the Flash 10 for 64-bit tar.gz from the Adobe website and close Firefox

Simplest thing after that is to extract the .so file (use right-click on the tar.gz) and copy the .so into .mozilla/plugins in your Home Folder. This is a hidden folder, so you'll have to check the Show Hidden Files box under View, and maybe create a new folder called "plugins" in the .mozilla folder if it doesn't already exist

Restart FF and it should work a charm...

---

### Post by p3ta on 2009-01-01
well i removed and reinstalled firefox with ubuntuzilla and also installed swiftweasel and managed to get Java to work with it but still not with firefox

i also managed to get flash working on firefox (thanx cj56, i had tried that bit earlier yesterday but i probably missed a step)

i now have libflashplayer.so in /usr/lib/mozilla/plugins and have linked both ~/.mozilla/plugins and ~/swiftweasel/plugins there. Weird thing is flash works on firefox that way but not on swiftweasel (but swiftweasel flash works fine if i use nspluginwrapper)

i also grabbed these
```
sudo aptitude install mozilla-mplayer
sudo aptitude install mozilla-plugin-vlc
```

the files are in /usr/lib/mozilla/plugins, they link over to swiftweasel and show up properly on about: plugins (libvlcplugin.so, mplayerplug-in-dvx.so, mplayerplug-in-qt.so, mplayerplug-in-rm.so, mplayerplug-in-wmp.so, mplayerplug-in.so) but not on about: plugins on firefox.

---

### Post by echofloripa on 2009-02-03
> **CJ56 said:**
> Presumably you've checked out Kilz' instructions in the sticky at the top of the forum?

Well worth doing, one line at a time, is
...
sudo apt-get -y purge mozilla-plugin-gnash
...
Restart FF and it should work a charm...

I have 8.10 64 bits. I'm trying for ages to use multi tab with "Tab Mix Plus", but no luck, I always get:

"Firefox could not install this item because "install.rdf" (provided by the item) is not well-formed or does not exist. Please contact the author about this problem."

Many other plugins give me the same result, quite frustrating, but I don't want to get back to windows, so trying desperately to get this fixed.

I'm using an AMD64, ubuntu 8.10 and firefox (bundled with ubuntu) 3.0.5.

I'm gonna try your steps above. 
I will let you know what happens :)

Update: Seems it didn't helped. I tried swiftweasel, and it works with tab mix plus. But it's missing a few things like the search while you type among others...

Any help much appreciated...

---

