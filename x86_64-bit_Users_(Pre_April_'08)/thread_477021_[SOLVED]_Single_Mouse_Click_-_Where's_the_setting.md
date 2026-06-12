---
title: "[SOLVED] Single Mouse Click - Where's the setting?"
date: 2007-06-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-06-17
I just reinstalled A64 ubuntu 7.04 - It was a great move..  Fixed my ATI video Driver - I now have all my resolutions and refresh rates at well as my Catalyst Control Center.  My desktop never looked so nice.

I can't remember where the setting is that lets me SINGLE CLICK on an icon or program to launch it.  Remind this old fart please.

---

### Post by Cappy on 2007-06-18
In Nautilus goto Edit-->Preferences
It is on the "Behavior" tab.
I'm not sure if that works in other programs or not.

---

### Post by crjackson on 2007-06-18
> **Cappy said:**
> In Nautilus goto Edit-->Preferences
It is on the "Behavior" tab.
I'm not sure if that works in other programs or not.

Thanks, exactly what I was looking for.

---

### Post by crjackson on 2007-06-18
You wouldn't know how to turn off the animated windows would you?

---

### Post by capecove on 2007-06-18
CR-- Are you referring to the Desktop Effects? You should see a choice to turn that on/off by going here: System->Preferences->Desktop Effects.

---

### Post by crjackson on 2007-06-18
> **capecove said:**
> CR-- Are you referring to the Desktop Effects? You should see a choice to turn that on/off by going here: System->Preferences->Desktop Effects.

When I click on desktop effects I get an error message telling me that compositing isn't supported on my system (presumably because of my video card driver).

What I want to turn off is the exploding frames when ever I minimize or maximize a window, and I would like to adjust the menu speed (when going to the applications button and rolling the mouse pointer - the delay before it will attempt to open up a menu sub-catagory)

It would be nice there were a tool that would let you tweak the interface (something like tweakUi)...

---

### Post by Cappy on 2007-06-18
Here is your composite problem:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Disable_Composite_Extension](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Disable_Composite_Extension)

As for the exploding thing .. do you have a red jewel in the top right hand corner? You have Beryl enabled somewhere =-/

---

### Post by Znupi on 2007-06-18
I think you can fix the exploding thing by doing the following: hit Alt+F2 and type gconf-editor. Go to **/desktop/gnome/interface/** and uncheck **enable_animations**. That, of course, if you don't have Beryl.

---

### Post by crjackson on 2007-06-19
> **Znupi said:**
> I think you can fix the exploding thing by doing the following: hit Alt+F2 and type gconf-editor. Go to **/desktop/gnome/interface/** and uncheck **enable_animations**. That, of course, if you don't have Beryl.

Nice looking tool.  It didn't do anything however...

---

### Post by Znupi on 2007-06-19
Well then, open a terminal and type
```

beryl-settings

```
Tell us what happens. I doubt there will be a 'unknown command' error.

---

### Post by crjackson on 2007-06-19
charles@K8N-Neo4-Platinum-SLI:~$ beryl-settings
The program 'beryl-settings' is currently not installed.  You can install it by typing:
sudo apt-get install beryl-settings
Make sure you have the 'universe' component enabled
bash: beryl-settings: command not found
charles@K8N-Neo4-Platinum-SLI:~$

---

### Post by Znupi on 2007-06-19
**System -> Preferences -> Desktop Effects**. Is **Enable Desktop Effects** pressed?

---

### Post by capecove on 2007-06-19
Znupi, I already tried giving him that option. Sounds like he has something odd going on...

---

### Post by crjackson on 2007-06-19
> **Cappy said:**
> Here is your composite problem:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Disable_Composite_Extension](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Disable_Composite_Extension)

As for the exploding thing .. do you have a red jewel in the top right hand corner? You have Beryl enabled somewhere =-/

No red jewel and no Beryl that I'm aware of.  In fact I'm starting to think that Beryl won't work on my system.

---

### Post by crjackson on 2007-06-19
> **Znupi said:**
> I think you can fix the exploding thing by doing the following: hit Alt+F2 and type gconf-editor. Go to **/desktop/gnome/interface/** and uncheck **enable_animations**. That, of course, if you don't have Beryl.

I spoke to soon, this did change some things.  Now regular folders and menus **ARE NOT** animated and behave the way I like.  Programs opening and closing however still display the exploding animated square frame as it maximizes or minimizes.  Because I was cliking on evolution and it still had that behaviour, I thought the setting did nothing.  I was wrong...  It looks like the programs control their own animation, or am I incorrect?

---

### Post by capecove on 2007-06-19
crjackson, I found this in amother branch of these forums. I must warn that it is intended for another version of Ubuntu, but you may find it helpful, interesting, somewhere to look, etc.

[http://ubuntuforums.org/showthread.php?t=393964&highlight=disable+animation](http://ubuntuforums.org/showthread.php?t=393964&highlight=disable+animation)

Good luck, let us all know how it works out. I would highly suggest backing up anything before changing it. YMMV...

---

### Post by Znupi on 2007-06-19
> **capecove said:**
> crjackson, I found this in amother branch of these forums. I must warn that it is intended for another version of Ubuntu, but you may find it helpful, interesting, somewhere to look, etc.

[http://ubuntuforums.org/showthread.php?t=393964&highlight=disable+animation](http://ubuntuforums.org/showthread.php?t=393964&highlight=disable+animation)

Good luck, let us all know how it works out. I would highly suggest backing up anything before changing it. YMMV...
That's not what he wants!

Have you tried rebooting or just logging out and back in after changing that key in gconf-editor? It might help.

---

### Post by crjackson on 2007-06-19
> **Znupi said:**
> That's not what he wants!

Have you tried rebooting or just logging out and back in after changing that key in gconf-editor? It might help.

No, I was about to go to work when I quit.  I'm at work now so I will do this tomorrow in the weee AM hours.

---

### Post by crjackson on 2007-06-19
> **capecove said:**
> crjackson, I found this in amother branch of these forums. I must warn that it is intended for another version of Ubuntu, but you may find it helpful, interesting, somewhere to look, etc.

[http://ubuntuforums.org/showthread.php?t=393964&highlight=disable+animation](http://ubuntuforums.org/showthread.php?t=393964&highlight=disable+animation)

Good luck, let us all know how it works out. I would highly suggest backing up anything before changing it. YMMV...

Although I've not done this with Linux, I have with windows so I know what effect it produces.  Basically when moving a window around on a screen, you move only the frame.  The when you release the mouse the frame will populate with it's content.  This really isn't my goal.  I just want my windows/programs to pop open and close without all the fanfare of animated frame shifting.  The method mentioned earlied did eliminate the issue for opening folders and such but it didn't change the way applications behave.

I didn't try rebooting or reloading the GUI afterwards because 1) I didn't think of it and 2) I had to run off to work.  I'll see how it behaves after rebooting tomorrow and report back.  Thanks for the help, it's much appreciated.

---

