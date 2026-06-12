---
title: "Color theme for Wine"
date: 2007-12-29
forum: Wine
---

### Post by Can+~ on 2007-12-29
I think everyone agrees that Wine default theme is pretty.. ugly. I've searched around, and found several posts on how to change it, so I'm compiling all that information, here.

**0. Customize?**
As everyone who has used windows, it's pretty difficult to customize, but the thing you can really customize on your first use, are the colors of the windows.

Each component on a normal windows has a name, and an attributed R G B color. You can edit this colors on the display settings on windows, or, in our case, you can edit them through the registry or 3rd party app. 

**1. How to customize**
**1.a The nice way** ([source](http://ubuntuforums.org/showthread.php?t=627631))

Install the application for windows xp (using wine.. of course) called 3D color changer (shareware, they accept donations):
[http://jote.pai.net.pl/jn/3dcc/](http://jote.pai.net.pl/jn/3dcc/)

Extract everything to your desktop, and run setup.exe it... If it doesn't run, make sure you extracted everything, and then try opening a shell and using:

> wine ~/Desktop/Setup.exe
The application consists on a example window (on the left), select an element, and under the name of the selected object, there's a color selector. It's pretty straightforward.

**1.b The ugly way**
Check for this file:

> gedit ~/.wine/user.reg
(Guessing you're on a gnome enviroment, KDE uses kate, etc)

This file stands for the "HKEY_CURRENT_USER" registry entry on a windows enviroment, using regedit. On a normal fresh wine installation, there should be a piece of text like this:

> [Control Panel\\Colors] 1198905015
(Important: That number, probably won't match with yours, don't change it!)

Under it you can add each component color using the following syntax:

> "NameOfTheComponent"="R G B"
Where R, G, and B are integers from 0 to 255 (1 unsigned byte ((2^8 )- 1)).

There are the possible tags:
> ActiveBorder ActiveTitle AppWorkspace Background
ButtonAlternateFace ButtonDkShadow ButtonFace
ButtonHilight ButtonLight ButtonShadow ButtonText
GradientActiveTitle GradientInActiveTitle GrayText
Hilight HilightText HotTrackingColor InActiveBorder
InActiveTitle InActiveTitleText InfoText InfoWindow
Menu MenuBar MenuHilight MenuText Scrollbar TitleText
Window WindowFrame WindowText

As this is would be a PAIN to edit manually, I already made a theme that is easy to copy-paste:
([Here is a screenshot](http://img.photobucket.com/albums/v517/CanXp/cantheme.jpg) for your delight)

> [Control Panel\\Colors] xxxxxxxxxxxxx (DON'T REPLACE THIS LINE!)
"ActiveBorder"="212 208 200"
"ActiveTitle"="34 85 234"
"AppWorkspace"="128 128 128"
"Background"="58 110 165"
"ButtonAlternateFace"="181 181 181"
"ButtonDkShadow"="206 206 206"
"ButtonFace"="233 232 231"
"ButtonHilight"="241 241 243"
"ButtonLight"="212 208 200"
"ButtonShadow"="183 183 183"
"ButtonText"="0 0 0"
"GradientActiveTitle"="137 184 235"
"GradientInActiveTitle"="192 192 192"
"GrayText"="128 128 128"
"Hilight"="10 36 106"
"HilightText"="255 255 255"
"HotTrackingColor"="0 0 128"
"InActiveBorder"="212 208 200"
"InActiveTitle"="128 128 128"
"InActiveTitleText"="212 208 200"
"InfoText"="0 0 0"
"InfoWindow"="255 255 225"
"Menu"="233 232 231"
"MenuBar"="212 208 200"
"MenuHilight"="10 36 106"
"MenuText"="0 0 0"
"Scrollbar"="212 208 200"
"TitleText"="255 255 255"
"Window"="255 255 255"
"WindowFrame"="0 0 0"
"WindowText"="0 0 0"


**1.c Even Uglier way**

Open a shell, and type (if wine is installed)
> regedit

Go to HKEY_CURRENT_USER/Control Panel/Colors. Is basically the same thing that opening the user.reg with the text editor, if you feel this is more comfortable, then knock yourselves out.

Happy theming.

References:
[Winehq user guide]("http://www.winehq.org/docs/en/wineusr-guide.html")
["Hairy_Palms" post]("http://ubuntuforums.org/showthread.php?t=627631")

---

### Post by Faud on 2007-12-29
Nice, great screenshot of WINE btw. Looks nice

---

### Post by Endolith on 2009-02-02
Also you can use this script to scrape the colors from GTK, so it matches your Gnome theme no matter what the colors.  It's not perfect, but it works decently with most engines:

[http://www.endolith.com/wordpress/2008/08/03/wine-colors/](http://www.endolith.com/wordpress/2008/08/03/wine-colors/)

---

