---
title: "Halo CE trying to get working with WINE"
date: 2012-06-30
forum: Wine
---

### Post by DarkBowser on 2012-06-30
I have 12.04 blah blah blah, and I am using WINE to try to install Halo CE. I enter my product key, and it fails to open a DLL to move on to the next step. How can I make this work?

---

### Post by Quackers on 2012-07-02
*Thread moved to **Wine**.*

---

### Post by thatguruguy on 2012-07-02
Did you read the suggestions [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720&iTestingId=63330")?

---

### Post by Lyfang on 2012-07-02
Run the installer from the Terminal & post error message. Use winetricks for installing missing components. Try PlayOnLinux.

---

### Post by DarkBowser on 2012-07-02
How do I run the CD .exe from the terminal?

---

### Post by Lyfang on 2012-07-03
> **DarkBowser said:**
> How do I run the CD .exe from the terminal?
Open Terminal, use cd & ls [http://www.math.utah.edu/lab/unix/unix-commands.html#cd](http://www.math.utah.edu/lab/unix/unix-commands.html#cd)
```
wine FILENAME.exe
```If you have hard time finding the location: browse to the folder of the game with your file manager, right-click the  .exe file and select file properties. Then you find the file  location/path of the .exe.

---

### Post by thatguruguy on 2012-07-03
> **DarkBowser said:**
> How do I run the CD .exe from the terminal?

Just because I'm curious, I'll ask again. Did you follow the directions given on the WineHQ page relating to Halo, which is [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720&iTestingId=63330")?

Since it's clear from your posts that you haven't read that page yet, why haven't you?

---

### Post by Dlambert on 2012-07-03
If you're to lazy! :) : 

```
Running full game: 
[LIST=1]
[*]Install mfc42 - for example, with winetricks:     winetricks mfc42
[*]Insert the CD, or mount the ISO:     mount -oloop Halo.iso /cdrom
[*]Launch the setup:     ./Setup.Exe
[*]Run the updater to patch Halo, which now includes no-cd:     ~/.wine/drive_c/Program\ Files/Microsoft\ Games/Halo/haloupdate.exe
[*]Run the game. The working directory must be the Halo directory.     cd .wine/drive_c/Program\ Files/Microsoft\ Games/Halo ./halo.exe
[/LIST]

```

---

### Post by DarkBowser on 2012-07-04
@Dlambert: Thank you for your very simple guide. You have my best answer.

EDIT: I run setup and it goes to 40% and a cab3.cab  fails to extract, low memory or swap.

---

### Post by Dlambert on 2012-07-04
Try burning the CD to an iso and run off your PC

---

