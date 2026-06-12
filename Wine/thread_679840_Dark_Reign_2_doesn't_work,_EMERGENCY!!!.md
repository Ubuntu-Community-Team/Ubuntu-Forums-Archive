---
title: "Dark Reign 2 doesn't work, EMERGENCY!!!"
date: 2008-01-27
forum: Wine
---

### Post by crazyfuturamanoob on 2008-01-27
Dark Reign 2 is an old 3d strategy game. Its home site is down, so no
help from there. I have dark reign 2 on cd, and it doesn't work.
I get this error:
[IMG]http://img98.imageshack.us/img98/9991/dr2errorfullgk6.jpg[/IMG]
Help, DR2 is the best game ever made, Tell me how to get it working!
Note: I mixed two images to see the whole error message, thats
why the image looks like weird.
Thanks for all replies.

---

### Post by Sugi on 2008-01-27
Oh man, I remember that bad A** game.  I use to play that all the time when it came out.  Please, if you get it working let us know.  I'll go find my old cds and dust them off to install them.

Well, I don't understand those errors at all, but maybe I can still help a bit.

Try these options:
 - uninstall it and reinstall it through wine
IE:
Terminal
$ cd /path/to/cd/
/path/to/cd/ $ wine game.exe

See if it gives you any errors during the installation.

~Next, if that didn't help.
 - Install the game on a windows box and copy the directory over to your Linux.

Sidenote: Make sure you have up to date wine and video drivers.

Good luck,
Sugi

---

### Post by hikaricore on 2008-01-28
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3082](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3082)

---

### Post by crazyfuturamanoob on 2008-01-28
I updated my video drivers yesterday (sunday), and I have played many
windows games. All they work perfectly throught wine. I didn't have any
problems when I installed dr2. I havent yet tried to install it trought wine,
but I didn't install it into its default directory.
I can't Install it on windows, because I installed ubuntu on it.
Last I remember, I had problems installing it on windows into another
directory than default. Maybe I should install it on its default.

---

### Post by crazyfuturamanoob on 2008-01-28
I tried to install it to its default directory, but still the same error.
Think the problem is in win32_socket.cpp? How can I update it?
Once when I tried to run soldat polyworks
(map creation app for soldat(a windows game)), it couldn't 
run until I updated a single dll in my windows directory. I did it trought google.
But how can I update something that is in wine?
Where are wine "windows" directories?
How about patching it to its newest version? 
Whats its newest version number, and where to get it?
DR2 home site is down... :(

---

### Post by Sugi on 2008-01-28
> **crazyfuturamanoob said:**
> 
Where are wine "windows" directories?(
/home/USER_NAME/.wine/
mine is
/home/LongPENIS/.wine/ (I have a odd user name, I know, but you get the idea)
Is that what you mean?

> **crazyfuturamanoob said:**
> DR2 home site is down... :(
Can you send a us a link for the home page.  All I got was IGN page for DR2.

---

### Post by crazyfuturamanoob on 2008-01-28
> /home/USER_NAME/.wine/
mine is
/home/LongPENIS/.wine/ (I have a odd user name, I know, but you get the idea)
Is that what you mean?

LoL, I ment that, but looks like wine's directories don't look like 
I imagine they could. I didn't find win32_socket.cpp there,
and most of the files looked kinda weird.
> Can you send a us a link for the home page. All I got was IGN page for DR2.
A year or two ago it did exists, but now it doesn't. It cannot be found
trought google or any search engine. It is useless, but anyway:
[http://darkreign2.won.net/](http://darkreign2.won.net/) Why did you ask?
Thanks anyway. I love replies.

---

### Post by hikaricore on 2008-01-28
> **hikaricore said:**
> [http://appdb.winehq.org/objectManager.php?sClass=application&iId=3082](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3082)

Not sure if you noticed but i linked the WINE appdb page showing the DR2 has a garbage rating and you will probably not be able to run it using WINE.

Best of luck anyways, and if you get it to work, please do post all the info you can on the AppDB page.

---

### Post by crazyfuturamanoob on 2008-01-29
> Dark Reign 2 requires Winsock 2

Users of the Windows 95 operating system are required to upgrade 
to Winsock 2 during the installation process of Dark Reign 2.  If they 
have already upgraded to Winsock 2 then you will not be prompted 
during the installation process to update Winsock.  Users of 
Windows 98 do not need to do this, as the proper version of 
Winsock is already incorporated into their operating 
systems.
I found that from readme.rtf (it was in dr2 installation directory).
I tried to run dr2 by setting wine to win95 and 98 modes but neither
didn't work. The installer didn't say anything about winsock.
Help, I am soon gonna to get windows if dr2 doesn't work...
(not really)
>  Originally Posted by hikaricore
[http://appdb.winehq.org/objectManage...ation&iId=3082](http://appdb.winehq.org/objectManage...ation&iId=3082)
Oh, I didn't notice that, but there reads, that some other guys are 
having exactly the same problem. I tried to google the answers,
but only thing I found was my own topic.
_________________________________________________

I haven't yet found a way to run dr2, but anyway:
I tried to run ws2setup.exe found in dr2 installation directory for fun,
but I found only an error message:
> An error was encountered while installi Winsock2.
Setup has been cancelled. See c:\windows\ws2setup.log for
more information. 
Then I opened ws2setup.log, and it had this:
> 

WS2SETUP begin: 01/28/2008 15:16:15

RegQueryValueEx(VendorInstallDll) failed

VendorWantsMSTCP=1, WantsMSIPX=2, WantsSetupUI=1

WantsMSDNS=1, WantsMSSAP=0

New wsock32.dll file version: 0004000a.00000678

ERROR: operating system not Windows95, canceling setup

WS2SETUP end: failure



WS2SETUP begin: 01/29/2008 13:10:33

RegQueryValueEx(VendorInstallDll) failed

VendorWantsMSTCP=1, WantsMSIPX=2, WantsSetupUI=1

WantsMSDNS=1, WantsMSSAP=0

New wsock32.dll file version: 0004000a.00000678

ERROR: operating system not Windows95, canceling setup

WS2SETUP end: failure



WS2SETUP begin: 01/29/2008 13:42:33

RegQueryValueEx(VendorInstallDll) failed

VendorWantsMSTCP=1, WantsMSIPX=2, WantsSetupUI=1

WantsMSDNS=1, WantsMSSAP=0

New wsock32.dll file version: 0004000a.00000678

ERROR: unsupported Windows9X version (4,10), canceling setup

WS2SETUP end: failure

Hope I said at least something useful for the geeks who solve these.
I didn't find anything winsocket related from wine's win directories.

---

### Post by stuart.crouch on 2008-01-30
You need to sign up to the wine appdb and put this information in the relevant place

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3082](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3082) 

before theres any chance of anyone solving things. 

Then you need to watch your bug report as the dev's WILL ask you for specific bits of information or to try running the program with various commands.


You wont get any resolution leaving that information here as the wine developers don't use this forum as a source of information.

---

### Post by BotFreak on 2008-07-13
Here's the fix u need...go to [www.mojo2go.we.bs](www.mojo2go.we.bs)
They have patches and bug fixes for dr2:guitar:

---

