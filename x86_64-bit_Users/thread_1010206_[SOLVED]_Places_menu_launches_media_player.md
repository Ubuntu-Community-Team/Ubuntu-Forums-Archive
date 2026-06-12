---
title: "[SOLVED] Places menu launches media player"
date: 2008-12-13
forum: x86 64-bit Users
---

### Post by John Jason Jordan on 2008-12-13
Ubuntu Intrepid x86_64 upgraded from Hardy, nVidia 177 driver, Gnome desktop.

This has been reported as a bug, and discussed in other threads, but none of the fixes have worked for me.

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/260492]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/260492")

In my case when I opened any folder in Places > it would launch mplayer. From the above thread, uninstalling mplayer would just make it launch a different media app. Of course, it is supposed to launch Nautilus.

I edited .local/share/applications/mimeapps.list and replaced 

inode/directory=mplayer;

with

inode/directory=nautilus-folder-handler.desktop;

Per the instructions in the Launchpad bug report, but that makes it launch Dolphin, not Nautilus. 

Dolphin is the default file browser for the KDE desktop. I assume it got installed because I have installed a lot of KDE apps, even though my desktop is the standard Ubuntu Gnome desktop, not KDE.

This problem occurs only on my laptop. I also have a desktop computer, also upgraded from Hardy x86_64 to Intrepid, and the problem does not appear. I thought that a simple solution would be to copy the settings in .local/share/applications/mimeapps.list from the desktop to the laptop. However, I can't find the file on the desktop computer. Since the desktop computer seems to work fine without it, I renamed it on the laptop, but that didn't change anything.

Somewhere there is an association calling Dolphin instead of Nautilus. Does anyone know where it is?

---

### Post by drs305 on 2008-12-13
One of the suggestions (slightly modified) from that thread that normally works is to right click on any folder, select Properties, Open with other application, and select "File Browser". Did that not work?

---

### Post by John Jason Jordan on 2008-12-13
> **drs305 said:**
> One of the suggestions (slightly modified) from that thread that normally works is to right click on any folder, select Properties, Open with other application, and select "File Browser". Did that not work?

I had already tried that solution, but it does not work because when I right click on a folder or bookmark it just opens that folder or bookmark. Right clicking does the same as left clicking. Maybe there is a way to change that?

---

### Post by John Jason Jordan on 2008-12-13
[QUOTE=drs305]How about hitting F10 with a folder highlighted? Does that open up the Properties dialog box? [/QUOTE]

F10 just makes the focus disappear, however, I finally fixed it. 

I launched Nautilus from the command line, and then I could right click on a folder. However, there was still no Properties option, just "open in a new tab" or "open in a new window."

But that was on the top level places menu. If I opened Computer (filesystem) and then /home/jjj/ I was able to get a Properties dialog box for the /home/jjj folder. And sure enough, Dolphin was set as the default application.

I deleted Dolphin, but then none of the file browser windows would open - "no application to launch this item." So I went back to the Open With tab in the Properties dialog box and scrolled down looking for Nautilus, but it was not listed. Then I noticed a Custom button on the bottom. I clicked on it, typed "nautilus" in the window, and closed the Properties dialog box.

Voilà! Now everything opens with Nautilus again.

So the instructions on the Launchpad site were correct, they were just unclear. I didn't know I had to launch Nautilus from the command line in order to get a file on which I could set the properties. I thought I could go to Places > Home, and with Places > Home selected right click on it.

I'm going to add this comment to the thread in x86_64 users, then mark the thread Solved.

Thanks for the suggestions.

---

### Post by Varikk on 2009-03-10
I had a similar issue but only when launching from the toolbar/places
If I went to home or desktop or bookmarks from the places tab it would launch in dolphin not nautilus as i prefer.

1. To fix this I opened home from places and it opened in dolphin.  

2. In the tool bar go to  File.  
then properties

3. this brings up a dialogue box
you should now see the general tab

4. click on the looking glass icon

5. you should now see an application preference order select dolphin and click remove.

6.  and updating system box opens 

7.  after it closes shut down the window using dolphin and try and open it. 

for me nautilus is now the preferred file management ... i don't have any clue why it switched to the kde dolphin file manager when I udated but it did.

thanks for your help and gl

---

