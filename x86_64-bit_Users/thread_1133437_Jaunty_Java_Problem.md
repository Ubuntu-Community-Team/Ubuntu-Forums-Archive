---
title: "Jaunty Java Problem"
date: 2009-04-22
forum: x86 64-bit Users
---

### Post by Nintendo01 on 2009-04-22
I just upgraded from Intrepid to Jaunty and Vuze appears to be trying to use OpenJDK even though I uninstalled that months ago. Here's the error it gives when I try to open it in a terminal:

exec: 11: /usr/lib/jvm/java-6-openjdk/jre/bin/java: not found

I used [this guide]("http://ubuntuforums.org/showthread.php?t=1019314") to keep up to date with the latest 64 bit Java and Firefox plugin and Vuze always used that version. Before I tried opening Vuze after upgrading I had deleted all Java from /opt and removed the Firefox symlink and got Firefox up and running with the Sun Java in the repos. I don't know if it would have worked with the /opt version, but deleting it may have thrown something off.

Installing OpenJDK gets it working, but I'd rather just have Sun Java if that's possible.

Edit: I was just playing around on the terminal and discovered this:

```
wayne@wayne-desktop:~$ java -version
The program 'java' can be found in the following packages:
 * gij-4.3
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.2
 * jamvm
 * kaffe
Try: sudo apt-get install <selected package>
bash: java: command not found

```

Before it would give the version of the Java I had installed in /opt, but I expected the repo's version to kind of overwrite that. It seems that Jaunty doesn't think Sun Java provides Java.

---

### Post by Arup on 2009-04-23
Isn't latest Sun Java x64 included in Jaunty repos. If that is the case, I would suggest removing existing Java in the /opt folder and installing the Sun Java from the repos alone.

---

### Post by FredB on 2009-04-23
There is not a lot of difference between Sun and OpenJDK java version. Used some java programs - like RSSOwl, and they worked perfectly with OpenJDK.

---

### Post by jespdj on 2009-04-23
The latest Sun Java (Java 6 update 13) is in the Jaunty repository:
```
sudo apt-get install sun-java6-plugin
```
Note that there's finally a 64-bit Sun Java browser plugin. The command above will install the JRE and the plugin.

There's no need to install Sun Java manually.

---

### Post by Nintendo01 on 2009-04-23
Just to clarify, I have installed Sun Java and the Firefox plugin from the repositories. Before I upgraded to Jaunty I was installing Sun Java manually and making it my system's default Java using [this guide]("http://ubuntuforums.org/showthread.php?t=1019314"). I think that when I deleted the Java I had installed in my /opt folder it didn't un-set that as my system's default Java. I need to make Vuze use the Sun Java I have installed from the repositories, probably by setting it as the system's default Java.

Edit: I just figured out where the repositories puts Java by looking in Open Office, where it is using the correct Java. I did the update-alternatives part of the above mentioned guide to set my Java, and java -version is now reporting correctly. Unfortunately Vuze is still trying to find OpenJDK.

---

### Post by Clancy_s on 2009-04-23
> **Nintendo01 said:**
> Edit: I just figured out where the repositories puts Java by looking in Open Office, where it is using the correct Java. I did the update-alternatives part of the above mentioned guide to set my Java, and java -version is now reporting correctly. Unfortunately Vuze is still trying to find OpenJDK.

Vuze uses a script in ~/.azureus that tells it where to find java (amongst other things).  You can edit it to tell Vuze were java is.

I'd tell you the exact name but I can't remember it and won't be back on my ubuntu box for a couple of weeks...

IIRC it was pretty obvious when I knew where to look.

---

### Post by Nintendo01 on 2009-04-23
> **Clancy_s said:**
> Vuze uses a script in ~/.azureus that tells it where to find java (amongst other things).  You can edit it to tell Vuze were java is.

I'd tell you the exact name but I can't remember it and won't be back on my ubuntu box for a couple of weeks...

IIRC it was pretty obvious when I knew where to look.

I looked through there a couple of times and can't find anything that tells it where to look. Azureus.config seemed to be my best chance, but searching the word "java" turns up nothing.

Thanks for everyone's help so far.

---

### Post by remin8 on 2009-04-24
Hopefully, fixed once the storm settles down!

---

### Post by platinumriver on 2009-04-26
[https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/296880](https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/296880)


> 

I've also updated from 8.10 to 9.04, and i have java6 installed. It will still not work because the path to the java executable has changed. To fix it:

$ sudo gedit /usr/bin/azureus

change

JAVA='/usr/lib/jvm/java-6-openjdk/jre/bin/java -Xmx1024M'

to

JAVA='/usr/lib/jvm/java-6-sun/jre/bin/java -Xmx1024M'


---

### Post by Nintendo01 on 2009-04-26
Thank you very much! That worked perfectly!

---

### Post by mozartlova on 2009-05-15
> **platinumriver said:**
> [https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/296880](https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/296880)

thanks very much for your help ... it (still) works.

but i'm very surprised that this hasn't been 'fixed' since january ... where does the problem lie (i re-installed vuze and it (obviously?) uses the same '/usr/bin/azureus' script!!)?

---

### Post by marcelkoopman on 2009-05-16
Try downloading vuze from the website. Its much easier then using the debian packages.

---

### Post by ken78724 on 2009-05-16
Nintendo1 & Problem Solvers, 
 am interested and have questions here as I can't follow from what is said in the last sudo note. I too updated 8.10 intrepid to 9.04 and find I can't login on webinars requiring Java as I did in 8.10. Believe I did an 8.10 update that installed necessary Java plugins but may not have "kept /etc,,,, .tiny as the upgrade installed 9.04". [Have but am not sure if vuze.exe.tar.gz.jar on my desktop & don't believe I had done an install thereof; I got my java6 via a sudo getit update, if I recall.] 

Q 1: Is it possible I "erased" the java6 amidst the 9.04 upgrade?  
Q 2: Can the solution you arrived at where you already know you definitely had Java6 installed but not working like you want, be applied to assure that I may "install Java6" and end up having benefit of both java options]? [yes I SunJava6 and OpenJDK java]
Q 3: Can I make the following presumption and get to the java install application?  Presuming I could "hunt Java's presence on my Jaunty" I did an applications > accessories > terminal with 
$ sudo gedit /usr/bin/azureus    I opened an azureus window but no output came up & I could not make the change the last mentor gave you Nintendo1 

Q4: So, all told where do I go with this to bring Java up to speed so I can attend and produce webinars? My apologies if my questions are to much; if so, must I open a new thread?

kenneth koym ;)

---

### Post by ken78724 on 2009-05-16
> **marcelkoopman said:**
> Try downloading vuze from the website. Its much easier then using the debian packages.

Marcel, note in post 13, I have vuze on my desktop. I'm building toward webinar productions & ubuntu Studio; so, I want java and related "tools". 

When I tried to incorporate vuze about 45 days back, my hands when up & I went to no where quick... Perhaps you could share a method to get moving..

plz advise. Many thanks. 

kenneth koym

---

### Post by isparkes on 2009-05-19
I think the root problem is that you are trying to run a 32 bit Java on a 64 bit machine. By default the libraries are not installed to do this in x64. To get them:

```
sudo apt-get install ia32-libs
```

you should then fine that things with a bundled jre start to work

---

### Post by letmekilluplz on 2009-06-24
I had the same problem so I changed the "JAVA=" thing and now I get.

```
exec: 11: -Djava.library.path=/usr/lib/jni:/usr/lib: not found

```

EDIT - I just realized I incorrectly entered the fix My Bad

---

