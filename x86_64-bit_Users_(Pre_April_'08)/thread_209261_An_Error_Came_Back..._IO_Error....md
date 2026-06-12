---
title: "An Error Came Back... I/O Error..."
date: 2006-07-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Miki01 on 2006-07-04
I am trying to move some of my files/documents from my old Windows XP computer into this one. Whenever I insert a disc into my drive and then open it up from the desktop, it looks like this (attached image #2) What's causing this problem? When I insert the disc back into my other PC running XP, its fine. What I do is right-click on the CD icon on the desktop and goto Eject. Once the CD is ejected, I press the eject button on my CD drive to bring the disc back in. At this point, I can see the correct names and icons in the disc. But when I try to drag and drop a file from the CD to my dekstop (or anywhere, for that matter, it keeps bringing up an "I/O Error". It disappeared at one point and I was able to transfer files again, but now it came back... How do I go about fixing this blasted error for good?

See the attached image to see what I mean.

This all came back after I used EasyUbuntu...

---

### Post by scxtt on 2006-07-04
the boxes look like the result of your system trying to use the wrong "language" - which you should be able to select when you login (if you're using GDM) ...

the I/O error might be a problem w/ the CD ...

---

### Post by Miki01 on 2006-07-04
I don't know, because this morning I was able to copy those files correctly. But then I deleted it along with some other stuff on my desktop. Then I used easyubuntu. After that I tried to copy the files in again but the i/o error came. I even get character errors with my torrent client... (see attached image for torrent client)

I just logged out, change the language, and logged back in... The characters are still blocks...

---

### Post by scxtt on 2006-07-04
did you try the language thing i mentioned before?  something like the screenshot i'm attaching (it's Xubuntu, but same difference) -- try setting it to English (USA) and see if you still have that problem ... as far as the I/O error, did you try it again? -- does it always happen?

---

### Post by Miki01 on 2006-07-04
I just logged back in... Bit Torrent still looks like a pile of blocks... I wonder what happened in order to make it do this...

---

### Post by Kilz on 2006-07-05
[QUOTE=Miki01]I just logged back in... Bit Torrent still looks like a pile of blocks... I wonder what happened in order to make it do this...[/QUOTE]
When you started the torrent. Did you download the torrent file to your desktop. Then open it with bittornado or open it with bittornado from the firefox download box that pops up asking what do you want to do with a file?

---

### Post by Miki01 on 2006-07-05
I opened it through firefox.

Also, the characters don't seem to affected only in bitornado, when I tried to download and install google's desktop video uploader, the characters were messed too... (attached image)

---

### Post by Kilz on 2006-07-05
[QUOTE=Miki01]I opened it through firefox.

Also, the characters don't seem to affected only in bitornado, when I tried to download and install google's desktop video uploader, the characters were messed too... (attached image)[/QUOTE]
This has to do with the fact you installed 32bit firefox with a work around. Remember me telling you that I had just updated my howto in the previous post? What I updated was a fix for this. [You will need this file]("http://www.ubuntuforums.org/attachment.php?attachmentid=12277&d=1152141374"). Download it to your desktop, then extract the file to your desktop. Then open a terminal
```

sudo cp -r  ~/Desktop/libpangohack/* /usr/lib32
```
After that you can delete the files on your desktop, next
```
gksudo gedit /usr/local/bin/firefox32
```
The text editor will start. The second line needs editing, to make the file look like this
```
#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0
export LD_PRELOAD=/usr/lib32/libpangohack.so.0
linux32 /usr/local/firefox32/firefox $@
```
Then close all firefox windows, and restart it. The problem will be gone when starting other programs for downloaded files with firefox.

---

### Post by Miki01 on 2006-07-05
When I entered the 2nd line in your first code, I got this:

> miki@Ubuntu:~/Desktop$ sudo cp -r  /libpangohack* /usr/lib32
cp: cannot stat `/libpangohack*': No such file or directory


I had already downloaded the file to my desktop and extracted it... Hmm...

---

### Post by Miki01 on 2006-07-05
Okay, thanks to Kilz, the bittornado thing is reading out in English again... But apparently. The CD reading is having some problems... Remember, all was good before I used EasyUbuntu. This is an update screenie of how the CD looks. In my WinXP PC, it looks fine, opens fine, and I can copy files from the CD to my desktop fine. If I recall, doesn't Automatix install something about CD Eject? How do I go about uninstalling that?

And what about EastUbuntu? It started happening after I used EasyUbuntu, so is there something there I would need to know? Since I used EasyUbuntu, I've had these errors, and that after that I can't even play DVDs in Totem anymore? EasyUbuntu may have fiddled with my codecs or libdvdcss?

And still. that blasted I/O Error... I'm running out of CD-RWs to back up my stuff... If the error wasn't there, I could reuse the CDs, but I can't because they're not backed up yet...

See attached images

---

### Post by Kilz on 2006-07-05
[QUOTE=Miki01]Okay, thanks to Kilz, the bittornado thing is reading out in English again... But apparently. The CD reading is having some problems... Remember, all was good before I used EasyUbuntu. This is an update screenie of how the CD looks. In my WinXP PC, it looks fine, opens fine, and I can copy files from the CD to my desktop fine. If I recall, doesn't Automatix install something about CD Eject? How do I go about uninstalling that?

And what about EastUbuntu? It started happening after I used EasyUbuntu, so is there something there I would need to know? Since I used EasyUbuntu, I've had these errors, and that after that I can't even play DVDs in Totem anymore? EasyUbuntu may have fiddled with my codecs or libdvdcss?

And still. that blasted I/O Error... I'm running out of CD-RWs to back up my stuff... If the error wasn't there, I could reuse the CDs, but I can't because they're not backed up yet...

See attached images[/QUOTE]
I was looking at the automatrix page and it says it installs microsoft tt fonts. I wonder if that could be why everything is unreadable on your cd's. Its worth a shot, you can always add them back if they are not at fault. Also [here is a page with the codes]("http://ubuntuforums.org/showthread.php?t=90797") for removing some of what automatrix installs.

```
sudo apt-get remove msttcorefonts
```
If you want to readd its only 
```
sudo apt-get install msttcorefonts
```

---

### Post by Miki01 on 2006-07-05
Okay, thanks. I typed that into terminal and received:

> miki@Ubuntu:~$ sudo apt-get remove msttcorefonts
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  msttcorefonts
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 168kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 107120 files and directories currently installed.)
Removing msttcorefonts ...
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.


Is what correct? Is what what it is supposed to respond with? I will do a test now to see how the CD's characters are.

EDIT: Hmm... Strange... I just inserted a CD, and it read this: (attached image)

I'm not entirely sure on the problem though. After my initial installation of Automatix, we had those problems that we had in the other thread. After we fixed them, some other ones appeared after firefox32 was installed. Now that firefox32 was fixed, multimedia errors started appearing. First with Youtube.com's video clips not having audio, then, my optical drive started making errors about libdvdcss. So I was refered to use EasyUbuntu. I used that, but no avail. Totem still reads that its missing plugins to play the DVDs. As well, after using EasyUbuntu, the problems in this thread appeared. I may be guessing that the problems may have something to do with EasyUbuntu... But I'm not sure, I'm only an amateur with linux, today is only day four...

---

### Post by Kilz on 2006-07-06
[QUOTE=Miki01]Okay, thanks. I typed that into terminal and received:



Is what correct? Is what what it is supposed to respond with? I will do a test now to see how the CD's characters are.

EDIT: Hmm... Strange... I just inserted a CD, and it read this: (attached image)

I'm not entirely sure on the problem though. After my initial installation of Automatix, we had those problems that we had in the other thread. After we fixed them, some other ones appeared after firefox32 was installed. Now that firefox32 was fixed, multimedia errors started appearing. First with Youtube.com's video clips not having audio, then, my optical drive started making errors about libdvdcss. So I was refered to use EasyUbuntu. I used that, but no avail. Totem still reads that its missing plugins to play the DVDs. As well, after using EasyUbuntu, the problems in this thread appeared. I may be guessing that the problems may have something to do with EasyUbuntu... But I'm not sure, I'm only an amateur with linux, today is only day four...[/QUOTE]

I think that the install is fubar because of the use of the auto install scripts. We have been going round and round and getting noplace. It may be easier to reinstall, and put what you need in one piece at a time.

---

### Post by Miki01 on 2006-07-06
Ah, well... I'll just post up a similar topic in Linux Forums and see if anyone else can figure out what's going on...

---

