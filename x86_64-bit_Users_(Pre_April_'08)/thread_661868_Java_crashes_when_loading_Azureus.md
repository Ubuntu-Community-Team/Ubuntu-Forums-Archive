---
title: "Java crashes when loading Azureus"
date: 2008-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Antarctica on 2008-01-08
Hey all, I'm having problems running Azureus.  It loads for a couple seconds and then crashes.  I'm running 64-bit Gutsy if that helps any.  Here's a copy of the output reported in the terminal.  I hope this can give you all a clue to what might be going on.
```
brett@brett-desktop:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'

** (SWT:22669): WARNING **: Invalid borders specified for theme pixmap:
        /home/brett/.themes/Cillop-Midnite/gtk-2.0/null.png,
borders don't fit within the image
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b051ab07e11, pid=22669, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /home/brett/.azureus/hs_err_pid22669.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

Okay, I just found out that the theme I'm using (downloaded from art.gnome.org) might be the problem.  If it is, is there any way to get around that?  I just might switch bittorrent programs even though I love Azureus.

---

### Post by tomdkat on 2008-01-08
I can run Azureus just fine using the 64-bit JRE from Sun.  I don't use icedtea-java7 package.

Peace...

---

### Post by 6568912 on 2008-01-08
someone still using it? (o__O)
*damn i am being so rude SORRRRRRY!*

---

### Post by Antarctica on 2008-01-09
Yeah, then whoever made the Azureus guide for [www.ubuntuguide.org](www.ubuntuguide.org) should take down the icedtea-java7 part.  It obviously doesn't work on 64-bit.

---

### Post by carverj on 2008-01-15
The problem for me is that i needed to install icedtea-java7 package in order to run miro.
Now no Azureus!!?

Here is my output for reference to this predicament:

```

jeremy@jeremy-UBUNTU:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
changeLocale: *Default Language* != English (Australia). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Australia)' (en_AU), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b5bf5352e11, pid=7412, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /home/jeremy/.azureus/hs_err_pid7412.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
jeremy@jeremy-UBUNTU:~$ sudo update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/lib/jvm/ia32-java-6-sun/jre/bin/java
*+        4    /usr/lib/jvm/java-7-icedtea/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.
jeremy@jeremy-UBUNTU:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
changeLocale: *Default Language* != English (Australia). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Australia)' (en_AU), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b96069fbe11, pid=7473, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /home/jeremy/.azureus/hs_err_pid7473.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
jeremy@jeremy-UBUNTU:~$ miro
/usr/lib/firefox
INFO     Starting up Miro
INFO     Version:    1.1
INFO     Revision:   https://svn.participatoryculture.org/svn/dtv/tags/Miro-1.1/tv/resources - 5991
INFO     Builder:    pbuilder@mercury
INFO     Build Time: 1200071857.24
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/jeremy/.miro/sqlitedb
TIMING   Database load slow: 2.476
TIMING   idle (Initializing database) too slow (2.958 secs)
INFO     Spawning auto downloader...
INFO     Displaying main frame...
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
WARNING  Volume changed before videoDisplay created
WARNING  Display updated before video display was created
INFO     Creating video display...
INFO     *** Launching Downloader Daemon ****
INFO     loaded renderer 'xinerenderer'
TIMING   gtkAsyncMethod: <function initRenderers at 0x1148b18> took too long: 1.286
TIMING   gtkSyncMethod: <function getDisplay at 0x1215848> took too long: 1.287
INFO     First URL is https://www.miroguide.com/
INFO     got file:///tmp/tmp_oZj1C.html
TIMING   gtkAsyncMethod: <function selectDisplay at 0x1215758> took too long: 3.227
TIMING   Icon clear: 3.321
INFO     Starting movie data updates
INFO     Finished startup sequence
TIMING   idle (finalizing startup) too slow (5.530 secs)
TIMING   idle (finalizing startup) cumulative is too slow (5.530 secs)
INFO     got file:///tmp/tmp39RHsT.html
INFO     *** Daemon ready ***
INFO     got https://www.miroguide.com/
LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /home/jeremy/.mozilla/plugins/libflashplayer.so [/home/jeremy/.mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /home/jeremy/mozilla/nphelix.so [/home/jeremy/mozilla/nphelix.so: wrong ELF class: ELFCLASS32]
INFO     got action:handleSelect?area=tablist&viewName=staticTabs&id=1569&shiftDown=0&ctrlDown=0
INFO     got file:///tmp/tmpjGkwzr.html
WARNING  eventloop: Interrupted system call
WARNING  eventloop: Interrupted system call
WARNING  Error resizing /home/jeremy/.miro/icon-cache/unknown.29895307 to 20x20:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/miro/imageresize.py", line 49, in multiResizeImage
    resizeImage(source_filename, resizedPath, width, height)
  File "/var/lib/python-support/python2.5/miro/platformutils.py", line 224, in resizeImage
    ignore_stderr=True)
  File "/var/lib/python-support/python2.5/miro/util.py", line 705, in call_command
    (args, pipe.returncode, stdout, stderr))
