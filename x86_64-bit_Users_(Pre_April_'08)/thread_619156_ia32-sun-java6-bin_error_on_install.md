---
title: "ia32-sun-java6-bin error on install"
date: 2007-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by studo77 on 2007-11-21
I am experiencing problems on installing the ia32-java.

Same as here:
[http://ubuntuforums.org/showthread.php?p=3811215#post3811215](http://ubuntuforums.org/showthread.php?p=3811215#post3811215)

for explanation on my problem see this:
[http://ubuntuforums.org/showpost.php?p=3810993&postcount=1186](http://ubuntuforums.org/showpost.php?p=3810993&postcount=1186)

Text is copied here for ease of read:
I am running Gutsy 64bit, and have on my previus install runned a Swiftweasel AMD 32bit using the script here.
I messed up the Ubuntu and had to start over. I tried installing the AMD 64bit from sourceforge:Swiftweasel. It did not work out.

Then tried to add the repository you mentioned for installing and getting updates fro 32bit swiftweasel. And installing with Synaptic, after running your script, without installing any browsers.

During all this i never got Java working right. It tested out ok on Suns testsite, but my bank does not work.

So i removed what i thought was everything: IA32xxxx, javas and firefox32, swiftweasel32 and so on.
Then i went through my folders and removed a "Java"-folder containing a security folder, the lib32-folder and a Mozilla-folder containing libjavaplugin.so.

Then i tried reinstalling with your script and now i cannot get Swiftweasel to run, i get this errormessage:
Code:

/usr/local/swiftweasel32/run-mozilla.sh: 424: /usr/local/swiftweasel32/swiftweasel-bin: not found

Any ideas?Now i want to clean my computer completely for 32bit mozilla and java, and the reinstall. I want my bank to work.

The "error" i got when running the bank-java-applet, was a greyed out swiftweasel, 100% CPU use and it stayed that way. On my previus install it worked.

/edit/
I get errors from ia32-java.

When using Synaptic:
E: ia32-sun-java6-bin: underproces post-installation script returned endstatus 127

And using the script:
hmm, now the script exits after chosing 4 for Gutsy 64bit... I used to get an error on ia32 saying a file exists, when producing a link, as well as the 127 error from above.

After a reboot i get the error of file again:
Code:

ln: make symbolic link '/usr/lib32/firefox32/plugins/libjavaplugin_oji.so' to '/usr/lib/jvm/ia32-java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so': File exists

and a purged remove from Synaptic and a dpkg -r ia32-sun-java-bin does not help, it still gives the same result.

/edit 2/
Also a sudo aptitude upgrade
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Does not help. It gives the same error and is not able to correct it.

---

### Post by Kilz on 2007-11-21
Exactly how did you do the following.

> So i removed what i thought was everything: IA32xxxx, javas and firefox32, swiftweasel32 and so on.

---

### Post by studo77 on 2007-11-21
In Synaptic i searched for ia32, and purge removed all installed. The same for the 32bit versions of Mozilla.

Then i removed the folders xx32 in /usr/local/

Deleted th /usr/lib32/firefox32/plugins/libjavaplugin_oji.so file.

These folders i removed (to root folder for backups)
/lib32/
/usr/share/swiftweasel32/

And a .java, Mozilla and Java folder, which i now lost the file telling me where they go...
I did not remove anything that looked to be installed or in root or filesystem dependent folders.

After reinstalling, it seem alle these folders are recreated, which was my reason for removing them in the first place, i wanted a completely new set of files.

The ia32-sun-java-bin i have reinstalled many times now and removing with Synaptic, dpkg and get the same error on install. And a Synaptic upgrade gives no error if ia32-sun-java-bin is not installed, but do if it is, and it cannot correct. (oops, already wrote this, but now i have tried removing using dpkg)

---

### Post by studo77 on 2007-11-21
A list of files contained in the removed folders:
folder:java
classpath.security
folder:security.d
100X-gnu.java.security.provider.Gnu
X=0-4
1004-gnu.javax.security.auth.callback.GnuCallbacks


lib32 contains a great number of files

folder:mozilla/plugins
libjavaplugin.so

folder:.java/.systemprefs (Not sure about if this is one i removed.)
.system.lock
.systemRootModfile

---

### Post by Kilz on 2007-11-21
> **studo77 said:**
> A list of files contained in the removed folders:
folder:java
classpath.security
folder:security.d
100X-gnu.java.security.provider.Gnu
X=0-4
1004-gnu.javax.security.auth.callback.GnuCallbacks


lib32 contains a great number of files

folder:mozilla/plugins
libjavaplugin.so

folder:.java/.systemprefs (Not sure about if this is one i removed.)
.system.lock
.systemRootModfile

First off you need to install or reinstall all of the ia32 packages. But first we will clear out downloaded files just in case. Its good to hear you have the swiftweasel repo added because stickk has agreed to host a few files for me.

```
sudo apt-get clean
sudo apt-get reinstall ia32-libs  linux32 ia32-lib-firefox-amd64
```



Also, just for future reference, it makes it harder if you are seeking help after doing wholesale removal of things. In the future you might want to make a post first then wait for an answer. This might save the trouble of making sure everything is in place. It could be a simple thing that can be fixed with minimal effort.

---

### Post by Ehtetur on 2007-11-22
If and when you get your system back on point, you may want to ditch the 32bit jre & the 32bit firefox, and instead install 64bit firefox with the j2re1.4-mozilla-plugin.

---

### Post by Kilz on 2007-11-22
> **Ehtetur said:**
> If and when you get your system back on point, you may want to ditch the 32bit jre & the 32bit firefox, and instead install 64bit firefox with the j2re1.4-mozilla-plugin.

I just installed the gutsy package, looks like they fixed blackdown crashing on every applet. Now it just crashes on new applets or freezees up the browser. Still not a good solution imho. At lweast when java 7 comes out it will solve the problem. Until then I would stick with the fully functional 32 bit java 6.

---

