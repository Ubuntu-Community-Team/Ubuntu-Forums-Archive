---
title: "ies4linux and wine"
date: 2008-08-10
forum: Wine
---

### Post by xecure on 2008-08-10
hello there i have trying to install ies4linux but when i enter the comand in terminal it gives me this error: ```
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

``` also this is what i'm using to install ies4linux```
tar zxvf ies4linux-latest.tar.gz
cd ies4linux-*
./ies4linux

```I am also using WINE 1.1.2 does this mean i have to downgrade my WINE to get IE working on ubuntu?

---

### Post by xecure on 2008-08-13
bump

---

### Post by colobix on 2008-08-13
Could u gimme the ie4linux install command plz?

---

### Post by xecure on 2008-08-13
entering ```
/home/usr/bin/ie6
``` in terminal opens up a window and it is completely white. there are no errors on the terminal console

---

### Post by xecure on 2008-08-14
bump

---

### Post by damis648 on 2008-08-14
Although I see no reason of using IE, Try the official IE6 installer:
[http://cdli.tucows.com/files4/ie6setup.exe](http://cdli.tucows.com/files4/ie6setup.exe)

---

### Post by xecure on 2008-08-14
As much as everyone hates IE, it is very necessary for web developers. Also many websites do not work well (or at all, for that matter) with Firefox, so i am forced to have a copy of IE working.

don't get me wrong, I prefer firefox over IE any day, all I'm saying is that IE is necessary in some cases.

---

### Post by efrens on 2008-08-15
Yeah I noticed that too.
Most likely its an ies4linux installer bug.
The installer must've been made before WINE turned 1.0 and up.

I actually tried to report this to the guy maintaining ies4linux but I can't get anything from tatanka.com.br.

Looks like he's watching over ubuntuforums.org though, so let's wish he'll bump into this thread sooner or later.

Anyway, ies4linux installs fine even with the warning, so I advice you to just ignore it.

[IMG]http://img381.imageshack.us/img381/4328/iediscrepancyeh6.png[/IMG]

One other thing, don't install ies4linux as root! Not like the dumb guy who posted that screenshot. :D (happens to be me)

---

### Post by xecure on 2008-08-20
ies4linux doesn't install fine for me=(
when I click on the icon on my desk top it opens up a white box with "Wine Internet Explorer" in the title

---

### Post by martalli on 2008-08-21
I can get ies4linux to install in hardy heron without too much difficulty...however, it will typically hang after just one use.  It seems that wineserver is hanging, and I often find more than one instance of internet explorer running.  My system subsequently comes to a crawl.

The computers in the office that were not upgraded to Hardy Heron, but instead remain on 7.10, run ies4linux just fine.  I wonder if we should just install an older version of wine, but I can forsee it breakign things such as google earth....

---

### Post by zhuohua on 2008-10-11
Hi, i still get this following errors. What should i do.. please help me.. thanx alot
 btw, i am on kubuntu hardy (wine 1.0)
 
 
 IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).
 
 No user interface available. Use command-line ies4linux or install pygtk. Details: [http://www.tatanka.com.br/ies4linux/page/No_GUI](http://www.tatanka.com.br/ies4linux/page/No_GUI)
 
 IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).
 
 
 Usage: ./ies4linux [OPTIONS]
 
 This script downloads and automagically installs multiple versions of
 Microsoft Internet Explorer on Wine.
 
 Without any option, IEs4Linux will:
 - install IE6
 - install Adobe Flash 9
 - create icons on Desktop and Menu
 - use folder: /home/zhuohua/.ies4linux
 
 You can configure other things:
 
 --install-ie55 Install IE5.5 in BASEDIR/ie55/
 --install-ie5 Install IE5 in BASEDIR/ie5/
 
 --install-corefonts Install MS Core Fonts (corefonts.sf.net)
 
 --no-flash Don't install Adobe Flash Player 9
 --no-ie6 Don't install IE 6
 
 --no-desktop-icon Don't create an icon in Desktop
 --no-menu-icon Don't insert icon on Menu
 
 --full-help Display all possible options

---

### Post by zhuohua on 2008-12-15
finally, i was able to run ies4linux.. ;)

i just did some changing in the script file so it won't compare to the older wine and run under terminal using ./ies4linux --no-gui

---

### Post by xecure on 2009-01-12
exactly what did you run in terminal?

---

### Post by wolfyking2 on 2009-01-12
[http://www.tatanka.com.br/ies4linux/page/Installation]("http://www.tatanka.com.br/ies4linux/page/Installation") try that

---

### Post by Alan McNea on 2009-01-26
I got it working.

Heres how:
1. Go to the directory with the ies4linux script
2. Go to the lib directory
3. Find the file "functions.sh" and open it with a text editor
4. Go to about line 36 in the "functions.sh" file
5. Find the line:
wine --version 2>&1  | grep -q "0.9." || warning $MSG_WARNING_OLDWINE
6. Change it to:
wine --version 2>&1  | egrep -q "0.9.|-1." || warning $MSG_WARNING_OLDWINE
7. Save the changes to the "function.sh" file
8. Go back to the directory with ies4linux
9. Run as normal.

I have already installed ie6 and it seems to run just fine (just got done with it).  I'm off to try and install ie7 now.

Laters.

---

### Post by ITROD on 2009-01-30
> **Alan McNea said:**
> I got it working.

Heres how:
1. Go to the directory with the ies4linux script
2. Go to the lib directory
3. Find the file "functions.sh" and open it with a text editor
4. Go to about line 36 in the "functions.sh" file
5. Find the line:
wine --version 2>&1  | grep -q "0.9." || warning $MSG_WARNING_OLDWINE
6. Change it to:
wine --version 2>&1  | egrep -q "0.9.|-1." || warning $MSG_WARNING_OLDWINE
7. Save the changes to the "function.sh" file
8. Go back to the directory with ies4linux
9. Run as normal.

I have already installed ie6 and it seems to run just fine (just got done with it).  I'm off to try and install ie7 now.

Laters.

This is great Alan....Thanks for your contribution and I look forward to using your IE7 fix....cheers!!!! ITROD

---

