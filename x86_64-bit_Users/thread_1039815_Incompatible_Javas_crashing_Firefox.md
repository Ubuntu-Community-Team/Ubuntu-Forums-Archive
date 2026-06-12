---
title: "Incompatible Javas crashing Firefox?"
date: 2009-01-14
forum: x86 64-bit Users
---

### Post by jmarks on 2009-01-14
To assess the possibility of moving all the Windows machines in my lab to Linux, I installed 64 bit Intrepid 8.10 onto a new machine at home: 
Dell 2.66 GHz quadcore, 4 GB RAM, ATI graphics card. The standard 64 bit install worked great out of the box (of course).
Because I wanted to assess the functionality of the 64 bit version of the NIH ImageJ image analysis package, I installed Sun Java 6 Runtime. (ImageJ runs great.)

However, shortly thereafter, Firefox 3.0.5 starting crashing on many, many sites, by simply closing windows. Running firefox from a terminal window gives the following:
```
jmarks@jmarks-desktop:~$ firefox
Error sanitizing history: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: chrome://browser/content/sanitize.js :: anonymous :: line 115"  data: no]
ICEDTEAPLUGIN_DEBUG = (null)
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
```

Starting Firefox in safe mode gives the identical output and does not prevent the crashes.
Occasionally, just before crashing, output is:

```
*** glibc detected *** /usr/lib/firefox-3.0.5/firefox: double free or corruption (!prev): 0x00000000040bf110 ***
aborted
```

My guess is that I have installed incompatible java apps on my system.

Searching installed applications for "java" on my system yields:
Sun Java 6 Runtime
Archive Manager
Ubuntu restricted extras
OpenJDK Java 6 Web Start
OpenJDK Java 6 Runtime
Icedtea Java Plugin

Is my idea of incompatible Java a likely explanation?
I am happy to give up 64-bit ImageJ functionality in favor of basic web browsing, but I am not sure what to uninstall, nor how to uninstall things completely.
Any suggestions would be most welcome. I'm almost ready to do a clean install, but would rather not.

---

### Post by Nintendo01 on 2009-01-14
I don't know much about linux or Firefox, but since your error is when failing to Load Plugin shared library /usr/lib/mozilla/plugins/libflashplayer.so, I think your problem is with flash, not java.

---

### Post by jmarks on 2009-01-15
> **Nintendo01 said:**
> I don't know much about linux or Firefox, but since your error is when failing to Load Plugin shared library /usr/lib/mozilla/plugins/libflashplayer.so, I think your problem is with flash, not java.

I appreciate the suggestion. However, when this behavior began, I wondered whether this was due to absence of a Flash plug-in. So, I installed the macromedia flash 10 64-bit plug-in. However, the crashes have continued unchanged.

---

### Post by jespdj on 2009-01-15
But why do you think this has anything to do with Java? There's nothing in the error message that suggests there's a problem with Java.

Look at this:
> LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: **wrong ELF class: ELFCLASS32**]

Did you install the 32-bit version of Flash on your 64-bit system? That's not going to work. You need to install 64-bit Flash.

