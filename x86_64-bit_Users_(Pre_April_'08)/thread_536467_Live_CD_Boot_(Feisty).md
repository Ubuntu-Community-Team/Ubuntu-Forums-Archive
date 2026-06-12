---
title: "Live CD Boot (Feisty)"
date: 2007-08-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by spoonman184 on 2007-08-27
I am trying to load the 64 bit live cd (Feisty) onto my pc, but when I select boot/install from the main menu, it will load the kernel fine, go to the black boot screen, a few lines will pass, then my monitor will go blank with no signal and I am forced to restart my pc. 

I believe it may have to with the video card. I reinstalled Windows XP and the driver was deleted. I am going to try and remove the video card in a few days and see if this resolves anything. I am unsure which video card is in the pc.

---

### Post by dewey on 2007-08-27
Did you try using the safe graphics mode, or the alternate install cd?

---

### Post by spoonman184 on 2007-08-27
Safe Graphics mode did the same thing

where can I get the alternate CD?

a link would be most appreciated =)

I will try again then using the alternate cd

---

### Post by edd07 on 2007-08-27
Just go to [the download page]("http://www.ubuntu.com/getubuntu/download") and check the 'Check if you need the Alternate CD" Option. 

Good Luck

---

### Post by crjackson on 2007-08-27
> **spoonman184 said:**
> I am trying to load the 64 bit live cd (Feisty) onto my pc, but when I select boot/install from the main menu, it will load the kernel fine, go to the black boot screen, a few lines will pass, then my monitor will go blank with no signal and I am forced to restart my pc. 

I believe it may have to with the video card. I reinstalled Windows XP and the driver was deleted. I am going to try and remove the video card in a few days and see if this resolves anything. I am unsure which video card is in the pc.

Mine is the same way.  For mine, when the initial boot screen (cd menu) us up, I select F4 and change the screen resolution to 1024x768.  Then select the boot/install and hit enter.  If that doesn't work, there are other boot options that will.  Try this one 1st and see what happens.

You may have to hit the F6 key and add: **nosplash noacpi noapic**

Do the screen resoultion 1st.

---

### Post by spoonman184 on 2007-08-27
I will try the resolution and no api w.e first. I got the alternate CD. Is there an option for a Live CD boot on the alternate, because as I was going through I got to the part where you need to partition your hard drive, and I was like uhh... not what I want to do just yet. 

Thx for the help. Kudos 4 U All!

---

### Post by spoonman184 on 2007-08-27
The (not alternate) boot CD works with a different resolution. 
I installed Feisty.
But now, how do I change the screen resolution before Feisty loads? In a sense, I installed an operating system but now I don't have a monitor. I am currently working off of the boot CD.

I will try looking in the BIOS to see if I can fix this.

---

### Post by crjackson on 2007-08-27
you need to edit your gurb and change the 2 instances of "splash" to "nosplash" and you may need to add the noacpi noapic paramaters as well.  That's why I like to start with the live CD.  It lets me check to see what parameters are going to be needed after the install is done, and you can edit the files in a GUI interface as well.

I'm not too great with the cli yet, so hopefully someone else who is will jump in now and help out.

---

### Post by spoonman184 on 2007-08-27
Ok.. I dont know what you just said. I don't know what to change because how do I change anything if I can't see anything? Am I supposed to change something while I have loaded the Live CD?

And I would like exact instructions, not generalizations. Such as:
Change your gurb by opening /home/gurb with GEdit and adding the line abcdefg

---

### Post by spoonman184 on 2007-08-28
Well I was able to load Ubuntu from the hard drive finally, but I had to do so using recovery mode. I typed exit as soon as the command prompt was available, and then all was bliss. But I would like it to remain bliss. I do not want to have to do this every time the PC restarts/shutdowns. I have tested this and I will need to do this every time. I changed the screen resolution once Ubuntu loaded and that did not fix the problem. I will try other things and downloading all updates to see if this fixes the solution.

---

### Post by crjackson on 2007-08-28
> **spoonman184 said:**
> Ok.. I dont know what you just said. I don't know what to change because how do I change anything if I can't see anything? Am I supposed to change something while I have loaded the Live CD?

And I would like exact instructions, not generalizations. Such as:
Change your gurb by opening /home/gurb with GEdit and adding the line abcdefg

```
gksudo gedit /boot/grub/menu.lst
```

use your find function or your eyes and you will locate two entries that say "splash"  replace them with "nosplash" (without the quotes).

Save and reboot.  Hopefully that will do it.  Post back and let us know what happened.

---

### Post by crjackson on 2007-08-28
> **spoonman184 said:**
> Well I was able to load Ubuntu from the hard drive finally, but I had to do so using recovery mode. I typed exit as soon as the command prompt was available, and then all was bliss. But I would like it to remain bliss. I do not want to have to do this every time the PC restarts/shutdowns. I have tested this and I will need to do this every time. I changed the screen resolution once Ubuntu loaded and that did not fix the problem. I will try other things and downloading all updates to see if this fixes the solution.

Changing the resolution was ONLY for booting the LiveCD.  It will do nothing for you at this point.  The problem is the splash screen (usually).  The rez change BEFORE booting the LiveCD was just to get you past the splash screen.  Desktop resolution has nothing to do with the LiveCD splash screen.

---

