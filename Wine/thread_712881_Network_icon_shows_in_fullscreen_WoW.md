---
title: "Network icon shows in fullscreen WoW"
date: 2008-03-02
forum: Wine
---

### Post by Lidnillek on 2008-03-02
Hey guys, 


Im pretty new to Ubuntu, and I've been trying to get World of Warcraft working, and after using other guides and threads on this forum, Ive nearly got it how I want it! only two small problems.....

1. When the game is in full screen, the network icon at the top of the screen flashes randomly, I cant click it, If i click off it, nothing happens
                                                                                                                       
[IMG]http://i13.photobucket.com/albums/a293/Kellindil967/Screenshot-01.jpg[/IMG]

If anyone has any idea how to get rid of this thing, that'd be awesome :)

2. I cant seem to open the game from my desktop....i created a file that i called *script.sh *, which has 

```
wine /home/corey/Desktop/WoW/WoW.exe
```

in it, but i dont know how to get it to automatically run? when i type that command into a terminal, wow starts up, but how do i make a file on the desktop to run it? (ive tried making a link to the WoW.exe, but that doesnt work either)


thanks in advance for any help, Lid

---

### Post by ssj3strife on 2008-03-10
Try going to Wine configuration, and under the Graphics tab, toggle the checkbox labelled "Allow the window manager to control the windows." It might get the network icon off there, but it might make things worse too. Alternatively, you could run a "killall nm-applet" before you start the game. Not really a fix, but it looks like you're using a wired ethernet connection, so I don't think it would really matter. You could use the script you wrote to run the killall command, then bring nm-applet back once the game exits. Quick and dirty. :)

As far as the script goes, did you remember to make it executable? chmod +x script.sh

---

### Post by spartan_87 on 2008-09-06
I know this thread is kind of old but iv found if you right click on your top toolbar and go to properties and choose autohide, the bar will stay minimized and you wont see the network manager icon in game anymore. I was having the same problem and saw this thread.

---

