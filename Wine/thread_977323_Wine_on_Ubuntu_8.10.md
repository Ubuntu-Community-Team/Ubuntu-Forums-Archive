---
title: "Wine on Ubuntu 8.10"
date: 2008-11-10
forum: Wine
---

### Post by Refuge on 2008-11-10
I installed WINE onto my ubuntu 8.10. However, I successfully installed IMVU through wine, however it won't open. When I click on the icon, it comes up with the little loading box but when it disappears, there is no login box that comes up.

Have I done anything wrong? I want to be able to get it to open this one windows program before I install bigger things like 3DS Max and Adobe Photoshop.

---

### Post by stinger30au on 2008-11-10
perhaps a link to the program you installed would be a start as i have never heard of it


have you installed the newest version of wine from here

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

easiest way to test the s/w is to start up shell (command prompt) and cd in to your wine directory and in to the program directory and wype in

wine ./program_name

and substitue program_name for the .exe file to start it with

now watch the data race by and see if any errors come up

you may needs something from winetricks to make it run
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by ajgreeny on 2008-11-10
Where is this icon that you click on, and what are its properties (when you right click it and choose properties, what is the launcher tab pointing to)?  If the icon appeared on the desktop automatically because you told the install process to put one there, it is just possible that it does not point to the correct file.

If you are talking about an icon put into the menu under Wine in your Applications menu, then it could be simply that IMVU will not work through wine.  I must add that I don't know IMVU at all, so that comment may not be of any consequence.

---

### Post by Refuge on 2008-11-10
Well this is the program;
[http://www.imvu.com](http://www.imvu.com)

I shall try the shell command box, and I didn't tell it where to install, IMVU automatically installs to C:\Application Data so I imagined WINE put it there and created a shortcut on the desktop.

---

### Post by wsbones on 2009-04-05
I'm a newbie.  I've installed Ubuntu 8.10 and Wine 1.1.18 and would like to get a window application to run.  The application is qvwin 4.0g for which I have the install disk. It's a Bible program that I ran under Windows XP. I installed it with no problem but when it tries to run, it can't find the qvwin.cfg file. The file is in the correct place however in the C:\qvwin subdirectory.  This app is supposed to work under Wine according to the Wine database.

Can anyone help?  Thanks.

Bill

---

### Post by wsbones on 2009-04-05
I found the answer.  you have to set wine up for win 3.1 and cd into the qvwin directory.

Bill

---

