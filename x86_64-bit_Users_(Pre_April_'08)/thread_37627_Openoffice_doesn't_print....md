---
title: "Openoffice doesn't print..."
date: 2005-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Optimal Aurora on 2005-05-27
I don't know where to put this at... I am presuming it may be me and my system... but openoffice prints under like fedora and windows, but the instance I go into Ubuntu and try to print for me a new or existing document I can't print. I don't know what is wrong... Ubuntu and Openoffice start-up successfully all the time but I am having problems because it won't print. Any help would be seriously appreciated... 

Thanks,
Aurora...

---

### Post by ::DoGG:: on 2005-05-28
What kind of a printer do you have ? Are you using CUPS ? did the printer worked on other 64 bit distros (if you had one) ? Are you able to print test page from system printing menu ?

---

### Post by Optimal Aurora on 2005-05-28
Yes it did with Fedora and I can print stuff from the net through firefox, I have it setup and configure even printed the test page... I have an old IJ600 compaq printer that uses the lexmark z32-tweaked print driver of cups...

---

### Post by Jarz Corp on 2005-06-08
As U will see if U search the forum(s) the print-link between cups and openoffice is broken in ubuntu. I am pretty sure it has worked and that this is something that was introduced via an update.

Can U actually see your printer within openoffice or only from the Printing (tool) in System>Administration ?

If it is the openoffice-cups problem U have run into, U will have to wait until v 2.something before it will be solved. It seems that nobody is going to do anything about it in version 1.something.

[http://www.ubuntuforums.org/showthread.php?t=16266&highlight=openoffice+cups](http://www.ubuntuforums.org/showthread.php?t=16266&highlight=openoffice+cups)

---

### Post by Optimal Aurora on 2005-06-11
no it saids that it is genric printer and doesn't include what I named the printer (Z32)... Thanks... I tried the Breezy version and it worked but, the after rebooting well the operating system wouldn't load so I had to reinstall...

---

### Post by Jarz Corp on 2005-06-12
Yes like I said the link is broken and the generic printer U could see in openoffice is the ooo default one and has nothing to do with your actual printer, it hasn't just renamed it. It doesn't communicate with the printer system at all.

U had to reinstall because it wouldn't boot, okay linux is going to be a very very bad experience for U if U reinstall everytime there is something U don't understand, but hey this way U also avoid learning anything from the experience.

---

### Post by wiraone on 2005-06-12
I'm having similar problem, I couldn't setup printer from Open Office. I've created new printer in Gnome, but the only printer available is generic printer, tried using OOadmin to add printer, but it dies before it let me add any printer.

---

### Post by hva on 2005-06-13
If you remove openoffice.org-gtk-gnome package your openoffice will be a bit uglier, but your cups printers will show in printing dialog as they're supposed to be.

---

### Post by Jarz Corp on 2005-06-14
Hmm seemed like a logical enough tip, so I tried it and it didn't work.

But hey I am on the 64bit platorm, so I have kind of gotten used to stuff not working by now.

---

### Post by wiraone on 2005-06-14
I can see the printer now .. but I still couldn't print out..!!

---

### Post by Jarz Corp on 2005-06-14
Well running into this problem along with the ooadmin one, has made me turn to abword, which is true opensource and a hell of a lot faster.

---

### Post by rsw on 2005-06-14
[QUOTE=Jarz Corp]Well running into this problem along with the ooadmin one, has made me turn to abword, which is true opensource and a hell of a lot faster.[/QUOTE]

same. works for printing simple school papers and such, however sooner or later I'm going to need openoffice to be able to print.

---

### Post by desdinova on 2005-06-14
Someone on here recently posted the link to deb's of the newest OO.org 2.0 - which has behaved like a charm for me

---

### Post by Jarz Corp on 2005-06-15
That sounds interesting, I have only heard praise about oooooo2 from the people who have tested it. It should also have the final features that are going to kill that other way to expensive low-grade piece of ram chugging software, can't remember the name. And by final features I don't mean an animated papirclip btw.

I will still use abiword for the day to day letters etc, it is sooo fast.

---

### Post by rsw on 2005-06-15
[QUOTE=desdinova]Someone on here recently posted the link to deb's of the newest OO.org 2.0 - which has behaved like a charm for me[/QUOTE]

Mind finding that post? I can't seem to locate it or these mythological packages ;) Thanks

---

### Post by estel on 2005-06-18
Found a nice way to get x86_64 OOo 2.0 builds.

[ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/ooo64bit02/Build-3/](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/ooo64bit02/Build-3/) has a .rpm which will Alien perfectly, and install to /opt/ using dpkg. Using it now :)

Sooo much better than OOo 1.1.3

---

### Post by Optimal Aurora on 2005-06-18
hay thanks I didn't think about looking for the rpm files...

---

### Post by Optimal Aurora on 2005-06-18
hay and they even got a .deb file, even more cool...

---

### Post by Optimal Aurora on 2005-06-18
Thanks, it works perfectly...

---

### Post by rsw on 2005-06-18
well, it installs and 'swriter' starts, seems to run fine.....


..... and then you go to try and use it :(

1. Save a file as .doc. Try to open it. It just sits there "importing the file", hung, using 99% of the cpu. no errors in the terminal (im launching from a terminal as a normal user with: /opt/openoffice.org1.9.108/program/soffice). no change when running it as root either.

2. Tried to save it as the default '.odt' filetype, it won't save it, just keeps bringing up the save-as dialog box. It never writes the file anywhere i tell it to, (yes every destination is writeable my user). The only filetype it will save to is .doc, ironically. hehe

A nice attempt, but broken as all hell.... unless you guys are installing this some other way? I made .deb's out of each of the rpms within that 75MB file (in the RPMS dir) and installed all of them with dpkg -i.

---

### Post by Optimal Aurora on 2005-06-18
[QUOTE=rsw]well, it installs and 'swriter' starts, seems to run fine.....


..... and then you go to try and use it :(

A nice attempt, but broken as all hell.... unless you guys are installing this some other way? I made .deb's out of each of the rpms within that 75MB file (in the RPMS dir) and installed all of them with dpkg -i.[/QUOTE]

Why didn't you use the following: **sudo alien -i openoffice.org*** to install them because, it didn't give me any problems... and works perfectly, other than me having to use SMEG to edit the gnome applications menu...

Oh and alien -i installs it and does basically what dpkg does but without completely erasing like dependencies and all, but then too they were no dependencies...

---

### Post by rsw on 2005-06-20
[QUOTE=Optimal Aurora]Why didn't you use the following: **sudo alien -i openoffice.org*** to install them because, it didn't give me any problems... and works perfectly, other than me having to use SMEG to edit the gnome applications menu...

Oh and alien -i installs it and does basically what dpkg does but without completely erasing like dependencies and all, but then too they were no dependencies...[/QUOTE]

I just downloaded the rpms again and tried your method... 

1. There ARE dependencies. I didn't have gcc4.0 (and in turn, libstdc++6 which this version of OO requires) and the .deb's from alien complained about this.

2. the 'test-tool' package conflicts with one of the core packages, tries to overwrite some file in it. I just deleted the test-tool rpm. 

anyways, same exact behavior as when i tried just using alient to convert & install with dpkg: hangs on "importing document..." 

Do you have the test-tool package installed? I have everything else installed except for that. Also, how are you launching this? Upon installation I have to run # chmod 755 -R /opt/openoffice.org1.9.108/program/ since they're not set executable by default. Perhaps you're running this a different way since you dont mention doing anything other than installing the packages with alien.

---

### Post by Tremblay on 2005-06-28
I experience the same problems as rsw (opening *.doc files; saving as *.odt and as *.doc files). I'm using the AMD64-k8 kernel (not the AMD64-generic kernel). I used Optimal's "sudo alien -i openoffice*" to install and am using "sudo /opt/openoffice.org1.9.108/program/soffice" to run the application (with which I can't do anything afterwards :P )

I also had to chmod 755 -R /home/tremblay/.openoffice.org1.9.108 -- since none of the files there were executable.

Could it have something to do with the fact that the files' owner is set to 'root' everywhere? Could this come in conflict with procedure calls once inside Open Office?

---

