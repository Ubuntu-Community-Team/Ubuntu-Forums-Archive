---
title: "change utorrent tray icon using Wine's %AppData% system variable"
date: 2007-12-06
forum: Wine
---

### Post by realthor on 2007-12-06
Hello, I am using gutsy and I have installed utorrent but I totally dislike the tray icon (because it takes the whole height of the panel making it look splitted by the icon - ugly anyway) .

I want to change it and the solution with alltray doesn't work for me -perhaps for gutsy also. I found this utorrent webpage ( [http://www.utorrent.com/skinning.php](http://www.utorrent.com/skinning.php) ) and found out that:

"tray.ico
    This is a standard Windows icon file. If tray.ico is found in %AppData%\uTorrent, it will replace the default icon in the system tray (bottom-right corner of your screen)." 

After some research I have found that in wine.inf (/home/username/.wine/drive_c/windows/inf/wine.inf) should have defined this variable but it is not defined there (wine 0.9.46). A patch I have found on [http://www.nabble.com/wine.inf:-set-APPDATA-tt13617493.html](http://www.nabble.com/wine.inf:-set-APPDATA-tt13617493.html) has the line to add for the AppData and it's:

HKLM,System\CurrentControlSet\Control\Session Manager\Environment,"APPDATA",,"%53%\Application Data" 

In Windows the %AppData% is reffering to C:\Documents and Settings\Username\Application Data\ . I have in Wine the C:/ drive but I don't know how to do to make Wine aware of this path (I can create it myself) so that utorrent see it and take the icon from there. And %53% is supposed to replace "C:\Documents and Settings\Username\" , and where can it be set?

Perhaps these info are of any help and someone can put them together to get a solution.

Any help would be appreciated.

---

### Post by shafin on 2007-12-07
I just placed the tray.ico at /home/username/.wine/drive_c/windows/profiles/shafin/Application Data/uTorrent folder and it worked for me,no changes were needed. However,I tested it with 5 different icon files from uTorrent skins page,from which one didnt work,I dont know why.

---

### Post by shafin on 2007-12-07
oops,double post.

---

### Post by realthor on 2007-12-09
I don't get it. I tried more than 10 icons from that page and I even tried with tray.ico and main.ico and the same ugly/non-transparent icon shows up. I am using latest Wine and latest utorrent...just don't get it. The other skin bitmaps work (toolbar., etc).

---

### Post by chochem on 2008-01-18
I tried the [alltray solution]("http://ubuntuforums.org/showthread.php?t=295134") but was disappointed as I lost the right-click options (pause, resume, etc.) so here's sort of a DIY solution. Simply put you edit the icon so it uses your system colours as background instead of relying on transparency, and edit a wine setting to match that colour.

Download an icon from [http://www.utorrent.com/skins.php](http://www.utorrent.com/skins.php) ("Program Icons")

Edit it in the GIMP
- First, if it has more layers, delete all but the one with with the biggest icon. Scale it to 16 by 16 pixels.
- Second, edit the background colour, choose the colour picker. We want the panel colour (system default in Gutsy is #edeceb, I think, at least on my system it is) so move the colour picker to the panel and get the panel colour and click ok. It should now be the background colour. Make a note of what this colour is in RGB.
- Third, focus the window with the icon open, enter the menu: Layer | Transparency | Remove alpha channel. This should supplant the transparent background with our background colour.
- Save it as "tray.ico".

Move the new tray.ico to the uTorrent Application Data directory in wine, which should be something along the lines of  /home/<user>/.wine/drive_c/windows/profiles/<user>/Application Data/uTorrent.

Enter wine configuration
- Make sure you're emulating Windows XP under the Applications tab.
- Click the tab Desktop Integration
- In the appearance section, open the 'Item' dropdown menu and choose 'Menu Background', click 'Colour' button and the 'Define custom colours'.
- Enter the Red-Green-Blue values you made a note of earlier. #edeceb translates as RGB: 237-236-235. Click 'Add to custom colours'. Choose the newly added custom colour and click ok and ok to exit wine configuration. You might wish to do the same for "Controls Background" in order for it to match in the program itself.

And that's it. Run utorrent and the icon should integrate nicely. Well, sort of. Choosing a square or semi-square icon will probably work better than round icons. Experiment :)

---

### Post by snakeboy on 2008-02-09
Thanks chochem!  After trying all sorts of different suggestions to replace the default icon, your method above was the only one that worked for me.  It's more of a workaround than a solution, but it does work!

[IMG]http://img138.imageshack.us/img138/4684/utorrentis3.jpg[/IMG]

Thanks again!

---

### Post by gamhead on 2011-02-20
This didnt work for me but I eventually found an answer here:
[http://ubuntuforums.org/showthread.php?t=1466473&page=4](http://ubuntuforums.org/showthread.php?t=1466473&page=4)

---

