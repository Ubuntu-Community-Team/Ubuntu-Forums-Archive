---
title: "Menu Start Problem"
date: 2008-03-07
forum: Wine
---

### Post by David Vincent-Jones on 2008-03-07
I have installed IntelliCAD 2000 onto the system and this runs correctly from the Terminal. I did change "Program Files" to "Program_Files" so that Terminal would not be upset but otherwise no other changes.

I installed "icad.exe" into the Wine setup, using W.XP but everything else remained as Wine was installed. I have not installed other programs.

I edited the location of "icad.exe" throught the browser in Wine .. it looks fine.

From the Terminal "icad.exe" runs perfectly but it fails to run from the menu system. notepad (the Wine app.) runs from the menu system.

Ideas would be appreciated.

---

### Post by happyhamster on 2008-03-08
- Do you mean you renamed the Program Files folder? In that case the menu entries can't find the program I think.

To fix the menu entries: right click the main menu and choose Edit Menu. When you find the correct wine entry, right-click again and choose Properties. You can edit the path to the program from there.

- Also: it's best not to rename any standard folders' names. If you have trouble with spaces or any special characters, you can 'escape' them by putting a \ before them:

cd Program\ Files

- or use quotes:

cd "Program Files"

- Or use the autocomplete function (very cool): type cd Pr and then press the tab key so linux can complete the line for you. This only works if there are no other folders starting with the letters "Pr", else try cd Pro and tab or cd Prog and tab, etc.
If you press tab twice, you'll get a list of all possible names.

Good luck.

---

### Post by David Vincent-Jones on 2008-03-09
Very strange ... I find that if I install my program starter string in a totally new menu location it runs just fine but if I attempt to install the starter string within the wine menu structure it fails.

Anyway it is running now ... that is the most important thing.

---

