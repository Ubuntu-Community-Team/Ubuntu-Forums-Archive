---
title: "Download Directory for Rapget in Wine.."
date: 2008-04-10
forum: Wine
---

### Post by hartguy on 2008-04-10
Ok, so I've been using Feisty with Wubi for a few months, and then recently (yesterday) reinstalled with Hardy beta. I was using RapGet in Windows, and I looked online and found Wine would allow it to work in Hardy. I ran it successfully (I even got the confirmation message when the file finished downloading), and in my elation at seeing it run, I completely forgot to change the download directory. Thus, I left it on all night, with the download directory being "c:/Downloads/". 

I looked for the files today, but could not find any of them. I used "search for files" in Places, and looked for the file names. I even rebooted to Windows and did a search there, just in case. Are the files lost? Or are they taking up a huge chunk of disk space in some random hidden folder? 

Thanks very much! :D

Edit:
The reason why I'm asking and not just re-downloading the files is that I downloaded like 52 files, each being around 100MB. So if those files are still floating around my hard drive, I'd prefer to track them down. Plus, it'd take a long time to download that many files again.

---

### Post by schtufbox on 2008-04-10
they will probably be in /home/yourusernamehere/.wine/c_drive/Downloads

might be drive_c  instead of c_drive, I'm at work and can't remember offhand :)
.wine is a hidden directory, but you can usually browse to it from the gnome menu as wine creates a wine entry, and one of the submenus allows you to go right to the directory

Hope this helps :)

---

### Post by hartguy on 2008-04-10
OMG!! Thanks soooooooooooooo much!! The files were in drive_c/Downloads/!! YAY!!!! :D

---

