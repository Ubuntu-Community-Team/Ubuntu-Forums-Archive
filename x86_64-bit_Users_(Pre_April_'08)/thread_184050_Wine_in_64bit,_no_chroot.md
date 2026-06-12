---
title: "Wine in 64bit, no chroot?"
date: 2006-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Randomskk on 2006-05-29
I installed Google's Picasa program, which uses Wine to run, in my 64-bit breezy by using --force-all on dpkg, and making sure ia32-libs was installed from the repos.
And it works!

If this works, how come I still can't get wine on 64 bit without a chroot?

---

### Post by Kilz on 2006-05-29
[QUOTE=Randomskk]I installed Google's Picasa program, which uses Wine to run, in my 64-bit breezy by using --force-all on dpkg, and making sure ia32-libs was installed from the repos.
And it works!

If this works, how come I still can't get wine on 64 bit without a chroot?[/QUOTE]

I dont know about Breezy, but I have 32 bit wine installed on Dapper 64 without a chroot. I used the sudo dpkg --force-architecture -i <packagename> command to install it. Granted it dosent find icons for things it installs to the desktop, but its a simple thing to change the icon on the launcher. So far I have IE, dvdshrink, CDisplay, and the windowz version of firefox installed with wine.

---

### Post by skippy81 on 2006-05-29
any chance you could tell me specifically what the names of the packages you installed were please Kilz?  I wouldnt mind having a go at what you did :)

---

### Post by Kilz on 2006-05-29
[QUOTE=skippy81]any chance you could tell me specifically what the names of the packages you installed were please Kilz?  I wouldnt mind having a go at what you did :)[/QUOTE]
No problem telling you, but its been a week since I did it. I just set up a testing partition so I can write it down as I install it so I dont forget anything. A hour or so and I will post here with some instructions others can follow.

---

### Post by Kilz on 2006-05-29
Ok here it is, I'm glad I installed the testing partition because it has a few steps I forgot about. If this works for a few people maybe I will try my hand at writing a howto on it. I'm not the best at the command line yet so some of the instructions use the gui. I dont know if this method will work with anything but Dapper, anyone willing to try please post if it dose work.

Make sure dpkg-dev is installed, I used snaptic to install it. You need it to open up .deb packages in the archive manager. I'm not sure if you need universe or multiverse for the install because I have them already setup.


Ok download the wine package
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fw%2Fwine%2Fwine_0.9.9-0ubuntu1_i386.deb&md5sum=133a5ccfa3f5514283989fa1e7ce4065&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fw%2Fwine%2Fwine_0.9.9-0ubuntu1_i386.deb&md5sum=133a5ccfa3f5514283989fa1e7ce4065&arch=i386&type=main)

get the libxxf86dga1 package

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibx%2Flibxxf86dga%2Flibxxf86dga1_1.0.0-0ubuntu3_i386.deb&md5sum=f1f2a20a6db2bf5eb44db45cdb3a1337&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibx%2Flibxxf86dga%2Flibxxf86dga1_1.0.0-0ubuntu3_i386.deb&md5sum=f1f2a20a6db2bf5eb44db45cdb3a1337&arch=i386&type=main)


extract the data.tar.gz from libxxf86dga1
extract the contents of data.tar.gz
There should be a /usr folder on the desktop now
I used gksudo nautilus to open nautilus as root and copy the contents of /home/username/Desktop/usr/lib to /usr/lib32
Close the terminal
Reopen the terminal


cd ~/Desktop

sudo dpkg --force-architecture -i wine_0.9.9-0ubuntu1_i386.deb

Install sidenet

Download 
[http://sidenet.ddo.jp/winetips/files/wine-config-sidenet-1.9.1.tgz](http://sidenet.ddo.jp/winetips/files/wine-config-sidenet-1.9.1.tgz)
extract

cd ~/Desktop/wine-config-sidenet 
./setup

Answer yes to if you want it to setup
Chose language, or hit enter for English

option 0 for install. IE errors out on install if you chose options 1-3

type in winecfg to test wine install

To get IE installed I had to use a few tricks

In snaptic install cabextract

Go to Ies4linux and download ies4linux
Extract ies4linux

then 
cd ~/Desktop/ies4linux-2.0beta6
./ies4linux
n
n
enter or chose language
y
sit back as it installs

Close the explorer window

Open up your home folder, click Edit, then preferences, on views tab select "show hidden and backup files" click close. Close and reopen Home folder.

Open /.ies4linux/ie6/c_drive
cut and paste the Program Files and windows folders into the c folder in home. Click replace all
Go to /.ies4linux/ie6 copy the 3 .reg files to the .wine folder in your home folder and click replace all

You can copy the nice IE in a wine glass icon from ./ies4linux and then delete the ./ies4linux folder and the launcher for IE on the desktop.

open /home/c/Program Files/Internet Explorer and right click on the iexplore binary. Chose open with other application, then use custom command, click browse, then chose wine and click open, then click open again. IE starts and associates wine to .exe files. You can add a launcher for IE now using the command wine "C:\Program Files\Internet Explorer\IEXPLORE.EXE" to launch it.

The only problems you will have now is that launchers placed on the desktop by install programs wont have a fancy icon. But that is easily fixed.

---

### Post by holomorph on 2006-06-02
Thanks for the tutorial; I just did this, but skipped all the buisness with sidenet and IE etc.  Installed windows firefox and flashplayer plugin, so now I can watch strongbad again :D

---

### Post by Xilon on 2006-06-03
oh yeAH!!! Thank you, thank you, thank you, thank you, thank you, thank you, thank you, thank you :P

I've been trying to setup Internet Explorer with wine for AGES, I knew how to install wine without a chroot but I could never get winetools to work and sidenet didn't want to install IE! Too bad it's a bit too late since I mainly wanted IE for flash because I need to see a site for uni but now that unit is finished :( lol still good :)

---

### Post by Aurdal on 2006-06-03
Am I missing something here?

Why on earth would you want to use IE?

---

### Post by Kilz on 2006-06-08
[QUOTE=Aurdal]Am I missing something here?

Why on earth would you want to use IE?[/QUOTE]

There are lots of reasons. My personal reason is that I have one web site that I have to access to find out about getting paid. It only runs in IE, and no other browser, I have tried them all. 
I have read that some people who design web sites aslo like to check their site to see how it looks for people with IE. So they have it installed.
Im not recommending it for surfing. But if you need it, and its the only reason you still have a windows partition, you can now run it under wine.

---

### Post by fluffington on 2006-06-09
Thanks, Kilz. I've been trying to figure this out for days.

[QUOTE=Aurdal]Am I missing something here? Why on earth would you want to use IE?[/QUOTE]

I develop web sites. Most people use IE. Therefore, it's in my best interest to make sure my sites work in IE, especially when I'm getting paid.

---

