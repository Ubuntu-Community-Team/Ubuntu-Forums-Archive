---
title: "Problems with fresh 9.04 installation"
date: 2009-09-12
forum: x86 64-bit Users
---

### Post by purity89 on 2009-09-12
I just installed Ubuntu 9.04 after a long period of just using XP, but I'm having some issues. I left the computer on for a couple of hours today, and when I returned I had several problems.

 - I think my ext3 partition have gone "read-only" on me
When I browse any part of the "File System" folders, or my users Documents/Music etc. folders and right click, "Create Folder" and "Create Document" is grayed out, and I can't use them

 - When I try open Terminal, Add/Remove..., OpenOffice, System Monitor or any other applications I just get blank windows without any context. I tried opening xterm by pressing Alt+F2 and typing in xterm, and that worked. When I type in gnome-terminal in xterm I get this output:

```
/home/purity/.themes/Dust Burnt/gtk-2.0/gtkrc:172: Unable to locate image file in pixmap_path: "toolbar_light.png"

/home/purity/.themes/Dust Burnt/gtk-2.0/gtkrc:174: Background image options specified without filename

(Might contain mistakes, as I couldn't copy from xterm
```

Also, I can't download files using Chromium, the save-window never appears, and Firefox won't even open. When try to open it I get "Starting Firefox ..." in the bottom panel, and after a while "Close Firefox" appears. I don't get any windows, just the text in the bottom panel, and I have to right click "Close Firefox" and close it to remove it. When I try and open Firefox via xterm I just get the same errors as above, and "Close Firefox" appears after a while.

I have Ubuntu 9.04 for 64-bit installed, and I've installed simple-ccsm, Chromium and done part 1 of the "Comprehensive Multimedia & Video Howto" from the forum. EDIT: And I have installed the latest Nvidia drivers (180-something I think?) via Add/Remove.

This only happens after the computer has been on for a while, when I restart everything is back to normal.

I'm hoping I could solve these problems somehow, as I really love Ubuntu, and would hate to return to Windows XP.

---

### Post by dumblebee100 on 2009-09-12
> **purity89 said:**
> I just installed Ubuntu 9.04 after a long period of just using XP, but I'm having some issues. I left the computer on for a couple of hours today, and when I returned I had several problems.

 - I think my ext3 partition have gone "read-only" on me
When I browse any part of the "File System" folders, or my users Documents/Music etc. folders and right click, "Create Folder" and "Create Document" is grayed out, and I can't use them

 - When I try open Terminal, Add/Remove..., OpenOffice, System Monitor or any other applications I just get blank windows without any context. I tried opening xterm by pressing Alt+F2 and typing in xterm, and that worked. When I type in gnome-terminal in xterm I get this output:

```
/home/purity/.themes/Dust Burnt/gtk-2.0/gtkrc:172: Unable to locate image file in pixmap_path: "toolbar_light.png"

/home/purity/.themes/Dust Burnt/gtk-2.0/gtkrc:174: Background image options specified without filename

(Might contain mistakes, as I couldn't copy from xterm
```

Also, I can't download files using Chromium, the save-window never appears, and Firefox won't even open. When try to open it I get "Starting Firefox ..." in the bottom panel, and after a while "Close Firefox" appears. I don't get any windows, just the text in the bottom panel, and I have to right click "Close Firefox" and close it to remove it. When I try and open Firefox via xterm I just get the same errors as above, and "Close Firefox" appears after a while.

I have Ubuntu 9.04 for 64-bit installed, and I've installed simple-ccsm, Chromium and done part 1 of the "Comprehensive Multimedia & Video Howto" from the forum. EDIT: And I have installed the latest Nvidia drivers (180-something I think?) via Add/Remove.

This only happens after the computer has been on for a while, when I restart everything is back to normal.

I'm hoping I could solve these problems somehow, as I really love Ubuntu, and would hate to return to Windows XP.


I too faced this problem ..this is caused by the ext4 file system and kernel related because when jaunty is release ext4 is rather new and buggy ...so after a while the files appears as read only ...

but there is a workaround for it ...when I used jaunty with ext4 ..and when I get readonly files then I would close all the nautilus things and start over

right now these bugs are eliminated ..now I use karmic koala alpha 5 ext4 and everything is fine 

