---
title: "Running Realflight 6.5 on Ubuntu 13.04"
date: 2013-04-28
forum: Wine
---

### Post by pacman377 on 2013-04-28
I have installed wine on my machine and was installing realflight when I got the "KEError 32318" warning. After some serching I found that the fix is to:

*The application wants a non-zero drive serial from a drive letter. Making one *[I]up for C:\ in winecfg -> Drives lets RealFlight start.

[/I]However what does it mean a non-zero drive serial I have change the "$0" in the "winecfg" file to 
"$1" and still no luck. Obviously Im missing something if anyone could help me fix the issue I wouldbe most greatful as I would love to get my simulator back up and running.

---

### Post by Mark Phelps on 2013-04-28
I know you mentioned v6.5 -- but maybe there is some info in the links for the other versions that will help:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=9130]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=9130")

---

### Post by pacman377 on 2013-04-28
Thanks for the reply. That link had what I needed but now I have another issue It keeps telling me to insert the cd when it is already in. Ive already made sure that the path and everything is correct in the drives tab in wine configure for the cd. So Im leaning to think that the copyright protection on the cd could be the issue. As much as I dont want to I may have to set up the computer to dual boot windows right now. Unless someone can shed some light on the current situation.

---

### Post by Mark Phelps on 2013-04-30
My suggestion is that you search this forum for that problem and its solution.  That is a common problem running stuff with Wine, and folks have repeatedly asked that to be solved.

---

