---
title: "Help &quot;marking application as executable&quot; for wine"
date: 2011-07-27
forum: Wine
---

### Post by David4321 on 2011-07-27
Hello,

Well, I'm in up to my eyebrows now...

Windows 7 64 is unbootable - maybe hard drive failure - trying to complete updated backup of windows HD before sending computer home for warranty support - what a good time to learn how to run Ubuntu from a CD to access the drive - I always wanted to anyway...

So I got Ubuntu 11.04 64 running, and I have installed wine - so far so good.

Now I am trying to run Syncback SE (my backup program) from my program files (x86) folder. I went to Applications > Wine > Browse C Drive. From there I select my HD C drive from the left hand pane > navigate to the SyncBackSE.exe file > right click > Open with Wine Windows Program Loader > "Blocked: wine start /unix"

So I read about it and try to modify the exe file properties. Right click > Properties > Permissions

Now the kicker: none of the properties can be modified, including "Allow executing file as a program". The box cannot be checked. No matter what I do, properties remains unchanged. (see attached screenshot)

Any suggestions how I can run my backup program in wine, in Ubuntu running from CD, to backup my C Hard Drive to my external backup drive?

Thanks...

---

### Post by amjjawad on 2011-07-27
Hello and Welcome :)

Why you want to run your Backup Program in Wine? even if that will work, I don't recommend to do so.

[http://en.wikipedia.org/wiki/Wine_(software](http://en.wikipedia.org/wiki/Wine_(software))
[http://www.winehq.org/](http://www.winehq.org/)

If you are trying to backup some data, then Copy some files and paste them on an external HDD is all what you really need.

If you are trying to create a clone to your Windows Installation, then please login to Windows and do that.

Good luck :)

---

### Post by David4321 on 2011-07-27
I know I can back up files manually using drag and drop. I want to run my backup program because it has profiles configured which will compare current drive state to last full backup, using selected drive areas and rules, and simply update the existing backup exactly as it should be. I think you can see the value in that.

Then I plan to wipe my drive and attempt reinstalling windows. If it succeeds, then I know I had a software problem behind the crash, but all my data is preserved. If it fails, then I know I had a hardware problem, and the computer goes back to ASUS, but my personal data has been made inaccessible to the support center staff. (Currently there is no password on Windows, and sensitive data would be exposed if I send the HD as-is.

So, is there any way to run my backup program from Wine? This would be the best fail-safe way to be sure I get the backup the way I need it to be.

Thanks

To Clarify: I cannot log into windows. System is completely unbootable. I am not sure if this is a hardware or a software problem. That is why I am using Ubuntu today, for the first time. I am running it from DVD to access my HD for backup purposes. I cannot physically remove the HD, because the torturer at ASUS who designed my computer made the RAM and HD user-inaccessible. There are no screws on the bottom, and it will void my warranty to open it myself. SO much for their top of the line multi-media system... I love everything else about it...

---

### Post by amjjawad on 2011-07-27
> **David4321 said:**
> I know I can back up files manually using drag and drop. I want to run my backup program because it has profiles configured which will compare current drive state to last full backup, using selected drive areas and rules, and simply update the existing backup exactly as it should be. I think you can see the value in that.

Then I plan to wipe my drive and attempt reinstalling windows. If it succeeds, then I know I had a software problem behind the crash, but all my data is preserved. If it fails, then I know I had a hardware problem, and the computer goes back to ASUS, but my personal data has been made inaccessible to the support center staff. (Currently there is no password on Windows, and sensitive data would be exposed if I send the HD as-is.

So, is there any way to run my backup program from Wine? This would be the best fail-safe way to be sure I get the backup the way I need it to be.

Thanks

Are you able to login to Windows?
If yes, then please do and check your backup program or do whatever you want while you are logging to Windows.

I know exactly what you mean but your approach in my humble personal opinion is not correct :)

---

### Post by David4321 on 2011-07-27
To Clarify: I cannot log into windows. System is completely unbootable. I  am not sure if this is a hardware or a software problem. That is why I  am using Ubuntu today, for the first time. I am running it from DVD to  access my HD for backup purposes. I cannot physically remove the HD,  because the torturer at ASUS who designed my computer made the RAM and  HD user-inaccessible. There are no screws on the bottom,  and it will void my warranty to open it myself. SO much for their top  of the line multi-media system... I love everything else about it...

---

### Post by amjjawad on 2011-07-27
> **David4321 said:**
> To Clarify: I cannot log into windows. System is completely unbootable. I  am not sure if this is a hardware or a software problem. That is why I  am using Ubuntu today, for the first time. I am running it from DVD to  access my HD for backup purposes. I cannot physically remove the HD,  because the torturer at ASUS who designed my computer made the RAM and  HD user-inaccessible. There are no screws on the bottom,  and it will void my warranty to open it myself. SO much for their top  of the line multi-media system... I love everything else about it...

Ok we need to slow down and take it step by step, ok? good :)

First of all, when anything goes wrong, you need to check your Software before you assume there is something wrong in your Hardware UNLESS there is something so obvious that will clearly show it's a Hardware issue.

After checking your Software, you can check later your Hardware that in most cases, you need a Software to do that job ;)

