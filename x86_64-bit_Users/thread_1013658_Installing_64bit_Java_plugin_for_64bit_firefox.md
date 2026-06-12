---
title: "Installing 64bit Java plugin for 64bit firefox"
date: 2008-12-17
forum: x86 64-bit Users
---

### Post by Antionio on 2008-12-17
Hello!

I've had HUGE problems with java plugins in the past and I've found forum threads very useful when searching installation help. So I decided to show you how I got the brand new 64bit java plugin working for 64bit Ubuntu (8.04) and the 64bit Firefox 3.0.4.

EDIT: Be sure to read the whole post and try the tips I've added below.

1)

Download Linux x64 JRE bin from the following address:
[https://jdk6.dev.java.net/6uNea.html](https://jdk6.dev.java.net/6uNea.html)

2)

Run the .bin file so that it extracts the jre files. Copy the files where you want to keep them. I put them next to my other JDK's and JRE's.

```

sudo chmod +x jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
sudo ./jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
sudo mv jre1.6.0_12 /some_path

```

3)

Create a symbolic link to Firefox plugin directory:

```

mkdir ~/.mozilla/plugins/
ln -s /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so ~/.mozilla/plugins/

```

4)

EDIT: These about:config settings might be unnecessary after all. Some people have gotten the plugin working without changing these settings.

Run Firefox and write about:config to the address bar. Write "java" to the filter so that you can find the settings more easily.

Change the following settings:

java.default_java_location_others = /path_to_jre/jre1.6.0_12
java.java_plugin_library_name = libnpjp2


5)

Voila, the plugin should be working now. If not, respond to this thread so we can troubleshoot for different ubuntu configurations. Also if you have some better way to get it working, please let us know.

EDIT:
Here are some tips people have posted:

1) If you're having problems getting java to work, uninstall any previous java version you might have! (for example icedtea and openjdk).

```

sudo apt-get remove icedtea6-plugin openjdk-6-jre

```

2) Try changing the default java jre with ```
sudo update-alternatives --config java
```

If you still don't get the plugin working after this, try to read through the responses of this thread for more tips. I might not update this tutorial so often.

---

### Post by mkwerner on 2008-12-17
Thanks a bunch - this worked for me!  I did have to remove the icedtea plugin for it to work, though!

Cheers,
M.

---

### Post by philinux on 2008-12-17
What if any are the benefits? Can you spot a difference in performance etc?

---

### Post by TheAL76 on 2008-12-17
> **philinux said:**
> What if any are the benefits? Can you spot a difference in performance etc?

For me, I can finally use the Facebook Photo application without it crashing Firefox.

---

### Post by craigsn on 2008-12-17
Not working for me. I have a fresh install of Ubuntu 8.10, and all I did was follow your directions to install and try to run a java application. No joy. What testing should I do?

Thanks
Craig

---

### Post by Antionio on 2008-12-18
> **craigsn said:**
> Not working for me. I have a fresh install of Ubuntu 8.10, and all I did was follow your directions to install and try to run a java application. No joy. What testing should I do?

I suspect that you don't have a previous installation of 64bit java. You can check it with "java -version" at the command line. I had a hunch when I made this tutorial, that the fact that I had a previous installation of 64bit jre made it go so smoothly. (My tutorial just uses the plugin, the java I'm using as a default is update 7, not 12 that includes the plugin, if I remember correctly).

I'll try to get into this a bit more but in the meantime you could try installing a 64bit java jre from the ubuntu repository or try to set the update 12 as a default jre (I'm not quite sure how to do that easily in ubuntu yet, since the Sun's .bin just decompresses the files. It doesn't do any config for java, I think.)

---

