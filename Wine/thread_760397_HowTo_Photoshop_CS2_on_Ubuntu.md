---
title: "HowTo Photoshop CS2 on Ubuntu"
date: 2008-04-20
forum: Wine
---

### Post by abh83 on 2008-04-20
This is not my work but I decided to share this with you in the hopes to spare you long hours of frustration.

I tried almost every HowTo I could find to get Photoshop running on my ubuntu system with no luck until a few days ago when I cam across this by coincidence.

> 
[B][SIZE="3"]Install Photoshop CS2 on Your Ubuntu PC - No hacking required![/SIZE]
By: Marius Nestor, Linux Editor [/B]

Starting from last night, Photoshop CS2 can now be installed easily by using Wine... on any Linux distribution! "Photoshop CS/CS2 should
now work, please help us testing it" - said the wonderful people behind the Wine project. Therefore, I've updated my Ubuntu 7.10 operating system to the latest version of Wine (version 0.9.54 - released on January 25, 2008) and grabbed my "dusted" Photoshop CS2 (a.k.a. version 9.0) CD. I've inserted the CD in the optical drive of my computer and installed Photoshop CS2 just like I was on a Windows PC. And guess what? It really works folks! Amazing! No hacks, no need to copy installation files from a Windows PC or any other "magic" tricks you probably saw on the Internet. The Wine team did a fantastic job with this last release. Thank you guys!

So... are you eager to see this miracle on your own Ubuntu PC? No problem! Read below our step-by-step tutorial on how to install Photoshop CS2 on Ubuntu Gutsy.

[I]Things you need:

&#8226; Wine 0.9.54
&#8226; An Original Photoshop CS2 CD[/I]

Step 1: Install and configure Wine

If you don't have Wine installed, here's how to get the latest version:

