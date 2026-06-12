---
title: "Warcraft 3 - xinit black screen"
date: 2007-04-06
forum: Wine
---

### Post by heri0n on 2007-04-06
Hey guys I'm playing wc3 through wine
I start a new x session by xinit -- :1 and then play game by wine wc3 --opengl watever
anyways
when i use ctrl alt f7, f8 to switch X sessions sometimes if I try to go back to my wc3 one (F8) it'll just be black screen and won't come back.. I can still hear the warcraft music though?

Any ideas?

---

### Post by daitheflu08 on 2008-06-25
I'm having the same problem, ever since I upgraded from 7.10 to 8.04 my warcraft 3 gives me a black screen when I start it up using Wine.  Once I get a blank screen I can't get out of it by any means.

I've checked around the net and can't find a solution.  

I'm using a nvidia 7900 graphics card 8.04 ubuntu hardy, the computers specs are up enough to run the game.  (I've run it on 7.10)

---

### Post by daitheflu08 on 2008-06-25
I'm sorry I don't have the same problem exactly ours are different.  Mine fails when I open WC3 with wine.

---

### Post by fattonyabc123 on 2008-07-15
i have the same problem as daitheflu08. im new to ubuntu and cant seem to get wc3 to work. i dont have any sound on this blank screen either.

---

### Post by Lakjin on 2008-07-15
well for one wine cannot run the in game movies.
so go to were you installed wc3, go to the movies folder and delete everything inside it. with that being said, wc3 doesnt run on my computer with wine either. i get it to load up but 1) it is sooooooooo laggy and 2) it keeps flashing back and forth from wc3 to the desktop

---

### Post by SilverDragon on 2008-07-15
> well for one wine cannot run the in game movies.
so go to were you installed wc3, go to the movies folder and delete everything inside it

Actually you can just rename the folder to something like Movies2 if you want to keep them, because when Warcraft loads it won't be able to find it and will just continue to load the game. Maybe you'll want to watch them later or something.

I used to just get a black screen before I renamed the Movies folder so I hope it helps.


p.s. You may want to try Wine as patched by shae.

[http://ubuntuforums.org/showthread.php?t=803988](http://ubuntuforums.org/showthread.php?t=803988)

It'll allow you to host games on ladder and custom games such as Dota(which I can confirm works) and it fixes the loss of focus bug (which I never had so I'm not sure about)

---

### Post by Lakjin on 2008-07-16
deleting everything inside but leaving the movies folders works fine, wc3 loads up.

but ya i guess if you wanna keep them...rename folder.

---

### Post by fattonyabc123 on 2008-07-16
yeah im still getting that loss of focus bug even after patching with shaes. idk where to go now

---

### Post by SilverDragon on 2008-07-16
This seems like a silly question, but what is the loss of focus bug? Do you lose focus when you try to switch to the desktop? or is it  something else?

---

### Post by Hairy_Palms on 2008-07-16
i fixed this by installing wine 0.9.61 alongside the latest version. no idea why the latest version has such a problem, but 0.9.61 runs it perfectly hosting and all.

---

### Post by fattonyabc123 on 2008-07-16
loss of focus bug is i think when it blinks between warcraft 3 and the desktop/ blue screen of emulated desktop. its still possible to use warcraft but the screen is flashing in and out so it gives me a headache. anyways how do i install both .9.6 and 1.1.1 at the same time? im a noob at ubuntu if someone can explain this itd be greatly appreciated

---

### Post by fattonyabc123 on 2008-07-17
robby@robby-desktop:~$ wine /home/robby/.wine/drive_c/program\ files/warcraft\ III/Frozen\ Throne.exe -opengl
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f3b0,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3594
fixme:win:EnumDisplayDevicesW ((null),0,0x33f658,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f690,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
robby@robby-desktop:~$ fixme:win:EnumDisplayDevicesW ((null),0,0x33f40c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f3e8,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:imm:ImmGetOpenStatus (0x13b298): semi-stub
fixme:imm:ImmReleaseContext (0x3002a, 0x13b298): stub
fixme:imm:ImmGetOpenStatus (0x13b298): semi-stub
fixme:imm:ImmGetOpenStatus (0x13b298): semi-stub
fixme:imm:ImmGetOpenStatus (0x13b298): semi-stub


thats what comes up when i run tft from the terminal. i dont know why this happens/ what all that text means, but the game plays just blinking in and out of focus.

ps sry for double post

---

### Post by daitheflu08 on 2008-10-23
I fixed it in tha past but now I've reloaded it and I dont know what to do.  And no I never had to disable the moveis.

I disable the movies and everythign runs completely slow and the graphics are blotchy.  Please provide some help, thanks.

---

