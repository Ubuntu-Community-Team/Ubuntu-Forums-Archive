---
title: "Help messed up display driver, left with command prompt!"
date: 2007-07-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by whitenight639 on 2007-07-04
hey im having a simalar problem, im a newbie and the learning curve is steep but im really loving ubuntu.
right im on dapper drake 6.06 LTS (x86_64)

im trying to get google earth and possible that sweet looking beryl working. 

everything was fine apart for 3d working im using an ATi (onboard) radeon Xpress 200G series grafcs card.

so i tryed installing the drivers from ATi, went through the configuration screens and it finished the install then said to open a configuration thing megig which wouldnt work, it added an ''ATi catylist controll centre'' icon in my applications drop down but when u click on it naff all happens. 

so i have no idea how to uninstall this, and i installed Xorg and Xserver in synaptic package manager (i dont know which ones come on with ubuntu standard so dont know which one to remove) 

I run the following command to try configure it 
sudo dpkg-reconfigure xserver-xorg

went through all the steps and after a re-boot was faced with a screen from Xserver telling me i messed up and the location of a log file. i can provide the log file if needed but its quite long. 
and i was left with just a command prompt, no GUI.

so iv rebooted and at the grub selected a different version (of which there is 2 versions and 2recoveries :o)


please for the love of god someone help me before i mess it up further, i havnt a clue whats what if i can just revert back to how it was i would be fine. if you need more details i will give them! 

Thanks

---

### Post by scragar on 2007-07-04
all of the recovery version are command prompt, load up one of them and type:

"startx"
or
"sudo startx"

to kick linux back online, if it loads correctly then it should save your settings again when you shut it down so you won't have to worry about doing this again.

sorry if this doesn't work though, I'm relatively new to linux myself.

---

### Post by whitenight639 on 2007-07-05
I'll try that in a min, im not on the recovery partition right now, i must have 2 seperate installs on my HDD then?

---

### Post by scragar on 2007-07-05
I don't fully understand your question, but recovery modes are just old settings from your log, it's not a separate instillation or anything incase that's what your asking.

---

### Post by pbaumgar on 2007-07-05
If you can, please post your Xorg.0.log from /var/log

---

### Post by whitenight639 on 2007-07-05
Xorg.0.log  **RENAME it to .txt or.log** its saved iv changed the file extension due to upload size allowed for text files

---

### Post by aquavitae on 2007-07-05
Look in your /etc/X11 directory.  There should be a file xorg.conf, and a few others with numbers on the end (or are the numbers in the middle?  Can't remember, but you should be able to work it out.)  The numbered ones are old backued up configuration files.  move xorg.conf to a new name to back it up (mv xorg.conf xorg.conf.backup) and mv the latest numbered one to xorg.conf (mv xorg.conf.10 xorg.conf).  This will hopefully restore the settings to the last one that worked, then you can try to sort out the graphics card problem.

---

### Post by gaylapdancer on 2007-07-05
Don't worry about the two sets of Ubuntu under GRUB, It's just the current, and previous kernal versions (You can tell by the number) which I assume are kept for recovery purposes incase something goes horribly wrong.

---