### Post by Yellow Pasque on 2008-12-18
I believe your step 3 will confuse n00bs (and it shouldn't have a specific FF version in it lest someone with a different version of FF tries to copy and paste)

```
sudo ln -s <PATH_TO_JRE>/jre1.6.0_12/lib/amd64/libnpjp2.so /usr/lib/firefox-addons/plugins
```
Also, some mozilla-based browsers (e.g. Swiftweasel) apparently only look in /usr/lib/mozilla/plugins, so a link might need to be created there.

EDIT: Actually, the correct anal-retentive, Debian policy-compliant way to do it would be to create a plugins dir in the .mozilla dir in the user's home directory and make the link there:
```
cd ~/.mozilla
mkdir plugins
ln -s <PATH_TO_JRE>/jre1.6.0_12/lib/amd64/libnpjp2.so ~/.mozilla/plugins
```

---

### Post by jamesstansell on 2008-12-18
> **Temüjin said:**
> 
EDIT: Actually, the correct anal-retentive, Debian policy-compliant way to do it would be to create a plugins dir in the .mozilla dir in the user's home directory and make the link there:
```
cd ~/.mozilla
mkdir plugins
ln -s <PATH_TO_JRE>/jre1.6.0_12/lib/amd64/libnpjp2.so ~/.mozilla/plugins
```

Just to follow up: when you do that be sure to de-configure any 'system' java plugin.  For example remove icedtea6-plugin or similar packages.  Check in your browser to see that the plugin you want is in the plugin list, and that it is the _only_ java plugin in the list.  Then, because there is not a system java plugin configured, each user will need to take this step.

---

### Post by Spr0k3t on 2008-12-19
This worked for me as well.  I had to remove IcedTea before the plugin was used.  I have OpenJDK installed.

Now the only 64bit plugin I need is from LogMeIn.com.

---

### Post by Sef on 2008-12-19
> This worked for me as well.  I had to remove IcedTea before the plugin was used.  I have OpenJDK installed.

OpenJDK is an open source version of Java.  [From Java on 64-bit Systems]("http://ubuntuforums.org/showthread.php?t=774956"):  > The easiest way to download OpenJDK and Icedtead (the plugin) is **Applications > Add/Remove > Change the Show box to either "All OpenSource Applications" or "All Available Applications"** (The former is also known as Universe and does not contain any proprietary applications, while the latter is also known as Multiverse and contains proprietary appliations.) > **Search: Icedtea > click on the boxes next to OpenJDK and Icedtea > apply changes > apply > close.**

---

### Post by vgrisham on 2008-12-19
Thanks! This how to (with the .mozilla plugin suggestion above) worked like a charm. It didn't work at first. Then I read through the appended suggestions and uninstalled all of the iced tea stuff.

---

### Post by jaxgent on 2008-12-19
Hi, How would I undo all the sudo commands from the 1st post and purge the install, I jumped in without a read through of all postings

Thanks

---

### Post by QCompson on 2008-12-20
Hmmm... I cannot get this to work.  I placed the plugin with other java junk in /usr/lib/jvm.  I linked to it in ~/.mozilla/plugins

I uninstalled icedtea.

I made the suggested changes to about:config settings.

Everything for java is pointing to libnpjp2.so in about: plugins

But if I go to a java test page, I get blank grey boxes.  I'm not sure where to start troubleshooting.  TIA.

---

### Post by jamesstansell on 2008-12-20
> **QCompson said:**
> Hmmm... I cannot get this to work.  I placed the plugin with other java junk in /usr/lib/jvm.  I linked to it in ~/.mozilla/plugins

I uninstalled icedtea.

I made the suggested changes to about:config settings.

Everything for java is pointing to libnpjp2.so in about: plugins

But if I go to a java test page, I get blank grey boxes.  I'm not sure where to start troubleshooting.  TIA.

If you turn off compiz do you still get the grey boxes?

---

### Post by QCompson on 2008-12-20
> **jamesstansell said:**
> If you turn off compiz do you still get the grey boxes?
Yep, compiz wasn't even on in the first place.  :(

When you all look at Firefox's Add-ons --> Plugins settings, does it just read "libnpjp2.so"?


Java also doesn't work in epiphany, opera or konqueror.

---

### Post by jamesstansell on 2008-12-20
> **QCompson said:**
> 
When you all look at Firefox's Add-ons --> Plugins settings, does it just read "libnpjp2.so"?

That sounds familiar.

If you type ```
javascript:java.lang.System.getProperty("java.version")
``` in the firefox url bar and hit enter, what does it do?

You are using a 64-bit version of Firefox 3, right?

---

### Post by w0ng on 2008-12-20
> **QCompson said:**
> Yep, compiz wasn't even on in the first place.  :(

When you all look at Firefox's Add-ons --> Plugins settings, does it just read "libnpjp2.so"?


Java also doesn't work in epiphany, opera or konqueror.

Exact instructions I followed per instructions throughout this thread:

1) Uninstall previous version of java I had installed
```
 sudo apt-get remove icedtea6-plugin openjdk-6-jre
```

2) Download Linux x64 JRE, give it permissions to execute, extract it, move it to the locations where other JRE's and JDK's are
```
wget http://www.java.net/download/jdk6/6u12/promoted/b02/binaries/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
sudo chmod +x jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
sudo ./jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
sudo mv jre1.6.0_12 /usr/lib/jvm/
```

3) Create mozilla plugins folder in home folder, create symlink to that folder
```
mkdir ~/.mozilla/plugins/
ln -s /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
```

