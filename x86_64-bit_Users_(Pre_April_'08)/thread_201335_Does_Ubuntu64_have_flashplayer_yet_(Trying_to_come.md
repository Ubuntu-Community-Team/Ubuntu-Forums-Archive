---
title: "Does Ubuntu64 have flashplayer yet? (Trying to come back to Ubuntu64)"
date: 2006-06-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by braveerudite on 2006-06-21
I want to know if Ubuntu 6.06 (AMD64 Version) has finally Java and flashplayer.  These are the only two things holding me back from installing Ubuntu.

---

### Post by PsychoTrauma on 2006-06-21
[QUOTE=braveerudite]I want to know if Ubuntu 6.06 (AMD64 Version) has finally Java and flashplayer.  These are the only two things holding me back from installing Ubuntu.[/QUOTE]

There is java but no firefox java plugin. As for flash you'll have to use gnash (but it won't work on everything yet).

---

### Post by dvejnovic on 2006-06-21
For java look at [ftp://ftp.tux.org/pub/java/JDK-1.4.2/amd64/03/]("ftp://ftp.tux.org/pub/java/JDK-1.4.2/amd64/03/")

---

### Post by braveerudite on 2006-06-21
I'm sad by the fact that I have to settle for 32 bit version.  Flahsplayer and Java are two so important thing... All this time and still no support for it.  Who will be the hero that ends this  ](*,)

---

### Post by eladamri on 2006-06-21
I found in the other 64bit flashplayer thread a link to [http://www.getswiftfox.com/]("http://www.getswiftfox.com/") and have been happily using flash on Ubuntu64 for a month now.

Try it. You'll probably like it. This HOWTO helps [http://ubuntuforums.org/showthread.php?t=142798]("http://ubuntuforums.org/showthread.php?t=142798")

---

### Post by JoWilly on 2006-06-21
Java and flash now work perfectly on firefox64 using these steps:

Java: install the blackdown java 1.4 (in the repos), java plugin works perfectly.

Flash: install nspluginwrapper to get macromedia flash 32bit to work perfectly on firefox64, search the threads in this section to find the easy howto.

---

### Post by braveerudite on 2006-06-21
I found the best solution.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Automatix is a graphical interface for automating the installation of the most commonly requested applications in Ubuntu linux.

---

### Post by JoWilly on 2006-06-21
[quote=braveerudite]I found the best solution.

[http://www.getautomatix.com/]("http://www.getautomatix.com/")

Automatix is a graphical interface for automating the installation of the most commonly requested applications in Ubuntu linux.[/quote]

Really ? Since when does automatix make 32bit plugins work on firefox64 ? I'd be glad to know as it didn't last time I checked.

---

### Post by braveerudite on 2006-06-21
[QUOTE=JoWilly]Really ? Since when does automatix make 32bit plugins work on firefox64 ? I'd be glad to know as it didn't last time I checked.[/QUOTE]


Oops sorry, I forgot I was trying to make up my mind about 32 or 64 and I forgot that detail.  I also posted today that I needed help getting the codecs to work or 32 bit version and I lost track.

---

### Post by Winblowz on 2006-06-22
[QUOTE=braveerudite]I'm sad by the fact that I have to settle for 32 bit version.  Flahsplayer and Java are two so important thing... All this time and still no support for it.  Who will be the hero that ends this  ](*,)[/QUOTE]
Even though there are workarounds for these, in order for them to be officially supported under 64-bit it is up to the developers. If Macromedia/Adobe would get its head out of its *** and Sun would work a bit harder, we could already have these things. If I were you, instead of sucking up to Adobe, I'd support Gnash for your flash needs.:cool:

---

### Post by free-zombie on 2006-06-23
[QUOTE=JoWilly]Really ? Since when does automatix make 32bit plugins work on firefox64 ? I'd be glad to know as it didn't last time I checked.[/QUOTE]
check again. The newest Automatix amd64 installes a 32bi swiftfox with Java and flash.

---

### Post by clooch on 2006-06-24
thank you that has helped me with flash.

---

### Post by linuxted on 2006-06-25
[QUOTE=JoWilly]Java and flash now work perfectly on firefox64 using these steps:

Java: install the blackdown java 1.4 (in the repos), java plugin works perfectly.

Flash: install nspluginwrapper to get macromedia flash 32bit to work perfectly on firefox64, search the threads in this section to find the easy howto.[/QUOTE]


java 1.4 does not work perfectly for me (unfortunately).  Blackdown is recognized as the version when I go to a java test sight, but for chat programs (see this site:  [http://www.hopeaz.com/Chat2.htm](http://www.hopeaz.com/Chat2.htm)) java crashes.

Any ideas?  I've tried automatix, java 5.0, downloading java myself and pulling my hair out :)

---

### Post by JoWilly on 2006-06-25
[quote=linuxted]java 1.4 does not work perfectly for me (unfortunately).  Blackdown is recognized as the version when I go to a java test sight, but for chat programs (see this site:  [http://www.hopeaz.com/Chat2.htm]("http://www.hopeaz.com/Chat2.htm")) java crashes.

Any ideas?  I've tried automatix, java 5.0, downloading java myself and pulling my hair out :)[/quote] 
Geez you are right :(

I have tried your link and my firefox crashed. It was working fine using other java applets...

Can you _please report a bug on launchpad with this link_, so that the developers get a chance to fix this ? (ubuntu maintainers will probably send the bug back upstream.... or you could report it to blackdown directly).

---

### Post by Kilz on 2006-06-25
[QUOTE=linuxted]java 1.4 does not work perfectly for me (unfortunately).  Blackdown is recognized as the version when I go to a java test sight, but for chat programs (see this site:  [http://www.hopeaz.com/Chat2.htm](http://www.hopeaz.com/Chat2.htm)) java crashes.

Any ideas?  I've tried automatix, java 5.0, downloading java myself and pulling my hair out :)[/QUOTE]

I have one, I wrote a [howto for running 32 bit firefox on amd64]("http://www.ubuntuforums.org/showthread.php?p=1174435#post1174435") with java, flash, acrobat, realplayer, and I plan on adding more plugins. Im running that howto setup and can open up that page just fine.

---

### Post by JoWilly on 2006-06-25
[quote=Kilz]I have one, I wrote a [howto for running 32 bit firefox on amd64]("http://www.ubuntuforums.org/showthread.php?p=1174435#post1174435") with java, flash, acrobat, realplayer, and I plan on adding more plugins. Im running that howto setup and can open up that page just fine.[/quote] 
Nice howto indeed :)

Have you Pm'd a mod to get it stickied ?

The fact that you can run it fine on java 1.5 probably means that that applet actually needs... java 1.5 :)

---

### Post by Kilz on 2006-06-25
[QUOTE=JoWilly]Nice howto indeed :)

Have you Pm'd a mod to get it stickied ?

The fact that you can run it fine on java 1.5 probably means that that applet actually needs... java 1.5 :)[/QUOTE]
Thanks :)
No, I havent. There is a long story behind why I made the howto. The old one I was sending people to got deleted by the document team. I contacted them , but I think I was put off and ignored. So I redid, updated, and fixed a few problems that were happening.
But if you think its worth stickying , maybe I should. Im still waiting for the pages that Cory Burgwer on the Doc team said would take the place of the old howto.

---

### Post by JoWilly on 2006-06-25
[quote=Kilz]
But if you think its worth stickying , maybe I should. Im still waiting for the pages that Cory Burgwer on the Doc team said would take the place of the old howto.[/quote]

It certainly IS worth it. People are constantly asking about the same things again and again ;)

---

### Post by loserboy on 2006-06-26
and again and again   ( and i was one of them)  :)

---

### Post by juah on 2006-06-26
[QUOTE=eladamri]I found in the other 64bit flashplayer thread a link to [http://www.getswiftfox.com/]("http://www.getswiftfox.com/") and have been happily using flash on Ubuntu64 for a month now.

Try it. You'll probably like it. This HOWTO helps [http://ubuntuforums.org/showthread.php?t=142798]("http://ubuntuforums.org/showthread.php?t=142798")[/QUOTE]


Does this mean one can use 32-bit Flashplayer with AMD64_swiftfox or what's the point? And if so: how. Is it just to install 32 flashplayer and making the soft link as adviced.

---

### Post by Kilz on 2006-06-26
[QUOTE=juah]Does this mean one can use 32-bit Flashplayer with AMD64_swiftfox or what's the point? And if so: how. Is it just to install 32 flashplayer and making the soft link as adviced.[/QUOTE]
Swiftfox is a nice program, its a little bit faster than the regular firefox because its optimised to the system. But Swiftfox is 32bit, even the versions for 64bit systems. Thats why it can use 32bit plugins. So yes you can use the 32 bit flashplayer with the amd64 labled but still only 32bit swiftfox.

---

### Post by juah on 2006-06-26
[QUOTE=Kilz]Swiftfox is a nice program, its a little bit faster than the regular firefox because its optimised to the system. But Swiftfox is 32bit, even the versions for 64bit systems. Thats why it can use 32bit plugins. So yes you can use the 32 bit flashplayer with the amd64 labled but still only 32bit swiftfox.[/QUOTE]


Yes! it does work quite nicely. All I did was remove gnash and install [http://www.debian-multimedia.org/pool/main/f/flash-player/flashplayer-mozilla_7.0.63.0-0.0_i386.deb]("http://www.debian-multimedia.org/pool/main/f/flash-player/flashplayer-mozilla_7.0.63.0-0.0_i386.deb")
with sudo dpkg -i --force-architecture before making the soft link for plugins.

P.S Can I safely remove --purge firefox64 or is this swiftfox dependend on that? Maybe not wise to to with --purge (bookmarks, other configurations?)

---

### Post by Kilz on 2006-06-26
[QUOTE=juah]Yes! it does work quite nicely. All I did was remove gnash and install [http://www.debian-multimedia.org/pool/main/f/flash-player/flashplayer-mozilla_7.0.63.0-0.0_i386.deb]("http://www.debian-multimedia.org/pool/main/f/flash-player/flashplayer-mozilla_7.0.63.0-0.0_i386.deb")
with sudo dpkg -i --force-architecture before making the soft link for plugins.

P.S Can I safely remove --purge firefox64 or is this swiftfox dependend on that? Maybe not wise to to with --purge (bookmarks, other configurations?)[/QUOTE]
It cant hurt to leave it, because your system is setup to use it if you open up html files on your computer. But if you want to remove the program its in /usr/lib/firefox. Then remove the //usr/bin/firefox launcher script, and replace it with one to launch swiftfox, or just edit it to llaunch swiftfox.

---

