---
title: "Qt applications in Kubuntu 64"
date: 2006-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by rogeriovinhal on 2006-07-18
Hi, I am having some problems with Qt applications in Kubuntu 64.
First, Firefox32 looks crappy in appearence. I wish I could make it look like the common firefox, that is looking like common KDE applications.
But this is only appearance, I can live with that.

The worst problem is with OpenOffice. Not only it looks as crappy as Firefox32, but it just takes ages to first load, but when it does, the other loads are normal, about 5 seconds...

Does anyone know anything about that?

---

### Post by Kilz on 2006-07-18
In my signature is a link for setting up 32bit firefox with working plugins. The download is from mozilla, maybe it will look better for you. If you want speed of startup try koffice.

---

### Post by rogeriovinhal on 2006-07-18
Actually, I did install it from your HOWTO's script, thanks very much for it, it worked flawlwssly. :) 

The looks of the programs looks like if you run an Gnome Application in Gnome, and the colors are like all grey. It has no "KDE touch" in them.

I am attaching one snapshot of Firefox32 and OpenOffice with Konqueror open, so you can see the difference between an KDE application and these others.
And the other snapshot is the Firefox 64 bit version which looks ok.

---

### Post by Kilz on 2006-07-18
> **rogeriovinhal said:**
> Actually, I did install it from your HOWTO's script, thanks very much for it, it worked flawlwssly. :) 

The looks of the programs looks like if you run an Gnome Application in Gnome, and the colors are like all grey. It has no "KDE touch" in them.

I am attaching one snapshot of Firefox32 and OpenOffice with Konqueror open, so you can see the difference between an KDE application and these others.
And the other snapshot is the Firefox 64 bit version which looks ok.

The icon set is a gnome set, its the default set. You may want to select another icon set or "theme" Go to tools, themes, then click get more themes. Then look for a kde set, [like this one]("https://addons.mozilla.org/firefox/1905/") then click the install link.
Then set it as the default set in themes window, highlight it, then click "Use Theme". Then restart firefox.

---

### Post by rogeriovinhal on 2006-07-18
Actually, I'm not complaining about the icons.
See that the window is completely different from the Firefox 64 to the Firefox 32?
It seems that everything about the window is drawn different, even the colors.

---

### Post by Kilz on 2006-07-18
> **rogeriovinhal said:**
> Actually, I'm not complaining about the icons.
See that the window is completely different from the Firefox 64 to the Firefox 32?
It seems that everything about the window is drawn different, even the colors.
To tell you the truth I dont see much of a diffrence. The only diffrence I see is that there are dividing lines between the text and icons. Background color is sometimes part of a theme. You might want to change it to see if there is any diffrence. 
Not seeing the difference may have to do with the fact Im using gnome. There is one thing we could try. Since you are using kubuntu the gtk export may be changing something. /usr/local/bin/firefox32 and edit out the "export GTK_PATH=/usr/lib32/gtk-2.0" line and see what happens after you restart firefox.

---

### Post by rogeriovinhal on 2006-07-18
That didn't do anything different... :( 

It seems that this is some kind of bad conversion of the conversion KDE does to GTK windows to his ones. I now took 3 snapshots, the first is by running the firefox32 directly by its folder (/usr/local/firefox32) with the command ./firefox, it seems like an original GTK application.

The second one is the "no KDE neither GTK" application, since it only changes the colors to KDE colors.

The third one is the completely KDE application, which is the firefox 64 bits. As you can see, there are some differences to the colors gradient, the fonts, even the icon at the taskbar, that showed only an X in firefox32...

---

### Post by Kilz on 2006-07-18
> **rogeriovinhal said:**
> That didn't do anything different... :( 

It seems that this is some kind of bad conversion of the conversion KDE does to GTK windows to his ones. I now took 3 snapshots, the first is by running the firefox32 directly by its folder (/usr/local/firefox32) with the command ./firefox, it seems like an original GTK application.

The second one is the "no KDE neither GTK" application, since it only changes the colors to KDE colors.

The third one is the completely KDE application, which is the firefox 64 bits. As you can see, there are some differences to the colors gradient, the fonts, even the icon at the taskbar, that showed only an X in firefox32...
My howto/scripts download firefox the mozilla download site. Its possible that Ubuntu/Kubuntu changes something to make it fit into the distro better. Im going to have to look into this to see what changes I can make.

---

### Post by Kilz on 2006-07-18
I think it has to do with the fact that there are 32bit qt libraries. I have tried to get the 64bit ones to work, but no such luck. Ill keep looking.

---

### Post by Kilz on 2006-07-19
You can try
```
sudo apt-get install ia32-libs-kde
```
But it may not help much. It may help open office more. I installed kubuntu in a virtual machine to see what was going on. You are correct that the widgets do not draw correctly. But this is not something that is unique to my script. Swiftfox dose exactly the same thing. It has to do with us forceing a 32bit application into a 64bit setup. You may be better off running a [chroot]("http://www.ubuntuforums.org/showthread.php?t=157412"). But there may be diffaculties setting it up that I am not aware with kde since I use gnome exclusivly.

---