4) Restart Firefox. Check that the plugin's installed properly by typing about:plugins in Firefox's address bar. Ensure no other plugins are installed that handle anything related to java. 
> **"about:plugins"]File name: libnpjp2.so

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet said:**
> 

5) Run the Java test page: [http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp)
[quote="Test your JVM"]You are using a newer version of JRE than
the current version available on Java.com
Your java configuration is:
    Vendor:     Sun Microsystems Inc.
    Version:    Java 6 update 12
    Operating System:   Linux

---

### Post by QCompson on 2008-12-20
> **jamesstansell said:**
> That sounds familiar.

If you type ```
javascript:java.lang.System.getProperty("java.version")
``` in the firefox url bar and hit enter, what does it do?

Appreciate all the help, folks.

Typing that in the url bar and hitting enter does nothing.


> You are using a 64-bit version of Firefox 3, right?
yep.

I have the same about: plugins output as w0ng.  I also followed pretty much the same steps, except that I unstalled icedtea and openjdk after I moved the new java in /usr/lib/jvm.  

Here is the output of "sudo update-alternatives --config java":

```
There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/cacao
          2    /usr/bin/gij-4.2
          3    /usr/bin/gij-4.3
*+        4    /usr/lib/jvm/java-6-sun/jre/bin/java
          5    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

```
Not sure if that helps.  Firefox should be looking at the plugin in .mozilla/plugins regardless, no?

Thanks.

---

### Post by jamesstansell on 2008-12-21
> **QCompson said:**
> Appreciate all the help, folks.

Typing that in the url bar and hitting enter does nothing.

I have the same about: plugins output as w0ng.  I also followed pretty much the same steps, except that I unstalled icedtea and openjdk after I moved the new java in /usr/lib/jvm.  

Not sure if that helps.  Firefox should be looking at the plugin in .mozilla/plugins regardless, no?

Thanks.

Firefox can sometimes pick up more than one java plugin which can lead to uncertainty about when it will use which one.  If libjpnp2.so is the only java plugin in your list then that should be good.

You did restart Firefox right?