Now, if you can not boot or login to Windows, then please tell us whether you can still access your Windows Partition(s) while you are logged in to Ubuntu?

If yes, I suggest to backup your important data. Better to do that to an external HDD.


Now, if you are trying to get Windows up and running again, there is a step we can do to make sure you'll be able to use Windows as before.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

ALL the instructions you need are inside that link :)


If you don't need Windows and you just need your files, then after backup, you can format Windows and allocate that HDD space to Ubuntu.

There are many approaches and solutions but we need to know what are you planning? Keep Windows? or get rid of it after backing up your files?

---

### Post by Elfy on 2011-07-27
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=21953](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21953)

> Before Installation it's necessary to set Wine to Windows 98 Version, it can be re-set to Windows XP after the install is complete...

You can set the executable bit with this command

```
sudo chmod +x /path/to/file
```

Obviously change the path to match - if it's on your desktop then ~/Desktop/file

You can also use tab complete - start the path - hit tab

Linux is case sensitive - desktop is not the same as Desktop

---

### Post by Elfy on 2011-07-27
Thread moved to Wine.

---

### Post by David4321 on 2011-07-27
a) I cannot check my windows OS: I cannot boot at all. I plan to backup > then reinstall windows. If it boots, all is well. If not, back to ASUS with it.

b) My windows partitions are available in Ubuntu.

c) I have done some critical backups since last post - but I still want to run SyncBackSE to do a full backup. (of course to external drive)

d) I have no plans to switch primary OS to Ubuntu at this time.

e) I have rebooted (to Ubuntu on DVD) and it appears I have to reinstall Wine. (nothing Linux related is on HD yet)

f) I do not understand anything forestpiskie said. I am an advanced Windows user, and this is my first time using any Linux software.

Anyone know what it will take to run my backup from my HD to my external Seagate GoFlex, using my backup profiles in SyncBackSE, run using Wine (stable version) in Ubuntu 11.04 from DVD boot?

When I use right click to open program with Wine Windows Program Loader I get "Blocked: wine start /unix". As mentioned above, the box cannot be checked for  "Allow executing file as a program" in properties - none of the properties can be modified for SyncBackSE.exe (the backup program) I am accessing it through Wine, not directly. 

I get the same result when I try to run the installer for SyncBackSE - "allow executing file as program" cannot be checked - it immediately deselects when I try.

Merci Beaucoup

Edit: OK, progress. I moved the installer to the desktop, and was able to change properties and install it. It has errors, but seems to be running. I cannot make it create a new profile - I actually want to provide it with my existing profiles. They normally live in my windows AppData folder. Where is the analagous location in Linux, where can I copy my backup profiles from AppData to so the program can use them?

I installed Wine using XP settings as advised above. My program is a current version I have been using with Win7 and Vista. Could this cause problems?

Alternately, is there a straightforward way to network Ubuntu with my working Vista computer? I could run the backup from there, if I can use Ubuntu to get my Win7 HD visible on the Vista system.

---

### Post by amjjawad on 2011-07-27
> **David4321 said:**
> a) I cannot check my windows OS: I cannot boot at all. 

I already offered my help and asked you to run the Boot Script and post the result here (as explained inside that link in my previous post) but it seems you ignored that :)
I'm trying to find out WHY you can't boot into Windows? maybe we can help without the need to re-install Windows!

