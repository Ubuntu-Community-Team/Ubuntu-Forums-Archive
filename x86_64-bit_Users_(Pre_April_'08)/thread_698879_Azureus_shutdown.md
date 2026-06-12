---
title: "Azureus shutdown"
date: 2008-02-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fleece Flamingo on 2008-02-16
Yesterday I just switched from i386 to 64bit and now I can no longer start Azureus. It will boot up and then close. Terminal says this
```
pj@pj-desktop:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b598d479e11, pid=12850, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /home/pj/.azureus/hs_err_pid12850.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
pj@pj-desktop:~$ 

```

---

### Post by jpkotta on 2008-02-16
This is a known issue with Iced Tea JVM.  I use Sun Java.  It's not enough to use update-alternatives, because Azureus thinks it knows better, and uses Iced Tea if it's installed no matter what.

I editted /usr/bin/azureus so that it used whatever Java is the default.  Alternatively, you can set the AZUREUS_JAVA environment variable.

```

if [ x$AZUREUS_JAVA = x ]; then
   echo "Looking for and picking a preferred Java runtime"
   echo "Use environment AZUREUS_JAVA to override"
#   if [ -f /usr/lib/jvm/java-7-icedtea/jre/bin/java ]; then
#      JAVA='/usr/lib/jvm/java-7-icedtea/jre/bin/java'
#   elif [ -f /usr/lib/jvm/java-6-sun/jre/bin/java ]; then
#      JAVA='/usr/lib/jvm/java-6-sun/jre/bin/java'
#   elif [ -f /usr/lib/jvm/java-1.5.0-sun/jre/bin/java ]; then
#      JAVA='/usr/lib/jvm/java-1.5.0-sun/jre/bin/java'
#   else
      echo '******** WARNING **********'
      echo 'Unable to find a supported Java runtime'
      echo 'Going to assume java is in your PATH'
      echo '****************************'
      JAVA='java'
#   fi
else
   # User explicitly set an AZUREUS_JAVA; let's use it!
   echo "Java Runtime specified using AZUREUS_JAVA environment"
   JAVA=$AZUREUS_JAVA
fi

```

---

### Post by Fleece Flamingo on 2008-02-18
thanks man

---

### Post by thebrandon on 2008-03-20
I am having a similar problem to the one stated above only the changes that I made to /usr/bin/azureus didnt fix the problem.

Before :

```
brandon@brandon-desktop:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb47fc74b, pid=10413, tid=3084987280
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0_03-b05 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0xb74b]
#
# An error report file with more information is saved as hs_err_pid10413.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

After Change :

```
brandon@brandon-desktop:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
******** WARNING **********
Unable to find a supported Java runtime
Going to assume java is in your PATH
****************************
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb472c74b, pid=10629, tid=3084135312
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0_03-b05 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0xb74b]
#
# An error report file with more information is saved as hs_err_pid10629.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

Did I do something wrong?  Here is a copy of my /usr/bin/azureus , just in case!

```
#!/bin/sh

dir=~/.azureus
[ -d $dir ] || mkdir -p $dir

# update symlinks to included plugins

[ -d $dir/plugins ] || mkdir -p $dir/plugins
for d in $dir/plugins/*; do
  [ -h $d ] || continue
  [ -e $d ] || rm -f $d
done
for d in /usr/share/azureus/plugins/*; do
  p=$(basename $d)
  [ -e $dir/plugins/$p ] || ln -s $d $dir/plugins/$p
done

cd ~/.azureus

CP=/usr/share/java/bcprov.jar
CP=$CP:/usr/share/java/log4j-1.2.jar
CP=$CP:/usr/share/java/commons-cli.jar
CP=$CP:/usr/lib/java/swt3.2-gtk.jar
CP=$CP:/usr/share/java/glib0.4.jar
CP=$CP:/usr/share/java/cairo1.0.jar
CP=$CP:/usr/share/java/gtk2.10.jar

JAVA=java
if [ x$AZUREUS_JAVA = x ]; then
   echo "Looking for and picking a preferred Java runtime"
   echo "Use environment AZUREUS_JAVA to override"
#   if [ -f /usr/lib/jvm/java-7-icedtea/jre/bin/java ]; then
#      JAVA='/usr/lib/jvm/java-7-icedtea/jre/bin/java'
#   elif [ -f /usr/lib/jvm/java-6-sun/jre/bin/java ]; then
#      JAVA='/usr/lib/jvm/java-6-sun/jre/bin/java'
#   elif [ -f /usr/lib/jvm/java-1.5.0-sun/jre/bin/java ]; then
#      JAVA='/usr/lib/jvm/java-1.5.0-sun/jre/bin/java'
#   else
      echo '******** WARNING **********'
      echo 'Unable to find a supported Java runtime'
      echo 'Going to assume java is in your PATH'
      echo '****************************'
      JAVA='java'
#   fi
else
   # User explicitly set an AZUREUS_JAVA; let's use it!
   echo "Java Runtime specified using AZUREUS_JAVA environment"
   JAVA=$AZUREUS_JAVA
fi

if [ -n "$JAVA_HOME" ]; then
    PATH="$JAVA_HOME/bin:$PATH"
fi

LD_LIBRARY_PATH=${LD_LIBRARY_PATH:+$LD_LIBRARY_PATH:}/usr/lib/jni
export LD_LIBRARY_PATH

exec java -Djava.library.path=/usr/lib/jni:/usr/lib \
	-Dgnu.gcj.runtime.VMClassLoader.library_control=never \
	-Dazureus.install.path=$dir \
	-classpath /usr/share/java/Azureus2.jar:$CP \
	org.gudy.azureus2.ui.swt.Main "$@"
```

---

