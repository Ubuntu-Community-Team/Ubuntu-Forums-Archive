---
title: "HowTo: Install Eclipse x64 IDE with PDT and WTP (WST)"
date: 2008-07-14
forum: x86 64-bit Users
---

### Post by hodge24 on 2008-07-14
Here's the method I used for installing the x64 version of Eclipse IDE, including PDT, and WTP (WST). The original article is posted on my blog, 64bitjungle.com - [http://www.64bitjungle.com/tech/64-bit-eclipse-linux-installation-including-pdt-wtp-wst-atf-and-mysql-sql-explorer-plugin/](http://www.64bitjungle.com/tech/64-bit-eclipse-linux-installation-including-pdt-wtp-wst-atf-and-mysql-sql-explorer-plugin/)

I'll add the MySQL plugin and ATF plugins when I have some more spare time (not much of that these days with a 3 month old Daughter!)

I've basically BBCoded the original article:

Unfortunately, there's no 64 Bit PDT all-in-one, but I managed to install a 64 Bit equivalent by cobbling together the relevant packages available by using the Eclipse Update Manager system, after initially installing the latest version of Eclipse Classic 3.3.2 64 Bit.

I wanted to keep everything (or as much as possible) 64 Bit, so I also download and installed the 64 Bit JRE, which can be [downloaded here]("http://www.java.com/en/download/linux_manual.jsp") (or use the [direct link to the bin file]("http://javadl.sun.com/webapps/download/AutoDL?BundleId=18707")). The method for installing the 64 Bit JRE is the same as the 32 Bit version - after the file downloaded to my desktop, I opened up a new Terminal Window (Applications -> Accessories -> Terminal), traversed to the directory I wanted to install it into, moved the file, made it executable, and ran it to install:

If the "java" directory doesn't exist, it needs to be created first:

```
sudo mkdir /usr/java
cd /usr/java
sudo mkdir 64
cd 64
sudo mv ~/Desktop/jdk-6u5-linux-x64.bin /usr/java/64/
sudo chmod a+x jdk-6u5-linux-x64.bin
sudo ./jdk-6u5-linux-x64.bin
```

listing the directory

```
ls
```

should return

```
jre1.6.0_05
```

which is the directory containing the necessary Java binaries.

```
cd /opt
sudo mv ~/Desktop/eclipse-SDK-3.3.2-linux-gtk-x86_64.tar.gz /opt
sudo tar -zxvf eclipse-SDK-3.3.2-linux-gtk-x86_64.tar.gz
```

then rename the eclipse directory:

```
sudo mv eclipse eclipse64
```

I also needed to get the newly installed Eclipse to run with the newly installed JRE - by default, the eclipse executable in the directory will try and detect Java and use whatever it finds, so I created a shell script:

```
cd eclipse64
sudo gksu gedit eclipse.sh
```

containing the following:

```
#!/bin/bash
PATH=/usr/java/64/jre1.6.0_05/bin:$PATH
/opt/eclipse64/eclipse
```