Here's an exercise.  Stop firefox and run the command ```
$ jps
```  Assuming you don't have azureus, eclipse or any other java program running, it should show just one process named Jps.  Now start firefox and go to a java website.  With firefox still running go back to your command window and run ```
$ jps -v
```  Is a new process now listed?  Is it the firefox process?  What is the output from jps -v?

Is java enabled in your browser?  What does [http://browserspy.dk/java.php](http://browserspy.dk/java.php) show?

---

### Post by QCompson on 2008-12-21
> **jamesstansell said:**
> You did restart Firefox right?
Of course.

This is the output of "jps" (before and after starting FF):
```
The program 'jps' can be found in the following packages:
 * cacao-oj6-jdk
 * openjdk-6-jdk
 * sun-java5-jdk
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
bash: jps: command not found
```

It's strange because sudo update-alternatives show the sun-javas are installed, but not the openjdk.  See attached picture [edit... nvm, not really relevant].

> Is java enabled in your browser?  What does [http://browserspy.dk/java.php](http://browserspy.dk/java.php) show?
Yes, enabled.  Java was working (to a limited extent) when icedtea was installed.

See second attachment for what that website shows.  Thank you for your help.

[edit: Tomorrow I'll probably try to wipe any trace of java off my system and start fresh... I'm worried that might be difficult considering I used the sun installer at some point a while ago.  Which java package should I install before I link the plugin?  

Java on linux is frustrating, and it doesn't make it any easier that there are 10,000 different versions of it.  :(  ]

---

### Post by stolk on 2008-12-21
I´ve been looking for this a long time. I tried Icedtea but it didn´t work for me.

Now I tried this (uninstalled icedtea first), I had only to do the first 3 steps and it worked!!

THANKS A LOT! :-):-)

---

### Post by Antionio on 2008-12-22
I've updated the main post with more detailed instructions. I tried to include all the great tips you have submitted! Thank you people! I'm glad this thread has proven to be useful :)

EDIT: I know some people are still having problems with the plugin, so I'll try to follow this thread and update the instructions ever so often. Some day it might even be a lot easier than it is now.

---

### Post by thaumielx72 on 2008-12-23
[QUOTE=w0ng;6408401]Exact instructions I followed per instructions throughout this thread:

3) Create mozilla plugins folder in home folder, create symlink to that folder
```
mkdir ~/.mozilla/plugins/
ln -s /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
```

Many thanks w0ng!!

That step was the one thing messing me up.  I highly recommend using your syntax there - if trying it the way it says in the original post doesn't work.

---

### Post by killer2239 on 2008-12-23
Was able to get java installed with this guide and tested. Thanks. I used the some_path directory, lol so that threw me off a bit.

---

### Post by vgrisham on 2008-12-24
I think this thread should get stickied so that future 64-bitters can refer to it easily.

---

### Post by xjcannonx on 2008-12-25
Thanks for this post!!

I just installed Ubuntu on my other computer for my wife, she tried to upload and couldn't and said to me "Maybe we should just go back to windows"

I almost cringed at that because I knew if I couldn't get it working quickly, I would hear a fit and have to go back to windows (I dual boot so it wouldn't be hard, but i'm just trying to ween her off Microsoft)

Luckily I went back to our great forums we got here and had this problem nipped in the but in minutes, Thanks

---

### Post by dBuster on 2008-12-26
I have followed every posting in this sticky as well as another one in the forums for installing this latest version of java.  I get it to show in the about: plugins however whenever I try to test java it hangs firefox to the point where I need to force quit firefox.  

Any ideas?

---

### Post by vgrisham on 2008-12-27
I'm not an expert at this stuff, but it sounds to me like you have multiple java plugins and or java runtime machines. Go to synaptic and make sure you've removed anything that has to do with icedtea or openjdk.

---

### Post by jamesstansell on 2008-12-27
> **vgrisham said:**
> I'm not an expert at this stuff, but it sounds to me like you have multiple java plugins and or java runtime machines. Go to synaptic and make sure you've removed anything that has to do with icedtea or openjdk.

I've never seen different JRE "interfere" with each other.  Though only issue I've seen is when firefox has multiple java plugins installed.  Even then I haven't seen the browser hang; just sometimes it uses one plugin and sometimes it uses the other.

---

### Post by jamesstansell on 2008-12-27
> **dBuster said:**
> I have followed every posting in this sticky as well as another one in the forums for installing this latest version of java.  I get it to show in the about: plugins however whenever I try to test java it hangs firefox to the point where I need to force quit firefox.  

Any ideas?

Sounds like some library or compiler version issue.

But to start with, make sure that Sun's libnpjp2.so 1.6.0_12 is the only java plugin that firefox is seeing.

---

### Post by vgrisham on 2008-12-27
As I said, I'm not an expert on this. I did get it to work, and until I removed the old plugin, Firefox was behaving strangely (though it didn't lock up).

What advice do you have for the dBuster?

---

### Post by tomdkat on 2008-12-27
I've got this installed now and so far so good!  :)

Peace...

---

### Post by zika on 2008-12-27
there is a new sub-version b03 of Java 64-bit plugin. 24-dec-2008. :)

You can rerun the same script You've used to install b02 since it overwrites everything (after a question) ...

enyou!

---

### Post by dBuster on 2008-12-27
> **jamesstansell said:**
> Sounds like some library or compiler version issue.

But to start with, make sure that Sun's libnpjp2.so 1.6.0_12 is the only java plugin that firefox is seeing.

I had it down to just seeing the one plugin being seen by firefox and I was locking up tighter than a drum.  The only way to get java working again was to install icedtea and gcjwebplugin.so

I had removed from the synaptic package manager all java...

So for now I am leaving as is until I get a day to give it another try or they come out with a deb installer that will update me.  Unless of course someone comes up with a try for me to give a shot at...

---

### Post by dspisak on 2008-12-29
Hi, Antonio.  I followed Tip #1 and Steps #1-#3.  Step #4 was not necessary.  The script had to be modified for the latest build, b3, and date, 22_dec_2008.  Firefox 3.0.5 recognizes it and so far so good.

Thank you for your help.

Dan

---

### Post by ubun_two on 2008-12-30
I got it to work, and it's much less CPU intensive compared to the icetea plugin.

Only thing is that I can't get the sound to work on it.  Does the sound work fine for everyone else?

I did disable the pulseaudio, so that could have something to do wtih it, I suppose.

---

### Post by Big_astur on 2008-12-30
> **ubun_two said:**
> I got it to work, and it's much less CPU intensive compared to the icetea plugin.

Only thing is that I can't get the sound to work on it.  Does the sound work fine for everyone else?

I did disable the pulseaudio, so that could have something to do wtih it, I suppose.
I have sound, at least in this game i have tried to check it :D

[http://www.arcadepod.com/java/details.php?id=5720](http://www.arcadepod.com/java/details.php?id=5720)

---

### Post by ubun_two on 2008-12-30
> **Big_astur said:**
> I have sound, at least in this game i have tried to check it :D

[http://www.arcadepod.com/java/details.php?id=5720](http://www.arcadepod.com/java/details.php?id=5720)
Nope, I get no sound.

You have pulseaudio, right?

---

### Post by dBuster on 2008-12-30
> **jamesstansell said:**
> Sounds like some library or compiler version issue.

But to start with, make sure that Sun's libnpjp2.so 1.6.0_12 is the only java plugin that firefox is seeing.

I have once again removed icedtea and the gcj java.  When I restarted firefox I tested the java and it came back 1.0.5 which is not what I was hoping for and then I checked the plugins again and it was seeing a gcjwebplugin of some sorts so I removed all reference to the gcj from the synaptic package manager and now firefox is only seeing the libnpjp2.so plugin.  However I am back to when I go to test java I lock up tigheter than a drum.  So the issue lies then I would say with something related to that plugin I am removing...  

Any further insight??:confused:

---

### Post by Kleist on 2008-12-31
It works! Thanks a lot. :D

---

### Post by Big_astur on 2008-12-31
> **ubun_two said:**
> Nope, I get no sound.

You have pulseaudio, right?
Yes.

---

### Post by ubun_two on 2008-12-31
> **Big_astur said:**
> Yes.

Alright, I got the sound, once I reinstalled the pulseaudio.

---

### Post by ZoRRoCanCer on 2009-01-21
> **Antionio said:**
> Hello!

I've had HUGE problems with java plugins in the past and I've found forum threads very useful when searching installation help. So I decided to show you how I got the brand new 64bit java plugin working for 64bit Ubuntu (8.04) and the 64bit Firefox 3.0.4.

EDIT: Be sure to read the whole post and try the tips I've added below.

1)

Download Linux x64 JRE bin from the following address:
[https://jdk6.dev.java.net/6uNea.html](https://jdk6.dev.java.net/6uNea.html)

2)

Run the .bin file so that it extracts the jre files. Copy the files where you want to keep them. I put them next to my other JDK's and JRE's.

```

