---
title: "installed picasa (what a mess)"
date: 2016-11-03
forum: Wine
---

### Post by irishy2 on 2016-11-03
Help please I have installed picasa in ubuntu16.04 but everything that could go wrong has done I seem to have lost all my images. In shotwell I have images now in one folder only(missing files) I have also lost my own desktop image can you help
thanks 
Irishy2

---

### Post by arochester on 2016-11-03
> On February 12, 2016, Google announced it was discontinuing support for Picasa Desktop and Web Albums, effective March 15, 2016, and focusing on the cloud-based Google Photos as its successor. Picasa Web Albums, a companion service, was closed on May 1, 2016. [https://en.wikipedia.org/wiki/Picasa](https://en.wikipedia.org/wiki/Picasa)

---

### Post by Bucky Ball on 2016-11-03
Welcome. Wow. How did you install it and where did you get it from? Did you install it using Wine? If not, you have installed a Linux stone cold dead version from 2012 ...

I'd get rid of Picasa to start with. Doubt if your pics are gone unless you've manually wiped them. 

You better go into detail and explain how you installed it, what you've tried to do with it since you installed it and how you tried to fix the problem.

---

### Post by irishy2 on 2016-11-03
thanks for advice this is going to sound a bit naive i googled how to get picasa in ubuntu 16.05 then copied and pasted, I actually don't know how to get rid of picasa if you could advise please

---

### Post by mastablasta on 2016-11-03
we do not know what install method you used.

---

### Post by irishy2 on 2016-11-03
t           
 
 
      
 
   
 
   
 

  
                                                      [h=1][How To Install Picasa 3.8 In Ubuntu Linux]("http://www.webupd8.org/2010/04/how-to-install-picasa-36-in-ubuntu.html")[/h]   Author: [Andrew]("http://www.webupd8.org/p/about.html") | Posted:  **April 10, 2010** | Updated: January 03, 2012   
     [TABLE]
[TR]
[TD="align: right"][/TD]
[TD="align: left"][LEFT][/LEFT]

[/TD]
[TD][/TD]
[TD][/TD]
[TD]  
[/TD]
[/TR]
[/TABLE]
   [CENTER][[IMG]http://img3.imagebanana.com/img/gcpx9fvc/Workspace1_007.png[/IMG]]("http://img3.imagebanana.com/img/1kdi78j8/Workspace1_007.png")[/CENTER]

It seems [a lot of people are using Picasa under Ubuntu]("http://www.webupd8.org/2010/04/best-linux-photo-manager-organizer.html") (which is a bit of surprise to me - I would have though people prefere [gThumb]("http://www.webupd8.org/2010/03/gthumb-finally-gets-flickr-support.html")  or digiKam). But Picasa for Linux is really old - 3.0 - while starting  with version 3.6, Picasa has a really interesting feature: face  recognition; and that might be very valuable to some. Also, Picasa 3.8  comes with a Batch Upload new feature as well as the ability to edit  images in Picnik (online image editor) and Face Movie (unfortunately  Face Movie doesn't work in Linux; but you can [create movies from your photos in Linux using PhotoFilmStrip]("http://www.webupd8.org/2010/08/make-movie-out-of-photos-in-ubuntu.html")).

The latest Picasa version - 3.8 - is not that easy to install so I  though I'd post about installing Picasa 3.8 under Ubuntu with simple  copy/paste commands (except one step in which you'll have to install  something visually).

Sure, you can simply install the Picasa 3.9 Windows binaries and  directly run it under Wine, but Picasa 3.8 will lack Linux integration  (with Gnome, KDE, etc.) such as:

[LIST]
[*]Camera/media detection integrated with Gnome/KDE.
[*]Mozilla/Firefox browser integration done via a plugin.
[*]picasa:// urls work in Firefox
[*]Xinerama support.
[/LIST]
[RIGHT](Info [provided by Google]("http://picasa.google.com/linux/download.html"))[/RIGHT]


[h=2]Install Picasa 3.8 over the original Picasa 3.0 for Linux.[/h]

**Step 1 (optional): install the latest Wine via PPA:**

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update && sudo apt-get install wine

**Step 2: Add the Google Testing PPA**

sudo sh -c "echo 'deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free' >> /etc/apt/sources.list.d/google.list"
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7FAC5991

**Step 3: Install Picasa 3.0**

Yes, Picasa 3.0, but we'll update it in the next step:

sudo apt-get update && sudo apt-get install picasahis is what i did then i was importing images when it went pear shaped

---

### Post by Bucky Ball on 2016-11-03
>  Posted: April 10, 2010

That should have had warning bells ringing. :)

Sorry, I have absolutely no idea about Wine or how to uninstall a program from it. Might be better here.

*Thread moved to **Wine**.*

Folks should be more familiar with your predicament here. I take it Wine is working fine, just picasa that has gone pear-shaped?

---

### Post by pfeiffep on 2016-11-03
> **irishy2 said:**
> thanks for advice this is going to sound a bit naive i googled how to get picasa in ubuntu 16.05 then copied and pasted, I actually don't know how to get rid of picasa if you could advise please
Quite possibly your computer memory knows what steps you executed - providing you used a terminal. Try launching a terminal and clicking the up arrow, this should display the most recent command executed - keep doing this and you should get to the commands you executed. Knowing how you installed this will provide the members here information with which to help you.

Alternately open a terminal which places you in your home directory and type
```
less .bash_history
```
[LIST]
[*]bash history file stores the terminal history
[*]less is a command that produces 1 screen of the file
[*]space bar advances 1 screen at a time
[*]down arrow advances 1 line at a time
[*]q exits the command
[/LIST]

I strongly suggest that blindly copying and pasting can be extremely hazardous to your system. When you need to learn what commands do use the man pages built into your system.
```
man less
```

---

### Post by Bucky Ball on 2016-11-03
@pfeiffep: see bottom of post six for how installed and commands used. ;)

---

### Post by mastablasta on 2016-11-04
not sure where picasahis is mentioned in the guide, but if you followed the guide check if the pcitures are maybe in your wine folder:

~/.wine/drive_c/Program\ Files/Google/Picasa3/

you may need to enable show hidden folders in your file manager so see it. it is in your /home folder if i remmber correctly. then you just click all the way to picasa3 folder.


also as in guide Digikam can do what you need. 
or try Shotwell rather than messing with unsupported windows programs.

---

### Post by Bucky Ball on 2016-11-04
> **mastablasta said:**
> also as in guide Digikam can do what you need. 
or try Shotwell rather than messing with unsupported windows programs.

+3 to looking for alternatives to Windows programs. Ubuntu is not a drop in replacement and you are better to avoid Wine for running things that can be done with native apps. 

If you are looking to run a lot of Win programs using Wine, advise you stick to Windows. :)

---

