---
title: "[SOLVED] Cant Access Add-ons for FF3"
date: 2008-06-19
forum: x86 64-bit Users
---

### Post by scpatl4now on 2008-06-19
When I click to browse add-ons it shows nothing but "firefox couldn't retrieve add-ons.  When I type the web address for add-ons I get a "failed to connect error".  I have uninstalled and reinstalled in synaptic a couple of times.  I have checked my version with dpkg -s firefox-3.0 and it says I have '3.0+nobinonly-0ubuntu0.8.04.1' This just started today.  I noticed my gmail and yahoo mail notifiers were not conecting so I uninstalled them thinking I would reinstall...but I cant even access the page

---

### Post by pixel :-) on 2008-06-20
try reinstalling firefox specific dependencies.

For example try reinstalling xulruner libmozjs0d

The config directory could be broken. rename .mozilla to something else(if you whant to retreave data,if you don't care just deleat it),it's a hidden directory in your home,tell your file bronzer to show you the hidden files.

---

### Post by scpatl4now on 2008-06-20
> **pixel :-) said:**
> try reinstalling firefox specific dependencies.

For example try reinstalling xulruner libmozjs0d

The config directory could be broken. rename .mozilla to something else(if you whant to retreave data,if you don't care just deleat it),it's a hidden directory in your home,tell your file bronzer to show you the hidden files.

I tried your suggestions.  I even renamed the .mozilla file.  When I reopened firefox I got the start page...but cant access or install extensions.  I see 2 errors:
Failed to load XPCOM component: /usr/lib/xulrunner-1.9/components/libpyloader.so
Failed to load XPCOM component: /usr/lib/xulrunner-1.9/components/pyabout.py
I dont know if these have anything to do with my problem.  I completely uninstalled Firefox and reinstalled...still the same

---

### Post by pixel :-) on 2008-06-20
reinstall xulrunner-1.9
test it
reinstall firefox-3.0
test it

In Ubuntu Firefox is cut in multiple packages,when you reinstall Firefox,you don't reinstall it's dependencies.Firefox is just a metapakage.The errors you reported,implie that it's xulrunner at fault(probably pyabout.py depends on that libpyloader.so).

reinstall python2.5
test it

The errors seems to be linked to python stuff.Look throe the dependencies of xulrunner and try to reinstall stuff that depends on python ,apparently only "python2.5" fit the profile.Other programs that use python are ok?

Purge(don't just uninstall) Firefox and firefox-3.0 then tell apt-get to autoremove.Tell synaptic to purge all residues of old pakages(residual config).Then reinstall firefox.Hopefully this will purge the broken stuff.

In synaptic,is there any pakage listed as broken?

When you start firefox in a terminal what does it say.

You updated to 3 right?You are not in 3 5beta.

---

### Post by scpatl4now on 2008-06-20
what is the difference between uninstall and purge? I am rather new with this

---

### Post by scpatl4now on 2008-06-20
> **pixel :-) said:**
> reinstall xulrunner-1.9
test it
reinstall firefox-3.0
test it

In Ubuntu Firefox is cut in multiple packages,when you reinstall Firefox,you don't reinstall it's dependencies.Firefox is just a metapakage.The errors you reported,implie that it's xulrunner at fault(probably pyabout.py depends on that libpyloader.so).

reinstall python2.5
test it

The errors seems to be linked to python stuff.Look throe the dependencies of xulrunner and try to reinstall stuff that depends on python ,apparently only "python2.5" fit the profile.Other programs that use python are ok?

Purge(don't just uninstall) Firefox and firefox-3.0 then tell apt-get to autoremove.Tell synaptic to purge all residues of old pakages(residual config).Then reinstall firefox.Hopefully this will purge the broken stuff.

In synaptic,is there any pakage listed as broken?

When you start firefox in a terminal what does it say.

You updated to 3 right?You are not in 3 5beta.



I thought this might help too:

scott@Gscott-desktop:~$ dpkg -s firefox-3.0
Package: firefox-3.0
Status: install ok installed
Priority: optional
Section: web
Installed-Size: 3648
Maintainer: Alexander Sack <asac@ubuntu.com>
Architecture: amd64
Version: 3.0+nobinonly-0ubuntu0.8.04.1
Replaces: firefox (<< 3), firefox-granparadiso, firefox-libthai, firefox-trunk
Provides: firefox-libthai, www-browser
Depends: debianutils (>= 1.16), fontconfig, libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>= 1.6.0), libgcc1, libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.12.0), libnspr4-0d (>= 1.8.0.10), libpango1.0-0 (>= 1.20.1), libstdc++6 (>= 4.1.1-21), psmisc, xulrunner-1.9 (>= 1.9~rc)
Recommends: ubufox
Suggests: firefox-3.0-gnome-support (= 3.0+nobinonly-0ubuntu0.8.04.1), latex-xft-fonts, libthai0
Conflicts: firefox (<< 3), firefox-granparadiso (<< 3.0~alpha8-0), firefox-libthai, firefox-trunk (<< 3.0~a8~cvs20070914t1713-0)
Conffiles:
 /etc/firefox-3.0/profile/bookmarks.html 5268a062e398d7c991f16155159088a3
 /etc/firefox-3.0/profile/localstore.rdf ea03cc19c2a3f622fa557cd8ea9da6eb
 /etc/firefox-3.0/profile/prefs.js 99940ecd258d83b3355ab06fca0ffddb
 /etc/firefox-3.0/profile/mimeTypes.rdf 69cdcb7e0209f2e9d29000ee1c0ee2f0
 /etc/firefox-3.0/profile/chrome/userChrome-example.css 4788fdaa51b0a238cb21f5c2877ef06d
 /etc/firefox-3.0/profile/chrome/userContent-example.css d3765c7d2de5626529195007f4b7144a
 /etc/firefox-3.0/pref/firefox.js 6f52c7983d5ecdc9d3b953863bbebca2
