---
title: "Ubuntu doesn't show desktop environment, request for help"
date: 2009-05-07
forum: x86 64-bit Users
---

### Post by jugendfan on 2009-05-07
Hi!

I hope this is the right place to ask for help. I have huge problems with my ubuntu.

I use ubuntu 9.04 Jounty Jackalope on an acer aspire 5100 laptop computer. I have double booted it with windows vista and i'm using the 64-bit version on an amd processor. Until this morning everything worked fine. I got all things up and running and the system worked satisfactionally. 

When i started Ubuntu this morning the bar that shows at the beginning showed fine but when it was supposed to switch to the desktop environment something went wrong and the screen just shows a lot of strange colours. 

I tried almost all the options in recovery mode but it didn't help. I also tried using a live cd and that worked to, so i could access the file system and salvage a few important files but i don't know how to fix ubuntu again. 

I think the problem could be connected to installing the ATI catalyst control center for my graphics-card. I think i did that last time i used Ubuntu, last night. But i am not sure. I never experianced this problem before. 

ps, i'm kind of a newbie

Pleace help! :(
Yours 
Jonathan

---

### Post by Yellow Pasque on 2009-05-07
Try booting without the splash screen so you can actually see where it's getting hung up,

Also, did you use the xfix recovery mode option?

---

### Post by lensman3 on 2009-05-07
Try a CNTL-ALT-BACKSPACE key sequence.  This command should try and kill the X11 gui and do an immediate restart.  It should kill X11 and then the run-level 5 spawn program (init - it is called init) should restart X11 and go to the login screen.

This might do a reset on your drives, but I don't hold much hope.

---

### Post by luctor on 2009-05-08
> **lensman3 said:**
> Try a CNTL-ALT-BACKSPACE key sequence.  This command should try and kill the X11 gui and do an immediate restart.  It should kill X11 and then the run-level 5 spawn program (init - it is called init) should restart X11 and go to the login screen.

This might do a reset on your drives, but I don't hold much hope.

Is far as I know CTRL-ALT-BACKSPACE is disabled by default.

To reset X11 enter ALT-SYSREQ-K

---

### Post by jugendfan on 2009-05-08
Would resetting X11 Gui endanger the stuff on my windows partition?

---

### Post by frakie on 2009-06-29
Same issue here... How can we solve it?

---

