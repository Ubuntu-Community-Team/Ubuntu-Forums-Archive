---
title: "update-java-alternatives ia32-java-6-sun"
date: 2007-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by smaller on 2007-10-26
I want to get the 32 bit java plugin for firefox working because the 64 bit JRE's either don't have a plugin or have one that doesn't work with my online banking applet.  (blackdown/icedtea)

So I installed the ia32-java-6-sun package and now I'm trying to update my system with the command below and as you can see it responds with a clear error message.

```
 sudo update-java-alternatives --plugin --set ia32-java-6-sun
update-alternatives: Cannot find alternative `/usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so'
```

What is strange however, is that this file does exist. Does anybody have any idea's?

---

### Post by chriv on 2008-06-12
You are correct.  The file does exist.  What does not exist is a debian packager "alternative" definition for that contains that file.  You have to install the alternative first.

The problem with the "update-java-alternatives" script is that it only changes which alternative is set.  It does not actually add any files to the alternative definitions.

To set a definition for an alternative, you have to run update-alternatives with the --install option.  I manually installed the jdk (with the jre) from sun's site to /usr/lib/jvm/ia32-java-6-sun, and then created my own script to install the alternatives before updating them.

update-java-alternatives reads the .jinfo file for the selected set of alternatives in /usr/lib/jvm, which contains 3 of the four needed arguments for an alternative (priority, name, and path), but does not contain the name of the link created by the alternative, so it cannot create it if it does not exist, and has not been programmed to install a new alternative, but only to select from existing ones.

This script created all the alternatives for me.  Set the priority high if you want ia32-java-6-sun to get automatic preference.  Set it low if you do not.  1075 was higher than anything on my system.  This script created all the alternatives for me.  Note that I used the ns7-gcc29 versions of libjavaplugin_oji.so, and that I coded the location of the links to the /usr/lib/<browsername>/plugins directory.  This may or not be correct (verify for yourself).  Note also that I modeled the structure after the real ubuntu ia32-java-6-sun package structure for consistency, including replicating their structure for sybolic links, and gziping all the man files.  This script could have been shorter, but I threw it together pretty quicly using sed and a copy of the .ia32-java-6-sun.jinfo file.

Here is my script (ia32-java-6-sun.sh):
```