sudo chmod +x jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
sudo ./jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin
sudo mv jre1.6.0_12 /some_path

```

3)

Create a symbolic link to Firefox plugin directory:

```

mkdir ~/.mozilla/plugins/
ln -s /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so ~/.mozilla/plugins/

```

4)

EDIT: These about:config settings might be unnecessary after all. Some people have gotten the plugin working without changing these settings.

Run Firefox and write about:config to the address bar. Write "java" to the filter so that you can find the settings more easily.

Change the following settings:

java.default_java_location_others = /path_to_jre/jre1.6.0_12
java.java_plugin_library_name = libnpjp2


5)

Voila, the plugin should be working now. If not, respond to this thread so we can troubleshoot for different ubuntu configurations. Also if you have some better way to get it working, please let us know.

EDIT:
Here are some tips people have posted:

1) If you're having problems getting java to work, uninstall any previous java version you might have! (for example icedtea and openjdk).

```

sudo apt-get remove icedtea6-plugin openjdk-6-jre

```

2) Try changing the default java jre with ```
sudo update-alternatives --config java
```

If you still don't get the plugin working after this, try to read through the responses of this thread for more tips. I might not update this tutorial so often.

Dude you did great. Thanks

---

### Post by Noo on 2009-01-27
The plug-in is working for me on my fresh Ubuntu 8.10 following the above instructions. I did notice that my Ubuntu version did not install any Java VM by default.

Since I didn't use the Synaptic Package Manager to install this beta the 'java' and 'javac' commands are not working (I've also downloaded and extracted the JDK because I want to do some Java programming). I've extracted both the JDK and JRE to /usr/lib/jvm/ as I assume, being a complete linux-n00b, that this is the most sensible location to put it.

When I run update-alternatives the result is the following. I don't know if it's supposed to give something else, given the current situation.

```

$ sudo update-alternatives --config java
No alternatives for java.

