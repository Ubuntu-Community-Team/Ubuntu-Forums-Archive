---
title: "Wine install to 12.04 wants to remove Google-Earth and some..."
date: 2012-05-04
forum: Wine
---

### Post by sdd on 2012-05-04
Does anyone know why, when I try to install Wine, I get the following:
To be removed:
  alien
  debhelper
  gettext
  google-earth-stable
  intltool-debian
  lsb-core
  po-debconf

I have just installed 12.04, and spent some time installing Google Earth, Sun Java 1.7, Netbeans 7. 

Please can anyone tell me why wine has an issue with these...

Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-24-generic
GNOME 3.4.1
Wine 1.4-0ubuntu4

Thanks
SDD

---

### Post by cogadh on 2012-05-04
Wine shouldn't be doing that, it's probably the 12.04 upgrade doing it (those look like some leftover post-upgrade removals). The Google Earth one is a little odd; did you install it via a repo or did you download and manually install from a .deb file?

---

### Post by sdd on 2012-05-05
No I downloaded  Google Earth, could not get it via the repos.

It is not GE I am worried about, I can re-install. It is the other stuff. I don't know what most of it is.

I had some issued installing 12.04 so  I think my local app db may by corrupt. Is there a db rebuild option?

Should  I just go for it?

Stuart.

---

### Post by oZiRiz on 2012-05-06
I have the same problem and my 12.04 is a fresh install.

I've tried to find out what causes the removal and I think it has something to do with gettext, but I'm not sure. And I have no idea how to fix it...but maybe someone else can help.

I think it's a dependency-bug...

greets
felix

---

### Post by BigSilly on 2012-05-08
Just discovered this one for myself too. Woops then. I'll try it directly from the WINE repo and see how I go.

---

### Post by sdd on 2012-05-09
So if it is not just me, how do we get it raised up the issues list for some one to look at. I use wine lots and need it to work.....

Or is that not how it works.

---

### Post by thatguruguy on 2012-05-09
I believe it has to do with a problem concerning ia32libs.

It appears that you can go ahead and safely install Wine, and then re-install the packages it has removed as necessary.

---

### Post by sdd on 2012-05-09
OK so I bit the bullet.

1) Uninstalled google-earth (see the web site for instructions)
2) add wine ppa via synaptic (ppa:ubuntu-wine/ppa) for latest wine.
3) installed playonlinux
4) installed Q4Wine. Seems like a nice app.
    Note wine libs at /usr/lib/x86_64-linux-gnu/wine
    There are also 32 bit wine libs at /usr/lib/i386-linux-gnu/wine.
    No Idea which I should use so went for the 64 bit one.

Tried to install google-earth. Failed without lsb-core.
Tried to install lsb-core using synaptic. Synaptic told me I had broken packages! So I used synaptic Edit-->Fix Broken Packages..

This re-installed ALL of the packages uninstalled when I installed wine, it even tried to re-install google-earth but I ignored it and went to the command line and installed it again.

This all seems to have worked..

I will update this thread if I find further issues.

Thanks for all your comments and help

Stuart

---

### Post by ndstate on 2012-05-09
I am having the same issue.  Is this a bug?

---

### Post by sdd on 2012-05-15
Wine is broken from this process. I can not install anything that uses 3D graphics...

I have tried 4 titles so far. None even try to run...

Think I might go back to (11.10) for a while.

This is very disapointing!

---

### Post by coleix on 2012-06-11
Wow, great that I did the search, it seemed like it wanted to uninstall too much stuff that I didn't know what it was, I tried to see if it asked the same for the 1.5 beta and I think it actually asks for more to be unistalled.
Thanks for the heads up, too bad though.

---

### Post by kilha on 2012-07-29
Same problem here. Any news on that issue?

---

### Post by opensshd on 2012-09-22
Workaround - amd64 12.04 - stock repos:

	
```
sudo apt-cache policy wine
```

this returns 1.4.0 for me.

```
sudo apt-get build-dep wine
```

Downloaded the source code for it here:

[http://sourceforge.net/projects/wine/files/Source/wine-1.4.tar.bz2/download](http://sourceforge.net/projects/wine/files/Source/wine-1.4.tar.bz2/download)

After build dep is done I:

```
./configure --without-x --without-freetype
```
```
make
```
```
sudo make install
```

Wine installs no errors.

Then as the workaround to the GUI frontend I:

```
sudo apt-get install q4wine
```


QT GUI works never asks to remove anything

Having an X issue of course, but I am able to 

sudo apt-get install --reinstall wine without removing packages... *working on it*

---

### Post by s1baker on 2012-11-14
Is this still an issue?

I want to install wine to play around with, but when I go to synaptic to do the install, I see it wants to un-install google-earth-stable.
I want google-earth at this time more than I want to play around with wine.
 Is there a work-around?

( 12.04.01 here, 64 bit )

---

### Post by Tiedemate on 2012-12-30
On 12.10 installation of Wine from the Ubuntu repos removes google-earth, but it can be reinstalled afterwards. No idea why this is happening...

---

### Post by JackAndKill on 2013-01-13
It's a bug within Synaptic !
Just install (using Synaptic) Wine.
It than removes GoogleEarth, but Wine is installed.
After installing Wine, just install GoogleEarth again.
That's all you need to do.
No dependency errors or broken links after you've done this... enjoy :popcorn:

---

### Post by Szasz on 2013-05-05
> **opensshd said:**
> Workaround - amd64 12.04 - stock repos:

    
```
sudo apt-cache policy wine
```

this returns 1.4.0 for me.

```
sudo apt-get build-dep wine
```

Downloaded the source code for it here:

[http://sourceforge.net/projects/wine/files/Source/wine-1.4.tar.bz2/download](http://sourceforge.net/projects/wine/files/Source/wine-1.4.tar.bz2/download)

After build dep is done I:

```
./configure --without-x --without-freetype
```
```
make
```
```
sudo make install
```

Wine installs no errors.

Then as the workaround to the GUI frontend I:

```
sudo apt-get install q4wine
```


QT GUI works never asks to remove anything

Having an X issue of course, but I am able to 

sudo apt-get install --reinstall wine without removing packages... *working on it*

I was not successful with (even) your suggestions. Everything went fine, no errors, but wine still seems to be not installed therefore I can not install q4wine.
How could I remove all the junk from the computer that has been left over during the aforementioned process?

---

