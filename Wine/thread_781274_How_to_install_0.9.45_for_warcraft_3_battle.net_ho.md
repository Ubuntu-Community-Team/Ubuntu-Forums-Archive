---
title: "How to: install 0.9.45 for warcraft 3 battle.net hosting in Hardy"
date: 2008-05-04
forum: Wine
---

### Post by zir0n on 2008-05-04
[COLOR="Red"]UPDATE:[/COLOR]I rewrote this "How to" to use wine-1.0-rc1, please refer to the new thread instead, located at...

[http://ubuntuforums.org/showthread.php?t=795714]("http://ubuntuforums.org/showthread.php?t=795714")

So I had this dilemma, everything was working fine in Gutsy. I was able to install wine 0.9.45 which is the last version where you could host games on Battle.net, but when I upgraded to Hardy, I could no longer install 0.9.45 off of [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) where they store the older versions. This is because libldap2 was replaced by libldap-2.4-2 in the Hardy upgrade process. Wine 0.9.45 has a required dependency with libldap2 and there is no way that I know of to downgrade to libldap2 without removing lots of other apps that depend on it. This "How To" will show you how to build your own wine from source and make the necessary changes to work with the new libldap-2.4-2 so you can host games on Battle.net in Hardy and play dota till you drop. 

[COLOR="RoyalBlue"]Step 1:[/COLOR] Make sure to remove your current wine if you have it installed. Bear in mind that some other apps you use wine for might not work in .9.45 as well as war3 will. 

```
sudo apt-get remove wine
```

[COLOR="RoyalBlue"]Step 2:[/COLOR] You will be compiling things in this "How to" so run.

```
sudo apt-get install build-essential
```

if you haven't already. You might need the kernel header files as well, as I had them installed for something else and didn't know if wine used them also.

[COLOR="RoyalBlue"]Step 3:[/COLOR] Download and unzip the wine-0.9.45.tar.bz2 source code from 

[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449) 

[COLOR="RoyalBlue"]Step 4:[/COLOR] Install the build dependencies for wine.

```
sudo apt-get build-dep wine
```

[COLOR="RoyalBlue"]Step 5:[/COLOR] Enter the wine-0.9.45/dlls/wldap32 directory and prepare to edit some code if your shy about that sorta thing.

[COLOR="RoyalBlue"]Step 6:[/COLOR] Use your favorite text editor (emacs,nano,vi,gedit,kate,etc...) to open parse.c

[COLOR="RoyalBlue"]Step 7:[/COLOR] Head to line 339 and rename the function "ldap_parse_sort_control" to "ldap_parse_sortresponse_control"

[COLOR="RoyalBlue"]Step 8:[/COLOR] Head to line 420 and rename the function "ldap_parse_vlv_control" to "ldap_parse_vlvresponse_control" and save the file.

[COLOR="RoyalBlue"]Step 9:[/COLOR] Go back to wine-0.9.45/ and run 

```
./configure
``` 

installing anything you're missing using "apt-get install"

[COLOR="RoyalBlue"]Step 10:[/COLOR] Hopefully you have all your make files made.

```
make depend && make wine
```

[COLOR="RoyalBlue"]Step 11:[/COLOR] Cross you fingers for 30mins-1hr...

[COLOR="RoyalBlue"]Step 12:[/COLOR] If you made it this far, prepare for Warcraft 3 Battle.net heaven and type...

```
sudo make install
```

[COLOR="Red"]*keep the wine-0.9.45 directory if you want to uninstall your built wine using "sudo make uninstall"[/COLOR]

[COLOR="RoyalBlue"]Step 13:[/COLOR] Test your (re)gained game hosting abilities by hosting and playing some DOTA!!!

[COLOR="Red"]**Disclaimer:[/COLOR] This is my first How to, and I know I probably could have combined some steps but I like the number 13, so I hope it helps war3 linux fans. I am not a wine developer, just figured that the new libldap-2.4-2 changed a function name by looking at my compiler errors during the wine build. I myself haven't had any problems with Warcraft 3 and hosting in Battle.net after using this method. If you have problems please reply to this thread and I will try to help you.

---

### Post by shae on 2008-05-05
Everything looks in order, but you might try updating your guide so you can 
build one of the newer ones with the patch that allows you to host.  

The patch can be found here: 
[http://bugs.winehq.org/attachment.cgi?id=8368]("http://bugs.winehq.org/attachment.cgi?id=8368")

---

### Post by Larrxi on 2008-05-15
For latest version of wine change step 5 to 8 to the following:

Step 5: Download [http://bugs.winehq.org/attachment.cgi?id=8368](http://bugs.winehq.org/attachment.cgi?id=8368) and save it as patch.diff in the wine-directory you unzipped.

Step 6: Change to the wine-directory you unzipped.

Step 7: Run the following: patch -p1 < patch.diff

Step 8: Skip this step

Happy hosting in latest Wine!

---

### Post by perfeng702 on 2009-03-29
i got it working. thanks.

---

