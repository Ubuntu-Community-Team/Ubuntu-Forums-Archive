---
title: "No &quot;Programs&quot; launcher in Wine menu"
date: 2008-07-25
forum: Wine
---

### Post by thomasyen on 2008-07-25
Hello,
I have been using Wine for some time now; however, I ran into some problems yesterday. I tried to install Dev-C++ using Wine, and failed (probably because I'd forgotten to install wine-dev). After the failure, I tried using Wine-doors, but failed as well. That's when I noticed (when trying to start a program from Applications -> Wine -> Programs) that the links don't work anymore; all my programs returned "Failure to open '/home/thomasyen/.local/share/applications/wine': permission denied" - or something like that. So I uninstalled Wine and Wine-doors, deleted the .wine folder, reinstalled Wine and Wine-doors. After I reinstalled all my previously installed programs, I found that there was no "Programs" launcher. I know that Wine should normally install with a "Programs" launcher in the menu, but there is none in my case. Can anyone help? (Preferably without having to reinstall the entire system.)

---

### Post by the_hardy_kid on 2008-07-25
I had a similar problem, where my "Programs" sub-menu didn't show up.

I managed to fix this with a new user, but unless one of the mods tell you a better method, don't. It's just a hassle.

Sincerely,
Tyler

---

### Post by thomasyen on 2008-07-25
Do you mean that you switched to using another account? I probably won't try it, since you advised me against it. Thanks though.

---

### Post by thomasyen on 2008-07-26
Anybody else with other suggestions?

---

### Post by mc4man on 2008-07-27
Maybe take a look at this file and see if anything is amiss.

```
cat /etc/xdg/menus/applications-merged/wine.menu
```
 
While I don't see it affecting wine partially there's no harm in deleting .config/menus/applications.menu and restarting. 

fairly useless info
Your individual program menus would be in .config/menus/applications-merged

edit : I'd probably also install a new program and see if anything shows up, maybe look in Other

---

### Post by stinger30au on 2008-07-27
you could try uninstalling it and then reinstall it

---

### Post by thomasyen on 2008-07-31
To mc4man,stinger30au:
Thanks for your replies. I tried uninstalling every program, installing Soldat, and also tried deleting the files mc4man specified. I also looked at the file mc4man mentioned, and there is no entry containing "Soldat". There is now a "Programs" folder in my menu after I deleted the files and installed Soldat; however, there is only the Accessories folder inside, with no Soldat folder. And I have tried uninstalling and reinstalling Wine, without success (there is still no "Soldat" folder). Thanks, though.

Any other suggestions?

---

### Post by Felson on 2008-07-31
"if" creating a new user has the new user work correctly, you could create a new user, delete your ".local" folder (or better, just rename it to ".local_bak") and copy the new users ".local" folder to your home dir. Be sure to fix ownership of the folder and it's contents after you copy it though.

---

### Post by mc4man on 2008-08-01
Not every program you install will create a menu item, most do, some don't.
Assuming you've seen Soldat before and don't mind another fresh start on wine, try this.
Use aptitude instead of apt-get

```
sudo aptitude purge wine
```
After that runs go into home dir. and shift/delete the .wine dir. While in home also go into .config -> menus and if there is an _applications-merged _folder shift/delete that.
Then run ```
sudo aptitude install wine
``` run winecfg, install Soldat and see what you've got.

---

### Post by thomasyen on 2008-08-07
To mc4man:

Thanks for your reply. However, after I did everything you've said, after I reinstalled Soldat, there is still no "Soldat" folder in the "Programs" folder, only "Accessories", in which there is only Notepad. Thanks for your attempt to help, though.

---

### Post by thomasyen on 2008-08-07
To Felson:

Thanks for your suggestion. However, after I created a new user and switched over to it, Soldat still did not show up in the Wine folder. It seems that the idea of creating a new user and switching over to it doesn't apply to every system. Thanks, though.

---

### Post by thomasyen on 2008-08-13
\bump

---

### Post by YokoZar on 2008-08-13
> **thomasyen said:**
> Hello,
I have been using Wine for some time now; however, I ran into some problems yesterday. I tried to install Dev-C++ using Wine, and failed (probably because I'd forgotten to install wine-dev).This shouldn't matter.  Wine-dev is for compiling windows programs against winelib, not for compiling windows applications inside wine using a windows compiler.

> After the failure, I tried using Wine-doors, but failed as well. That's when I noticed (when trying to start a program from Applications -> Wine -> Programs) that the links don't work anymore; all my programs returned "Failure to open '/home/thomasyen/.local/share/applications/wine': permission denied" - or something like that. So I uninstalled Wine and Wine-doors, deleted the .wine folder, reinstalled Wine and Wine-doors.The problem here is you ran something as root (ie with sudo) when you shouldn't have.  That made root the owner to whatever got created in you .local folder (as well as the .wine folder), so your normal user can't access it.

>  After I reinstalled all my previously installed programs, I found that there was no "Programs" launcher. I know that Wine should normally install with a "Programs" launcher in the menu, but there is none in my case. Can anyone help? (Preferably without having to reinstall the entire system.)The programs launcher disappered because Gnome is running as your normal user, and it can't see it either (since it's a root-owned file).


Fix this by resetting your user as the owner of the folder and files: sudo chown -R $USER:$USER ~/.local
sudo chown -R $USER:$USER ~/.wine

---

### Post by thomasyen on 2008-08-20
To YokoZar:
Thanks for your suggestion. However, after I changed the ownership of the folders and rebooted the machine, I still only have the "Accessories" folder available to me, and no "Soldat" folder. Thanks for your time though.

Maybe there's some command to print out (hopefully useful) system information that I can post here? (Maybe something that can print more information than what "top" has to provide.)

---

