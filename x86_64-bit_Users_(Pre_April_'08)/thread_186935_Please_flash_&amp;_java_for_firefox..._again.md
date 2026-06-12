---
title: "Please: flash &amp; java for firefox... again"
date: 2006-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by gaatmx on 2006-06-02
With the recent changes in the forums,:confused:  the new features of Dapper (specially those concerning the ability to install 32bit packs 'easy'):)  I need to ask for a renewed/revised HOWTO to get Java & flash (plug-ins) work with firefox running 64bit system.:???: 

I think this feature is important enough to give a thread in this new Dapper 64bit forum.
Thanks a lot.
G

---

### Post by JoWilly on 2006-06-02
Its the same if you install it on breezy or dapper. It does not change anything.

But it would definitely be nice to have a sticky howto for 32 bit apps in 64 as so many people are constantly asking about the same things.

Meanwhile, the search function is your friend ;)

---

### Post by Terracotta on 2006-06-02
[QUOTE=gaatmx]With the recent changes in the forums,:confused:  the new features of Dapper (specially those concerning the ability to install 32bit packs 'easy'):)  I need to ask for a renewed/revised HOWTO to get Java & flash (plug-ins) work with firefox running 64bit system.:???: 

I think this feature is important enough to give a thread in this new Dapper 64bit forum.
Thanks a lot.
G[/QUOTE]
Easy install of 32bit programs and 64-bit programs are for Edgy Eft, not Dapper Drake. but if you find the right debs:
sudo dpkg -i --force-architecture "package-name".deb
will most likely do the trick
to install flash:
download the flashplayer installer from Macromedia
extract the file,
cp the libflashplayer.so file to /usr/lib32/firefox/plugins 
or to /usr/lib32/opera/plugins for opera.
I'm not completely positiv about the firefox file.

---

### Post by dyrer on 2006-06-03
With older Ubuntu version this was a mess, is this working now? (with 6.06 LTS)

---

### Post by christoffer on 2006-06-03
Extracting the plugin and putting it in /usr/lib32/firefox/plugins did not work for me. Any other ideas? :-)

---

### Post by wmcbrine on 2006-06-03
I found that I could install Java in my 64-bit Firefox with Dapper. Seems to be working well. GPL Flash is still so-so.

I'd heard that Adobe wasn't going to make Flash 8 for Linux, but would skip to 8.5, and include a 64-bit version then. So I was disappointed to see no Linux binaries of Flash 8.5 on the beta page -- only Windows and Mac.

---

### Post by zluka on 2006-06-03
try swiftfox people.. it just installs flash (dunno how). just find the package that suits you, unpack it to your home directory, run swiftfox.sh, go to any site with flash, and, voila! it just installs the plug-in..

not sure about java, will try ;)

---

### Post by JoWilly on 2006-06-03
[QUOTE=christoffer]Extracting the plugin and putting it in /usr/lib32/firefox/plugins did not work for me. Any other ideas? :-)[/QUOTE]

There is a wrapper script available that makes 32bit flash and java plugins work with a 64 bit browser... search the forums ;)

---

### Post by Kilz on 2006-06-03
[QUOTE=JoWilly]There is a wrapper script available that makes 32bit flash and java plugins work with a 64 bit browser... search the forums ;)[/QUOTE]

I tried a for a few hours to get that to work, no luck. Swiftfox on the other hand runs flawlessly with no setup other than extracting the archive and making a launcher.

---

### Post by JoWilly on 2006-06-03
[QUOTE=Kilz]I tried a for a few hours to get that to work, no luck. Swiftfox on the other hand runs flawlessly with no setup other than extracting the archive and making a launcher.[/QUOTE]

Its the same with firefox.... get it from getfirefox.com.... :)

---

### Post by JoWilly on 2006-06-03
Unfortunately, the AMD64 swiftfox is 32bit (this is why flash works).

This means that you can install flash, but not the other plugins (quicktime etc...). For them to work you need a 32bit media player with plugins (i.ex 32 bit totem).

---

### Post by Kilz on 2006-06-03
[QUOTE=JoWilly]Its the same with firefox.... get it from getfirefox.com.... :)[/QUOTE]

I would, but I only need one working version of firefox, perhaps the next time I have to do a complete reinstall. Hopefull that wont be for a long time. I just locked the @#$%^@#%^#$ ati drivers to ones that work.

