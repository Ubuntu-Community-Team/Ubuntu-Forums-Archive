---
title: "Sun java 6 from official site -&gt; firefox"
date: 2008-09-04
forum: x86 64-bit Users
---

### Post by pivot@pivpoint.no on 2008-09-04
Greetings!

Theres a whole bunch of posts about java here at ubuntuforums. So many it's inpossible to find what I'm looking for.

I've downloaded and compiled the java 64 bit from java.com using their guide [http://java.com/en/download/help/5000011400.xml#install](http://java.com/en/download/help/5000011400.xml#install)

This all worked fine. Placed it in /usr/java as the guide suggested. However, event though I've removed all java from synaptic firefox still uses the old open source java.

about: plugins

```
GCJ Web Browser Plugin 0.96-pre

    File name: libgcjwebplugin.so
    The GCJ Web Browser Plugin executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	GCJ 	class,jar 	Yes
application/x-java-applet 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.3 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	GCJ 	class,jar 	Yes
application/x-java-applet;jpi-version=1.4.2_01 	GCJ 	class,jar 	Yes
application/x-java-bean 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.3 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	GCJ 	class,jar 	Yes
application/x-java-bean;jpi-version=1.4.2_01 	GCJ 	class,jar 	Yes
```

When I try javatester.com it tells me

```
Java Version: 1.5.0 from Free Software Foundation, Inc.
```

How can I make it use the sun java that I've just compiled? I've never quite understood all this firefox plugins structure. Where's the configuration info that tells firefox what plugins to use for what content?

Any help woould be much appriciated!

---

### Post by jespdj on 2008-09-04
Sun's 64-bit Java version does not include a browser plug-in. Did you really download the source code and compile a Java runtime environment yourself? It sounds like you are making things way too complicated.

