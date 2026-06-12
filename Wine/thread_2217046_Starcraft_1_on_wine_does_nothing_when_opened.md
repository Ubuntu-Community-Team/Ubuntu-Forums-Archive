---
title: "Starcraft 1 on wine does nothing when opened"
date: 2014-04-15
forum: Wine
---

### Post by wolfguy14 on 2014-04-15
So I downloaded starcraft anthology from my battle.net account (I lost my disks years ago) and it installed fine but everytime I go to play it nothing comes up?. Also I installed warcraft 3 but everytime I try to open that it asks for a disk (once again downloaded from battle.net cause I lost my disc years ago)

---

### Post by sffvba[e0rt on 2014-04-15
*Thread moved to **Wine**.*

---

### Post by CitadelUniversal on 2014-04-15
> **wolfguy14 said:**
> So I downloaded starcraft anthology from my battle.net account (I lost my disks years ago) and it installed fine but everytime I go to play it nothing comes up?. Also I installed warcraft 3 but everytime I try to open that it asks for a disk (once again downloaded from battle.net cause I lost my disc years ago)

Do you use the proprietary graphics card driver or the open source drivers usually the proprietary driver works better though if you are using 64-bit you MUST have the 32-bit libraries installed - if you have 64-bit OS then install the 32-bit libraries.

---

### Post by wolfguy14 on 2014-04-15
Theres no option to change the graphics driver in my wine config [IMG]http://i.imgur.com/pH8GPOZ.png[/IMG]

---

### Post by CitadelUniversal on 2014-04-15
You should have on your system a software from canonical called "additional drivers" search for it on the HUD Display - once you found it then switch to the proprietary graphics card driver.

---

### Post by Mark Phelps on 2014-04-15
Depending on the version of Ubuntu you're running and the video chipset you have in your PC, you may not be able to install proprietary drivers.

We need to know the Ubuntu version you're running.

To see which video chipset, open a terminal and enter "lspci", look for the line containing "VGA" and post that information back here.

---

### Post by adec2 on 2014-04-18
Starcraft works out of the box with the cd version so this sounds like another problem

---

