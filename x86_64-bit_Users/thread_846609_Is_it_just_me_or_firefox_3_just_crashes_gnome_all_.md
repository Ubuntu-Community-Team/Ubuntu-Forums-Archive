---
title: "Is it just me or firefox 3 just crashes gnome all the time"
date: 2008-07-01
forum: x86 64-bit Users
---

### Post by Derviansoul on 2008-07-01
Hello everyone,
I've got installed Ubuntu 8.04 x64, and the desktop it's so unstable there isn't a day where Firefox 3 does crash more than once, or just crashes gnome with no reason at all, in such a way that i have to reset the computer manually.

I've got an ati x1300 card but even with all the effects off it still happens as often, such problems don't occur with opera.
Does anyone has this problem? My Firefox version is the final one from the repositories.
regards

---

### Post by stchman on 2008-07-01
> **Derviansoul said:**
> Hello everyone,
I've got installed Ubuntu 8.04 x64, and the desktop it's so unstable there isn't a day where Firefox 3 does crash more than once, or just crashes gnome with no reason at all, in such a way that i have to reset the computer manually.

I've got an ati x1300 card but even with all the effects off it still happens as often, such problems don't occur with opera.
Does anyone has this problem? My Firefox version is the final one from the repositories.
regards

I run FF3 on Hardy 64 on 3 different machines (C2Q, C2D, Athlon64) and ZERO crashes ever.  You may have a hardware problem.

What are the specs of your PC?

---

### Post by Derviansoul on 2008-07-01
I didn't had any probs with ff2 on gutsy:(

p dual core 2.0ghz 4gb ram, ati x1300 with ati drivers from the repositories. i did thought it could be the compiz effects that come with gnome that would be doing this, but the same happens without the desktop effects, have you got any extensions?
I've got webdeveloper, delicious, adblock plus, downloadthem all and flashgot, i had all this extensions with ff2, and the crashes are too random. the whole gnome crashes when i click on a link or i just refresh a page, etc. this is driving me nuts,i used e17 for a while and i haven't had any crashes at all with ff3,i think it's something to do with this version of gnome:S.
I'ven't tried to remove this extensions because without them ff has the same use to me as opera:S.
regards

---

### Post by Yellow Pasque on 2008-07-01
Try uninstalling the Ubuntu version of FF and check out Swiftweasel (link in sig). If it does the same thing, then it's the Mozilla code base. If not, then the repo build is at fault.

Also, do you have Flash installed? Flash is still buggy and advertisements used to crash my system. Try a Firefox add-on called Flashblock which replaces Flash content with a play button, so you can decide what content to view (you can also "whitelist" sites to have the content load automatically).

---

### Post by Derviansoul on 2008-07-02
I've got flash 10 installed, from the adobe website, the crashes occur all the time, with or without flash:S, i did thought about it,i've got two more computers at home with ubuntu x64 8.04 at home but it doesn't crash this often:S,i will try to do what u advised me,and hope for the best:s, but the thing is that this only happens with gnome:S on this computer. I used for a few days e17 to check if i the same happenned, but i never had any problems:S.
Thanks for the help i will check it out.

---

### Post by lukjad on 2008-07-02
Also try Seamonkey. It's a faster slicker Firefox and Thunderbird rolled into one.

---

### Post by Derviansoul on 2008-07-02
Hello

just installed swiftweasel, looks better and it's faster to be honest i will let us know, if it still crashes like firefox,but for now i love it and i more people should try it,coz it's faster than firefox 3 to start even with all the extensions.

I will check seamonkey if swiftweasel doesn't work, i don't really like apps like thunderbird i find them a just waste space on the hd.
regards

---

### Post by lukjad on 2008-07-02
Well, I never use Thunderbird but this is still faster that Firefox anyhow.

---

### Post by erkanea on 2008-07-03
actually i also have that firefox crashing gnome problem 2 times, consider system installed yesterday. im getting thrown to console, if i look running processes with "top" i see Gnome is using %100 cpu.

hardware : hp 6910p ----> c2duo 2.0 Ghz, 4 gb RAM, ati x2300
software : hardy 8.04 fully updated, firefox 3.0, flashplugin-nonfree, ati drivers from repo's, compiz

---

### Post by Anzan on 2008-07-03
It's not [just] you. It's me.

---

### Post by Derviansoul on 2008-07-03
Hello everyone,

I've being using swiftweasel for two days now, and i hadn't major problems, besides that it starts allot faster, in 2days i had 1crash but the webpage was using flash.

thanks temujin for the tip.
hope this helps a few more of us.

> **Temüjin said:**
> Try uninstalling the Ubuntu version of FF and check out Swiftweasel (link in sig). If it does the same thing, then it's the Mozilla code base. If not, then the repo build is at fault.




