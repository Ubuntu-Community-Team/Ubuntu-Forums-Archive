---
title: "[SOLVED] Opera, Adobe Flash 9, and 64..."
date: 2008-06-12
forum: x86 64-bit Users
---

### Post by Dark_Fire on 2008-06-12
```

```Hey hey!

I installed the new Opera 9.5 64 beta on my PC. Used it on Fedora 8 i386 with no problem...

I installed Ubuntu 8.04 - the Hardy Heron 64 on my AMD. When I opened Opera I noticed that there is no flash plugin installed. I quickly opened FireFox to double check and saw that there is no plugin installed.

I tried going to adobe website but saw they have no 64 version. So I followed this link:
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

Did all that and now I have the flash plugin. It works in firefox, but when I open a website in Opera, it ether crashes opera, or just makes it REALLY slow, or says I dont have the plugin installed...

When I go to youtube it just loads a empty space. When I drag windows over it it leaves their foot print in that space. (if you know what I mean). If I right click it brings up the
```
[settings]
[about Adobe Flash 9]
```
menu and then crashes compleately...

Does anyone know how to fix it? I just disabled it but now some websites look really weird and I really wanne watch something on youtube :P

Firefox doesn't work flash files thru proxy for some reason. So I cant open youtube on Firefox for some reason. The player loads but the video doesnt... Been a problem on both Linux and Windows. Guess its a Firefox error. But Opera works. Thats why I need it for opera. :/

Thanks in advance

---

### Post by Npl on 2008-06-12
What path is shown in you open [opera:plugins]("opera:plugins")?
Ubuntus packages install the flashplugin with a ndiswrapper, Opera must use the plugin directly, the path to the plugin should be "/usr/lib/flashplugin-nonfree/libflashplayer.so". If its something else its likely the wrong one.

You can adjust the paths Opera is searchin in through Preferences->Contents->Plugin Options->Plugin paths. Disable the mozilla one.

Also you should use flash 10 beta, works better than the current version. DL it directly from adobe and extract libflashplayer.so to /usr/lib/flashplugin-nonfree/libflashplayer.so

---

### Post by Colonel Kilkenny on 2008-06-12
Yeah, just as Npl said. Do not follow those instructions with Opera, there is no need. I have no idea why the tutorial isn't mentioning that Opera (and Konqueror?) do not need nspluginwrapper...

And if you really have installed Opera 9.5 Beta you should upgrade it because 9.5 Final was released earlier today.

edit.
Personally I always make dir ~/.opera/plugins and put opera-specific plugins there. Firefox may that way use whatever nspluginwrappernonsense it wants and I don't have overwrite anything. I just point Opera to search from my own dirs. Preferences -> Advanced -> Content -> Plug-in options.

---

### Post by Dark_Fire on 2008-06-12
Hey Npl, Thanks so much!

It worked!

For anyone else thats having this problem ill just give a nice step by step fix.
How to make Flash work in Opera 64:
Install Flash -> ```
sudo apt-get install flashplugin-nonfree lib32nss-mdns
```
Open Opera and check if it works.
If it doesnt work goto [opera:plugins]("opera:plugins")
If you see a "Shockwave Flash" in the list.
If there are more than one or the link to it is other than
/usr/lib/flashplugin-nonfree/libflashplayer.so follow these few steps.

Go to Tools->Preferences->Advanced->Contents->Plugin Options->Plugin Path
Check for a "/usr/lib/mozilla/plugins" and untick that one.
If you dont have "/usr/lib/flashplugin-nonfree/" add it here.

Save and it should work. Else just restart Opera and it WILL work.

Thanks again for the help...

Hope this helps someone else too :)

Dark_Fire

---

### Post by benign on 2008-07-03
Wow. Thanks Dark_Fire!

Opera was freezing up on me and hogging a core when I closed a playing flash when I just had the nonfree installed

lib32nss-mdns helped for some reason or another.

---

