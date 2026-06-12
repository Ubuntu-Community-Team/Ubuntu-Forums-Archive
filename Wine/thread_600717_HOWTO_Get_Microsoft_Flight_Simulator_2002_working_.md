---
title: "HOWTO: Get Microsoft Flight Simulator 2002 working on Wine"
date: 2007-11-02
forum: Wine
---

### Post by TheThinker on 2007-11-02
I don't know if anyone's figured this out also, but I found that Microsoft Flight Simulator 2002 works quite well on Wine version 9.46. Note: I haven't tried the same instructions on later versions that have been out like .47 and .48.

First of all, do not use Wine-File. It works great on other games but for the purpose of installing MFS 2002 you're going to have to use the terminal. Insert CD #1 into your main CD drive and BEFORE YOU DO ANYTHING move or reduce the size of the window so that it's well away from the center of the desktop screen yet large enough for you to type commands into. Trust me; there's a reason for this. Secondly, use Wine-Config and change the OS to XP if you haven't done so already.

After you're done adjusting the terminal, type in and enter:

wine /media/cdrom0/setup.exe

This should get the setup working with the game, although I've found that (depending on how old your CD drive is) it can take minutes for the setup to load. If this happens, be patient.

Now, there are moments within the setup menu in which you select an option, enter it, and nothing seems to happen. That's okay. It actually turns out that the installer creates an additional window that you cannot see when this happens. To see this window, press the key combination ALT+TAB to select the Terminal window that you used to run the installer. Since the terminal is well away from the center of the screen, once you see terminal you'll also see the new window that the installer created. You may need to switch from the Terminal window to the Setup Window using the ALT+TAB key again, so keep that in mind for later.

Once you have the installation working, it will ask for the next CD again. I found that simply opening your CD drive by pressing its "open" button successfully mounts and unmounts the next CD into the installer. However, it might not happen this way, so the Terminal comes in handy once again. You can switch to your terminal window and use it to create a new terminal window. In that new terminal window, type and enter:

wine eject d:

Note: If you inserted the CD into a different drive, just replace " d " with the letter corresponding to your drive.

Everything else at this point should be relatively smooth. I've found that the installer actually creates links (yes, Windows links!) to MFS 2002 on your desktop. I'd just delete them if I were you. 

That's the end of the installation, but what about getting the game to work? If the installation seemed to go well, use Wine-File to execute the Flight2002.exe file. Now, on my computer an error message alerted me that MCF 2002 had to use a default font for the main menu. Click "Okay" and wait until the main menu appears.

If the main menu still doesn't appear for some time (say, 5 minutes), experiment using the ALT+TAB command to switch between the opened windows and back to MFS 2002. Sometimes you'll just see a black screen if you switch back, and at this point it helps to click on one of the screen's corners (I can't explain the bug; I just handle it!).

Playing the game can give you some minor bugs (yet ironically are present when running on Windows also). When loading a flight, you may see just a black screen, and the solution for this I've found was to just click at the corners and attempt to resize the window (even though you'll see no borders at all). It's strange that this seems to get the video up and running, and running well I may add.

I haven't yet gotten to experiment with joysticks or the like; sorry. If you're content with just using the standard key controls, then I'm glad to be of some help to you! Enjoy your cruises!:)

Special notes: MFS 2002 also installes the AirFight simulation, and I've found it to be buggy to say the least. Let me know of any other bugs you find with similar versions of Wine if you get MFS 2002 working too please!

---

### Post by secristrc on 2008-05-10
At what point in the process did you install Direct X?  I've had no luck getting this to run, but was encouraged by your posting.

I'm very interested in seeing this work.  Thanks!

rcs

---

### Post by TheThinker on 2008-05-11
If you're using the same version of wine as I described above, then you shouldn't have to install Direct X. If it asks to install it, just refuse. Besides, it's generally not advised to install Direct X on wine anyway, unless you're confidant that Direct X will be stable on your system.

---