Sorry i didn't understood the comment below, r u trying to correct my english, does it happens to u as well, or....

> **Anzan said:**
> It's not [just] you. It's me.

Sorry if my english isn't the best ones, but if there is a grammatical problem i will try to fix it.



regards

---

### Post by Yellow Pasque on 2008-07-03
> **Derviansoul said:**
> thanks temujin for the tip.
You're welcome. Enjoy the speed :)

> Sorry i didn't understood the comment below, r u trying to correct my english, does it happens to u as well, or....

He is saying that he has the same issue.

---

### Post by DelSol on 2008-07-04
i've got similar issues. it crashes back to the login screen. acutally i dont think ff crashes gnome, i think it crashes x.

---

### Post by studyhard888 on 2008-07-04
> **Derviansoul said:**
> I didn't had any probs with ff2 on gutsy:(

p dual core 2.0ghz 4gb ram, ati x1300 with ati drivers from the repositories. i did thought it could be the compiz effects that come with gnome that would be doing this, but the same happens without the desktop effects, have you got any extensions?
I've got webdeveloper, delicious, adblock plus, downloadthem all and flashgot, i had all this extensions with ff2, and the crashes are too random. the whole gnome crashes when i click on a link or i just refresh a page, etc. this is driving me nuts,i used e17 for a while and i haven't had any crashes at all with ff3,i think it's something to do with this version of gnome:S.
I'ven't tried to remove this extensions because without them ff has the same use to me as opera:S.
regards


I think that type of your ubuntu makes troubles.What type of ubuntu do you download ?? LiveCD or Alternate ?? As far as i know,LiveCD is very unstable.

---

### Post by mikey on 2008-07-04
I've experienced pretty much the same issues with gnome and ff3/splash on hardy and mint 5. I've tried some tweaks like removing nonfree flash package and directly installing the tar.gz from adobe, installing a previous ff, swift, etc. gdm also seemed problematic. often wouldn't load, creating a crash and reboot forever pattern which we can all do without.

I managed to get youtube working but other sites like pandora were problematic. as a lark, I switched to kde and , who would have thunk, but ff3 works like a charm without any tweaking. so here's the simple remedy till someone with greater abilities solves these gnome issues.

amd 64 dual core

---

### Post by terencelhl on 2008-07-04
> **mikey said:**
> I've experienced pretty much the same issues with gnome and ff3/splash on hardy and mint 5. I've tried some tweaks like removing nonfree flash package and directly installing the tar.gz from adobe, installing a previous ff, swift, etc. gdm also seemed problematic. often wouldn't load, creating a crash and reboot forever pattern which we can all do without.

I managed to get youtube working but other sites like pandora were problematic. as a lark, I switched to kde and , who would have thunk, but ff3 works like a charm without any tweaking. so here's the simple remedy till someone with greater abilities solves these gnome issues.

amd 64 dual core

Hi Mikey,

When do you start experiencing these? After installing or upgrading?

Please share.

Thank you.

Regards,

Terence Loo

---

### Post by Derviansoul on 2008-07-04
> **studyhard888 said:**
> I think that type of your ubuntu makes troubles.What type of ubuntu do you download ?? LiveCD or Alternate ?? As far as i know,LiveCD is very unstable.

I used the live cd i didn't bother to use the alternate, but isn't the gnome version the same, with the same gdm?i really don't understand how come an alternate cd can make such a dif, i used before texted based installations on fedora and the normal ones, and i never had a problem or saw any changes.

I really would recommend everyone to download swiftweasel and remove ff3, i'm really happy about it, and i only had i crash until now, and it was related with flash, that's it.

Could everyone that has issues with firefox and hardy x64, post their hardware, and add-ons installed with firefox, maybe we will find common things between everyone,so the developers or ubuntu staff could have a look and report this issue.
regards

---

### Post by mikey on 2008-07-05
hi terence
I only did a fresh install. no upgrading
best
mikey

---

### Post by Yellow Pasque on 2008-07-05
> **studyhard888 said:**
> I think that type of your ubuntu makes troubles.What type of ubuntu do you download ?? LiveCD or Alternate ?? As far as i know,LiveCD is very unstable.
There's nothing on the LiveCD that's different from the Ubuntu code base. It just lacks proprietary video drivers, which is where a lot of people get hung up. Don't start/spread rumors.

---

### Post by DarthPooky on 2008-08-11
it worked and then the next time i tried it crashed firefox.:(:(:(:(

---

### Post by DarthPooky on 2008-08-11
sorry for the double post but i may have found a solution create a google account if you don't already have one and add the pandora player to your igoogle homepage. It works for me.:guitar::lolflag:

---

