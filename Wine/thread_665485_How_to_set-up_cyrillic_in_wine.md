---
title: "How to set-up cyrillic in wine??"
date: 2008-01-12
forum: Wine
---

### Post by yesint on 2008-01-12
Dear All,
I have a problem running applications with Russian interface in wine. I've searched a lot, but didn't find any comprehensive instructions of configuring wine for non-english programs. I'm a bit surprised with this, because this problem should affect anybody running programs with non-latin non-unicode interface.

The problem is the following. When I'm running any program with Russian interface, all Cyrillic characters are displayed as "?????". All user input in Russian is also displayed as "????". At the same time if I'm typing in Russian in the text fields in winecfg, the characters are displayed with no problems, so the fonts are there. Gnome menu entries added by the installer of this program also contain funny symbols, but work correctly.
Such problem also exists in Windows itself. There I have to chose Russian as the language for non-unicode programs in the Control Panel to see cyrillic in the interface. However, I've no idea how to emulate this in wine.

I'm running Ubuntu 7.10 and wine 0.9.46. Russian works perfectly in all native linux applications.

Any help will be deeply appreciated!

---

### Post by yesint on 2008-01-13
I just don't believe that nobody have this problem except me!

---

### Post by ddnlds on 2008-01-14
Yes, I have this issue, but I don't know how to resolve it yes :)

---

### Post by padonok600 on 2008-01-26
$sudo apt-get install msttcorefonts

restart X by log off and log back in

---

### Post by PunkLV on 2008-08-24
add this to your EXE commands line

*LANG=ru_RU.UTF-8* wine WoW.exe

I'm not a necro, just solved this few minutes ago for my WoW.

---

### Post by temcat on 2008-08-24
> **PunkLV said:**
> add this to your EXE commands line

*LANG=ru_RU.UTF-8* wine WoW.exe

I'm not a necro, just solved this few minutes ago for my WoW.

Try copying TrueType fonts like Arial, Tahoma, Verdana etc. to the Windows/Fonts directory on your wine C drive. Maybe you won't need to set LANG after that.

---

### Post by Mr.Enrich on 2010-04-11
Absolute beginner here. I have a problem trying to run a windows application in Bulgarian. It works fine if i set the entire ubuntu in Bulgarian, but I'd prefer to have it in English... Hate to give windows as an example but this resembles the function in windows control panel named  language for non-unicode programs. I have an english XP and the mentioned software works fine only if it's setup like this:
[IMG]http://download.fiat-bg.org/Personal_folders/Malone/Images/Untitled-2.png[/IMG]

If it's not I get question marks all over the place. Same as my current attempt with wine and ubuntu. So the question is - where do I set up this in ubuntu?

---

### Post by tetris9999 on 2011-04-25
thanks to temcat, just added the LANG=bg_BG.UTF-8 and the path to the exe file in the command to run on click field. That fixed the problem :P

---

### Post by v_mil on 2012-03-18
Dear members! I try a solution by Temcat and obtain very strange behavior. I use windows version of DraftSight CAD program because of no 64-bit Linux one.
Used Wine 1.4 @ Ubuntu 11.04 x64

Before a solution I have English interface. Files named in Cyrillic appears in list of recent files as spaces. I type Cyrillic text in text edit dialogue blindly because of replacing all characters as spaces. In the drawing this text appears very good.
I have msttfcorefonts and ISOCPEUR TTF Font installed. 

After a solution

~/.wine/drive_c/Program Files/Dassault Systemes/DraftSight/bin$ LANG=ru_RU.UTF-8 wine draftsight.exe

The interface is Russian but there is no possibility to type any Cyrillic character - the keyboard uses Latin in any language mode. Many English keys produces no character. Typing dtext produces ext. I see the same result in Russian Ubuntu interface.

What's wrong :confused:
Many thanks for assistance!

---

### Post by FokkerTISM on 2012-06-30
I have foobar2000 running under Ubuntu 12.04 LTS in wine. I have some Russian and Ukrainian albums encoded as FLAC/CUE sheets. However, the Cyrillic letters only show up as Latin letters with diacritic marks. I've tried the LANG=ru_RU.utf-8 but it doesn't work. I have Wine 1.4.1. I also have some Russian and Bulgarian albums encoded as separate FLAC and MP3 files and they show up as Cyrillic. Sometimes, the sound is very choppy and sped up, and sometimes music files won't play at all. It also doesn't recognise the files on my external hard drive even though the Ubuntu file explorer recognises them just fine.

---

### Post by ApoE4 on 2012-07-11
> add this to your EXE commands line

LANG=ru_RU.UTF-8 wine WoW.exe

Truth, still not the whole truth. That works iff your locale **is set to ** ru_RU.UTF-8 or at least that locale was generated beforehand. You may well have Cyrillic kbd installed, but your locale be smth different - en_US.UTF-8 as in my case. That command will not carp about the absent locale and you'll get those ????? in your windows app.

What you need then, is to generate the necessary locale. 400+ locale names are listed in */usr/share/i18n/SUPPORTED*. You may cull what you need and append a line like [FONT="Courier New"]ru_RU.UTF-8 UTF-8[/FONT] to your */var/lib/locales/supported.d/local* file. Next, you run ```
sudo dpkg-reconfigure locales
``` and there you are.

At least, that did the trick for me on Ubuntu 12.04 x64.

---

### Post by dino99 on 2012-07-12
you might need to select the required fonts (russian) into synaptic, install them and finally set your locale as explained previously

---

### Post by ApoE4 on 2012-07-12
> **dino99 said:**
> you might need to select the required fonts (russian) into synaptic, install them and finally set your locale as explained previously
The funny thing, as I tried and added an Afghani kbd to my existing two, I was immediately able to type Afghani in every Ubuntu window open and even copy-paste it to the app running under wine - I don't remember myself ever installing Afghani fonts! Evidently, I couldn't have typed Afghani into wine before generating the corresponding locale. 
I took Afghani just 'cos it was the first on the list of available kbds. Looks like some (minimal) set of fonts is present for every lang supported by Ubuntu. 
>  man locale-gen...
Compiled  locale  files  take  about 50MB of disk space, and most
users only need few locales.  In order to save disk  space,  compiled  locale
files  are not distributed in the locales package, but selected locales are
automatically generated when this package is installed  by  running the
locale-gen program.

---

### Post by FokkerTISM on 2012-07-19
Thanks. I tried adding locales for Russian, Ukrainian and Bulgarian and my CUE files now show up as Cyrillic.

---

### Post by Natanael on 2013-01-27
Has anyone found a solution how to type russian characters on wine non UTF programs in english (not cyrylic) Ubuntu?

---

### Post by mevsme on 2013-04-04
I wonder how to type cyrillic letters in Adobe Photoshop 7 in Wine, any ideas people?

---