Description: safe and easy web browser from Mozilla
 Firefox delivers safe, easy web browsing. A familiar user interface,
 enhanced security features including protection from online identity theft,
 and integrated search let you get the most out of the web.
 .
 This browser was previously known as Firefox 2, Firebird and Phoenix.
 .
 Install this firefox package too, if you want to be automatically upgraded to
 new major firefox versions in the future.

---

### Post by pixel :-) on 2008-06-20
remove,simply removes the files,but leaves the configuration files in /etc
purge removes everything,including what was put in /etc

sudo apt-get check firefox-3.0 //if it gives errors,do what it sais and restart firefox to see,if it worked
sudo apt-get remove firefox-3.0 
sudo apt-get autoremove //removes libraries that are not used by enything

use synaptic to purge ALL old config residues(don't know the command line).status-->not installed,they are marked as not installed,mark them for complite removal,make sure that you don't remove installed pakages,only ones with an empty scare,when you done close synaptic

sudo apt-get install firefox-3.0

hopefully this will work.You have to restart firefox to see it.

---

### Post by scpatl4now on 2008-06-20
> **pixel :-) said:**
> remove,simply removes the files,but leaves the configuration files in /etc
purge removes everything,including what was put in /etc

sudo apt-get check firefox-3.0 //if it gives errors,do what it sais and restart firefox to see,if it worked
sudo apt-get remove firefox-3.0 
sudo apt-get autoremove //removes libraries that are not used by enything

use synaptic to purge ALL old config residues(don't know the command line).status-->not installed,they are marked as not installed,mark them for complite removal,make sure that you don't remove installed pakages,only ones with an empty scare,when you done close synaptic

sudo apt-get install firefox-3.0

hopefully this will work.You have to restart firefox to see it.


Wish I could say that worked, but it did not.  I also had FF2 installed on my system (it also did the same thing).  I removed it completely and did all the steps you outlined.  When I reinstalled FF3 it did the same thing (except most of the add-ons I had were gone...and cant install them).  I'm not sure what else to do.  Please explain the purge all config files.  That was the only step I was unsure of, and I might have done that incorrectly.
One more thing...I cannot access the login for Gmail or Yahoo mail...I get the same error as the add-ons

---

### Post by philinux on 2008-06-20
If you can get into Firefox backup your bookmarks. If you cant then browse to you home folder and press ctrl h to display the hidden files.

Look for the .mozilla folder and open the folder firefox then folder 

???????.default the ?? are random letters.

Look for bookmarks.html right click copy and paste them somewhere safe like your desktop. You can import them back later.

Now delete the .mozilla folder. It will be recreated when you launch firefox.

---

### Post by scpatl4now on 2008-06-20
> **philinux said:**
> If you can get into Firefox backup your bookmarks. If you cant then browse to you home folder and press ctrl h to display the hidden files.

Look for the .mozilla folder and open the folder firefox then folder 

???????.default the ?? are random letters.

Look for bookmarks.html right click copy and paste them somewhere safe like your desktop. You can import them back later.

Now delete the .mozilla folder. It will be recreated when you launch firefox.

Did that...reinstalled...same thing.  No extensions, cant access any type of webmail...cant get any extensions

---

### Post by scpatl4now on 2008-06-20
Ok...just call me stupid.  The other night my connection went down and switched to my DSL backup.  When I went back to cable, I inserted the ethernet cable into the other NIC...thus, I pulled an IP adress not listed in my firewall which in turned blocked non-listed apps.  Its fixed though...goes to show...stupid isn't platform specific...lol
Thanks for all the help though...I now know more about Firefox 3 than I ever care to

---

### Post by philinux on 2008-06-20
Excellent news. We've all been there.

Please mark the thread solved.

---

### Post by konungursvia on 2008-06-21
This is a continuation of the issue with a different cause. I now notice ads in ff3, whereas adblock plus always zapped them. Now I see that adblock plus is not compatible with ff3. So i update and see a new ff3 version. I install that. Now it always says "FF3 will install this next time you restart". But when I restart, no updated add-ons are in fact reinstalled. I still see ads, and I still see the "will install this next time you restart FF". Any ideas?

---