it clearly states that it has mistakes ...well I can edit gtkrc files and I know what that error means ( the gtkrc needs some png file and it didnt get it so cannot display ...well if gtkrc has some mistakes then it will take default theme ..but your error is very rare ..just provide that files and u may be ok ...I should ask which version of jaunty did u installed ..stable or alpha ones ....because stable ones dont have almost any bugs 

as discussed above .the file permissions I think so ..but Im not sure about this .....why dont u try to load from terminal and see output in terminal ..that may help you

---

### Post by purity89 on 2009-09-12
The first time I installed 9.04, a couple of days ago, did indeed use ext4, but that gave me even more trouble. So gave up on that and did a fresh install with ext3 instead. So I don't think that is the problem.

I've switched to another theme now, and I'll check if I still get the same error messages when trying to start terminal from xterm (just have to wait for everything to go downhill first :P).

I'm fairly confident I installed a stable version of Jaunty. But what do you mean by "why dont u try to load from terminal and see output in terminal" ? Load what from terminal?

By the way, the system locked completely up on me a short while after my first post, nothing, not even the mouse (neither mousepad nor bluetooth mouse), so I had to force the system to a reboot. When I rebooted I got a message that I had a bad shutdown or something like that, and that I had to run fsck. I did that and got lots of errors that needed to me fixed.

---

### Post by dumblebee100 on 2009-09-12
> **purity89 said:**
> The first time I installed 9.04, a couple of days ago, did indeed use ext4, but that gave me even more trouble. So gave up on that and did a fresh install with ext3 instead. So I don't think that is the problem.

I've switched to another theme now, and I'll check if I still get the same error messages when trying to start terminal from xterm (just have to wait for everything to go downhill first :P).

I'm fairly confident I installed a stable version of Jaunty. But what do you mean by "why dont u try to load from terminal and see output in terminal" ? Load what from terminal?

By the way, the system locked completely up on me a short while after my first post, nothing, not even the mouse (neither mousepad nor bluetooth mouse), so I had to force the system to a reboot. When I rebooted I got a message that I had a bad shutdown or something like that, and that I had to run fsck. I did that and got lots of errors that needed to me fixed.


loading from terminal means opening a terminal and launching application from it ...just like 
```
sam@sam-desktop:~$ gedit 

(gedit:7139): Gtk-WARNING **: Theme directory 48x48/emotes of theme hydroxygen has no size field


(gedit:7139): Gtk-WARNING **: Theme directory 48x48/actions of theme hydroxygen has no size field


(gedit:7139): Gtk-WARNING **: Theme directory 48x48/apps of theme hydroxygen has no size field

```

well here I get some warnings 
Im asking what ru getting from the terminal output ...bcz that may reveal solutions for many of ur problems 



yeah when you do a hard boot then the file system crashes( its not the correct word but its close ) ..I mean there will be errors which should be corrected before it is mounted again ..so during boot process ....before the partitions get mounted ..the fsck does its thing ..and corrects filesystems ....sometimes it falls back to shell and ask us to do a manual fsck ....

or else we can do a complete fsck even when we are in gui ...ie by unmouting partition and then doing fsck ..anyways you cant unmount root partition ..so that should be done only during boot time 



and regarding your system response I have no idea .why your system gets stuck ..I used jaunty long time back 32 bit edition ...it was cool to use ...even after one day full usage my memory doesnt exceed 400mb and cpu is amost less than 5 percent all the time .unless any major firefox activity


did u have correct graphics drivers and what background activities are going on during that stuck up

---

### Post by purity89 on 2009-09-12
I haven't had any errors or crashes yet, so it seems as if though it was only the theme I was using that was causing my problems. That seems weird though, I thought that was a popular theme, used by many? Others should be experiencing the same problems...

I tried loading lots of apps from terminal, and didn't get any error messages.

I'll leave my computer running through the night, and see if there are any errors then.

One last thing, I'm running Transmission to download some large Blu-Ray rips, and because of this (it seems) my two cpu's are alternating between 100% load, so my fan is constantly running at high speeds. Funny thing is that I can't see any processes in System Monitor that are using cpu power. Is this a common problem with Transmission? I'm installing uTorrent tomorrow.

I've attached a picture of what my cpu usage graphs look like.

---

### Post by David-IT on 2009-09-12
well i never really had any problems with ext4 file system but i only used it for like a couple minutes due to permission problems with files in Home i am on ext3 know with no problem's :D

---

### Post by purity89 on 2009-09-13
Okay, now something has happened again. I can't save files, create folders or anything like that on my *ext3* partition (where Ubuntu is installed) and programs have empty windows when I try and run them. When I run gnome-terminal via xterm I get no error messages, but when i run gedit I get these:

```
$ gedit

** (gedit:31089): WARNING **: Cannot create the 'gedit' connection.

### After closing the gedit window:

(gedit:31089): Gtk-WARNING **: Attempting to store changes into `/home/purity/.recently-used.xbel', but failed: Failed to create file '/home/purity/.recently-used.xbel.ETHPZU': Read-only file system

(gedit:31089): Gtk-WARNING **: Attempting to set the permissions of `/home/purity/.recently-used.xbel', but failed: Read-only file system

** (gedit:31089): CRITICAL **: bacon_message_connection_free: assertion `conn != NULL' failed

** (gedit:31089): WARNING **: Could not write gedit state file: Failed to create file '/home/purity/.gnome2/gedit/gedit-2.773OZU': Read-only file system
```

So it does indeed seem like the file system has gone read-only on me. The only programs I have had running is Transmission and Chromium.

Are there any debug programs or something like that I could run and print the results from here, that could give an explanation to my problem?

---

### Post by dumblebee100 on 2009-09-15
> **purity89 said:**
> Okay, now something has happened again. I can't save files, create folders or anything like that on my *ext3* partition (where Ubuntu is installed) and programs have empty windows when I try and run them. When I run gnome-terminal via xterm I get no error messages, but when i run gedit I get these:

```
$ gedit

** (gedit:31089): WARNING **: Cannot create the 'gedit' connection.

### After closing the gedit window:

(gedit:31089): Gtk-WARNING **: Attempting to store changes into `/home/purity/.recently-used.xbel', but failed: Failed to create file '/home/purity/.recently-used.xbel.ETHPZU': Read-only file system

(gedit:31089): Gtk-WARNING **: Attempting to set the permissions of `/home/purity/.recently-used.xbel', but failed: Read-only file system

** (gedit:31089): CRITICAL **: bacon_message_connection_free: assertion `conn != NULL' failed

** (gedit:31089): WARNING **: Could not write gedit state file: Failed to create file '/home/purity/.gnome2/gedit/gedit-2.773OZU': Read-only file system
```

So it does indeed seem like the file system has gone read-only on me. The only programs I have had running is Transmission and Chromium.

Are there any debug programs or something like that I could run and print the results from here, that could give an explanation to my problem?

please post your fstab details ...and wats ur kernel version ...I think there is some bug in past which makes the filesystem readonly I mean soft locks after some time of inactivity ...if you are using that kernal u shud upgrade it ...before that post fstab ..we will look into it and see ur problem ..

---