OSError: call_command with ('/usr/bin/convert', '/home/jeremy/.miro/icon-cache/unknown.29895307', '-strip', '-resize', '20x20>', '-gravity', 'center', '-bordercolor', 'black', '-border', '10', '-crop', '20x20+0+0', '+repage', '/home/jeremy/.miro/icon-cache/unknown.20x20.29895307') has return code 1
stdout:
stderr:convert: missing an image filename `/home/jeremy/.miro/icon-cache/unknown.20x20.29895307'.


WARNING  Error resizing /home/jeremy/.miro/icon-cache/unknown.29895307 to 76x76:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/miro/imageresize.py", line 49, in multiResizeImage
    resizeImage(source_filename, resizedPath, width, height)
  File "/var/lib/python-support/python2.5/miro/platformutils.py", line 224, in resizeImage
    ignore_stderr=True)
  File "/var/lib/python-support/python2.5/miro/util.py", line 705, in call_command
    (args, pipe.returncode, stdout, stderr))
OSError: call_command with ('/usr/bin/convert', '/home/jeremy/.miro/icon-cache/unknown.29895307', '-strip', '-resize', '76x76>', '-gravity', 'center', '-bordercolor', 'black', '-border', '38', '-crop', '76x76+0+0', '+repage', '/home/jeremy/.miro/icon-cache/unknown.76x76.29895307') has return code 1
stdout:
stderr:convert: missing an image filename `/home/jeremy/.miro/icon-cache/unknown.76x76.29895307'.


WARNING  Error resizing /home/jeremy/.miro/icon-cache/unknown.29895307 to 108x81:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/miro/imageresize.py", line 49, in multiResizeImage
    resizeImage(source_filename, resizedPath, width, height)
  File "/var/lib/python-support/python2.5/miro/platformutils.py", line 224, in resizeImage
    ignore_stderr=True)
  File "/var/lib/python-support/python2.5/miro/util.py", line 705, in call_command
    (args, pipe.returncode, stdout, stderr))
OSError: call_command with ('/usr/bin/convert', '/home/jeremy/.miro/icon-cache/unknown.29895307', '-strip', '-resize', '108x81>', '-gravity', 'center', '-bordercolor', 'black', '-border', '54', '-crop', '108x81+0+0', '+repage', '/home/jeremy/.miro/icon-cache/unknown.108x81.29895307') has return code 1
stdout:
stderr:convert: missing an image filename `/home/jeremy/.miro/icon-cache/unknown.108x81.29895307'.


WARNING  Error resizing /home/jeremy/.miro/icon-cache/unknown.29895307 to 226x170:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/miro/imageresize.py", line 49, in multiResizeImage
    resizeImage(source_filename, resizedPath, width, height)
  File "/var/lib/python-support/python2.5/miro/platformutils.py", line 224, in resizeImage
    ignore_stderr=True)
  File "/var/lib/python-support/python2.5/miro/util.py", line 705, in call_command
    (args, pipe.returncode, stdout, stderr))
OSError: call_command with ('/usr/bin/convert', '/home/jeremy/.miro/icon-cache/unknown.29895307', '-strip', '-resize', '226x170>', '-gravity', 'center', '-bordercolor', 'black', '-border', '113', '-crop', '226x170+0+0', '+repage', '/home/jeremy/.miro/icon-cache/unknown.226x170.29895307') has return code 1
stdout:
stderr:convert: missing an image filename `/home/jeremy/.miro/icon-cache/unknown.226x170.29895307'.