```

My question is how do I 'install' both this beta JRE and JDK so that there is some level of Gnome and console integration.

EDIT: I have a little problem with the plug-in. Audio seems to be lagging behind a lot, even in the simplest applets there is a sound latency of about 500-1000 ms. Audio is performing well in Totem and Gnome, so I don't believe it's something system-wide.

---

### Post by Linux user 66 on 2009-01-27
Worked great for me (Ubuntu 8.10).

Thanks.

---

### Post by dBuster on 2009-01-27
I too am experiencing sound issues with the sound being there at first for games and then it stops or is not functioning.  I am running Jaunty Alpha 3 with a clean install and this 64bit java is the only java installed!  Other than the sound it is quite speedy and impressive to me!!!

Yes I have Pulseaudio installed and I even reinstalled it to see if it would fix the issue...

---

### Post by lazyart on 2009-01-29
Thanks to the OP for posting this.  Finally, LogMeIn.com remote control works from my 64 bit Intrepid system.

---

### Post by Noo on 2009-01-30
I still haven't figured out how to install this java beta for general use throughout ubuntu. Anyone?

---

### Post by novafluxx on 2009-02-13
I installed the release version, and linked the plugin...that works!

Now how do I make this Java work throughout Ubuntu?? I had the bin in /opt and "installed it" there...so now the JRE file is there in /opt

I've tried running java -version and i get
```

The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * cacao-oj6-jre-headless
 * gij-4.2
 * kaffe
 * jamvm
 * openjdk-6-jre-headless
 * cacao
 * gij-4.3
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found

```

---

### Post by Sp|ke on 2009-02-13
I think (know) I've messed up somwhere along the way with this one.
If I try to run any Java applet Firefox shuts down immediatly with the following errors.

```

Didn't find JVM under /home/spike/.mozilla/plugins
firefox: ../../../../src/plugin/solaris/plugin2/common/JavaVM.c:104: InitializeJVM: Assertion `foundJVM' failed.
Aborted

```

Any ideas?

edit: libnpjp2 **is** in .mozilla/plugins and appears in the about : plugins page

---

### Post by oldos2er on 2009-02-14
> **Noo said:**
> I still haven't figured out how to install this java beta for general use throughout ubuntu. Anyone?

 This worked for me: [http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/)

 The link says "hardy," but I'm using Intrepid (8.10) and these instructions worked fine.

---

### Post by dank133 on 2009-02-17
I'm experiencing exactly the same symptoms as sp|ke.

Didn't find JVM under /usr/lib64/mozilla/plugins
firefox: ../../../../src/plugin/solaris/plugin2/common/JavaVM.c:104: InitializeJVM: Assertion `foundJVM' failed.
Aborted

I'm using 64-bit firefox version 3.0.6.

Does anyone know if the 64-bit jre1.0.6_12 plugin works with firefox 3.0.6?

I've read though several forums, my alternatives are set properly.

My only guess, as a noob is that I'm missing some environment variable that points JVM to /usr/java/jre1.0.6_12/bin as opposed to the plugins directory of my browser. Does this make sense?

---

### Post by oldos2er on 2009-02-17
"Does anyone know if the 64-bit jre1.0.6_12 plugin works with firefox 3.0.6?"

 It does.

---

### Post by cardiforia on 2009-02-20
Hello,

It's strange how I follow all your steps but nothing came out. At home I have AMD64 X2 machine and all works just perfect. At my office I have Intel x86_64 based PC and there I have the same installation like at home but I have no working java on the office machine. On both places I have Ubuntu 8.10 64-bit version. I seriously doubt if it depends on the CPU brand at all. Does someone have an idea about this?

Thanks and great day

---

### Post by AprilHare on 2009-02-20
It works, thankyou very much!
Now then: how do I add it as an alternative java using update-alternatives? I need the plugin for another application and it needs to be registered java.

---

### Post by jespdj on 2009-02-21
Installing Sun Java 6 update 12 with the 64-bit plugin is easy: see [Sprocket_dk's guide here](http://ubuntuforums.org/showthread.php?t=1063635). Works on 8.04 as well as on 8.10.

---

### Post by thedavis on 2009-02-23
Thanks, thats worked for me. Now I can upload photos to facebook using the java applet :)

---

### Post by istblacken on 2009-02-24
i followed the instructions and it works perfectly. thanks for the guide.

---

### Post by zika on 2009-02-24
new version is available. (update 14)
instructions are for AMD64, change for other accordingly ...
```
cd ~/Desktop
wget http://www.java.net/download/jdk6/6u14/promoted/b01/binaries/jre-6u14-ea-bin-b01-linux-amd64-03_feb_2009.bin
sudo chmod +x jre-6u14-ea-bin-b01-linux-amd64-03_feb_2009.bin
sudo sh ./jre-6u14-ea-bin-b01-linux-amd64-03_feb_2009.bin
sudo mv jre1.6.0_14 /opt/jre1.6.0_14
(see update below)##sudo ln -s /opt/jre1.6.0_14/lib/amd64/libnpjp2.so ~/.mozilla/plugins
sudo ln -s /opt/jre1.6.0_14/lib/amd64/libnpjp2.so /usr/lib/mozilla/plugins
```open about:config in FF```

