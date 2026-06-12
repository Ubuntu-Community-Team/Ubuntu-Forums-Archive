---
title: "Need to run ie6 under win200 or winxp"
date: 2008-04-03
forum: Wine
---

### Post by S29K on 2008-04-03
I am one of the unfortunate souls stuck having to run ie6 at work.  I need both ie6 to access Chrysler's portal site and the emulation software I have run on my company's DMS needs ie6 to function properly.  I have been using ies4linux and and older version of the ERALink emulator from Reynolds & Reynolds for well over a year now with few difficulties.

Now R&R has released a new version of the emulator that I HAVE to upgrade to which requires windows 2000 or XP.  Here's the problem, ies4linux installs IE6 under win98.  I have tried all kinds of different tricks to get it to run under winxp or win2000 to no avail.  I've played with stock wine, winetricks, winedoors, winexs, playonlinux, crossover and various concoctions of my own.

Oh, and to add to my misery, Chrysler has now upped their requirements for a training portion of the site to use Acrobat7...not available for win98.  I can use the firefox useragentswitcher add-on to fool the site into thinking I am using WinXP/IE7 but it doesn't detect Acrobat7 even though I have Acrobat 8 installed.

Does anyone know how I can get ie6 installed and working under win2000 or winxp?  HELP! :confused:

---

### Post by AndrewTheArt on 2008-04-03
run 

```
WINEPREFIX=~/.ies4linux/ie6 winecfg
```

or

```
WINEPREFIX=~/.ies4linux/ie7 winecfg
```

 and change "Windows 98" to "Windows XP"

Good luck :)

---

### Post by S29K on 2008-04-04
Thanks for the help but I tried that.  Unfortunately ies4linux won't display secure sites under winxp or win2000 using this method...regular sites work fine but the one I need is [https://dealerconnect.chrysler.com](https://dealerconnect.chrysler.com)
:(

---

### Post by EvanCarroll on 2008-05-01
try using the Firefox "User Agent Switcher" it can mimmick a ie7 browser. It will work as long as chrysler doesn't *really* require IE7 specific features, (vbscript and ms activex)

---

### Post by nick09 on 2008-05-01
Try using the IE tab addon for firefox.

---

### Post by S29K on 2008-05-02
First off, thanks for the replies.

Unfortunately, the Chrysler website opens in any browser but some of the functionality doesn't work properly in anything other than IE6 or IE7.  They are using non-standard html for navigation layout and for some reason a particularly important javascript expanding menu tree doesn't work in firefox even with all plugins and add-ons enabled.  Lazy, inconsiderate programmers with no regard for standards.  This drives me nuts.

Secondly, my accounting system software runs on CentOS but for some incredibly bizarre reason MUST be accessed through a Windows-Only emulator that emulates a Televideo 955 terminal...a full screen layout terminal that we actually used before PCs and emulation.  The emulator works reasonably well under wine but requires IE to be installed to poll the network to check for a valid license.  I am unsure which part of IE it uses but having IE working properly under wine is the only way for both applications to work.

The emulator was recently updated and I now have to run wine as Win2000 or WinXP to install and run it.  The only method for successfully installing IE that I have found is ies4linux which defaults to Win98 and for some reason will not run properly if I switch wine to Win2000 or WinXP after the installation.

Add to this a new problem where the fonts in the emulator worked fine under wine 0.9.52 but display half-lit pipe '|' characters instead of spaces making the screen almost unreadable in later versions of wine.  I upgraded to Hardy and older versions of wine are not available.  I have tried compiling an older version but the dependencies cause problems as they have changed since 0.9.52 and are not available in the Hardy repositories. :(

---

