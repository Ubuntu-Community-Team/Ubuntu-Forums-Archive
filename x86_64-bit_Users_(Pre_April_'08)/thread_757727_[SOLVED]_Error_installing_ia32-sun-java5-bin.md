---
title: "[SOLVED] Error installing ia32-sun-java5-bin"
date: 2008-04-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by lynwode on 2008-04-17
Guys,
I am trying to install a 32bit Oracle on 64bit x86-64 machine 
I have had a good hunt around and it looks like I need linux32 and ia32*.

So as root : apt-get install inux32 ias32*

 All goes well apart from the ia32-sun-java5-bin and ia32-sun-java6-bin parts. Here is the error:

[INDENT]Setting up ia32-sun-java5-bin (1.5.0-11-1ubuntu2) ...
/var/lib/dpkg/info/ia32-sun-java5-bin.postinst: line 72: /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.11/bin/java: No such file or directory
dpkg: error processing ia32-sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ia32-sun-java6-bin (6-00-2ubuntu2) ...
/var/lib/dpkg/info/ia32-sun-java6-bin.postinst: line 72: /usr/lib/jvm/ia32-java-6-sun-1.6.0.00/bin/java: No such file or directory
dpkg: error processing ia32-sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ia32-sun-java5-bin
 ia32-sun-java6-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)[/INDENT]

/usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.11/bin/java is link to /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.11/jre/bin/java
this second file exists though.

any ides?

---

### Post by Kilz on 2008-04-17
Are you setting it up on Gutsy? If so it looks like you are trying to install a older package ia32-sun-java6-bin (6-03-0ubuntu2) is the current. ia32-sun-java6-bin (6-00-2ubuntu2) is 3 versions old. Have you refreshed the package lists lately?

---

### Post by lynwode on 2008-04-17
I'm on Feisty. How would one go about refreshing the package list?

---

### Post by lynwode on 2008-04-18
I have refreshed the package list but still get the same errors. any ideas?

---

### Post by Kilz on 2008-04-18
The other possibility is that the repositories are not enabled. ia32-sun-java5-bin is in the multiverse repository. There is [a way to do it graphically ]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories") or you can edit the /etc/apt/sources.list . If you want to edit the list, you will see lines like this

#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

in it, just remove the # from in front of them, you might also want to uncomment the other sections like backports and universe. Afterwards, referesh or update the package lists again and you should have no problems.

---

### Post by lynwode on 2008-04-20
Thanks for you help Kliz. After a trip down the packge update road I decided to upgrade to Gutsy Gibbon and all is looking good..... eventuallly :)

---