> I plan to backup > then reinstall windows. If it boots, all is well. If not, back to ASUS with it.

Is this a laptop or a PC?
Do you have a restore partition? what do you get when you turn your machine one? 

> b) My windows partitions are available in Ubuntu.

That is good to know.

> c) I have done some critical backups since last post - but I still want to run SyncBackSE to do a full backup. (of course to external drive)
I have read your first post.
Are you trying to access your program "SyncBackSE" which is installed in C: Drive inside Programs Files? Have you considered to re-install that program?

If I understood your post correctly, you are trying to access an already installed program. As far as I know, you can't do that even if you are dual booting two Windows Versions ***(trying to access a program installed in OS1 from OS2 without installing the same program on OS2)*** and I have no clue whatsoever whether it's possible with Wine or not?! perhaps someone else could help here?!

> d) I have no plans to switch primary OS to Ubuntu at this time.

OK :)

> e) I have rebooted (to Ubuntu on DVD) and it appears I have to reinstall Wine. (nothing Linux related is on HD yet)
Does it mean you did NOT install Ubuntu yet? I'm confused now. Can you please explain that clearly?
I have read your posts again but still confused!


> f) I do not understand anything forestpiskie said. I am an advanced Windows user, and this is my first time using any Linux software.
I have never used Wine and not planning to.
However, many will help you here even if you are new user to Linux ;)

> **Anyone know what it will take to run my backup from my HD to my external Seagate GoFlex, using my backup profiles in SyncBackSE, run using Wine (stable version) in _Ubuntu 11.04 from DVD boot?_**
I hope someone else with more experience can offer some help!

I don't think it's possible if you ask me but that's ONLY me. Again, hope someone else could offer a better advice.
Apparently, you did NOT install Ubuntu yet. However, it's good to confirm that, please!

---

### Post by amjjawad on 2011-07-27
> **David4321 said:**
> Edit: OK, progress. I moved the installer to the desktop, and was able to change properties and install it. It has errors, but seems to be running. I cannot make it create a new profile - I actually want to provide it with my existing profiles. They normally live in my windows AppData folder. Where is the analagous location in Linux, where can I copy my backup profiles from AppData to so the program can use them?

I installed Wine using XP settings as advised above. My program is a current version I have been using with Win7 and Vista. Could this cause problems?

Alternately, is there a straightforward way to network Ubuntu with my working Vista computer? I could run the backup from there, if I can use Ubuntu to get my Win7 HD visible on the Vista system.

If you have broken Windows and you can NOT even login to it, how do you expect to run a program which is installed in non-bootable Windows from Ubuntu LiveCD using Wine?

I just don't get it ... totally non sense, sorry!

---

### Post by David4321 on 2011-07-27
> **amjjawad said:**
> I already offered my help and asked you to run the Boot Script and post the result here (as explained inside that link in my previous post) but it seems you ignored that :)
I'm trying to find out WHY you can't boot into Windows? maybe we can help without the need to re-install Windows!

Please don't try to troubleshoot my Windows problem. It is severe, and no boot is available in the present condition, not even to safe mode.

I ignored your Boot Script suggestion because I have no idea what you are talking about. I am an advanced windows user, but not a programmer, and this is my first experience with Linux. I am clueless about that suggestion...

> **amjjawad said:**
> Is this a laptop or a PC?
Do you have a restore partition? what do you get when you turn your machine on? 

It is a laptop. I just need to back up, then attempt complete Windows reinstall. I already know that much.

> **amjjawad said:**
> If I understood your post correctly, you are trying to access an already installed program. As far as I know, you can't do that even if you are dual booting two Windows Versions ***(trying to access a program installed in OS1 from OS2 without installing the same program on OS2)*** and I have no clue whatsoever whether it's possible with Wine or not?! perhaps someone else could help here?!

I now understand that error - I have now installed SyncBackSE in Ubuntu. See my last post.

> **amjjawad said:**
> Does it mean you did NOT install Ubuntu yet? I'm confused now. Can you please explain that clearly?
I have read your posts again but still confused!

I have not installed - I am running from DVD. I do not trust the HD, that is why I am down this road to begin with. I suppose I could try installing Ubuntu - my data seems intact, even though bootup is hopeless.