---

### Post by maury on 2006-06-03
I installed Swiftfox with no problem and went to flash and downloaded and extracted flash for amd_64 and copy and pasted the required files to Swiftfox plugins folder. Normally this would work but I got no joy. Any ideas on this. Maury

---

### Post by JoWilly on 2006-06-03
[QUOTE=maury]I installed Swiftfox with no problem and went to flash and downloaded and extracted flash for amd_64 and copy and pasted the required files to Swiftfox plugins folder. Normally this would work but I got no joy. Any ideas on this. Maury[/QUOTE]

swiftfox is 32bit so 64bit flash will not work.

but where in the world did you get 64bit flash ? this is what we are all looking for  :KS

---

### Post by maury on 2006-06-03
Sorry it is Flash 7. I've been sitting at the computer too long trying to get things going. Everything is working well except getting media players working <sigh>

---

### Post by JoWilly on 2006-06-03
[QUOTE=maury]Sorry it is Flash 7. I've been sitting at the computer too long trying to get things going. Everything is working well except getting media players working <sigh>[/QUOTE]


ok, so if you use swiftfox32 or firefox32 the easiest is to go to a flash site and click on the link that requests to install flash. It will install automatically.

as for media players, install all the gstreamer10 plugins and totem will play almost everything except wmv. The totem plugin will play quicktime, etc... in firefox64.

mplayer64 is nice too.

---

### Post by gaatmx on 2006-06-03
Do anyone tried the Automatix script?
The "pure amd64" version claims to add support for java, flash and quite a bunch of other stuff.... without "taint" your 64bit install with any 32 bit program.

G.

---

### Post by JoWilly on 2006-06-03
[QUOTE=gaatmx]Do anyone tried the Automatix script?
The "pure amd64" version claims to add support for java, flash and quite a bunch of other stuff.... without "taint" your 64bit install with any 32 bit program.

G.[/QUOTE]

Automatix installs the free flash 4 plugin. It does not play much.

Gnash is much better. It registers as version 8, but does not play everything yet (but plays more than the free flash 4 and is in active development).

It installs the blackdown java; the plugin works fine.

---

### Post by sostenible on 2006-06-05
I managed to get Flash & Java working on Firefox in five minutes following these few simple steps [http://ubuntuforums.org/showthread.php?p=904320#post904320](http://ubuntuforums.org/showthread.php?p=904320#post904320)

I installed afterwards a few more 32 bit applications, not available on 64bit format, doing apt-get install from chroot /chroot/ and they all work fine.

By the way, I am newbie, no technical knowledge at all.

---

### Post by gaatmx on 2006-06-05
Well, I get now a funstional firefox32 with java and flash in my 64 bit eviroment following this:
[https://wiki.ubuntu.com/FirefoxAMD64FlashJava]("https://wiki.ubuntu.com/FirefoxAMD64FlashJava")
The RealPlayer part also works pretty well.=D> 
And about the AutomatixPure64 thing:
I use it for install almost everything :o  but stay away of the firefox enhancements they claim if you follow the instructions above.:-k 

Good luck!

---

### Post by JoWilly on 2006-06-05
[quote=gaatmx]Well, I get now a funstional firefox32 with java and flash in my 64 bit eviroment following this:
[https://wiki.ubuntu.com/FirefoxAMD64FlashJava]("https://wiki.ubuntu.com/FirefoxAMD64FlashJava")
[/quote]

Very nice wiki, indeed :)

---

### Post by ahotz on 2006-06-05
Hi
I havent seen anyone mention this, but konqueror uses the java executable instead of a plugin(somehow). This allows you to use the sun java 64 bit executable to run java applets flawlessly. The only thing to make sure of is that /usr/bin/java points to the sun jre not gcj/gij.

---

### Post by JoWilly on 2006-06-05
[quote=ahotz]Hi
I havent seen anyone mention this, but konqueror uses the java executable instead of a plugin(somehow). This allows you to use the sun java 64 bit executable to run java applets flawlessly. The only thing to make sure of is that /usr/bin/java points to the sun jre not gcj/gij.[/quote]

Yep, for the kde goers...

For us gome guys we need the blackdown java, which has a working 64bit plugin for firefox et all.

---

