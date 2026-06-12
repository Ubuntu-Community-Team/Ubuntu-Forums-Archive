---
title: "the new repositories dont like me"
date: 2007-05-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by nonewmsgs on 2007-05-06
sudo apt-get install build-essential
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing ia32-libs-gtkglext1 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/packages.dfreer.org_dists_feisty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
william@williams-beast:~/Desktop$ 


ummm...now what?


Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing ia32-libs-gtkglext1 (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/packages.dfreer.org_dists_feisty_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'
i think im in trouble now.... someone want to help?

---

### Post by dfreer on 2007-05-06
ooops.. looks like my repository is messing you up. good thing I was looking in the 64-bit forum and happened upon your thread. Give me a couple of hours and I will get this fixed for ya. In the future though, if you have any problems with my repository please leave a message in this thread, thanks!

[http://ubuntuforums.org/showthread.php?t=432642](http://ubuntuforums.org/showthread.php?t=432642)

---

### Post by dfreer on 2007-05-06
fixed. Have fun!

---

### Post by nonewmsgs on 2007-05-06
thanks soo much.  im sorry i didnt post in the right place, but i was panicked.

---

### Post by dfreer on 2007-05-06
don't worry about it. I should've done more thorough testing on the repository before I added those packages, it seems that even though a package will install cleanly using dpkg, the repository is VERY picky. Glad to see that someone is using the repository, the main thing I should focus on is getting important packages up there (wine, firefox, flash, mplayer, java).

---

### Post by nonewmsgs on 2007-05-06
it still isnt working :|

---

### Post by dfreer on 2007-05-07
It's working fine from this end. What are your error messages now?

---

