---
title: "Installing an extra package with WINE"
date: 2013-07-14
forum: Wine
---

### Post by lampadron on 2013-07-14
Hi everyone ):P. 

I have a problem with winetricks. I want to play League of Legend and for that I need to install adobeair and wininet. But the winetricks gives me the error message that says that it's impossible to install that packages. What I should do? May I download those packages and install them with wine? Will it work? 


P.S. 


 Sorry for my English.
I'm using wine 1.4 and the error messages are:
for adobe air
 "This application requires a version of Adobe AIR which cannot be found. Please download the latest version of the runtime from adobe website or contact the application author for an updated version "
 
It looks like i should install package manually, but, should I add the package to winetrick list or just install it with wine.


for wininet 
"sha1sum mismatch! Rename /home/myFolder/.cache/winetricks/wininet/3725.exe and try again."


I've tried to rename that file but it still doesn't work:mad:.
I've search in google and I've found this page [https://code.google.com/p/winetricks/issues/detail?id=238](https://code.google.com/p/winetricks/issues/detail?id=238) . It says that it is impossible to download the wininet in the new version of winetricks. So my question is, how I can resolve this problem?

Thank for your future replies :p!

---

### Post by lah7 on 2013-07-30
You may wish to try another frontend similar to Winetricks called **PlayOnLinux** *(available at [http://www.playonlinux.com]("http://www.playonlinux.com/") or a slightly older version in the Ubuntu Software Center)*

It's still Wine but it's easier to choose which version of Wine as well as being able to manually install individual components like Winetricks does.
Somebody has already devised a PlayOnLinux script containing all the packages you need, since there's a League of Legends option available in the games category in the Install Menu (check the "Testing" checkbox). PlayOnLinux will set up a virtual drive and download the required packages there. You may wish to try that.

Alternately, try a newer version of Wine, a different OS or manually seek & download the components that Winetricks are struggling to download and place them in winetricks' directory: [COLOR=#0000cd]~/.winetricks[/COLOR]

---

