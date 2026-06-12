---
title: "Totally new to Linux! No sound"
date: 2008-11-26
forum: x86 64-bit Users
---

### Post by Brutally on 2008-11-26
This my first install of any linux.
I've not heard a sound from this at all what could be the basic error? How would i rectify that too please?
Spec AMD 64 linux 8.04.
Creative X-Fi Fatal1ty sound card there is a linux driver for this but all it does is download to my desktop. How do you install?
Sorry but totally new to this - the instructions in their readme file

SAYS
In terminal,


1) Goto source directory

2) Execute make command as root

   make

   make install


ok i go to source then type make ----- etc but it dont work.
how do i make something root?
Cheers in advance

---

### Post by ibizatunes on 2008-11-26
What sound card do you have? Maybe post this in absolute beginner

---

### Post by Brutally on 2008-11-26
> **ibizatunes said:**
> What sound card do you have? Maybe post this in absolute beginner

Sorry really a total newbie.
All i found on forum was x64 so posted here.
I keep having to load windows just to post on this forum as the firefox brower just keeps cursor spinning and doesn't load the edit or anything to forum :(

---

### Post by ibizatunes on 2008-11-26
Welcome btw,
the creative card your talking about isnt really supported yet in linux! I would bet it will work by ubuntu 10.4 (2version time)
There is ways of getting it to work, but i havent managed it myself yet
I cant really help  you sorry

---

### Post by halovivek on 2008-11-26
i am also having the same problem. till now i am trying to get a solution from that one. wait and wait.

---

### Post by nss0000 on 2008-11-26
BigB:

That's a well-known weakly-supported soundcard. I use a SB16 whitebox workalike without issue.

---

### Post by Brutally on 2008-11-26
I have an onboard soundcard too but im getting no sound from either!
Is there not just a mute somehwere?

---

### Post by nzadLithium on 2008-11-26
could you paste the output when you run make here? and if you have onboard sound you might want to make sure its disabled in your bios, as having two soundcards plugged in can cause weird device numbering if it isn't setup right.

---

### Post by BGFG on 2008-11-26
Hey, when i first started using ubuntu i thought i had no sound also. have you checked your volume settings ? In my case, system volume was turned down. (the speaker icon in the tray)

But you have a sound card and i do not. So if you need to install your driver:
[LIST=1]
[*]Right click on the file on the desktop open with archive manager and extract it to the desktop
[*]Go Applications >>Accessories>>Terminal
[*]In the terminal, type: ```
 cd Desktop/"your driver folder name"
```
[*]Then type :```
 sudo make 
```
[*]then type :```
 sudo make install 
```
[/LIST]

---

### Post by markbuntu on 2008-11-27
Extensive sound troubleshooting and setup is here, including links for multiple sound cards and links for getting your X-f\Fi working along with a lot of stuff you didn't know you needed to know:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

