---
title: "Trouble with Beryl"
date: 2007-07-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by acewolff80 on 2007-07-01
This is my first post so go easy. :)
I have installed several things in Feisty so far and most have gone well, but I am stuck with my graphics issues.  They seem to be related but I can't figure out how to fix them.  Maybe someone else's perspective will be able to help me.
I have installed Wine, Flash, Java, Ati drivers, and Beryl using guides that I have found in the forums.  The installations all seem to go as they are supposed to, but I can't get most of these programs to run correctly.  Beryl manager loads but will not load the effects and I get the xcomposite failed messege  when I type "beryl" in terminal.  Also, Wine is installed and I installed Guild Wars and America's Army.  Both attempt to start, but never get past loading screens.  Also, Flash works as far as Youtube, but Java starts loading runescape (my test page), but won't start the game.  I can't help but think that these are all related somehow.
Can anyone help untangle this mess?
I have Feisty Fawn
X1600 Radeon card
I have tried both closed source and open source drivers following forum guides.
I have 64bit Ubuntu (could be the problem)

Any help would be greatly appreciated!

---

### Post by CheShA on 2007-07-01
> **acewolff80 said:**
> 
 Beryl manager loads but will not load the effects 

If you right click the diamond shaped Beryl icon (next to your clock in gnome) you should be able to "select window manager" - mine lists compiz, metacity, beryl.  Selecting beryl enables effects.

---

### Post by r_rehashed on 2007-07-01
surely something to do with the graphics drivers.

i faced the same problems with Edgy, where the drivers for intel's x3000 graphics engine weren't there.
Then it used to show my card as an i810, instead of 946GZ.

Is your card properly recognised?

I can recommend 1 simple gui tool that comes in handy at such times. search for "sysinfo" in Add/Remove Apps

---

### Post by weblordpepe on 2007-07-01
Uninstall the restricted ATI driver, dude. It doesn't support Beryl.

ATi aren't known for their awesome linux support. The open-source radeon driver isn't near as fast, & wont fully support some game graphics, but it will let you do Beryl.

Its some openGL extension that the official ATi driver doesnt support. Im using the very lastest one, and it still don't work.

---

### Post by acewolff80 on 2007-07-01
As to enabling Beryl using the diamond try icon,... I tried that and when Beryl should be applying effects the screen flashes and the windows lose their borders and then it switches back to the default desktop manager.  It won't keep Beryl selected.  I assume that this means that it is crashing.

As to the Graphics card being setup right,.... I am not sure that it is, but I know the ATI control panel works fine and says that the card is installed fine.  Also, the driver shows up as being in use when I select the restricted drivers control panel.

---

### Post by acewolff80 on 2007-07-01
I tried installing the open-source driver, but It either won't work without first uninstalling the restricted one, or it doesn't fix the problem.  How do I completely remove the restricted driver?

---

### Post by weblordpepe on 2007-07-01
I'm in the same boat as you. I installed the ati driver from the ATi website and now it has goofed up my Ubuntu. games wont even load.
Remind me not to go near ATi ever again.

---

### Post by mig5 on 2007-07-06
> **acewolff80 said:**
> Java starts loading runescape (my test page), but won't start the game.

Did runescape work before you fiddled with the graphics drivers?  When you say loading do you mean that java loads, or that runescape's red and black bar loads?  Which version of java do you have installed?  How did you install, via synaptic or from the Sun website?
If the page just loads with no applet, have you installed the plugin for your browser? (in synaptic its j2re.1.4-mozilla-plugin for blackdown java and sun-java6-plugin for Sun java.  If you installed from the website then the instructions should have explained how to make the symbolic link for the plugin).

As for the driver issue can't you just edit your xorg.conf and change the driver back to what it was before?

---

