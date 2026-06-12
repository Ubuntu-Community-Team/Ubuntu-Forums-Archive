---
title: "flash plugin ---always the same question---"
date: 2005-07-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by lucaflea on 2005-07-12
hi. i can't install  flash plugin. i've tried all the common and usual ways... it doesn't work....

how can i do it?

---

### Post by linuxfanatic1024 on 2005-07-12
Download the file from
[http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Then, untar it, and copy these files:

- libflashplayer.so
- flashplayer.xpt

into /usr/lib/mozilla/plugins if you use Mozilla, or /usr/lib/mozilla-firefox/plugins if you use Firefox. The provided installation script doesn't work, and I looked at it and it was very buggy.  :-x 

Alternatively, you can try installing the package flashplugin-nonfree.

Good luck!

--Dan "Crash" Brodzik

---

### Post by lucaflea on 2005-07-12
no way no way no way!!!  ](*,) 

i read somewhere that for amd64 users there's no macromedia flash plugin avaliable...


and now????

i'm slowly slipping into windows again.....

---

### Post by newbie2 on 2005-07-12
[QUOTE=lucaflea]hi. i can't install  flash plugin. i've tried all the common and usual ways... it doesn't work....

how can i do it?[/QUOTE]
suse can do it?
[http://www.novell.com/coolsolutions/qna/15068.html](http://www.novell.com/coolsolutions/qna/15068.html)
 and ubuntu not?????

---

### Post by negatory on 2005-07-12
> Download the file from
[http://www.macromedia.com/shockwave...=ShockwaveFlash](http://www.macromedia.com/shockwave...=ShockwaveFlash)

Then, untar it, and copy these files:

- libflashplayer.so
- flashplayer.xpt

into /usr/lib/mozilla/plugins if you use Mozilla, or /usr/lib/mozilla-firefox/plugins if you use Firefox. The provided installation script doesn't work, and I looked at it and it was very buggy. 
This doesn't work in a 64bit firefox...maybe in a chroot enviroment you can install it this way but I really don't know because I dont chroot.

Pedro Carrico

---

### Post by DancingSun on 2005-07-12
SUSE is probably running 32-bit browsers, so the flash plug-in will work there.

You can do this with Ubuntu, but it doesn't work out of the box: you need to do the chroot thing to install 32-bit apps.

---

### Post by adonim on 2005-07-12
I am new here, try to do my homework.. since hours now...:-(

thank you for the path!

 /usr/lib/mozilla-firefox/plugins

I found it, downloaded the install_flash_player_7linux and tried to copy both files (.xpt and .so) into the plugin folder.... schocks, the error was:

"You do not have permission to write to this folder"

now what....?

then i opened terminal and typed:
apt-get install flash7/installer (actual path)
and got the error:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? ]
(*,) 

HELP.. please!!!

---

### Post by lucaflea on 2005-07-13
you have to write "sudo" before "apt-get" and then type your root password....

but i think it wont work....

i can't install flash plugin...

---

### Post by fistfullofroses on 2005-07-13
Until Macromedia releases a 64bit version we are all S.O.L.

---

### Post by linuxfanatic1024 on 2005-07-26
1. You never told me you had a 64-bit system. I use 32-bit systems...
2. That's the problem with binary-only software. Yeah, we need it for now, but I hope that the open-source libflash (or was it libswf?) catches up so that this can be fixed.

---

### Post by newbie2 on 2005-07-26
"Sure, if you follow the instructions on Ubuntu Forums, you'll be able to watch all the movie trailers at Apple's site right in your browser, just the way nature intended. But keep surfing around, and sooner or later you'll hit a video that's been encoded differently--perhaps using a newer codec not yet supported by Totem--and you'll have hit a brick wall. Or, even more frustratingly, the Web site you're visiting might sniff your browser to discover you're running Linux, at which point it will tell you (often wrongly) that your system is incompatible with the site's offerings, and not even give you the opportunity to try playing the video. (I'm looking at you, CNN.com.) Maddening!"
[http://www.pcworld.com/reviews/article/0,aid,121910,00.asp](http://www.pcworld.com/reviews/article/0,aid,121910,00.asp)
 :roll:

---

### Post by nrayever on 2005-07-26
linuxfanatic1024 why u didn't guessed that it was about an amd64 machine?? here we r at a amd64 support subforum, ok?? maybe tha's why it was for an amd64 user, hehehehehe.

then i suggest to fill in the request and wishlist to macromedia, to develop flash player native for x86_64 platform. this is the link on the forum.

[http://www.ubuntuforums.org/showthread.php?t=51211](http://www.ubuntuforums.org/showthread.php?t=51211)

fill in your request and wishlist. let's make this a reallity.

---

