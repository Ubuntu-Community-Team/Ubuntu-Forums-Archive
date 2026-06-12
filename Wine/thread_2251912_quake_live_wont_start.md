---
title: "quake live wont start"
date: 2014-11-07
forum: Wine
---

### Post by christoph5 on 2014-11-07
downloaded the quakelive exe file from [http://www.quakelive.com/#!welcome](http://www.quakelive.com/#!welcome) and installed it thru wine and it installed and i have a game start icon on the desktop now, quake live meny something comes up and i choose "start" but nothing happends,  game dont start!

---

### Post by christoph5 on 2014-11-09
help me please answears

---

### Post by howefield on 2014-11-09
Thread moved to the "*Wine*" forum.

Have you looked at the [Wine application database web]("https://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true") site ?

Few mentions of a Platinum rating, but I know little of gaming so can't help further than pointing you there whilst waiting for a reply here.

---

### Post by aquablue25 on 2014-11-09
Sup mate, 

how about some additional system information like OS, hardware and software details?

Also, if WineHQ won't run Quake Live out of the box, you might need some additional tweaking to get it working.

I recommend you try this: [https://www.codeweavers.com/compatibility/browse/name/?app_id=5827](https://www.codeweavers.com/compatibility/browse/name/?app_id=5827)

Download and install the Crossover trial in order to user it to install Quake Live with it: [https://www.codeweavers.com/products/crossover-linux/download/](https://www.codeweavers.com/products/crossover-linux/download/)

The installation itself should be fully automated and Crossover will download and install all needed dependencies automatically for you.

Let us know how it goes.

Cheers,
Aqua

---

### Post by jason147 on 2014-11-09
[LIST=1]
[*]Go to quakelive and login (or sign up, then log in)
[*]The site will try to install the plugin
[*]Instead of allowing Firefox to install your plugin, right click on the link and save the file
[*]Open the file using Archive Manager and right click on install.rdp and 'Open With...' your choice of editor
[*]Modify the line containing <em:maxVersion>...</em:maxVersion> so that it reads <em:maxVersion>4.*</em:maxVersion> -- or substitute whatever version or versions you run
[*]Add a line containing <em:unpack>true</em:unpack> inside the <Description>...</Description> tag
[*]When you save, Archive Manager will ask if you'd like to update the archive. Click 'Update'
[*]Fire up Firefox and click Tools -> Add-Ons -> Extensions
[*]Click the button to the left of the Search text box (in the top right) and choose 'Install Add-on from File...'
[*]Select the XPI file which you just modified and install it
[*]Once finished, go to quakelive and log in
[*]It should begin downloading all the game data you need to play
[*]Pick a game
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular][Here is where I found the fix]("http://www.quakelive.com/forum/showthread.php?7195-Running-Quake-Live-in-Firefox-4-on-Linux-fixes-inside") (thanks to @fossfreedom). In case something changes or you run another version of linux/firefox, you can always follow it to get a good answer or a link to a good one.

I hope this helps, And I do not take any credit for this Fossfreedom is the guy to thank I had the same problem :)

Cheers,
Jason[/FONT][/COLOR]

---

