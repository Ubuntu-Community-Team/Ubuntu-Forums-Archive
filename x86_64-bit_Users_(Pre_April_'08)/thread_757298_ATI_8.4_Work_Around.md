---
title: "ATI 8.4 Work Around"
date: 2008-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kilz on 2008-04-16
There is a new 8.4 driver out and [it has a bug]("http://ubuntuforums.org/showpost.php?p=4730372&postcount=4") (surprise surprise) :). This bug can be worked around. This fix only stops this specific install bug. If you have had other problems in the past it will not fix them.

1. [Get the new ATI 8.4 driver save it to your desktop.]("http://ati.amd.com/support/driver.html")
2. [Go here ]("http://wiki.cchtml.com/index.php/Ubuntu")and follow the instructions for your version in creating the packages using the Method #2. Do not install the packages.

Next
1.right click on the xorg-driver-fglrx_8.476-0ubuntu1_amd64.deb and chose Extract Here. This will make a xorg-driver-fglrx_8.476-0ubuntu1_amd64.deb_FILES folder.  Delete the deb, rename it , or move it.
2. Rename the xorg-driver-fglrx_8.476-0ubuntu1_amd64.deb_FILES folder xorg-driver-fglrx_8.476-0ubuntu1_amd64.
3. Inside is a control and a data tar.gz file. Right click on them one at a time and extract them.
4. Delete the control.tar.gz, data.tar.gz and debian-binary file.
5. Rename the control.tar.gz_FILES folder to DEBIAN (case sensitive).
6. Download the attached preinst.tar.gz that matches your version, extract it and add it to the DEBIAN folder, let it overwrite the existing one.
7. inside the  data.tar.gz_FILES folder is a usr and a etc folder , drag them out by the DEBIAN folder and delete the data.tar.gz_FILES folder.
8. Open a terminal and navigate to the folder holding the xorg-driver-fglrx_8.476-0ubuntu1_amd64 folder.
9. Enter this command
```
dpkg -b xorg-driver-fglrx_8.476-0ubuntu1_amd64 xorg-driver-fglrx_8.476-0ubuntu1_amd64.deb
```

The new package should make in a minute. Continue the install at Unofficial ATI Linux Driver Wiki with the new package.

---

### Post by bestguy on 2008-04-16
For what kind of Bug is this the Workaround ? 

Maybe it will help when you declare the Bug

---

### Post by crjackson on 2008-04-16
> **Kilz said:**
> [COLOR="Red"][SIZE="5"]WARNING[/SIZE][/COLOR] there is a bug that returns the error

diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx' clashes with `diversion of /usr/X11R6/lib32/libGL.so.1.2 to /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'

[SIZE="4"]**He Already Did....**[/SIZE]

---

### Post by engindumlu on 2008-04-16
> **crjackson said:**
> [SIZE="4"]**He Already Did....**[/SIZE]

yep, i just finished fixing

---

### Post by casiciaco on 2008-04-17
Hello,
I have applied the fix and then I get the following error:
"
dpkg: error processing xorg-driver-fglrx_8.476-0ubuntu1_amd64.deb (--install):
 cannot overwrite  `/usr/lib32/libGL.so.1', used by package ia32-libs
"
I have translated it from my local language (locale), so may be not the exact message.

I own a HD 3870 and no driver is currently working with my card and monitor (20') 1680x1050
So I am working with vesa driver and 1280x1024.
I want to try this new driver to see if the bug is fixed.

Please, any help ?

---

### Post by Kilz on 2008-04-17
Was this the same error you have gotten with other drivers?

---

### Post by purewater08 on 2008-04-17
> **casiciaco said:**
> 
dpkg: error processing xorg-driver-fglrx_8.476-0ubuntu1_amd64.deb (--install):
 cannot overwrite  `/usr/lib32/libGL.so.1', used by package ia32-libs