#!/bin/sh
export JAVA_PACKAGE_NAME=ia32-java-6-sun-1.6.0.06
export JAVA_PACKAGE_ALIAS=ia32-java-6-sun
export JAVA_PACKAGE_PRIORITY=1075
export JAVA_PACKAGE_SECTION=non-free
#
update-alternatives --install /usr/bin/ControlPanel ControlPanel /usr/lib/jvm/ia32-java-6-sun/jre/bin/ControlPanel $JAVA_PACKAGE_PRIORITY
update-alternatives --auto ControlPanel
update-alternatives --install /usr/bin/java java /usr/lib/jvm/ia32-java-6-sun/jre/bin/java $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/java.1.gz java.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/java.1.gz
update-alternatives --auto java
update-alternatives --install /usr/bin/java_vm java_vm /usr/lib/jvm/ia32-java-6-sun/jre/bin/java_vm $JAVA_PACKAGE_PRIORITY
update-alternatives --auto java_vm
update-alternatives --install /usr/bin/javaws javaws /usr/lib/jvm/ia32-java-6-sun/jre/bin/javaws $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/javaws.1.gz javaws.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/javaws.1.gz
update-alternatives --auto javaws
update-alternatives --install /usr/bin/jcontrol jcontrol /usr/lib/jvm/ia32-java-6-sun/jre/bin/jcontrol $JAVA_PACKAGE_PRIORITY
update-alternatives --auto jcontrol
update-alternatives --install /usr/bin/keytool keytool /usr/lib/jvm/ia32-java-6-sun/jre/bin/keytool $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/keytool.1.gz keytool.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/keytool.1.gz
update-alternatives --auto keytool
update-alternatives --install /usr/bin/pack200 pack200 /usr/lib/jvm/ia32-java-6-sun/jre/bin/pack200 $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/pack200.1.gz pack200.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/pack200.1.gz
update-alternatives --auto pack200
update-alternatives --install /usr/bin/policytool policytool /usr/lib/jvm/ia32-java-6-sun/jre/bin/policytool $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/policytool.1.gz policytool.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/policytool.1.gz
update-alternatives --auto policytool
update-alternatives --install /usr/bin/rmid rmid /usr/lib/jvm/ia32-java-6-sun/jre/bin/rmid $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/rmid.1.gz rmid.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/rmid.1.gz
update-alternatives --auto rmid
update-alternatives --install /usr/bin/rmiregistry rmiregistry /usr/lib/jvm/ia32-java-6-sun/jre/bin/rmiregistry $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/rmiregistry.1.gz rmiregistry.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/rmiregistry.1.gz
update-alternatives --auto rmiregistry
update-alternatives --install /usr/bin/unpack200 unpack200 /usr/lib/jvm/ia32-java-6-sun/jre/bin/unpack200 $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/unpack200.1.gz unpack200.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/unpack200.1.gz
update-alternatives --auto unpack200
update-alternatives --install /usr/bin/orbd orbd /usr/lib/jvm/ia32-java-6-sun/jre/bin/orbd $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/orbd.1.gz orbd.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/orbd.1.gz
update-alternatives --auto orbd
update-alternatives --install /usr/bin/servertool servertool /usr/lib/jvm/ia32-java-6-sun/jre/bin/servertool $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/servertool.1.gz servertool.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/servertool.1.gz
update-alternatives --auto servertool
update-alternatives --install /usr/bin/tnameserv tnameserv /usr/lib/jvm/ia32-java-6-sun/jre/bin/tnameserv $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/tnameserv.1.gz tnameserv.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/tnameserv.1.gz
update-alternatives --auto tnameserv
update-alternatives --install /usr/bin/HtmlConverter HtmlConverter /usr/lib/jvm/ia32-java-6-sun/bin/HtmlConverter $JAVA_PACKAGE_PRIORITY
update-alternatives --auto HtmlConverter
update-alternatives --install /usr/bin/appletviewer appletviewer /usr/lib/jvm/ia32-java-6-sun/bin/appletviewer $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/appletviewer.1.gz appletviewer.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/appletviewer.1.gz
update-alternatives --auto appletviewer
update-alternatives --install /usr/bin/apt apt /usr/lib/jvm/ia32-java-6-sun/bin/apt $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/apt.1.gz apt.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/apt.1.gz
update-alternatives --auto apt
update-alternatives --install /usr/bin/extcheck extcheck /usr/lib/jvm/ia32-java-6-sun/bin/extcheck $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/extcheck.1.gz extcheck.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/extcheck.1.gz
update-alternatives --auto extcheck
update-alternatives --install /usr/bin/idlj idlj /usr/lib/jvm/ia32-java-6-sun/bin/idlj $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/idlj.1.gz idlj.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/idlj.1.gz
update-alternatives --auto idlj
update-alternatives --install /usr/bin/jar jar /usr/lib/jvm/ia32-java-6-sun/bin/jar $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/jar.1.gz jar.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/jar.1.gz
update-alternatives --auto jar
update-alternatives --install /usr/bin/jarsigner jarsigner /usr/lib/jvm/ia32-java-6-sun/bin/jarsigner $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/jarsigner.1.gz jarsigner.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/jarsigner.1.gz
update-alternatives --auto jarsigner
update-alternatives --install /usr/bin/java-rmi.cgi java-rmi.cgi /usr/lib/jvm/ia32-java-6-sun/bin/java-rmi.cgi $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/java-rmi.cgi.1.gz java-rmi.cgi.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/java-rmi.cgi.1.gz
update-alternatives --auto java-rmi.cgi
update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/ia32-java-6-sun/bin/javac $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/javac.1.gz javac.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/javac.1.gz
update-alternatives --auto javac
update-alternatives --install /usr/bin/javadoc javadoc /usr/lib/jvm/ia32-java-6-sun/bin/javadoc $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/javadoc.1.gz javadoc.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/javadoc.1.gz
update-alternatives --auto javadoc
update-alternatives --install /usr/bin/javah javah /usr/lib/jvm/ia32-java-6-sun/bin/javah $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/javah.1.gz javah.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/javah.1.gz
update-alternatives --auto javah
update-alternatives --install /usr/bin/javap javap /usr/lib/jvm/ia32-java-6-sun/bin/javap $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/javap.1.gz javap.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/javap.1.gz
update-alternatives --auto javap
update-alternatives --install /usr/bin/jconsole jconsole /usr/lib/jvm/ia32-java-6-sun/bin/jconsole $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/jconsole.1.gz jconsole.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/jconsole.1.gz
update-alternatives --auto jconsole
update-alternatives --install /usr/bin/jdb jdb /usr/lib/jvm/ia32-java-6-sun/bin/jdb $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/jdb.1.gz jdb.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/jdb.1.gz
update-alternatives --auto jdb
update-alternatives --install /usr/bin/jhat jhat /usr/lib/jvm/ia32-java-6-sun/bin/jhat $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/jhat.1.gz jhat.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/jhat.1.gz
update-alternatives --auto jhat
update-alternatives --install /usr/bin/jinfo jinfo /usr/lib/jvm/ia32-java-6-sun/bin/jinfo $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/jinfo.1.gz jinfo.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/jinfo.1.gz
update-alternatives --auto jinfo
update-alternatives --install /usr/bin/jmap jmap /usr/lib/jvm/ia32-java-6-sun/bin/jmap $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/jmap.1.gz jmap.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/jmap.1.gz
update-alternatives --auto jmap
update-alternatives --install /usr/bin/jps jps /usr/lib/jvm/ia32-java-6-sun/bin/jps $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/jps.1.gz jps.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/jps.1.gz
update-alternatives --auto jps
update-alternatives --install /usr/bin/jrunscript jrunscript /usr/lib/jvm/ia32-java-6-sun/bin/jrunscript $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/jrunscript.1.gz jrunscript.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/jrunscript.1.gz
update-alternatives --auto jrunscript
update-alternatives --install /usr/bin/jsadebugd jsadebugd /usr/lib/jvm/ia32-java-6-sun/bin/jsadebugd $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/jsadebugd.1.gz jsadebugd.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/jsadebugd.1.gz
update-alternatives --auto jsadebugd
update-alternatives --install /usr/bin/jstack jstack /usr/lib/jvm/ia32-java-6-sun/bin/jstack $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/jstack.1.gz jstack.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/jstack.1.gz
update-alternatives --auto jstack
update-alternatives --install /usr/bin/jstat jstat /usr/lib/jvm/ia32-java-6-sun/bin/jstat $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/jstat.1.gz jstat.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/jstat.1.gz
update-alternatives --auto jstat
update-alternatives --install /usr/bin/jstatd jstatd /usr/lib/jvm/ia32-java-6-sun/bin/jstatd $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/jstatd.1.gz jstatd.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/jstatd.1.gz
update-alternatives --auto jstatd
update-alternatives --install /usr/bin/native2ascii native2ascii /usr/lib/jvm/ia32-java-6-sun/bin/native2ascii $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/native2ascii.1.gz native2ascii.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/native2ascii.1.gz
update-alternatives --auto native2ascii
update-alternatives --install /usr/bin/rmic rmic /usr/lib/jvm/ia32-java-6-sun/bin/rmic $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/rmic.1.gz rmic.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/rmic.1.gz
update-alternatives --auto rmic
update-alternatives --install /usr/bin/schemagen schemagen /usr/lib/jvm/ia32-java-6-sun/bin/schemagen $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/schemagen.1.gz schemagen.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/schemagen.1.gz
update-alternatives --auto schemagen
update-alternatives --install /usr/bin/serialver serialver /usr/lib/jvm/ia32-java-6-sun/bin/serialver $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/serialver.1.gz serialver.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/serialver.1.gz
update-alternatives --auto serialver
update-alternatives --install /usr/bin/wsgen wsgen /usr/lib/jvm/ia32-java-6-sun/bin/wsgen $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/wsgen.1.gz wsgen.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/wsgen.1.gz
update-alternatives --auto wsgen
update-alternatives --install /usr/bin/wsimport wsimport /usr/lib/jvm/ia32-java-6-sun/bin/wsimport $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/wsimport.1.gz wsimport.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/wsimport.1.gz
update-alternatives --auto wsimport
update-alternatives --install /usr/bin/xjc xjc /usr/lib/jvm/ia32-java-6-sun/bin/xjc $JAVA_PACKAGE_PRIORITY --slave /usr/share/man/man1/xjc.1.gz xjc.1.gz /usr/lib/jvm/ia32-java-6-sun/man/man1/xjc.1.gz
update-alternatives --auto xjc
update-alternatives --install /usr/lib/xulrunner-addons/plugins/javaplugin_oji.so xulrunner-addons-javaplugin.so /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so $JAVA_PACKAGE_PRIORITY
update-alternatives --auto xulrunner-addons-javaplugin.so
update-alternatives --install /usr/lib/firefox/plugins/javaplugin_oji.so firefox-javaplugin.so /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so $JAVA_PACKAGE_PRIORITY
update-alternatives --auto firefox-javaplugin.so
update-alternatives --install /usr/lib/iceape/plugins/javaplugin_oji.so iceape-javaplugin.so /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so $JAVA_PACKAGE_PRIORITY
update-alternatives --auto iceape-javaplugin.so
update-alternatives --install /usr/lib/iceweasel/plugins/javaplugin_oji.so iceweasel-javaplugin.so /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so $JAVA_PACKAGE_PRIORITY
update-alternatives --auto iceweasel-javaplugin.so
update-alternatives --install /usr/lib/mozilla/plugins/javaplugin_oji.so mozilla-javaplugin.so /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so $JAVA_PACKAGE_PRIORITY
update-alternatives --auto mozilla-javaplugin.so
update-alternatives --install /usr/lib/midbrowser/plugins/javaplugin_oji.so midbrowser-javaplugin.so /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so $JAVA_PACKAGE_PRIORITY
update-alternatives --auto midbrowser-javaplugin.so
update-alternatives --install /usr/lib/xulrunner/plugins/javaplugin_oji.so xulrunner-javaplugin.so /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so $JAVA_PACKAGE_PRIORITY
update-alternatives --auto xulrunner-javaplugin.so
update-alternatives --install /usr/lib/firefox-3.0/plugins/javaplugin_oji.so firefox-3.0-javaplugin.so /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so $JAVA_PACKAGE_PRIORITY
update-alternatives --auto firefox-3.0-javaplugin.so
#

