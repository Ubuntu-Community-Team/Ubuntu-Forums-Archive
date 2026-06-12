---
title: "cedega &amp; City of Heroes"
date: 2007-03-21
forum: Wine
---

### Post by Voltaic Shock on 2007-03-21
I have installed cedega to run CoH.  I was able to get the updater to show up and actually hit accept to run the game, but after that nothing showed up.  I am no longer able to get the updater to load with cedega.

Should I uninstall cedega along with the game and start over from scracth?  Has anyone gotten this game to run with cedega.  It's a supported game.

Thanks for the help!

Voltaic Shock

---

### Post by demonhunter on 2007-04-23
As I remember, Updater must be ran using wine since it doesn't work with cedega.
Try to update it using wine and then run cedega just to enter the game.

I remember that I used to do that when I was a COH player.

---

### Post by graabein on 2007-04-24
**Voltaic Shock** did you get it to work? I dual boot with XP just to play games. If not for City Of Heroes (and later Age of Conan) I could wipe the wretched partition clean and go 100% GNU/Linux. Oh golly...

---

### Post by lordhebe on 2007-04-24
Well I have no problems with city of heroes under cedega and the patcher does work. Make sure that if the file is called CohUpdater.new then rename it CohUpdater.exe. Also the game must be run in WIN 2k compatibility mode. If that doesn't work my advice would be reinstall the game and try again.

---

### Post by upchucky on 2007-04-24
I got the updater to work....once.... I have an error that the help file says i must do this;....

cat /proc/sys/net/ipv4/tcp_wmem   ....which returns:  4096    16384   131072   

then I am supposed to change the middle set of numbers to 32768 by doing this;....

 sudo echo 4096 32768 131072 > /proc/sys/net/ipv4/tcp_wmem
bash: /proc/sys/net/ipv4/tcp_wmem: Permission denied

the above is supposed to increase my tcp window to stop the error.

when i....  sudo gedit  /proc/sys/net/ipv4/tcp_wmem   ...there is nothing there.

I dont know why i get permission denied, nor do i know why there is nothing in the file they mention. any hints?

---

### Post by upchucky on 2007-04-27
update, City of Heroes working fine with Cedega, wish the window was larger, it does not utilize my 17" display. plus i cant use the extra buttons in game on my 7 button trackball.
 there are answers out there, just gotta find them!!

---

### Post by Voltaic Shock on 2008-01-29
I had CoX running on my desktop, but then I updated Cedega and it stopped working.  I am not sure why I can't re-install CoX on my desktop.

---

### Post by Perfect Storm on 2008-01-29
Change the engine for the game (the engine you used before upgrading it).

---

### Post by Voltaic Shock on 2008-01-29
> **Artificial Intelligence said:**
> Change the engine for the game (the engine you used before upgrading it).

I have tried different engines, but I am having problems actually installing the game.

---

### Post by Perfect Storm on 2008-01-29
What about changing xp/win2000/w98 and see if it makes any changes. Have you checked their game list to see which engine have most stars?

---

### Post by Voltaic Shock on 2008-01-29
> **Artificial Intelligence said:**
> What about changing xp/win2000/w98 and see if it makes any changes. Have you checked their game list to see which engine have most stars?

I have done all that, but I can try looking again and get back to you.

---

### Post by csills6776 on 2010-01-14
What was your resolution to the permission denied error?  I am getting the same error.

---

