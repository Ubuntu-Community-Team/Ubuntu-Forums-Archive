---
title: "Upgrading ubuntu. Will wine applicatons be affected?"
date: 2011-07-06
forum: Wine
---

### Post by jfreak_ on 2011-07-06
So I am running 10.04 now and will be installing(not upgrading) 11.04. I have some applications in wine that for various reasons cannot be reinstalled. I was wondering that if I simply copied .wine from 10.04 to 11.04 will those applications still work, keeping in mind that the wine version in 10.04 is much older than that in 11.04.

---

### Post by An Sanct on 2011-07-06
There is always the option to uninstall the never version and instal an older one (talking about wine)

Its always a good idea to check this kind of scenario in a virtual machine. There are too many variables and none can be ignored, so doing it in a VM can alert you about problems nobody would/could predict.

Just curious ... what kind of Windows software?

---

### Post by jfreak_ on 2011-07-06
Most important is the Office 2007. The original disk is lying at home 1500 miles away.

And a VM on my aging laptop with 1 gig of memory would be a joke....

So basically I'll have to learn the hard way?

---

### Post by An Sanct on 2011-07-06
There is WineHQ, that says [Office 2007 (v12)]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992") has gold status.

So it should run normally. Which part of Office 2k7 is needed? ... Open Office can handle a lot ...

---

### Post by jfreak_ on 2011-07-08
bump?

---

### Post by bobwyajnr on 2011-07-08
@**jfreak_**

Dude, this stuff is all covered in the Wine FAQ... See the top of the subforum in the stickies - you read them right? (Or were you too busy posting urgent requests for help :) )

If you plan on using Unity it may break some stuff - like Wine applications. But who cares? Just backup your full WINEPREFIX (e.g. default is **/home/*user*/.wine**) somewhere sensible (e.g. offline thumb drive/external harddisk). You're good to go - even if you have to reinstall Ubuntu - after Unity trashes your system... :popcorn:

You can copy any whole WINEPREFIX structure (i.e. including all subfolders) onto another machine/Linux-install and run your applications (if you have Wine installed! - usual caveats apply of course)...

Time for you to get reading the [Wine user guide]("http://www.winehq.org/documentation") and [Wine FAQ]("http://wiki.winehq.org/FAQ") me tinks?? :-)

I'm on 11.04 (Linux-Mint 11) but using Gnome 2.32 on top of KDM/Kwin and it runs a treat :-) I warn you (before you update) that Compiz 0.9.4 appears to be very buggy on my ATI 4650M card (don't know what hardware you are rolling with)... Who knows could be 'cause I'm running it with Gnome 2.32.:)


Bob

---

### Post by jfreak_ on 2011-07-09
thank you for your extremely lucid response. Also could you kindly point out the relevent section in the stickie which deals with my issue (I checked but I couldn't find it since i was too busy posting urgent requests for help :D )

---

### Post by bobwyajnr on 2011-07-09
> **jfreak_ said:**
> thank you for your extremely lucid response. Also could you kindly point out the relevent section in the stickie which deals with my issue (I checked but I couldn't find it since i was too busy posting urgent requests for help :D )

Quoting from section 7.2 of the FAQ:
> Yes: ~/.wine is just the default Wine "prefix" (a.k.a. "configuration directory" or "bottle").

You can change which prefix Wine uses by changing the WINEPREFIX environment variable (outside Wine). To do this, run something like the following in a terminal:

```
export WINEPREFIX=~/.wine-new
wine winecfg
```

Wine will then create a new prefix in ~/.wine-new.

To use the default prefix, use the command unset WINEPREFIX . Or just set WINEPREFIX to ~/.wine.

Alternatively, you can specify the wine prefix in each command, e.g.

```
WINEPREFIX=/path/to/wineprefix wine winecfg

```
You can rename, move, copy and delete prefixes without affecting others, and each prefix has its own wineserver instance.

Wherever you see "~/.wine" or "$HOME/.wine" in this Wiki, you can usually replace it with "$WINEPREFIX".


TBH I do keep posting the same comment. But the documentation isn't really that obtuse. Try looking through the source code if you think it is (btw Wine takes as long to compile as the whole Linux Kernel :-) )

Bob

---

