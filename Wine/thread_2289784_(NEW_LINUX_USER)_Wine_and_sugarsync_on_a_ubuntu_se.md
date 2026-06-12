---
title: "(NEW LINUX USER) Wine and sugarsync on a ubuntu server... working, but..."
date: 2015-08-06
forum: Wine
---

### Post by Art_Port on 2015-08-06
Hi;

im very very very new with linux enviroment, but i manage to install a server, including SAMBA for windows user to access some folders, MySQL database and some other things...

i use Sugarsync for cloud folder syncronization on Windows enviroment, and a friend of mine tell me how to install Wine on my server to install/run windows applications, Sugarsync seams to work normally but when i tried to ADD local folders for backup, there is none on sugarsync screen.... it seems sugarsync does not "see" all the folders on my drive

any advice to solve this?

---

### Post by Simon_Tomoko on 2015-08-13
I am not familiar with this SugarSync and have little understanding of MySQL data base.  I do know that by default most WINE programs see the Linux root as a Z:\ drive.  If I was looking for a data folder located in Linux;

/media/Drive C/Graphics/test/mydata.db

The Windows path in WINE would be;

Z:\media\Drive C\Graphics\test\mydata.db

For files stored in the WINE virtual C:\ it would be;

Z:\home\(your user ID)\.wine\drive_c\

Personally to me, this seems very convoluted, in the sense that; MySQL database programs and servers can be installed on Linux much easier than rerouting it through WINE.

---

