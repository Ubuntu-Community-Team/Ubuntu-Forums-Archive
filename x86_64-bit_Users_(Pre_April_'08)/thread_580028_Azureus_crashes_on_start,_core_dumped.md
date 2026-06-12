---
title: "Azureus crashes on start, core dumped"
date: 2007-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Zorael on 2007-10-18
It draws the interface, but it only shows as a flash, then it crashes and displays the following in the terminal:

```
zorael@azrael:~$ azureus &
[1] 7129
zorael@azrael:~$ #
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b6918c58331, pid=7129, tid=1076017488
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0_03-b05 mixed mode)
# Problematic frame:
# V  [libjvm.so+0x336331]
#
# An error report file with more information is saved as hs_err_pid7129.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#

[1]+  Aborted                 (core dumped) azureus
zorael@azrael:~$

```

I'm running Java 6. I'll add that log file as an attachment.


Any ideas? :(

---

### Post by Zorael on 2007-10-18
It starts if I do:
```
$ rm -rf ~/.azureus/logs
```

Very odd?

What does that folder contain, anyway? Would it be safe to add that line to a startup script, or would I be shooting myself in the foot?

---

### Post by Kilz on 2007-10-18
> **Zorael said:**
> It starts if I do:
```
$ rm -rf ~/.azureus/logs
```

Very odd?

What does that folder contain, anyway? Would it be safe to add that line to a startup script, or would I be shooting myself in the foot?

Thats the logs, you might want to look at the reason why removing them lets azerus start. Perhaps they cant be written to. If not it cant hurt to wipe the logs, in fact maybe turn off logging to see if it helps.

---

### Post by easyease on 2007-10-18
same problem here on a fresh gutsy install. very annoying.

---

### Post by Kilz on 2007-10-18
> **easyease said:**
> same problem here on a fresh gutsy install. very annoying.

I bet this comes from people thinking someone else will report the bug and not filing a bug report during development.

---

### Post by conehead77 on 2007-10-19
> **Kilz said:**
> I bet this comes from people thinking someone else will report the bug and not filing a bug report during development.

Its a known bug, i saw the bug report for it some weeks ago. When Azureus crashes, it will close immediately after startup.
Deleting the log files is the only known workaround yet i believe.

Well, i switched to Deluge anyhow :)

---

### Post by waza456 on 2007-10-19
I' ve had the same problem with azureus in the past. Then i managed to fix it by typing 
```
sudo update-alternatives --config java

``` and selecting one of the alternatives. However, now i just upgraded to gutsy, and the same problem appeared, but none of the alternatives seems to do the work. I don't if this can help you, but you may try it out and tell us. 

ps: i just used this trick to fix frostwire, which also was not willing to start and get to work :-)

---

### Post by Lord C on 2007-10-19
Same problem here, on regular 32bit Gutsy.

Thanks for the tip about removing log files.
How weird though.

I also have to Open torrent files manually through Azureus. If I try double-clicking a .torrent file, Azureus will crash, and I will have to remove the logs again.
Something seriously wrong there.

---

### Post by luctor on 2007-10-19
I'm not at my ubuntu box at the moment so I have to do this out of my head

I've installed sun-java6-jre, remove the other java stuff (gij I think ..)

that fixed it.

be sure to check sudo update-alternatives --config java :-)

---

### Post by tomdkat on 2007-10-19
Are you all running this version of the Java runtime:

# Java VM: Java HotSpot(TM) 64-Bit Server VM (**1.6.0_03-b05** mixed mode)

I haven't had any problems with either Azureus or FrostWire on either Feisty Fawn or after my recent upgrade to Gutsy Gibbon BUT I'm running JRE 1.6.0_02, not 03.  The Gutsy Gibbon upgrade left my Java environment alone and Frostwire "just worked".

I wonder if these problems are related to some change in the JRE from 1.6.0_02 and 1.0.6_03.

Peace...

---

### Post by LavianoTS386 on 2007-10-19
When I upgraded to Gusty the installer removed azureus, because it knew it wouldn't work (this is when Gutsy was still in Tibe 5)

---

### Post by kejar31 on 2007-10-19
I resolved the problem

first install Azureus via apt-get

```

sudo apt-get install azureus

```

now download Azureus 2.5.0.4 from here

[http://sourceforge.net/project/showfiles.php?group_id=84122&package_id=88270&release_id=481206](http://sourceforge.net/project/showfiles.php?group_id=84122&package_id=88270&release_id=481206)

make sure you get the 64 bit one.

copy Azureus2.jar to /usr/share/java

```

sudo cp ~/azureus/Azureus2.jar /usr/share/java/

```
now open Azureus at least once with your own account (other wise you will get that crappy vuze interface with your account after installing updates)

now exit Azureus

at a command prompt type 

```

sudo azureus

```

install all updates (when it asks you to restart tell it you will restart later then exit and restart again with sudo azureus until all updates are complete)

When all updates are complete make sure you open azureus as yourself and go out and grab the safepeer plugin ;-)

