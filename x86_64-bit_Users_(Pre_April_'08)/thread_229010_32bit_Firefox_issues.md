---
title: "32bit Firefox issues"
date: 2006-08-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by mattlach on 2006-08-03
Hi all,

I followed an guide on the forums here (can't find it right now) that helped me install 32 bit firefox with flash and java support on my AMD64, and I am having some odd graphics bugs.

[img]https://home.comcast.net/~mkarlsson/ubuntuforums/firefoxissues.jpg[/img]

As you can see above, the dividers between the tabs, as well as all radio buttons, check boxes, scroll bars, etc. are all missing/blank/grey.

This does not happen with the 64bit version installed with apt-get.

I also did this on Breezy without a problem, but now in dapper I am having issues.

Does anyone know what might be wrong, and how I might fix it?

Thanks,
Matt

---

### Post by aceracer24 on 2006-08-03
I just got done installing mine as well and I can say I do not have any problems at all. I would suggest trying the install again. Here is a link to where you got the info to instrall: [http://www.ubuntuforums.org/showthread.php?p=1174435](http://www.ubuntuforums.org/showthread.php?p=1174435)

---

### Post by mattlach on 2006-08-04
Well..

I tried downloading and downloading 1.5.0.6  (I had 1.5.0.4) as well as removing all of the configuration data, but still no luck.  Same graphics bug.

Could I be missing some sort of library maybe?

---

### Post by Kilz on 2006-08-04
> **mattlach said:**
> Well..

I tried downloading and downloading 1.5.0.6  (I had 1.5.0.4) as well as removing all of the configuration data, but still no luck.  Same graphics bug.

Could I be missing some sort of library maybe?

You downloaded the [Firefox32 deb file with launcher.]("http://home.comcast.net/~deletebox/firefox32-1.5.0.6_amd64.tar.gz") from my howto page. Extracted it, installed the .deb file, dragged the launcher to the desktop. Then used that to start firefox?
Or did you download Firefox from the firefox website and install it yourself?

---

### Post by mattlach on 2006-08-04
> **Kilz said:**
> You downloaded the [Firefox32 deb file with launcher.]("http://home.comcast.net/~deletebox/firefox32-1.5.0.6_amd64.tar.gz") from my howto page. Extracted it, installed the .deb file, dragged the launcher to the desktop. Then used that to start firefox?
Or did you download Firefox from the firefox website and install it yourself?


I think aceracer linked to the wrong guide.  I followed another one that did not involve any .deb files, but went throught the process of downloading and extracting firefox to /usr/local/firefox32 and creating a custom executable link for it.  (This worked fin in Breezy, but is giving me issues in Dapper.)

I'll have to take a look at your deb and see if that works better.

---

### Post by Kilz on 2006-08-04
> **mattlach said:**
> I think aceracer linked to the wrong guide.  I followed another one that did not involve any .deb files, but went throught the process of downloading and extracting firefox to /usr/local/firefox32 and creating a custom executable link for it.  (This worked fin in Breezy, but is giving me issues in Dapper.)

I'll have to take a look at your deb and see if that works better.

The deb file is linked at the top of the my howto linked in aceracer24's post. The howto is older and isnt updated as much. Im putting in more energy to the auto setup scripts. The advantages are that the deb file is will do everything the same on the systems its installed to, in other words it eliminates errors. The other good thing it dose is that its easy to remove/upgrade it.

---

### Post by mattlach on 2006-08-12
> **Kilz said:**
> The deb file is linked at the top of the my howto linked in aceracer24's post. The howto is older and isnt updated as much. Im putting in more energy to the auto setup scripts. The advantages are that the deb file is will do everything the same on the systems its installed to, in other words it eliminates errors. The other good thing it dose is that its easy to remove/upgrade it.

Well,  I removed my manual install of firefox, and I still have the same issue.  I think I am going to post about it over in the original thread with the debs and see if anyone knows whats going on.

Thanks for the help,
Matt

---

### Post by infinitepi on 2006-08-13
i'm having this same issue after runing the script that also installs the mplayer plugin...  i copy aand pasted the commands from that guide and didn't notice any errors.

---

### Post by Kilz on 2006-08-13
Ok, do you both have ia32-libs-gtk installed? If so what version? Are either of you running Kubuntu?


infinitepi - Did you run the auto install script, or follow the cut/paste manual howto?

---

### Post by mwshook on 2006-08-13
I had the same issue come up when I switched themes. The bug happens on some themes, but doesn't happen on other themes. Try switching to the default "Human" theme, and it may go away.

---

### Post by wilberfan on 2006-08-23
I'm was having the same missing radio buttons, etc, problem that  mattloch was having--and as I tried changing theme settings, Firefox32 crashed--and now won't start at all...

I get a spinning cursor for 10 or 15 seconds, but then stops--and nothing opens.   I tried reinstalling Firefox32 using Kilz's deb, etc...and that worked until it crashed again when I tried to change themes again.

A third re-install, and a couple of reboots, but Firefox32 will now not start at all.

Any idea what's going on??

[edit]  I just tried running it from the terminal, and got these error messages:

> ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.

** ERROR **: No such image: /usr/share/themes/Crux/pixmaps/progressbar_trough.pn g
aborting...
/usr/local/firefox32/run-mozilla.sh: line 131:  5752 Aborted                 "$p rog" ${1+"$@"}

---

### Post by Kilz on 2006-08-23
> **wilberfan said:**
> I'm was having the same missing radio buttons, etc, problem that  mattloch was having--and as I tried changing theme settings, Firefox32 crashed--and now won't start at all...

I get a spinning cursor for 10 or 15 seconds, but then stops--and nothing opens.   I tried reinstalling Firefox32 using Kilz's deb, etc...and that worked until it crashed again when I tried to change themes again.

A third re-install, and a couple of reboots, but Firefox32 will now not start at all.

Any idea what's going on??

[edit]  I just tried running it from the terminal, and got these error messages:

libpangohack only loads graphics in applications firefox starts to use downloaded files. Like if you click on a tar.gz link and click the open automaticly with file roller. It does nothing else, so ignore it. [If you read message 10]("http://www.ubuntuforums.org/showpost.php?p=1375280&postcount=10") in this thread you will get the answer on how to solve the problem.

---

### Post by wilberfan on 2006-08-23
> **Kilz said:**
> libpangohack only loads graphics in applications firefox starts to use downloaded files. Like if you click on a tar.gz link and click the open automaticly with file roller. It does nothing else, so ignore it. [If you read message 10]("http://www.ubuntuforums.org/showpost.php?p=1375280&postcount=10") in this thread you will get the answer on how to solve the problem.

I had to *uninstall* firefox32, then reinstall it (I hadn't uninstalled it the first couple of tries.).  With firefox CLOSED, I changed to a different theme setting.  That did solve the problem.   

Thanks for the reply!

---

### Post by saneone on 2007-03-21
I have a problem with Firefox32 font rendering... It renders non-antialiased ugly fonts, while Firefox64 renders them very good, the same as Konqueror (that means - very nice, OS X like)...

How can i fix this?

---

