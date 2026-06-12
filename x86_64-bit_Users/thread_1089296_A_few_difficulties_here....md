---
title: "A few difficulties here..."
date: 2009-03-07
forum: x86 64-bit Users
---

### Post by Atlantia_Rai on 2009-03-07
Hello!
I am very new to Ubuntu. I just finished installing a few hours ago. I am now trying to install the 250 some odd updates for it. So I go to updates, and but it comes up with a window stating that it cannot lock something or over, and unlock some over thing? (I'll go check it out later, and post more specifications.) It says something about needing authorization, but give me no where for a password or anything.
If you have any idea, please let me know, I really want to get this working.
As well, my wireless while in Ubuntu does not work, but I think this is because it has not been updated yet.

One last thing, anyone know how to get a tablet laptop to work with Ubuntu? That is what I have installed it on, and I really depend on my touchscreen for many things. How can I make the touchscreen compatible with Ubuntu?

Thank you very much!

---

### Post by axel_2078 on 2009-03-07
When you get that error message, it's normally because you have some other kind of package manager running in the background. Make sure you don't have Synaptic, add/remove programs, Aptitude, or the command prompt open when you attempt to update via the update manager.

---

### Post by Atlantia_Rai on 2009-03-07
Thank you. I will go and give that a try right now. :)

---

### Post by sumit.kalra999 on 2009-03-07
Hi,

something about authentication...

<snip>

Added by bapoumba: regarding authentication, please see here [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by Favux on 2009-03-07
Hi Atlantia_Rai,

You should be able to get your tablet set up.  What type of tablet pc do you have?  Which Ubuntu did you install?  Was it Intrepid (8.10)?

---

### Post by Atlantia_Rai on 2009-03-07
> **Favux said:**
> Hi Atlantia_Rai,

You should be able to get your tablet set up.  What type of tablet pc do you have?  Which Ubuntu did you install?  Was it Intrepid (8.10)?

I have a 2524 HP Pavilion.

I installed Ubuntu 8.10 for 64 bit.

I have read that you can get the tablet working with it, I'm just such a newb at this that I usually have no idea what people are talking about. It took me a number of reinstalls before I could even make it so I can see files from both OS (Vista and Ubuntu). But I got that working.

---

### Post by Atlantia_Rai on 2009-03-07
Right. So I`m in my Ubuntu now, and it`s magically installing the updates. It is no longer prompting me for some authorization thingummy. That`s good I suppose.

Another issue has popped up. My laptop puts itself into French mode when in Ubuntu. So I cannot so an `at` sign for emails, or question marks. Any idea how to change the keyboard for Ubuntu? 
In Windows, it`s just a simple `Ctrl+Shift`. I try that on Ubuntu and it just doesn`t want to work.

Sorry for so many questions everyone. But thank you very much for helping me!

Edit: I figured out how to fix the keyboard issue. Turns out that having it in 'Canada' mode makes it French and all silly like that. I set is to USA instead. Now it works fine.

---

### Post by Favux on 2009-03-07
Hi again Atlantia_Rai,

Do you mean a HP Pavillion TX2524 with a stylus with a button and an eraser, and touch?

---

### Post by Atlantia_Rai on 2009-03-07
> **Atlantia_Rai said:**
> Right. So I`m in my Ubuntu now, and it`s magically installing the updates. It is no longer prompting me for some authorization thingummy. That`s good I suppose.

Another issue has popped up. My laptop puts itself into French mode when in Ubuntu. So I cannot so an `at` sign for emails, or question marks. Any idea how to change the keyboard for Ubuntu? 
In Windows, it`s just a simple `Ctrl+Shift`. I try that on Ubuntu and it just doesn`t want to work.

Sorry for so many questions everyone. But thank you very much for helping me!

Edit: I figured out how to fix the keyboard issue. Turns out that having it in 'Canada' mode makes it French and all silly like that. I set is to USA instead. Now it works fine.

> **Favux said:**
> Hi again Atlantia_Rai,

Do you mean a HP Pavillion TX2524 with a stylus with a button and an eraser, and touch?

Yes that is the one. I always forget to say 'tx2524'. I shoud try and remember that from now on.

---

### Post by Favux on 2009-03-07
Hi Atlantia_Rai,

You have the choice of trying the 0.8.1-6 debs from Loic2 at his Wacom wiki or compiling the kernel driver.  I'd try the deb.s first.  The link for Loic2's Wacom wiki is at the top of this thread:

[http://ubuntuforums.org/showthread.php?p=6546012#post6546012]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012")

So you'd skip section 1 on compiling the kernel driver because your going to try the pre-compiled wacom debs.  At the bottom is a sample TX2500 xorg.conf and instructions for using it are in section 2  (remember to backup your xorg.conf!).  Take it slow and read this over.  This should get your Wacom features working.

Then towards the bottom is a link to the Rotation HOW TO.  That will let you get your tablet pc into tablet mode.

And this thread is useful for setting up other TX2500 stuff.

[http://ubuntuforums.org/showthread.php?t=845911]("http://ubuntuforums.org/showthread.php?t=845911")

---

