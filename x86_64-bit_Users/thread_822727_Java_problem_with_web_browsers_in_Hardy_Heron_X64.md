---
title: "Java problem with web browsers in Hardy Heron X64"
date: 2008-06-08
forum: x86 64-bit Users
---

### Post by NNG on 2008-06-08
I recently decided to switch from a 32-bit version of Ubuntu to a 64 bit version. The transition was pretty smooth but I have yet to get Java to work on web browsers. However, programs that depend on JRE and JDK (such as weatherbug and netbeans) work fine, Java isn't working one either Firefox 3 or SeaMonkey. I  installed Java using synaptic package manager.

```
will@Will-Ubuntu:~$ java -version
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK 64-Bit Server VM (build 1.6.0-b09, mixed mode)

```

One interesting thing is that Sun Java 6 doesn't also appear when using java -version. I tried uninstalling Sun Java thinking that it might be conflicting with OpenJDK but that's not the case as neither browser uses Java either way. 

Some help would be appreciated. I'm not very knowlegeble when it comes to Linux yet so I'm really at a loss on how to fix this and I haven't found anything else that might help me.

---

### Post by Falcorian on 2008-06-08
I, too, have been unable to get it working. I've let firefox install a pluging and still nothing.

---

### Post by User3k on 2008-06-08
[http://ubuntuforums.org/showthread.php?t=774956]("http://ubuntuforums.org/showthread.php?t=774956")

---

### Post by Bubba64 on 2008-06-08
> **User3k said:**
> [http://ubuntuforums.org/showthread.php?t=774956]("http://ubuntuforums.org/showthread.php?t=774956")

The first thread is a good start add remove has java 6. A lot of the time instead of source compiling in synaptic whole set ups are in add remove always check there.

---

### Post by NNG on 2008-06-08
I reinstalled OpenJDK with add/remove and it didn't change anything. I still can't get Java on browsers. :(

---

### Post by Bubba64 on 2008-06-08
> **NNG said:**
> I reinstalled OpenJDK with add/remove and it didn't change anything. I still can't get Java on browsers. :(

Did this install java 6 in add remove just search with java to find it. Also have you looked in your browser preferences to see if cookies and java are enabled, also have you added a java blocker to your system like no script.

---

### Post by NNG on 2008-06-08
Browser preferences are good and yes, both Sun Java 6 runtime and openJDK runtime are installed.

---

### Post by Bubba64 on 2008-06-08
> **NNG said:**
> Browser preferences are good and yes, both Sun Java 6 runtime and openJDK runtime are installed.

I don't know if his link will help the writer doesn't say which FF or distribution.
[http://www.derickrethans.nl/firefox_and_64_bit_java_plugin.php](http://www.derickrethans.nl/firefox_and_64_bit_java_plugin.php)
It appears on a short Google search that Sun hasn't made a 64 bit java setup so to speak. I have seen others say using a 32 bit FF was their answer. Here is another link.
[http://www.cyberciti.biz/tips/linux-flash-java-realplayer-under-64bit-firefox.html](http://www.cyberciti.biz/tips/linux-flash-java-realplayer-under-64bit-firefox.html)
Here is the Google link I found with 64 bit java Firefox linux.
[http://www.google.com/search?hl=en&q=64+bit+java+Firefox+linux&btnG=Search](http://www.google.com/search?hl=en&q=64+bit+java+Firefox+linux&btnG=Search)
Good luck

---

### Post by rev_b on 2008-06-09
The only way I managed Java to work without too many hassles was to install a 32-bit browser and 32-bit java to /~ and make a link in plugin folder to the 32-bit java plugin.

I installed Icecat, because it can run along with firefox; you can't run firefox 32 and 64 bits at the same time.

On the seldom ocasions I need java, I just open Icecat.

---

### Post by NNG on 2008-06-10
> **Bubba64 said:**
> I don't know if his link will help the writer doesn't say which FF or distribution.
[http://www.derickrethans.nl/firefox_and_64_bit_java_plugin.php](http://www.derickrethans.nl/firefox_and_64_bit_java_plugin.php)
It appears on a short Google search that Sun hasn't made a 64 bit java setup so to speak. I have seen others say using a 32 bit FF was their answer. Here is another link.
[http://www.cyberciti.biz/tips/linux-flash-java-realplayer-under-64bit-firefox.html](http://www.cyberciti.biz/tips/linux-flash-java-realplayer-under-64bit-firefox.html)
Here is the Google link I found with 64 bit java Firefox linux.
[http://www.google.com/search?hl=en&q=64+bit+java+Firefox+linux&btnG=Search](http://www.google.com/search?hl=en&q=64+bit+java+Firefox+linux&btnG=Search)
Good luck
Ok, the ndiswrapper looks promising but I'm a little confused at what to do in what to do for downloading/installing the java program. 

So for this line right here, what would replace the libflashplayer.so and would I need to do anything else (such as downloading the plugin) in addition to running the command. I'm sorry, I just don't know much about linux yet :(
```
# nspluginwrapper -i /usr/lib/mozilla/plugins/**libflashplayer.so**
```

---

### Post by Bubba64 on 2008-06-10
> **NNG said:**
> Ok, the ndiswrapper looks promising but I'm a little confused at what to do in what to do for downloading/installing the java program. 

So for this line right here, what would replace the libflashplayer.so and would I need to do anything else (such as downloading the plugin) in addition to running the command. I'm sorry, I just don't know much about linux yet :(
```
# nspluginwrapper -i /usr/lib/mozilla/plugins/**libflashplayer.so**
```

I would help you more if I knew what the answers are, but I am not a geek. Keep trying on this forum and set it up so you get instant notification if you don't so if a real geek posts you can be right on it.

---

### Post by mhenriday on 2008-07-05
Generally speaking, I have no problem getting websites to recognise the **JRE** files I've installed from Synaptic (first screenshot below), but when attempting recently to make use of [**_Screencast-o-matic_**]("http://screencast-o-matic.com/"), I was informed that I did _not_ have **Sun Java** installed (second screenshot below).

I then turned to **Sef**'s [_brief tutorial_]("http://ubuntuforums.org/showthread.php?t=774956") and tried to install via «Applications» &#8594; «Add/Remove» as suggested there, but that didn't work too well either : as can be seen in the third screendump below, I was informed that the package concerned is merely an installer package, and that in order to install the **jdk** package, I should have to do so from **Sun**'s website. No sooner said than done, but when I try to install the programme according to the Sun tutorial, using```
./jdk-6u6-linux-x64.bin
``` I was first asked to accept **Sun**'s licensing terms - which, of course, I did - but thereafter I was merely asked if I want to replace (!!) the jdk files that have already been installed ! And despite these efforts, **Screencast-o-matic** still didn't recognise that I had **Java** installed and suggested once again that I install it....

The above cautionary tale seems to be par for the course for 64-bit users ; had I had 32-bit **Hardy** installed, I suspect that things would have been more or less as easy as rolling off a log. Hopefully a 64-bit plug-in for **Firefox** will become available before the end of the present year, but it would be nice if we users were not always constrained to return to the back of the queue after waiting months or years to come to its head....

Henri

PS :&#12288;what did I do to resolve my immediate problem with **Screencast-o-matic** ? Rebooted to **Vista** and created my screencast on that platform. Not precisely the *dénouement* I desired....

---

### Post by Cloud79 on 2008-07-10
This worked for me

[http://www.derickrethans.nl/firefox_and_64_bit_java_plugin.php](http://www.derickrethans.nl/firefox_and_64_bit_java_plugin.php)

Uninstalled icedtea first

---

### Post by stchman on 2008-07-10
Use Icedtea as the SUN browser plugin is 32 bit.

```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin

```

The plugin works for about 70% of the sites I have visited.

---