```

To make this consistent with my /usr/lib/jvm/.ia32-java-6-sun.jinfo file, I changed it as well:
```

name=ia32-java-6-sun-1.6.0.06
alias=ia32-java-6-sun
priority=1075
section=non-free

jre ControlPanel /usr/lib/jvm/ia32-java-6-sun/jre/bin/ControlPanel
jre java /usr/lib/jvm/ia32-java-6-sun/jre/bin/java
jre java_vm /usr/lib/jvm/ia32-java-6-sun/jre/bin/java_vm
jre javaws /usr/lib/jvm/ia32-java-6-sun/jre/bin/javaws
jre jcontrol /usr/lib/jvm/ia32-java-6-sun/jre/bin/jcontrol
jre keytool /usr/lib/jvm/ia32-java-6-sun/jre/bin/keytool
jre pack200 /usr/lib/jvm/ia32-java-6-sun/jre/bin/pack200
jre policytool /usr/lib/jvm/ia32-java-6-sun/jre/bin/policytool
jre rmid /usr/lib/jvm/ia32-java-6-sun/jre/bin/rmid
jre rmiregistry /usr/lib/jvm/ia32-java-6-sun/jre/bin/rmiregistry
jre unpack200 /usr/lib/jvm/ia32-java-6-sun/jre/bin/unpack200
jre orbd /usr/lib/jvm/ia32-java-6-sun/jre/bin/orbd
jre servertool /usr/lib/jvm/ia32-java-6-sun/jre/bin/servertool
jre tnameserv /usr/lib/jvm/ia32-java-6-sun/jre/bin/tnameserv
jdk HtmlConverter /usr/lib/jvm/ia32-java-6-sun/bin/HtmlConverter
jdk appletviewer /usr/lib/jvm/ia32-java-6-sun/bin/appletviewer
jdk apt /usr/lib/jvm/ia32-java-6-sun/bin/apt
jdk extcheck /usr/lib/jvm/ia32-java-6-sun/bin/extcheck
jdk idlj /usr/lib/jvm/ia32-java-6-sun/bin/idlj
jdk jar /usr/lib/jvm/ia32-java-6-sun/bin/jar
jdk jarsigner /usr/lib/jvm/ia32-java-6-sun/bin/jarsigner
jdk java-rmi.cgi /usr/lib/jvm/ia32-java-6-sun/bin/java-rmi.cgi
jdk javac /usr/lib/jvm/ia32-java-6-sun/bin/javac
jdk javadoc /usr/lib/jvm/ia32-java-6-sun/bin/javadoc
jdk javah /usr/lib/jvm/ia32-java-6-sun/bin/javah
jdk javap /usr/lib/jvm/ia32-java-6-sun/bin/javap
jdk jconsole /usr/lib/jvm/ia32-java-6-sun/bin/jconsole
jdk jdb /usr/lib/jvm/ia32-java-6-sun/bin/jdb
jdk jhat /usr/lib/jvm/ia32-java-6-sun/bin/jhat
jdk jinfo /usr/lib/jvm/ia32-java-6-sun/bin/jinfo
jdk jmap /usr/lib/jvm/ia32-java-6-sun/bin/jmap
jdk jps /usr/lib/jvm/ia32-java-6-sun/bin/jps
jdk jrunscript /usr/lib/jvm/ia32-java-6-sun/bin/jrunscript
jdk jsadebugd /usr/lib/jvm/ia32-java-6-sun/bin/jsadebugd
jdk jstack /usr/lib/jvm/ia32-java-6-sun/bin/jstack
jdk jstat /usr/lib/jvm/ia32-java-6-sun/bin/jstat
jdk jstatd /usr/lib/jvm/ia32-java-6-sun/bin/jstatd
jdk native2ascii /usr/lib/jvm/ia32-java-6-sun/bin/native2ascii
jdk rmic /usr/lib/jvm/ia32-java-6-sun/bin/rmic
jdk schemagen /usr/lib/jvm/ia32-java-6-sun/bin/schemagen
jdk serialver /usr/lib/jvm/ia32-java-6-sun/bin/serialver
jdk wsgen /usr/lib/jvm/ia32-java-6-sun/bin/wsgen
jdk wsimport /usr/lib/jvm/ia32-java-6-sun/bin/wsimport
jdk xjc /usr/lib/jvm/ia32-java-6-sun/bin/xjc
plugin xulrunner-addons-javaplugin.so /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
plugin firefox-javaplugin.so /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
plugin iceape-javaplugin.so /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
plugin iceweasel-javaplugin.so /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
plugin mozilla-javaplugin.so /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
plugin midbrowser-javaplugin.so /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
plugin xulrunner-javaplugin.so /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
plugin firefox-3.0-javaplugin.so /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so

```

Now if you run
```

sudo sh ia32-java-6-sun.sh
sudo update-java-alternatives --plugin --set ia32-java-6-sun

```

This WILL set your alternatives, but it might not be enough to get your browser working correctly.  I can get ia32-java-6-sun to work on a 32-bit copy of firefox 2, 32-bit swiftweasel 2, etc.

I cannot get ia32-java-6-sun working on firefox 3.  firefox 3 only has a single installer for linux, unlike older versions that had architecture specific installers.

The only java plugin I can make work in firefox 3 on a 64-bit platfrom at all is gcj4.2, which is extremely buggy, and does not achieve desired results.

Use these scripts at your own risk, or use them to create your own alternatives, but either way, they illustrate how to create alternatives definitions.

FYI, your alternatives definitions are maintained in text files in /var/lib/dpkg/alternatives.  I DO NOT RECOMMEND manually editing these text files, as this can really screw up the synchronization with the /etc/alternatives links and the links to those links in the "real" locations.

---

