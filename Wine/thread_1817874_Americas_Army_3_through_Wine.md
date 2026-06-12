---
title: "Americas Army 3 through Wine"
date: 2011-08-03
forum: Wine
---

### Post by freshmeat20 on 2011-08-03
Got AA3 installed through steam but I have no control over the main menu or the mouse. Wondering what could be causing this?

Edit: I found this [http://www.wtfm.org/aa3-wine](http://www.wtfm.org/aa3-wine) page which says it a fix for this but I have no idea where to put this script in.

---

### Post by freshmeat20 on 2011-08-03
Bump. Didnt put in enough info till the edit sorry.

---

### Post by freshmeat20 on 2011-08-04
bump. Im stuck at this script fix and only need to know how to use it.

---

### Post by disabledaccount on 2011-08-04
This not a script but patch to Wine source code that allows to dynamically switch mouse warping mode. Normally Mouse Warp Mode is statically defined in Wine registry.
To use this patch You need to download complete Wine source (I suggest to use version that the patch was created for), use patch command to apply the changes and compile it.

This is very strange solution - I don't know if it will help You, because I don't play AA3. However I suggest to first try different warping modes provided by latest version of Wine and windowed mode for the game.

regards.

---

### Post by freshmeat20 on 2011-08-04
Could you tell me how to apply this patch? I have the wine source now should I install this before I compile or after in a /root/wine folder?

---

### Post by disabledaccount on 2011-08-05
> To apply:
 
[LIST]
[*]*Download Wine 1.1.28 sources.*
[*]cd dlls/dinput
[*]*Apply the patch above.*
[/LIST]
>patch <name_of_patch_file.diff

Then You should compile Wine:
[COLOR=#006600]sudo apt-get install build-essential
[/COLOR][COLOR=#006600]sudo apt-get build-dep wine[/COLOR] - this will install dependancies for latest wine, but it should work

cd to base src dir (something like /usr/src/wine-1.1.28/)
>./configure - if something is wrong/missing then here you will get error message
>make depend && make
>sudo make install

---

