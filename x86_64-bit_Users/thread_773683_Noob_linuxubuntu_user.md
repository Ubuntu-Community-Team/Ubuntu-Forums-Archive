---
title: "Noob linux/ubuntu user"
date: 2008-04-29
forum: x86 64-bit Users
---

### Post by kamale on 2008-04-29
Hello every1, I've just decided to move into linux and made my choice of joining Ubuntu. Its been really tough cause i see people typing stuff like codes to run in consoles and stuff. So basically i'm a lil afraid to go into this console line editing stuff. Would some1 be nice enough to give me a laymans step by step on launching any particular program with console editings and stuff?

Also i just installed Wine using the Add/Remove program application. Now all i see is under "Others" is "Configure Wine". How do i actually launch Wine? I dont see it in any of my tabs above???

---

### Post by logos34 on 2008-04-29
This should answer your questions about Wine:
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

> Would some1 be nice enough to give me a laymans step by step on launching any particular program with console editings and stuff?

You want to open and edit a system config file or simply launch an app from the command-line?  Be more specific.

---

### Post by ajmorris on 2008-04-29
hi there,
you might like to see these urls: [http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)
[http://www.tuxfiles.org/](http://www.tuxfiles.org/)
[http://www.physics.ubc.ca/mbelab/computer/linux-intro/html/](http://www.physics.ubc.ca/mbelab/computer/linux-intro/html/)
(there are many more sites out there, phycocats, ubuntu.wiki.com... if the ones i mentioned dont suffice, google can always help you out :) )

but basically the standard commands you will be wanting for the command line are:
./<application> (from the current working directory to run an application)
or /<path to application> (for an app not in the current working directory)
cd (change directory)
ls (list directory contents)
rm (remove)
mv (move)
cp (copy)
editing can use an all array of commands... ubuntu standard is: (for GUI: gedit, for Command Line: nano)

(also, please note, there are many parameters for most commands, man <command> or <command> --help can help you with syntax etc on how to use the commands)

also, for wine, once applications are installed, they will be automagically added to the start menu from which you can run them, but, as far as i know, to install a windows application with wine, is to use the command line, for which the syntax is:
wine setup.exe   (also, note, wine is never to be run as root, things dont work properly with it if you do)

AJ

---

### Post by kamale on 2008-04-29
Ok for example the site you gave me, they say something like this

Add the following repository, deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main

#

Add the repository key by typing the following into a terminal:

    *

      wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -


And all those weird stuff haha i'm so sorry i'm really new. So was wondering where do i go to access this repositories and terminal?

---

### Post by ajmorris on 2008-04-29
a terminal is in the menus, as is a text editor, however, you can use Alt+f2 if you know the name of the app you are trying to run.

so, for those repositories, you can do: ```
Alt+f2
``` and input gnome-terminal into there

then do ```
sudo su (this uses your own password to get root access) or you can use su (this will need the root password to be root)
```
then do
```
gedit /etc/apt/sources.list
``` and append what they say to :)

(there are many different was repos can be added, such as via synaptic package manager, and also, many different ways to edit the file itself, this is just one way)

---

### Post by kamale on 2008-04-29
> **ajmorris said:**
> a terminal is in the menus, as is a text editor, however, you can use Alt+f2 if you know the name of the app you are trying to run.

so, for those repositories, you can do: ```
Alt+f2
``` and input gnome-terminal into there

then do ```
sudo su (this uses your own password to get root access) or you can use su (this will need the root password to be root)
```
then do
```
gedit /etc/apt/sources.list
``` and append what they say to :)

(there are many different was repos can be added, such as via synaptic package manager, and also, many different ways to edit the file itself, this is just one way)

huhuhu lost me there :lolflag:. But thanks i'll read the site that tuxfiles site. Its really interesting and step by step. Thanks so much guys. So much more quicker and better replies then other linux OS forums :guitar:

---

### Post by kamale on 2008-04-29
Oh btw does any1 know why i can't watch youtube videos? everytime i open the video i want it just shows a grey area where the video is supposed to be.

I already installed the latest flash stuff.

Thats weird just yesterday i was able to watch videos. But today its just a grey blank area

---

### Post by didi2005 on 2008-04-29
I also having issue like Kamale, yesterday i can watch/display flash...
Today the area became blank also...

---

### Post by kamale on 2008-04-29
I dunno its just funny, everytime i encounter this problem i just restart my PC and everythings back to normal. Is this usual?

Didi by any chance are you from the GMT+8 zone?

---

### Post by didi2005 on 2008-05-02
> **kamale said:**
> I dunno its just funny, everytime i encounter this problem i just restart my PC and everythings back to normal. Is this usual?

Didi by any chance are you from the GMT+8 zone?

Im from GMT+8 zone... Malaysia
I think is the flash problem... 
Sometimes i just refresh few times and can display flash .

---

