---
title: "Yahoo pool"
date: 2008-08-10
forum: x86 64-bit Users
---

### Post by shane4stef on 2008-08-10
Anyone know how to get java working for yahoo pool...dont wanna be  swiching to 32bit firefox again...just want my 64bit to be working as it should...I know this is just java`s  fault...anyone know when the proper 64bit plugin will be up to date and ready for us all?

---

### Post by shane4stef on 2009-01-30
New java update now works with yahoo pool...Ubuntu just gets better and better

---

### Post by jp_coll2003 on 2009-01-31
HOWTO: Java64 with 64-bit Firefox plugin
This tutorial was written specifically for Java 1.6.0_12, but should work fine on future revisions.


Installing Java for 64-bit

Begin by downloading Java from Sun. Download Here (Linux x64 self-extracting JRE file)

or paste this command into the terminal:

Code:

wget -c 'http://www.java.net/download/jdk6/6u12/promoted/b02/binaries/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin'

Next, we'll create an install directory in /opt (as this is probably the best place for development applications).

Code:

cd /opt
sudo mkdir java
cd java

Let's copy the installer file to the java directory.

Code:

sudo cp ~/jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin /opt/java/

Finally, let's execute the installer

Code:

sudo bash jre-6u12-ea-bin-b02-linux-amd64-08_dec_2008.bin

For good measure, let's register this as the default Java provider.

Code:

sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/jre1.6.0_12/bin/java" 1
sudo update-alternatives --set java /opt/java/jre1.6.0_12/bin/java

Installing Firefox plugin
First, lets remove the gcj web plugin:
Code:

sudo apt-get remove icedtea-gcjwebplugin

If it comes up with "not found" or the like, ignore it and continue.

Since we have it all setup, all we need to do is install the Firefox plugin. This can be done in one simple command (change according to version).

Code:

mkdir ~/.mozilla/plugins
ln -s /opt/java/jre1.6.0_12/lib/amd64/libnpjp2.so ~/.mozilla/plugins/

You can test the plugin by restarting your browser and going to [http://www.javatester.org/version.html](http://www.javatester.org/version.html) and checking for the pink box and line of text.
__________________
HOWTO: Java64 with 64-bit Firefox plugin
Last edited by Frak; 2 Weeks Ago at 12:29 PM.. Reason: Fixed some mistakes here and there.
Frak is online now Report Post   	Reply With Quote

---

### Post by Vadi on 2009-01-31
Thanks for the info

---

### Post by shane4stef on 2009-02-02
This does not work now. I just used the proper 64bit version using Killz scripts. 2 clicks and both installed and now yahoo pool and other things java and flash are working great. not saying everything will as killz says its just in testing still..but so far it absolutely works for what i want. Thanks to jp_coll2003 for your info...was gonna try your way but seen killz script and it saved a lot of hassle. But many thanks anyways.

---

