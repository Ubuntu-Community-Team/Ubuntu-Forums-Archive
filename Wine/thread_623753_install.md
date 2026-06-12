---
title: "install"
date: 2007-11-26
forum: Wine
---

### Post by danny cox on 2007-11-26
i would to learn how to do an intall 
new to linux

---

### Post by danny cox on 2007-11-26
that is add programs to ubuntu

---

### Post by machoo02 on 2007-11-26
Do you mean you want to add Windows programs to Ubuntu using Wine?  It's pretty simple.  First, make sure you have Wine installed:```
sudo aptitude install wine
```You can use either the version that's available in the Ubuntu repositories, or you can add get the latest version straight from [WineHQ]("http://www.winehq.org/site/download-deb").  After Wine is installed, you need to set up your 'fake' C: drive...this is done by entering this command into a terminal:```
winecfg
```This command brings up the Wine Configuration panel; whenever you need to change anything about your Wine configuration (such as DLL overrides or Windows version to emulate), enter this command to bring up the panel.

To install software, simply navigate to the folder with the setup program and run it using Wine.  For example, if my username was bob, and the setup.exe program was located in folder foo in my home folder, the commands would look like this:```
cd /home/bob/foo
wine setup.exe
```The installation program should then begin, and will install your program into the fake C: drive located in the .wine folder in your home folder.  If you have a question about whether a program will work or not, be sure to check out the [Wine Application Database]("http://appdb.winehq.org").  In addition, the [Wine Wiki]("http://www.wine-wiki.org/") has some information about general Wine setup and getting programs to work.

Cheers!

---

### Post by fluxbug22 on 2007-11-26
do you mean to add programs that are on the system or programs from a cd or the internet. If you mean programs on the system go to applications-->add/remove programs.

hope this helps

---

### Post by danny cox on 2007-11-26
sorry! had to step out 
things i downloaded like the christian package

---

### Post by jken146 on 2007-11-26
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) is a good guide for installing things.

It is better in almost all cases to install things from the Ubuntu repositories (with Add/Remove, Synaptic, apt-get etc) because dependencies and updates are sorted out for you.

---

### Post by machoo02 on 2007-11-26
> **danny cox said:**
> sorry! had to step out 
things i downloaded like the christian packagePlease try to be a little more specific/give a little more detail as to what you are trying to install, that way we can give you a better, more detailed answer.

---

### Post by danny cox on 2007-11-26
thinks i'm runing  kubuntu i think 6.06 
 
  typed  comand
      danny#danny-laptop:~ $  sudo apt-get install christ 
      password:
     reading pakage lists. . . done
    building dependency tree . . ' done
 E: could not find package christ 
   
 this (christ)  was a rename from convert_to_ ubuntu_christian_edition_feisty

 i can get the termial to find a file

---

### Post by t3h_h4ck3r on 2007-11-26
I have a question!? Where do I install wine? Waht DIR?

---

### Post by TidusBlade on 2007-11-26
You can find WINE, in any Add/Remove Programs, just check the box, and it will install ;) IT's gonna have it's own menu under Utilities in Kubuntu, forgot about Ubuntu.

---

### Post by t3h_h4ck3r on 2007-11-26
even if i dont have an internet connection?

---

### Post by machoo02 on 2007-11-27
> **t3h_h4ck3r said:**
> even if i dont have an internet connection?Unfortunately, no.  Any software that's in the repositories and was not installed during the initial installation requires an internet connection.  The repositories are basically servers that contain all of the software packages.

---

### Post by machoo02 on 2007-11-27
> **danny cox said:**
> thinks i'm runing  kubuntu i think 6.06 
 
  typed  comand
      danny#danny-laptop:~ $  sudo apt-get install christ 
      password:
     reading pakage lists. . . done
    building dependency tree . . ' done
 E: could not find package christ 
   
 this (christ)  was a rename from convert_to_ ubuntu_christian_edition_feisty

 i can get the termial to find a fileWhat kind of file did you download: .deb or .exe?  Where did you get it from?  by the looks of it, it is a package from Ubuntu Christian Edition...did you check for any instructions over at their website?

---

### Post by t3h_h4ck3r on 2007-12-08
can I download it on a seperate computer as an executable file that installs itself, put it on a disk or JumpDrive and then put it on mine?

---

