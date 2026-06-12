---
title: "Can't install Mafia.."
date: 2008-01-17
forum: Wine
---

### Post by gray_damascus on 2008-01-17
I use 7.04. So I wanted to install Mafia... The setup won't start with wine...

I researched on this and learned that people who have installed Mafia used loki...

what is loki and where can I get it? is it for free?
Is there any other alternatie to install mafia?

---

### Post by kostkon on 2008-01-17
If you mean *Mafia* the game, then according to its [*Wine Application Database* page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2291") it runs just fine.

What error messages do you get?

---

### Post by gray_damascus on 2008-01-17
Yes its the game...

if its the setup.exe, no error messages comes... it just opens a simulated desktop and closes.

if its the MafiaLauncher.exe:

err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\fidz\\Desktop\\Mafia1\\MafiaLauncher.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\fidz\\Desktop\\Mafia1\\MafiaLauncher.exe" failed, status c0000135

**BTW, I transferred the files from the CD's to my desktop... either way mounted or not, I can't install

---

### Post by gray_damascus on 2008-01-17
bump

---

### Post by hikaricore on 2008-01-17
Please wait 24-48 hours before bumping your posts.
Patience is a thing you'll need to observe around here as this is a volunteer forum.

---

### Post by gray_damascus on 2008-03-28
been a long time...

sorry hikaricore...


found the problem in wine...

i needed the 'MFC42.DLL'

it should also be placed in the systems32 folder or something in wine...


just posting this so anyone with the same problem would know...

---