---

### Post by yang on 2007-10-20
The cause of this error for me is trying to open a torrent file "externally", e.g. by double-clicking on a torrent file in Nautilus (I've associated Azureus with torrents). Thereafter, launching Azureus immediately exits. Opening torrents from within Azureus works fine, though.

Removing the logs directory works (thanks - before I was removing my whole .azureus).

---

### Post by Misbah on 2007-10-20
Add another one to the problem. Everything else works GREAT on me for gutsy. No wireless problems with my Linksys card, no driver issues with my 7800GT, just.. azureus. Flashes up, crashes. But for me erasing the logs does nothing. Heres some code, similar to the previous posters core dump.

```
misbah@misbuntu:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Sat Oct 20 04:58:26 CDT 2007::org.gudy.azureus2.pluginsimpl.local.PluginInitializer::loadPluginFromDir::881:
  java.lang.ClassNotFoundException: com.azureus.plugins.azemp.EmbeddedMediaPlayerPlugin
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPluginFromDir(PluginInitializer.java:820)
        at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPluginsFromDir(PluginInitializer.java:510)
        at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPlugins(PluginInitializer.java:318)
        at com.aelitis.azureus.core.impl.AzureusCoreImpl.start(AzureusCoreImpl.java:313)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.run(Initializer.java:311)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread$1.runSupport(SWTThread.java:115)
        at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
        at java.lang.Thread.run(Thread.java:619)

Error loading plugin 'azemp' / 'com.azureus.plugins.azemp.EmbeddedMediaPlayerPlugin' : java.lang.ClassNotFoundException: com.azureus.plugins.azemp.EmbeddedMediaPlayerPlugin
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb474d74b, pid=8751, tid=3084188560
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0_03-b05 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0xb74b]
#
# An error report file with more information is saved as hs_err_pid8751.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
misbah@misbuntu:~$ 

```

EDIT: this is with 3.0.3.4 written over whatever I got through synaptic.

---

### Post by easyease on 2007-10-20
> **Kilz said:**
> I bet this comes from people thinking someone else will report the bug and not filing a bug report during development.
good ponit, i hold my hands  up on this one, i didnt think of reporting the bug.i just came here as my first port of call to see  if anyone else had the problem.

---

### Post by reckor on 2007-10-20
Hello all!

I'm not using 64-bit system but I have almost the same problem.
Here goes my log:

======================================
DEBUG::Sat Oct 20 18:03:08 GMT-03:00 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,ConfigurationChecker::setSystemProperties::145,ConfigurationManager::initialise::138,ConfigurationManager::getInstance::71,LoggerImpl::init::90,Logger::<clinit>::48,Class::initializeClass::-1,StartServer::<init>::70,Main::<init>::56,Main::main::162
changeLocale: *Default Language* != en (US). Searching without country..
changeLocale: Searching for language en in *any* country..
changeLocale: no message properties for Locale 'en (US)' (en_US), using 'English (default)'
DEBUG::Sat Oct 20 18:03:10 GMT-03:00 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,CryptoManagerImpl::<init>::73,CryptoManagerImpl::getSingleton::60,CryptoManagerFactory::getSingleton::33,AzureusCoreImpl::<init>::155,AzureusCoreImpl::create::92,AzureusCoreFactory::create::46,Main::<init>::143,Main::main::162
DEBUG::Sat Oct 20 18:03:15 GMT-03:00 2007::com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualBlockingServerChannelSelector::accept_loop::138:
    VirtualBlockingServerChannelSelector$1::runSupport::85,AEThread::run::69
java.lang.NullPointerException
   at gnu.java.nio.ServerSocketChannelImpl.accept(libgcj.so.81)
   at com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualBlockingServerChannelSelector.accept_loop(VirtualBlockingServerChannelSelector.java:129)
   at com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualBlockingServerChannelSelector$1.runSupport(VirtualBlockingServerChannelSelector.java:85)
   at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)

[1]+  Aborted                 (core dumped) azureus
==============================================

There isn't any JAVA problem as I could guess. 
I tried to remove the log but still the same.

Does anyone can help me?

Thanks in advance!

---

### Post by marcw on 2007-10-20
> **conehead77 said:**
> Its a known bug, i saw the bug report for it some weeks ago. When Azureus crashes, it will close immediately after startup.
Deleting the log files is the only known workaround yet i believe.

