---
title: "Jedi II Outcast on Ubuntu 7.04"
date: 2007-07-15
forum: Wine
---

### Post by toddbmobile on 2007-07-15
**Step 1**
Remove any existing installs of &#8220;wine.&#8221;
[B]
Step 2[/B]
Delete the &#8220;.wine&#8221; folder in you home holder (remember it is hidden) and its contents. (regretfully this would remove any preexisting windows program installs)
[B]
Step 3[/B]
Goto Winehq for the latest version of &#8220;wine.&#8221; (must be 0.9.39 or newer)
[http://www.winehq.org/](http://www.winehq.org/) and download Wine 0.9.39 or newer.
[B]
Step 4[/B]
Once at the site select &#8220;Binary packages for various distributions will be available from:&#8221;

[http://www.winehq.org/site/download](http://www.winehq.org/site/download)
[B]
Step 5[/B]
Then select Ubuntu link.

**Step 6**
Next, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copying and pasting the following code below at the prompt &#8220;$.&#8221;

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
[B]
Step 7[/B]
Next, add the repository to your system's list of APT sources. Do this by selecting copy and then paste the below code in the terminal prompt &#8220;$.&#8221;
sudo wget [http://wine.budgetdedicated.com/apt/....d/feisty.list](http://wine.budgetdedicated.com/apt/....d/feisty.list) -O /etc/apt/sources.list.d/winehq.list
[B]
Step 8[/B]
sudo apt-get update (updates the above repository on you system)
[B]
Step 9[/B]
sudo apt-get install wine (Installs &#8220;wine.&#8221; Select &#8220;y or yes&#8221; if asked to do so.)
[B]
Step 10[/B]
(The remaining steps and paths will change based on where your setup.exe for Jedi Knight II:Outcast is located)

Also in a terminal window type the code below at the prompt &#8220;$&#8221;:

[B]cd /cdrom

Step 11[/B]
at the prompt &#8220;$&#8221;:
cd GANEDATA

then

wine Setup.exe
[B]

NOTE:[/B] After installation you will need to goto Megagames and get the no-cd crack for the single player side. I have tested and both multiplayer and single player work. To launch the game you will need to "cd" to the folders in the ".wine" folder and actually type jk2sp.exe or jk2mp.exe in a terminal window.

**Sound Issues:**
Regretfully the only problem I really found is with sound, so before I launch the game I run the command below as ROOT which enables sound:

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

---

### Post by mbadawi23 on 2008-04-17
Is it needed to uninstall and reinstall every thing?
I already installed Jedi knight outcast smoothly. Can't I just follow your steps afterwards?

---

### Post by Ferrat on 2008-04-17
My guess would be that he posted this when wine 0.9.39 was fairly new and not everyone had it, just install Jedi II Outcast as normal :)

---

