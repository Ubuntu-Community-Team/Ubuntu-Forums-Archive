---
title: "Flash 9 on Edgy Eft and AMD64"
date: 2006-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by ispmarin on 2006-11-21
Hello all. I managed to install flash 9 on opera on an amd64. The procedure is simple (with all ia32libs installed ):
1) Install libstdc5++ (sudo apt-get install libstdc5++)
2) Download opera 9.02 from [www.opera.com](www.opera.com) (32bits)
3) Install via dpkg (dpkg -i --force-architecture opera<version>.deb)
4) Download the flash 9 player from 

[http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz)

5) Open it with (tar xvfz FP9_plugin_beta_112006.tar.gz)
6) Copy the file libflashplayer.so to the directory /usr/lib/opera/plugins
7) Go inside opera in Tools -> Preferences -> Content -> Plugins Options and click find new plugins.
8) Restart opera, and let it roll! 

Hope it helps.

EDIT: the package is libstdc++5. Sorry about the typo

Ivan

---

### Post by xopher on 2006-11-21
Testing this right now. Had been waiting for an excuse to try out Opera ;) Now with Flash 9 BETA 2 and this, hehe.

Thanks!

Ill let you know if it works for me.

edit: You probably mean 

1) Install libstdc++5 (sudo apt-get install libstdc++5)

---

### Post by xopher on 2006-11-21
Ok, ran into a little problem it seems:

/usr/lib/opera/9.02-20060919.6/opera: error while loading shared libraries: libaudio.so.2: cannot open shared object file: No such file or directory

I have ia32-libs, -libs-gtk, -libs-kde, -libs-sdl and lib32asound2 installed. This should be sufficient right?

locate gives me this: /usr/lib/libaudio.so.2
Shouldn't it be in lib32?

Ok I did som searching. The file should be in package libaudio2, but there doesnt seem to be a lib32version of it.

EDIT:

Solution:

cd /usr/lib/opera/9.02-20060919.6/
sudo ln -s /usr/lib32/libasound.so.2 libaudio.so.2

Got it to start ;) Let's see about flash.

EDIT again: WORKS! Thanks for making me do this ;)

---

### Post by ispmarin on 2006-11-21
Yeah, sorry about the typo...

Im glad that it worked out! :D

---

### Post by tog on 2006-11-28
I have trouble opening Opera. When I start it, I get > /usr/lib/opera/9.02-20060919.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file:

I have libqt-mt.so.3 file in /usr/lib, and a sym link to it doesn't seem to help. Any suggestions?

found the solution: I had to install ia32-libs-kde.

---

### Post by djgregory on 2006-12-02
oh mercy me, thank you ispmarin.  I think it was you who came to me in a dream one night long ago in the form of a slender blonde in a red dress with the highway sign "Indiana SR-9" ironed on to the front of the dress.

Yes, that was you.  It must have been.

The Gods smiled upon me when I stumbled upon this.  After all the time I've spent with disdain in my heart for Adobe/Macromedia, it's only fitting that I randomly found this.

I cast Holy Word in your presense, which dispels evil, removes fear, cures poison, restores 1000 HPs, restores all stats, and invulnerability for 3 turns.

---

### Post by Chinello Cybernético on 2006-12-02
Hi, I installed it correctly, and it works good. 

But, when I download any file, my "transfers tab" don't show anything, but if I click on a "ghost item" in the transfers list, I can see some information, but not all.

You can see > [[img]http://img176.imageshack.us/img176/1893/operahu4.th.jpg[/img]](http://img176.imageshack.us/my.php?image=operahu4.jpg)

Has anyone a suggestion?

See more information about my system:

> chinello@chinellux:~$ aptitude search ia32-libs
i   ia32-libs                                                   - ia32 shared libraries for use on amd64 and ia64 systems
i   ia32-libs-gtk                                               - gtk+ ia32 shared libraries for with OpenOffice.org
i   ia32-libs-kde                                               - KDE ia32 shared libraries for with OpenOffice.org
p   ia32-libs-openoffice.org                                    - ia32 shared libraries for with OpenOffice.org
i   ia32-libs-scim                                              - scim ia32 shared libraries for use with OpenOffice.org
i   ia32-libs-sdl                                               - ia32 shared libraries of sdl related packages for use on amd64 and ia6

When I run it from a terminal, it shows me this errors:

> chinello@chinellux:~$ /usr/bin/opera
qstring_to_xtp result code -2
ScimInputContextPlugin()
Qt: Locales not supported on X server
QInputContext: no input method context available
QInputContext: no input method context available
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
QInputContext: no input method context available
QInputContext: no input method context available
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
QInputContext: no input method context available
QInputContext: no input method context available
qstring_to_xtp result code -2
qstring_to_xtp result code -2
~ScimInputContextPlugin()

In this session, I typed the url of ubuntu web page and gone to it.

Any help would be great :)

Thanks

---

### Post by encho on 2006-12-13
It works perfectly. Anyone had any luck with java? There is an option to specify the java path, I tryed it, but it is not working (not recognized).

---

### Post by ispmarin on 2006-12-13
Hello folks. I am having the same problem that you, Chinello Cybernético. My transfer tab is blank also. Dunno what to do. Gmail also gives me 100% CPU, some crashes happens from time to time.

encho: You have to download the jre 1.5 _32bits_ from the sun site, and installs it in a place different that the jre 64bits. Then you can add in the plugins tab in opera the java path.

---