java.default_java_location_others -> /opt/jre1.6.0_14
java.java_plugin_library_name -> libnpjpj2.so
```it starts really fast!
and it runs very fast ... real progress ... ;)
**update:**You might choose to install this new jre and link this new plugin with a new jre:```
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/jre1.6.0_14/bin/java" 1
sudo update-alternatives --set java /opt/jre1.6.0_14/bin/java
```but that is not really necessary in the case that You already have latest sun-java6-jre or even sun-java6-jdk installed cause they are already 64-bit and cannot be removed without pulling OpenOffice and similar with them. it seems better to have one full package (complete) and just add this plugin as icing on the cake ... ;) I prefer to do the above.
You might also want to change the names of directories (I for example use /opt/java to put this new jre so I do not need to change anything once a new sub-version arrives. just extract it there and everything is already prepared. only first 4 commands in the first group above are, then, necessary.

**alternative way ([COLOR=Yellow]it doesn't work always, still testing[/COLOR]):**```
wget http://www.java.net/download/jdk6/6u14/promoted/b03/binaries/jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.jar
java -jar jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.jar
(choose /opt/java as install directory)
```it is even quicker and more intuitive for the cost of slightly bigger archive (in case You already have Java installed).
[B]
update:[/B]  After some time and few updates we can stop using ~/.mozilla/plugins folder. It is not necessary anymore. It is commented in code above now ...

---

### Post by rsay on 2009-03-01
Thanks Zika,

Your instructions worked very well. I had to make one adjustment for my system:

```
sudo ln -s /opt/jre1.6.0_14/lib/amd64/libnpjp2.so /usr/lib/mozilla/plugins

```

I'm happy to finally have this working!!

---

### Post by zika on 2009-03-02
> **rsay said:**
> Thanks Zika,

Your instructions worked very well. I had to make one adjustment for my system:

```
sudo ln -s /opt/jre1.6.0_14/lib/amd64/libnpjp2.so /usr/lib/mozilla/plugins

