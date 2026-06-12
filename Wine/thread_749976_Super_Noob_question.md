---
title: "Super Noob question"
date: 2008-04-09
forum: Wine
---

### Post by Distortedgamer on 2008-04-09
Alright, this sounds like a super noob question, but I just don't know the GUI very well, or could be blind.

I just installed WINE through apt-get and I can't seem to find where to start it. I have checked through all of the folders under APPLICATIONS, but its not there. Anyone have any ideas on where it is or how to start it? 

Thanks

I will try a reboot now.

---

### Post by tamoneya on 2008-04-09
if you have an exe file say ```
wine /some/directory/windowsprogram.exe
```

---

### Post by Seti on 2008-04-09
to clarify you can start an exe with wine on the command-line, by opening a terminal and doing ```
wine yourexe.exe
```

You can also hit [ALT][F2] and a prompt will come up.

```
wine yourexe.exe
``` should also work there.

---

### Post by Distortedgamer on 2008-04-09
OK Thanks, I see how that works.

Is there a way to do a virtual desktop environment? I am trying to run DreamWeaver and possibly some games, how do I 'install them'?

And thank you very much for the quick response!

---

### Post by warp99 on 2008-04-09
You should be able to right click on a .exe file and an option for "open with wine" should be available. You can also run wine from the command line:

```
wine foo.exe
```

Just make sure you're in the same directory as the .exe file. In Gnome I believe wine is in the administration folder.

And this:

> will try a reboot now. 

Don't waste your time with reboots, this isn't Windows. With Linux you only need to reboot for a kernel update or the restricted modules installation or the once in a while system lockup and even with that you would press alt+printscreen+'b' to reboot the kernel.

If you want to reload the desktop just press ctrl+alt+backspace.

Edit:

To install the Windows apps just run the setup file:

```
wine D:\EXPENSIVE_BUGGY_SOFTWARE\setup.exe
```

---

### Post by Distortedgamer on 2008-04-09
> **warp99 said:**
> 

```
wine D:\EXPENSIVE_BUGGY_SOFTWARE\setup.exe
```

hahahaha great example. 

Any suggestions for webpage creating software? I know basic html and basic php, but not anywhere near what I need for the site that I want. I heard that Dream Weaver writes the code for you.

---

### Post by schtufbox on 2008-04-09
What do you need the software to be doing? What sort of website are you making.
NVU, while lacking many advanced features is a nice little WYSIWYG web editor.  It's free too.

---

### Post by warp99 on 2008-04-09
> **Distortedgamer said:**
> hahahaha great example. 

Any suggestions for webpage creating software? I know basic html and basic php, but not anywhere near what I need for the site that I want. I heard that Dream Weaver writes the code for you.

I'm not a html/php script writer, but here is a list of alternative apps for Dreamweaver:

Quanta Plus ( [http://quanta.kdewebdev.org/](http://quanta.kdewebdev.org/) )
Geany ( [http://geany.uvena.de](http://geany.uvena.de) )
Nvu ( [http://www.nvu.com/index.php](http://www.nvu.com/index.php) )
Screem ( [http://www.screem.org/](http://www.screem.org/) )
KompoZer ( [http://www.kompozer.net/](http://www.kompozer.net/) )
Bluefish ( [http://bluefish.openoffice.nl/index.html](http://bluefish.openoffice.nl/index.html) )

Courtesy of the Linux Alternative Project [http://www.linuxalt.com/](http://www.linuxalt.com/)

Most if not all of these are available in the Ubuntu repositories. I would check in the programming forum to see what others are using.

---

### Post by tamoneya on 2008-04-09
I like gedit but maybe thats just me.

---

### Post by Distortedgamer on 2008-04-09
I am making a myspace-type site but specifically for my family. Everyone can post pics and everyone else can leave comments on those pics. 

Thanks for all of the Dream Weaver alternatives, I will check those out too.

Thanks.

---

