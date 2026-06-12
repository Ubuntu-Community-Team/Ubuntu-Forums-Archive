---
title: "TightVNC problem"
date: 2005-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by hrt on 2005-12-27
Not sure if this problem is specific to AMD 64 or not. Also not sure if it's specific to Kubuntu or if Ubuntu also has the problem.

I installed TightVNC and it works, as long as I use a command line in a terminal window. If I try to run it from the KDE menu or the KDE Run command prompt, it doesn't work. I'm pretty sure it's because I don't get a password prompt in KDE. This leads me to believe that I'm missing some graphics library to create the password prompt. I can't find any information on what these libraries might be, anyone have any suggestions?

---

### Post by sciurus on 2005-12-27
I believe the syntax is either kdesudo <command> or ksudo <command>.

---

### Post by hrt on 2005-12-28
Not sure what you mean by your response. VNCviewer works without a problem when I enter it in a terminal window, the exact same command line does not work from the GUI.

---

### Post by WirelessMike on 2005-12-31
Are you typing "xtightvncviewer" in the run command window?

---

### Post by hrt on 2006-01-02
In a terminal (normal user), both xtightvncviewer -via <ipaddress> <ipaddress> and vncviewer -via <ipaddress> <ipaddress> work. Neither command will work as a menu item in KDE, or in the "Run Command" menu item. I really think I'm missing a library for creating the graphical login/password prompt, I just can't figure out which one is needed.

---

