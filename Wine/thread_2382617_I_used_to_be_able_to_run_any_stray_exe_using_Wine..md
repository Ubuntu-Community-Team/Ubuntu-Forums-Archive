---
title: "I used to be able to run any stray exe using Wine. No longer an option?"
date: 2018-01-15
forum: Wine
---

### Post by Mugsy323 on 2018-01-15
I recently reinstalled Wine (actually, I had to reinstall Ubu en total from scratch), and I *used to* be able to run ANY exe simply by double-clicking on it.

Now suddenly, I can't do this anymore. "Wine" isn't even listed as an "Open With" option. :(

It appears that Wine will now only run apps that are *installed* under the Wine interface ("Wine Tricks"). Is that accurate? :P

I sure liked the old way better. I don't wish to install a *second* copy of every Windows app already installed on my (dual boot) PC.

---

### Post by TheFu on 2018-01-15
WINE never worked that way for me for any non-trivial application.

Always had to install within the WINE environment.
Sometimes had to use different WINE setups for different programs because the required total environment for each was different.

---

### Post by Mugsy323 on 2018-01-16
Thanks for the reply, but I used Wine that way going back to Ubu 9.04.

I wanted to install a program I wrote myself using Wine, but since it does not appear in the list of known apps, there is no obvious way to install it.

It's ridiculous that Wine can only run a select few apps from a pre-approved list that must be downloaded by Wine. That's nuts.

---

### Post by deadflowr on 2018-01-16
It's a known bug.
See another thread on same issue:
[https://ubuntuforums.org/showthread.php?t=2376225&p=13706821#post13706821]("https://ubuntuforums.org/showthread.php?t=2376225&p=13706821#post13706821")
And the bug report: [https://bugs.launchpad.net/ubuntu/+source/wine-development/+bug/1576326]("https://bugs.launchpad.net/ubuntu/+source/wine-development/+bug/1576326")
> It's ridiculous that Wine can only run a select few apps
Indeed

---

### Post by Mugsy323 on 2018-01-17
Okay, I found a "cheat". :D (This is was done using Ubuntu 17.10.)

**First, the long way (to understand what's going on.)** Skip to the section in [COLOR="#FF0000"]Red[/COLOR] below if you don't need the details. ;)

First, if you haven't already, install the Wine interpriter and "Wine Tricks". Copy whatever Windows program you wish to install to Ubuntu's "Downloads" folder.

Launch "Wine Tricks" and select any of the 3 "Install" options just to get past the first menu.

When the second menu showing apps you may download/install comes up, click Cancel to get to menu 2 (is there a more direct way?)

Select "**Run taskmgr**" from the menu and click OK. The Windows Task Manager will appear.

Under "File", click "**New Task**" and "Browse" to Ubu's "Downloads" folder to find your app.

If your program is a standalone exe with nothing to install, that's it. Simply run your app. If it is an "installer", it's a bit more involved. :o

If your exe is an Installer/Setup app, run it. Windows apps typically install to the "Program Files" (or "Program Files (x86)" folder, but many allow you to install your app to a different folder/location. It doesn't really matter, but an easier to find/remember folder is easier. 

*The "Task Manager" can't browse the Wine folder* (only Ubu's) to run your newly installed app, so we need to do it from the Wine CLI (for now.)

Close the "Task Manager" and return to Wine menu 2.

Select "**Run a commandline shell (for debugging)**" to open the Wine CLI. The starting path will be Wine's "C" drive.

If you are familiar with DOS, just change folders till you find your installed app's exe. 

If you don't know DOS, type "**dir**" for a directory to list the files/folders on Wine's virtual c_drive. Use "**cd**" to **C**hange the current **D**irectory to that of your app (type the folder name *exactly* as it appears in the directory listing. Ex: "cd Program\ Files\ (x86)") Keep doing this till you have changed to the folder containing your exe.

Once you've located your .exe, type "**wine** " followed by the exe name (ex: wine MyApp.exe) and press enter. Your app will then run! :D

**Leave the CLI window open so you can see the exact path for the steps below.**


**[COLOR="#FF0000"]Now, of course, you don't want to go though all this hassle every time you wish to run your app, so we'll put a shortcut on the Desktop.[/COLOR]**

If you have already installed a Wine-compatible app with shortcut on your desktop, simply clone the shortcut (copy/paste) and rename it. If not, install something small/simple using Wine just for the shortcut. (I'm not sure how to create a null shortcut from Ubu.) Shortcuts to *existing* folders/apps can be created by simply holding Shift/Ctrl while dragging your icon to the Desktop.)

Right-click for "Properties" of your cloned Windows/Wine app shortcut and replace the path/filename to that of your own exe (ex: **env WINEPREFIX="/home/*MyAccountName*/.wine" wine-stable C:\\Program\ Files\ \(x86\)\\Notepad\\notepad.exe**). You can change the icon by clicking on the icon image (in the "Properties" dialog) and replacing it with any picture file.)

Now you can run your custom Windows app right from the desktop at any time (if you get the "Trusted App" dialog, just OK it.) :D

I can once again run most any Windows application using wine. I'm sure others will find this useful. Any idea how to get a post *pinned?*

---

### Post by Mugsy323 on 2018-01-17
Long ago, you used to be able to run ANY Windows executable by simply double-clicking an .exe file and running it using Wine. This no longer appears to be the case (likely for safety/security reasons), but I found a "cheat". :D
(This is was done using Ubuntu 17.10. the Wine interpreter & "Wine Tricks" installed.)

**First, the long way (to understand what's going on.)** Skip to the section in [COLOR="#FF0000"]Red[/COLOR] below if you don't need the details. ;)

First, copy whatever Windows program you wish to install to Ubuntu's "Downloads" folder.

Launch "Wine Tricks" and select any of the 3 "Install" options just to get past the first menu.

When the second menu showing apps you may download/install comes up, click Cancel to get to menu 2 (is there a more direct way?)

Select "**Run taskmgr**" from the menu and click OK. The Windows Task Manager will appear.

Under "File", click "**New Task**" and "Browse" to Ubu's "Downloads" folder to find your app.

If your program is a standalone exe with nothing to install, that's it. Simply run your app. If it is an "installer", it's a bit more involved. :o

If your exe is an Installer/Setup app, run it. Windows apps typically install to the "Program Files" (or "Program Files (x86)" folder, but many allow you to install your app to a different folder/location. It doesn't really matter, but an easier to find/remember folder is easier.

*The "Task Manager" can't browse the Wine folder* (only Ubu's) to run your newly installed app, so we need to do it from the Wine CLI (for now.)

Close the "Task Manager" and return to Wine menu 2.

Select "**Run a commandline shell (for debugging)**" to open the Wine CLI. The starting path will be Wine's "C" drive.

If you are familiar with DOS, just change folders till you find your installed app's exe.

If you don't know DOS, type "**dir**" for a directory to list the files/folders on Wine's virtual c_drive. Use "**cd**" to **C**hange the current **D**irectory to that of your app (type the folder name *exactly* as it appears in the directory listing. Ex: "cd Program\ Files\ (x86)") Keep doing this till you have changed to the folder containing your exe. (Note: If your file/folder contains spaces or other non-alphanumeric characters, either precede each non-letter with a "\" or enclose the path in quotes.)

Once you've located your .exe, type "**wine** " followed by the exe name (ex: wine MyApp.exe) and press enter. Your app will then run! :D

**Leave the CLI window open so you can see the exact path for the steps below.**


**[COLOR="#FF0000"]Now, of course, you don't want to go though all this hassle every time you wish to run your app, so we'll put a shortcut on the Desktop.[/COLOR]**

If you have already installed a Wine-compatible app with shortcut on your desktop, simply clone the shortcut (copy/paste) and rename it. If not, install something small/simple using Wine just for the shortcut. (I'm not sure how to create a null shortcut from Ubu.) Shortcuts to *existing* folders/apps can be created by simply holding Shift/Ctrl while dragging your icon to the Desktop.)

Right-click for "Properties" of your cloned shortcut and replace the path/filename to that of your own exe (ex: **env WINEPREFIX="/home/*MyAccountName*/.wine" wine-stable C:\\Program\ Files\ \(x86\)\\Notepad\\notepad.exe**). You can change the icon by clicking on the icon image (in the "Properties" dialog) and replacing it with any picture file.)

Now you can run your custom Windows app right from the desktop at any time (if you get the "Trusted App" dialog, just OK it.) :D

---

### Post by QIII on 2018-01-17
Threads merged.

---

### Post by QIII on 2018-01-17
No.  You duped your post by duplicating it elsewhere.  Please do not create duplicate posts.

---

### Post by ejbiow on 2018-05-06
Or you can just install a file manager other than nautilus/files, which seems to be stripping out more functionality and customizability with every single release.  

I suggest nemo. Then just go to an .exe file, right-click and select properties, at the bottom you will see 'Enter a custom command...', type in wine (or /usr/bin/wine), hit the "Set as default" button, and presto, even naught-of-use, er... nautilus will have wine set as the default application.

---

### Post by Mugsy323 on 2018-05-06
> **ejbiow said:**
> Or you can just install a file manager other than nautilus/files, which seems to be stripping out more functionality and customizability with every single release.  

I suggest nemo. Then just go to an .exe file, right-click and select properties, at the bottom you will see 'Enter a custom command...', type in wine (or /usr/bin/wine), hit the "Set as default" button, and presto, even naught-of-use, er... nautilus will have wine set as the default application.

I'll look into it. Thx.

---

### Post by Mugsy323 on 2018-05-08
> **ejbiow said:**
> I suggest nemo.

I've finally gotten around to trying this.

"Nemo" is not found in the Software Store so I used apt-get, but even after installing, nothing is different. Do I need to change something else? Is there a way to configure "Nemo"?

---

### Post by ejbiow on 2018-05-14
> **Mugsy323 said:**
> I've finally gotten around to trying this.

"Nemo" is not found in the Software Store so I used apt-get, but even after installing, nothing is different. Do I need to change something else? Is there a way to configure "Nemo"?

Nemo is highly configurable, even more so than nautilus was before Gnome started making it so simple it is just about my least favorite file manager in Linux-dom. Just left-click on the file, choose properties, then select the 'Open with' tab and type in *wine*.
[https://tinyurl.com/y7xzz4rp](https://tinyurl.com/y7xzz4rp)

---

### Post by monkeybrain20122 on 2018-05-14
You can still do it by copying/linking wine.desktop to /usr/share/applications

```
sudo cp /usr/share/doc/wine-stable/examples/wine.desktop /usr/share/applications/
```

or
```

sudo ln -s /usr/share/doc/wine-stable/examples/wine.desktop /usr/share/applications/
```

Then wine windows program loader will show up in the nautilus' "open with" list.

---

### Post by Mugsy323 on 2018-05-15
> **ejbiow said:**
> Nemo is highly configurable, even more so than nautilus was before Gnome started making it so simple it is just about my least favorite file manager in Linux-dom. Just left-click on the file, choose properties, then select the 'Open with' tab and type in *wine*.
[https://tinyurl.com/y7xzz4rp](https://tinyurl.com/y7xzz4rp)

Thanks. This seems to have helped some, though my success rate getting Windows apps to run under Wine still seems to be below 50%.

(Tip for future readers of the thread: You must type "wine" to add the app to the list of "Open With" apps. Typing "Wine", won't work. Case sensitive.)

---

### Post by cesarcruz on 2018-06-02
> **monkeybrain20122 said:**
> You can still do it by copying/linking wine.desktop to /usr/share/applications

```
sudo cp /usr/share/doc/wine-stable/examples/wine.desktop /usr/share/applications/
```

or
```

sudo ln -s /usr/share/doc/wine-stable/examples/wine.desktop /usr/share/applications/
```

This works for me. Thanks!!

> **monkeybrain20122 said:**
> Then wine windows program loader will show up in the nautilus' "open with" list.

---

