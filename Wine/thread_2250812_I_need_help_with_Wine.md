---
title: "I need help with Wine"
date: 2014-10-31
forum: Wine
---

### Post by Licious on 2014-10-31
Hello, 

I bought a laptop that I need to use for work too. I installed Ubuntu (14.10 LTE) on it and I really need to use a program that, I found out later, is made only for Windows. 
The program is called ACS Gold Studio. The installer is compatible with Windows XP / 7 / Vista. 
First I configured Wine to run as Windows 7, tried to install the software (ACS Gold Studio) and it wouldnt even open. I uninstalled the software and then I configured Wine to run as Windows XP. 
When I opened ACS Gold Studio it all looked good, then when I tried to use it, creating a new project, the software crashed. Saying that it encounterd a serious problem and it needs to close. I tried everything I could find on the Internet and it didnt help, unistalled it again, tried different solutions, still nothing.
Can someone please help me? I really need to make this software work on my laptop.

---

### Post by adec2 on 2014-10-31
Have you looked to see if the program requires any other extras to run like .net for instance? Does it try to run an extra installer on windows for .net during installation? That may give you a pointer.
If it is a wine problem you could try posting a bug report in the winehq database. Failing that try and install XP in virtualbox and use it through there?

---

### Post by Mark Phelps on 2014-11-01
Unfotunately, LOTS of Windows apps run poorly, or not at all, in Wine.  Checked the WineHQ website to see the rating for this app -- and it's not listed.  That means that it's likely that it's NOT going to work in Wine.

---

### Post by adec2 on 2014-11-01
Just because it isnt listed in the winehq database doesn't mean it wont work it just means nobody has added it and reviewed its compatiblity with wine. You are free to register and post a bug with the winehq bugzilla

---

### Post by Licious on 2014-11-03
> **adec2 said:**
> Have you looked to see if the program requires any other extras to run like .net for instance? Does it try to run an extra installer on windows for .net during installation? That may give you a pointer.
If it is a wine problem you could try posting a bug report in the winehq database. Failing that try and install XP in virtualbox and use it through there?

I tried to install Virtualbox but i dont know how to use it or if I installed correctly. Can you help me with some guidlines, explanations or the steps I have to take?

---

### Post by Bucky Ball on 2014-11-03
> **Licious said:**
> I tried to install Virtualbox but i dont know how to use it or if I installed correctly. Can you help me with some guidlines, explanations or the steps I have to take?

If you want help installing virtualbox please post another thread in Virtualisation. This support request has nothing to do with your thread title, is off-topic and in the wrong area of the forum. You will improve your chances by posting a new thread. Good luck.

Just a tip: Give your threads descriptive titles. Everyone needs help with something so be specific about what you need help with specifically (I need help with installing 'whatever' in Wine' for instance. 99% of people posting threads in this section of the forum need help with Wine. ;)

---

