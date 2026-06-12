---
title: "Guide to running NWN2 in WINE"
date: 2008-10-23
forum: Wine
---

### Post by dayosh on 2008-10-23
***DISCLAIMER***
The author feels it important to impress upon the reader that this guide is not foolproof, nor will it guarantee complete success.  _There will be many bugs and glitches to work out_, but the author wishes to express that while this guide is not a complete victory, it is still a significant foothold to build upon.  In short, the success of this guide is reliant upon the readers, to experiment and tweak, in order to sooner find out what works and what does not.  In short, think of this guide as a starting nudge in the right direction.  The rest will come gradually with time and experimentation.
----------------------------------

This guide will show you how to install Neverwinter Nights 2 (and play such) in Wine.  After some lengthy experimentation, I have found that it does play somewhat.  However, I believe that a warning is necessary:  The game (as it runs on my own computer) is nothing like its native Windoze counterpart.  It is quite laggy (some environments on my system can take minutes to load, and then the background is still rather patchy).


**Contents:**
1. Installing WINE
2. Installing Mono 2.0
3. Installing Wine tricks
4. Installing DirectX 9 into WINE
5. Installing NWN2
6. Configuring Settings/Troubleshooting



1. _Installing WINE_

For those who don't already have this program, it can be installed via your package manager, or by entering the following terminal command:

```
sudo apt-get install wine
```

The program should install automatically, allowing us to continue on to step 2.
-----------------------------


2. _Installing Mono 2.0_

Mono 2.0 is an “open source, UNIX version of the Microsoft .NET development platform.”  It can be found and [[COLOR="Red"]downloaded here[/COLOR]]("http://www.go-mono.com/mono-downloads/download.html").

When downloading **be sure to download the version for Windows**!  We are going to be incorporating this into WINE, so do not download the Linux version.

Once the download has finished, open the file (should be something like “mono-2.0-gtksharp-2.10.4-win32-5.exe”).  Follow the on-screen installation instructions, and that should be the end of that.  Easy peasy.
---------------------------------


3. _Installing Wine Tricks_

Wine Tricks is little more than a program containing a bunch of pre-coded tasks that are generally used with WINE.  Its purpose is to (generally) make your life easier by taking many tasks and reducing them to a single click.

To install Wine Tricks, simply entering the following into a terminal command line:

```
wget http://www.kegel.com/wine/winetricks
```

This will download and install the program, simple as that, allowing us to move onto the next step.
---------------------------------


4. _Installing DirectX 9 into WINE_

In a command terminal, type:

```
sh winetricks
```

This will bring up the following Wine Tricks window.  Be sure to check the “directx9” box, as in the screenshot below:

[IMG]http://img.photobucket.com/albums/v134/dayosh/Screenie1.png[/IMG]

Once you do this, the program will automatically download (and install) DirectX 9 into Wine.  Give it a few minutes as it does its thing, and then the Direct X 9 installation wizard will pop up.  Just follow the on-screen instructions, and then “Finish” after the installation completes.

If you open a terminal and type:

```
winecfg
```

This should bring up the WINE configuration window.  If you click on the “Libraries” tab, you will see that Wine Tricks even added all of the necessary .dll files into the program's cache for you (technology is nifty like that).  You should now have DirectX9 installed, and should be ready to install NWN2.
-----------------------------


5. _Installing NWN2_

I think for the most part, this should be fairly self-explanatory.  Insert DVD.  Follow instructions.  Done.
---------------------------------------------


6. _Configuring Settings/Troubleshooting_

As stated previously, this guide is not foolproof.  There will be glitches and errors (and it will be pretty “lag-a-docious” in general).  A good general tip is to set all graphics capabilities to their lowest possible settings, and as you progress, try enabling /disabling option by option until you achieve a setup that is a happy medium.  Below are some typical problems (and solutions) I ran into when running the program.

_FAQ:_

**Problem:** My mouse seems to register as being slightly lower /higher than it actually is (I have to be below /above a button in order to click it).

**Solution:** In the Options, under the “General” tab, try unchecking the “Full Screen” option.  This did the trick for me, and even corrected this issue later on whenever I went back into full screen mode, again.


**Problem:**  In the opening cinematic (and even afterwards) the screen is entirely black.  I can't see a thing!

**Solution:**  Press “ESC” to bring up the Options menu.  Go to the “General” tab, and under “Shadow Options,” select “Off”, and this should fix that problem.


**Problem:**  There aren't any shadows, but when I mouse over a character or an object (a chest) much of the screen goes black.

**Solution:**  Enter the Options, and in the “General” tab, uncheck “Cursor Highlighting.”  This should fix the issue.
------------------------------------------------------

Again, the _gameplay is going to be very rough at best_, but as stated previously, it is a foothold which (hopefully) will lead to a much greater victory, given enough support and interest.  Good luck, and thanks for reading!   :)

---

