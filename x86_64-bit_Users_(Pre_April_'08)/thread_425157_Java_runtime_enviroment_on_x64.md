---
title: "Java runtime enviroment on x64"
date: 2007-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by ffxr on 2007-04-27
Hi..

i need to install a Java Runtime environment on my x64 system..

can anyone recommend the most stable and straightforward way to do this, please..?

i have had a search through the forum & realize this probably gets discussed at length, but i am getting conflicting messages... i am worried some the informations may be out of date...

I have visited the Sun website and they do offer a 64bit download, but in their install notes i notice:

[B]"NOTE:
Linux x64 download: Please use the 32-bit version for Java applet and Java Web Start support. "[/B]

I need java applet & Java Web Start Support for the web application i NEED to get running... I don't want to start installing things in a haphazard trial & error way, so could anyone who has it working properly on there system, pls step forward and let me know how they have achieved it... i am open to any method as long as it WORKS..

thanks.

---

### Post by brew1brew on 2007-04-27
check out Kilz howto and script to install 32bit firefox + java, flash and other plugins.

[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

Les

---

### Post by ffxr on 2007-04-27
yes.. thanks.. i had 32 bit browser installed via Kilz script... but any java enabled sites were crashing my browser..

i have now installed a JRE via the relevant sections in this: [https://help.ubuntu.com/community/FirefoxAMD64FlashJava](https://help.ubuntu.com/community/FirefoxAMD64FlashJava)

& i can get my application to launch.. but it seems a bit flaky.. and the mouse doesnt seem to be working right..  

The reason for my concern over this is that i need to run real time financial stock market charting software, you can maybe undestand my concern at trying to ensure as reliable a java enviroment as possible...

i am considering installing a 32 bit linux os & dual booting or running a 32 bit virtual OS...tho,  i would rather stay native 64bit..

i am taking a little cool off period.. now to consider my options & i am very open to any comment at all.

---

### Post by brew1brew on 2007-04-27
yeah, the first time I used it, it was using blackdown java and it was crashing on every site I went to. I installed the Sun 32 bit java to fix it. This tread describes how to fix it manually. 

[http://ubuntuforums.org/showthread.php?t=416001](http://ubuntuforums.org/showthread.php?t=416001)

I think I installed Sun's Java 6, Kilz changed his script to install Sun's Java 5 (or 1.5) as he doesn't care for 6. I'm running Java 6 on my wifes machine without issue and Java 5 on mine without issue.

So you can install it manually or use Kilz's latest script to fix it.

Les

---

### Post by ffxr on 2007-04-28
blackdown kills my 64bit firefox..  (is there any other way to get a JVM in a 64bit browser?)

i used Kilz script (thanks dude) and installed 32bit firefox & the Java plugin, then i installed Java Web Start as per this instruction: [http://dmartin.org/weblog/running-java-web-start-apps-on-ubuntu-linux-for-amd-64](http://dmartin.org/weblog/running-java-web-start-apps-on-ubuntu-linux-for-amd-64)

my application seems to be nice and stable, so im gonna stick with AMD64 xubuntu.. i am very happy with this outcome...thanks..

*i should have named this thread Java Web Start.. i will change it if i can.

---

