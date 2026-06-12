---
title: "Bit Che"
date: 2008-03-12
forum: Wine
---

### Post by newfy78 on 2008-03-12
I installed Bit Che using wine.  Everything works fine except when I do a search I can't see any results.

I can see Bit Che searching the torrent sites and it says there are results, but I can't see them.

I'm assuming this is simply because wine doesn't have the font(s) that I need.

I tried to find out what font Bit Che uses to no avail.

Can anyone help?

P.S.  the Bit Che menus are displayed and work fine.  It is only the results that I can't see.

---

### Post by newfy78 on 2008-03-14
bump.....

Anyone?

---

### Post by newfy78 on 2008-03-18
bump.

last attempt.  I have a funny feeling I'm not going to get the answer.

---

### Post by chip! on 2008-04-07
hello,

i'm the developer of bit che and i recently got Ubuntu 7.10 setup to test Bit Che..

using the latest release of WINE, Bit Che does run and search..

i am brand new to ubuntu, but i noticed that launching the .torrents after downloading them with Bit Che was not automatic into the default torrent handler for ubuntu. after some playing around, i was able to get it working. now you can open torrents directly with Bit Che and have them open in either Ubuntu's default torrent downloader (or you can specify if you want to use uTorrent to download torrents).

Attached you will find 3 files that will let you either launch .torrents into your systems default or uTorrent (in Wine).


**For the default system torrent downloader:**

1. you need to modify the Wine registry to point to a special script to handle launching the torrent.
import the registry file "Default_System.reg" into your WINE registry to setup the .torrent handling in the registry. 

2. Then extract the "torrent_open.script" to your "C:\Program Files\Bit Che\" virtual path in WINE.

3. Now when you 'Open Torrents' in Bit Che, they will be handled by the script which launches gnome-btdownload  (by default on Ubuntu 7.10).


**For using uTorrent in Wine:**

1. Import the "uTorrent_Wine.reg" into your WINE registry.

2. Now "C:\Program files\uTorrent\uTorrent.exe" will be used to handle the opening of .torrents in WINE.



The other issue is that the ListView font is pretty small but I am updating Bit Che to allow this to be changed.

If anyone else wants to chime and help me get Bit Che running smooth on Ubuntu, please do! 

thanks,
chip
convivea.com

---

### Post by maxter on 2008-04-30
hi chip, and thanks for your work :)
first of all a request :) 
it should be nice to have a native linux bit che implementation
it should not be so difficult with mono, using visual basic as programming language so i hope you will consider this possibility :)

anyway, i'm posting here to suggest to linux bit che users to install tahoma font in wine fonts directory, untill chip will update bit che.
the font will be ever small, but at least readeable. 
with 1280*1024 resolution, without 
tahoma it is impossibile to read any text without a magnifier :)

furthermore, in hardy, the default torrent manager is not more gnome-btdownload, so the the torrent_open.script should be modified substituting gnome-btdownload with transmission (the new default torrent downloader), or obviously with you preferred software (azureus etc. etc.)

thanx again to chip and....
HASTA LA VICTORIA SIEMPRE!!! :)

---

### Post by Jawbraeka on 2008-08-23
are you working on an ubuntu 8.04 hardy heron for deluge fix as well as this is a great revolutionary search engine for torrents and can you please fix the font as well as mentioned earlier and its quite true that the font is quite hard to read or jsut release a linux port as it seems to do everything is should in linux.

---

### Post by saintryan on 2008-10-22
Hey chip! great program.

Please tell us your going to be working on a version for ubuntu. (without having to use wine)
That would be awsome.

---

### Post by chafic2783 on 2009-01-22
has anyone been able to get the "open torrent option" and/or the "open source page" option to work in linux (kubuntu/ubuntu).  i've tried to modify the torrent_open.script and replaced "gnome-btdownload" with "ktorrent" but this does not seem to work.

also, i have no idea how to make the internet browser launch to the torrent's source page.

any help would be greatly appreciated.

regards,
chafic

---

### Post by faazil on 2009-10-19
thanks for advice on the font worked like a charm.

---

### Post by Rubicon421 on 2010-08-06
Anyone know how to set Deluge to be the default torrent client in that script instead of utorrent? I have Bit Che working but when I click open torrent I get nothing. I have to download and save the torrent first. Then if I double click it Deluge opens because the torrent is in the linux file system. It won't work from the wine C:\ temp location and cross over from wine to Deluge though. It has to be saved somewhere first then opened.

---

### Post by tOtOrooo on 2010-10-19
Thanks Chip for sharing the setup files with us.

---