```I'm happy to finally have this working!!
of course, I forgot that line while copying from my notebook. thanks, I've corrected it.
I did not manage to make this work in Opera 10 yet ... ;( but I'm not giving up .. ;))

---

### Post by Kareeser on 2009-03-03
Works great! Facebook photo uploads load zippy, and error free.

Note that the path for the symlink has to be the full path... I didn't know that at first... heh.

Sticky anyone?

---

### Post by broken tibula on 2009-03-23
I tried this so that I could upload photos to Facebook, but it didn't work and now neither does my audio...  :(  Running Ubuntu 8.10, Firefox 3.0.7  I uninstalled Icedtea and Openjdk, tried reinstalling pulseaudio... to no avail.  Help?  Anyone?

---

### Post by linuxpenguin on 2009-03-26
Sorry I can't say about that audio problem.  Check your audio settings though, and make sure they are as they should be.  It may have reset them or changed them in such a way that is causing you to not hear your sound anymore.  You may want to look at what "services" are running too - at least one of the "audio settings management" services should be running.

Anyways, I came here to say that I have created a .deb package from the AMD64 RPM package found over at download.java.net.  I've only tested it on my personal PC but it works fine for me, if you wanna download the .deb it's on my site: [http://www.linuxpenguin.net/content/view/154/1/]("http://www.linuxpenguin.net/content/view/154/1/")
Don't forget you will need to run these commands after, if you do install it:
```
sudo update-java-alternatives -s java-6-sun
sudo ln -s /usr/java/jre1.6.0_12/lib/amd64/libnpjp2.so /usr/lib64/firefox-3.0.7/plugins/
```
Hope it helps you guys out, at least until an AMD64 version makes its way to the repo's.

---

### Post by JimmyA on 2009-03-28
Thank you so much Antionio! This finally worked after looking everywhere to make it work.

---

### Post by scientist47 on 2009-04-07
There is a package for the Sun 64 bit plugin in Jaunty Multiverse:
[http://packages.ubuntu.com/jaunty/sun-java6-plugin]("http://packages.ubuntu.com/jaunty/sun-java6-plugin")
It depends on the bin/jre packages of the same version in the same repository:
[http://packages.ubuntu.com/jaunty/sun-java6-bin]("http://packages.ubuntu.com/jaunty/sun-java6-bin")
[http://packages.ubuntu.com/jaunty/sun-java6-jre]("http://packages.ubuntu.com/jaunty/sun-java6-jre")

Just download and install them, or add the repository and install them.
Then disable or install the icedtea plugin.

I did:
[LIST=1]
[*]add the Jaunty Multiverse repository:
[LIST]
[*]```
sudo -b gedit /etc/apt/sources.list
```
[*]add the line:
```
deb http://ftp.science.nus.edu.sg/ubuntu/ jaunty multiverse
```
[/LIST]
[*]Install sun-java6-plugin and uninstall icedtea6-plugin in Synaptic (After reloading). **DO NOT UPGRADE EVERYTHING**
[*]Disable the jaunty repository, and reload. 
[*]Restarted firefox 3.0.8, and successfully uploaded images to facebook with the advanced interface.[/LIST]

---

### Post by Yellow Pasque on 2009-04-07
scientist47: while it may have worked for you in this instance, it is really dangerous to mix repos from different versions of Ubuntu and I would not recommend it on these forums.

---

### Post by JimmyA on 2009-04-18
(This post can be deleted)

---

### Post by dtoronto on 2009-04-18
Awesome

Thanks

---

### Post by DesertBlade on 2009-06-05
Mad props! Worked flawlessly.  Downloaded the bin from the java website ([http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp))

---

### Post by zika on 2009-06-06
> **DesertBlade said:**
> Mad props! Worked flawlessly.  Downloaded the bin from the java website ([http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp))
I think there is "update 14" available on [https://jdk6.dev.java.net/6uNea.html](https://jdk6.dev.java.net/6uNea.html).

---

### Post by branque on 2009-06-26
thank you, had the problem with java and facebook, but followed your instructions and now its working fine.

---

### Post by owensnick on 2009-07-01
I have followed all instructions to the letter, but still no luck. I've installed release 14 of jdk 6, that works perfectly no problems running or compiling. I added a symbolic link to /usr/mozilla/plugins/ and ~/.mozilla/plugins. Made appropriate changes in about:config.

However firefox still says there is no java plugin installed. about:plugins gives no mention of java and shows no sign it even sees libnpjp2.so.

I don't have icedtea or openjdk6 installed. I'm running Ubuntu 7.04 (old I know) and 64-bit Firefox 3.0.1.

Any ideas or where to go next?

---

### Post by zika on 2009-07-01
> **owensnick said:**
> I have followed all instructions to the letter, but still no luck. I've installed release 14 of jdk 6, that works perfectly no problems running or compiling. I added a symbolic link to /usr/mozilla/plugins/ and ~/.mozilla/plugins. Made appropriate changes in about:config.

However firefox still says there is no java plugin installed. about:plugins gives no mention of java and shows no sign it even sees libnpjp2.so.

I don't have icedtea or openjdk6 installed. I'm running Ubuntu 7.04 (old I know) and 64-bit Firefox 3.0.1.

Any ideas or where to go next?You might want to change the value of **java.java_plugin_library_name** in **about:config** of FF. Put either libnpjp2.so (if You've already made a symbolic link in */usr/mozilla/plugins/* or *~/.mozilla/plugins*) or the _full_ path to that file regardless of making symbolic link. If that does not work we will try some other remedies ...

---

### Post by owensnick on 2009-07-01
> **zika said:**
> You might want to change the value of **java.java_plugin_library_name** in **about:config** of FF. Put either libnpjp2.so (if You've already made a symbolic link in */usr/mozilla/plugins/* or *~/.mozilla/plugins*) or the _full_ path to that file regardless of making symbolic link. If that does not work we will try some other remedies ...

Thanks for the suggestion, still no change. I already had libnpjp2.so in the **java.java_plugin_library_name **preference. I changed to full path and still no java in about:plugins. I've made sure all the permissions for all of the java release 14 and particuarly the plugin are correct so allow all to read + execute. But to no avail...

Is there a way to get firefox to give a diagnostic on what it is reading/trying to load from the plugin directory?

---

### Post by owensnick on 2009-07-01
Ah...I haven't fixed it, but I think I've found the reason:

LoadPlugin: failed to initialize shared library /usr/lib/jvm/jdk1.6.0_14/jre/lib/amd64/libnpjp2.so [/usr/lib/jvm/jdk1.6.0_14/jre/lib/amd64/libnpjp2.so: wrong ELF class: ELFCLASS64]

Hopefully this should help me find where I've gone wrong.

---

### Post by herteljt on 2009-07-04
If this has already been mentioned sorry for the repeat.

I ran into troubles launching web start applications. I had java update 14 installed correctly but had failed to changed the preferences in firefox so that web start launched the correct java version. 

I went to  Edit > Preferences > Applications tab and changed the java webstart application to correct the problem.

---