Read this sticky: [Adobe Flash and 64-bit](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by jmarks on 2009-01-15
> **jespdj said:**
> But why do you think this has anything to do with Java? There's nothing in the error message that suggests there's a problem with Java.

Look at this:


Did you install the 32-bit version of Flash on your 64-bit system? That's not going to work. You need to install 64-bit Flash.

Read this sticky: [Adobe Flash and 64-bit](http://ubuntuforums.org/showthread.php?t=772490)

I thought I did install 64-bit Flash, using this: 
```

sudo killall -9 firefox
echo "Downloading and instaling Getlibs for required libraries"
wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
tar zxvf install_flash_player_10_linux.tar.gz
sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/
rm -rf ~/install_flash_player_10_linux/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
echo "You may re-start Firefox now"
```

How can I learn what Flash I currently have installed?
How can I remove all installed flash correctly to see if this fixes my problem?
If, after removing Flash, my Firefox still crashes like crazy, what else could I do to figure out what's going on?

---

### Post by jespdj on 2009-01-15
That script does not install 64-bit Flash, it installs 32-bit Flash 10 with nspluginwrapper (an adapter to make 32-bit Flash work in 64-bit Firefox). It looks like something has gone wrong with the installation of Flash or nspluginwrapper.

By typing **about:plugins** in the address bar of Firefox, you can see what plugins are installed.

There is currently an alpha version of 64-bit Adobe Flash. (Adobe calls it an "alpha version" but it works better than any previous release version of Flash). The sticky topic explains how to install it. Read the sticky topic carefully and follow the instructions.

You might need to remove the 32-bit Flash and nspluginwrapper first. Look at the content of the script:
```
echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
```

---

### Post by jmarks on 2009-01-17
> **jespdj said:**
> That script does not install 64-bit Flash, it installs 32-bit Flash 10 with nspluginwrapper (an adapter to make 32-bit Flash work in 64-bit Firefox). It looks like something has gone wrong with the installation of Flash or nspluginwrapper.

By typing **about:plugins** in the address bar of Firefox, you can see what plugins are installed.

There is currently an alpha version of 64-bit Adobe Flash. (Adobe calls it an "alpha version" but it works better than any previous release version of Flash). The sticky topic explains how to install it. Read the sticky topic carefully and follow the instructions.

You might need to remove the 32-bit Flash and nspluginwrapper first. Look at the content of the script:
```
echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
```

Well, I uninstalled 32 bit flash and installed 64 bit flash per the sticky at the top of the forum. about:plugins in Firefox now shows no icedtea plugin and the correct Flash plug-in.

Unfortunately, firefox continues to crash like crazy. For example, just try to look at a flight schedule on [www.aa.com](www.aa.com)
Out of frustration, I reinstalled firefox 3 and its obvious components shown in synaptics package manager, but got no change in Firefox behaviour.
Upon starting Firefox from a terminal window, the error message continues to be the following (note the absence of the 32 bit flash error):
```

jmarks@jmarks-desktop:~$ firefox
Error sanitizing history: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: chrome://browser/content/sanitize.js :: anonymous :: line 115"  data: no]
```
Also, there is no bookmarks toolbar (it's checked appropriately under View Toolbars), and cannot bookmark sites.
Do I blow my Ubuntu away and start again? 
Do I totally remove Firefox and all plug-ins and start again, and if so, how?
I'd rather spend time debugging in order to learn more, but not if it's a lost cause.
Thank you very much for your help.
jm

---

### Post by jmarks on 2009-01-17
One more thing: looking through the reports of 64-bit firefox crashing, I came across this thread:
[http://ubuntuforums.org/showthread.php?t=1011649](http://ubuntuforums.org/showthread.php?t=1011649)

This person's problems sound very similar, perhaps identical, to mine, except I'm running 3.0.5.

thanks again.

---

### Post by jespdj on 2009-01-18
> **jmarks said:**
> Do I blow my Ubuntu away and start again? 
Do I totally remove Firefox and all plug-ins and start again, and if so, how?
I'd rather spend time debugging in order to learn more, but not if it's a lost cause.
Thank you very much for your help.
jm
That would be a bit drastic! Before reinstalling the whole operating system, try deleting your .mozilla directory in your home directory (that's the directory that contains all Firefox' settings etc.):
```
rm -rf ~/.mozilla
```

---

### Post by Clancy_s on 2009-01-18
> **jespdj said:**
> That would be a bit drastic! Before reinstalling the whole operating system, try deleting your .mozilla directory in your home directory (that's the directory that contains all Firefox' settings etc.):
```
rm -rf ~/.mozilla
```

I'd suggest backing up your bookmarks (at least) first, possibly the whole directory.

If it fixes things you can reload your bookmarks in the new install.

---

### Post by Thelasko on 2009-01-20
> **Clancy_s said:**
> I'd suggest backing up your bookmarks (at least) first, possibly the whole directory.

If it fixes things you can reload your bookmarks in the new install.

Better yet, just rename the .mozilla folder.  For example, you could name it .mozillabackup and it would be just like deleting it.  This way it's much easier to restore this file if it wasn't the cause of your issues.

---

### Post by jmarks on 2009-01-20
> **jespdj said:**
> That would be a bit drastic! Before reinstalling the whole operating system, try deleting your .mozilla directory in your home directory (that's the directory that contains all Firefox' settings etc.):
```
rm -rf ~/.mozilla
```
  
Well, I deleted my mozilla directory and started again. I got my bookmarks toolbar back, but Firefox is still crashing on the American Airlines site ([www.aa.com, as soon as possible flights are displayed]("http://www.aa.com")). I haven't done a lot of other browsing, so I'm not yet sure if the AA site is throwing some code at 64 bit java that it can't handle, or whether there is a more pervasive problem in my installation.

Today, it first crashed with the memory allocation error
```
*** glibc detected *** /usr/lib/firefox-3.0.5/firefox: double free or corruption
```and the backtrace (for what it's worth) consisted of
```
/lib/libc.so.6[0x7f886b232938]
/lib/libc.so.6(cfree+0x76)[0x7f886b234f86]
/usr/lib/libtalloc.so.1(talloc_free+0x128)[0x7f885c08db88]
/lib/libnss_wins.so.2[0x7f885d2e0f48]
/usr/lib/libtalloc.so.1(talloc_free+0x232)[0x7f885c08dc92]
/lib/libnss_wins.so.2(alloc_sub_basic+0x8e9)[0x7f885d308d02]
/lib/libnss_wins.so.2(talloc_sub_basic+0x24)[0x7f885d30926d]
/lib/libnss_wins.so.2[0x7f885d258be9]
/lib/libnss_wins.so.2(lp_lockdir+0x1e)[0x7f885d259a93]
/lib/libnss_wins.so.2(lock_path+0x9)[0x7f885d303972]
/lib/libnss_wins.so.2(receive_unexpected+0x2c)[0x7f885d2ae321]
/lib/libnss_wins.so.2(receive_nmb_packet+0x3b)[0x7f885d2b0d2e]
/lib/libnss_wins.so.2(name_query+0x303)[0x7f885d2b3530]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname_r+0x2c8)[0x7f885d256202]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname2_r+0x2b)[0x7f885d256484]
/lib/libc.so.6[0x7f886b286f73]
/lib/libc.so.6(getaddrinfo+0x1de)[0x7f886b28896e]
/usr/lib/libnspr4.so.0d(PR_GetAddrInfoByName+0x108)[0x7f886a8e0828]
/usr/lib/xulrunner-1.9.0.5/libxul.so[0x7f88699e9f6a]
/usr/lib/libnspr4.so.0d[0x7f886a8ecdc3]
/lib/libpthread.so.0[0x7f886bee03ea]
/lib/libc.so.6(clone+0x6d)[0x7f886b29fc6d]
```The second time, on the same site, with the same request, I got
```
segmentation fault
```Unless these snippets clearly demonstrate a problem, I guess I'll just spend a lot of time on the browser, seeing what works and doesn't work.

In case it's helpful, my Firefox java plugins are listed as follows:

```
**libnpjp2.so**

 File name:  libnpjp2.so 
  MIME Type Description Suffixes Enabled    
application/x-java-vm Java Yes   
application/x-java-applet Java Yes   
application/x-java-applet;version=1.1 Java  Yes   
application/x-java-applet;version=1.1.1 Java Yes   
application/x-java-applet;version=1.1.2 Java Yes   
application/x-java-applet;version=1.1.3 Java Yes   
application/x-java-applet;version=1.2 Java    Yes   
application/x-java-applet;version=1.2.1 Java Yes   
application/x-java-applet;version=1.2.2 Java Yes   
application/x-java-applet;version=1.3 Java Yes   
application/x-java-applet;version=1.3.1 Java Yes   
application/x-java-applet;version=1.4 Java Yes   
application/x-java-applet;version=1.4.1 Java Yes   
application/x-java-applet;version=1.4.2 Java Yes   
application/x-java-applet;version=1.5 Java Yes   
application/x-java-applet;version=1.6 Java Yes   
application/x-java-applet;jpi-version=1.6.0_12 Java Yes   
application/x-java-bean Java Yes   
application/x-java-bean;version=1.1 Java Yes   
application/x-java-bean;version=1.1.1 Java Yes   
application/x-java-bean;version=1.1.2 Java Yes   
application/x-java-bean;version=1.1.3 Java Yes   
application/x-java-bean;version=1.2 Java Yes  
 application/x-java-bean;version=1.2.1 Java Yes   
application/x-java-bean;version=1.2.2 Java Yes   
application/x-java-bean;version=1.3 Java Yes  
 application/x-java-bean;version=1.3.1 Java Yes   
application/x-java-bean;version=1.4 Java Yes   
application/x-java-bean;version=1.4.1 Java Yes   
application/x-java-bean;version=1.4.2 Java Yes   
application/x-java-bean;version=1.5 Java Yes   
application/x-java-bean;version=1.6 Java Yes   
application/x-java-bean;jpi-version=1.6.0_12 Java Yes
```Thank you to all for your help.
jm

---

### Post by jespdj on 2009-01-21
Why are you still thinking this has anything to do with Java? The stack trace that you posted doesn't contain anything that seems to be related to Java. I looked at [www.aa.com](www.aa.com) and searched for some random flights, and looked at the source code of the pages. There is no Java on the American Airline website.

If you uninstall all Java versions from your computer, does the crash go away?

Looking at the stack trace, it looks like it has to do something with libnss_wins. Maybe it is [bug #309539](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/309539)?

---

### Post by jmarks on 2009-01-21
> **jespdj said:**
> Why are you still thinking this has anything to do with Java? The stack trace that you posted doesn't contain anything that seems to be related to Java. I looked at [www.aa.com]("http://www.aa.com") and searched for some random flights, and looked at the source code of the pages. There is no Java on the American Airline website.

If you uninstall all Java versions from your computer, does the crash go away?

I only thought it might be Java-related because (I thought) Java was ubiquitous on sites that made complex calculations like booking flights, and I had added the 64 bit Java from Sun in order to make ImageJ work. (Although I have worked with and programmed systems since the DEC PDP-11, I am a Linux noob.)

Thank you for taking the time to look through my backtrace and even the AA site!
I am happy to uninstall all Java from my machine, but for 3 things:
1. I don't know how to ascertain all the Javas I have
2. I don't know how to completely uninstall them
3. I don't know which Javas to put back, if the crashing problem is unchanged.

> **jespdj said:**
> Looking at the stack trace, it looks like it has to do something with libnss_wins. Maybe it is [bug #309539]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/309539")?
This bug looks promising as a cause. I presume I look at /etc/netswitch.conf and see if WINS is present? I think I may have added WINS in an (ultimately successful) effort to mount windows shares from my local network. I can't confirm that WINS is present now because I am at work at my linux box is at home, but I will do so. In fact, I may do this first before removing Java, and assess whether the system still crashes after I removed the offending WINS in that file. If the crashing is gone, I will mark this problem as solved. If not, I will go the Java removal route.
In any case, I remain incredibly impressed at and grateful for the level and amount of community support that is available in the Linux/Ubuntu world.

---

### Post by jmarks on 2009-01-21
> **jmarks said:**
>  This bug looks promising as a cause. I presume I look at /etc/nswitch.conf and see if WINS is present? I think I may have added WINS in an (ultimately successful) effort to mount windows shares from my local network. If the crashing is gone, I will mark this problem as solved.
In any case, I remain incredibly impressed at and grateful for the level and amount of community support that is available in the Linux/Ubuntu world.

This problem is [SOLVED]. Removing WINS from /etc/nsswitch.conf has stopped Firefox from crashing.
Can anyone explain why having the system use a WINS server in this way should cause Firefox to crash? While I have learned a lot through this process,  I would appreciate  learning a little more.

Thank  you all. (I would thank people properly and mark this thread as solved, but see no  medals to click on in people's posts, and the Thread Tools drop down does not contain the option to mark thread as solved).

---

### Post by jespdj on 2009-01-22
Good, so it was indeed a case of that bug! :)

Why this happens... it's a bug in Firefox, or in a library that Firefox is using. It's up to the developers of Firefox or the library to find out exactly where in the software the bug happens and fix it.

I found the bug in the Ubuntu bug database by googling for "libnss_wins", which I saw in the stack trace that you posted.

A lot of websites use Java**Script**, but JavaScript is something completely different and unrelated to Java (despite the similarity in the name - that's a historical accident caused by marketing people from Netscape and Sun...).

---

### Post by Thelasko on 2009-01-22
> **jmarks said:**
> (I would thank people properly and mark this thread as solved, but see no  medals to click on in people's posts, and the Thread Tools drop down does not contain the option to mark thread as solved).

[They have been disabled for a while due to some recent issues with the server.]("http://moxiefoxtrot.com/2009/01/14/recent-ubuntuforums-downtime/")

---

### Post by ymmottommy on 2009-01-23
Hi it seems that you guys are familiar with programing in linux so I take the change to make a question to you. Can you tell me how I can install java for firefox on my computer. I have Ubuntu 8.10 Best regards ymmottommy

---

### Post by jespdj on 2009-01-23
Hello ymmottommy,

Welcome to the Ubuntu Forums. Please open your own new topic of appending your question to someone else's topic.

The first thing to try to get Java working in Firefox is installing the package **icedtea6-plugin**, you an do this using Synaptic (System > Administration > Synaptic Package Manager) or from a terminal window:
```
sudo apt-get install icedtea6-plugin
```
This will install OpenJDK Java and the IcedTea browser plug-in to make Java work from Firefox.

See also [the sticky topic](http://ubuntuforums.org/showthread.php?t=774956) about Java on 64-bit systems.

---

### Post by ymmottommy on 2009-01-25
Hi, this was useful information for me since I am a new user of linux.
Buth I still have problems with java when I try to log into my bank.
The message I got is: applet not initialized
Best regards ymmottommy:)

---

### Post by jespdj on 2009-01-25
The issue with Java at the moment is this:

Sun currently does not have a browser plug-in included with Java for 64-bit systems. (It's coming in the next update of Sun Java). On Ubuntu, there are several options:
[LIST=1]
[*]Install OpenJDK Java and the IcedTea plugin.
[*]Install the beta-version of Sun Java 6 update 12.
[*]Install a 32-bit Firefox and 32-bit Java.
[/LIST]
OpenJDK is a version of Java based on Sun Java (because Sun is making its Java implementation open source), but it is not yet 100% compatible with Sun Java, so not everything works. Unfortunately, it seems that the applet from your bank does not work with OpenJDK Java.

So, remove it again:
```
sudo apt-get purge icedtea6-plugin openjdk-6-jre openjdk-6-jre-headless
```
Follow the instructions in [this thread](http://ubuntuforums.org/showthread.php?t=1019314) to install the beta version of Sun Java 6 Update 12.

---

