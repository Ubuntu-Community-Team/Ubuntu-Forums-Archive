---
title: "Hoopladigital.com using wine"
date: 2013-12-27
forum: Wine
---

### Post by windphere on 2013-12-27
**Start using hoopla digital today to begin borrowing free digital video, music and audiobooks with your library card.**

Follow the directions on [http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html](http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html)

Next go to Menu and open "Netflix Desktop"  This will do some installations.

--

Now install "Wine" through the Software Manager or Package Manager. 

From Menu open "Configure Wine" and close

Open  file manager - press Ctrl H,  (Press F3 for double screen) and copy  .wine-browser and paste to .wine  (merge, replace) - Then copy .wine and  paste to .wine-browser (we do this to get "Wine Windows Program  Loader")

---

Now download Flashplayer [http://download.macromedia.com/pub/flashplayer/installers/archive/fp_11.9.900.170_archive.zip](http://download.macromedia.com/pub/flashplayer/installers/archive/fp_11.9.900.170_archive.zip)

open  File Manger go to Downloads and move file    "fp_11.9.900.170_archive.zip"    to   /.wine-browser/drive_c/Program  Files/  - right click and click "Extract Here" - go to extracted file  and open  "flashplayer11_9r900_170_win.exe" with "Wine Windows Program  Loader"  (best to open with "Other Application" and choose "Wine Windows  Program Loader"  This will allow all wine programs to open  automatically from now on.

----

from the file manager go  to home/.wine-browser/drive_c/Program Files/Mozilla Firefox/firefox.exe -  right click - Open With - Wine Windows Program Loader
 (Ctrl h for hidden files )

with Firefox open go to  download.  Close Firefox.

----

Open Firefox from /home (this is the name of your computer)  /beast/.wine-browser/drive_c/Program Files/Mozilla Firefox.

Goto [http://hoopladigital.com](http://hoopladigital.com)  Sign in

find something you want to watch.

Press Play

Install  Plugin - Widevine  * Press "Allow" top left * then press "Install" *  Then press Restart or close and reopen your browser - (if it says  install Flash you need to do the above first).  Restart browser.

To check what is installed go to "Tools - Ad-ons - Plugins

Shockwave Flash (for Hoopla)
Silverlight Plug-In (for netflix)
Widevine Media Optimizer (for Hoopla)

---

### Post by mlnease on 2014-09-11
Bravo (or 'Brava' as the case may be)!  *Brilliant*!  Thank you.

---

### Post by hackerb92 on 2014-11-17
Thanks for the tip! It looks like in the year since the above answer was posted, it has become *much* easier to get hoopla working. Just install [pipelight]("http://pipelight.net/cms/installation.html") and then run

```
sudo pipelight-plugin --enable widevine
```

Voila, free movies streaming from your local public library! (I'm watching the silent masterpiece **CALL OF CTHULHU** as I type this and it's working great.)

---

### Post by mlnease on 2014-11-17
> **hackerb92 said:**
> Thanks for the tip! It looks like in the year since the above answer was posted, it has become *much* easier to get hoopla working. Just install [pipelight]("http://pipelight.net/cms/installation.html") and then run

```
sudo pipelight-plugin --enable widevine
```

Voila, free movies streaming from your local public library! (I'm watching the silent masterpiece **CALL OF CTHULHU** as I type this and it's working great.)
Thanks for this.  I followed the pipelight instructions above, successfully I think.  Unfortunately, Hoopla required installation of Adobe Flash--I complied but Hoopla still displays the 'missing plugin' (Adobe Flash) error message and won't play.  Reviewing the comments in Ubuntu Software Center, this appears to be a common problem.

Thanks again for your time just the same.

---

### Post by NoBugs! on 2015-11-06
I like Firefox too, but is all that work worth it when it works with no extra setup in Chrome/Chromium browser?

---

### Post by mlnease on 2015-11-09
> **NoBugs! said:**
> I like Firefox too, but is all that work worth it when it works with no extra setup in Chrome/Chromium browser? A fair question.       If I knew how to 'sandbox' Chrome, I might try it; but I don't trust Google enough to use their search engine without TOR (or Ixquick proxy), much less trust my OS and files to their browser--call me paranoid.         Thanks for your time and attention.

---

