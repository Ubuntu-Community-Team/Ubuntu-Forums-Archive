---
title: "First suspend fine, second suspend forbidden"
date: 2009-04-27
forum: x86 64-bit Users
---

### Post by khamil8686 on 2009-04-27
I start up my computer with Ubuntu 9.04 Jaunty Jackalope x64 installed and then can suspend once just fine, then i can resume fine, but the screen comes up with a small plug icon in the system tray that wasnt there when i suspended and then wont suspend again (using the power button on my computer as the suspend button, set it to default under power options), i click on the little plug and it gives me the options to suspend and hibernate but when i click on suspend a window pops up and says "Action Forbidden - Suspend not available on this computer" when i know my motherboard supports suspend, it worked flawlessly on intrepid ibex but not on jaunty for some reason. ive only been using ubuntu for about 2 months so dont know too much jargon and such yet but not really afraid to use the command line and do technical things, i enjoy them :) i thought maybe i had some weird quirk and tried a 2nd fresh install of jaunty (first install was fresh also) but the suspend problem persists. any help would be appreciated, thank you :)

--update--
this problem doesnt always happen on the second suspend, i just had a string of this problem hapening on the 2nd suspend (start computer up for the day, suspend once, come back, problem occurs) it happens intermittently. things ive done include reinstalling the package uswsusp because i read about it on another thread possibly being the problem for another suspend problem, i also had the setting where the os will save what programs were running and then bring them up again in the same state when you resume i disabled that option so whenever i log out or suspend it begins the programs anew (least i suspect this is what it does)

---

### Post by khamil8686 on 2009-04-27
With this problem ive also tried to log out then log back in and whenever i do it (timed re-login) everything comes back but is frozen and an alert box pops up and says Failed to initialize HAL! Any help is appreciated :) Thank you!

---

### Post by raziv on 2009-05-18
I had a similar problem, with the power-manager applet on my netbook chageing from the level meter to a power-plug icon after using an external DVD drive. Suspend stopped working with the same message as you describe. Also, I couldn't mount CDs in my drive.
What solved both these problems was typing:
```

sudo service hal restart

```
in a terminal window. The power-manager was immediately revived and suspend operations where available.

NOTE:
I am no expert, and don't know what the risks are in using this command, so you may wish to look around before you use it. No negative effects have been spotted with my wee AA1.
yet. ;)

HTH
-- raziv

---

### Post by khamil8686 on 2009-05-18
ill give that a try when i have some free time :) i found that killall gnome-power-manager got rid of the plug icon but then i couldnt suspend, i was just happy i could get rid of the plug icon lol. sudo service hal restart gives me some more to go on and poke around and try to figure out what is going on. right now i have dual boot 8.10 and 9.04 using 9.04 as a project to work on in my free time, thank you for the reply! :)

---

### Post by raziv on 2009-05-18
> **khamil8686 said:**
> ill give that a try when i have some free time [...] thank you for the reply!
With much pleasure indeed. Be sure to keep us up to date on your problem's status.
> [...] i found that killall gnome-power-manager got rid of the plug icon but then i couldnt suspend, i was just happy i could get rid of the plug icon lol. [...]
That is like disconnecting the warning light and buzzer on an airplane when the weather's bad :). The plug icon is shown (at least in my case - scholarly opinion welcome, anyone?) when the power-manager cannot obtain data about the power system status, i.e. something is wrong.
In my short linux experience, but that nevertheless includes wiping out a whole harddrive with a single Enter press, I found that killing a process without knowing *exactly* why is not the best CoA, to say the least. Some (all?) OS programs (such as hal) have scripts that do the shutting-down and starting-up in a controlled manner. I believe it is always better to use these, whenever possible, instead of brutally killing processes (even though the latter is more fun ;)).

---

### Post by khamil8686 on 2009-05-18
hehe disconnecting the warning light and buzzer got rid of the icon, that small part at least made me happy! hehe the plug when i hold the mouse icon over it says Unable to get data... i never knew what it was trying to get data from! but that makes alot of sense that it couldnt obtain data about the systems power status. id click on that plug and click suspend on the menu that would pop up and it would tell me suspend is forbidden! anyways, i tried "sudo service hal restart" and the plug icon disappeared but then when i tried to suspend again it would fade to a black screen, display some text, or display a blinking cursor and never shut off the monitor or fans and id have to do a hard restart (press power button till it rebooted? unsure what its called) so maybe it thought it was suspended but never shut off anything? i have no idea, and im not really versed in command line and more in depth linux topics yet, *pats stack of new books on how to use command line and more advanced linux topics* so hopefully in a few weeks :) having a brain injury makes it kinda frustrating too, i have short term memory loss so ill have an error occur and write down some details but then when i think about it later ill realize i need more details so ill have to make it happen again :P im kinda like dory from finding nemo :) anyways, i appreciate the help! if you have any other ideas im happy to give em a try, heres a new post i made recently i think might have something to do with it, unable to load modules.dep FATAL error and 2 softresets failed. check it out, i think (hope? maybe hope is a bad word if modules.dep is a horrible thing to fix) that they might be related, but im not sure :P [http://ubuntuforums.org/showthread.php?t=1162619&highlight=2+softresets+failed](http://ubuntuforums.org/showthread.php?t=1162619&highlight=2+softresets+failed)

---

### Post by khamil8686 on 2009-06-07
ordered a NVIDIA video card and going to bypass the ati video card on my mobo, hopefully this fixes it :)

---