Now instead of running the eclipse executable, I run eclipse.sh (make sure it's executable)

```
sudo chmod 755 eclipse.sh
```

before running

```
/opt/eclipse64/eclipse.sh
```

**PDT and WTP Plugins**

Goto Help -> Software Updates -> Find and Install, and select "Search for new features to install".Click on "New Remote Site" for each of the following:

```

Name: PDT, URL: http://download.eclipse.org/tools/pdt/updates/
Name: WTP, URL:  http://download.eclipse.org/webtools/updates/
Name: GEF, URL:  http://www.eclipse.org/gef/updates/
Name: EMF, IRL:  http://www.eclipse.org/modeling/emf/updates/

```

Actually, there are only a couple of components required from the GEF (Graphical Editing Framework) and EMF (Eclipse Modeling Framework) packages to satisfy dependencies - WTP (Web Tools Platform) requires a package from GEF, and GEF from EMF...

After adding these, click on Finish - the Update Manager will then query any mirrors for the latest versions of the plugins. Once it has finished, a dialog appears, where it is possible to select the plugins to download and install. First, I selected PDT - the Update Manager then informed me that PDT requires files from WTP, so I tried clicking the "Select Requires" button, hoping that it would sort out the dependencies on my behalf. Unfortunately, nothing happened... So, I selected WTP manually, then expanded GEF -> Eclipse SDK R3.3.1 and Selected Graphical Editing Framework 3.3.1v20070814, then expanded EMF -> EMF SDK 2.3.2 and selected Eclipse Modeling Framework (EMF) - org.eclipse.emf.ecore 2.3.2v200802051830... I could **then** click "Select Required" to get the last few residual required dependencies... Phew...

OK, with the dependencies sorted, click Next, accept the agreements, click finish, and go and make a brew (that's Tea) while the Update Manager downloads and installs the requested stuff.

Once it's finished, restart Eclipse, and it's done.

Oh, if you want a desktop icon, just create a file on your Desktop called Eclipse.desktop,

```
cd ~/Desktop
gedit Eclipse.desktop
```

and add the following:

```
[Desktop Entry]
Categories=;
Encoding=UTF-8
Exec=/opt/eclipse32/eclipse.sh
Hidden=false
Icon=/opt/eclipse64/icon.xpm
Icon[en_US]=/opt/eclipse64/icon.xpm
Name=Eclipse
Name[en_US]=Eclipse
Terminal=false
Type=Application
Version=1.0
```

---

### Post by lord of konsum on 2008-07-24
Hmm, GEF and EMF has moved to new urls..

OLD:

Name: GEF, URL:  [http://www.eclipse.org/gef/updates/](http://www.eclipse.org/gef/updates/)
Name: EMF, IRL:  [http://www.eclipse.org/modeling/emf/updates/](http://www.eclipse.org/modeling/emf/updates/)

NEW:

Name: GEF, URL:  [http://download.eclipse.org/tools/gef/updates/releases](http://download.eclipse.org/tools/gef/updates/releases)
Name: EMF, IRL:  [http://download.eclipse.org/modeling/emf/updates/releases](http://download.eclipse.org/modeling/emf/updates/releases)

---

### Post by ericson578 on 2008-09-10
I get this error message when I try and install the updates to eclipse:
Cannot find a solution satisfying the following requirements Match[requiredCapability: org.eclipse.equinox.p2.iu/org.eclipse.gef.source.feature.group/[3.4.0.v20080115-677-8082A5696H274A,3.4.0.v20080115-677-8082A5696H274A]].


Also, when I tried to add these urls it didn't work:

Name: WTP, URL:  [http://download.eclipse.org/webtools/updates/](http://download.eclipse.org/webtools/updates/)
Name: GEF, URL:  [http://www.eclipse.org/gef/updates/](http://www.eclipse.org/gef/updates/)
Name: EMF, IRL:  [http://www.eclipse.org/modeling/emf/updates/](http://www.eclipse.org/modeling/emf/updates/)


Any suggestions? Why on earth is it so hard to use the eclipse update manager :(

---

### Post by ericson578 on 2008-09-11
I'm using eclipse Version: 3.4.0
Build id: I20080617-2000

So I think my problems stem from this guide being for an older version of eclipse. Was hopeful it would work though, doah.

From the update page I tried typing in "EMF", "GEF", and "WTP".  Lots of options to choose from, so it's hard for me to know if I installed all the right stuff.  Unfortunately eclipse can't seem to resolve the dependencies for me.

After installing what I hope was the correct packages for emf, gef, and wtp, I searched for "PDT" and chose:
PDT Feature

but I get this error message when I try and install it:

Cannot complete the request.  See the details.
Cannot find a solution satisfying the following requirements Match[requiredCapability: org.eclipse.equinox.p2.iu/org.eclipse.ltk.core.refactoring/[3.3.0.v20070606-0010,3.3.0.v20070606-0010]].

---

### Post by ericson578 on 2008-09-11
Wow that was tough!

I finally got it working though, here's a very quick how (I'll try and write up more specifics when I get time in a few days)

basically I went to this site: [http://download.eclipse.org/tools/pdt/downloads/](http://download.eclipse.org/tools/pdt/downloads/)

I chose the 2.0.0 Integration Build to install.
Clicking on [http://download.eclipse.org/tools/pdt/downloads/release.php?release=I20080909](http://download.eclipse.org/tools/pdt/downloads/release.php?release=I20080909) 
brought up a screen that lists all of the dependencies needed before you can actually install pdt.  Note that some of the links were broken, to find those packages I just searched for example "eclipse GEF" and then looked for the same build to download.

The instructions on this page on how to unpack items really helped:[http://wiki.eclipse.org/PDT/Installation#Eclipse_3.4_.2F_Ganymede_.2F_PDT_2.0](http://wiki.eclipse.org/PDT/Installation#Eclipse_3.4_.2F_Ganymede_.2F_PDT_2.0) .  I made all of my install dirs under /opt (the same dir that I installed ecslipse too).

After all of the installs this is what my /opt looks like:

dltk-core-sdk-I-I200809081043-200809081043-incubation.zip_/
dtp-1.6.1RC2-200809090500.zip_/
eclipse/
emf-runtime-2.4.1.zip_/
GEF-ALL-3.4.0.zip_/
org.eclipse.php_feature-I20080909.zip_/
wtp-wst-M-3.0.2-20080906061108.zip_/

I installed PDT last, and it works! :) can't wait to being way more productive with my php coding.

---

