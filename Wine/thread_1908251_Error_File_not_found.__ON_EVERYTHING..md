---
title: "Error: File not found.  ON EVERYTHING."
date: 2012-01-13
forum: Wine
---

### Post by B-Mart on 2012-01-13
So, I am posting this on the Wine section because the error I get is in the Wine style of boxing.  For some reason after I updated Wine recently, every time I try and open a folder from "Places" I get a Wine error saying "File not found."  It's infuriating, since when I tried to check my wine folders and settings, it gave me the same error.  I'm unfamiliar, so it's another added challenge.  So my question is, "How can I make it stop?".  Oh, I've also noticed that if I browse from the desktop's "Computer" icon I am fine, however, it's annoying to have to minimize everything just to browse for a file.  If anyone can help that would be great.

---

### Post by B-Mart on 2012-01-13
Okay so I will attach a screenshot of the error...dunno if that will HELP, I doubt it.  Anyway, I tried to remove wine through synaptic and any time I try to add or remove ANY package it gives me an error about not being able to find a file named "bnetd" I don't know WHERE the file went, dunno what happened to it, all I know is not having it is giving me a ton of trouble.

---

### Post by B-Mart on 2012-01-13
the file. :/[ATTACH]210747[/ATTACH]

---

### Post by B-Mart on 2012-01-13
Here's some error message I got

Removing wine ...
Setting up bnetd (0.4.25-8) ...
chown: cannot access `/var/run/bnetd': No such file or directory
dpkg: error processing bnetd (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 bnetd

I don't even.

---

### Post by ergo-proxy on 2012-01-13
Try to reinstall wine completly:
 
sudo apt-get purge wine
sudo add-apt-repository ppa:ubuntu-wine/ppa (can be skipped if you have wine repo already added)
sudo apt-get update 
sudo apt-get install wine1.3

---

### Post by B-Mart on 2012-01-13
Thanks for the reply.  It didn't seems to work, everything went well, it purged and re-installed.  However, when I tried to use my paths, it still gave me the error.  It's odd.  However, I looked under wine in the applications tab and it would give me the same error when trying to browse the C drive.  Also, as an update I have fixed the problems with synaptic and that 'bnetd' directory issue.  Thanks for the suggestion Ergo.

---

### Post by B-Mart on 2012-01-14
Alright, well, as I have found, wine just won't work with me on this.  No matter what version I run it will not work proper inside of nautilus.  It sucks, really.  I'll keep working on it and see if I can fix it on my own.  Is it that wine gives itself some weird permissions which causes to try and open anything under itself? I dunno, weird.  Anyway, I'll keep everyone updated.

---

### Post by B-Mart on 2012-01-14
Of course silly me forgot to add some details about my distro, derp.  I'm running lucid 10.04, and I have tried both beta releases of wine (1.3) and the "stable) 1.2.  Neither have worked, obviously.  My computer is a HP G72 laptop.  What's really getting to me is it's not letting me even open the C drive under it's own option it gives you under "applications" and seeing that I don't know the command prompt for it I can't run for errors.  Nor do I know the command prompt to open my browser windows under "places".  Anyway, back to the drawing board I go...*grumble grumble*

---

### Post by B-Mart on 2012-01-14
Alright! So, just to start I will be marking this thread as [Solved] after this here post, since I FINALLY found some answers.  So, for those of you who could be reading this there is two simple answers...

1.  You just herped the derp and just need to some simple point-and-clicks.  To do this you simply just need to Right-click an open spot on the desktop then "Create Folder" then just right click the new one and select "Open With Other..." then select "file browser" and it should be associated with the system again, and ta-da! works!  Easy, right?  Well, that didn't work for me, and if it didn't for you then...

2!  Go into your Terminal (Applications>Accessories>Terminal) then enter this bit of code:
```
gconftool-2 -s /desktop/gnome/url-handlers/file/command -t string "nautilus \"%s\""
gconftool-2 -s /desktop/gnome/url-handlers/file/enabled -t bool true
```

Just copy/paste this and you should be good after running it.  Do I know what this code is DOING? No not really...but it worked!  Anyway, hope this helps, if it doesn't don't be afraid to shoot me a message and I will try and help you out the best I can :D

---