Ubuntu 8.04 comes with the [OpenJDK](http://openjdk.java.net/) implementation of Java, which is Sun's project to make their Java implementation 100% open source. The 64-bit version of OpenJDK Java does contain a browser plug-in (although it doesn't work with all applets yet).

You can install it with:
```
sudo apt-get install openjdk-6-jre
```

---

### Post by pivot@pivpoint.no on 2008-09-04
Yeah, I did. And the reason is that the icedtea (and the openjdk) doesnt work with a bank security system we use in Norway called BankID. It's a java applet I need to have working to be able to log on to my internet bank, and pay for stuff at Norwegian webshops.

I havent gotten anything to work with this BankID system, and I read that Swedish have the same problem. I can get regular java to work with icedtea n such, but not the stuff I really need...

:(

---

### Post by pivot@pivpoint.no on 2008-09-04
Figured I might aswell try the openjdk again. Since you mentioned it.
I get an error now. For some reason...

```
The following packages have unmet dependencies:
  openjdk-6-jre: Depends: openjdk-6-jre-headless (= 6b09-0ubuntu2) but it is not going to be installed
E: Broken packages

```

---

### Post by pivot@pivpoint.no on 2008-09-04
```
pivot@pivlaptop:~$ sudo apt-get install openjdk-6-jre-headless
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openjdk-6-jre-headless: Depends: tzdata-java but it is not going to be installed
E: Broken packages

```

```
pivot@pivlaptop:~$ sudo apt-get install tzdata-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  tzdata-java: Depends: tzdata (= 2008b-1ubuntu1) but 2008e-1ubuntu0.8.04 is to be installed
E: Broken packages

```

```
pivot@pivlaptop:~$ sudo apt-get install tzdata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tzdata is already the newest version.
The following packages were automatically installed and are no longer required:
  openoffice.org-draw classpath-gtkpeer openoffice.org-impress
  odbcinst1debian1 gnome-menus classpath-common java-common
  openoffice.org-math unixodbc fastjar openoffice.org-calc cacao libwpg-0.1-1
  classpath
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


I cannot remove and install an older version of tzdata, since it seems to be really important to the system. This is all messed up...?

---

### Post by philinux on 2008-09-04
Use synaptic. Custom Filters. Choose Broken. See if that fixes it.

---

### Post by pivot@pivpoint.no on 2008-09-04
Nope. Sorry. Nothing in the list under custom filters - broken

---

### Post by ashmew2 on 2008-09-04
Try

sudo apt-get install -f

to fix broken dependencies!

Plus could you hook me up the BankID site/java applet u use ? I just installed a 64 bit system myself and just remembered seeing ur thread that i need java too..Im not guna compile it but use openjdk..Link me and ill see what i can do ! :D

If that fixes it , try 

sudo aptitude install openjdk-6-jre

---

### Post by pivot@pivpoint.no on 2008-09-04
ash: You can try
[https://www2.sparebank1.no/portal/2619/3_privat?_nfpb=true&_pageLabel=page_privat_forside](https://www2.sparebank1.no/portal/2619/3_privat?_nfpb=true&_pageLabel=page_privat_forside)
Click "Logg inn" and type in any number  11 digits and it will send you to the BankID applet.

The sudo apt-get install -f didnt do anything
And when I try to run the sudo aptitude install openjdk-6-jre 
this is what I get 

```

The following packages have unmet dependencies:
  tzdata-java: Depends: tzdata (= 2008b-1ubuntu1) but 2008e-1ubuntu0.8.04 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
tzdata [2008e-1ubuntu0.8.04 (hardy-updates, now) -> 2008b-1ubuntu1 (hardy)]

Score is 80

Accept this solution? [Y/n/q/?] 

```

Should I really downgrade? If I choose yes it asks me if I want to remove a bunch of other packages

```
The following packages are unused and will be REMOVED:
  cacao classpath classpath-common classpath-gtkpeer fastjar gnome-menus 
  libwpg-0.1-1 odbcinst1debian1 openoffice.org-calc openoffice.org-draw 
  openoffice.org-impress openoffice.org-math unixodbc 
The following NEW packages will be automatically installed:
  lesstif2 libaccess-bridge-java openjdk-6-jre-headless openjdk-6-jre-lib 
  tzdata-java 
The following packages will be DOWNGRADED:
  tzdata 
The following NEW packages will be installed:
  lesstif2 libaccess-bridge-java openjdk-6-jre openjdk-6-jre-headless 
  openjdk-6-jre-lib tzdata-java 
0 packages upgraded, 6 newly installed, 1 downgraded, 13 to remove and 0 not upgraded.
Need to get 28.9MB/29.3MB of archives. After unpacking 35.7MB will be used.
Do you want to continue? [Y/n/?] 

```

---

### Post by ashmew2 on 2008-09-04
Go for it....you can upgrade later...The primary concern is to get a stable dependency structure isnt it ? Plus ill give that link a try and get back to you...

Btw , You installed packages when you were compiling ? (library packages with lib in their names ? )

I was trying to compile VLC on my end and i f'ed up my dependencies as well lol...

---

### Post by pivot@pivpoint.no on 2008-09-04
Well. It was a automated process, but I assume it did install some libs.

---

### Post by ashmew2 on 2008-09-04
If you fixed that dependency issue , try a 

```
sudo apt-get install ubuntu-restricted-extras
```

for the sun-java6-jre plus codecs + unrar and stuff..

---

### Post by Kilz on 2008-09-04
There is a solution to the Sun java issue. [The 32bit browser with flash and Sun Java plugins script]("http://ubuntuforums.org/showthread.php?t=202537") still works. In fact its sole use now is for people who need a Sun Java plugin where the openjdk one does not work. It will install a 32bit firefox, or perhaps swiftweasel (a optimized firefox build)and working plugins alongside of your 64bit browser.

Sun java 6 does not have a 64bit plugin, no matter where you look or try it just doesnt exist. The 64bit browser needs a 64bit plugin.

---

### Post by pivot@pivpoint.no on 2008-09-04
The Sun java still doesnt work, Even after the dependencies was fixed and the openjdk-6-jre was installed.

Beginning to think about the 32bit firefox. Have had nice success with it in earlier distros.

---

### Post by pivot@pivpoint.no on 2008-09-05
After a reboot it now seems to be using Sun Java.

Javatester.com:

```
Java Version: 1.6.0 from Sun Microsystems Inc
```

The Java.com site also tells me I have Java 6 update 0 from Sun Microsystems.

about: plugins:

```
GCJ Web Browser Plugin (using IcedTea) 1.0

    File name: gcjwebplugin.so
    The GCJ Web Browser Plugin (using IcedTea) executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes
```


Although. The BankID stuff still doesnt work.... :(
Still thinking about the 32 bit version. Unless someone has any more suggestions?

---

### Post by Kilz on 2008-09-05
> **pivot@pivpoint.no said:**
> After a reboot it now seems to be using Sun Java.

Javatester.com:

```
Java Version: 1.6.0 from Sun Microsystems Inc
```

The Java.com site also tells me I have Java 6 update 0 from Sun Microsystems.

about: plugins:

```
GCJ Web Browser Plugin (using IcedTea) 1.0

    File name: gcjwebplugin.so
    The GCJ Web Browser Plugin (using IcedTea) executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes
```


Although. The BankID stuff still doesnt work.... :(
Still thinking about the 32 bit version. Unless someone has any more suggestions?

Icedtea is not Sun Java.

---

### Post by pivot@pivpoint.no on 2008-09-05
I know. Any that kinda puzzles me. Since the Java.com site and javatester.com tells me I'm using Sun - but the about: plugins tells me it's Icedtea....

Anyways. Installed firefox32 instead, and got the java n stuff working. I still cannot get the BankID to work though. Weird problem. Now it just dies when trying to access the site...

---

### Post by jamesstansell on 2008-09-05
I wonder if the appletviewer in the sun-java6-jdk package will run the bank applet?  I assume probably not.  Too bad I can't try it out.

---

### Post by Kilz on 2008-09-06
> **pivot@pivpoint.no said:**
> I know. Any that kinda puzzles me. Since the Java.com site and javatester.com tells me I'm using Sun - but the about: plugins tells me it's Icedtea....

Anyways. Installed firefox32 instead, and got the java n stuff working. I still cannot get the BankID to work though. Weird problem. Now it just dies when trying to access the site...

You can try to install lib32nss-mdns and I also recommend using Swiftweasel (optimized firefox build) on the howto in case you went with firefox.

---

### Post by pivot@pivpoint.no on 2008-09-06
Yeah. Installed swiftweasel too, and now it's set as default browser. Seems to be working nice:)

Although the bankid stuff still doesnt work. The browser hangs when trying to access the bankid java. Checked synaptic and I already had lib32nss-mdns.

Guess this was more difficult than I was hoping for

---

### Post by Sef on 2008-09-07
> Sun java 6 does not have a 64bit plugin, no matter where you look or try it just doesnt exist. The 64bit browser needs a 64bit plugin.

One is [coming]("http://ubuntuforums.org/showthread.php?t=774956") in early 2009.

---

### Post by pivot@pivpoint.no on 2008-09-07
Oh... so the java from this address

[http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80)

isnt what I was looking for in the first place? Some threads claim that sun has released a 64bit version. Some doesnt. Not sure what to think. However. It's all really difficult to make work, so I'll guess I'll have to use a virtualbox windows for my banking stuff. Kinda sux though.

---

### Post by Sef on 2008-09-07
> Some threads claim that sun has released a 64bit version.

Sun has released a 64-bit version of Java as your link shows.  However, Sun has not released a 64-bit java plug-in yet.   That is due in early 2009.

---

### Post by JAwuku on 2008-09-09
If I remember rightly, browsers such as Opera and Kubuntu's Konqueror use the java executable directly; they do not depend on a plugin. Maybe you could give these a try.

[_**Opera download for 64-bit**_]("http://www.opera.com/download/index.dml?opsys=Linux%20x86_64&lng=en&ver=9.52&platform=Linux%20x86_64&local=y")

---

### Post by pivot@pivpoint.no on 2008-09-11
Sorry man. Didnt work either... :( 
Java is installed in it's default location, as you can see above...

---