> **amjjawad said:**
> I hope someone else with more experience can offer some help!

Me too... ;)  Thanks for your efforts.

---

### Post by David4321 on 2011-07-27
> **amjjawad said:**
> If you have broken Windows and you can NOT even login to it, how do you expect to run a program which is installed in non-bootable Windows from Ubuntu LiveCD using Wine?

I just don't get it ... totally non sense, sorry!

That's a bit rude - I have NO EXPERIENCE with a dual boot scenario whatsoever. Please reread my post you just quoted and you will see that by now I have figured out by myself (no one mentioned it to me) that I have to install it in Ubuntu - and have done so. 

I can access any data on the drive - I just cannot boot to it.

---

### Post by amjjawad on 2011-07-27
> **David4321 said:**
> Me too... ;)  Thanks for your efforts.

Good luck with that and please don't thank me, it's a pleasure to help people here :)

---

### Post by amjjawad on 2011-07-27
> **David4321 said:**
> That's a bit rude 

My apology, I did not mean anything bad. Please don't be offended :)

Good luck again with that!

---

### Post by David4321 on 2011-07-27
OK, I guess you are washing your hands of it. Anyone else?

1) Where in Ubuntu do I install files from AppData that my program needs?

2) What's a Boot Script, do I need to know how to use it, could that help my issues?

3) My program has run well in Vista and Win7, will there be a problem running it in Wine with XP settings? Can it even run without Ubuntu installed? (I am running from DVD)

4) Is there a straightforward way to network Ubuntu with my working Vista laptop? I could run the backup program from there, if I can use Ubuntu to get  my Win7 HD visible on the Vista system.

Recap from above: 
a) I want to run my own backup program to backup from HD to external drive, using Wine. 
b) I can access all files on my drive partitions in Ubuntu. 
c) There is NO WAY to boot to my Win7 OS, not even in safe mode - something is seriously wrong. 
d) I just want to do the backup, then try reinstalling windows. 
e) I cannot remove my HD from computer. This will void warranty, as case has no screws for user servicing of HD & RAM   : - (
f) I am going to sleep now, and I will try to install Ubuntu to a new partition tomorrow.

Thanks for all replies.

---

### Post by disabledaccount on 2011-07-27
> **David4321 said:**
> 
3) My program has run well in Vista and Win7, will there be a problem running it in Wine with XP settings? Can it even run without Ubuntu installed? (I am running from DVD)

4) Is there a straightforward way to network Ubuntu with my working Vista laptop? I could run the backup program from there, if I can use Ubuntu to get  my Win7 HD visible on the Vista system.

Recap from above: 
a) I want to run my own backup program to backup from HD to external drive, using Wine. 
b) I can access all files on my drive partitions in Ubuntu. 
c) There is NO WAY to boot to my Win7 OS, not even in safe mode - something is seriously wrong. 
d) I just want to do the backup, then try reinstalling windows. 
e) I cannot remove my HD from computer. This will void warranty, as case has no screws for user servicing of HD & RAM   : - (
f) I am going to sleep now, and I will try to install Ubuntu to a new partition tomorrow.

Thanks for all replies.
3. Wine is experimental project - don't expect that it will run every Windows app without problems / crashes / bugs. If Your data is so important, then just make a copy (eventually compressed) because this is most safe way. Besides, if You want to use already installed program You have to copy it's folder to separate wine location, because NTFS permissions are not supported under wine (that's why You can't make Your program executable). But in this case most probably it won't solve all problems because installed software usually needs proper registry entries to work.
You can try to install Syncback SE under wine, but again - results are not predictable.

4. CIFS/Samba client is available on LiveCD, so You may try it. But does it differ from copying? (it will be slower - that's for sure).

c) If it happened after bigger portion of updates, then it's nothing especially strange - but before reinstalling I would check HDD's SMART and RAM

---

### Post by David4321 on 2011-07-28
[B]1) Where in Ubuntu do I install files from AppData that my program needs?
 [/B]
I Really need to know this in order to place my backup profiles where SyncBackSE can find them when running in Wine.

