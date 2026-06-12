---
title: "Downloading chrome from chromesetup.exe"
date: 2008-11-04
forum: Wine
---

### Post by sea_monkey987 on 2008-11-04
Ok.  you know how all the tutorials say the online installer doesn't work?  you have to get the offline installer.  well, on my wine installer, the online installer does work.  it downloads the chrome and installs it.  trouble is, i have no idea how i got it to be this way!  if i changed the WINEPREFIX variable and run the chromesetup.exe from a new "C:", the installer fails to download like the websites say.  i've tried installing gecko from winetricks: it doesn't seem to help.

So, how do I get the chromesetup.exe to download chrome on a fresh wine install?  i ask this because i want the built-in update functionality to work on my CIV IV game when I install the game on another box which doesn't yet have wine on it.  (the built-in update function didn't work in CIV IV until chromesetup.exe started successfully downloading Chrome from google's servers)

---

### Post by sea_monkey987 on 2008-11-06
bump

---

### Post by lifestream on 2008-11-06
Mmmm you don't want to use [Chromium]("http://www.codeweavers.com/services/ports/chromium/") .deb? You just double click and it automagically installs

---

### Post by sea_monkey987 on 2008-11-07
thanks for the reply lifestream.  i'm aware of the chromium package but my main goal is not installing chrome.  i want wine programs to be able to access the internet in the background (what i mean by this is programs that access locations without opening a browser such as iexplore.exe into the foreground).

---

