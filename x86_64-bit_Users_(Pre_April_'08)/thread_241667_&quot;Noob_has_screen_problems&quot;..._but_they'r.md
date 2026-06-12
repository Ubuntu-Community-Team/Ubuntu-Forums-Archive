---
title: "&quot;Noob has screen problems&quot;... but they're original!"
date: 2006-08-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by HeresJohnny on 2006-08-22
Hello everyone, this is my first post, and I promise I wouldn't be doing it unless there were a good reason.  I installed 64-bit for my Compaq 2570NR (dual-boot XP, 1.8, 512, 60gig, ATI Radeon xpress 200M), and had remarkably few problems doing so from the main installer, basically following the prompts.  I rebooted a few times just to make sure that both Windoze and Ubuntu both worked well, and then I took my laptop home to show my skills that can't be topped to the family, and... I got a bunch of crap.  Specifically, "Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly."  I viewed the server output...
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected.

Fatal server error:
No screens found

I can't understand why I was able to get Ubuntu to load correctly a few times and then had problems.  I don't see that others have had this particular problem.  Can anyone help?

Also, I found (while Ubuntu was working) that I could view and open files from my NTFS (Windows) drive.  I didn't think I would be able to do that, but I was.  (I opened an OOO doc and a presentation)  Is that weird, or normal?  Thanks for your help!!!

---

### Post by John.Michael.Kane on 2006-08-22
Have you read this [**[COLOR="Navy"]PLEASE READ: The Latest Updates Break the Xserver![/COLOR]****[COLOR="Red"] HOWTO solve the problem[/COLOR]**]("http://www.ubuntuforums.org/showthread.php?t=241254")

---

### Post by Kilz on 2006-08-22
> **HeresJohnny said:**
> Also, I found (while Ubuntu was working) that I could view and open files from my NTFS (Windows) drive.  I didn't think I would be able to do that, but I was.  (I opened an OOO doc and a presentation)  Is that weird, or normal?  Thanks for your help!!!

Yes Ubuntu mounts the ntfs drive in read only mode. Its kind of nice if you have media files you like. But dont try writing to it, no matter what anyone says is safe. You could corupt the whole drive and loose everything.

---

### Post by HeresJohnny on 2006-08-23
Thanks for your help!

I shall bow in appreciation for your awesomeness...[http://ubuntuforums.org/images/smilies/eusa_whistle.gif](http://ubuntuforums.org/images/smilies/eusa_whistle.gif)
:-\"

---

