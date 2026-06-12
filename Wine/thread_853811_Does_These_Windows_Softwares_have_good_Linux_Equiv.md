---
title: "Does These Windows Softwares have good Linux Equivalent?"
date: 2008-07-08
forum: Wine
---

### Post by Diptansu on 2008-07-08
Does These Windows Softwares have good Linux Equivalent?

1)Global Mapper
2)Rockworks
3)AutoCAD
4)ArcGIS
5)CorelDRAW

Pls Help.

---

### Post by Joshuwa on 2008-07-08
1...Not familiar
2...Not familiar
3...Not familiar, but I imagine there are hundreds of CAD apps for linux

4...Unfortunately I have not found one, and I have not had success running ArcGIS with wine. There is GRASS, but I'll be darned if I can figure this out; it may be similar, but at this stage, I cannot imagine it being a faithful replacement.

5...InkScape might be worth looking into. Could you run CorelDRAW under WINE?

---

### Post by sawjew on 2008-07-08
[LIST=1]
[*]The best alternative here is probably [Quantum GIS]("http://www.qgis.org/").  It is a GIS system that can work with native files from MapInfo and ARCGis and has numerous plugins available to provide extra features.
[*]I Don't know of a direct alternative here but [GRASS GIS]("http://grass.itc.it/") has extensive capabilities in the area of hydrological and groundwater modelling and has also been used for mapping of fault lines so it may be able to help.
[*]The ubuntu repositories have Qcad and SAGcad in them which are both quite good 2D CAD programs.  [BricsCAD ]("http://www.bricsys.com/en_INTL/")has a linux version but unfortunately it is behind their windows versions.  They are currently developing a new linux version which should be out anytime soon.  Other than that AutoCAD apparently works well with wine.
[*]Once again Quantum GIS or QGIS as it is known.  This is developing rapidly and it has a plugin for GRASS so it can be used as a graphical interface for GRASS and combine the features of the two GIS packages.
[*]Not really familiar with CorelDRAW but there is [Inkscape ]("http://www.inkscape.org/")as already mentioned, [XaraLX]("http://www.xaraxtreme.org/") and [Skencil]("http://www.nongnu.org/skencil/index.html"), and Openoffice Draw for simpler drawings.
[/LIST]

All of these, apart from BricsCAD are in the repositories so can be found via add/remove or synaptic.  I use [this ]("https://launchpad.net/~qgis/+archive")repository to keep my QGIS up to date.

The only software that costs anything in that list is BricsCAD and it is about a 10th of the price of AutoCAD.

Check out GRASS GIS, it is quite difficult to learn but it is known as one of the most sophisticated GIS packages available.

Good luck.

---

### Post by Diptansu on 2008-07-09
Thanx for replyin guys ...

