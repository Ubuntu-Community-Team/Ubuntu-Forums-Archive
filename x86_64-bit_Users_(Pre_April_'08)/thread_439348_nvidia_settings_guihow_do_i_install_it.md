---
title: "nvidia settings gui???how do i install it???"
date: 2007-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by saru411 on 2007-05-10
ok, i have a running version of 6.10 64 with beryl on another hdd. i feel ive screwed it up to the point where i cannt fix it without hours of eye strain and debugging, so here i am installing a fresh copy of 7.04. i have installed the glx driver for my 7600 gt and its running fine. my problem is i had a settings gui for my nvidia card under applications>(another tree started here but i forgot the name of it, although i know its not listed in my list currently and it was listed at the bottom. it was also under the tree with envy in it on my other hdd). i also remember going thru a series of questions while setting up my nvidia card on the last install, but i never got prompt to answer any questions about setup this time. ive been looking threw synpathic manager but i fail to see anything that acts as a gui for nvidia settings in it. any help is appreciated........all i really want is a link of how to get this gui installed or just the gui itself.

again thanks all of you great ubuntuers out there who have helped me in the past =)

---

### Post by stmiller on 2007-05-10
type 
nvidia-settings
in a terminal

---

### Post by John.Michael.Kane on 2007-05-10
If you want to add it to your menu

Run:
```
gksudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```

If on KDE:
```
kdesu kate /usr/share/applications/NVIDIA-Settings.desktop
```

A blank file will open up.

Copy paste this info:
```
[Desktop Entry] 
Name=NVIDIA Settings 
Comment=NVIDIA X Server Settings 
Exec=nvidia-settings 
Icon= 
StartupNotify=true 
Terminal=false 
Type=Application 
Categories=Application;System;
```

CTRL+ALT+BACKSPACE re-login nvidia settings should be in your menu.

Hope this helps.

---

### Post by saru411 on 2007-05-11
thanks the terminal command worked great. then i tried to add the menu icon like plisskin said but i dont see it under any of the applications sub trees. where is it hmmmmmmm

---

### Post by John.Michael.Kane on 2007-05-11
> **saru411 said:**
> thanks the terminal command worked great. then i tried to add the menu icon like plisskin said but i dont see it under any of the applications sub trees. where is it hmmmmmmm


Looks like your going to have to add it to the menu manually.

Right click on Applications-->edit menus--->system tools---new item

In the Name field Put NvSettings or the name of your choice.

In the command field put nvidia-settings 

Click ok. you should now see the entry in the menu.

---

### Post by saru411 on 2007-05-11
thanks, that worked.

---

### Post by John.Michael.Kane on 2007-05-11
> **saru411 said:**
> thanks, that worked.

No problem..

---

### Post by saru411 on 2007-05-22
now ive had this working for awhile but every time i reboot my screen size is reformated, and yes i do hit the save to x file button. now what do i do?

---

### Post by shad0w_walker on 2007-05-22
If i read the instructios posted earlier the settings program isnt run as root (Needed to save the settings to X config file) 

You need to edit the menu entry slightly, do the same you did to add it but then right click on the entry and select the edit option.

To get the settings wizard to run as root use this command:

```
gksu nvidia-settings
```

This should make it run as root and allow it to save the changes when you click the save button in it.

---

### Post by saru411 on 2007-05-22
that worked. well i ran it in terminal then restarted x and it was saved. thanks for the help, now to edit my app > system tools>nvidia settings.

Edit: fixed the app also =)

---

### Post by sonnet on 2007-05-22
> **shad0w_walker said:**
> If i read the instructios posted earlier the settings program isnt run as root (Needed to save the settings to X config file) 

You need to edit the menu entry slightly, do the same you did to add it but then right click on the entry and select the edit option.

To get the settings wizard to run as root use this command:

```
gksu nvidia-settings
```

This should make it run as root and allow it to save the changes when you click the save button in it.
Hi I followed the instructions some post above,to setup the nvidia setting panel into the menu,I dind't get error in the terminal but it didn't work.

If  I digit your command gksu nvidia-settings the menu appear but how can I make it stay into the menu?

---

### Post by shad0w_walker on 2007-05-22
You need to add a menu entry to your applications (I have mine in the system preferences section)

1. Right click on your Applications and select Edit menus from the menu that appears
2. Select the menu section you want to put the button in
3. Click the New Item button next on the right hand side of the menu editor

Another box should pop up now, put in these details:

Type: Application
Name: Nvidia settings (Or whatever you want to call the button)
Command: gksu nvidia-settings
Comment: (Anything you want to put as a comment)

5. Click ok and close the menu editor

You should have a nice new button in the menu you selected.

---

