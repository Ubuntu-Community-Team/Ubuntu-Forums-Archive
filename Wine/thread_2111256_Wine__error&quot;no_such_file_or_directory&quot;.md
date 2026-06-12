---
title: "Wine  error:&quot;no such file or directory&quot;"
date: 2013-02-01
forum: Wine
---

### Post by midwestmac on 2013-02-01
I'm a Newbie using Lubuntu 12.04 

 I was hoping someone can point me in the right direction.
I have installed (with the synpatic manager) Wine1.4, winetricks, wine1.4 i386 ,wine gecko1.4, wine1.4common.

From the GUI I can open   programs/accessories/notepad  (It works.)
But if I click on "Browse C drive" I get Error "No such file or directory"
If I click on "Wine Tricks" (it does nothing)
If I click on "configure Wine" (it pops up fine and everything looks to be there)

I have this listed " ppa.launchpad.net/ubuntu-wine/ppa/ubuntu"  in Synpatic

I even tried to install from the terminal and still get "no such file or directory" from the GUI.

I searched for bugs relating to this but only found this "http://itgeo.info/wine/ "
tried " sudo Kate" but "Kate"  isn't a command.

Any ideas ? thanks

---

### Post by cmcanulty on 2013-02-01
I have had better luck with wine by putting the exe files in /home/yourname/.wine/drive_c/Program Files/

---

### Post by Tweak42 on 2013-02-01
I haven't used Lubuntu but most things should work and be in the same places as vanilla ubuntu.

> **midwestmac said:**
> 
From the GUI I can open   programs/accessories/notepad  (It works.)
But if I click on "Browse C drive" I get Error "No such file or directory"
As cmcanulty mentioned above this directory should be located in: ```
/home/<username>/.wine/drive_c/
```You should be able to browse there with the file manager, but you may need to show hidden files because the "." at the start of the name denotes it as hidden.

> If I click on "Wine Tricks" (it does nothing)
Try opening a terminal and running "winetricks".  Report back any error messages.

> If I click on "configure Wine" (it pops up fine and everything looks to be there)

I have this listed " ppa.launchpad.net/ubuntu-wine/ppa/ubuntu"  in Synpatic

I even tried to install from the terminal and still get "no such file or directory" from the GUI.

I'm not sure what you are trying to install here.

> 
I searched for bugs relating to this but only found this "http://itgeo.info/wine/ "
tried " sudo Kate" but "Kate"  isn't a command.

Any ideas ? thanks
Kate is a text editor but it's probably not installed if you are getting that error.  I think the default text editor for Lubuntu is leafpad, so try this command instead.
```
sudo leafpad /usr/share/applications/wine-browsedrive.desktop
```

---

### Post by midwestmac on 2013-02-03
Hello thanks guys for the response,
As a newbie I thought it might be easier for me to do things from the  desktop with wine until I get used to it. I'm learning to fix things  through the terminal, but of course I bet some of the windozs programs  I'll have to command through the terminal any way:smile: or the file manager (if it'll let me).


Tweak42, I had Wine working with another install of Lubuntu 12.04 (not sure if it was Wine 1.3 or 1.4 ) I had wine/ppa udating OS

Anyways I can see this (with the file manager)
/home/<username>/.wine/drive_c/

I just can't go to it from the desktop> (under all my tabs) I get "error :[B]no such file or director

[/B]@Tweak42, the wine tricks I got that working, had to install "zenity" thanks

But I thought the other install I did I could click on "browse c drive" from my desktop where the "Wine tabs are"   If that makes sense?

---

### Post by Tweak42 on 2013-02-05
> **midwestmac said:**
> 

I just can't go to it from the desktop> (under all my tabs) I get "error :[B]no such file or director

But I thought the other install I did I could click on "browse c drive" from my desktop where the "Wine tabs are"   If that makes sense?

I'm pretty sure that the command does not work because something is wrong with the syntax for the command run when you click on "browse c: drive".  I don't use Lubuntu so I can't tell you how to find what the command it's trying to run, where to edit it, and the correct command to replace it with.  You may try asking in Desktop Environments forum "how do I edit the tabs in Lubuntu" or something like that.

---

