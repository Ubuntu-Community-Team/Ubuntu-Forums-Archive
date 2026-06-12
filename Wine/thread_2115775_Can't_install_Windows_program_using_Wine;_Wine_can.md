---
title: "Can't install Windows program using Wine; Wine can't read DLLs"
date: 2013-02-13
forum: Wine
---

### Post by Weboh on 2013-02-13
I am trying to install Age of Empires III on Ubuntu 12.10 with "wine1.4 1.4.1-0ubuntu1 ". When I get to the product key part and enter my valid product key, it gives me a message that's header said "Invalid CD key!", but the rest of it says "Error loading the PID Generator DLL. The DLL could not be found! Please make sure the file is available in the installation directory and try again," (Note that the comma is a part of the message, and that is where it ends). I was able to locate said DLL, but when I tried to open it, I found out that Ubuntu can't open DLLs, not even with Wine. This is probably because just the DLLs themselves aren't meant to be open separate anyway. Is Wine just having a problem loading the DLL for some reason? What's wrong? I need very specific steps to fix it, as I am a Ubuntu n00b. I have Q4Wine installed and see options like "override DLL" that might help if I knew how to use them. Help Please!

---

### Post by Bucky Ball on 2013-02-13
You might want to look here and research whether that actually will run with Wine. It's not a given.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2441](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2441)

Some stuff works great, some not at all, and everything in between.

---

### Post by Weboh on 2013-02-13
It does.

---

### Post by oldos2er on 2013-02-14
Moved to Wine.

---

### Post by snowpine on 2013-02-14
I am not familiar with this software, so I can't vouch for this solution, but have you seen these detailed instructions?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3795](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3795)

---

### Post by Weboh on 2013-02-14
I did all the things it said to do to install it, but now I have a new problem that that doesn't tell me how to solve. The install works until I get to the point where it tells me to insert the next disk. I've tried mounting a new virtual disk, mounting a new virtual disk and unmounting the first one, and mounting a physical disk. Nothing's worked. The install program won't recognize the new disk.

---

### Post by |{urse on 2013-02-14
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3795](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3795)

Scroll down to the how-to about halfway down the page, it explains why the dlls are not being found and how to fix that.

*edit* D'oH someone already posted that, but yeah, there.

When trying to patch AoE III or install an expansion if the install complains about a problem is the AoE III installation and suggests you reinstall to fix the problem, you are probably just missing a few Registry Keys.

-Run "wine regedit" from a terminal 
-Navigate to HKEY_LOCAL_MACHINE->SOFTWARE->Microsoft->Microsoft Games->Age of Empires 3->1.0 
-Right click in the right pane and click "New->String Value" Name it "CDPath". 
-Right click on the new key and select "Modify". 
-For "Value Data" enter wine's path to your cd drive, ex: "D:\". 
-Click "OK".

Yep, you need to set the cdpath in the registry also.

---

### Post by Weboh on 2013-02-14
Yeah, did that. That's not the problem any more, the problem is what's mentioned in the post above.

---

### Post by |{urse on 2013-02-14
You already changed the cdpath value in regedit?

---

### Post by Weboh on 2013-02-14
I attached a screenie of the error message and what I did. My actual disk is scratched and won't work, so you'll see from the screenie that I told it to go to /media/[username]/AOE Disk 2. I also tried /media/AOE Disk 2. Should I mount the virtual disk to drive D (is that even possible)? You've been very helpful so far, thanks!

---

### Post by Mark Phelps on 2013-02-14
> **Weboh said:**
> How do I set the CD path in the registry? (What is the registry?)

The code is listed in post #7 -- but you said you already did this!

---

