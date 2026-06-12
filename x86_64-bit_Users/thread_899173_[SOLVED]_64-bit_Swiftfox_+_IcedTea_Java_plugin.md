---
title: "[SOLVED] 64-bit Swiftfox + IcedTea Java plugin"
date: 2008-08-24
forum: x86 64-bit Users
---

### Post by svk on 2008-08-24
Hello,

I'm having some issues trying to get Java to work on my 64-bit browser using the IcedTea plugin.  I read [here]("http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695") that just a week ago, IcedTea was finally able to run signed Java applets on x86_64.

Here are the packages I have installed:

[LIST]
[*]swiftfox-athlon64 (version 3.0.2pre-2) -- to get this installed, I followed the directions [here]("http://getswiftfox.com/deb.htm").
[*]openjdk-6-jre (version 6b11-6ubuntu1)
[*]icedtea-gcjwebplugin (version 1.0-1ubuntu3)
[/LIST]
However, Swiftfox is not able to detect the IcedTea plugin.  I opened swiftfox via the terminal, but no relevant error messages were visible *yet*; then I navigated to about:plugins, and this showed up on the terminal:

```

LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so [/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so: **wrong ELF class: ELFCLASS64**]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/libnullplugin.so [/usr/lib/xulrunner-addons/plugins/libnullplugin.so: **wrong ELF class: ELFCLASS64**]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/libunixprintplugin.so [/usr/lib/xulrunner-addons/plugins/libunixprintplugin.so: **wrong ELF class: ELFCLASS64**]

```Why does this happen?

Perhaps, does this mean that I am **not **running the 64-bit version of swiftfox?  I have the swiftfox-athlon64 package installed from the repositories described [here]("http://getswiftfox.com/deb.htm"), so I *should* have 64-bit swiftfox running.  In fact, here's what I see in Help -> about:

Mozilla/5.0 (X11; U; Linux i686 (**x86_64**); en-US; rv:1.9.0.2pre) Gecko/2008072611 Firefox/3.0.2pre (Swiftfox)

Which suggests I have 64-bit swiftfox.  Is there a better way to make sure of this?

What else could cause these errors?  Please help!

Thank you in advance.

---

### Post by Nepherte on 2008-08-24
I've had the same problem as you have now. You can find the topic here: [http://ubuntuforums.org/showthread.php?t=817337](http://ubuntuforums.org/showthread.php?t=817337)

The solution is in post [#22]("http://ubuntuforums.org/showpost.php?p=5125426&postcount=22").

---

### Post by Kilz on 2008-08-24
Another option would be the free as in freedom [Swiftweasel ]("http://swiftweasel.tuxfamily.org/") that works just fine instead of the proprietary Swiftfox.

---

### Post by svk on 2008-08-24
Thanks for the help.

Sorry, Nepherte, the solution in that thread did not work for me.  I think our issues are slightly different -- I don't have libxul.so anywhere on my computer, but Swiftfox does not complain that it's missing.  Also, in your case, you had wrong ELF class ELFCLASS32, but in my case, I have wrong ELF class ELFCLASS64.  To me, this seems like I don't even have a 64-bit browser running...

I'm willing to try Swiftweasel.  I found the deb files here:

[http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717](http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717)

But now I'm wondering -- is my system "k8", or is it "athlon64"?  Which package do I install?  My processor is actually AMD Turion 64 X2, or more specifically, it is listed as TL-56.  Does this qualify as k8, or as athlon64?

Thanks again for the help.

---

### Post by svk on 2008-08-24
I downloaded the k8 package.  I hope I didn't download the wrong one!  If I did, please tell me.

From there, we're back to Nepherte's thread.  I just followed all the steps in that thread, and it works now!

Summary:

[LIST]
[*]Create directory "plugins" under /usr/lib/mozilla (if it does not exist already).
**sudo mkdir /usr/lib/mozilla/plugins**
[*]Create a symbolic link to the gcjwebplugin.so file under /usr/lib/mozilla/plugins.
**sudo ln -s /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so /usr/lib/mozilla/plugins/gcjwebplugin.so**
[*]Make sure that /usr/local/swiftweasel3/plugins is a valid symbolic link to /usr/lib/mozilla/plugins.  (Already was in my case).
[*]Find the libxul.so file, and create a symbolic link to it in the /usr/lib directory.  In my case, this was:
**sudo ln -s /usr/lib/xulrunner-1.9.0.1/libxul.so /usr/lib/libxul.so**
[/LIST]
That's it.  I restarted swiftweasel, navigated to about:plugins, and saw that the "GCJ Web Browser Plugin (using IcedTea) 1.0" was loaded.

Thank you for the help!

---

