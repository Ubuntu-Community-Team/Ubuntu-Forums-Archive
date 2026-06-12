---
title: "little help for a new user? multi boot problems"
date: 2008-05-04
forum: x86 64-bit Users
---

### Post by RaveJunkie on 2008-05-04
Ok i have been using Ubuntu since 7.10 so im STILL VERY new user but have re did my kernel and many other changes thanks to these forums and just recently signed up, but have been using these for a year or so.  I hope im not re posting same problem but I have installed, XP pro no prob, then 32 bit vista ultimate, then 64bit ultimate and had to use vista boot pro, and they all then worked, then i got greedy and wanted my ubuntu on, i installed it and rebooted and everything on ubuntu works :)   but after editing my grub menu i got xp and ubuntu to boot, BUT bot my vistas now after pointing them to the right drive with grub says "missing win32.exe"  is this a common prob?? i tried a repair install on vista but it just says "cant repair this error" I can post my grub.menu later today if needed but i dont think i did it wrong or it would not find the vista error right? makes sense...... i also found if i unplug the ubuntu drive (disable the ide controler) it boots vista....... any idea how to fix this.....

I am very good with XP and gui's so if there is a grub gui editer that would also make my day btw......

i know im new in all but im not worthless so please be nice  ;)

thanks in advance

---

### Post by alexandru_sorin on 2008-05-05
Try to use EasyBCD next time. You gone have less problems.
For now, check if the vista partion number is corect in your grub list. Me, i reinstall vista, install easybcd after that instal ubuntu, add ubuntu to boot in easybcd.

---

### Post by RaveJunkie on 2008-05-05
OK so i really would like but them booting is more inportant but I WOULD like the drive letters to be the same in all 5 of my boots, and with many network drives this could be a problem......

ok here is my plan of action you tell me if this sounds good.....??

im going to format all but my storage (500gig) drive then go to work on other 6 drives.... i have 4 xtra sata and 2 ide

Im thinking xp first then changing its drive letter to W right off the bat
[COLOR="Purple"]
then Ubuntu and Backtrack 3   Easy to this point

ok now gets VERY hard i can install vista 32 bit in windows no prob then install bdcedit and get them working..... now vista 64bit ultimate is lame and will ONLY install as the C:/ and can only be done from the disk....... (no where near as friendly as ubuntu  :(  )    ok this is where everything messes up on me and i need help....... i will try to get in 64bit and just set the vista options with bcdedit..... (i have no clue what winblows was thinking with this SUPER not user friendly stock way to edit the mbr/boot.ini)   but my ubuntu should be ok booting from the vista menu......?

sorry for the long game plan but i really dont want to mess this up for the 4th time..... lol  sound like this plan should work and get all my drive letters the same>>>????[/COLOR]

---

