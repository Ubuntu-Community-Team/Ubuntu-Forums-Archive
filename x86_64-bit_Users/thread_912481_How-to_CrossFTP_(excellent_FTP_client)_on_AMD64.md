---
title: "How-to: CrossFTP (excellent FTP client) on AMD64"
date: 2008-09-06
forum: x86 64-bit Users
---

### Post by RavanH on 2008-09-06
Looking for a good FTP client for my Ubuntu Hardy AMD64, I was disappointed by gFTP and since I decided to move away from FireFox 3.0 (way too sluggish and bloated) towards the lean and mean Opera browser, I could not use the excellent FireFTP plugin anymore :(

I had previously used the java app [_CrossFTP_]("http://crossftp.com/") on a 32bit system. It can be started straight from their website by way of Java WebStart. Now we all know, that SUN's version is not available for 64bit systems, unless you want to go and [_install 32bit FF or Swiftweasel_]("http://ubuntuforums.org/showthread.php?t=202537") (How-to and script by Kilz). And the OpenJDK Web Start resulted in the error: ```
javaws http://crossftp.com/crossftp.jnlp
netx: Invalid XML document syntax.
``` According to CrossFTP Support this is caused by javaws not being 100% compatible.

On the CrossFTP website is mentioned the possibility to run the java app locally, so I wanted to try it out. To my great relief, CrossFTP is working like lightning now and is available to all users on the system.
So for anyone who wants to try it out and does not want to wait for SUN's Java WebStart for 64bit ([_early 2009_]("http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695")?), here is how I did it. 


[FONT="Impact"][SIZE="3"][COLOR="SlateGray"]Prerequisites[/COLOR][/SIZE][/FONT]

- You have Java installed properly on your system. Either **Sun Java** or **OpenJDK** will do but I found this app running fastest on OpenJDK. See the Sticky [_Java on AMD64_]("http://ubuntuforums.org/showthread.php?t=774956") to get either or both.

- You (user) are in the sudoers list meaning you can run commands 'as root'.


[FONT="Impact"][SIZE="4"][COLOR="Sienna"]How-to install the excellent FTP client java application CrossFTP on 64bit Ubuntu for all users[/COLOR][/SIZE][/FONT]

1. Open a Terminal Screen and create a dir for CrossFTP:
```
sudo mkdir /opt/crossftp
```

2. Get the files:
```
cd /opt/crossftp
sudo wget -c http://crossftp.com/crossftp.jar http://crossftp.com/crossftp-resources.jar http://crossftp.com/commons-logging.jar http://crossftp.com/jnlp.jar http://crossftp.com/logo_big.gif
```
If the connection got lost and files are incomplete, just run step 2 again and download will resume.

3. Create a new file for command line startup:
```
sudo gedit /usr/bin/crossftp
``` Paste the following code into it ```
#!/bin/sh
# CrossFTP Client Startup batch file. For more information, please refer to http://www.crossftp.com

java -cp /opt/crossftp/crossftp.jar:/opt/crossftp/crossftp-resources.jar:/opt/crossftp/commons-logging.jar:/opt/crossftp/jnlp.jar crossftp.ui.MainFrameWindow
``` Save it and close the text editor.

4. Make it executable:
```
sudo chmod +x /usr/bin/crossftp
```

5. At this point the FTP client can be started from command line. Please do so to test: ```
crossftp
``` If this fails, try and repeat the previous steps and see if you missed anything.

6. Create a new menu link:
```
sudo gedit /usr/share/applications/crossftp.desktop
``` Paste the following code into it ```
[Desktop Entry]
Categories=Network;FileTransfer;
Encoding=UTF-8
Exec=crossftp
GenericName=CrossFTP
Icon=/opt/crossftp/logo_big.gif
Name=CrossFTP
Terminal=0
Type=Application
Version=1.0
``` Save it and close the text editor.

Now, the app is available for all users straight from their 'Applications > Internet' (or 'Computer > Network' in Xubuntu) menu! Drag and drop the menu item to anywhere on your panel(s) or to your Cairo Dock for quick access :)


[FONT="Impact"][SIZE="3"][COLOR="SlateGray"]Tips[/COLOR][/SIZE][/FONT]

To make CrossFTP fit better into your desktop environment, open the app and go to menu 'Tools > Global Options' and set on the tab 'Display' Look & Feel to GTK+. Also choose a font type that is actually on your system. Close and restart CrossFTP to apply changes.

Supposedly, when CrossFTP runs locally it checks for updates. I have not encoutered this situation yet (just using it for a week) but I suppose three will be some sort of notice when there is a newer version. Follow the **update instructions** below.

If you have two both Sun Java and OpenJDK installed on your system, you might want to test on which engine CrossFTP runs best. To change the engine do in terminal ```
 sudo update-alternatives --config java
``` And follow instructions to switch to the other engine. I have found that CrossFTP starts fastest on the **OpenJDK** engine, and normal operation seems smoother too. I have not found any incompatibility issues yet... Other than the initial javaws problem, ofcource ;)


[FONT="Impact"][SIZE="3"][COLOR="SlateGray"]Update[/COLOR][/SIZE][/FONT]

Whenever you find there is a newer version available, update by giving the following commands in terminal
```
cd /opt/crossftp
sudo rm crossftp.jar crossftp-resources.jar commons-logging.jar jnlp.jar
sudo wget http://crossftp.com/crossftp.jar http://crossftp.com/crossftp-resources.jar http://crossftp.com/commons-logging.jar http://crossftp.com/jnlp.jar
```


[FONT="Impact"][SIZE="3"][COLOR="SlateGray"]Remove[/COLOR][/SIZE][/FONT]

Not happy with it? Want to get rid of it completely?
```
sudo rm -R /usr/bin/crossftp /usr/share/applications/crossftp.desktop /opt/crossftp
```
And to remove your personal settings do:
```
rm -R ~/.crossftp
```


--RavanH

---

### Post by ariel on 2008-09-06
For the best graphical FTP client, I recommend filezilla. It's been fairly recently rewriten with a Linux focus. I've used it to transfer folder trees with thousands and thousands of files and it has shown to be amazingly solid.

A slighly outdated (but fully functional) version is available in the repos:

> sudo apt-get install filezillaor altenatively you can get the very latest version from the project website:

[http://filezilla-project.org/](http://filezilla-project.org/)

---

### Post by RavanH on 2008-09-07
> **ariel said:**
> For the best graphical FTP client, I recommend filezilla. It's been fairly recently rewriten with a Linux focus. I've used it to transfer folder trees with thousands and thousands of files and it has shown to be amazingly solid.

A slighly outdated (but fully functional) version is available in the repos:

or altenatively you can get the very latest version from the project website:

[http://filezilla-project.org/](http://filezilla-project.org/)

Thanks for the tip, but I found Filezilla to be very bad at keeping the connection with my hosting providers server alive. Even with the Keep Alive setting explicitly checked. CrossFTP is the only one so far that does a good job at it.

Also I miss the ability to open new tabs in Filezilla. Keeping multiple connections open without having to switch windows, is very useful to me :)

---

