---
title: "Sun Studio Enterprise 8 + Ubuntu 64"
date: 2006-09-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by kopilo on 2006-09-07
Hi, I've never installed Sun's Java Studio Enterprise on linux before, so I thought I would give it a shot.

After downloading the 'jstudio_ent8_dl-linux-jds.sh' file, I opened a terminal and typed 'bash jstudio_ent8_dl-linux-jds.sh' which returned an error.
> This application requires a Java Run Time Environment (JRE) to run. Searching for one on your computer was not successful. Please use the command line switch -is:javahome to specify a valid JRE.  For more help use the option -is:help.
Thus then I tried running 'bash jstudio_ent8_dl-linux-jds.sh -is:javahome' but it only returned the same error...

Any suggestions? Should I be installing this in some other fashion?

:-k

---

### Post by Kilz on 2006-09-07
> **kopilo said:**
> Hi, I've never installed Sun's Java Studio Enterprise on linux before, so I thought I would give it a shot.

After downloading the 'jstudio_ent8_dl-linux-jds.sh' file, I opened a terminal and typed 'bash jstudio_ent8_dl-linux-jds.sh' which returned an error.

Thus then I tried running 'bash jstudio_ent8_dl-linux-jds.sh -is:javahome' but it only returned the same error...

Any suggestions? Should I be installing this in some other fashion?

:-k

Well from reading the error. 
> This application requires a Java Run Time Environment (JRE) to run You need to install a Java run time enviroment. When you install things from a .sh script it will not automaticly install requirements like apt/synaptic does. The script is telling you what it needs. Running the inscript with a different command is likely to give you the same error.
I know the blackdown java install off the top of my head
```
sudo apt-get install j2re1.4
```

---

### Post by kopilo on 2006-09-07
I have a JRE installed, opps should have stated that, well at any length I can already run jar files by typing java -jar *filename*
However the classpath variable shows as being blank.
...
Ohh well, *tries installation*, I'll post the version here later.

I noticed this during install; 
[COLOR="DarkRed"]dpkg - warning: downgrading j2re1.4 from 1.4.2.02-1ubuntu3 to 1.4.2.02-1.[/COLOR]

> java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) 64-Bit Server VM (build Blackdown-1.4.2-02, mixed mode)


Still same error occurs.

Ok I found [this]("http://blogs.sun.com/coldrick/entry/java_development_on_ubuntu_part3") website, I tried to display the JAVA_HOME path by typing in 'echo $JAVA_HOME' into terminal and it showed a blank line.

---

### Post by FluffyElmo on 2006-09-07
Try *java -version*, if the resulting text includes "*gij (GNU libgcj)*" then you're using the default gcj compiler and you'll need a better JVM. Download the Sun one from [java.sun.com]("http://java.sun.com") and  install it.

If you already have a real JVM installed then you have to provide the path to it to the installer. The command will probably be like this:
*jstudio_ent8_dl-linux-jds.sh -is:/home/username/jdk1.5.0_05/*

You can also export JAVA_HOME using the command (assuming bash):
*export JAVA_HOME=/home/username/jdk1.5.0_05/*

Hope this helps...

---

### Post by kopilo on 2006-09-07
Found this link which seems more relevent:
[http://blogs.sun.com/coldrick/entry/java_development_on_ubuntu_part2](http://blogs.sun.com/coldrick/entry/java_development_on_ubuntu_part2)

I hope this does not mean I require JDK to be installed to install something that the M$ Win version installs.

---

### Post by Kilz on 2006-09-07
> **kopilo said:**
> Found this link which seems more relevent:
[http://blogs.sun.com/coldrick/entry/java_development_on_ubuntu_part2](http://blogs.sun.com/coldrick/entry/java_development_on_ubuntu_part2)

I hope this does not mean I require JDK to be installed to install something that the M$ Win version installs.

Is the software you are installing 64bit?

---

### Post by FluffyElmo on 2006-09-07
Yes, you have to install a JDK, or a supported JVM which in this case is probably Suns. Simple to install, just download it at and run the install script. Then export the directory it's in as JAVA_HOME and run the installer for Studio Enterprise.

So long as the JVM/JDK you install is 64bit then you're fine. Java applications run cross-platform without modification unless they use external native libraries.

---

### Post by kopilo on 2006-09-07
I'm not sure, Java is meant to be platform independant.. Most likely written for 32 bit systems though.

I got the install from [here]("http://developers.sun.com/prodtech/devtools/free/")

Username: [email]960pnzwt72vjk4c@temporaryinbox.com[/email]
password: kilzrocks

---

### Post by kopilo on 2006-09-07
> **FluffyElmo said:**
> Yes, you have to install a JDK, or a supported JVM which in this case is probably Suns. Simple to install, just download it at and run the install script. Then export the directory it's in as JAVA_HOME and run the installer for Studio Enterprise.

So long as the JVM/JDK you install is 64bit then you're fine. Java applications run cross-platform without modification unless they use external native libraries.
That's the trick, which JDK is for 64 bit unix/linux systems?

---

### Post by FluffyElmo on 2006-09-07
*jdk-1_5_0_08-linux-amd64.bin*

Go to the Java SE download section of java.sun.com, scroll down to *Linux x64 Platform* and choose the non-rpm version. Here is a link to the download page, but it will probably stop working when the session times out.
[https://sdlc6c.sun.com/ECom/EComActionServlet/DownloadPage:~:com.sun.sunit.sdlc.content.DownloadPageInfo;jsessionid=A651E670CE6EACF3117E18A0C2AE1725;jsessionid=A651E670CE6EACF3117E18A0C2AE1725]("https://sdlc6c.sun.com/ECom/EComActionServlet/DownloadPage:~:com.sun.sunit.sdlc.content.DownloadPageInfo;jsessionid=A651E670CE6EACF3117E18A0C2AE1725;jsessionid=A651E670CE6EACF3117E18A0C2AE1725")

---

### Post by kopilo on 2006-09-08
Thanks, I downloaded 'jdk-1_5_0_08-linux-amd64.bin' and then in terminal went to the download location and ran 'bash jdk-1_5_0_08-linux-amd64.bin'. I read through the statement and said yes to install, it seemed to install ok but the command 'javac' is not recoginsed, CLASSPATH is empty and Studio Enterprise still doesn't install.

---

### Post by kuja on 2006-09-08
Looks like you're doing things the hard way to me. 

```
sudo apt-get install sun-java5-jdk sun-java5-jre sun-java5-bin
```
Instead of sun-java5-bin, you can use ia32-sun-java5-bin for a 32-bit JRE

Voila, more easily installed, more easily removed. Also lets you set it to default much easier.

And to set which java environment you want your system to use by default
```

sudo update-alternatives --all

``` Change anything related to java. Just hit enter to leave something at the defaults.

---

### Post by kopilo on 2006-09-09
Yeah I'm doing things the hardway because I want to be able to install Java and Studio Enterprise without an internet connection.

However I'll try the 'atp-get' install.

---

### Post by kopilo on 2006-09-09
ok I did the atp-get command, now Javac works, however the $CLASSPATH still echos nothing and 'bash jstudio' still comes up with the same error.

:-k

---

### Post by kopilo on 2006-09-10
Ok now I feel a little bit like a doofus, but at least it is installed.

All that was required was to make it executable and to run it like so.
```

chmod +x jstudio_ent8_dl-linux-jds.sh
./jstudio_ent8_dl-linux-jds.sh

```
Add '-is:log install.log' to the end of the second command to log the installation.

source: [Sun 's JStudio Installation + Starting guide for linux](http://docs.sun.com/source/819-2807/chap_linux_installing.html)

---

