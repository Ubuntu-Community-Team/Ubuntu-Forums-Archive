---
title: "Wine Gecko Installer"
date: 2008-05-10
forum: Wine
---

### Post by reyhan on 2008-05-10
Hello i just installed Counter Strike 1.6 and when i want to play it Why do i have To install Wine Gecko? and how do i install it ?

---

### Post by cogadh on 2008-05-10
Gecko is required for HTML rendering. To install, just open a terminal and type:
```
wine iexplore http://www.winehq.org
```
Follow the prompts and it will install itself. You will know the install is complete and successful when the WineHQ website is displayed.

---

### Post by reyhan on 2008-05-10
And why Wine Needs gecko?

---

### Post by cogadh on 2008-05-10
As I said, it is required for HTML rendering. Wine doesn't have an HTML rendering engine built in, so it needs the standard Gecko engine installed.

---

### Post by reyhan on 2008-05-10
i already follow the prompt but the 
WineHQ website is not being displayed

---

### Post by cogadh on 2008-05-10
Did Gecko actually download (there should have been a progress bar)? If it didn't or it did but didn't install for some reason, then you can either try the automatic method again, or do this:

[list=1]
[*]Open a terminal and manually download/extract the Gecko package by running the following:
NOTE - You will need to install the cabextract package from the repositories to do this
```
wget http://downloads.sourceforge.net/wine/wine_gecko-0.1.0.cab && cabextract wine_gecko-0.1.0.cab
```
[*]Next, run the following to create the directories needed for Gecko:
```
mkdir -p ~/.wine/drive_c/windows/gecko/0.1.0/
```
[*]Place the extracted Gecko files into the newly created directory:
```
mv wine_gecko ~/.wine/drive_c/windows/gecko/0.1.0/
```
[*]Run regedit in the terminal. Go to HKEY_CURRENT_USER/Software/Wine/MSHTML and create a new key labelled "0.1.0"
[*]In the new "0.1.0" key, create a new string value labelled "GeckoPath" and set the string value to "c:\windows\gecko\0.1.0\wine_gecko"
[/list]
That's it, Gecko should be installed now.

---

### Post by reyhan on 2008-05-11
Ok....
now i am confused i already follow your instruction but
still same??????:confused::confused::confused::(:(:(

---

### Post by reyhan on 2008-05-11
this is the screenshots on the registry
is it correct?

---

### Post by svn7svn on 2012-08-12
> **reyhan said:**
> this is the screenshots on the registry
is it correct?

mine looks the same now.  is there a command you can run in the terminal to see if it's done properly, or some other way to confirm?

---

### Post by overdrank on 2012-08-12
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

