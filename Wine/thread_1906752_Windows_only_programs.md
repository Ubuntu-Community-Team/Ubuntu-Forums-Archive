---
title: "Windows only programs"
date: 2012-01-09
forum: Wine
---

### Post by Airycat on 2012-01-09
I have a few programs that are available for Windows only. There are no Linux alternatives. Right now I have Ubuntu installed in the program files of Windows and I have to choose either Windows or Ubuntu when I turn on the computer. The thing is it's a hassle to have to reboot every time I need to use one of those programs. I end up staying in Windows, which, after having used Ubuntu especially, is a real pain. Besides that, now I can't use Chrome or GIMP in Windows. I get a message that the disk is empty...weird.

Anyway, **my question**:  Is there a way to install/use windows in a different work space or something, so that I can be in Ubuntu, but access my windows programs, without rebooting, when I need them? I prefer Ubuntu, but I need those programs for what I do.

I did do a search for this, but came up with too many threads, the first of which made no sense to me (games forum).

TIA
~Faith/Airycat

---

### Post by Basher101 on 2012-01-09
try either Wine or run windows in a virtualbox

---

### Post by Airycat on 2012-01-09
Wow! That was fast!! Thank you. Can you direct me to something that will tell me what those are and how to use them?

---

### Post by imachavel on 2012-01-09
> **Basher101 said:**
> try either Wine or run windows in a virtualbox

quite a common answer. For virtualbox questions ask perryg at virtualbox.org, he is friggin awesome. for wine, download it(if it's not in the repository, then install it.) Before you try opening your program, you right click on it and select open with wine. But FIRST, right click on it, go to properties, then select 'mark as executable'

I don't know much about this stuff. But that seems like the best idea to get you started. If a windows program doesn't work in wine, look for a linux open source equivalent. There we go try it out.

---

### Post by imachavel on 2012-01-09
> **Airycat said:**
> Wow! That was fast!! Thank you. Can you direct me to something that will tell me what those are and how to use them?

[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

[https://www.virtualbox.org/](https://www.virtualbox.org/)

btw don't get confused by virtualbox, it's a lot easier to use then you think. Just don't be confused by how difficult it 'appears' to set it up. Set it up right with extensions, additions downloaded, usb filter for each device you want to configure, and proper set up for virtual ram, virtual hard disk, virtual cd rom, virtual processor, virtual video memory. It's all in settings. Your ram and processor will get EATEN up by virtual box. Give it a good shot, go create an account at those forums, and perry g will guide you

---

### Post by oldos2er on 2012-01-09
Moved to Wine.

> I did do a search for this, but came up with too many threads, the first of which made no sense to me (games forum).

Yes, the Wine forum was recently moved "under" Gaming & Leisure, because the majority of Wine questions are games related. But this (Wine) is still the correct forum for Wine questions.

There are native Linux versions of both Chrome and Gimp; for other Windows programs, check the Wine app database to see if there's a chance they'll run:  [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by grahammechanical on 2012-01-09
There is a section of this forum for wine. It is part of the Other Community Discussions>Gaming and Leisure. Here is a link:

[http://ubuntuforums.org/forumdisplay.php?f=313]("http://ubuntuforums.org/forumdisplay.php?f=313")

Running Windows games is one of the main reasons for using wine. Hence all the references to gaming. 

This is a link to the wine application database page. See, if your programs are listed and how well they work. If at all. Wine is not perfect.

[http://ubuntuforums.org/forumdisplay.php?f=313]("http://ubuntuforums.org/forumdisplay.php?f=313")

Wine is in the Ubuntu Software Centre or you follow the method found on this page:

[http://www.winehq.org/download/ubuntu]("http://www.winehq.org/download/ubuntu")

One piece of advice, if I may, when you have installed wine you can search for it in the Dash by typing wine in the search panel (11.04 and 11.10). You will see an icon for Uninstall Wine SoFtware. Click on that icon and an Add/Remove panel will open. It will have a button labelled Install. clicking on that will bring up a Windows type file open dialog and you can use that to browse to the setup.exe or install.exe file of your program.

That is one way of installing a Windows program through wine and with a bit of luck (or thanks to the hard work of the wine developers) your program will install and may put an icon on the desktop or in the Dash. Click on the program icon and the program should load or you can drag it to the Launcher so that it is available for loading.

Regards.

---

### Post by Airycat on 2012-01-09
> **oldos2er said:**
> Moved to Wine.





There are native Linux versions of both Chrome and Gimp;

Yes, I have them and they work fine in Ubuntu. It's windows that doesn't play nice.


:KS
Thank you all for your help!

---

### Post by Synoc on 2012-01-09
as far making it executable through the GUI... it seems to love to make it "world executable" which I don't like. I find it better to chmod it

```
chmod 774 program.exe
```

maybe I just don't play with the GUI enough, but everytime I try and look at the permissions via ls -l it tells me it is world executable.

---

