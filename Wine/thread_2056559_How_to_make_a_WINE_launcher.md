---
title: "How to make a WINE launcher?"
date: 2012-09-11
forum: Wine
---

### Post by pgrytdal on 2012-09-11
Hello!

I was wondering... I have a game called Stronghold installed on my Windows side of my computer.

I was wondering if there was a way I could create a launcher on my desktop, that would trigger Stronghold to launch through Wine... at least until I can borrow the install disk from my friend.

Is this possible?

Thanks!

---

### Post by cortman on 2012-09-11
[This thread]("http://askubuntu.com/questions/137151/how-does-one-create-a-custom-application-launcher-for-wine-installed-apps") should help.

---

### Post by pgrytdal on 2012-09-11
> **cortman said:**
> [This thread]("http://askubuntu.com/questions/137151/how-does-one-create-a-custom-application-launcher-for-wine-installed-apps") should help.

Am I supposed to replace "Foobar" with the application name and .exe file?

---

### Post by cwwilson721 on 2012-09-11
Your "install" creates a few issues:
[LIST]
[*]The original, being on a NTFS drive, will run HORRIBLE. Best if you copy the game files from the Windows side to a folder on the Linux side
[*]Does your game even work under wine? Check the winedb to be sure.
[/LIST]

Example: Copy the Stronghold files to your home folder in a folder you name "stronghold"
Create a wineprefix for your stronghold install:
```
env WINEPREFIX=/home/<USERNAME>/wine-stronghold winecfg
```
The above creates a "bottle" of a default wine install in the folder "wine-stronghold" in your home directory.

While the winecfg gui is up, check that the correct OS version (WinXP, Win7, whatever) is selected. While there, I always (but this part is up to you) remove the "drive" that points to "/". I don't want ANY Windows program having "accidental" access to my entire HDD

Go ahead and close winecfg. Go to your home folder, right click on the "Stronghold" folder you copied the Windows files to, and select "Make Link". Copy this link to wine-stronghold/drive_c/Program Files (Or Program Files (x64) or wherever you want to run it from, and rename it to "Stronghold" (This makes it easier to add files or whatever to the actual "Stronghold" folder without having to drill through the wine folder. Also, if Stronghold on the Windows side ever changes, it's VERY easy to recopy to your Stronghold folder in your Home directory.)

Let us say you want to launch "Start.exe" from within this folder. Open a terminal, and type the following:

```
env WINEPREFIX=/home/<USERNAME>/wine-stronghold wine "C:\Program Files\Stronghold\Start.exe"
``` 
The above will launch the file "Start.exe" in wine.
Note the CAPITALIZATION. There IS a difference between "start.exe" and "Start.exe"

If this launches the program correctly, then you can edit a launcher to run this same command in the "Command" slot.

Of course, this assumes that Stronghold doesn't need any additional tweaks. If you need to run winetricks to install vbrun, for example, use:
```
env WINEPREFIX=/home/<USERNAME>/wine-stronghold winetricks
``` This will allow winetricks to run in your wine-stronghold install, instead of the default .wine folder

---