1. Open a terminal (Applications -> Accessories -> Terminal) and paste the following commands (one by one - hit ENTER after each one):

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
```

```
sudo apt-get update
```

Then close the terminal window.

2. Go to Applications -> Add/Remove, make sure you select the "All available applications" option in the upper-right side of the window, search for wine and install it. When it's done, close the window.

3. Hit ALT+F2 and paste in the following command:

```
wine iexplore http://appdb.winehq.com/
```

Click 'Install' when prompted and when you'll see the "Wine Internet Explorer" window and WineHQ website, then you can close it.

4. Search on Google for the Tahoma font with the following string:

tahoma filetype:ttf

Save it on your desktop, then move it to the Wine fonts folder (full path -> /home/yourusername/.wine/drive_c/windows/fonts).

*Tip: To see the .wine folder, go to View -> Show Hidden Files option in your home directory.*

Step 2: Install Photoshop CS2

Insert your Photoshop CS2 CD in the optical drive and a folder should appear after a few seconds. Go to the "Adobe Photoshop CS2" directory, right click on the setup.exe file and choose the Open with "Wine Windows Emulator" option. The Photoshop installer will pop-up and I guess you know what to do now.

When the installation is over, you will find the Adobe Photoshop CS2 and Adobe ImageReady CS2 shortcuts under the Wine entry in your Start Menu.

And here it is.... Adobe Photoshop CS2 running on Ubuntu 7.10. Enjoy!


source: [http://news.softpedia.com/news/Install-Photoshop-CS2-on-Your-Ubuntu-PC-77260.shtml](http://news.softpedia.com/news/Install-Photoshop-CS2-on-Your-Ubuntu-PC-77260.shtml)

---

### Post by dover19 on 2008-04-21
Will this work with the whole Creative Suite? I also need to run Illustrator and InDesign and I really want to ditch Windows.

---

### Post by YokoZar on 2008-04-22
Steps 1 and 4 are no longer needed on Hardy :)

---

### Post by mwerlberger on 2008-04-22
Great stuff. Thx. Does anybody know if it will be possible to run CS3 with wine? Running Photoshop, inDesign, ... CS3 would be great. Or are there some fundamental problems so that this will not be possible in near future.

Regards,
 Manuel

---

### Post by abh83 on 2008-04-29
Is anyone else having issues getting photoshop to work in wine on hardy?

I've managed to install photoshop but I get an error seconds after the photoshop splash-screen is done loading and photoshop then quits automatically.

:(

---

### Post by yogo on 2008-04-29
I am using Gutsy and was not able to install using that method or any other method for that matter.

The one outlined here wanted me to have service pack two installed and quit because I did not?

---

### Post by Kinst on 2008-04-29
> **abh83 said:**
> Is anyone else having issues getting photoshop to work in wine on hardy?

I've managed to install photoshop but I get an error seconds after the photoshop splash-screen is done loading and photoshop then quits automatically.

:(

Sounds like a font error. Try installing tomaha fonts. You can use wine-doors or winetricks to do it for you.

---

### Post by RobbanC on 2008-04-30
Oooh! So close!

Installation and activation runs smooth and PS is starting up nicely but right after the splash screen I get this error message (screendump as attachment) and then PS quits. I guess it's the same problem as the one abh83 has.

Translation from the error box would be something like:
"An error was found in a program directory and the product can not continue. Please reinstall the program"

I copied tahoma.ttf to both ~/.fonts and  ~/.wine/drive_c/windows/fonts before I installed this thing.

Any ideas, please?

---

### Post by SCURVER on 2008-04-30
***[COLOR="Red"][/COLOR]***

     Is it possible to process Photoshop Elements 6.0 on UBUNTU as well?

                                       FLASH

---

### Post by Cifra on 2008-05-04
> **RobbanC said:**
> Oooh! So close!

Installation and activation runs smooth and PS is starting up nicely but right after the splash screen I get this error message (screendump as attachment) and then PS quits. I guess it's the same problem as the one abh83 has.

Translation from the error box would be something like:
"An error was found in a program directory and the product can not continue. Please reinstall the program"

I copied tahoma.ttf to both ~/.fonts and  ~/.wine/drive_c/windows/fonts before I installed this thing.

Any ideas, please?

It's not a directory, but a library that has issues. You did try reinstallind it, didn't you?

---

### Post by Scooter7 on 2008-05-06
I had the same problem, RobbanC, but now I'm happily running PS CS2.

Here's what fixed it for me:

[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

I hope it works for you!

---

### Post by Glucklich on 2008-05-13
Na, for me seems to be another kind of problem.
What it says goes something like this:
"Unable to continue because of hardware or system error. Sorry, but this error is unrecoverable." And it just shows me a 'Quit' button.
It was all OK in the first time I've installed it, but when I open the second time it shows this message. And this is the second time I make the installation.
Any idea of what this could be?

---

### Post by Glucklich on 2008-05-14
Hello? Can anyone help me on this issue? I can't seem to find the solution for this one.

---

### Post by Scooter7 on 2008-05-16
Gluklich, did you try the solution I posted?   It solved the error you're describing for me, I think.

[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem), give it a shot, let us know if it works.   I may be thinking of another solution I didn't post, though...

---

### Post by Half-Left on 2008-05-16
> **Glucklich said:**
> Na, for me seems to be another kind of problem.
What it says goes something like this:
"Unable to continue because of hardware or system error. Sorry, but this error is unrecoverable." And it just shows me a 'Quit' button.
It was all OK in the first time I've installed it, but when I open the second time it shows this message. And this is the second time I make the installation.
Any idea of what this could be?

You have to install the times32.exe font [http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe)

---

### Post by Scooter7 on 2008-05-16
Ah, thanks for that Half-Left, that's the solution I was trying to think of.

---

### Post by david_ozura on 2008-05-21
Does anybody know if it is possible to run Adobe InDesign CS2 by using Wine. I am using Ubuntu  8.04 - the Hardy Heron.
Thank you.

---

### Post by Glucklich on 2008-05-23
Thank you Half-Left. It worked, but now it gives another error.
"An error has been detected with a required application library and the product cannot continue. Please reinstall the application."
Any ideas?

---

### Post by JimmyI on 2008-05-27
Thanks Scooter7. You solved the problem I had with Photoshop. Even got my favourite plugins working too. Now there's no need to boot into Windows Yay!

---

### Post by xieu90 on 2008-07-02
hi everyone
I installed cs2 and now I can't use any hotkey
even Ctrl O !
what would the problem be ?

---

### Post by pcjunkie on 2008-07-02
I use wine doors for that. Although most things don't actually work, auto hot key does. 

Wine doors will also add win system fonts although just grabbing them from a win system is easier.


> alison@alison-desktop:~$ wine Photoshop.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\windows\\system32\\Photoshop.exe": Module not found
alison@alison-desktop:~$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report


---

### Post by Scooter7 on 2008-07-02
@pcjunkie:

Looks like you're having this problem, judging from your console output: [http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

@xieu90: I've no idea why they don't work, but, if I remember correctly, they didn't work even when I installed with wine doors.

---

### Post by kumo99 on 2008-07-05
@ abh83 : Thank you for adding the tutorial it works great.
@ Scooter7: the link was helpful thank you.

however, when i click on "Save for web" the related window gets blocked and i can't click on any button, so i have to click on "Force quit" to start again.. any idea on how to fix it..?!

thank you

---

### Post by Scooter7 on 2008-07-05
As far as I know, Save for Web doesn't work at all under wine.   I'm not sure why.   I haven't found a solution yet, but you could try searching the forum and google yourself.

---

