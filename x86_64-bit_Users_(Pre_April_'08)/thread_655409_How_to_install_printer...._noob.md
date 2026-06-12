---
title: "How to install printer.... noob"
date: 2008-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrchaos101 on 2008-01-01
SCX-4521F    By Samsung


This is an All in one printer.   I would like to be able to scan and such... but this may be a bit to be asking.

Any help on getting this printer to at least print would be nice.

---

### Post by tgilber1 on 2008-01-01
> **mrchaos101 said:**
> SCX-4521F    By Samsung


This is an All in one printer.   I would like to be able to scan and such... but this may be a bit to be asking.

Any help on getting this printer to at least print would be nice.

Try the following URL to download Samsung's unified driver, which also has the instructions to install the ppd

[http://www.samsung.com/us/support/download/supportDownDetail.do?group=&type=&subtype=&model_nm=SCX-4200&mType=DR&dType=D&vType=R&cttID=828690&prd_ia_cd=&disp_nm=SCX-4200](http://www.samsung.com/us/support/download/supportDownDetail.do?group=&type=&subtype=&model_nm=SCX-4200&mType=DR&dType=D&vType=R&cttID=828690&prd_ia_cd=&disp_nm=SCX-4200)


Installation instructions

build date : 2007-11-22  Unified Linux Driver

[Ubuntu OS Installation]
1. Download and extract the driver
2. Open terminal'' #from Ubuntu use sudo rather than root
3. Execute installation program.
$ sudo cdroot/autorun
4. After intall, PPD path is set again.
$ sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/custom/samsung
5. Execute Configurator, and Add your printer model name by Add Printer

---

### Post by Bruce M. on 2008-01-01
> **mrchaos101 said:**
> SCX-4521F    By Samsung


This is an All in one printer.   I would like to be able to scan and such... but this may be a bit to be asking.

Any help on getting this printer to at least print would be nice.

Check out this [site]("http://www.elijahlofgren.com/ubuntu/#scx-4521f"), it should solve your problem.

Happy New Year.
Bruce

---

### Post by mrchaos101 on 2008-01-01
ok forgive me for this.....

at terminal how do i CD to my desktop

I have the unifided driver and I extracted it to my desk top

I need to sudo run the auto run from the terminal

Also how do I run a file from the terminal?

---

### Post by Kilz on 2008-01-01
cd = change directory             
When the terminal opens it starts out in your home folder by default
```
cd Desktop 
```will get you to your desktop
./filename will execute files if they can be.

---

### Post by Bruce M. on 2008-01-01
> **Kilz said:**
> cd = change directory             
When the terminal opens it starts out in your home folder by default
```
cd Desktop 
```will get you to your desktop
./filename will execute files if they can be.

:(  I type too slow.

---

### Post by mrchaos101 on 2008-01-01
thanks

seems to be close to how Dos worked so I may be ok

I figured out  the /  part

if I as  in /home   and there was an folder in  /home/folder1/folder2

I could tell it  cd /folder1/folder 2   (i think)

How do I back up one leve?

Before in Dos I could do    CD..   and it would back me up one level.

---

### Post by Bruce M. on 2008-01-01
> **mrchaos101 said:**
> thanks

seems to be close to how Dos worked so I may be ok

I figured out  the /  part

if I as  in /home   and there was an folder in  /home/folder1/folder2

I could tell it  cd /folder1/folder 2   (i think)

How do I back up one leve?

Before in Dos I could do    CD..   and it would back me up one level.

Found this [here]("http://www.ss64.com/bash/"):

 cd

Change Directory - change the current working directory to a specific Folder.

SYNTAX 
      cd [-LP] [directory]

OPTIONS
    -P  : Do not follow symbolic links
    -L  : Follow symbolic links (default)

If directory is not given, the value of the HOME shell variable is used.

If the shell variable CDPATH exists, it is used as a search path.
If directory begins with a slash, CDPATH is not used.

If directory is `-', this will change to the previous directory location (equivalent to $OLDPWD ).

The return status is zero if the directory is successfully changed, non-zero otherwise.

Examples

move to the sybase folder
$ cd  /usr/local/sybase
$ pwd
/usr/local/sybase

Change to another folder
$ cd /var/log
$ pwd
/var/log

Quickly get back
$ cd –
$ pwd
/usr/local/sybase

move up one folder
$cd ..
$ pwd
/usr/local/

$ cd     (Back to your home folder)

----
Bruce

---

