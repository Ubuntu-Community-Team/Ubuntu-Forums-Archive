---
title: "Oblivion"
date: 2012-12-15
forum: Wine
---

### Post by Beardedturtle on 2012-12-15
This guide is rubbish [http://www.uesp.net/wiki/Oblivion:Linux#Installing_Oblivion](http://www.uesp.net/wiki/Oblivion:Linux#Installing_Oblivion) is there any new guides out there?
Got this error through Wine and Playonlinux
Error Code:    -5006 : 0x8000ffff
Error Information:
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\ObjectHolder.cpp (442)
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (520)
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (520)
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (520)
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (520)
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (520)
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (520)
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (520)
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (520)
>Kernel\ServiceProvider.cpp (109)
>Kernel\ServiceProvider.cpp (87)
>Kernel\FileGroup.cpp (520)
>Kernel\ServiceProvider.cpp (109)
>Kern>SetupDLL\SetupDLL.cpp (1284)
PAPP:Oblivion
PVENDOR:Bethesda Softworks ([http://www.bethsoft.com](http://www.bethsoft.com))
PGUID:35CB6715-41F8-4F99-8881-6FC75BF054B0
$11.0.0.28844
@Windows XP Service Pack 3 (2600) BT_OTHER 20783.31683

---

### Post by oldrocker99 on 2012-12-16
PlayOnLinux has an Oblivion install script which is most likely up to date. I haven't attempted using it, but it would be worth a try.

---

### Post by Beardedturtle on 2012-12-16
> **oldrocker99 said:**
> PlayOnLinux has an Oblivion install script which is most likely up to date. I haven't attempted using it, but it would be worth a try.
 

It will install it half way then stop saying it cannot be installed unpatched how the Hell can I patch a non existent game.....

---

### Post by howefield on 2012-12-16
Thread moved to the "*Wine*" forum.

---

### Post by xREDEMPTIONx on 2012-12-17
I installed Oblivion with Playonlinux without the install script. Just go to  -configure- and create a new drive. Once created run the installer in that drive. I think the only package I installed in the drive was d3dx9. Set GLSL to enabled and set your video memory size and you should be good to go. Runs and plays perfect. This is on latest Playonlinux and wine 1.5.19.

---

### Post by Beardedturtle on 2012-12-17
> **xREDEMPTIONx said:**
> I installed Oblivion with Playonlinux without the install script. Just go to  -configure- and create a new drive. Once created run the installer in that drive. I think the only package I installed in the drive was d3dx9. Set GLSL to enabled and set your video memory size and you should be good to go. Runs and plays perfect. This is on latest Playonlinux and wine 1.5.19.

Feature Transfer Error #2147418113 Every time...

---

### Post by Beardedturtle on 2012-12-17
Error in POL_Shortcut
Binary not found: OblivionLauncher.exe
Have you installed the program to the default location?

Next page:

If you do not have the Shivering Isles disc please update to the latest patch and try again.

---

### Post by xREDEMPTIONx on 2012-12-17
I never got any errors like that, strange. If you have a windows partition you could always install the game there and then copy it over to a new drive in Playonlinux. I have done that with quite a few of my games with success. You will have to manually add some registry entries for the install dir etc. I found those with a google search. Have you also tried the playonlinux forums? There might be somebody there with some knowledge of the errors you are seeing.

---

### Post by Beardedturtle on 2012-12-18
> **xREDEMPTIONx said:**
> I never got any errors like that, strange. If you have a windows partition you could always install the game there and then copy it over to a new drive in Playonlinux. I have done that with quite a few of my games with success. You will have to manually add some registry entries for the install dir etc. I found those with a google search. Have you also tried the playonlinux forums? There might be somebody there with some knowledge of the errors you are seeing.
 
How about virtualbox? Install Win. 7 on it....just a thought but idk if it works I installed Fedora 17 on it and refuses to recognize my HDTV Ubuntu had no problems...maybe it is a VB issue.

---

### Post by xREDEMPTIONx on 2012-12-19
I don't see why that wouldn't work. Install the game on windows7 in virtualbox and then copy it over to playonlinux. Have you tried the Playonlinux or wine forums for more information on your errors?

---

### Post by Beardedturtle on 2012-12-23
> **xREDEMPTIONx said:**
> I don't see why that wouldn't work. Install the game on windows7 in virtualbox and then copy it over to playonlinux. Have you tried the Playonlinux or wine forums for more information on your errors?


I gave up WINE causes my pc to lag it will take 1,8Gb out of 8Gb of memory and my CPU usage during wine or steam usage is 19% on all 4 cores--19% 19% 19% 19% so screw it.

---

### Post by Beardedturtle on 2012-12-23
Got Win 7 installed time to tinker with it.....

---

### Post by Beardedturtle on 2012-12-23
Windows cannot read the disc but Linux can?? Screw it

---

### Post by sffvba[e0rt on 2012-12-23
Please refrain from making multiple posts in such short succession after each other.  If you want to add anything relevant to your posts you can edit a post and add the information.

All of your ranting is not helping you solve your problem.

Have you done as mentioned earlier and checked the Wine-HQ site and/or the Play on Linux site to find more information on the error messages you are getting?


404

---

### Post by Beardedturtle on 2012-12-23
> **not found said:**
> Please refrain from making multiple posts in such short succession after each other.  If you want to add anything relevant to your posts you can edit a post and add the information.

All of your ranting is not helping you solve your problem.

Have you done as mentioned earlier and checked the Wine-HQ site and/or the Play on Linux site to find more information on the error messages you are getting?


404

Nothing works so to Hell with it I give up until someone ports it over to Linux. Uninstalling POL now.

---

### Post by Beardedturtle on 2012-12-24
> **Beardedturtle said:**
> Nothing works so to Hell with it I give up until someone ports it over to Linux. Uninstalling POL now.
oblivion install completed, but installed file /home/bearded/.local/share/wineprefixes/oblivion/dosdevices/c:/Program Files (x86)/Bethesda Softworks/Oblivion/Oblivion.exe not found

---

### Post by xREDEMPTIONx on 2012-12-24
The actual installed game path and the registry entry probably do not match. Did you change the default install path for some reason? Run Registry Editor in the Oblivion drive and make sure this key is correct.

-HKEY_LOCAL_MACHINE
  -Software
    -Bethesda Softworks
       -Oblivion                                    (string) Installed Path                     Your Install Path Here

---

### Post by Beardedturtle on 2012-12-25
> **xREDEMPTIONx said:**
> The actual installed game path and the registry entry probably do not match. Did you change the default install path for some reason? Run Registry Editor in the Oblivion drive and make sure this key is correct.

-HKEY_LOCAL_MACHINE
  -Software
    -Bethesda Softworks
       -Oblivion                                    (string) Installed Path                     Your Install Path Here

I will try again in a few days. =)

---

### Post by Beardedturtle on 2012-12-30
> **xREDEMPTIONx said:**
> The actual installed game path and the registry entry probably do not match. Did you change the default install path for some reason? Run Registry Editor in the Oblivion drive and make sure this key is correct.

-HKEY_LOCAL_MACHINE
  -Software
    -Bethesda Softworks
       -Oblivion                                    (string) Installed Path                     Your Install Path Here

Oblivion is still giving file transfer errors and hard crashing Virtualbox I give up,

---

