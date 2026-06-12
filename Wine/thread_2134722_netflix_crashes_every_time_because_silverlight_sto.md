---
title: "netflix crashes every time because silverlight stops working?"
date: 2013-04-12
forum: Wine
---

### Post by drazzah on 2013-04-12
Hi,
  I don't know much at all about Ubuntu and using it; due to unforeseen circumstances I now have my boyfriend's laptop for the month which runs ubuntu. Anyways, while using netflix via wine, it told me to update silverlight. So, stupidly, I did so not knowing that I shouldn't have. So when I installed the latest version of silverlight, netflix stopped working properly. Everytime I open netflix using netflix-desktop in terminal, the plugin crashes and netflix freezes. 

  So my question is: is there any way to fix this? I attempted to uninstall silverlight but I haven't found out how. Anything complicated on ubuntu goes totally over my head.. but if anyone knows how to do this to fix netflix, I'd appreciate it. 

  I'm not sure if anyone needs this info, but I have an Asus N61JQ and I have ubuntu version 12.04 LTS.

  Thanks.

---

### Post by anoldone on 2013-04-12
Two ways to uninstall are listed under Wine's FAQ:
[http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391](http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391)

---

### Post by ernestj on 2013-04-12
i pasted the command exactly like they are written in the instructions and nothing happened. 

in the terminal it just acted like i put nothing in there.

is there a command that i add to the code on the above website for wine?

Ernie

---

### Post by kurt18947 on 2013-04-12
> **ernestj said:**
> i pasted the command exactly like they are written in the instructions and nothing happened. 

in the terminal it just acted like i put nothing in there.

is there a command that i add to the code on the above website for wine?

Ernie

That might be a good thing.  If you see no feedback from a terminal command, it most likely did what you asked.  You should  get some response if it DIDN'T succeed.

---

### Post by anoldone on 2013-04-12
```
wine uninstaller
```
Opens "Add/Remove Programs" window for me which lists currently installed applications.

---

### Post by compholio on 2013-04-25
If you update the netflix-desktop package to the latest version (0.7.0) and wipe the profile folder (rm -Rf ~/.wine-browser) then when you relaunch netflix-desktop it should automatically create a new profile with the correct version of Silverlight.

---

