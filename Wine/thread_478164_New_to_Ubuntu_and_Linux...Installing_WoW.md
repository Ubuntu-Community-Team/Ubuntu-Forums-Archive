---
title: "New to Ubuntu and Linux...Installing WoW"
date: 2007-06-19
forum: Wine
---

### Post by testament0221 on 2007-06-19
So I'm sure you guy's have heard many stories about people switching from Windows to Linux. Just assume that most of the reasons previous posters have stated apply to me as well. 

So now that that's out of the way, I have a quick question. I was reading the Howto Install WoW for Ubuntu guide, located here: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

As my topic states, I am new to linux. I very used to Windows, and how you install apps. My particular problem is where it states to create a new directory, and copy the contents of my WoW CD's into it, then run the WINE apt-get command. So, I may be overthinking this or whatever...but going off of those instructions, this is what I THINK I should do:

Click Places
Click Homes
Create a new folder (directory), which I named World of Warcraft
I am then going to insert each one of my WoW CD's, explore them, copy ALL of there contents, then paste them into my new World of Warcraft directory
Once this is done, I run the WINE apt-get command, inserting the directory of /home/myname/World of Warcraft
This should prompt wine to install World of Warcraft

So does that sound correct? Also, will I encounter any CD requests during installation. And finally, what about Burning Crusade? Do I add the Burning Crusade file contents to my World of Warcraft directory at the same time that I add the original game to it?

Any help would be appreciated. Thanks.

---

### Post by sad_iq on 2007-06-19
After you copy the content of all your cd's you open a terminal and do ```
cd /home/your_user_name/World of Warcraft
``` (replace your_user_name with the appropriate name and World of Warcraft with the name of the directory were you copied the content of all your cd's)
 then type ```
wine Installer.exe
``` It should install now!!!

---

### Post by testament0221 on 2007-06-19
cool...so do I need to copy the Burning Crusades in there as well? Can I install WoW AND Burning Crusade with one install? Thanks.

---

### Post by testament0221 on 2007-06-19
So I'm in the process of installing World of Warcraft. I copied the ORIGINAL four CD's and ran wine to install them. However I am confused about installing Burning Crusade. Do I create a new directory for Burning Crusade, and run Wine to install it? Or do I copy the CD's into the SAME folder that I copied my original CD's in? Also, when I actually install Burning Crusade, and it asks me where I want to install it, do I install burning crusade in the World of Warcraft folder?

Any help would be appreciated. Thanks.

---

### Post by Syke on 2007-06-19
Just copy all the files into any temporary folder on your hard drive, and run the installer. Let it install to the same World of Warcraft folder.

After it's done installing, you can delete the files you copied from the CD. They're not used after the install completes.

---

### Post by RojoGrande on 2007-06-19
You will need to copy and install Burning Crusade seperately.  I just installed Ubuntu last week and I just spent the whole weekend getting WoW working.  Alot of that time was spent downloading all the patches though which will take some time if you don't already have them.  I also ran into several other small issues which took time and research to resolve, but now that it's running, it looks good.  

Now if I can just figure out how to get my sound working and get my in game settings to save, I'll be good to go.

---

### Post by hikaricore on 2007-06-21
Similar threads merged, moved to Gaming and Leisure.

Please in the future only make one thread for the same/similar topic.
And if there is an existing thread for your topic, consider posting there.

--Aaron :: UGA

---

### Post by tzengenis on 2008-10-16
i install wow too in ubuntu hardy 
i find it very easy using some webs from help config wine/wow config/etc
only bad is the fps in the game is low.. i try alot options but still low.. 
any1 know what i do wrong????

---

### Post by Linuxidiot on 2008-11-17
Hey how are ya, Lol took me 2 weeks to figure out how to get WoW to run on linux, its not that it was hard, its jusst that i was soo used to windows way of doing things:) So in my extensive questioning and researching i have found that you probably wont get the right path in the command terminal to use wine installer.exe unless you have been around the linux comminuty for a while...the easiest way to find the path is to open your terminal and type "cd" space then find where your wow installer is and drag the actual installer to your terminal window and drop it...this should tell you exactly where it is in your system...you might have to backspace the path a bit so it just points to the folder where the installer is in, once you have achieved this and your dir is pathed to the right folder you can then run wine installer.exe. BE FOR WARNED, make sure your wine is configured!!! When installing wine and you get to the part that says configwine or something like that make sure you press auto detect and apply or you will run into pointless problems. I hope this helps

---

### Post by Crazybear546 on 2009-04-19
Hi I am new to ubuntu and I was trying to get wow to install on my computer I installed wine and configured it but in the terminal after i type in 
cd /<path-to-directory>/ (i replaced with a path i made with files on copied from a trial cd.
 wine Installer.exe
I get the error  No installer data could be found. If this problem persists, please contact Blizzard Technical Support.

If someone could help me it would be greatly appreciated.

---

### Post by phantom3113 on 2009-04-19
Just throwing this out there, but I believe you can do all this right from the cd. When you put the cd in, go into the cd's folder (explore the cd contents), locate the installer file, right click and select "open with wine windows program loader" (or even double-click, since wine should be the default program for that). From there, the install should run normally

---

### Post by hikaricore on 2009-04-19
Why oh why did up such an old thread...

---

