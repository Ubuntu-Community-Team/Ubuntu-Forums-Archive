---
title: "Running Steam with WINE"
date: 2007-11-30
forum: Wine
---

### Post by ShinodaTheory on 2007-11-30
Hello all!

Let me start off by saying this is really complex for me, I am trying to install Steam through WINE and its not looking good right now. I just installed WINE 9.50, and I have even checked the ADB for a solution and I just can;t get it to work. :( Any Suggestions?

Thanks!

---

### Post by cogadh on 2007-11-30
Since the 'buntu package for 0.9.50 isn't available yet, I assume you compiled it yourself? Did the compile encounter any errors or problems?

When you installed Steam, did you follow any "how-to" guides like this one:
[http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

---

### Post by ShinodaTheory on 2007-11-30
> **cogadh said:**
> Since the 'buntu package for 0.9.50 isn't available yet, I assume you compiled it yourself? Did the compile encounter any errors or problems?

When you installed Steam, did you follow any "how-to" guides like this one:
[http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

I get to the point were I have to run the "wine start SteamInstall.msi" command line, after that I get an error reporting this:

"fixme:exec:SHELL_execute flags ignored: 0x00000500
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: File not found"

What now?,lol

---

### Post by cogadh on 2007-11-30
Usually, that error occurs if you haven't changed directories to the location of the Steam installer before running the command. If you did already CD to that directory, then try running it like this:
```
wine msiexec /i SteamInstall.msi
```

---

### Post by ShinodaTheory on 2007-11-30
> **cogadh said:**
> Usually, that error occurs if you haven't changed directories to the location of the Steam installer before running the command. If you did already CD to that directory, then try running it like this:
```
wine msiexec /i SteamInstall.msi
```

Hmm, forgive me for asking this, but... How do I change the Directories for SteamInstall.msi? I didn't see anything in the How-to on changing it.

---

### Post by cogadh on 2007-11-30
In the terminal, just "cd" to the directory you downloaded it to. For example, if you downloaded it to the desktop:
```
cd Desktop/
wine start SteamInstall.msi
```

---

### Post by AlexFoster on 2007-12-26
Well, poop, that didn't work for me. My problem is when I do the "wine start SteamInstall.msi" nothing happens. I tried cd Desktop to no avail.

---

### Post by Royall on 2007-12-26
First, you need to install a web browser in Wine, which is trivially simple.
step 1:
```
wine iexplore
```

Then, just install Steam.
step 2:
```
msiexec steamInstall.msi
```

After these two steps, I'm pretty sure Steam worked exactly as it did in Windows for me.

---

### Post by AlexFoster on 2007-12-26
Well, apparently I didn't install the new wine properly. After I wrestle that into place I'll be back...

---

### Post by jacob21 on 2007-12-26
Thank you cogadh, I just installed Ubuntu yesterday and couldn't get steam to install.  Working fine now.

---

### Post by AlexFoster on 2008-01-04
Okay, so I've tried to search for the error message I've been getting when I try to install wine, but I'm having no luck, please point me in the correct direction for a way to resolve this. I try to install the new wine in a terminal and get this:

Depends: libasound2 (> 1.0.14) but 1.0.13-1ubuntu5 is to be installed
Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
Depends: libgphoto2-2 (>= 2.4.0) but 2.3.0-0ubuntu4 is to be installed
Depends: libgphoto2-port0 (>= 2.4.0) but 2.3.0-0ubuntu4 is to be installed
Depends: libxml2 (>= 2.6.29) but 2.6.27.dfsg-1ubuntu3 is to be installed
E: Broken packages

---

### Post by ubu-for on 2008-01-05
> **ShinodaTheory said:**
> I just installed WINE 9.50, and I have even checked the ADB for a solution and I just can;t get it to work.

Try [this HOWTO](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games) and different [Wine versions](http://wine.budgetdedicated.com/archive/index.html).

---

### Post by AlexFoster on 2008-01-05
Man alive, can I be dense. Updated my wine successfully. Now on to steam...

---

