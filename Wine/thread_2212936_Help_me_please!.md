---
title: "Help me please!"
date: 2014-03-23
forum: Wine
---

### Post by s1ll7gurl on 2014-03-23
I have been to three other forums already and they are continually redirecting me.  I just want to do my homework.  Please, Help me!

[COLOR=#000000][FONT=Verdana]I cannot run anything in Wine. At all. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]All my issues started when my school's IT decided to uninstall and re-install drivers. I was running a windows partition at the time. I couldn't access internet which I need for classes so I gave up on Windows and wiped the drive to put Linux on. I'm still learning a lot about Linux, so if this is in the wrong spot, please help cause I have no idea where to put stuff anymore.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I currently have Wine 1.6.something. I have been trying to update, thinking that is the issue. However, it won't let me. I click the link to install it and nothing happens so I decide to update manually. This is what the Terminal spits out:[/FONT][/COLOR]

[COLOR=#000080][FONT=Verdana]Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
Some packages could not be installed. This may mean that you have 
requested an impossible situation or if you are using the unstable 
distribution that some required packages have not yet been created 
or been moved out of Incoming. 
The following information may help to resolve the situation: 

The following packages have unmet dependencies: 
wine1.7 : Depends: wine1.7-i386 (= 1:1.7.14-0ubuntu1) but it is not going to be installed 
E: Unable to correct problems, you have held broken packages.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]If ANYONE can tell me how to fix this, please, DO! I am sick and tired of being unable to do things for class because they "only run on Windows". [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Please, and thank you.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Ahlyssa[/FONT][/COLOR]

---

### Post by Doug S on 2014-03-23
> **s1ll7gurl said:**
> [COLOR=#000080][FONT=Verdana]
wine1.7 : Depends: wine1.7-i386 (= 1:1.7.14-0ubuntu1) but it is not going to be installed [/FONT][/COLOR]Well, I don't understand because I see wine 1.4 as the current version for saucy (13.10).
Even for the current development version of Ubuntu (which you shouldn't be using yet), Trusty 14.04, I see it as wine version 1.6.

What version of Ubuntu are you using?

---

### Post by monkeybrain20122 on 2014-03-23
> **s1ll7gurl said:**
> I have been to three other forums already and they are continually redirecting me.  I just want to do my homework.  Please, Help me!

[COLOR=#000000][FONT=Verdana]I cannot run anything in Wine. At all. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]All my issues started when my school's IT decided to uninstall and re-install drivers. I was running a windows partition at the time. I couldn't access internet which I need for classes so I gave up on Windows and wiped the drive to put Linux on. I'm still learning a lot about Linux, so if this is in the wrong spot, please help cause I have no idea where to put stuff anymore.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I currently have Wine 1.6.something. I have been trying to update, thinking that is the issue. However, it won't let me. I click the link to install it and nothing happens so I decide to update manually. This is what the Terminal spits out:[/FONT][/COLOR]

[COLOR=#000080][FONT=Verdana]Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
Some packages could not be installed. This may mean that you have 
requested an impossible situation or if you are using the unstable 
distribution that some required packages have not yet been created 
or been moved out of Incoming. 
The following information may help to resolve the situation: 

The following packages have unmet dependencies: 
wine1.7 : Depends: wine1.7-i386 (= 1:1.7.14-0ubuntu1) but it is not going to be installed 
E: Unable to correct problems, you have held broken packages.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]If ANYONE can tell me how to fix this, please, DO! I am sick and tired of being unable to do things for class because they "only run on Windows". [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Please, and thank you.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Ahlyssa[/FONT][/COLOR]

You click which link to install what?

The repo doesn't have wine 1.7. You have to install it from Wine's ppa.[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa) 

P.S. I always install wine from ppa as the Ubuntu 'officially supported' version is outdated. I don't know it is till on 1.4. I have been running 1.7 since 13.04 or maybe even 12.04.

---

### Post by oldos2er on 2014-03-24
Moved to Wine.

> **s1ll7gurl said:**
> [COLOR=#000000][FONT=Verdana]I cannot run anything in Wine. At all. [/FONT][/COLOR]

What programs are you trying to run in Wine? It may simply be that they won't work under Wine, since not all Windows programs do.

---

### Post by Hodevah on 2014-03-24
Might I also kindly suggest  a proper thread title as the one that you have is quite frustrating to others who peruse the forums to find a way to help others and come across thread titles that provide no foreknowlege of what the problem can be. Please edit your thread title to something more appropriate.

---

### Post by Mark Phelps on 2014-03-25
BEFORE you struggle a lot more with Wine, you might prevent wasting your time by going to the WineHQ website (link follows) and looking up the apps and versions you want to use.  Anything not listed, or rated lower than Gold, is essentially going to be a waste of your time:  [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

---

