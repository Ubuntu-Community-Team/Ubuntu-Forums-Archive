---
title: "Wine very slow performance"
date: 2008-08-22
forum: Wine
---

### Post by abcuser on 2008-08-22
Hi,
in Ubuntu 8.04 I have installed several applications under Wine 1.0. All applications are working well, but performance is very very slow. For instance one application on Windows XP on the same! hardware starts up in half a second. The same application starts up in Wine in 18 seconds.

Also MS-Word and MS-Excell are running very very slow. I am used to type with 10-fingers so I am typing very fast, but characters are displaying after 10 seconds on screen, so working with application is very time consuming.

Is there any thing I should set under Wine to dramatically speed up Wine applications?
Thanks,
Abcuser

---

### Post by donovajf on 2009-10-27
I see no one has replied but did you ever find out what the issue was and how to correct? I am encountering the same right now.

---

### Post by lithmariel on 2009-10-27
Here too.

---

### Post by unidentified on 2009-10-28
> **abcuser said:**
> Hi,
in Ubuntu 8.04 I have installed several applications under Wine 1.0. All applications are working well, but performance is very very slow. For instance one application on Windows XP on the same! hardware starts up in half a second. The same application starts up in Wine in 18 seconds.

Also MS-Word and MS-Excell are running very very slow. I am used to type with 10-fingers so I am typing very fast, but characters are displaying after 10 seconds on screen, so working with application is very time consuming.

Is there any thing I should set under Wine to dramatically speed up Wine applications?
Thanks,
Abcuser
This happens with some apps, (e.g. / i.e. Adobe PS CS3, MSO 2007 and so on). I believe Wine run games and apps at full speed or even faster than Windows.

Source(s):
Personal Experience.

---

### Post by Soulcage on 2009-10-28
Upgrade to wine 1.1.32 it might help, if nothing else it's the version you're supposed to use.

---

### Post by donovajf on 2009-10-28
I have wine-1.1.27 which the latest one the Ubuntu package manager lists: *wine-1.1.27~winehq0~ubuntu~8.04~0ubuntu1*. 
I'd rather not go outside the Ubuntu tested versions. I have had some issues whenever I've done that. FYI: it took 30 seconds for the Wine Configuration tool to come up.

---

### Post by lithmariel on 2009-10-28
My wine is all messed up, and its very very very slow compared to windows on everything I tested out (if I ever got them working), it don't even show text on its configuration windows, and I got 1.1.32 already (and reinstaled it 2 or 3 times, for that matter)

---

### Post by regor210 on 2009-10-28
I have had much better performance using Wine with a 64 bit processor. Most Programs work better using wine than in there native Windows. Setup has been a problem but once the game or &#65279;application is up and working performance has been grate.   

You could try going to System>Administration>System Monitor and ckick on the Resources tab.
Look at Swap. Hopefully its showing 0 bytes.

Now start the Wine program that is giving you trouble. You may need to goto configure Wine 1st and click on the Graphics tab and check the "Emulat a vitual desktop" check box. Don't forget to uncheck it after are test.

Now look at Swap. If Swap is bing used this could explain why your program is running so slow. Also look at CPU and regular memory use. 

Maybe you just need a little more memory?

---

### Post by donovajf on 2009-10-28
I have 4 processors Intel Core2 Quad CPU Q8200 @2.33GHz each and 3.0 GiB memory. I think that is enough to run Wine.  The SWAP seems to be at a constant 1.3% or 38.9MiB. It doesn't go up when kicking off Wine apps. As a matter of fact, when I start WoW (which is my biggest resource hog) all other resources go up but SWAP stays flat lined.

Are there some Wine logs to look at?

---

### Post by regor210 on 2009-10-28
abcuser's 10 &#65279;second lag made me think of a possible Swap issue. WoW on the other hand is a hole new can of worms. I have never used WoW but I know it can be a bit tricky to get it up and running right. There is a WoW thread here  

[http://ubuntuforums.org/showthread.php?t=579378&highlight=wow&page=206](http://ubuntuforums.org/showthread.php?t=579378&highlight=wow&page=206)

As you can see its 206 pages long. If it were me I would try starting the game in Terminal to see what kind of errors pop up. Here's how.

If you have a WoW desktop icon you can right click on it and copy everything in the command box then paste it in Terminal. You find under Application>Accessories> Terminal. Start the game and shut it down to see what's going on.

If you do not have An Icon you could do the same by right clicking Applications then Edit Menus to find the start command. You must be careful not to make changes to anything under Menus.

You can post the output in the WoW thread for help.  

PS. Nice hardware!

---

### Post by donovajf on 2009-10-29
recor210, I used your advise of running Wine apps in a terminal & no matter which I run, the common error & outputs are:

[B]```
Warning: could not find DOS drive for current working directory '/home/myhome', starting in the Windows directory.
err:process:__wine_kernel_init boot event wait timed out
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM motherbd
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM motherbd
```[/B]

Any insights?

---

