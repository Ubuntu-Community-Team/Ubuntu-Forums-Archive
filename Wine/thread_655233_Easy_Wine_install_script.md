---
title: "Easy Wine install script"
date: 2008-01-01
forum: Wine
---

### Post by Ferrat on 2008-01-01
Well made a script a while back by chopping and pusseling with other peoples scripts to get a wine script that worked good and installed the stuff needed ect. for a good stable install. 

Well the synaptic version is always behind and wine most often work best with the latest version and also I've seen alot of people having trubble with their wine install not being sure what exactly to install and what is needed ect.. and I've been attaching it from time to time in answers to help people out so I thought that it would just be easier making a thread for it to link to that also ensures people that it's a good script and help make it even better if possible. 

If you use it please give feedback of what you thought and how it worked for you and your system :) 


[COLOR="Red"][SIZE="4"]What does the script do? [/SIZE][/COLOR]

Well its a really simple script, it askes you for what version of wine you want to install (latest version number can be found at [http://www.winehq.org](http://www.winehq.org) )

then you get a option if you want to install it after the script is done.. [COLOR="Red"]why this you ask? isn't this a install script?[/COLOR]
Well yes but the script generates a .deb file, a pkg that will register with your system for easy uninstall in synaptic, also this makes it possible to easy switch between version by just uninstalling and installing the pkgs as you see fit and this is good for if you have a game/program that won't run on the latest due to regression ect. but all the other ones works better with the latest.

after that it wants to install all the useful pkgs that wine uses everything is in the Ubuntu repositories so there should be no trubble

Then it generates the pkg file and if you wanted installs it. 

all the files end up in your home directory in a folder called winestuff, I recommend you delete all files that are there except the .deb file cause the .deb file is 15-20MB but the full unpacked source is ~500MB  and you only need the .deb file for installing it.

[COLOR="Red"][SIZE="4"]run the script or any script [/SIZE][/COLOR]

Open up a terminal 

navigate to the place where you extracted the script 

type in 
> 
sh wineCMD


and the script should launch

And as stated before all feedback is good, if you have any trubble just ask and if you got ideas for how to improve it please tell me :)


EDIT:
Script updated for Hardy (replaced some libs etc)

---

### Post by Izek on 2008-02-09
I have to say, your script downloads a hefty load (way over 150 MB) to just package a deb file that's about 15-20 MB. It's still doing its thing (after about 25 mins of it being started. It also said at one point I need the gutsy CD, so I gave it what it wanted. Good thing I didn't tell it to install after the file was done, it would have taken more time, plus given conflict errors because wine is still installed (0.9.54)

It froze on this command for about a minute or two, then started again...
```
gcc -c -I. -I. -I../../../include -I../../../include   -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -g -O2  -o vartype.o vartype.c

```

After a while... I got this message... (30+ mins after starting your script)

```
======================== Installation successful ==========================
grep: /var/tmp/IYZaGDreeLrbWWgVGCQSp/newfile: No such file or directory
```

And after a few seconds, terminal quit. **After installing this deb file... Wine did not get added to the Applications list.**

---

### Post by pcjunkie on 2008-02-11
how do you run a script like this?

---

### Post by aoanla on 2008-02-11
> **Izek said:**
> I have to say, your script downloads a hefty load (way over 150 MB) to just package a deb file that's about 15-20 MB.

Yes, it compiles the version of wine you selected from source - the extra stuff it is downloading are all the libraries that the Wine source code needs to be compiled with. 
(If I used it, it would download hardly anything, since I already have most of these development libraries installed.)

>  It's still doing its thing (after about 25 mins of it being started. It also said at one point I need the gutsy CD, so I gave it what it wanted. Good thing I didn't tell it to install after the file was done, it would have taken more time, plus given conflict errors because wine is still installed (0.9.54)

It froze on this command for about a minute or two, then started again...
```
gcc -c -I. -I. -I../../../include -I../../../include   -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -g -O2  -o vartype.o vartype.c

```


Yes. Compiling complex code takes a long time. The command that it "froze" on is a compile step - the vartype.c file presumably references lots of other files, or has hard-to-optimise code in it.

> 
After a while... I got this message... (30+ mins after starting your script)

```
======================== Installation successful ==========================
grep: /var/tmp/IYZaGDreeLrbWWgVGCQSp/newfile: No such file or directory
```

And after a few seconds, terminal quit.

That line appears to be output from the Wine source compilation process, rather than the script itself. I doubt that there's much that the author can do about it...

> 
 **After installing this deb file... Wine did not get added to the Applications list.**

I'm not surprised. I doubt the deb it creates is clever enough to alter things like the menus and so on - it just installs the compiled version of Wine...

---

### Post by Ferrat on 2008-02-11
No it doesn't show up in the app menu until you have installed anything with it then wine itself should make a entry under applications but it shows up in synaptic from the get go making it easier to uninstall

The 
> ======================== Installation successful ==========================
grep: /var/tmp/IYZaGDreeLrbWWgVGCQSp/newfile: No such file or directory

Should AFAIK mean that the installation was successful and that the tempfile is removed

yes it's a lot of downloading if you don't have all the packages, some are for building, others are for optimizing wine and installing everything that wine uses, for ex. (I think) it makes sure you have all the audio packages needed so you don't miss out on anything that wine can do.

and make sure to remove all the files except .deb created in the $HOME/winestuff/0.9.xx/ since the uncompiled source is ~500MB

---

### Post by Ferrat on 2008-02-11
> **pcjunkie said:**
> how do you run a script like this?

just open up a terminal 

go to the directory that has the script in the terminal

for ex. 

$HOME/Desktop/

if you downloaded it to your desktop

then just run it with 

> sh wineCMD

I'll put this in the first post, as well =)

---

### Post by Izek on 2008-02-12
Also, I'd like to ask you if you plan to add menu edits in the future.

---

### Post by Ferrat on 2008-02-13
you mean a gui for it?

---

### Post by Izek on 2008-02-13
> **Ferrat said:**
> you mean a gui for it?

No, a gui for your script would be a window telling what's going on. I mean to add the menu edits to the deb file that it creates (like with the normal deb file does when installing Wine 9.54)

---

### Post by Ferrat on 2008-02-13
Well wine should show up in your applications list as soon as you have installed anything with wine, if you mean like crossovers menu that has a lot of options ect then not it's not something I've planed

---

### Post by Izek on 2008-02-13
> **Ferrat said:**
> Well wine should show up in your applications list as soon as you have installed anything with wine, if you mean like crossovers menu that has a lot of options ect then not it's not something I've planed

Using your script didn't make wine appear in the applications list, that's what I was saying.

---

### Post by Ferrat on 2008-02-13
> **Izek said:**
> Using your script didn't make wine appear in the applications list, that's what I was saying.

Have you installed anything in wine(not just installed wine but installed something in to wine)? cause that should make wine create an own entry at least it does for me

---

### Post by Izek on 2008-02-13
> **Ferrat said:**
> Have you installed anything in wine(not just installed wine but installed something in to wine)? cause that should make wine create an own entry at least it does for me

Wine has three things in the application menu by default (without installing anything in wine)

Applications > Wine > Applications > Notepad
Applications > Wine > Browse C:\ Drive
Applications > Wine > Configure Wine

I'd install something, but I recently switched back to WinXP to test **Wompiz**.

---

### Post by Ferrat on 2008-02-13
Ah ok never used the maintained one, prefer one that I know is more attuned for my system, but I can look in to that, not sure if it's a compiling add or source add, if it's a source add then I can't do it since my script gets the source dir. from wines ftps. 

I'll let you know what I find out =)

---

### Post by Izek on 2008-02-14
> **Ferrat said:**
> Ah ok never used the maintained one, prefer one that I know is more attuned for my system, but I can look in to that, not sure if it's a compiling add or source add, if it's a source add then I can't do it since my script gets the source dir. from wines ftps. 

I'll let you know what I find out =)

You may just want to talk with **scott**@**open-vote.org** (Scott Ritchie)

---

### Post by PsYcO~KJ on 2008-04-15
Well i was trying to install wine using the source, and saw a post of yours somewhere, and i was like yes, a script to do the work for me, im in love, yay.

so its going now, doing its thing, idk if its good yet or not, just the occasional "y" to get it to continue.

This is my first day on Linux, as i didnt wanna have to purchase a new windows version to run my 4gigs of ram, and its just cheaper/easier to get Linux up n running, if you know what to do, and have your 4gig good to go

---

### Post by Izek on 2008-05-09
> **PsYcO~KJ said:**
> Well i was trying to install wine using the source, and saw a post of yours somewhere, and i was like yes, a script to do the work for me, im in love, yay.

so its going now, doing its thing, idk if its good yet or not, just the occasional "y" to get it to continue.

This is my first day on Linux, as i didnt wanna have to purchase a new windows version to run my 4gigs of ram, and its just cheaper/easier to get Linux up n running, if you know what to do, and have your 4gig good to go

I'm pretty sure Win XP can run 4 GB of RAM. If not, there's always ReactOS in the future.

---

### Post by ssarkarhyd on 2008-08-19
Hi,

I followed your directions by the book. However towards th end after all individuals compiles went right, it asked me for my sudo pwd, which I gave, but the .deb file was not generated. feel very frustrated after such hefty downloading in a low-speed connection. Sucks

---

### Post by kevinsmith2050@gmail.com on 2008-08-19
hi

kevin.........:popcorn:

:guitar::lolflag:
[MinnesotaDrugTreatment]("http://www.drugtreatments.com/minnesota")

---

