---
title: "Installing flash player"
date: 2007-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Slimshady on 2007-03-26
Hi, i installed flash player 9 following this guide:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)
but i still cant watch flash videos.

---

### Post by Kilz on 2007-03-26
> **Slimshady said:**
> Hi, i installed flash player 9 following this guide:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash). 
and it doesnt help, i keep getting the error : 
```
Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest flash player.
```
when i try see videos in youtube....

If you are running the 64bit version of Ubuntu that howto will not work for you. The Browser in the 64bit version is 64bit, it cant use the flash plugin in that howto, because the plugin is 32bit. There are 2 options. 
1. You can install the nspluginwrapper . This is hard to setup and doesn't have java support.
2. You can install the 32bit Firefox and all plugins with my script/howto. The link is in my signature.

---

### Post by Slimshady on 2007-03-27
I tried to install nspluginwrapper, using this guide:
[http://ubuntuforums.org/showthread.php?t=290785](http://ubuntuforums.org/showthread.php?t=290785)
but it didnt work. i get this message:
> slimshady@ubuntu:~$ sudo nspluginwrapper -i /usr/lib/mozilla/plugins32/libflashplayer.so 
nspluginwrapper: /usr/lib/mozilla/plugins32/libflashplayer.so is not a valid NPAPI plugin


---

### Post by Kilz on 2007-03-27
> **Slimshady said:**
> I tried to install nspluginwrapper, using this guide:
[http://ubuntuforums.org/showthread.php?t=290785](http://ubuntuforums.org/showthread.php?t=290785)
but it didnt work. i get this message:

As I said , nspluginwrapper is hard to setup. Just install 32bit Firefox/flash with my script. Its easy and should work without any problems.

---

### Post by Slimshady on 2007-03-27
But you sure it will work well?
and do i have to remove first my 64bit firefox or can i have the both installed?.

---

### Post by Kilz on 2007-03-27
> **Slimshady said:**
> But you sure it will work well?
and do i have to remove first my 64bit firefox or can i have the both installed?.

Im reasonably sure it will work well, seeing how the howto has 120k hits and many satisfied people running 32bit firefox. You can leave the 64bit version installed. The howto doesnt replace the 64bit version because other applications (like the help document viewer) use the 64bit browser. It simply installs a second browser that can use flash.

---

### Post by rjfioravanti on 2007-03-27
when will proper support for 64 bit browser be provided?

---

### Post by Kilz on 2007-03-27
> **rjfioravanti said:**
> when will proper support for 64 bit browser be provided?

The problem isnt the browser, but that Flash is a proprietary format owned by Adobe. As such the open source community does not have access to the code. Dont hold your breath waiting for Adobe to release a 64bit version of Flash. 
But the good news is that a 32bit browser will run just fine on the 64bit version.

---

### Post by ndefontenay on 2007-03-28
I'm having the "not a valid NPAPI" too.

I got it working with flash 32 bit just fine. The only thing is that it's 7.0 and I need 9.0! :?

---

### Post by Kilz on 2007-03-28
> **ndefontenay said:**
> I'm having the "not a valid NPAPI" too.

I got it working with flash 32 bit just fine. The only thing is that it's 7.0 and I need 9.0! :?

You must be running an old install of Firefox 32. The script and howto have been updated for over a month. The manual howto instructions give step by step directions on how to upgrade flash.

---

### Post by Slimshady on 2007-03-28
I downloaded the tar.gz file (which contains the script) , extract it and tried to run the script buy clicking on it but nothing happend. i think i have some problem with script files but i dont know what it is. i tried also run the comman 'sh [filename]' but nothing happend.  any suggestions?

---

### Post by chrism66 on 2007-03-28
Did you choose the "run in a terminal option"?

---

### Post by Kilz on 2007-03-28
> **Slimshady said:**
> I downloaded the tar.gz file (which contains the script) , extract it and tried to run the script buy clicking on it but nothing happend. i think i have some problem with script files but i dont know what it is. i tried also run the comman 'sh [filename]' but nothing happend.  any suggestions?

Inside of the tarball you downloaded is a README file with instructions. Please read and follow them.

---

### Post by Slimshady on 2007-03-29
> **Kilz said:**
> Inside of the tarball you downloaded is a README file with instructions. Please read and follow them.

from the README file:
> Doubble click on the base plugins file. Select "Run In Terminal"
its exactly what i did- but when i choose 'open with' -> 'other' -> 'run in terminal', i cant press ok after that (Ok was disabled).
anyway, just now i tried to choose the script file, and than -> 'tools' -> 'execute shell command' and than ok, and it seems that it runs, but when it gets to the part which i need to choose a browser (1-5) i press 2 and nothing happens. i had to close it, and than i saw in the directory file called 'ia32-lib-firefox-amd64.deb' so what do i do with it?

---

### Post by Kilz on 2007-03-29
> **Slimshady said:**
> from the README file:

its exactly what i did- but when i choose 'open with' -> 'other' -> 'run in terminal', i cant press ok after that (Ok was disabled).
anyway, just now i tried to choose the script file, and than -> 'tools' -> 'execute shell command' and than ok, and it seems that it runs, but when it gets to the part which i need to choose a browser (1-5) i press 2 and nothing happens. i had to close it, and than i saw in the directory file called 'ia32-lib-firefox-amd64.deb' so what do i do with it?

Perhaps it isnt clear to you. Its not telling you to right click and select anything. It is simply telling you, to with the left mouse button perform a double click. A box with the options run in terminal, display, cancel and run should appear. At that point you should select the run in terminal option.

By the way, what version of Ubuntu are you using?

---

### Post by Slimshady on 2007-03-29
> **Kilz said:**
> Perhaps it isnt clear to you. Its not telling you to right click and select anything. It is simply telling you, to with the left mouse button perform a double click. A box with the options run in terminal, display, cancel and run should appear. At that point you should select the run in terminal option.

By the way, what version of Ubuntu are you using?

yes it is clear to me - im not THAT newbe. But as i said - when i double click (yes, with the left button)  on this script (or any other script) nothing happen, nothing, No box runs in no terminal, and nothing else happens.  i dont know why it is, but i think at the beginning (when i just started using linux) it wasnt like that, i think i changed something in the settings, so now i cant run any script. any idea what could it be?

---

### Post by Kilz on 2007-03-29
> **Slimshady said:**
> yes it is clear to me - im not THAT newbe. But as i said - when i double click (yes, with the left button)  on this script (or any other script) nothing happen, nothing, No box runs in no terminal, and nothing else happens.  i dont know why it is, but i think at the beginning (when i just started using linux) it wasnt like that, i think i changed something in the settings, so now i cant run any script. any idea what could it be?

right click on the file, select properties, click on the permissions tab. Make sure the box that allows the file to be executed is checked.

---

### Post by Slimshady on 2007-03-30
Yep, it's already checked. And still, cant execute it.....   :(

---

### Post by Kilz on 2007-03-30
> **Slimshady said:**
> Yep, it's already checked. And still, cant execute it.....   :(

That is a problem, if you cant execute shell scripts you will not have a fully functional system. I have no idea how to fix it either. Your only option as far as firefox32 may be to follow the manual howto. but the problem of no shell scripts is a serious one imho.

---

### Post by Slimshady on 2007-03-31
Actually, i have like half functional system- i mean, some of the commands in the scripts really work. for example, i built a script that is suppose to copy some file, and for debugging i also added echo command in the beginning of the script - so the echo command didnt work, i.e nothing was printed, even i terminal window wasnt  opened, but the copy command did work, the file was copied.  So i dont really know what the hell happens in my system, but if someone has any idea please help me!
if it helps- this problem happen onli in KDE,  in GNOME it works fine. but im working with KDE all the time so.....

---

