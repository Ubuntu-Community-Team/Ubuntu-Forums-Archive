---
title: "ubuntuStudio8.10,desktop 64 AMD from U8.04.1"
date: 2009-03-19
forum: x86 64-bit Users
---

### Post by ken78724 on 2009-03-19
Not sure Ubuntu Studio 8.10 64AMD can be built from U8.04.1 as I could not get The Lasko's method to work but on Jaunty 9.04, I get fair results using 9.04 & the following: 

 I. Start ubuntustudio build from U 9.04 64 bit by opening > terminal and do a 
A.sudo aptitude search ubuntu studio AMD 64 [input password & return]
B.sudo aptitude install ubuntustudio [input password & return] Then I followed the output by 
c. Yes continue   

II. Then for a fuller ubuntustudio, open terminal
#!/bin/sh
gksudo "aptitude -y install ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-controls ubuntustudio-default-settings ubuntustudio-desktop ubuntustudio-gdm-theme ubuntustudio-icon-theme ubuntustudio-graphics ubuntustudio-look ubuntustudio-menu ubuntustudio-screensaver ubuntustudio-sounds ubuntustudio-theme ubuntustudio-video ubuntustudio-wallpapers usplash-theme-ubuntustudio linux-rt linux-restricted-modules-rt linux-image-rt linux-headers-rt";

this boots up in Ubuntu Studio & lets U open>administration>"Ubuntu Studio Controls". Gives 300+ options within this programs

---

### Post by Thelasko on 2009-03-20
> **ken78724 said:**
> If you start with 8.04.1 Hardy Herron & want StudioU, is it best to gpart HD for 8.10 desktop-64AMD or to write over 8.04.1 in same partition?

I'm confused with your question.  Do you want Ubuntu Studio 8.04 or 8.10?  If your partitions are already the way you want them, you shouldn't have to repartition, just write over it.

You also probably don't need the "linux-rt" part of that command.  That only installs the real time kernel, which sometimes causes more problems than it solves.

---

### Post by ken78724 on 2009-03-21
best solution I can offer is in Post No. 1

---

### Post by ken78724 on 2009-03-21
for Ubuntu-Studio the best solution I can offer is in Post No. 1

---

### Post by ken78724 on 2009-03-21
best solution I can offer is in Post No. 1

---

### Post by ken78724 on 2009-03-21
want to install U Studio on Jaunty asap

---

### Post by Thelasko on 2009-03-21
so, you're trying to upgrade from 8.04 to 8.10?

---

### Post by ken78724 on 2009-03-21
for 8.10, 8.04.1 and 9.04 Jaunty Ubuntu Studio best solution I can offer is in Post No. 1

---

### Post by ken78724 on 2009-03-21
for Ubuntu Studio best solution I can offer is in Post No. 1

---

### Post by Thelasko on 2009-03-23
Upgrading via synaptic is not reliable.  The best way to upgrade is a fresh install using a CD.  You can save your packages in synaptic and keep all of your documents in a separate home partition so you don't lose your work during the upgrade.

---

### Post by ken78724 on 2009-03-23
for 8.10, 8.04 or 9.04 I believe best solution I can offer is in Post No. 1

---

### Post by ken78724 on 2009-03-23
see best solution I can offer in Post No. 1

---

### Post by Thelasko on 2009-03-23
Okay, now I think I understand.  You want to take the new Ubuntu 8.10 CD and run it as a live cd and then install it over the old installation.  When the Live CD starts, just click on the install icon and follow the prompts.

---

### Post by ken78724 on 2009-04-10
best solution I can offer is in Post No. 1

---

### Post by ken78724 on 2009-04-24
visiting a totally different thread puzzle was resolved as follows: 
deb [http://ubuntu-bug](http://ubuntu-bug) apt-get
E: Malformed line 75 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Routine used to work around the problem: 
An error resulted as follows:
E: Type 'sudo' is not known on line 57 in source list /etc/apt/sources.list

E: The list of sources could not be read.

Go to the repository dialog to correct the problem.

E: _cache->open() failed, please report.

The message pretty well tells you what is wrong, to repair the problem press Alt-F2 and type:
Code:  gksu gedit /etc/apt/sources.list
Enter your password when prompted.

This will open the file /etc/apt/sources.list in a text editor as root

Next enable line numbering in the text editor by going to Edit-->Preferences-->View and check the line number box.

I scrolled down to line 75 and completely removed the line, then saved and followed by running the Ubuntu 8.10 intrepid installation update that synaptic program manager had before it over the past three (3; or was it four??) months????? from notes eight months earlier I learned Save the file and close the text editor. Go to System-->Administration-->Synaptic Package Manager and click the Reload button. You should now be able to download packages again.

While you have Synaptic open go to Edit-->Mark Packages By Task, a window will pop up, just scroll down to Video Creation And Editing Suite and mark it for installation, this should install most of the programs you need for what you want to do. :):)  

Truly and not sure how a notice "a source list /etc/apt/sources.list"

---

### Post by Thelasko on 2009-04-24
> **ken78724 said:**
> Though I have not gone there, if you'd like to use TheLasko's solution go ahead. Am amidst digging out a long time in the dungeon..
:guitar:

Indeed, you should be able to edit your sources list in synaptic without going to the command line, or editing the file by hand.  I think it's under either the "edit" or "settings" menu.  It should say "edit sources" or something similar.

---

### Post by ken78724 on 2009-09-05
for 8.10, 8.04 & 9.04 64 AMD Jaunty, best solution I can offer is in Post No. 1

---

### Post by ken78724 on 2009-09-06
Can anyone give a holler on an installable ubuntuStudio for 9.04 64 AMD Jaunty? I'd like to delete this thread.

Developers, do we have an install that runs studio in 9.04 64 bit?

---

### Post by Thelasko on 2009-09-07
> **ken78724 said:**
> Is there a direct install of Ubuntu Studio ready for 9.04 64 AMD Jaunty

[Yes]("http://ubuntustudio.org/downloads")

---

### Post by ken78724 on 2009-10-26
for 8.10, 8.04 & 9.04 I believe the best solution I can offer is in Post No. 1

---

