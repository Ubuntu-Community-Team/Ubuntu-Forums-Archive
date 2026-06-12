---
title: "Play Warcraft 3"
date: 2007-12-04
forum: Wine
---

### Post by dethredic on 2007-12-04
Is there any way to see / watch replays?

[Look here]("http://ubuntuforums.org/showthread.php?p=3912071#post3912071")

---

### Post by nille on 2007-12-04
The best way is the follow the instructions found in WineHQs AppDb:
[http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)

To run an .exe-fil you just do like this:
**wine file.exe**

Or right-click and make sure .exe-files are opened with Wine.

Good luck!

---

### Post by dethredic on 2007-12-04
Ok, it seemed to install fine, but when I start it up, I get a blank screen, and nothing happens.

---

### Post by dethredic on 2007-12-04
Ok, I got it to start up, but because I have two screnes, it thought of them as 1, and stretched it really wide. Also the resolutions are different, so the bottom of part of it got cut off. 

Can I just have it run on 1 screen?

---

### Post by nille on 2007-12-05
I'm not sure how you have set up your X-screens (Xinerama? Twinview?), so I'm not sure I can help you with that. Try to disable Xinerama, if it's enabled.

Perhaps this guide is helpful? (I know it's at the Gentoo-wiki)
[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

But I know that the following keys in **regedit** could be relevant for resolution-tweaking:
**HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft III\Video** and then the **resheight** and **reswidth** values.

---

### Post by dethredic on 2007-12-05
I am currently in twin view

---

### Post by justagamer on 2007-12-05
I have a question involving this subject i have ubuntu 7.10 running warcraft TFT under wine it works fine. I was just wondering if there is a way to run the game in it's own window rather then having it full screen?

---

### Post by dethredic on 2007-12-05
Not sure, if this will work, but it works in windows.

Rightclick->Properties->Launcher Tab-> command, and add a *space*-windowed

---

### Post by justagamer on 2007-12-05
Thank you it worked :)

---

### Post by dethredic on 2007-12-05
no problem, glad I could help!

BTW: Does anyone know if replays work?

---

### Post by dethredic on 2007-12-06
Now I can't connect to battle net. I just hang on the initiating connection to battle net.

Any ideas?

---

### Post by Vinno on 2007-12-06
Havent had time to try it on ubuntu yet but tried it on fedora 8, same problem, cant connect to battlenet.

---

### Post by dethredic on 2007-12-07
That is weird, I had this working before.

I guess I will just have to switch partitions to play.

---

### Post by Necromundi on 2007-12-07
I have the same problem, wc3 tries to connect to battlenet but it never gets contact.

Before i updated my ubuntu it worked flawless, but ever since i updated it fails to connect. 
Could it be something wrong in the last update of ubuntu and/or wine?

---

### Post by Echow on 2007-12-07
Try updating to .9.50 at [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
If that doesnt work you might have to return to the fiesty build (pre .9.46) There is a bug with .9.46>.9.49 with battlenet.

---

### Post by panaretos22 on 2007-12-07
ok thanx a lot is worked fine for me:) Thanx a lot again

---

### Post by dethredic on 2007-12-07
Worked great for me as well. I jut followed the "get the latest Wine" instructions!

---

### Post by dethredic on 2007-12-07
Ok, is there any way to open/watch replays?

---

### Post by dethredic on 2007-12-08
anyone?

---

### Post by UpinSmoke:D on 2011-03-14
i  instaled war3 roc and war3 tft patched with 1.24e patch ...i can start   game without problems ...but when i install eaurobattle.net patch and   start loader i get this message :


 
There was an error patching war3.exe(Unable to read memory) .Make sure you are using version 1.22a-1.23a.


pls help me reinstalled 3 times and tried so many thing noone helped ...thx in advance
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=10559853") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=10559853")

---

