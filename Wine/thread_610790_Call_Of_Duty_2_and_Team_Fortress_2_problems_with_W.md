---
title: "Call Of Duty 2 and Team Fortress 2 problems with Wine"
date: 2007-11-12
forum: Wine
---

### Post by Cardamar on 2007-11-12
Alright. Here's the problem.
First off, I'll start with Team Fortress 2;
I just upgraded from Wine 0.9.46 to Wine 0.9.49. TF2 ran fine in .46 ((even though it did have some minor graphical problems)), but now that I've upgraded, it won't start. I'll launch Steam, go to my Games list, click TF2, and hit launch. First, it gives me this error telling me my graphics drivers are outdated, something about Direct3D HAL blah blah blah, but I got that same error in .46 every time I launched the game and it worked fine. So, I click Continue and a window comes up saying "Preparing to launch Team Fortress 2..." just like it should. However, when the window disappears, nothing happens. TF2 doesn't launch. The Preparing To Launch window just vanishes as that's it. Do I have to reinstall TF2 now that I've upgraded Wine? 
[noob]And also, on a side note, how might I go about updating my video drivers so I don't get the weird graphical glitches in game? I've got the .run file to upgrade them, but what do I do with it? [/noob]

Now for Call Of Duty 2;
As unfortunate as it is for me, I got CoD2 a while back when it was being sold on 6, count them, SIX CDs instead of one DVD.
Anyway, the Setup begins to run just fine. I open up the CD and navigate to Setup.exe on Disc One. However, when setup reaches the end of the first disc it simply stops. Doesn't prompt for Disc 2 or anything, just stops.

Any thoughts?

Thanks,
Cardamar~

---

### Post by mbradlcu on 2007-11-12
yea I had to downgrade to wine 46, think steam didnt' work anymore among other things..

as for the cd issue you may be able to explicated eject the cd as long as you're not in that directory,, use the command line and type 'eject'. I'm not totally sure this works as I may have just copied over the complete install from a MS install.. good luck!

---

### Post by Cardamar on 2007-11-13
hm. Downgrade, eh? I hate using outdated software, but I'll give it a shot.
And I went and figured out the whole .run dilemma, so that's solved.
As for CoD2, I'm just gonna buy the version that's on one DVD, since my only problem here seems to be switching discs.
Thanks for the help, bro (=

---

### Post by cogadh on 2007-11-13
When installing games through Wine from a CD or DVD, you should use the terminal and not the file browser to do it. Using the file browser can lead to CD switch problems as the drive will be marked as "in use" by the file browser and CD swaps will be prevented. You can get around it by using the command "wine eject", but it doesn't always work right and the newly inserted CD may have problems mounting.

To run an install from the terminal, it's really quite simple:
```
wine /media/cdrom/setup.exe
```
Adjust the path and executable name to match your actual system and game.
If you still have the CD swap problem (it can happen), then open a separate terminal and use the "wine eject" command:
```
 wine eject D:
```
Obviously change the drive letter to match your actual Wine configuration. You should be able to pop in the next CD, allow it to automount normally, then continue the install.

As for your TF2 problem, did you make any custom registry edits in Wine with 0.9.46 and if so, did you run "wineprefixcreate" after updating to 0.9.49?

---