Anywy, cant install "qgis" in hardy heron. :(

[http://download.qgis.org/downloads.rhtml](http://download.qgis.org/downloads.rhtml) here they told me to install it by apt-get (the command is "sudo apt-get update && sudo apt-get install qgis". But with this ubuntu is checking various 'packages' and 'sources', just to say 
 
Package qgis is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package qgis has no installation candidate 

at the end.

---

### Post by sawjew on 2008-07-09
You will need to enable the universe repositories to install qgis.  Just go to System>Administration>Software Sources and check the boxes next to "Community maintained open source software (universe)" and "Software restricted by ... (multiverse)".

It will say you need to update when you are closing the window, say OK to that and then run

```
sudo apt-get install qgis qgis-plugin-grass
```

This will install Qgis and GRASS GIS.

Have fun.

Edit:  Apparently Qgis isn't in the universe repositories anymore as of Hardy so follow the instructions [here]("http://techmania.wordpress.com/")

---

### Post by ooobuntooo on 2008-07-09
[http://www.osalt.com/autocad](http://www.osalt.com/autocad)
[http://www.osalt.com/corel-draw](http://www.osalt.com/corel-draw)

---

### Post by Diptansu on 2008-07-09
Thanx sawjew ...

I tried What u said ...

First I tried to check those boxes you said at System>Administration>Software Sources. Found that these boxes are already checked. But as you said i still unchecked those boxes [:p] and checked them again. It Showed the following msg ...

"[B]The information about available software is out-of-date

To install software and updates from newly added or changed sources, you have to reload the information about available software.

You need a working internet connection to continue.[/B]"

It had two button. "Reload", "Close". I clicked "reload". Then it downloaded near about 42 packages.

Then i "sudo apt-get install qgis qgis-plugin-grass".

Gave the following msg ...

"[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package qgis is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package qgis has no installation candidate[/B]"

Entirly confused, Dont know what to do now.:???:

---

### Post by Diptansu on 2008-07-09
Thanx ooobuntooo,

I hvnt seen ur links 'bout CAD yet. Surely i wd do . Thanx again.

---

### Post by ooobuntooo on 2008-07-09
> **Diptansu said:**
> Thanx ooobuntooo,

I hvnt seen ur links 'bout CAD yet. Surely i wd do . Thanx again.

[http://www.osalt.com](http://www.osalt.com) is a great website for finding Linux software alternatives.

---

### Post by sawjew on 2008-07-09
Hi Diptansu,

Just to point out the edit on my previous post, I found out after I had replied to you that Qgis is no longer in the ubuntu repositories.  You need to add the extra repository as described in the directions I have linked to [here]("http://techmania.wordpress.com/2008/07/09/qgis-on-ubuntu-hardy/").

If you are not familiar with how to add repositories just open Software Sources (under System>Administration) go to the 3rd party software tab, add repository and paste in this line ```
deb http://ppa.launchpad.net/qgis/ubuntu/ hardy main
```

Then update the repositories again and then

```
sudo apt-get install qgis qgis-plugin-grass python-sip4 python-qt4 
```

Note:  you will get a message about the software not being authenticated, just ignore it and keep going (click OK).

It should all work now.

---

### Post by Diptansu on 2008-07-10
Hi sawjew,

This time everything worked well ... it was downloaded ... installed.

But sad enough i didnt find any new 'icon' to click and start the application. I really searched well.

help me out man ... ](*,)

---

### Post by Frak on 2008-07-10
> **ooobuntooo said:**
> [http://www.osalt.com](http://www.osalt.com) is a great website for finding Linux software alternatives.
They're fairly outdated, well, since they show that Nero doesn't have a Linux version.

---

### Post by sawjew on 2008-07-10
You can start qgis from a terminal using the command```
qgis
```

you can also hit Alt>F2 on your keyboard and enter qgis into the "Run Application" window.

If you want a menu entry you can either right click on the Applications menu and select "Edit menus" and add a menu entry (the icon is in /usr/share/pixmaps/qgis-icon.xpm) or you can extract the desktop file attached into either /usr/share/applications or ~/.local/share/applications

Check if the GRASS plugin is available after you have started Qgis.  If it isn't let me know because I have a solution for that also.

---

### Post by Diptansu on 2008-07-10
> You can start qgis from a terminal using the command
Code:

qgis

you can also hit Alt>F2 on your keyboard and enter qgis into the "Run Application" window.


These two things worked nice ... the software is starting properly (though i didn't get enough time to explore this).. I ll do it and let u know what happened.

> If you want a menu entry you can either right click on the Applications menu and select "Edit menus" and add a menu entry (the icon is in /usr/share/pixmaps/qgis-icon.xpm)

I did this. The "Qgis" icon is now showing in the menu alright. But its not working. :(
Each time i click on it give the following msg ...
> Could not launch menu item
Failed to execute child process "/usr/share/pixmaps/qgis-icon.xpm" (Permission denied)

As a new boy in linux didnt really understood what to do when u said this ... :)
> you can extract the desktop file attached into either /usr/share/applications or ~/.local/share/applications

i didnt get time check the software. after i do it i ll let u know 'bout the "GRASS plugin".

U know its really nice to find ppl have solutions of every problem i face.
Its a gr8 forum, at least for the beginners.:)

---

### Post by sawjew on 2008-07-11
I'm glad it is working for you now.

As for the menu entry you can add it with the menu editor as follows;
[LIST=1]
[*]Right click on the Applications menu
[*]Select "Edit Menus"
[*]In the left hand column select the sub-menu you want to put the menu entry in.  I have mine under "Education"
[*]The contents of the sub-menu will be displayed on the right
[*]Select "New Item" on the right.  This will open a dialog box to enter the application information.  I have attached a screenshot of what this should look like.
[*]Under "Name" enter ```
Quantum GIS
```
[*]Under "Command" enter ```
qgis
```
[*]Click the button over on the right of the window which is where you enter the icon details.  This will open a file browser window.
[*]In the top bar paste ```
/usr/share/pixmaps/qgis-icon.xpm
```
[*]Close the dialog and the menu editor and "Quantum GIS" should be in the menu under "Education" or wherever you chose to put it.
[/LIST]

If you installed the GRASS plugin you will also have GRASS installed and you can add a menu entry for it the same way.

use ```
grass
``` for the command and ```
/usr/share/qgis/grass/modules/v.out.ogr.shape.1.png
``` for the icon.

If you want to use GRASS itself I advise you to go to the [GRASS website]("http://grass.itc.it/") and spend some time looking through it and at the documentation available.

GRASS is extremely powerful but is not particularly user friendly and I can't give you much assistance there.

Qgis on the other hand is quite easy to use and if you have used any other GIS package you shouldn't have to much trouble.  It can work on Mapinfo tables and ARCGis shapefiles too and can even combine them together.  It is not yet as full featured as Mapinfo and ARCGis but it is developing rapidly and with the ability to integrate with GRASS it promises to be a killer GIS app in the not too distant future.

By the way I have also successfully run the trial version of MapInfo version 9 on wine.

Have fun :)

---

### Post by Diptansu on 2008-07-12
Its a late reply ... and i m sorry for that ...

Actually i discovered myself what u said about the "qgis" command and icon ... (and it was a gr8 fun) 

I hvnt got time yet to check the GRASS website ... but surely i wd do it ...

Now i wd try to install any linux equivalent of AutoCAD ... if i get any trouble there i wd feel free to tell u ...:p

At last , I must thank u all  .... :)

---

