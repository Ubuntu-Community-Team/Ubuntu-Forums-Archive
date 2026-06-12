---
title: "OpenJDK and Eclipse"
date: 2008-08-15
forum: x86 64-bit Users
---

### Post by brentnorin on 2008-08-15
Hi, I've just recently started using Ubuntu on my AMD64 environment, and so far no real problems in x64. I have flash working, and OpenJDK installed and working. I can run java commands from terminal, so I know it is working. Can't get applets in firefox working, but thats not a concern for now.

Anyways, my problem is after installing Eclipse 3.4 Ganymede, it won't find the OpenJDK! How can I change it to look for a different JDK instead of the default Sun one?

---

### Post by Nepherte on 2008-08-16
Do you mean you can't make a project using openjdk, or you can't run eclipse with openjdk? Eclipse has a file 'java_home' that says in what order it has to look for jvms. Open that file and put the directory pointing to your openjdk installation first.

You can get the java web browser plugin with entering this command:
```
sudo apt-get install icedtea-gcjwebplugin
```

---

### Post by IntuitiveNipple on 2008-08-16
To ensure Eclipse is using the OpenJDK:

Edit **~/.eclipse/eclipserc** and set **JAVA_HOME** to the path of the JVM (Java Virtual Machine) you require. The list of installed alternatives can be found using:
```

update-alternatives --list java

/usr/bin/gij-4.2
/usr/lib/jvm/java-6-openjdk/jre/bin/java
/usr/lib/jvm/java-gcj/jre/bin/java
/usr/lib/jvm/java-6-sun/jre/bin/java
/usr/lib/jvm/ia32-java-6-sun/jre/bin/java

```
The paths above point to the executable JRE (Java Run-time Environment). The Eclipse *JAVA_HOME* is the path up to *and including* the forward-slash before **jre/bin/java**, e.g. "/usr/lib/jvm/java-6-openjdk/".

The quick way to set the required JAVA_HOME is this:
```

JRE=$(update-alternatives --list java | grep openjdk) sed -i -e "s,^\(JAVA_HOME=.*\)$,#\1," -e "1 i\
JAVA_HOME=${JRE%%jre/bin/java*}
" ~/.eclipse/eclipserc

```
This code will cope with an existing JAVA_HOME by commenting it out whilst inserting a new line with the OpenJDK path.

**Note:** The command is typed over multiple lines so press Enter after "i\" and again after "*}". Copy the code above and paste directly into a terminal (Ctrl+Shift+V) to save on typing.

When started, Eclipse configuration shows:
```

java.home=/usr/lib/jvm/java-6-openjdk/jre
java.io.tmpdir=/tmp
java.library.path=/usr/lib/jni
java.runtime.name=OpenJDK  Runtime Environment
java.runtime.version=1.6.0_0-b11

```

---

### Post by brentnorin on 2008-08-16
Sorry i took so long to reply, was working. Thanks to both of you, I have eclipse running and working with me! I also got my java web start going. Thanks.

---

### Post by IntuitiveNipple on 2008-08-16
Did you have to do anything special to enable Java Web Start? If so, would you mind detailing the steps for others?

---

### Post by brentnorin on 2008-08-17
No I just installed OpenJDK from the package manager and then the GCJWebPlugin after that. Nothing special that isn't documented already.

---

