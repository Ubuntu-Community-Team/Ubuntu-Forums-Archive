---
title: "What's going on with Wine?"
date: 2007-09-21
forum: Wine
---

### Post by Arukas on 2007-09-21
Hello,


   I use to be able to open Dark Crusade up fine with wine, now I can't.  Instead of playing the video now, it shows "Divx" logo.  Then the next thing I see after the loading screen is a "light blue" screen of death, can anyone help me fix that?


-Arukas

---

### Post by Perfect Storm on 2007-09-21
I'm afraid that's normal with wine. Some thing works in one version but breaks in another, but then something new works.

Don't upgrade wine if the version you have works for the stuff you have.

---

### Post by cogadh on 2007-09-21
You can downgrade to previous version by doing the following:
[LIST=1]
[*]Uninstall Wine like this:
```
sudo apt-get remove --purge wine
```
[*]Download a .deb of the previous version of Wine from here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
[*]Install it (just double click on the downloaded file)
[*]Force that version of Wine in Synaptic (prevents it from updating again). Instructions here: [https://help.ubuntu.com/community/SynapticHowto#head-ec06ac55f7b20957887c4b9cfdea6efd07727415](https://help.ubuntu.com/community/SynapticHowto#head-ec06ac55f7b20957887c4b9cfdea6efd07727415)
[/LIST]

---

### Post by Arukas on 2007-09-21
I had a problem with forceing Synaptic.  The guide says to hit apply, but after I choose the version of Wine I want, the apply button is still greyed out.

-Arukas

---

### Post by cogadh on 2007-09-21
Sorry, I should have said use the lock version option, not the force version option. Just select the installed Wine package, click on the Package menu and select "Lock Version".

---

### Post by Arukas on 2007-09-21
Thanks got Synaptic squarded away.

 I have another question.  I found out Wine 0.3.35 is a good version to run DoW.   I notice that the camera in DoW will not pan all the way in and out like it is suppose to do.  I never installed Direct X or anything, and from what I read I am not suppose too.  

  So is there a way to fix the graphics like that or is that the best Wine can do?

-Arukas

---

### Post by cogadh on 2007-09-21
I hope you meant to type version 0.9.35, not 0.3.35. I can't imagine a Wine version as old as the 0.3.xx series would work at all or would be available for download anywhere.

The game's function in Wine should be no different than what you would find running the game in Windows (note I said *should*). However, I have found that some mouse controls do perform oddly on occasion. Are the camera functions controlled with the mouse scroll wheel, or is there a keyboard function that does the zooming in and out?

---

### Post by Arukas on 2007-09-21
I type the wrong version number you are right.  It funny how the camera zoom works.  I can zoom in and out and move.  But I can't zoom all the way in.  It odd how it working.  ( and I did note you said "should" )

-Arukas

---

### Post by Arukas on 2007-09-21
Figured it out.  I had to fix the ingame settings.  Apparently they changed on me.  So the game works fine.  


Here's another question, do you know how to get the sound to work better?  It don't really bug me, but its getting a little crazy.

-Arukas

---

### Post by cogadh on 2007-09-21
What do you have set for a sound system in Wine?

---

### Post by Arukas on 2007-09-22
I am using the ASL setting, recommending int eh guide i read.

-Arukas

---

### Post by reset3x on 2007-09-22
You can get 9.44 here: [http://www.getdeb.net/category.php?id=11](http://www.getdeb.net/category.php?id=11)

All packed up in deb... I

'm afraid to try if since I have 9.33 running great....

---

### Post by hikaricore on 2007-09-22
reset3x: There's no point in getting WINE throught GetDeb.net that package was submitted to them by someone, and will not be kept up to date.
Instead you should download it here where it is posted a day or so after the biweekly updates: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by ELD on 2007-09-22
You should also submit an reports about something not working in an updated version, someone will get around to fixing it, "regressions" are common and do get fixed.

---

### Post by cogadh on 2007-09-22
> **Arukas said:**
> I am using the ASL setting, recommending int eh guide i read.

-Arukas
Sorrry, I should have asked for more details than that, like bitrate, hardware acceleration setting, sample rate, emulation on/off.

---

### Post by reset3x on 2007-09-23
> **hikaricore said:**
> reset3x: There's no point in getting WINE throught GetDeb.net that package was submitted to them by someone, and will not be kept up to date.
Instead you should download it here where it is posted a day or so after the biweekly updates: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

I stand corrected!! Thanks! Never knew that wine site existed...

Peace!!

---

### Post by reset3x on 2007-09-24
I currently have Wine 0.9.33 installed via Synaptic. If I were to upgrade Wine via the packages here : [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) would it hose the apps I currently have installed?

Thanks in advance....

---

### Post by cogadh on 2007-09-24
Generally speaking, no. There is always the chance that a different version of Wine will have a regression or some other bug that will prevent a previously functional app from working, but more often than not, applications that previously worked will continue to work at least as well as they used to, if not better.

---

### Post by reset3x on 2007-09-24
> **cogadh said:**
> Generally speaking, no. There is always the chance that a different version of Wine will have a regression or some other bug that will prevent a previously functional app from working, but more often than not, applications that previously worked will continue to work at least as well as they used to, if not better.

I'll give it a whirl.. Thanks for replying!!

---

### Post by reset3x on 2007-09-26
> **reset3x said:**
> I'll give it a whirl.. Thanks for replying!!

Wasn't a good idea.. Things broke and I ended up reinstalling via Synaptic... Oh well....

---

### Post by cogadh on 2007-09-26
Yeah, I've been having some problems with the latest Wine myself. The games I run that still work definitely work better, but at least one of my previously working games won't run at all anymore and another has severe issues with stuttering. The next update will likely correct this as I have never had a problem persist for more than one update (so far).

---

### Post by reset3x on 2007-09-26
I'm about to cave in and try Cedega... But it kills me to have to pay to play..... :mad:

---

### Post by cogadh on 2007-09-26
Well, I've posted my opinion of Cedega all over these forums many times, so I won't bore you with yet another rant. Suffice it to say that, in my opinion, Cedega is not worth the expense in any conceivable way.

---

### Post by reset3x on 2007-09-28
> **cogadh said:**
> Well, I've posted my opinion of Cedega all over these forums many times, so I won't bore you with yet another rant. Suffice it to say that, in my opinion, Cedega is not worth the expense in any conceivable way.

Gotcha!!! I'll just keep plugging away... I just can't get around that Registtry in use BS when I try to play STEAM games... I've hit every forum and googled my behind off and tried everything I could find... Registry blob, open - close STEAM, Cache integrity.... Reboot....  No worky.... Only HL2 works.. Episode 1, Lost Coast, CS:S and HL: Source peter out... :confused:

---

### Post by Joe88 on 2007-09-28
> **Artificial Intelligence said:**
> I'm afraid that's normal with wine. Some thing works in one version but breaks in another, but then something new works.

Don't upgrade wine if the version you have works for the stuff you have.

Isn't there a way you can tell wine what emulation engine to use with specific games or can only Cedega do this?

---

### Post by cogadh on 2007-09-28
You can do it, but it requires you to compile each Wine version you wish to use from the source and install them in separate directories. It can't be done using precompiled packages, like those that are available in the repositories.

Oh, and Wine is not an emulator.

---

### Post by bliffle on 2007-09-29
> **cogadh said:**
> You can do it, but it requires you to compile each Wine version you wish to use from the source and install them in separate directories. It can't be done using precompiled packages, like those that are available in the repositories.

....

True. Thanks for the reminder.

---

