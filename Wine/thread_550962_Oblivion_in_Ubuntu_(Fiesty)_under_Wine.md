---
title: "Oblivion in Ubuntu (Fiesty) under Wine"
date: 2007-09-14
forum: Wine
---

### Post by darthlunchbox42 on 2007-09-14
I'm very new to Ubuntu, I just installed it yesterday, and I have been screwing around with it since then, so when I say that I have no idea what I'm doing in any way, believe me.  In relation to Ubuntu, I'm still learning how to breath.  I realize that there have been a few thread over the same subject as this, but I found none that helped with my specific problems.

However, I just came upon [this]("http://ubuntuforums.org/showthread.php?t=349764") information about playing Oblivion in Ubuntu with Wine, and Oblivion being one of my favorite games, I decided to give it a go.  I figured parts of it out, but I ran into some trouble with it.  Below, I've quoted which parts I'm having trouble with and a short description of my troubles.  If anyone could help or point me in the right direction, that would be greatly appreciated.  Thanks!

> Desktop Integration tab.

Here you should make a folder as your 'Windows folder base' and populate it. I use ~/Documents/Windows/. After you make these folders match them up in this interface, since Oblivion follows the logo requirements and uses a 'My Games' folder.

```
mkdir -p ~/Documents/Windows/{Desktop,Documents,Pictures,Music,Video}
```

When I put the mkdir code into the terminal and press enter, nothing happens.  No folder is created or anything like that.


> Drives tab.

Add a new drive for example 'D:' and click Show Advanced to set it as a CDROM drive. Browse to the mount point for your Oblivion DVD or loopback image. In my example it's '/opt/games/Windows/CDROM/'.


If you have the space I'd suggest copying your Oblivion DVD to a disk image, so you can keep it in your Collector's box. You all bought the Collector's Edition didn't you? Well you should it has some cool stuff. Here's a handy, dandy bash script to mount your Oblivion.iso.

```
#!/bin/sh
ISO=/opt/iso/Oblivion.iso
sudo mount -o loop -t iso9660 $ISO /opt/games/Windows/CDROM/
```

I added a new drive and made it a CD ROM drive, but I don't know what it means by browsing to the mount point.  Also, in my /opt directory, there is nothing there, and I need to be root to do anything to it, I believe.

> 5. Registry editing in Wine. Run the command below and it'll pop-up a Wine version of regedit.

```
wine regedit.exe
```

Now browse HKEY_CURRENT_USER / Software / Wine / Direct3D. Right click in the pane to make New > String Value for each of the following key pairs:

```
OffscreenRenderingMode	fbo
	UseGLSL					enabled
	VideoMemorySize		256
```

I browsed to HKEY_CURRENT_USER / Software / Wine, but there was no Direct3D folder under that.  This might change if I figure out how to do the previous steps, but I don't know.

---

### Post by Dark Aspect on 2007-09-14
Well the mkdir command should have worked I am little confused on why it would not,check the path name is my best guess.I do know how to fix the 3rd problem though.In the registry you have to create your own Direct3D folder by right clicking on wine and select new key.Then to add the OffscreenRenderingMode_fbo,right click on the new key you created and enter a new string.

---

### Post by darthlunchbox42 on 2007-09-14
Sweet, thanks.  You were right about the first problem, I was just typing something in wrong, figures.  And I fixed my third problem.

The second one still stands, though.  There is nothing in the /opt folder, at least that I can see.  And from looking at the directory's properties, I need to be root to do anything to it.  This is where my complete lack of Linux experience comes into play: I don't know how to do anything with this root business.  :confused:

---

### Post by Jerryfan on 2007-09-14
[http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux)

This guide is a little more thourgh. YOu have to create the Direct3D folder if you dont have it.

---

### Post by darthlunchbox42 on 2007-09-15
Alright, so with setting the path of the D:\ drive, how am I supposed to do that?  Am I supposed to pop the Oblivion DVD in and do something with it, or go in and create the directories manually?  And I need to have root access to do anything in the /opt directory.  I have the password, but it doesn't let me do anything, much less prompt me for the password.

---

### Post by Mariano Oliveto on 2007-11-27
> **darthlunchbox42 said:**
> Alright, so with setting the path of the D:\ drive, how am I supposed to do that?  Am I supposed to pop the Oblivion DVD in and do something with it, or go in and create the directories manually?  And I need to have root access to do anything in the /opt directory.  I have the password, but it doesn't let me do anything, much less prompt me for the password.

If you don't know the path of your DVD drive one thing you can do is insert the Oblivion DVD in your drive. This should automatically mount your DVD and an icon should appear in your Ubuntu Desktop. There you can double click on the icon and a File Browser Window will pop. There you can either see the path by pressing the button right below the next button (this button toggles between button-based and text-based location bar) or pressing the UP button and then see if your DVD is mounted in /media/cdrom0 or  /media/cdrom1 (maybe just /media/cdrom).

To sum up:

1) Insert Oblivion (or any other) DVD
2) Wait till automount DVD icon appears in the Ubuntu Desktop
3) Double click the "automounted" DVD icon to show its contents in File Browser
4) Find out the path of the DVD by looking at the location bar or browsing

Once you know the path go to the Wine Configuration ("Applications -> Wine -> Configure Wine" or type "winecfg" in terminal) and to the Drives section. Then click on D: and type the path in the "Path" text box below. Then click on Apply or OK.

I'm not sure but I think that the /opt folder will be empty unless you install the game in that path or you copy the files there (At least mine was empty and I didn't have to use it at all). Just be careful when you use the suggested sh script: change the "OBLIVION_DIR=" line to the path where you chose to install the game. Mine was /home/username/.wine/drive_c/Program\ Files/Bethesda\ Softworks/Oblivion/ because I chose the default installation path (c:\Program Files\Bethesda Softworks\Oblivion) and Wine makes the install shield (or whatever) think that C: is /home/username/.wine/drive_c/ (or the path you specified in the Drives tab ;) )

Beware with this path though because it is tricky to set the Oblivion.sh script (I omitted the OBLIVION_DIR line and directly used cd  /home/username/.wine/drive_c/Program\ Files/Bethesda\ Softworks/Oblivion/) If you have doubts about this post again and I will explain.

Good luck!!! :D

---

