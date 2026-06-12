---
title: "[SOLVED] I did something stupid... how do I uninstall this application?"
date: 2008-03-07
forum: Wine
---

### Post by noobuntu7 on 2008-03-07
OK... please don't laugh. I did something super-stupid and I can't believe that I did it. I am using Xubuntu 7.10 and I installed Wine, mainly just to see if it would work with some very old Windows games I had lying around. Once I installed Wine, I thought I would see if it would even work by trying to install a game from it's CD (the game was called Lemmings Revolution).

So I ran the installer, and I chose to install it in **Compact** mode (this means with the minimum amount of software for the game to run). The installer seemed to work fine, and then when it was done I got an error message that said "DirectX is not compatible with your version of Windows".

 It wouldn't let me play the game, so I tried to figure out a way of uninstalling it (I didn't know at the time that there was a **Uninstall Wine Software** program). I tried something *really* stupid... I went into the .wine folder and I tried to delete the game manually out of it's libraries. Well, when I did that... apparently I didn't remove all of the game files. It was still listed in my Applications drop-down list (under **Other**). So I tried using the file manager and selecting "show hidden folders" and then deleting the .exe file... I thought that would surely remove the game, it didn't. 

Then when I found out that Wine had an **Uninstall Wine Software** button, I tried it and it would start the uninstaller and then say that there was no uninstaller.exe and it wouldn't uninstall it.

I tried using Add/Remove programs, and Synaptic Package Manager, but they only can uninstall apps that are in their libraries of apps for Ubuntu (not software you install from a CD).

Then I tried searching for it in nautilus, and it gives me an error message every time I try to search for anything: "The name org.freedesktop.Tracker is not in the .service files". So I can't search for anything there. (By the way, **WHY** doesn't Xubuntu come with a search function like Windows? It should be right in the applications list! Something like: "Search for files on your system").

Is there anything I can do? If you need more info or clarification I'll be glad to add some. Thanks in advance.

---

### Post by Lacrimstein on 2008-03-07
I don't think its because you didn't remove all the files, but rather that you left the shortcut in the menu (similar to windows; if you remove game files, the launcher in the main menu would still be there - but it wouldn't work, of course). You have to edit the menu manually to get it out. Right click on the menu button, and select "customize menu".

---

### Post by insineratehymn on 2008-03-07
You could just delete the whole folder in the wine subdirectory of your home folder...

rm -r ~/.wine/drive_c/Program\ Files/NAME OF FOLDER

Nautalis' search function... yeah... I don't suggest it.

If you like the whole windows/vista'esque feel, I would look into KDE4.

I think that even KDE is calling that Beta right now, but it looks pretty and it keeps my attention.

You know. The bright colors and whatnot.

Oh! Edit:

If you want to search from something, use the locate command!

First update the index, from a console type this:

sudo updatedb

Then search for anything you want!

locate happytonenailfungus

It will then gladly search EVERYTHING.

If you have a massive hard drive it may take a minute to do the updatedb, but I think it does it automatically at midnight or something.

---

### Post by Victormd on 2008-03-07
Also, if you are familiar with the windows registry, you can use wine regedit to remove any signs of Lemmings from the registry (just like in windows).
If you want to try again, you can try configuring WINE to run as Windows 95 (under Wine configuration) and see if that works. I don't remember if it has Win3.1 or anything less than Windows 95, but it's worth a shot.

---

### Post by noobuntu7 on 2008-03-07
Thank you so much insineratehymn,
You helped me a lot with the **sudoupdatedb** and then **locate** commands. I had tried using the **locate** command before, but it never worked because I hadn't updated the database (and I know you aren't supposed to, but I shut the system off at night). I found the remaining Lemmings files and then deleted them, problem solved. God bless and thanks for the help!

Shalom,
noobuntu7

---

### Post by insineratehymn on 2008-03-08
Thanks for the thanks!

If you need anything else I troll the unanswered posts quite often.

:)

---

