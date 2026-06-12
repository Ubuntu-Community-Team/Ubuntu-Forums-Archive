---
title: "Compiz/XGL Update...Now not working"
date: 2006-08-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by TripleE on 2006-08-15
I just updated to the latest XGL and now the it will not come up at all (Menu Panel, title bar of windows...):mad:  Any suggestings on how to fix it?  I am running Ubuntu 6.06 AMD64.

edit: Does anyone know the best thread to follow so I can try to reinstall it?  I originally followed:
 [http://ubuntuforums.org/showthread.php?t=194993&highlight=easy+xgl+install](http://ubuntuforums.org/showthread.php?t=194993&highlight=easy+xgl+install)

---

### Post by TripleE on 2006-08-16
I kept looking for other howtos.  I found [http://www.ubuntuforums.org/showthread.php?t=133427](http://www.ubuntuforums.org/showthread.php?t=133427).  I tried it but it did not work either.  I then remembered that I could just revert back to an older package.  So I did a:
```
sudo apt-get remove --purge compiz compiz-gnome

```

Then to install the older package:
```
sudo dpkg -i /var/cache/apt/archives/compiz-gnome_0.0.13-0quinn29_amd64.deb
sudo dpkg -i /var/cache/apt/archives/compiz_0.0.13-0quinn29_amd64.deb

```

Now all I get is a white screen where the windows should be.

---

### Post by Fedcer on 2006-08-16
I have the latest packages and they are working fine. The reason why compiz may not be working right may be that they need cgwd and cgwd-themes to to have window decorations,etc.
Did you install this two packages when you updated? If not, then try updating again and installing them.
Oh, and remember that the script that starts compiz should now say "cgwd --replace" instead of "gnome-window-decorator".

EDIT: You could try with this guide: [http://www.ubuntuforums.org/showthread.php?t=225141](http://www.ubuntuforums.org/showthread.php?t=225141), it is the most updated one I've found.

-

---

### Post by TripleE on 2006-08-17
> I have the latest packages and they are working fine. The reason why compiz may not be working right may be that they need cgwd and cgwd-themes to to have window decorations,etc.
Did you install this two packages when you updated? If not, then try updating again and installing them.
 I went ahead and did a:
```
sudo apt-get install cgwd cgwd-themes

``` and I got:
```
The following packages have unmet dependencies:
  cgwd-themes: Depends: cgwd (>= 0.54) but 0.53 is to be installed
E: Broken packages

``` > Oh, and remember that the script that starts compiz should now say "cgwd --replace" instead of "gnome-window-decorator".
 I removed "gnome-window-decorator" from my "Startup Programs" in "Sessions".  Thanks for the tip.
>  EDIT: You could try with this guide: [http://www.ubuntuforums.org/showthread.php?t=225141](http://www.ubuntuforums.org/showthread.php?t=225141), it is the most updated one I've found.
 I also followed this howto step by step (I already had the nvidia drivers and k8 kernel installed) and tried to reboot again.  Now I am getting:
```

dlopen: libglitz-glx.so.1 cannot be open shared object file:  No such file or directory
unrecognized option: -fullscreen

``` I did a:
```
sudo apt-get install libglitz-glx1

``` to resolve the problem.

Thanks for the help.  Any Ideas on the cgwd-themes package?

EDIT: By the way, I just got my new video card in.  I upgraded from a 7300GS to a 7900GT.  It is sweet.

---

### Post by John.Michael.Kane on 2006-08-17
cgwd-themes package can be found here add the line to your sources.list.also the repo is gpg

```
deb http://www.beerorkid.com/compiz dapper main 
```

```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```

**[COLOR="Red"]Only download the cgwd-themes package from here. then comment out the repo.[/COLOR]**

---

### Post by TripleE on 2006-08-17
Very strange.  I already had the repo and the key, but it did not work.  I reimported the key and the install went through fine.  Thanks.

FYI:  System -> Preferences -> CGWD Themer is where the themer is.  It took some time for me to find it.

---

