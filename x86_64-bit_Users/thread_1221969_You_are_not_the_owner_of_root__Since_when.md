---
title: "You are not the owner of root?  Since when??"
date: 2009-07-24
forum: x86 64-bit Users
---

### Post by Jazmac on 2009-07-24
I assume I need to enable something but I did the install so I don't get this one.  I'm attempting to install a theme.  And I need to drill down in the root and root opens but no files show up.  Then I went directly to the root and it says** "I am not the owner**"  :confused:

I'm a noob (hides face in shame) and I assume something has to be enabled.  What do I do?

-JazMac

---

### Post by NullHead on 2009-07-24
Do you mean root's folder, or root? As in /root or / 

/ being the root of the whole file system, or /root, being the administrator account's home folder.

---

### Post by WakkiTabakki on 2009-07-24
Hi
How did you try to install the theme? Where did you get the theme from, and in what format is it?

/N

---

### Post by oldos2er on 2009-07-24
> **Jazmac said:**
> I assume I need to enable something but I did the install so I don't get this one.  I'm attempting to install a theme.  And I need to drill down in the root and root opens but no files show up.  Then I went directly to the root and it says** "I am not the owner**"  :confused:

I'm a noob (hides face in shame) and I assume something has to be enabled.  What do I do?

-JazMac

 Usually you would install a theme you've downloaded by dragging and dropping it somewhere under the Theme tab of System, Preferences, Appearance.

---

### Post by Jazmac on 2009-07-24
> **WakkiTabakki said:**
> Hi
How did you try to install the theme? Where did you get the theme from, and in what format is it?

/N

I was attempting to install **Animated Desktop** from [here]("http://www.compiz-themes.org/content/show.php?content=88248&forumpage=5").  I was trying to follow the video to get it installed.  Normally it's drag and drop but not all are that way I'm finding out.  Here is the instructional video.
**[http://www.youtube.com/watch?v=FfQ8Fh5-D-U](http://www.youtube.com/watch?v=FfQ8Fh5-D-U) **


> **NullHead said:**
> Do you mean root's folder, or root? As in /root or / 
 
 / being the root of the whole file system, or /root, being the administrator account's home folder.
 
Hmmm.  Remember, I'm still a noob so you'll have to use that Linux to Windows decoder ring for a minute.  I was drilling down to the ROOT folder and the cursor just spun there and no files would show.  Using the File Browser, I'm locked from it as well.

Pardon my explanation.  I'm still a bit of a yut with Ubuntu. 


> **oldos2er said:**
> Usually you would install a theme you've downloaded by dragging and dropping it somewhere under the Theme tab of System, Preferences, Appearance.


I agree that is what you would usually do but this theme required a bit more of a gymnastic effort.

Anyway, I don't mind the theme support but I need to understand why I as the administrator is lock out of some areas.  I can get there doing sudo bash but the gui prevents me and I think that's odd.

-JazMac

---

### Post by NullHead on 2009-07-24
> **Jazmac said:**
> Hmmm.  Remember, I'm still a noob so you'll have to use that Linux to Windows decoder ring for a minute.  I was drilling down to the ROOT folder and the cursor just spun there and no files would show.  Using the File Browser, I'm locked from it as well.

-JazMac

Okay, that is the home folder of the root account (root = administrator). I suggest you try doing what you need to do with a file browser run as root (the administrator). Try this in a terminal window: ```
gksudo nautilus
```

Using the window that **should** have opened up, you should now be able to see the contents of the root folder (/root) 

It's quite possible that there's nothing inside the root folder, so if you don't see anything in there, press the keycombo CTRL+h to see hidden files and folders. 

I think after that, you should be able to see something in there. 

:popcorn:

---

### Post by NullHead on 2009-07-24
After watching the video, I've come to the conclusion that accessing the "r0ot" folder isn't needed. This person that made the video is showing you how to make a shortcut for running a-desk. Accessing the "r0ot" folder is actually his own username ... so in reality, all you need to do is go to your "home" folder, press CTRL+h and find the .v.a-desk folder. 

You can safely skip that step of his tutorial. 

You do however, need to finish the tutorial. Add the command "/usr/local/bin/a-desk" into the Command option in the "Add Custom Launcher" window.

---

