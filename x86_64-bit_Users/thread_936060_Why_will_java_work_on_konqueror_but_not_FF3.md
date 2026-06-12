---
title: "Why will java work on konqueror but not FF3"
date: 2008-10-02
forum: x86 64-bit Users
---

### Post by wncben on 2008-10-02
Yeah, I know, running KDE apps on gnome is not a great idea.  Call it desperation, call it fits and giggles, whatever, I loaded up Konqueror (though nothing else in kde, just installed konqueror through add programs for a lark) and lo and behold, java works.  I can go to my bank, and the menus appear and work.  I can go to sites where dropdown menus drop under the main area of a site in FF, and they work properly...   I did not install any other plugins, I did not install any other java.  I am using the iced tea open jave and plugin.   Why oh why will Konqueror run java, apparently fully, and not FF3?
  Is it time for me to say good by to my trusty surf buddies, gnome and fox?
I mean Konq was not stable, crashed often and none of the other features I tried (including help) seemed to work because I didn't have the rest of kde installed...

  I am left with the options of 32 bit ff3, maybe kubuntu, or no java? 

are there any 64 bit  browsers for gnome that can use java fully?

~Ben

---

### Post by wncben on 2008-10-02
It is maddening,  There are so many sites I can't access fully, some even log my system down and freeze everything up under FF3, but work just fine under konqueror...  Why does the konqueror plugin work but not the ff one?   I take it konqueror is not mozilla based, but is there a way to make the Konqueror plugin work for ff3?  Is konqueror 32 bit perhaps?  

~'Ol Ben

---

### Post by Sef on 2008-10-02
1) What version of Ubuntu are you using?

2) >  are there any 64 bit  browsers for gnome that can use java fully?

See this [sticky]("http://ubuntuforums.org/showthread.php?t=774956").

---

### Post by wncben on 2008-10-03
I'm using 64bit hardy, and followed the sticky on this subject.  I have the current versions of open jdk and the iced tea plugin, which is apparently recognized by ff when I type in 'about:plugins'...  I do have some limited java usage but like 1 in 3 or worse websites seem to have some sort of issue, ranging from menus that pop under page elements to java objects that don't ever appear.  One site seemed to lock up all computer resources, causing a system lockup, but works fine with Konqueror, loading quicly and not using any appreciable extra system resources..  I am puzzled mostly because konqueror seems to have a working 64bit plugin. I assume that it is not a mozilla based browser.  If this is the case is there a gnome browser based on the same engine?  If konq is mozilla based, will its plugin work with ff? 
  I like FF I would rather use FF, but I NEED java functionality.  
It is possible that there is some other underlying issue, however I do not have the skills to diagnose it myself.

The only way I know to have full java funtionality on 64bit is to install 32 bit ff, which I did do  back on feisty using Kilz' howto, but I would prefer not to do that again.
Thanks~Ben

---

### Post by Sef on 2008-10-03
>  I assume that it is not a mozilla based browser.

It is not.  It uses KHTML as the engine.

>   If this is the case is there a gnome browser based on the same engine?

Right now there is Epiphany which uses the gecko engine.   However, it is being switched over to Webkit.

---

### Post by philinux on 2008-10-03
Open a terminal and use

```
firefox -safe-mode

```
I don't see the problems you're having. It may be some addons that are at fault. The above command will also show you any errors in the terminal.

---

### Post by wncben on 2008-10-06
I tried running firefox in safe mode and still have java issues.  At this point I think I am just going to install 32 bit ff and be done with it.  The only think I can think of is that somehow I fraked something in openjdk or icedtea when I inadvertantly installed sun java and now there is something broken...  I tried uninstalling and reinstalling all the open java packages with synaptic, but it didn't resolve anything.
  I am at a loss.  From what people seem to be saying I shouldn't have the problems with java that I am, but I am...
For example, the website for stc valves, manufacturer of solenoid valves and such ([www.stcvalve.com](www.stcvalve.com)) locks up my system and causes all kinds of bad juju (it seems like it uses all of my memory or cpu resources, although system monitor doesn't seem to notice, but it acts like swap memory is running full bore, and everything slows to a halt until the page finishes loading, which can take from 5 minutes or more, if it loads at all, at which point I can close it, otherwise I need to do a hard reeboot ie. pushing and holding the power button...)
 On ff3windows and on konqueror I have no problem, the page loads right up in seconds.
  This is the worst culprit so far, in every other page I have issues that effect the page (menus popping under or not showing up at all) but nothing like stcvalve.com
 Any help is greatly appreciated, I really don't want to do the 32bit thing if I can avoid it.

Thanks~Ben

---

### Post by Sef on 2008-10-07
>  At this point I think I am just going to install 32 bit ff and be done with it

For some sites, you have to use the 32-bit ff.  OpenJDK is not compatible with all Java sites.

---

