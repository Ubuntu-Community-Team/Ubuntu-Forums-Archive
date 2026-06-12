---
title: "Rosetta Stone 3.4.7 and the mic issue"
date: 2014-05-28
forum: Wine
---

### Post by Alex D on 2014-05-28
Hi folks,

I am on Mint 13 MATE, I had no issues to install RS  3.4.7 using Wine 1.7.18 (even the previous versions had no issue to  install), however the mic list does not show up.
It does if I apply the winepulse.drv, but the sound is garbled.
I  wanted to apply the other trick: launch your program with WINENOPULSE=1  wine program.exe etc. but I cannot understand how to do it.

Can you help?

Thank you
Alex

---

### Post by ryanvade on 2014-05-31
cd to the directory that has the rosetta stone .exe file (in a terminal)
cd ~/.wine/drive_c/"Program Files (x86)"/rosetta_directory_name_here
then run the following
WINENOPULSE=1  wine rosettastone_file_name.exe

---

### Post by Alex D on 2014-06-10
Hi,

I tried your solution, got to the cd directory and ran: 

WINENOPULSE=1 wine RosettaStoneVersion3.exe

I get the following error:
wine: cannot find L"C:\\windows\\system32\\RosettaStoneVersion3.exe"

Why does it go to windows\\system32 to search for it?

Many thanks for your help.

Alex

---

### Post by Alex D on 2014-06-19
Anybody?

---

### Post by Tom_ZeCat on 2014-06-20
Hi, Alex, you might not like my solution, but I fought with this issue for days, never getting it to work, pulling out my hair and practically getting an ulcer.  I finally resorted to not using WINE and instead running RS via Windows 7 under VirtualBox.  I prefer to run Windows apps under WINE if at all possible so that everything's integrated into Kubuntu for me, but some apps just haven't run satisfactorily for me, Rosetta Stone being one of them.  I remember seeing a lot of reports at winehq.org of mike hassles in RS.  I don't think anyone has solved this one.  Of course, if I'm wrong and someone has, please speak up.

---

### Post by Alex D on 2014-07-15
You are right, I do not like to go virtual but if there is no choice I will have to.
As a secondary question, given that I will have to uninstall RS from my machine, apart using the software removal, how do I remove the content of the 3 CDs? I do not think that the software removal will get rid of them.

Thank you
Alex

---

### Post by monkeybrain20122 on 2014-07-15
All your wine applications are in the ~/.wine folder. You can either 1) use uninstall wine programs(a wine utility like Windows' add/remove) to just remove RS, or 2) if you have nothing else installed with WINE simply delete the ~/.wine folder. To get rid of the .desktop files (the launcher icons) go to ~/.local/share/applications/wine and delete them/it.

All the ~/. folders are hidden folders in your /home/usrname directory, press ctrl+h or choose 'show hidden' from file manager's folder to show them.

P.S. RS is over-rated and a rip off IMO. There are many excellent free language lessons online (e.g the BBC ones) and the real way to learn a language is to make friends with native speakers. :)

---

