---
title: "help with lost data.."
date: 2008-11-28
forum: x86 64-bit Users
---

### Post by U83RMENSCH on 2008-11-28
I was looking up how to wipe a drive in linux.. and i accidentally wiped my primary drive opposed to the secondary drive i was meaning to wipe :/  my bad. ( the command was supposed to write the whole drive with zeros ) 

after seeing half my play list start disappearing as i was listening to music I realized what i had done and switched off the pc.. so all the data cant be lost. 

i booted up puppy off a usb drive to try and recover some files ( i really just need my pictures is all.. every thing else can be recovered else where ). 

can any one help me out and help me find a way to get my pix off this hard drive. I have a second computer running windows XP right now and i can boot puppy off a usb drive if there are any advantages to that as well ( I also have a copy of Ubuntu 8.10 64bit live cd ) 

help please? :(

---

### Post by Sef on 2008-11-28
I have used [Knoppix]("http://knoppix.com") successfully to get data off of hard drives that won't boot up.  

You should be able to use Puppy or Ubuntu for this too.  Just boot them up and find the hard drive then the data that you want to move off the hard disk to a usb key.

---

### Post by U83RMENSCH on 2008-11-28
sorry if this sounds rude.. but what part of i already tried booting into puppy and mounting the drive didnt you understand?

---

### Post by Jouke74 on 2008-11-28
kuch kuch kuch... Backup?

In this order you could try 
NB. I am not responsible for more data loss!
NB. Both program require knowledge of file systems and system repair, so use with care!

1. Testdisk
Use the Ubuntu live-cd and install the program from the repro, or download a deb.

2. Sleuthkit tools
This one is difficult to use.
[http://www.sleuthkit.org/](http://www.sleuthkit.org/)

---

### Post by alwayshere on 2008-11-28
photorec is good recovery app txt based 

sudo apt-get install testdisk

then in terminal put

sudo photorec

its a bios type thing i used it the other dat to get some mp3 files i deleted .

im sure if you google photorec you will find more info on how to use it ,but its easy to figure it out eitherway

takes a while to search so best you search for the type of file you are loooking for eg i search mp3 files 

 good luck

---

### Post by U83RMENSCH on 2008-11-29
this looks like it may work.. however it seems it wants to write to the live disk directories.. If I can restore most of the data I've lost.. I'd like to try and restore as much as possible ( this means a lot of files ) how can I tell test disk to save to a differnt location? I dont have nearly enough memory to save all these files.

---

### Post by alwayshere on 2008-11-29
might be something on these sites that may help ??

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://mirror.href.com/thestarman/testdisk.html](http://mirror.href.com/thestarman/testdisk.html)

---

### Post by U83RMENSCH on 2008-11-29
yeah this looks like those links might help.. i have to get ready for work so I'll have to try them when i get home.. but thanks! :D

---

### Post by gpsmikey on 2008-11-29
Something else to try - not a lot of help, but it can find text you have lost in files.  
Cat the /dev/whatever | strings > newfile_on_another_disk
Yeah, I know it's crude, but it can get a surprising amount of text back - guy at work managed to "rm -r" from the wrong directory (like root instead of where he meant to be and, just for entertainment, he was root when he did it) and managed to get about 80% of his source files back - better than nothing !!
Make sure any writes (new files etc) go to a different partition or even better, a different disk.  You might consider an external hard drive (good for backups too ... )

mikey

---

### Post by Jouke74 on 2008-12-01
In the Ubuntu live disk you can click on places and mount another working partition in addition to the one you are trying to restore. Then use /media/{name of partition here}/ to save your files to.

---