> **tomazzi said:**
> 3. Wine is experimental project - don't expect that it will run every Windows app without problems / crashes / bugs. If Your data is so important, then just make a copy (eventually compressed) because this is most safe way. Besides, if You want to use already installed program You have to copy it's folder to separate wine location, because NTFS permissions are not supported under wine (that's why You can't make Your program executable). But in this case most probably it won't solve all problems because installed software usually needs proper registry entries to work.
You can try to install Syncback SE under wine, but again - results are not predictable.

I am TRYING to back up my data. Using my usual backup program is the only way I know to update my incremental backup and be sure it is complete, without counting bits for every folder. 

> **tomazzi said:**
> 4. CIFS/Samba client is available on LiveCD, so You may try it. But does it differ from copying? (it will be slower - that's for sure).

I am only thinking that if I can enable sharing, I could run backup from Vista machine. I don't know if this may be easier than getting SyncBackSE to run in Wine.

> **tomazzi said:**
> c) If it happened after bigger portion of updates, then it's nothing especially strange - but before reinstalling I would check HDD's SMART and RAM

See attached screenshot. I don't know how to interpret this. Certainly I'm not comfortable attempting any repartitioning before my full backup is secure.

Thanks

---

### Post by David4321 on 2011-07-28
New result: I got SyncBackSE to install and run in Wine. It did not display any drives or partitions outside of Ubuntu C and Z drives. I created a test profile anyway, and it failed. I am giving up on this method.

I would like to try networking Vista with Ubuntu. What is critical is that the Vista machine be able to access the entirety of the unbootable HD in the Win7 machine which is running Ubuntu LiveCD. This HD has 2 partitions, C and D. (on disk utility scan above)

I can open network in Ubuntu, and I see an object labelled the same as the Vista  computer. I can open it and see 3 folders: Admin$, C$, and D$ - these  are not shared folders on the Vista system to my knowledge. When I open  Network on Vista, I do not see any external objects.

1) Will Samba client allow Vista to view entirety of 2 Windows 7 HD partitions?
2) How to configure this?
3) Can you recommend a good quick-start tutorial?

Any suggestions appreciated.

---

### Post by disabledaccount on 2011-07-28
Here is the page You should start with:
[https://help.ubuntu.com/community/Samba/SambaClientGuide](https://help.ubuntu.com/community/Samba/SambaClientGuide)

And about Your HDD:
I'm surprised that in age of win7 ASUS made such huge mistake with partitioning - what a shame - but this is not source of the problem. SMART is reporting bad sectors - You can click "SMART data" to see what is the scale of damage (sometimes SMART shows false alerts and this can be checked by looking on details)

---

### Post by PayPaul on 2011-10-12
> **David4321 said:**
> Please don't try to troubleshoot my Windows problem. It is severe, and no boot is available in the present condition, not even to safe mode.

It is a laptop. I just need to back up, then attempt complete Windows reinstall. I already know that much.



I now understand that error - I have now installed SyncBackSE in Ubuntu. See my last post.



I have not installed - I am running from DVD. I do not trust the HD, that is why I am down this road to begin with. I suppose I could try installing Ubuntu - my data seems intact, even though bootup is hopeless.



Me too... ;)  Thanks for your efforts.
I have a similar problem to yours. My Windows install (the second install after the first one fell apart) has sporadic startup problems. It too, does a stall in Safe Mode as well. It is, if I suspect correctly, a slight problem with the main HD but I believe my reinstalling Win7 on a completely clean formatted partition may very well do the trick. You may want to look into a HD diagnostic program. There is one in Ubuntu that actually found a couple of bad sectors on my HD. That would be the first thing I'd do. Check with the manufacturers website for the drive and see if they have any diagnostic and/or repair tools for that drive.

In the end it is best to do a clean install of windows on a reformatted partition or reformat the entire drive. There's bound to be garbage lying around the drive that a simple reinstall of Windows won't get rid of. It's good to have another OS such as Ubuntu around. I find that glitches get taken care of much easier with it especially when one uses the terminal for commands, debugging modes and to completely Kill badly behaving programs and packages. 

If you are totally sure that HD of yours is DOA can you obtain or do have another drive to install Windows and Ubuntu on? In the end clean installs are what you want. The DVD, even in persistence mode, can only provide you with so much functionality. Persistence mode, I believe is done by pressing F6 when you click on the "try ubuntu" button. I would never rely upon it for long term usage.

---

