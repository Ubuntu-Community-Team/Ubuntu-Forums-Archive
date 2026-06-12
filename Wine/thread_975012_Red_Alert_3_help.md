---
title: "Red Alert 3 help"
date: 2008-11-08
forum: Wine
---

### Post by butler pirate on 2008-11-08
Well I'm new to ubuntu and i'm loving it.  I got Wow running, but I've heard rumors that RA3 should work according to the beta testing so I go ahead and install it.  I installed it from the cd instead of copying to my hdd, it installs but ea download manager froze during the install.  I ran the game and it gave me this message "The game can not start There seems to be a problem contacting the license server. Ensure your internet connection is active and try again in a few minutes."
  
    In fact it seems to be the exact message from spore because it's from EA, so i followed a few spore facts seeing how there was a lack for ra3.  One told me to install winhttp.  After each attempt id try running the game or eadownload manager. I then tried adding comctl32.dll on a hunch.  I tried doing it in the gnome-terminal, it didn't work but it did say something like ASetup.exefixme:winhttp:request_set_option unimplemented option 31

 I tried to set the request_set_option to 1 but it didn't work.  I tried copying the cd to desktop, running it in terminal, and using the wine command on the eadm, it finally installed that time and then the game ran.  I think it would give me a missing dll and i may have gotten that during the time I was troubleshooting.  It runs pretty slow and there is no cursor.  I'm running the latest ubuntu and wine as of october. 

 My first question is can I use the C&C cursor fix for this somehow?  I saw that you had to get a wine patch, but that was for a really old wine version and I've already installed. So would I just uninstall wine somehow?  I'm afraid that'd ruin the game I've already got on here but it would be worth trying out, but I'm not even sure if it would work for ra3.  Also I don't have an exe i have to run it from file and I can't figure out where I installed this, could someone explain about ubuntu and how i could find it.  Anyway I'm going to see if I could find some of these answers, also i'd like to play the coop missions too if anyone has a fix for the lan.

---

### Post by netyire on 2008-11-09
Wine has a wonderful 'appdb' section on it's website where game compatibility is frequently updated to keep up with the various changes made in the new wine releases every so often. Workarounds and tips to get games running with wine is also placed here. If you want to get a game working with Ubuntu, make sure to check out the appdb section of the wine website first, at [http://appdb.winehq.com](http://appdb.winehq.com)

It appears that network access is unavailable at the moment, but I'm sure someone will fix it or provide a workaround (like that for C&C3). In the meanwhile, single player access seems to be the limit.

There are, however, some recommendations for getting the game to run more smoothly on wine, one of which is related to the animated cursor, here's the howto pulled from appdb.winehq.com:

> git clone git://repo.or.cz/wine/hacks.git                            
cd hacks
./configure --prefix=$HOME/wine-ra3   #you can set it to wtvr you want.                            
make && make install #this will install wine + some wine patches (including the animated cursor patch) to your home directory only...
start the game with $HOME/wine-ra3/bin/wine /patch/to/your/RA3.exe
thats it :)                            


Good luck and happy gaming!

---