I got the same error :(

---

### Post by Kilz on 2008-04-17
> **purewater08 said:**
> I got the same error :(

The error is saying that the file exists in other packages. I have uploaded a [new preinst for Gutsy]("http://ubuntuforums.org/attachment.php?attachmentid=66224&d=1208442874"), I'm still using Feisty (for 2 more days). But if it still doesnt install, use 
```
sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.471-0ubuntu1_amd64.deb
```
To install the package. You should have the ati version of that file if you want to install ati drivers.

---

### Post by casiciaco on 2008-04-17
It worked I have been able to install it.
Thank you.

Unfortunatelly, the driver doesn't work for my  HD3870  :(

---

### Post by purewater08 on 2008-04-17
I am using hardy so I modified the file preinst since the only difference is line 17, dont even know if it matters :p

DISTRO=gutsy  =>  DISTRO=hardy

I still got problem untill remove some packages(maybe the xorg-driver-fglrx) and reboot and it installs, thanks.

---

### Post by bestguy on 2008-04-17
> **crjackson said:**
> [SIZE="4"]**He Already Did....**[/SIZE]

Never got this Error Message. So why should i use a workaround if i don't have an error ?

Maybe its hardware specific and not depending on the new Ati Driver.

---

### Post by Saint Angeles on 2008-04-17
sudo sh ati...

thats the way i've done it since 7.11

with gutsy and hardy. no problems.

---

### Post by Kilz on 2008-04-17
> **bestguy said:**
> Never got this Error Message. So why should i use a workaround if i don't have an error ?

Maybe its hardware specific and not depending on the new Ati Driver.

Maybe its Ubuntu version specific, or dependent on other installed software.

---

### Post by st0nedpenguin on 2008-04-17
> **Saint Angeles said:**
> sudo sh ati...

thats the way i've done it since 7.11

with gutsy and hardy. no problems.

Same here, spent a few hours fiddling about trying all the other fancy install options then just ran the installer and everything has been working fine since.

---

### Post by Playa1313 on 2008-04-18
> **purewater08 said:**
> I am using hardy so I modified the file preinst since the only difference is line 17, dont even know if it matters :p

DISTRO=gutsy  =>  DISTRO=hardy

I still got problem untill remove some packages(maybe the xorg-driver-fglrx) and reboot and it installs, thanks.

This worked for me.

Here is the fixed package ready for hardy x64 if you rather not run that whole process.

[http://www.mediafire.com/?4zn54zxx9d2](http://www.mediafire.com/?4zn54zxx9d2)

---

### Post by Páraquedas_cascais on 2008-04-22
Hi!

After doing all the process workaround, with no error! The xorg.conf looks ok, everthing says ATI in DEVICE and in MONITOR section. Did the restart and :confused::confused::confused: BlackScreen !!! :(

This on a ASUS EAH3870 ! Any sugestions ?

---

### Post by Kilz on 2008-04-22
> **Páraquedas_cascais said:**
> Hi!

After doing all the process workaround, with no error! The xorg.conf looks ok, everthing says ATI in DEVICE and in MONITOR section. Did the restart and :confused::confused::confused: BlackScreen !!! :(

This on a ASUS EAH3870 ! Any sugestions ?

type in ```
dpkg-reconfigure xesrver-xorg
``` and configure the driver.

---

### Post by EmmetCaulfield on 2008-04-26
> **Playa1313 said:**
> 
Here is the fixed package ready for hardy x64 if you rather not run that whole process.

[http://www.mediafire.com/?4zn54zxx9d2](http://www.mediafire.com/?4zn54zxx9d2)

I'm sure it's probably fine, but I'm a bit paranoid about installing packages of unknown provenance. I've posted an explanation of the bug and a script that fixes the broken package, as built by the ATI download, at [http://caulfield.info/emmet/2008/04/fix-ati-catalyst-84-driver-pac.html](http://caulfield.info/emmet/2008/04/fix-ati-catalyst-84-driver-pac.html). It's just a shell-script, so you can read exactly what the script does before you run it.

---

### Post by ronaldvalenzuel on 2008-04-29
Hi, there. I was trying your fix, but now I get stuck with a:
dpkg: error processing xorg-driver-fglrx_8.476-0ubuntu1_amd64.deb (--install):
trying to overwrite `/usr/lib32/libGL.so.1', wich is also in package ia32-libs
Errors were encountered while processing:
xorg-driver....

I'm trying on Ubuntu Hardy ( I took the Gutsy file and change the distro line to hardy). 
Any suggestion? thanks.

---

### Post by Kilz on 2008-04-30
> **ronaldvalenzuel said:**
> Hi, there. I was trying your fix, but now I get stuck with a:
dpkg: error processing xorg-driver-fglrx_8.476-0ubuntu1_amd64.deb (--install):
trying to overwrite `/usr/lib32/libGL.so.1', wich is also in package ia32-libs
Errors were encountered while processing:
xorg-driver....

I'm trying on Ubuntu Hardy ( I took the Gutsy file and change the distro line to hardy). 
Any suggestion? thanks.

You might want to try it again. That is the error its supposed to fix. If you have to use the other file. There isnt any difference that will matter.

---

