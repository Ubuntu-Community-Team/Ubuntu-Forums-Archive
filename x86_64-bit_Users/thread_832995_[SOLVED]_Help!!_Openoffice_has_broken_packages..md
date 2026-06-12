---
title: "[SOLVED] Help!! Openoffice has broken packages."
date: 2008-06-18
forum: x86 64-bit Users
---

### Post by indikid on 2008-06-18
Hi, My openoffice has broken packages. Tried to repair them with synamptic but couldn't do so. So i decided to remove it and reinstall. But the same error turns up again. Below is the result when i run synamptic...


E: openoffice.org-calc: Package is in a very bad inconsistent state - you should
E: openoffice.org-writer: Package is in a very bad inconsistent state - you should

Any ideas on how to resolve this??? Thanks in advance folks....:)

---

### Post by Dwezzel on 2008-06-18
Same Here...

Can't do nothing with OpenOffice.  Uninstall and re-install...same results.

Hope somebody will find something...and fast !

Here's somekind of log when trying to start openoffice from a command line : 

```
$ openoffice
$ Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f0ab0a7297c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7f0ab0a72a15]
#2 /usr/lib/libX11.so.6 [0x7f0ab473c323]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7f0ab4733d54]
#4 /usr/lib/libgdk-x11-2.0.so.0(gdk_window_new+0x395) [0x7f0ab061cc05]
#5 /usr/lib/libgtk-x11-2.0.so.0 [0x7f0aabcab4c8]
#6 /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f) [0x7f0aafab0bcf]
#7 /usr/lib/libgobject-2.0.so.0 [0x7f0aafac4386]
#8 /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x875) [0x7f0aafac60d5]
#9 /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83) [0x7f0aafac6483]
#10 /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0x77) [0x7f0aabc9c957]
#11 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f0aac05476d]
#12 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f0aac05516a]
#13 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f0aac05582b]
#14 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f0aac02df64]
#15 /usr/lib/openoffice/program/libvcl680lx.so [0x7f0ab7fd94ed]
#16 /usr/lib/openoffice/program/libvcl680lx.so [0x7f0ab7f6e322]
#17 /usr/lib/openoffice/program/libvcl680lx.so(_ZN9TabDialogC2EP6WindowRK5ResId+0x5f) [0x7f0ab7fab1cf]
#18 /usr/lib/openoffice/program/libsvx680lx.so [0x7f0aa5165084]
#19 /usr/lib/openoffice/program/libsvx680lx.so [0x7f0aa5339db4]
```

Thx...

---

### Post by Sef on 2008-06-18
Try this:

System > Administration > Synaptic Package Manager > Edit > Fix Broken Packages > Follow the directions.

---

### Post by Dwezzel on 2008-06-18
Thx Sef...But didn't do anything more...OpenOffice still can't open itself...neither Writer nor Calc...

Dwe

---

### Post by Dwezzel on 2008-06-18
OK, I found a dirty solution from another site :

#sudo apt-get remove openoffice.org-gtk

And Openoffice is working again !

Officially : Bug #236676 in openoffice.org-amd64 (Ubuntu)

Hope it will helps 

Dwe

---

### Post by saru411 on 2008-06-18
Synaptic Package Manager> Settings> Preferences> Files> Delete Cached Package Files.

Next fix broken dependancies and all should be good to go.

---

### Post by indikid on 2008-06-19
Thanks for all the help guys but it seems that my problem is far from over. I can't access my Synaptic Package Manager. The Program opens but as soon as it does it closes! Tried to launch it through terminal and the program crashed again. This is the output from terminal:  

paul@paul-desktop:~$ sudo synaptic package manager
Segmentation fault
paul@paul-desktop:~$ 

