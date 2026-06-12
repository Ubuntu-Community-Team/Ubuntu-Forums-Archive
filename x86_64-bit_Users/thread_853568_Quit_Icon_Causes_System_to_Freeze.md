---
title: "Quit Icon Causes System to Freeze"
date: 2008-07-08
forum: x86 64-bit Users
---

### Post by MainFrame185 on 2008-07-08
I have a new install of Ubuntu 8.04 LTS desktop, 64 bit. It just started locking up when I click on the quit icon, either on the desktop or from the system menu. 

Has anyone else seen this and if so do you know a fix for it?

---

### Post by Laser Dude on 2008-07-13
I notice the same problem with the 32-bit version.  Every time I try to use quit, it causes the system to lock up.  At that point I usually hit ctrl-alt-backspace to reset X, and then shutdown from there.

It's seems to go away if you use a different user, so that means it's specific to the user, not the system.

---

### Post by Javawag on 2008-07-17
> **Laser Dude said:**
> I notice the same problem with the 32-bit version.  Every time I try to use quit, it causes the system to lock up.  At that point I usually hit ctrl-alt-backspace to reset X, and then shutdown from there.

It's seems to go away if you use a different user, so that means it's specific to the user, not the system.

Hey people, I had the same problem on 32-bit, and I found a solution so I thought I'd share.

Goto System > Preferences > Sessions and tick the box next to "Power Manager" and click close. Press Alt+F2 and type gnome-power-manager and press enter. 

TADA! It should now be fine, although for me I had to press Ctrl+Alt+Backspace to exit the first time, but when I logged back in, it was fixed.

- Javawag

---

### Post by epathchina on 2008-07-18
> **MainFrame185 said:**
> I have a new install of Ubuntu 8.04 LTS desktop, 64 bit. It just started locking up when I click on the quit icon, either on the desktop or from the system menu. 
A source that I've experienced often relates to Processor Nap. I 
have a dual G4, and due to fan noise, I early adopted the habit of 
turning one processor off and using the Nap feature of the 
Hardware Preference Pane. [note; requires installing CHUD tools]. 
It works beautifully, unless one hits upon the wrong combination. 
Single Processor + Nap works fine; but avoid Dual Processor +
Nap&#8212;it will result in system wide freeze that will require a hard 
restart. A tricky feature is that even if you have Single Processor+
Nap selected, if the computer is allowed to go to sleep, when it 
awakens, it will revert to Dual Processor mode, with the Nap still 
selected&#8212;again, a guaranteed source of freezing.
Has anyone else seen this and if so do you know a fix for it?
[car dvd player]("http://www.epathchina.com/car-dvd-players-c-114.html")
[mp5 player]("http://www.epathchina.com/mp5-players-c-131.html")

---

### Post by blazyyo on 2008-07-30
The same thing happens to me. It was working fine, until I suspended the computer. The suspend seemed to work fine, but when it resumed I got an error message.

Now when I choose Quit, it takes about 30-60 seconds before the Quit options show up (and suspend/hibernate are no longer options). My way around this is opening the terminal, and typing "sudo shutdown 0". I'm not that great with the terminal, so if this seems like a problem to anyone, please let me know.

---

### Post by Javawag on 2008-07-30
Well that sucks. "sudo shutdown 0" or "sudo shutdown now" are as far as I know perfectly good ways of shutting your computer down - I think that's all the Quit button does anyways.

Suggestion: Create a launcher to that command, right click on the desktop, click Create Launcher and type "gksudo shutdown 0"... that way you wont have to use the terminal to shutdown. Note it's gksudo rather than sudo, so it comes up with a window asking for your sudo password if needed.

Hope this helps,
- Javawag

---

### Post by blazyyo on 2008-07-31
Actually you're solution is post #3 worked perfect. Thanks Javawag.

---

### Post by Javawag on 2008-07-31
Ah cool. Good to hear!!

Glad I could help
- Javawag

---

### Post by stumped on 2009-01-18
Thank you Javawag. I have been trying to figure this out for a while now.
   Your solution worked perfect! =D>

---

### Post by mwillams73 on 2009-03-13
I would thank you but now if i clik on the shutdown icon my system freezes and i cant clik on anything!! Its weird though cause the clock is ticking away and the mouse moves I just cant select anything and the only way to fix it is to control alt backspace and log in then if i clik on the shutdown icon again freeze time all over again, I tried doing the reverse of what you said but that doesnt work either, So yeah dude thanks for helping me bork mysystem worse than it was!!!!!!!!!!!!

---

### Post by cholericfun on 2009-03-23
hi
#3 worked here too,


because a friend had a similar problem,i have played around with launcher a bit trying out
 gksudo shutdown -hP now
but it never worked somehow
then i discovered that my own shutdown/restart just resulted in a system freeze.

---

