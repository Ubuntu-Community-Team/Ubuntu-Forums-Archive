---
title: "Which java6 plugin to use in Mozilla?"
date: 2008-11-12
forum: x86 64-bit Users
---

### Post by zika on 2008-11-12
I need a java6 plugin for Mozilla in Ubuntu Intrepid Ibex on amd64 machine.

Every sugestion (with some explanation) will be greatly appreciated.

---

### Post by jocko on 2008-11-12
icedtea6-plugin work fine for me, and seems to be the preferred one as it is the java plugin included in the ubuntu-restricted-extras meta package. Just install it from synaptic or apt-get.

---

### Post by cariboo on 2008-11-12
There is only one java6 plugin available for 64bit linux. The easiest way to install it plus a lot of other codecs needed for playing various types of audio and video files, is to install the **ubuntu-restricted-extras** meta-package. You can install it using Add/Remove Programs, Synaptic Package Manager and of course the command line.

Jim

---

### Post by selllwow on 2008-11-12
[size=2][color=#282827][color=#000000][sell wow gold](http://www.virdeal.com), [sell gaia gold](http://www.virdeal.com), [sell ffxi gil](http://www.virdeal.com), [sell maple story mesos](http://www.virdeal.com) [http://www.virdeal.com](http://www.virdeal.com) [/color][/color][/size]

---

### Post by Thelasko on 2008-11-13
[Here's another thread]("http://ubuntuforums.org/showthread.php?t=972922") about Java on 64-bit.  The OP posted all of the packages he/she has installed.  Note that further down the page I tell him/her to uninstall GCJ.  Once GCJ was removed, it worked fine.

---

### Post by zika on 2008-11-14
I've replied several days ago but it did not reach forum:

first:

I've installed gcjwebplugin as mozilla gave me the choice while
accessing java oriented site. it works now but still I can not access
the site [http://socr.ucla.edu/htmls/SOCR_Experiments.html](http://socr.ucla.edu/htmls/SOCR_Experiments.html). should I
try icedtea6-plugin now? if I do try it shoud I try to uninstall
gcjwebplugin?

also:

thank You very much! I've installed icedtea6-plugin and now that page
works fine. with gcjwebplugin it did not.

I've unistalled gcj.

Thank You for all answers.

---

### Post by Sef on 2008-11-14
>  it works now but still I can not access
the site [http://socr.ucla.edu/htmls/SOCR_Experiments.html](http://socr.ucla.edu/htmls/SOCR_Experiments.html).

The OpenJDK plugin is still missing [Live Connect]("http://ubuntuforums.org/showthread.php?t=774956").   Sun Java 64-bit still does not have plugin.

---

### Post by zika on 2008-11-14
this ([http://socr.ucla.edu/htmls/SOCR_Experiments.html](http://socr.ucla.edu/htmls/SOCR_Experiments.html)) site works now
with icedtea but I need to refresh once the applet is started. I am
waiting for updates. eventhough this (refresh) is not a high price to
pay ... ;)

---

### Post by zika on 2008-12-27
since I've asked this question I've found another thread where Alpha version of 64-bit Java plugin was proposed. I've used it with great success. today I found that a new sub-version (b03) is available as of 24-dec-2008.

site is:
[https://jdk6.dev.java.net/6uNea.html](https://jdk6.dev.java.net/6uNea.html)
```

wget http://www.java.net/download/jdk6/6u12/promoted/b03/binaries/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin
cd /opt
sudo sh ~/**where_You've_downloaded_it**/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin
cd /usr/lib/mozilla/plugins
sudo ln -s /opt/jre1.6.0_12/lib/amd64/libnpjp2.so
```or last two command can be replaced by
```
mkdir ~/.mozilla/plugins/
ln -s /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
```I've used former rather than latter.
enyou!

---

