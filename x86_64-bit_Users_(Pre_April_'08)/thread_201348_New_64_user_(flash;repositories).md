---
title: "New 64 user (flash;repositories)"
date: 2006-06-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Endow on 2006-06-21
Please people I need help desperately.80% of the sites I usuallu surf on use flash in one way or another and i'm using LTS on my amd64 (the 64bit version).

Now I understand there is more than one way to solve my problem (I can't install flash) so I would like you guys to give me the easiest waya round the 64bit flash problem.


Also there is a number of tutorials that says I need to enable certain repositories.Namely enable multiverse and universe repositories.How can i do that?

The instructions on the ubuntu page don't work for me since I don't have the same repositorie list and I don't wanna screw up by adding/removing random repositories.

Thanks in advance :-)

---

### Post by JoWilly on 2006-06-21
Read the sticky at the top for how to get flash and install nspluginwrapper to get the 32bit macromedia flash to work on firefox64. Everything is in the threads in this section.

---

### Post by Endow on 2006-06-21
Man the instructions on how to install nspluginwrapper look like chinese!

[http://www.gibix.net/dokuwiki/en:projects:nspluginwrapper](http://www.gibix.net/dokuwiki/en:projects:nspluginwrapper)

I downloaded all four files : plugin,viewer and sources.What do I do now?

---

### Post by JoWilly on 2006-06-21
Howto in this thread:

[http://ubuntuforums.org/showthread.php?t=160318]("http://ubuntuforums.org/showthread.php?t=160318")

---

### Post by Endow on 2006-06-22
Well yeah, what's alien?

---

### Post by incubus on 2006-06-22
Remember Google is your friend.

[http://www.kitenet.net/~joey/code/alien.html](http://www.kitenet.net/~joey/code/alien.html)

To install it:
$ sudo apt-get install alien

incubus

PS: You said you want to know how to enable universe/multiverse.  
Edit your file /etc/apt/sources.list and see that you have something similar to this:

```

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
```

The point is that you have to delete the "#" for uncommenting and make sure you have "universe" and "multiverse" written there. Note that I'm in the US, so the "us" part may change for you.

---

### Post by Kilz on 2006-06-22
If the nspluginwrapper is to difficult or you cant get it to work. You can install 32 bit firefox with java and flash. Unfortunately a member of the document team is playing games and keeps deleting the page. I copied it into a post.
[http://www.ubuntuforums.org/showpost.php?p=1158450&postcount=85](http://www.ubuntuforums.org/showpost.php?p=1158450&postcount=85)

---

### Post by warp99 on 2006-06-22
[QUOTE=Kilz]If the nspluginwrapper is to difficult or you cant get it to work. You can install 32 bit firefox with java and flash. Unfortunately a member of the document team is playing games and keeps deleting the page. I copied it into a post.
[http://www.ubuntuforums.org/showpost.php?p=1158450&postcount=85](http://www.ubuntuforums.org/showpost.php?p=1158450&postcount=85)[/QUOTE]


You don't have to create or export the pangorc file with LTS 6.06. You only need: 

sudo apt-get install ia32-libs ia32-libs-gtk gsfonts gsfonts-x11 linux32

Install the firefox 32-bit from mozilla as you would any normal tar file. With flash you need to use linux32. With java install and make the symlink for the plugin. Eveything in Dapper works fine without the need for additional work with the pangorc aliases files. 

32-bit support works VERY well under Dapper. I even deleted my chroot environment, didn't need it anymore. :cool:

---

### Post by Endow on 2006-06-24
Thanks for your help guys but after checking out all the options I can't even begin to comprehend how anyone would NOT want go to the same way i did (this is also a chance of you guys to tell me how :mrgreen:).

I mean Swiftfox.It not only solved my  problem (flash) but it's also a much faster browser.

---

### Post by JoWilly on 2006-06-24
[quote=Endow]Thanks for your help guys but after checking out all the options I can't even begin to comprehend how anyone would NOT want go to the same way i did (this is also a chance of you guys to tell me how :mrgreen:).

I mean Swiftfox.It not only solved my  problem (flash) but it's also a much faster browser.[/quote]

Well, all the 32bit plugins now work perfectly in firefox64 with nspluginwrapper, and the latest firefox64  1.5.0.4  is not slow anymore on my machine (the previous version was slow, but now its as fast at the 32bit version).

So as I'm running a 64 bit system I don't see any reason why I should run 32bit apps if they run as well in 64 bit :)

---

### Post by jvictor on 2006-06-26
Theres a browser called **flock** [www.flock.com](www.flock.com) u get a 32 bit browser but it installs MM-Flash plugin and works perfectly fine .. its based on mozilla (I guess) and looks and behaves pretty similar to Firefox.

---

### Post by abeowitz on 2006-06-27
The libflash-mozilla (gpl flash) works fine in Firefox 64, and seems to handle most of the web site menus and simple animations.

I only need the simple things, not games or media, so this works fine for me.

---