Any advice on how to resolve this??? :( I can't access add/remove programs too. Same error there....

---

### Post by Sef on 2008-06-19
<snip>

---

### Post by PmDematagoda on 2008-06-19
Open up a terminal and execute:-
```
sudo apt-get install --reinstall openoffice.org
```

---

### Post by JKoder on 2008-06-20
> **Dwezzel said:**
> OK, I found a dirty solution from another site :

#sudo apt-get remove openoffice.org-gtk

And Openoffice is working again !

Officially : Bug #236676 in openoffice.org-amd64 (Ubuntu)

Hope it will helps 

Dwe
I have this problem to and this helped me. OpenOffice is running again, but i am wondering when will we get an update so we wont need to do apt-get remove stuff ?

---

### Post by JC Cheloven on 2008-06-20
Hi, My problem was: superior and inferior panels didn't hide during presentations in OOo. I installed **openoffice.org-gtk** and a dependency package, and presentations were fine.

But then I realized that I couldn't export or save in different format from wordprocesoor or spreadsheet (OOo hangs absolutely, not even the xkill thing works). So I uninstalled **openoffice.org-gtk** and now I can export or save in different format again, but I see the panels when running presentations. Choosing from the bads the less bad here...

Edit: BTW, Dematagoda & other wise people: Is there any reason for your recommendation of using apt-get?   Isn't aptitude any better??  Or is just a matter of habit?

---

### Post by Stunts on 2008-06-21
@ JC Cheloven:

I have the same issue as you. Tough I can't run oo.org at all if openoffice.org-gtk is installed.
In order to make the gnome panel go away when viewing presentations in fullscreen mode, all you have to do is click the button "Slide show" instead of hitting F5 to start the presentation.

At least it works for me!

Following the bug reports at launchpad, ir seems that a patch is close to developed, it's just got a few minor glitches to go over before going upstream.

The problem should be solved soon.

---

### Post by indikid on 2008-06-23
> **PmDematagoda said:**
> Open up a terminal and execute:-
```
sudo apt-get install --reinstall openoffice.org
```

I just tried this out but i still can't reinstall openoffice. Once terminal comes across the error it gives this report.

paul@paul-desktop:~$ sudo apt-get install --reinstall openoffice.org
[sudo] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:

  openoffice.org: Depends: openoffice.org-base but it is not going to be installed
                  Depends: openoffice.org-core (= 1:2.4.1-1ubuntu1) but it is not going to be installed
                  Depends: openoffice.org-draw but it is not going to be installed
                  Depends: openoffice.org-filter-binfilter but it is not going to be installed
                  Depends: openoffice.org-filter-mobiledev but it is not going to be installed
                  Depends: openoffice.org-impress but it is not going to be installed
                  Depends: openoffice.org-java-common (> 2.2.0-4) but it is not going to be installed
                  Depends: openoffice.org-math but it is not going to be installed
                  Depends: openoffice.org-officebean but it is not going to be installed
                  Depends: openoffice.org-writer2latex but it is not going to be installed
  openoffice.org-calc: Depends: openoffice.org-base-core (= 1:2.4.0-3ubuntu6) but it is not going to be installed
                       Depends: openoffice.org-core (= 1:2.4.0-3ubuntu6) but it is not going to be installed
  openoffice.org-style-human: Depends: openoffice.org-common (= 1:2.4.1-1ubuntu1) but it is not going to be installed
  openoffice.org-writer: Depends: openoffice.org-base-core (= 1:2.4.0-3ubuntu6) but it is not going to be installed
                         Depends: openoffice.org-core (= 1:2.4.0-3ubuntu6) but it is not going to be installed
                         Depends: python-uno (>= 1:2.4.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
paul@paul-desktop:~$ 

What can i do about this??? :( n oh, apt-get -f install gives me this output....

paul@paul-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-writer python-uno
Suggested packages:
  openoffice.org-base openoffice.org-style-hicontrast
  openoffice.org-style-industrial openoffice.org-gcj
Recommended packages:
  gij java-gcj-compat openjdk-6-jre sun-java5-jre sun-java6-jre java2-runtime
  openoffice.org-filter-binfilter openoffice.org-java-common
  openoffice.org-writer2latex
The following NEW packages will be installed:
  openoffice.org-base-core openoffice.org-common openoffice.org-core
  python-uno
The following packages will be upgraded:
  openoffice.org-calc openoffice.org-writer
2 upgraded, 4 newly installed, 0 to remove and 42 not upgraded.
3 not fully installed or removed.
Need to get 0B/48.8MB of archives.
After this operation, 167MB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing openoffice.org-calc (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
dpkg: error processing openoffice.org-writer (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 openoffice.org-calc
 openoffice.org-writer
E: Sub-process /usr/bin/dpkg returned an error code (1)
paul@paul-desktop:~$

---

### Post by stchman on 2008-06-23
I don't know why people are having this problem.  I have 64 git Hardy running on an Athlon 64 and a Core 2 Quad with no problems.

---

### Post by indikid on 2008-06-23
> **stchman said:**
> I don't know why people are having this problem.  I have 64 git Hardy running on an Athlon 64 and a Core 2 Quad with no problems.

Well this entire problem popped up when I did an upgrade on openoffice.... Things just went awfully wrong from then... Right now i can't even do a single update due to this!!! 

This stinks!!! :(

---

### Post by paulderol on 2008-06-23
the locking assertion failure is [ bug 185311 ]("https://bugs.launchpad.net/ubuntu/+source/libxcb/+bug/185311")
it is being repaired, i am to understand, and a committed fix for Ibex is already upstream.

---

### Post by JC Cheloven on 2008-06-23
> **Stunts said:**
> @ JC Cheloven:

I have the same issue as you. Tough I can't run oo.org at all if openoffice.org-gtk is installed.
In order to make the gnome panel go away when viewing presentations in fullscreen mode, all you have to do is click the button "Slide show" instead of hitting F5 to start the presentation.

At least it works for me!

Following the bug reports at launchpad, ir seems that a patch is close to developed, it's just got a few minor glitches to go over before going upstream.

The problem should be solved soon.

Hi, Stunts,
I tried it, and surprisingly, it works!! Thank you very much. 

The different behaviour of a command being invoked by -in principle- equivalent methods, is beyond me :confused: Let's wait for a proper fix.

It is also strange that lately I get workarounds for my own issues even when posting in other people's threads. Is a pleasure to belong to this helpful community :-)

Greetings

---

### Post by Stunts on 2008-06-24
JC Cheloven,
Here's a better fix for you!

```
cd /usr/lib/openoffice/program/
./soffice.bin
```

This way you can run openoffice.org with GTK integration (using this command it will run even if the packages openoffice.org-gtk and openoffice.org-gnome are installed).
You can even turn it into a script and place a launcher for it in gnome panel to use while the bug gest fixed upstream.

It's still just a  workaround, but I find it better then removing GTK integration.

---

### Post by PmDematagoda on 2008-06-24
> **indikid said:**
> I just tried this out but i still can't reinstall openoffice. Once terminal comes across the error it gives this report.

paul@paul-desktop:~$ sudo apt-get install --reinstall openoffice.org
[sudo] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:

  openoffice.org: Depends: openoffice.org-base but it is not going to be installed
                  Depends: openoffice.org-core (= 1:2.4.1-1ubuntu1) but it is not going to be installed
                  Depends: openoffice.org-draw but it is not going to be installed
                  Depends: openoffice.org-filter-binfilter but it is not going to be installed
                  Depends: openoffice.org-filter-mobiledev but it is not going to be installed
                  Depends: openoffice.org-impress but it is not going to be installed
                  Depends: openoffice.org-java-common (> 2.2.0-4) but it is not going to be installed
                  Depends: openoffice.org-math but it is not going to be installed
                  Depends: openoffice.org-officebean but it is not going to be installed
                  Depends: openoffice.org-writer2latex but it is not going to be installed
  openoffice.org-calc: Depends: openoffice.org-base-core (= 1:2.4.0-3ubuntu6) but it is not going to be installed
                       Depends: openoffice.org-core (= 1:2.4.0-3ubuntu6) but it is not going to be installed
  openoffice.org-style-human: Depends: openoffice.org-common (= 1:2.4.1-1ubuntu1) but it is not going to be installed
  openoffice.org-writer: Depends: openoffice.org-base-core (= 1:2.4.0-3ubuntu6) but it is not going to be installed
                         Depends: openoffice.org-core (= 1:2.4.0-3ubuntu6) but it is not going to be installed
                         Depends: python-uno (>= 1:2.4.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
paul@paul-desktop:~$ 

What can i do about this??? :( n oh, apt-get -f install gives me this output....

paul@paul-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-writer python-uno
Suggested packages:
  openoffice.org-base openoffice.org-style-hicontrast
  openoffice.org-style-industrial openoffice.org-gcj
Recommended packages:
  gij java-gcj-compat openjdk-6-jre sun-java5-jre sun-java6-jre java2-runtime
  openoffice.org-filter-binfilter openoffice.org-java-common
  openoffice.org-writer2latex
The following NEW packages will be installed:
  openoffice.org-base-core openoffice.org-common openoffice.org-core
  python-uno
The following packages will be upgraded:
  openoffice.org-calc openoffice.org-writer
2 upgraded, 4 newly installed, 0 to remove and 42 not upgraded.
3 not fully installed or removed.
Need to get 0B/48.8MB of archives.
After this operation, 167MB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing openoffice.org-calc (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
dpkg: error processing openoffice.org-writer (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 openoffice.org-calc
 openoffice.org-writer
E: Sub-process /usr/bin/dpkg returned an error code (1)
paul@paul-desktop:~$

It has pointed out two packages, so remove them with:-
```
sudo apt-get remove openoffice.org-calc openoffice.org-writer
```
and try:-
```
sudo apt-get install openoffice.org

```

JC Cheloven:- I guess I prefer apt-get because whenever I install an application, I do it because I want to use it and in any case I don't care about the extra packages it installs and leaves behind when removed. aptitude is good, but from my standpoint I really don't see a sizeable difference between the two except that aptitude is less likely to leave unnecessary stuff around than apt-get is.

---

### Post by indikid on 2008-06-24
> **PmDematagoda said:**
> It has pointed out two packages, so remove them with:-
```
sudo apt-get remove openoffice.org-calc openoffice.org-writer
```
and try:-
```
sudo apt-get install openoffice.org

```


Hey PmDematagoda, First of all, thanks for that reply. Secondly, I just tried the first command you gave me. Terminal returned this output.

paul@paul-desktop:~$ sudo apt-get remove openoffice.org-calc openoffice.org-writer
[sudo] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  openoffice.org-calc openoffice.org-writer
0 upgraded, 0 newly installed, 2 to remove and 60 not upgraded.
2 not fully installed or removed.
After this operation, 41.0MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing openoffice.org-calc (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
dpkg: error processing openoffice.org-writer (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 openoffice.org-calc
 openoffice.org-writer
E: Sub-process /usr/bin/dpkg returned an error code (1)
paul@paul-desktop:~$ 


Guess my system is really messed up. I've already reinstalled Ubuntu around 5 times or so, so don wanna do it again.... Is there any other way around this problem? Can't I make terminal ignore this error and install Openoffice.org, and make other upgrades...? Is there a manual way to remove openoffice.org-calc and openoffice.org-writer? I can't make any installation or removal because of this issue... :(

---

### Post by PmDematagoda on 2008-06-24
Ok, try this instead:-
```
sudo dpkg --remove-reinstreq openoffice.org-calc openoffice.org-writer
```

---

### Post by indikid on 2008-06-26
I finally managed to solve this problem after all those weeks of agony! So a[COLOR=Navy]** *BIG THANKS***[/COLOR] to all you guys who helped me out...! I'm still not sure if I did the right thing though, but my system seems to be running fine so far - Either I got damn lucky or it's just a ticking bomb...! so please do tell me if I got it right or not...

PmDematagoda's last command got me going...

> **PmDematagoda said:**
> Ok, try this instead:-
```
sudo dpkg --remove-reinstreq openoffice.org-calc openoffice.org-writer
```

Once i executed the command terminal said it didn't recognise -reinstreg.  So I tried to install openoffice.org again. That turned out the usual error stating that there were unmet dependencies. I deciede to try and use synaptic to fix the packages. This time i deciede to do it one at a time. I opened synaptic and tried a couple of random packages and these didn't work. I tried the openoffice.org-style-human package next. This for some reason unknown to me was installed - and it so happened that that was the only package that got installed!!

Next I tried the force install again:

```
Sudo apt-get -f install 
```The force install command returned and error like before --

> dpkg: error processing openoffice.org-calc (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
dpkg: error processing openoffice.org-writer (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 openoffice.org-calc
 openoffice.org-writer
[COLOR=DarkRed]E: Sub-process /usr/bin/dpkg returned an error code (1)
[/COLOR]Since the error was in dpkg, I googled the last line that told me where the directory was. Found a post by[COLOR=Blue] [feral-deb]("http://www.linuxquestions.org/questions/user/feral-deb-390619/")[/COLOR] in Linuxquestions.org: 

>  [COLOR=Blue][feral-deb]("http://www.linuxquestions.org/questions/user/feral-deb-390619/"):
[/COLOR]I had a similar problem and what i found that worked for me was going into [COLOR=Green]**/var/lib/dpkg/info**[/COLOR] and deleting everything that had that name and you may also have to go into**[COLOR=Green] /var/cache/apt/archives[/COLOR]** and do the same thing. I'm fairly new to linux so if this breaks anything i am sorry. i haven't run into any problems yet that this has caused.
I tried that and deleted every reference to openoffice.org in those two locations. Next I ran 
```
Sudo apt-get update
```and then 
```
Sudo apt-get autoremove
``` Once that was done i reinstalled openoffice.org
```
sudo apt-get install openoffice.org
```Openoffice.org installed without any errors and it was functional again - jus like normal!! :lolflag:

---

