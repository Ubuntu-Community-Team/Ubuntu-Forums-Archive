---
title: "Wine 0.9.59 and WoW on 7.10"
date: 2008-04-11
forum: Wine
---

### Post by Boktai1000 on 2008-04-11
Hey this is my first post on the Ubuntu forums, but Ive just today updated to Wine 0.9.59 from .58 on Gutsy Gibbon, and everything looked like it was working fine, when I logged into World of Warcraft I noticed a few of my Keybinds didn't work, they included Shift+Mousewheel Up/Down and Shift + the Mousewheel middle button.  I think it might be a problem with shift because I tried to rebind it and it set it as camera zoom, which would just be the mousewheel up/down.  Again I had no problems with this from .58 and any previous version, if anyone knows how to fix it due to something new in .59 or maybe i found a bug, either way if anyone knows a solution or would like to help me troubleshoot that would be very helpful :P.

Edit: It appears I am still able to use shift to type capital letters, but it also appears that i cant use ctrl+scroll up/down either, and actually it does work about 10% of the time... weird problems.  Anyways this still isn't something I can stand, I would prefer 100% of the time of it working and I have a raid coming later today and I'm hoping it will be fixed by then >.<

---

### Post by Shay Stephens on 2008-04-11
Did it work with .9.58?  If so, just uninstall .9.59 and reinstall .9.58.

---

### Post by Boktai1000 on 2008-04-11
Yea just did that, it was easier than i thought it might be to do, i thought it was going to nuke the .wine folder, so i ended up backing some stuff up but everything was in tact, so that was pretty nice for future reference ill know what to do.  Everything seems in order with .58, must just be a weird issue with .59 is there anyway to report this or see if they are aware of it?

---

### Post by Shay Stephens on 2008-04-11
wine periodically has regressions in certain areas, so I like to keep a mental note of which version of wine is stable for me, that way I can test out the new release and go back if needed.  Usually within a few upgrades, any regressions are usually taken care of.  And like you discovered, it is real easy to uninstall and reinstall wine :-)

---

### Post by sephiros9883 on 2008-04-11
i have the exact same issue, and was wondering how do you go back to an old wine?

---

### Post by Spydr4590 on 2008-04-11
I just wanted to reply. I have a stable 7.10 and have been using many revisions of WINE. The 9.58 version of wine, shift key worked fine. Just installed 9.59 and my shift key no longer works. Very annoying. Hopefully someone can post a work around or I will need to downgrade back to 9.58. Thanks :)

---

### Post by Lotekk on 2008-04-11
Wanted to reply as well, having the same exact issue.  Everything was perfect in 0.9.58 Wine, let my auto-update install 0.9.59 and now I can't shift-click to link items in game anymore. Nor can I ctrl-click to try them on.  

Will be reverting back to 0.9.58 in a moment.  Guess this is one of those prime examples of "If it ain't broke don't fix it!" :P


UPDATE:  Went back to 0.9.58 and confirming it does fix this issue, so it wasn't some crazy fluke, it is 0.9.59 causing the shift/ctrl key issues.


**sephiros9883:** The way I went back to 0.9.58 from .59 was simply "Uninstalling" Wine completely via my package manager (Synaptic Package Manager).
Once it's gone I just double-clicked the .deb of 0.9.58 for Ubuntu 7.10 that I downloaded from [The WineHQ .deb packages archive](http://wine.budgetdedicated.com/archive/index.html) ([http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)).  
Let it install (ignoring the warnings that a new version of wine is available) and I was good to go, WoW was back to it's normal glory.  There may be an easier way to but that worked for me. :)

---

### Post by Boktai1000 on 2008-04-11
I think someone should see if this is happening to them on Hardy Heron.  If u need to know how to downgrade don't worry about your .wine folder because everything stays in tact, I was worried i would lose my vent setup and wow so i backed them up, just go to the download section on the main site and it says at the bottom old .deb files or like archive of debs, just download 0.9.58 for gutsy, and then remove wine with synaptic, install .58 and your shift will return to normal :)

---

### Post by sephiros9883 on 2008-04-11
actually I'm on Hardy Heron (testing it out to see if i can make the switch)

That's why i asked, because there is no Debian packages for 8.04!

I guess i out of luck for now. I tried to compile the source, but it seemed to need a lot of libs to compile with opengl support and many other features, so I didn't do it.

If you have any other solutions, please share! :)

---

### Post by Boktai1000 on 2008-04-12
Actually one of my friends was running 8.04, and I think he got Wine set up by go into Add/Remove programs and searching for Wine.  If that doesn't work try searching synaptic package manager.

---

### Post by zilog on 2008-04-12
I have this problem too. 7.10 with 0.9.59.
Its like if you right/left-click with the mouse it completely ignores any pressed shift/ctrl/alt keys.
In 58 all was fine.

---

### Post by JettCRX on 2008-04-12
Ahhh this thread was just what I needed.  Thanks!

---

### Post by Stormspireiv on 2008-04-13
I'm not a WOW user, but I can confirm that this bug does not only affect WOW.

I found this happened in Warhammer 40000: Dawn of War (and expansions) as well. Launching the game in a seperate X session seems to remedy the issue if you do not feel like downgrading (though more testing is required)

P.S. I'm on Gutsy not Hardy.

---

### Post by Burkey on 2008-04-14
Exactly the problem I hit last night.  I am on Hardy.. how do I downgrade to .58 ince the budget dedicated deb's are all for Gutsy?

I have not started looking yet but if i find and answer will post here for anyone else, unless someone else beats me to it

---

### Post by Shay Stephens on 2008-04-15
You can get .9.58 here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

They have versions going back many releases of ubuntu (scroll down the list to find your version).

---

### Post by Sauli on 2008-04-15
I have similar Shift key problems wIth Ubuntu 8.04 Beta and Wine  0.9.59 when playing WoW. 

Wine  0.9.59 is the first Wine installation in my new PC. When I removed it with Synaptic Package Manager  and downloaded the previous version 0.9.58  and opened it with GDebi Package Installer it refused to install due to "Error: Dependency is not satisfied: libldap2"

Edited 16.4:
               the missing ibldap2 can be downloaded from [http://packages.ubuntu.com/gutsy/i386/libldap2/download](http://packages.ubuntu.com/gutsy/i386/libldap2/download)
               install it with the dpkq package manager or GDebi Package Installer before you install the 0.9.58 version

With 0.9.58 the shift-click seems to work ok.

Sauli

---

### Post by kogos on 2008-04-22
version 0.9.60 is out... check it out cause it might fix the problem...
Among other bug fixes, i see this for version 0.9.60:

"12543  Shift-click not working in World of Warcraft after upgrade to latest
wine (0.9.59) (affects Photoshop, too)"

---

### Post by JettCRX on 2008-04-22
0.9.60 may be *out*, but it's not in the Ubuntu repositories yet, fyi.

---

### Post by ferod on 2008-04-22
Can confirm that shift click works in 0.9.60, mouse side buttons are still working and such... We have ourselves a perfect wow environment =O.

---

