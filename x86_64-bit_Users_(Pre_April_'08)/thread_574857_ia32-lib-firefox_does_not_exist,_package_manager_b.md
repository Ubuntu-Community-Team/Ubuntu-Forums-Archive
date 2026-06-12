---
title: "ia32-lib-firefox does not exist, package manager broken"
date: 2007-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Silent_Hunter on 2007-10-13
Swiftweasle32 depends on ia32-lib-firefox, but that package does not exist. Synaptic and apt say that they are broken. Swiftweasle32 works just fine without that package that does not exist in the repositories. How can I get the package manager not to complain about a missing package that does not exist and still keep Swiftweasle?

---

### Post by Kilz on 2007-10-13
[Swiftweasel32 was made for my 32bit howto.]("http://ubuntuforums.org/showthread.php?t=202537") It cant be should not be installed by itself. Secondly the reasons for using a 32bit version have lessened. Unless you require java, its not necessary to install a 32bit browser.

---

### Post by FredB on 2007-10-14
Indeed. And swiftweasel is only a rebranded and more optimized version of firefox after all !

---

### Post by Silent_Hunter on 2007-10-14
I did install it for java, and it works good for java. Blackdown java is too old of a version to use for yahoo games such as chess and pool. I can't use the package manager to install anything else until I fix the problem.

---

### Post by Silent_Hunter on 2007-10-14
If I can't get this problem fixed, I'd like to install swiftdove (im not sure what the difference is) instead of using that deb package that has non existent dependencies. Are there any instructions on compiling swiftdove? I downloaded it, but saw no configure script and the README did not contain any directions for compiling.

---

### Post by Kilz on 2007-10-14
> **Silent_Hunter said:**
> If I can't get this problem fixed, I'd like to install swiftdove (im not sure what the difference is) instead of using that deb package that has non existent dependencies. Are there any instructions on compiling swiftdove? I downloaded it, but saw no configure script and the README did not contain any directions for compiling.

Swiftdove is a email client, its a build of Thunderbird and has no requirements to my knowlage. Swiftweasel32 has requirements. The link in my last post should give all the info you need to get it running.

---

### Post by Silent_Hunter on 2007-10-14
> **Kilz said:**
> Swiftdove is a email client, its a build of Thunderbird and has no requirements to my knowlage. Swiftweasel32 has requirements. The link in my last post should give all the info you need to get it running.

I did get Swiftweasle32 from your howto thread. It doesn't have all the required information to get it running. I solved the problem by finding ia32-lib-firefox-amd64.deb from searching google and installing it.

---

### Post by Kilz on 2007-10-14
> **Silent_Hunter said:**
> I did get Swiftweasle32 from your howto thread. It doesn't have all the required information to get it running. I solved the problem by finding ia32-lib-firefox-amd64.deb from searching google and installing it.

You have been told this a few times, yet you insist on saying that the you were not given everything needed.
That is not the truth. 
1. The automatic setup script installs it. 
2. From the [SIZE="3"][COLOR="Sienna"]**Firefox**[/COLOR][/SIZE] section of the manual howto. [The same page you downloaded the Swiftweasel32.deb from.]("http://ubuntuforums.org/showthread.php?t=202537")
```
Download any of the browser deb files above. I totaly recommend Swiftweasel Then download the [ia32-lib-firefox-amd64]("http://home.comcast.net/~ubuntu64user/ia32-lib-firefox-amd64.deb") packages save them to your desktop.
Double click on ia32-lib-firefox and let Gedebi install it first then do the same with the browser deb you selected from above.
```

It clearly gives a link and instructions on how to install the file. Users are warned not to install the Swiftweasel32.deb deb file by itself.

"**The deb's below are for upgrading or adding Swiftweasel as a second browser after running the install script. Do not install the deb by itself.**"

The reason you can download the Swiftweasel32.deb is so
1. You can upgrade previous installs to the latest version.
2. You can add the Swiftweasel32 browser if you used the script to install Firefox32.

But for some reason you chose to ignore the plain large bold writing that warned you not to do it. Why is beyond me. 
You were told in a few places where to get the information.
1. [In this thread.]("http://ubuntuforums.org/showpost.php?p=3526151&postcount=2")
2. In the howto thread. [By me]("http://ubuntuforums.org/showpost.php?p=3527113&postcount=1147") and by [Rui Pais]("http://ubuntuforums.org/showpost.php?p=3526485&postcount=1146")

In fact on the howto thread you even [quoted the big bold warning not to install the deb by itself.]("http://ubuntuforums.org/showpost.php?p=3526301&postcount=1145") I have attached a screen shot.

Why you chose to use google after being pointed to the informations is a mystery to me. But Im glad you finally found it.

---

