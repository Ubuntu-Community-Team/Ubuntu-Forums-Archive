---
title: "Installed program won't start"
date: 2022-06-13
forum: Wine
---

### Post by asb3 on 2022-06-13
I'm running wine-5.0 on ubuntu  20.04.
Last week I installed a windows program, and it ran fine.
Today I tried to run it and it failed.
I've done the obvious things (robooting, reinstalling the program) and it still doesn't run.
What could cause this? 
How do I get error messages from WINE?

---

### Post by TheFu on 2022-06-13
> What could cause this? 
Thousands of things. Perhaps 100s of thousands of things.  Do you have any reasonable guesses?
What has changed in the last week?  Did you reboot? Patch? 
Is the version of WINE the same?
Is the WINE environment the same?
Did you use any winetricks?
Are there any other changes ... snap, flatpak, apt, DE, window manager, version of the WINE API used?  Where any other Windows programs installed into the same PREFIX?  That can be a bad idea, since settings for 1 program can conflict with another.

What do the system, hardware and WINE log files show?

All these questions are common and there are web articles about each that every web-search tool will find.

---

### Post by asb3 on 2022-06-13
I'm not aware of anything on the system that has changed since the program ran successfully.
I have rebooted.
I haven't changed WINE or the WINE environment.
The only other WINE program I use regularly still runs.
I didn't use winetricks.
I don't use snaps.
Where are the system, hardware, and WINE log files stored?

---

### Post by schwim-dandy on 2022-06-13
What happens when you start the executable through wine in the terminal?  Does it result in any errors?

---

### Post by TheFu on 2022-06-13
> **asb3 said:**
> I'm not aware of anything on the system that has changed since the program ran successfully.
I have rebooted.
I haven't changed WINE or the WINE environment.
The only other WINE program I use regularly still runs.
I didn't use winetricks.
I don't use snaps.
Where are the system, hardware, and WINE log files stored?

[https://ubuntu.com/tutorials/viewing-and-monitoring-log-files](https://ubuntu.com/tutorials/viewing-and-monitoring-log-files) - google found that easily. Thought I'd mentioned that?

If you are using 22.04, then it is extremely unlikely that you aren't using snap packages.  Canonical has been installing them by default for many of our normal tools.  If you didn't go out of your way, Chromium or Firefox are both snap packages as are a number of Gnome packages.

BTW, is the program super secret?  Every WINE setup for each program is a little different. There are often guides over at WINE-HQ for each version of popular programs.  They maintain a DB with this information.

---

### Post by asb3 on 2022-06-14
Thanks for the pointer to the tutorial.
The program is the Garmin GNS430/530 trainer.
According to the log file, the program ran successfully:
gnome-launched-wine-programs-Garmin-400W-500W_Series_trainer-GNS400W-500W_Trainer.desktop-20553.scope: Succeeded.
When I launch the program, the cursor is replaced by a small circle  containing blue arcs.  After about 20 seconds the cursor reverts to the  arrow, but the window the app is supposed to open doesn't appear.


Snap packages do not install on my system because of the way I had to  partition my hard drives to avoid losing data data when I upgraded to  20.04. I don't remember exactly the problem, but it involved the boot  partition being too small for to upgrade.  I think I had to do a clean  install (rather than an upgrade) on a different hard drive, and set up  some symbolic links to the directory structure which broke snap. 
I don't remember exactly what I did, but I'm sure that 1) 20.04  installed properly and works, 2) my home directory survived, and 3) SNAP  doesn't work.

---

### Post by TheFu on 2022-06-14
[https://appdb.winehq.org/objectManager.php?sClass=application&iId=14032](https://appdb.winehq.org/objectManager.php?sClass=application&iId=14032) is what winehq says.
I don't think I'd trust this program under Linux, if you life is on the line.
I'd run a virtual machine, install the version of Windows is needs, install the program there and run it that way.

---

### Post by asb3 on 2022-06-14
The program ran fine a few days ago. Now it doesn't start. I'd like to fix it.

---

### Post by mIk3_08 on 2022-06-15
> **asb3 said:**
> I'm running wine-5.0 on ubuntu  20.04.
Last week I installed a windows program, and it ran fine.
Today I tried to run it and it failed.
I've done the obvious things (robooting, reinstalling the program) and it still doesn't run.
What could cause this? 
How do I get error messages from WINE?
For me, I rather use VM than wine. I don't know what happen with wine. Before I used to have wine in my Linux Ubuntu Operating System and it works smoothly to any applications in my Linux Ubuntu Operating System but suddenly wine won't work well in my Linux Ubuntu Operating System I don't know what happen so I decided not to use wine anymore. That's why I prefer to use VM than wine. Regards and Cheers.

---

### Post by TheFu on 2022-06-15
> **mIk3_08 said:**
> For me, I rather use VM than wine. I don't know what happen with wine. Before I used to have wine in my Linux Ubuntu Operating System and it works smoothly to any applications in my Linux Ubuntu Operating System but suddenly wine won't work well in my Linux Ubuntu Operating System I don't know what happen so I decided not to use wine anymore. That's why I prefer to use VM than wine. Regards and Cheers.

I had a similar issue.  Wanted to use WINE for MS-Visio and Quicken and a few games.  Was able to get Quicken working about 80% - the main things - which became the wineHQ guide for quicken.  But they release a new program every year and my efforts to get the next version working failed.  The development company had change to an OCX which WINE doesn't support.  Since Visio wasn't working and I had a VM for that, after about 3 weeks of trying to get the new Quicken working, I gave up and installed it into the same VM.

Did you ignore Shwim-Dandy's suggestion for a reason?

---

### Post by asb3 on 2022-06-17
I didn't take schwin-daddy's suggestion because I don't know the exact name of the app.  The only way I can launch it by clicking on the icon that the installer created.

---

### Post by schwim-dandy on 2022-06-17
> **asb3 said:**
> I didn't take schwin-daddy's suggestion because I don't know the exact name of the app.  The only way I can launch it by clicking on the icon that the installer created.

Rather than just ignore the troubleshooting suggestions, in the future, perhaps you should ask how to.

To see what's installed via wine, look at the virtual drive, it's usually installed in your home directory, and find  the installed application's executable.  Then you can use wine to start it in the terminal:

```
Look in: ~/.wine/drive_c/program files/
```

Find your application directory, then executable.  Once found, in the terminal:

```
wine <app executable name>
```

Look at what gets printed to terminal to look for any potential errors.

---

### Post by asb3 on 2022-06-18
Thank you for your help.  The program works when invoked from the command line.  
Still a mystery why it doesn't when I click on the icon.  How do I find out what is executed when an icon is clicked?

---

### Post by schwim-dandy on 2022-06-18
I've never used wine in Ubuntu.  Can you tell me how you installed the appliction?  I'll try to duplicate the process and see if I can't find out how to determine the executable path.

---

### Post by TheFu on 2022-06-18
> **asb3 said:**
> Thank you for your help.  The program works when invoked from the command line.  
Still a mystery why it doesn't when I click on the icon.  How do I find out what is executed when an icon is clicked?

Look inside the menu file. Those are typically text with and Exec= line.

But if it is working, just create your own .desktop file with the exact command that you typed that is working inside. Every program in your menus has a .desktop file, so there are hundreds of examples you can look at on your system already.

---

