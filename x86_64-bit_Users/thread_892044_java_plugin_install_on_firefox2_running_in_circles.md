---
title: "java plugin install on firefox2 running in circles"
date: 2008-08-16
forum: x86 64-bit Users
---

### Post by bluepowder7 on 2008-08-16
so i'm trying to get java to work on firefox2 (accessing toyota university with user-agent-switcher set to IE7), and it seems to keep telling me that i need to install two things in order to display content.  so i install them, but it keep on complaining that i need to install them.  it's like i'm running in circles.

here's what it tells me i need to install:

[IMG]http://i106.photobucket.com/albums/m244/GregR7/screenshots/java-circles.jpg[/IMG]

---

### Post by Kilz on 2008-08-16
> **bluepowder7 said:**
> so i'm trying to get java to work on firefox2 (accessing toyota university with user-agent-switcher set to IE7), and it seems to keep telling me that i need to install two things in order to display content.  so i install them, but it keep on complaining that i need to install them.  it's like i'm running in circles.

here's what it tells me i need to install:

[IMG]http://i106.photobucket.com/albums/m244/GregR7/screenshots/java-circles.jpg[/IMG]

How was Firefox 2 installed?
What version of Ubuntu are you running?
When you start Firefox 2 is any other browser open?
When you type ```
about:plugins
``` in the address bar and hit enter do you see java listed?

---

### Post by bluepowder7 on 2008-08-16
* ff2 was installed using terminal and "sudo aptitude install firefox2" or "...firefox-2" or whatever that was (i'm using terminal sudo aptitude as much as possible, mostly to get maximum familiarization with what is going on)

* xubuntu 8.04-64bit

* yup, opera 9.50 is open as that is my main browser

* i see ShockWave Flash and FutureSplash Player listed, and below that a ton of GCJ, but the java content (online courses and exams) still don't come up

---

### Post by Kilz on 2008-08-17
> **bluepowder7 said:**
> 

* i see ShockWave Flash and FutureSplash Player listed, and** below that a ton of GCJ**, but the java content (online courses and exams) still don't come up

Then Java is installed. At least the Java plugins that a 64bit browser can use. The site probably needs a Sun Java plugin. The problem is there is no 64bit Sun Java plugin (yet, but Java 7 should have one). The only alternative I know is to install the [32bit browser and plugins script]("http://ubuntuforums.org/showthread.php?t=202537"). That will install 32bit Firefox and a Sun Java plugin.

---

