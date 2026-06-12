---
title: "File Associations"
date: 2007-07-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by benplanet on 2007-07-01
My file associations are messed up. I noticed this after attempting to get Gdesklets working for about 1 hour! (to no avail)
Anyways, .Deb packages and tars aren't readable anymore. I have to manually select open with specific application. Those 2 extensions seem like the only ones to be  malfunctioning. 

Is there a fix to get the extensions working with the default programs like before??


thanks so much to this great Ub Community!



Update: found another similar thread: [http://ubuntuforums.org/showthread.php?p=2599591](http://ubuntuforums.org/showthread.php?p=2599591)
Basically the same EXACT problem .. all due to Gdesklets. which leads to lose all default file associations for all major applications.

Here are the fixes from ubuntuforums and lunchpad:
"the answer found on ubuntuforums.org: "reinstall the packages
gnome-mime-data, shared-mime-info, and mime-support using synaptic" (thx
ComplexNumber)."

and
"
sudo update-mime-database /usr/share/mime
sudo dpkg-reconfigure shared-mime-info
killall gnome-panel
killall nautilus
" 

Reboot and things should be back to normal!


--------------------------

Could somebody help me with this side issue: now that my default extensions are back to normal, when I double click on a .deb package or a pdf document I get an error message (take a look at screenshots)

[[IMG]http://img253.imageshack.us/img253/8199/screenshotnu3.th.png[/IMG]](http://img253.imageshack.us/my.php?image=screenshotnu3.png)

[[IMG]http://img294.imageshack.us/img294/7959/screenshot2he6.th.png[/IMG]](http://img294.imageshack.us/my.php?image=screenshot2he6.png)

Now, how can i open up my files without having to right-click "open with" ? Ps. I am logged in as root. 


Thanks!!!!

---

### Post by newlinux on 2007-07-01
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_default_file_type_.22Open_with.22_program](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_default_file_type_.22Open_with.22_program)

Should help. You probably want gdebi with .debs and file-roller for .tars

---

### Post by benplanet on 2007-07-02
So in short there is no automatic way to reset file associations? Because now i discovered Mp3s and video files were disassociated as well. 

Doing it manually did not solve it for me, when I double click it still asks me to open with instead of just doing it automatically, even though the default program I set was added to the list. 

Oh well, this is more of an annoyance than anything.... I hope there is another solution **maybe through terminal ?**



Thanks for the reply newlinux!!!

---

### Post by octesian on 2007-07-02
Edit: I found this post in another thread which kinda fixes it.  Its still a little wierd.  

> **felipe82 said:**
> aha! fixed it!

Apparently it's very old bug (like 2 years), I found the bug on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/19101](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/19101)

And after a lot of ranting posts for 2 years someone finally types in the solution:

```
sudo update-mime-database /usr/share/mime
sudo dpkg-reconfigure shared-mime-info
killall gnome-panel
killall nautilus
```

It worked for me.

Someone really need to warn new Ubuntu 7.04 AMD64 users to NEVER install gDesklets (remove from automatix at least, I'll send them an email), it didn't even work, and when I got it to work I realized that there weren't than many desklets out there, so it gave me nothing but these 2 bugs in the end.

Apparently screenlets work better, if you want to give them a try.

thx for all the help ComplexNumber

---

### Post by benplanet on 2007-07-03
Thanks octesian!!! you pointed me to the right direction man!  I fixed my problem but now i have a new one ... 


Does anyone know why I get these error messages now??  [[IMG]http://img253.imageshack.us/img253/8199/screenshotnu3.th.png[/IMG]](http://img253.imageshack.us/my.php?image=screenshotnu3.png)

---

### Post by benplanet on 2007-07-04
bumpy bump!

---

### Post by colo505 on 2007-07-25
Thanks! gDesklets did that to my system too, and you just saved it.

---

### Post by miguelitu on 2007-09-08
to fix the "open with" issue, this worked for me:

delete the .xml file (or move it somewhere, for safety) from ~/.local/share/mime/packages

then do the processes you described again.

hope it works.

---

### Post by phenest on 2007-09-24
Another victim here.

I followed everything here but .iso files still don't work. They open with archive manager when I click on them, but the Properties window shows them as an 'iso document', and 'Write To Disc' no longer shows with the right click.

---

### Post by phenest on 2007-09-25
Please someone help. I'm so close to just reinstalling, but that doesn't explain what is wrong.

---

### Post by phenest on 2007-09-25
Hmmm. Interestingly, I just re-installed. After some updates, I'm back at square one. iso have lost their association and "Write To Disc" is not on the context menu. I did have Feisty-Updates and Feisty-Proposed checked before the update. Any ideas?

---

### Post by phenest on 2007-09-27
Bump

---

### Post by phenest on 2007-09-29
Hmm. Not sure what happened here. Could be something to do with trying to upgrade to Gutsy Beta (unsuccessfully I might add). I deleted all hidden files in my home folder (except for .mozilla and .mozilla-thunderbird), and restarted. Now file associations are back to normal.

---

### Post by s_spiff on 2007-10-08
thank you! this how to saved my installation!!!

---

