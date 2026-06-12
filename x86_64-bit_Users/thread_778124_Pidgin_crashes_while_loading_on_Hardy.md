---
title: "Pidgin crashes while loading on Hardy"
date: 2008-05-01
forum: x86 64-bit Users
---

### Post by Saghaulor on 2008-05-01
I've installed a fresh copy of Hardy as my upgrade from Gutsy to Hardy was botched.

Anyways, Pidgin crashes every time I try to load it. I've completely removed it via synaptic, and then reinstalled it and it still crashes.

Any thoughts?

---

### Post by Yellow Pasque on 2008-05-01
Try loading it from a terminal to see any messages the program outputs before it exits.

---

### Post by Saghaulor on 2008-05-01
> **Temüjin said:**
> Try loading it from a terminal to see any messages the program outputs before it exits.

Apparently I have to run pidgin as a sudo. I got it working. Thanks for the help.

---

### Post by Yellow Pasque on 2008-05-01
I would advise against that because of security concerns. What error messages does it give you when you try to run it as a regular user?

---

### Post by soxs on 2008-05-02
Do _NOT_ run pidgin as sudo. It's like leaving your frontdoor open!
Post your error messages you get from ```
pidgin
``` from terminal

---

### Post by bconverse on 2008-05-04
I am having the same problem, however, I cannot get any error messages from trying to run pidgin from the terminal.  It freezes before anything can come up. The buddy list window appears, but its just a white box with the window border.  No text appears inside it at all, then its frozen.  Oddly, this was working fine before.  Nothing I might've done prior to this stands out as a cause. 

I should add that I have tried removing and reinstalling with synaptic.  No help there.

---

### Post by KillaKurt on 2008-05-04
I had this problem on Gutsy.  I uninstalled and reinstalled also and nothing helped.  I had messed up something with an Nvidia driver beforehand anyway so I just reformatted my partition and reinstalled the OS lol...

I'ma n00b! O:-)

---

### Post by Hammer89 on 2008-05-04
Did you try running "sudo apt-get remove --purge pidgin && sudo apt-get install pidgin" (sans quotes)?

---

### Post by toppledgod on 2008-05-04
> **soxs said:**
> Do _NOT_ run pidgin as sudo. It's like leaving your frontdoor open!
Post your error messages you get from ```
pidgin
``` from terminal

toppledgod@toppledubuntu:~$ pidgin
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!

---

### Post by Yellow Pasque on 2008-05-04
See this thread:
[http://ubuntuforums.org/showthread.php?p=3624430](http://ubuntuforums.org/showthread.php?p=3624430)

---

### Post by bconverse on 2008-05-04
> **Temüjin said:**
> See this thread:
[http://ubuntuforums.org/showthread.php?p=3624430](http://ubuntuforums.org/showthread.php?p=3624430)

That did it for me.  Thanks!

---

### Post by bconverse on 2008-05-04
Looks like I spoke too soon.  I was able to open it right after I followed the directions in that thread (renaming the .purple folder to .purple.bak) But, I closed it and tried to re-open it, and we are back to crashing, and I still can't get any error output in the terminal.

---

### Post by Yellow Pasque on 2008-05-05
Did you look at the other solutions in that thread?

---

### Post by peakshysteria on 2008-05-06
pidgin -h

---

