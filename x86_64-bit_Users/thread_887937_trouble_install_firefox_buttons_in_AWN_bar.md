---
title: "trouble install firefox buttons in AWN bar"
date: 2008-08-12
forum: x86 64-bit Users
---

### Post by arkarkwin on 2008-08-12
Hi 
   I used latest Ubuntu 8.04 hardy on compaq presario f767nr laptop. Everything work fine with compiz desktop. I could used all the cool feature of famous tube and shaking windows in there. All the transparency setting in there also work. 
  However in awn mac like desktop panel I have trouble installing new buttons in there. I read all the help files and google forums but I couldn't find any answers to it. 
 Basically the way I understand is that if I want to install new buttons like firefox browser in the awn bar, I have to created a launcher in awn-manager. I have to put firefox command in command buttons and search an icon for it and wrote the name of the program name in it. and then restarted the awn program. I did all that but firefox buttons will not simply appeared.I try to drag the buttons in launchers to the bar but it simply goes back into the launcher but I did mange to see the + sign when the icon reached to the bar. I check the ~/.config/awn/launcher and I found the launcher I created. I found awn_launcher.desktop and when I open it vim editor, I found these
"[Desktop Entry]
Comment=mozilla internet exploer
Name=firefox broswer
Encoding=UTF-8
Exec=firefox
Type=Application
Icon=firefox-3.0"
  I could open the program in file Browsers by going to it's path and it show as firefox icons and when I open it, it launch the program. 
The .desktop however differs from typical awn launcher icon in /usr/share/avant-manager/applets/~.desktop which code were written as 
"[Desktop Entry]
Type=Application
X-AWN-AppletType=Python
Name=Weather Applet
Comment=Display the local weather
Exec=weather/weather.py
Icon=weather-clear
X-AWN-AppletCategory=Network,News
X-Ubuntu-Gettext-Domain=awn-extras-applets"
  When I open awn program in shell or terminal I found the following things written
arkarkwin@arkarkwin-laptop:~$ awn
Screen is composited.
APPLET : /usr/share/avant-window-navigator/applets/main-menu.desktop
APPLET : /usr/share/avant-window-navigator/applets/showdesktop.desktop
APPLET : /usr/share/avant-window-navigator/applets/awnterm.desktop
APPLET : /usr/share/avant-window-navigator/applets/weather.desktop
APPLET : /usr/share/avant-window-navigator/applets/awnsystemmonitor.desktop
APPLET : /usr/share/avant-window-navigator/applets/shinyswitcher.desktop
APPLET : /usr/share/avant-window-navigator/applets/separator.desktop
APPLET : /usr/share/avant-window-navigator/applets/cairo-clock.desktop
APPLET : /usr/share/avant-window-navigator/applets/stacks.desktop
APPLET : /usr/share/avant-window-navigator/applets/trasher.desktop
APPLET : /usr/share/avant-window-navigator/applets/battery-applet.desktop

AWNLib Warning in weather.py:
	timing.time is deprecated; use timing.register instead


AWNLib Warning in weather.py:
	timing.time is deprecated; use timing.register instead


AWNLib Warning in weather.py:
	timing.time is deprecated; use timing.register instead

No support for device type: thermal
WM=compiz
ShinySwitcher Message:  compiz detected
ShinySwitcher Message:  viewport/compiz detected.. using existing workspace config
cols = 1,  rows=1
No support for device type: thermal
No support for device type: thermal
No support for device type: thermal
No support for device type: thermal
No support for device type: thermal
No support for device type: thermal
No support for device type: thermal
No support for device type: thermal"
 I guess No support for device type:thermal mean my firefox launchers or was it something else?
  I had some experience with slackware and kde desktop and this is my first time with Ubuntu and Gnome and I like Ubuntu a lot because I don't have to go through all the trouble with complying source and building my own slack pkg packages just to run mac like baghira theme in kde-desktop. But this unable to install firefox launchers in awn is really starting to bugs me.
  Any help or advice would be really appreciated it.

---

### Post by Arcturus691 on 2008-11-17
Here is an easy way to add Firefox to AWN.
[LIST=1]
[*]Go to Main panel->Applications->Internet
[*]Click on Firefox and drag it to the AWN dock
[/LIST]
It is that simple, I couldn't believe I didn't try it earlier.

You can also drag a desktop icon to the AWN dock but if you remove the icon on the desktop you will lose the icon on the AWN dock.  This is also true if you delete the icon out of the menu as well.

Hope this helps

---

