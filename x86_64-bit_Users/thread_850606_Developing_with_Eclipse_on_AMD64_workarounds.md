---
title: "Developing with Eclipse on AMD64: workarounds"
date: 2008-07-05
forum: x86 64-bit Users
---

### Post by Emblem Parade on 2008-07-05
Using Sun's Java 6 or OpenJDK 6 is currently not recommended for Linux on AMD64, as it can result in segmentation faults. [(See Launchpad bug.)]("https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/238066")

I hope to save you the time I wasted on trial and error. Here are my conclusions:

1. The default Ubuntu installation uses GCJ, but with it I've encountered numerous problems and crashes in Eclipse. I strongly recommend running Eclipse 3.2.2 on Sun's Java 5. Note that what you run Eclipse on does mean what you will run your applications on -- it's only the IDE. Eclipse simply runs best on Java 5 right now. Java 6 is inherently broken.

To install Java 5:

```
sudo aptitude install sun-java5-jdk
```

To make Eclipse use Java 5:

```
sudo gedit /etc/eclipse/java_home
```

...and make sure this line is the topmost of the list:

```
/usr/lib/jvm/java-1.5.0-sun
```

2. If you want to develop for Java 6, I recommend using Java 7 instead. It's still in beta, but it is fully backward compatible with Java 6, and unfortunately is the best we have while Java 6 is broken.

To install Java 7, download the latest binaries from [here]("http://download.java.net/jdk7/binaries/"). For Ubuntu, you want the "Linux X64 self-extracting JDK file." I recommend moving the directory to where all there other JVMs are. The command would be something like this:

```
sudo mv jdk1.7.0 /usr/lib/jvm/
```

Note that if you're usually afraid, for good reason, of installing software not from the Ubuntu repositories, that this is especially safe. All files installed are in that directory, and nowhere else. Simply delete the directory to uninstall.

To make Eclipse use Java 7 for your applications, go to Window -> Preferences -> Java -> Installed JREs, and add an entry for /usr/lib/jvm/jdk1.7.0 . You'll need to clean/rebuild workspace to make sure it uses the new JRE.

Good luck!

---