jeremy@jeremy-UBUNTU:~$ WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...
Exception exceptions.KeyboardInterrupt in <module 'threading' from '/usr/lib/python2.5/threading.pyc'> ignored

jeremy@jeremy-UBUNTU:~$ sudo update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/lib/jvm/ia32-java-6-sun/jre/bin/java
 +        4    /usr/lib/jvm/java-7-icedtea/jre/bin/java

Press enter to keep the default[*], or type selection number: 1
Using `/usr/bin/gij-4.2' to provide `java'.
jeremy@jeremy-UBUNTU:~$ sudo update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/bin/gij-4.2
          2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/lib/jvm/ia32-java-6-sun/jre/bin/java
 +        4    /usr/lib/jvm/java-7-icedtea/jre/bin/java

Press enter to keep the default[*], or type selection number: 
jeremy@jeremy-UBUNTU:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
changeLocale: *Default Language* != English (Australia). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Australia)' (en_AU), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b5da8116e11, pid=7979, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /home/jeremy/.azureus/hs_err_pid7979.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
jeremy@jeremy-UBUNTU:~$ sudo aptitude remove icedtea-java7-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  icedtea-java7-plugin 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 131kB will be freed.
Writing extended state information... Done
(Reading database ... 119677 files and directories currently installed.)
Removing icedtea-java7-plugin ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
jeremy@jeremy-UBUNTU:~$ sudo update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/bin/gij-4.2
          2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/lib/jvm/ia32-java-6-sun/jre/bin/java
 +        4    /usr/lib/jvm/java-7-icedtea/jre/bin/java

Press enter to keep the default[*], or type selection number: 
jeremy@jeremy-UBUNTU:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
changeLocale: *Default Language* != English (Australia). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Australia)' (en_AU), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002ab9e16f0e11, pid=8072, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /home/jeremy/.azureus/hs_err_pid8072.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
jeremy@jeremy-UBUNTU:~$ miro
/usr/lib/firefox
INFO     Starting up Miro
INFO     Version:    1.1
INFO     Revision:   https://svn.participatoryculture.org/svn/dtv/tags/Miro-1.1/tv/resources - 5991
INFO     Builder:    pbuilder@mercury
INFO     Build Time: 1200071857.24
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/jeremy/.miro/sqlitedb
TIMING   Database load slow: 1.829
TIMING   idle (Initializing database) too slow (2.357 secs)
INFO     *** Launching Downloader Daemon ****
INFO     Spawning auto downloader...
INFO     Displaying main frame...
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
WARNING  Volume changed before videoDisplay created
WARNING  Display updated before video display was created
INFO     Creating video display...
INFO     loaded renderer 'xinerenderer'
TIMING   gtkAsyncMethod: <function initRenderers at 0x1148b18> took too long: 1.242
INFO     First URL is https://www.miroguide.com/
INFO     got file:///tmp/tmpnFFyhs.html
LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /home/jeremy/.mozilla/plugins/libflashplayer.so [/home/jeremy/.mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /home/jeremy/mozilla/nphelix.so [/home/jeremy/mozilla/nphelix.so: wrong ELF class: ELFCLASS32]
TIMING   Icon clear: 0.165
INFO     Starting movie data updates
INFO     Finished startup sequence
TIMING   idle (finalizing startup) too slow (2.818 secs)
INFO     got file:///tmp/tmpWVDrI_.html
INFO     got https://www.miroguide.com/
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
INFO     *** Daemon ready ***

jeremy@jeremy-UBUNTU:~$ WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...
TIMING   WARNING: Calling <bound method DownloaderDaemon.closeCallback of <dl_daemon.daemon.DownloaderDaemon object at 0xc9fad0>> on AsyncSocket: Outgoing 127.0.0.1:57464 too slow (1.128 secs)
Exception exceptions.KeyboardInterrupt in <module 'threading' from '/usr/lib/python2.5/threading.pyc'> ignored


```

---

### Post by Skerit on 2008-01-20
I recently found a way to fix this on the forums, I can't find it again I'm afraid, but I still have the command:

in /usr/lib/jvm execute ...

sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so 

You need to change "1.6.0.04" to the correct version number, of course...
Basically the problem should be caused by java itself, not azureus.

---

### Post by prince_niceguy on 2008-01-27
use sun java and change your azureus script to point to the sun java install.

it should work. i am using sun java and azureus runs smoothly..

---

