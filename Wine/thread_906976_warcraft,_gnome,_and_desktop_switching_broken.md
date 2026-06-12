---
title: "warcraft, gnome, and desktop switching broken"
date: 2008-09-01
forum: Wine
---

### Post by moneyd on 2008-09-01
greetings,

up until about an hour ago, i had a perfectly decent running warcraft install on ubuntu 8.04 hardy.

somehow in the process of trying to get warcraft to run on a dedicated xserver, (which i failed to figure out btw, so help on that would be apprecciated), i managed to find some way to make warcraft take over my desktop.

before i would launch wow on desktop 2 with firefox or something on desktop 1 and ctrl-alt-l or r arrow back and forth

now the switching still seems to work (i can switch to desktop 1 and it will actually give me alt-tab options for the windows there (no warcraft option)) but warcraft is the only thing i can see

i tried using 2 different launch-wow.sh scripts i found, one in the forum archives here and one from the gentoo wiki howto, but i doubt those caused the problem (i did get errors about permissions and being unable to use X, so i found this thread, [http://ubuntuforums.org/showthread.php?t=255148](http://ubuntuforums.org/showthread.php?t=255148) which involved using sudo dpkg-reconfigure x11-common, so its possible that may have mucked it up i suppose.

i tried to remove x11-common to reinstall it back to defaults but cant do that without removing a ton of stuff, heh, so i tried just a reinstall but the settings i did in dpkg-reconfigure still stayed.

any ideas why this may be happening, what i might have done to cause it or how to fix it?

and any info on getting wow up and running on a dedicated x server for hardy would be greatly appreciated (best ive gotten so far is a xserver full of vertical lines on the F9 term, ugh)

thanks for any and all help, its greatly appreciated

regards


EDIT:

solved

the desktop paging no longer functioned after setting seperate preferences in winecfg (specifically, unchecking "Graphics->Allow the Window Manager to control the windows"
checking this again restored desktop hotkey paging (ctrl-alt-l or r arrows)

this leaves you a bit stuck in terms of using the alt-key in gaming (warcraft at least) as that was one way to enable it, the other is System->Preferences->Windows and modifying the movement key (i'll be going with that one for now till i can figure out how to successfully launch a dedicated WoW XServer)

---

