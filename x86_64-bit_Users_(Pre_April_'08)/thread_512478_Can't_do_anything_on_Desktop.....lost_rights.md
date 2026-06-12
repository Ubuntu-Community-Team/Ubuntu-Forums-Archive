---
title: "Can't do anything on Desktop.....lost rights?"
date: 2007-07-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by deejmer on 2007-07-29
Hello,
I was doing very well with setting up almost anything on Ubuntu 7.04, and then I tried to follow this tutorial ([http://ubuntuforums.org/showthread.php?p=1174435]("http://ubuntuforums.org/showthread.php?p=1174435")) to get flash/shockwave working in by x64 installation.   Now I can't do ANYTHING on the desktop.  I can't create, delete, move, etc my files.  It seems as if I lost admin rights on my own desktop.  (and never got flash working BTW)

Here is the message I'm getting when trying to delete something:
"Cannot move "*blahblahblah*" to the trash because you do not have permissions to change it or its parent folder."

Anyone know how I fried this?  I feel like I should get rid of the firefox32 browser that I installed from the tutorial at the link above.....not really sure how i'd do that though.

Sorry for being a newb.  Trying to make the shift from windows (yuck) to Ubuntu Feisty which I've loved so far.

Thanks!

---

### Post by aysiu on 2007-07-29
Go to [a terminal](http://www.psychocats.net/ubuntu/terminal) and type ```
sudo chown -R *username:username* /home/*username*
``` where *username* is your actual username. Make sure the *-R* is capitalized. That should do it.

---

### Post by Kilz on 2007-07-29
> **deejmer said:**
> Hello,
I was doing very well with setting up almost anything on Ubuntu 7.04, and then I tried to follow this tutorial ([http://ubuntuforums.org/showthread.php?p=1174435]("http://ubuntuforums.org/showthread.php?p=1174435")) to get flash/shockwave working in by x64 installation.   Now I can't do ANYTHING on the desktop.  I can't create, delete, move, etc my files.  It seems as if I lost admin rights on my own desktop.  (and never got flash working BTW)

Here is the message I'm getting when trying to delete something:
"Cannot move "*blahblahblah*" to the trash because you do not have permissions to change it or its parent folder."

Anyone know how I fried this?  I feel like I should get rid of the firefox32 browser that I installed from the tutorial at the link above.....not really sure how i'd do that though.

Sorry for being a newb.  Trying to make the shift from windows (yuck) to Ubuntu Feisty which I've loved so far.

Thanks!

Please copy/paste the results of this command to a post in this thread before running the fix above so I can tell what went wrong and fix the howto if necessary
```
ls -al ~/
```

---

### Post by paintedoverpaint on 2007-08-20
I had the exact same problem when installing 32-bit Firefox in order to get Flash.  First, Thank You Aysiu.  Second, in response to Kilz, I included a carbon copy of the terminal prior to the fix:

```
joe@joe-desktop:~$ ls -al ~/
total 26500
drwxr-xr-x 48 joe  joe      4096 2007-08-20 01:38 .
drwxr-xr-x  4 root root     4096 2007-05-16 00:19 ..
-rw-r--r--  1 root root        0 2007-05-16 00:47 1
drwxr-xr-x  2 joe  root     4096 2007-08-13 23:19 .automatix
drwxr-xr-x  8 joe  joe      4096 2007-08-19 19:24 .azureus
-rw-------  1 joe  joe      1948 2007-08-20 01:51 .bash_history
-rw-r--r--  1 joe  joe       220 2007-05-16 00:19 .bash_logout
-rw-r--r--  1 joe  joe      2298 2007-05-16 00:19 .bashrc
drwxr-xr-x  2 joe  joe      4096 2007-08-20 01:36 .beryl
-rw-r--r--  1 joe  joe       185 2007-08-20 01:36 .beryl-managerrc
drwx------  4 joe  joe      4096 2007-05-16 01:07 .config
-rw-r--r--  1 joe  joe        60 2007-08-19 16:25 .DCOPserver_joe-desktop__0
lrwxrwxrwx  1 joe  joe        36 2007-08-19 16:25 .DCOPserver_joe-desktop_:0 -> /home/joe/.DCOPserver_joe-desktop__0
drwxr-xr-x  9 root root     4096 2007-08-19 23:57 Desktop
-rw-------  1 joe  joe        26 2007-05-16 00:24 .dmrc
drwxr-xr-x  8 joe  joe      4096 2007-07-25 00:09 .dvdcss
drwxr-xr-x  4 joe  joe      4096 2007-05-16 01:08 .emerald
-rw-------  1 joe  joe        16 2007-05-16 00:24 .esd_auth
drwxr-xr-x  7 joe  joe      4096 2007-08-20 01:30 .evolution
lrwxrwxrwx  1 joe  joe        26 2007-05-16 00:19 Examples -> /usr/share/example-content
drwxr-xr-x  2 joe  joe      4096 2007-08-20 01:37 .fontconfig
drwxr-xr-x  3 joe  joe      4096 2007-08-20 01:37 .fullcircle
drwx------  4 joe  joe      4096 2007-08-20 01:36 .gconf
drwx------  2 joe  joe      4096 2007-08-20 01:52 .gconfd
-rw-r-----  1 joe  joe         0 2007-08-19 23:46 .gksu.lock
drwxr-xr-x  4 joe  joe      4096 2007-05-16 00:48 .gnome
drwx------ 15 joe  joe      4096 2007-08-20 01:30 .gnome2
drwx------  2 joe  joe      4096 2007-05-16 00:24 .gnome2_private
lrwxrwxrwx  1 joe  joe        35 2007-05-16 00:48 googleearth -> /home/joe/google-earth//googleearth
drwx------  5 joe  joe      4096 2007-05-16 00:48 .googleearth
drwxr-xr-x  9 joe  joe      4096 2007-05-16 00:48 google-earth
-rwxr-xr-x  1 joe  joe  23852601 2007-05-10 08:22 GoogleEarthLinux.bin
drwxr-xr-x  2 joe  joe      4096 2007-05-16 02:26 .gstreamer-0.10
-rw-r--r--  1 joe  joe        13 2007-08-14 16:47 .gtk-bookmarks
-rw-r--r--  1 joe  joe        85 2007-05-16 00:24 .gtkrc-1.2-gnome2
-rw-------  1 joe  joe      7695 2007-08-20 01:36 .ICEauthority
drwxr-xr-x  2 joe  joe      4096 2007-05-16 01:02 .icons
drwx------  4 joe  joe      4096 2007-05-26 20:41 .kde
drwxr-xr-x  3 joe  joe      4096 2007-08-13 21:34 .kpackage
drwx------  3 joe  joe      4096 2007-05-16 00:48 .local
drwx------  3 joe  joe      4096 2007-05-16 00:48 .loki
drwx------  3 joe  joe      4096 2007-08-20 01:38 .macromedia
drwxr-xr-x  3 joe  joe      4096 2007-05-16 02:16 .mcop
-rw-------  1 joe  joe        31 2007-05-16 17:02 .mcoprc
drwx------  3 joe  joe      4096 2007-05-16 00:24 .metacity
drwx------  4 joe  joe      4096 2007-08-20 00:07 .mozilla
drwxr-xr-x  2 joe  joe      4096 2007-08-20 00:32 .mplayer
drwxr-xr-x  3 joe  joe      4096 2007-08-20 01:30 .nautilus
-rw-r--r--  1 joe  joe   2834432 2007-05-16 17:44 nautilus-debug-log.txt
drwx------  3 joe  joe      4096 2007-08-19 14:51 .openoffice.org2
drwxr-xr-x  2 joe  joe      4096 2007-08-09 07:30 Pictures Joe and Katy
drwxr-xr-x  2 joe  joe      4096 2007-08-09 07:33 Pictures Piano Move
-rw-r--r--  1 joe  joe       566 2007-05-16 00:19 .profile
drwxr-xr-x  2 joe  joe      4096 2007-08-13 22:19 .qt
-rw-------  1 joe  joe     12914 2007-08-19 18:35 .recently-used
-rw-r--r--  1 joe  joe    127837 2007-08-20 00:59 .recently-used.xbel
drwxr-xr-x  2 joe  joe      4096 2007-07-25 00:12 .serpentine
-rw-r--r--  1 joe  joe         0 2007-05-16 00:25 .sudo_as_admin_successful
drwxr-xr-x  6 joe  joe      4096 2007-05-16 01:08 .themes
drwx------  5 joe  joe      4096 2007-08-16 23:15 .thumbnails
drwx------  2 joe  joe      4096 2007-08-20 01:46 .Trash
drwx------  2 joe  joe      4096 2007-08-20 00:10 .tsclient
drwxr-xr-x  2 joe  joe      4096 2007-05-16 00:24 .update-manager-core
drwx------  2 joe  joe      4096 2007-05-16 00:24 .update-notifier
drwxr-xr-x  2 joe  joe      4096 2007-08-20 01:31 Virtual Machine
drwxr-xr-x  3 joe  joe      4096 2007-05-16 01:29 .vlc
drwxr-xr-x  2 joe  joe      4096 2007-08-13 23:19 vmware
drwxr-xr-x  2 joe  joe      4096 2007-08-18 18:00 .vmware
drwxr-xr-x  2 joe  joe      4096 2007-08-16 23:15 .wapi
-rw-------  1 joe  joe       122 2007-08-20 01:36 .Xauthority
drwxr-xr-x  2 joe  joe      4096 2007-05-16 02:16 .xine
-rw-r--r--  1 joe  joe      6783 2007-08-20 01:46 .xsession-errors
joe@joe-desktop:~$ sudo chown -R joe:joe /home/joe
Password:
joe@joe-desktop:~$ 

```

Hope this helped.  I'm also very new at non-windows os, but I'm loving every minute of it.

---

### Post by Kilz on 2007-08-20
Just to make sure, how did you install 32bit Firefox?

---

### Post by mrbungle on 2007-08-26
the same thing happened to me after installing the 32bit flash.  i can't save or delete anything from the desktop now:(

how can i fix this?

thanks

---

### Post by Kilz on 2007-08-26
> **mrbungle said:**
> the same thing happened to me after installing the 32bit flash.  i can't save or delete anything from the desktop now:(

how can i fix this?

thanks

Exactly how did you do that following the commands? I have been unable to duplicate it, but others have done it. Did it happen after this command?
```
chown -R <username>:users /home/<username>/.macromedia
```
Because if we cant figure this out, today I am going to remove the manual howto.

---

### Post by mrbungle on 2007-08-26
well i used your autoscript

1. Download the script.
2. Right click on the tar.gz and select "Extract Here"
3. Close all browsers.
4. Inside the folder that extracts is a "GetFlash" file, double click on it.
5. Select "Run in Terminal"
6. When the terminal closes, restart your browser.
7. Your done


i never used the code you mentioned because it worked after i did the autoscript.

---

### Post by mrbungle on 2007-08-26
can i simply use gksudo and whatever file manger to change the permission on the desktop?

it won't even let me unmount my ipod now :(

---

### Post by Kilz on 2007-08-26
So we know what was affected, to change it all back please give me the results of the command

```
ls -al ~/
```

and

```
ls -al /home
```

---

### Post by John.Michael.Kane on 2007-08-26
You can see if any of these help.

chown username:users filename/directory 

Or

chmod 755 file name

You can try ```
gksudo nautilus
```

Another option .
```
umount /mnt/ipod
```



@Kilz I tested your manual method, and install went off fine.

---

### Post by mrbungle on 2007-08-26
drwxr-xr-x 37 mike mike   4096 2007-08-26 17:05 .
drwxr-xr-x  3 root  root      4096 2007-08-18 14:26 ..
drwx------  2 mike mike    4096 2007-08-19 16:43 .AbiSuite
-rw-------  1 mike mike    2602 2007-08-26 13:56 .bash_history
-rw-r--r--  1 mike mike     220 2007-08-18 14:26 .bash_logout
-rw-r--r--  1 mike mike   2298 2007-08-18 14:26 .bashrc
drwx------  9 mike mike    4096 2007-08-19 15:52 pics
drwx------  5 mike mike     4096 2007-08-18 14:41 .cache
drwxr-xr-x  2mike mike   4096 2007-08-19 20:20 .compizconfig
drwx------  9 mike mike    4096 2007-08-25 22:06 .config
drwxrwxr-x  2 root  mike     4096 2007-08-26 13:58 Desktop
-rw-------  1 mike mike      24 2007-08-18 14:37 .dmrc




and



drwxr-xr-x  3 root  root  4096 2007-08-18 14:26 .
drwxr-xr-x 22 root  root  4096 2007-08-18 15:33 ..
drwxr-xr-x 37 mike mike 4096 2007-08-26 17:05 mike

---

### Post by mrbungle on 2007-08-26
type this in the terminal?

```
chown username:users filename/directory 
```

tried 

gksudo thunar but didn't change it back.

---

### Post by Kilz on 2007-08-26
> **mrbungle said:**
> type this in the terminal?

```
chown username:users filename/directory 
```

tried 

gksudo thunar but didn't change it back.

The command is 
```
sudo chown -R mike:mike /home/mike
```
To put things back.

Did you run the GetFlash script on a root login?

---

### Post by mrbungle on 2007-08-26
no i was just logged in my normal username.

---

### Post by mrbungle on 2007-08-26
success!!!   desktop back to normal.


thanks for the help guys!

i do remember having a hard time getting the getflash file to run.  i couldnt get it to right click and run in terminal, so i think i got it running by opening the terminal 1st and typing a command to open it. i can't quite remember?  anyway maybe that had something to do with why this happened? the flash installed and works fine though.

---

### Post by Kilz on 2007-08-26
> **mrbungle said:**
> success!!!   desktop back to normal.


thanks for the help guys!

i do remember having a hard time getting the getflash file to run.  i couldnt get it to right click and run in terminal, so i think i got it running by opening the terminal 1st and typing a command to open it. i can't quite remember?  anyway maybe that had something to do with why this happened? the flash installed and works fine though.

It could be, because I looked over the script. The script makes a folder in your temp directory. Everything is done there. There isnt even one chown command in the whole thing. How your home folder got owned by root is a mystery to me.

---