[https://bugs.launchpad.net/ubuntu/gutsy/+source/azureus/+bug/68020](https://bugs.launchpad.net/ubuntu/gutsy/+source/azureus/+bug/68020)

It looks like this bug has been around awhile.  I'd have thought that it would've been fixed by now.

---

### Post by misterbeetz on 2007-10-20
> **marcw said:**
> [https://bugs.launchpad.net/ubuntu/gutsy/+source/azureus/+bug/68020](https://bugs.launchpad.net/ubuntu/gutsy/+source/azureus/+bug/68020)

It looks like this bug has been around awhile.  I'd have thought that it would've been fixed by now.

Yeah, I just had this problem a couple of minutes ago on 32-bit Gutsy.  Removing the log files did not work for me so I used a confirmed solution in that bug report which was to install:

azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb

I got the package from here and installing it fixed the problem:

[http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb)

- misterbeetz

---

### Post by reckor on 2007-10-20
> **reckor said:**
> Hello all!

I'm not using 64-bit system but I have almost the same problem.
Here goes my log:

======================================
DEBUG::Sat Oct 20 18:03:08 GMT-03:00 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,ConfigurationChecker::setSystemProperties::145,ConfigurationManager::initialise::138,ConfigurationManager::getInstance::71,LoggerImpl::init::90,Logger::<clinit>::48,Class::initializeClass::-1,StartServer::<init>::70,Main::<init>::56,Main::main::162
changeLocale: *Default Language* != en (US). Searching without country..
changeLocale: Searching for language en in *any* country..
changeLocale: no message properties for Locale 'en (US)' (en_US), using 'English (default)'
DEBUG::Sat Oct 20 18:03:10 GMT-03:00 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,CryptoManagerImpl::<init>::73,CryptoManagerImpl::getSingleton::60,CryptoManagerFactory::getSingleton::33,AzureusCoreImpl::<init>::155,AzureusCoreImpl::create::92,AzureusCoreFactory::create::46,Main::<init>::143,Main::main::162
DEBUG::Sat Oct 20 18:03:15 GMT-03:00 2007::com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualBlockingServerChannelSelector::accept_loop::138:
    VirtualBlockingServerChannelSelector$1::runSupport::85,AEThread::run::69
java.lang.NullPointerException
   at gnu.java.nio.ServerSocketChannelImpl.accept(libgcj.so.81)
   at com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualBlockingServerChannelSelector.accept_loop(VirtualBlockingServerChannelSelector.java:129)
   at com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualBlockingServerChannelSelector$1.runSupport(VirtualBlockingServerChannelSelector.java:85)
   at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)

[1]+  Aborted                 (core dumped) azureus
==============================================

There isn't any JAVA problem as I could guess. 
I tried to remove the log but still the same.

Does anyone can help me?

Thanks in advance!

> **misterbeetz said:**
> Yeah, I just had this problem a couple of minutes ago on 32-bit Gutsy.  Removing the log files did not work for me so I used a confirmed solution in that bug report which was to install:

azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb

I got the package from here and installing it fixed the problem:

[http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb)

- misterbeetz

HI there!
Thanks Misterbeetz! It has worked with this package!

Regards!

---

### Post by tobyglenn on 2007-10-21
I just ran across the same problem with azureus with Ubuntu Gutsy. I fixed it for myself using the 64 bit instructions but just downloading the 32 bit version. So, this is what I did to fix the azureus Aborted (core dumped) error. [LIST=1]
[*]Go to [http://sourceforge.net/project/showf...ease_id=481206](http://sourceforge.net/project/showf...ease_id=481206) and download the 32bit version of azureus (the tar.gz independent)
[*]Unpack it with the unarchiver and put it in your home folder
[*]Then run this command sudo cp ~/azureus/Azureus2.jar /usr/share/java/
[*]Launch azureus from the command line with the command azureus
[/LIST]
It sounds to easy to be true but that is all it took for me to get azureus to work on my machine. let me know if that works for all the rest of the 32bit users having this problem.

---

### Post by marcw on 2007-10-22
> **misterbeetz said:**
> Yeah, I just had this problem a couple of minutes ago on 32-bit Gutsy.  Removing the log files did not work for me so I used a confirmed solution in that bug report which was to install:

azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb

I got the package from here and installing it fixed the problem:

[http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb)

- misterbeetz

I know this is a 64bit forum but I just wanted to say that this fix you found solved the 32bit gutsy crashing issue for me.  Thanks!

---

### Post by Polya on 2007-10-27
thanks

---

### Post by AbyssUK on 2007-10-27
> **misterbeetz said:**
> Yeah, I just had this problem a couple of minutes ago on 32-bit Gutsy.  Removing the log files did not work for me so I used a confirmed solution in that bug report which was to install:

azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb

I got the package from here and installing it fixed the problem:

[http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb)

- misterbeetz

This fixed it for me Thanks!

---

### Post by jonah1980 on 2007-10-27
try the new 3.0 deb: [http://www.getdeb.net/app.php?name=Azureus](http://www.getdeb.net/app.php?name=Azureus)

---

### Post by ubuntios on 2007-10-29
Hi guys , I had the same problem and I solve it with 2 steps


code : sudo wget [http://superb-west.dl.sourceforge.net/sourceforge/azureus/Azureus2.5.0.0.jar](http://superb-west.dl.sourceforge.net/sourceforge/azureus/Azureus2.5.0.0.jar)

code : sudo mv Azureus2.5.0.0.jar /usr/share/java/Azureus2.jar

start Azureus ..... Enjoy

Hope that helps

---

### Post by ema on 2007-10-30
> **misterbeetz said:**
> Yeah, I just had this problem a couple of minutes ago on 32-bit Gutsy.  Removing the log files did not work for me so I used a confirmed solution in that bug report which was to install:

azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb

I got the package from here and installing it fixed the problem:

[http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb)

- misterbeetz

This one worked for me too...

Ubuntu 7.10 32bit x86
--------------------------------------------
It doesn't crash anymore but seems like firewalled and doesn't download a byte...

---

### Post by drmatty on 2007-10-31
Is there any harm in removing the logs? That fix worked for me. Thanks.

---

### Post by aridhol on 2007-11-02
> **misterbeetz said:**
> Yeah, I just had this problem a couple of minutes ago on 32-bit Gutsy.  Removing the log files did not work for me so I used a confirmed solution in that bug report which was to install:

azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb

I got the package from here and installing it fixed the problem:

[http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb)

- misterbeetz


This also worked for me.

---

### Post by holotone on 2007-11-04
> **kejar31 said:**
> I resolved the problem

first install Azureus via apt-get

```

sudo apt-get install azureus

```

now download Azureus 2.5.0.4 from here

[http://sourceforge.net/project/showfiles.php?group_id=84122&package_id=88270&release_id=481206](http://sourceforge.net/project/showfiles.php?group_id=84122&package_id=88270&release_id=481206)

make sure you get the 64 bit one.

copy Azureus2.jar to /usr/share/java

```

sudo cp ~/azureus/Azureus2.jar /usr/share/java/

```
now open Azureus at least once with your own account (other wise you will get that crappy vuze interface with your account after installing updates)

now exit Azureus

at a command prompt type 

```

sudo azureus

```

install all updates (when it asks you to restart tell it you will restart later then exit and restart again with sudo azureus until all updates are complete)

When all updates are complete make sure you open azureus as yourself and go out and grab the safepeer plugin ;-)

Worked perfectly for me.. Thanks!

---

### Post by eggZter on 2007-11-12
> **aridhol said:**
> This also worked for me.

yup me too :) thanx guys

---

### Post by elec999 on 2007-11-17
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E4350500214), pid=8232, tid=3084254096
#
# Java VM: Java HotSpot(TM) Server VM (1.6.0_03-b05 mixed mode)
# An error report file with more information is saved as hs_err_pid8232.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)
Thanks

---

### Post by elec999 on 2007-11-17
> **ubuntios said:**
> Hi guys , I had the same problem and I solve it with 2 steps


code : sudo wget [http://superb-west.dl.sourceforge.net/sourceforge/azureus/Azureus2.5.0.0.jar](http://superb-west.dl.sourceforge.net/sourceforge/azureus/Azureus2.5.0.0.jar)

code : sudo mv Azureus2.5.0.0.jar /usr/share/java/Azureus2.jar

start Azureus ..... Enjoy

Hope that helps
Thank you, your way to work the best.
Thanks

---

### Post by Bozebus on 2007-12-02
None of the fixes I have found work for me. I have uninstalled azureus, removed every trace of it, and installed in apt, and even from the sourceforge files. I have had issues with openoffice locking up on me as well, and swiftfox crashing when I try to download something.

I think Gutsy is too buggy for my use, so I am reinstalling Edgy. Maybe they will fix these issues at a later time, I just prefer a more stable release.

---

### Post by DelTarrant on 2007-12-04
Hi

I was having the same problem with Azureus crashing out on startup on my Ubuntu AMD64 install hence eventually finding you guys, but found a workaround that worked for me. I uninstalled the opensource java7 and installed Sun's java6 jre. Now after reinstalling Azureus 2.5.0.4 using apt, it's now working OK.

Hope that helps.

---

### Post by limeric22 on 2007-12-07
> **luctor said:**
> I'm not at my ubuntu box at the moment so I have to do this out of my head

I've installed sun-java6-jre, remove the other java stuff (gij I think ..)

that fixed it.

be sure to check sudo update-alternatives --config java :-)
luctor's post #9 worked for me. thanks luctor.
By the way, i'm on gutsy gibbon 7.10 amd64 with azureus 2.5.

---

