---
title: "which IM can login Microsoft Office Communicator ?"
date: 2007-11-29
forum: Wine
---

### Post by magicsky on 2007-11-29
[SIZE="5"][B][SIZE="5"][SIZE="4"]As title: which IM can login Microsoft Office Communicator?
Pidgin Can't, and I try to wine Communicator, but it's can't "next" when choose Directory , of course, I can't change Directory[/SIZE][/SIZE][/B]

Did anyone hnow how to solve it? or which IM  can login Microsoft Office Communicator?

Thanks![/SIZE]

---

### Post by Vadi on 2007-11-29
I've never heard of that protocol... but from the word "Microsoft" in it, I doubt many can (microsoft purposely doesn't publish/publishes really horribly documentation so that nobody else can use their custom protocols).

So, best bet is with wine. I'll give a try myself.

---

### Post by Vadi on 2007-11-29
Um, I tried downloading the trial version, but for some reason in the end after umpteen steps it gave me a link to download, not the client...

---

### Post by mojorising on 2007-12-27
I would really like to be able to log into LCS/ Communicator as my company uses it and I can't get them to use XMPP/ Jabber (or anything else, for that matter) and I'm sure there's lots of people out there in the same situation.

You might want to read this thread to find out more on the subject: [http://ubuntuforums.org/showthread.php?t=526857&highlight=communicator](http://ubuntuforums.org/showthread.php?t=526857&highlight=communicator)


Mike

---

### Post by Thund3rstruck on 2008-01-13
Yea, Communicator/LCS is a messenger client being offered with the new sharepoint initiative where the server runs internally so you can filter communications through out the enterprise. 

My company just killed all Jabber access and is forcing the use of LCS. It was only a matter of time before various individuals got fired from comments made on LCS to other co-workers. 

I have tried the Pidgin plug-in without success so for now it looks like VMWare is the only way to work with LCS

---

### Post by mojorising on 2008-12-19
Hi. There is great news for those of us who have to log into LCS servers at work -- the SIPE project has resumed and has a functional test version out. 

SIPE is a plug-in for Pidgin, allowing it to log in and exchange messages on an LCS server (Communicator server).

[https://sourceforge.net/projects/sipe/](https://sourceforge.net/projects/sipe/)

Installing SIPE is more of an "advanced user" operation as it currently must be compiled. I believe an unsupported DEB package for Debian/ Ubuntu will be released before very long.

Visit the SIPE project page and forums ([https://sourceforge.net/forum/forum.php?forum_id=688534](https://sourceforge.net/forum/forum.php?forum_id=688534)) for more information as well as installation instructions. 

Basically, the install procedure is like this:

sudo apt-get install pkg-config libglib2.0-dev libgtk2.0-dev pidgin-dev libpurple-dev libtool intltool comerr-dev 
 
Then do the following:
tar -xjvf pidgin-sipe-1.3.1.tar.bz2 
cd pidgin-sipe-1.3.1 
./configure --prefix=/usr 
make  
sudo make install 


I'm quite sure you also need the build-essential meta package to compile the code. 

If you have any questions or need any more information, post to the SIPE forum (after reading all the readmes and information already provided of course. ;)  ). 


Hope this helps some people out there who may have been struggling or (worse) waiting to switch from Windows because of the lack of LCS client. 


Mike


FYI: I just noticed this thread is in the Wine section (not sure why that is) but Wine is not needed to run the LCS/ Communicator plugin.

---

### Post by MickPatten on 2009-01-25
Might sound silly, but for noobs - don't forget you'll need to get the bz2 file from SourceForge and have it in the same dir as you are running the TAR command to make and install.

Get the bz2 file here;
[http://sourceforge.net/project/showfiles.php?group_id=194563](http://sourceforge.net/project/showfiles.php?group_id=194563)

This post was to save them from hunting around the forum links to find the bz2 file...

---

### Post by mangloid on 2009-02-02
any reason why the protocol wont be listed in pidgin after installing?

---

### Post by mark_knowles on 2009-03-17
For those of you wanting SSL/TLS support, building the packages is not very easy.  It involves getting the current .tar.gz file and applying some of the git updates.

As I can't quite remember how to reproduce the output, I've uploaded a .deb package with some instructions here:
[URL="http://mknowles.com.au/wordpress/index.php/2009/03/18/pidgin-and-microsoft-office-communicator-in-ubuntu/"]
http://mknowles.com.au/wordpress/index.php/2009/03/18/pidgin-and-microsoft-office-communicator-in-ubuntu/[/URL]

Here's the content of that site reproduced.  Please visit the URL for up to date info.

**Howto:**

For anyone looking for Microsoft OCS/LCS support in Pidgin, here is a debian package that you can install in Ubuntu.  It has been tested in Ubuntu Intrepid on i386.  It comes with no support, but I would like to hear if people are successfully using this package or if it is broken in any way.

This package is built from the sources at the SIPE project at [http://sipe.sourceforge.net/](http://sipe.sourceforge.net/).  A big thankyou to Anibal Avelar aka “fixxxer”.  I only packaged the project, so I cannot take any credit.  If I’ve missed thanking/attributing anyone else, please let me know.

Download the package here: [pidgin-sipe_1.3.2-1_i386.deb]("http://mknowles.com.au/wordpress/wp-content/uploads/2009/03/pidgin-sipe_132-1_i386.deb")

Install the package by running the following command:

sudo dpkg -i pidgin-sipe_1.3.2-1_i386.deb

If you connect to a corporate server that runs Active Directory, the initial configuration can be a bit difficult to figure out.

Here’s a rule of thumb:

**Basic Tab:**

Protocol: Microsoft LCS/OCS
Username: Your Exchange email address
Password: The password for your domain account
Local Alias: Leave this blank, it’s not needed

**Advanced Tab:**

Use Proxy: Enable this setting
Proxy Server: Change this to the server your company is using.  See note below.
Use non-standard port: This may be required.  I have seen some servers run on port 5061
Connection type: SSL/TLS
User Agent: Leave as is
Auth User: The username you use to log into your domain (not your email address)
Auth Domain: The domain your Windows workstation logs into.

**Determining your Server:**

You can usually find out your server by typing the following command:

netstat -na | more

Look for any entries that have a remote address of 5060 or 5061.  That is a dead giveaway.

**Build instructions:**

If anyone manages to re-build this package, some instructions would be good.  I used a strange combination of a pre-built tar file and some portions of the git repository.  It was difficult to reproduce, hence me sharing the package.

---

### Post by stavinski on 2009-03-30
I tried adding an account in the XML file with what I thought might be the right settings, still no dice, doesn't seem to recognize the protocol? 

I'm running Hardy, possibly part of theproblem if package is for Intrepid.

---

### Post by fatbuttlarry on 2009-08-05
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=123763&stc=1&d=1249512444[/IMG]

I created a small how-to on the connection settings, hope this helps some users (the how-to is for Windows, but it should be identical settings for Ubuntu)

[http://fatbuttlarry.blogspot.com/2009/08/pidgin-microsoft-office-communicator.html](http://fatbuttlarry.blogspot.com/2009/08/pidgin-microsoft-office-communicator.html)

I'll get this running in Ubuntu shortly, but I just wanted to post this, as there's not much on the internet about getting it working.

-Tres

---

### Post by mynk on 2009-11-05
$ sudo apt-get install pidgin-sipe

Worked for me on Karmic Koala. The account details should be as below

Basic

Protocol: Microsoft OCS/LCS
Username:
Password:

Advanced

Use proxy: checked
Proxy Server: your ocs server
Connection Type: SSL/TLS
Auth User: domain account name
Auth Domain: your domain

Courtesy link: [http://www.randombugs.com/linux/howto-install-configure-microsoft-ocs-lcs-pidgin-ubuntu-linux.html](http://www.randombugs.com/linux/howto-install-configure-microsoft-ocs-lcs-pidgin-ubuntu-linux.html)

I was trying to get pidgin work on XP also. SIPE can be installed from -

[http://sourceforge.net/projects/sipe/](http://sourceforge.net/projects/sipe/)

Hope this helps,
Mayank:D

---

### Post by TheCleaner on 2009-12-16
> **mynk said:**
> $ sudo apt-get install pidgin-sipe

Worked for me on Karmic Koala. The account details should be as below

Basic

Protocol: Microsoft OCS/LCS
Username:
Password:

Advanced

Use proxy: checked
Proxy Server: your ocs server
Connection Type: SSL/TLS
Auth User: domain account name
Auth Domain: your domain

Courtesy link: [http://www.randombugs.com/linux/howto-install-configure-microsoft-ocs-lcs-pidgin-ubuntu-linux.html](http://www.randombugs.com/linux/howto-install-configure-microsoft-ocs-lcs-pidgin-ubuntu-linux.html)

I was trying to get pidgin work on XP also. SIPE can be installed from -

[http://sourceforge.net/projects/sipe/](http://sourceforge.net/projects/sipe/)

Hope this helps,
Mayank:D

Works like a champ!  Thank you very much!

---

### Post by dferrero on 2009-12-29
Shameless plug:

A commercial multi-protocol, multi-platform instant messaging client JBuddy Messenger is available also. JBuddy Messenger supports AIM, ICQ, MSN, Yahoo, XMPP, Lotus Sametime and of course, Microsoft LCS 2005 and OCS 2007. It is available for Mac, Linux, Windows and other Unixes. A free, 30-day evaluation license is available by submitting a request at: [http://www.zionsoftware.com/products/messenger/](http://www.zionsoftware.com/products/messenger/)

As of this writing (late December 2009), the best LCS/OCS version, 3.2.091222 of JBuddy is at 
[http://www.zionsoftware.com/products/messenger/downloads/beta/]("http://www.zionsoftware.com/products/messenger/downloads/beta/")
This version is expected to go GA in early January 2010.

Pricing is $30 per user with bulk-license discounts available.

David Ferrero
Zion Software, LLC
[http://www.zionsoftware.com/]("http://www.zionsoftware.com/")

---

### Post by suyog on 2010-05-01
> **mark_knowles said:**
> For those of you wanting SSL/TLS support, building the packages is not very easy.  It involves getting the current .tar.gz file and applying some of the git updates.

As I can't quite remember how to reproduce the output, I've uploaded a .deb package with some instructions here:
[URL="http://mknowles.com.au/wordpress/index.php/2009/03/18/pidgin-and-microsoft-office-communicator-in-ubuntu/"]
http://mknowles.com.au/wordpress/index.php/2009/03/18/pidgin-and-microsoft-office-communicator-in-ubuntu/[/URL]

Here's the content of that site reproduced.  Please visit the URL for up to date info.

**Howto:**

For anyone looking for Microsoft OCS/LCS support in Pidgin, here is a debian package that you can install in Ubuntu.  It has been tested in Ubuntu Intrepid on i386.  It comes with no support, but I would like to hear if people are successfully using this package or if it is broken in any way.

This package is built from the sources at the SIPE project at [http://sipe.sourceforge.net/](http://sipe.sourceforge.net/).  A big thankyou to Anibal Avelar aka “fixxxer”.  I only packaged the project, so I cannot take any credit.  If I’ve missed thanking/attributing anyone else, please let me know.

Download the package here: [pidgin-sipe_1.3.2-1_i386.deb]("http://mknowles.com.au/wordpress/wp-content/uploads/2009/03/pidgin-sipe_132-1_i386.deb")

Install the package by running the following command:

sudo dpkg -i pidgin-sipe_1.3.2-1_i386.deb

If you connect to a corporate server that runs Active Directory, the initial configuration can be a bit difficult to figure out.

Here’s a rule of thumb:

**Basic Tab:**

Protocol: Microsoft LCS/OCS
Username: Your Exchange email address
Password: The password for your domain account
Local Alias: Leave this blank, it’s not needed

**Advanced Tab:**

Use Proxy: Enable this setting
Proxy Server: Change this to the server your company is using.  See note below.
Use non-standard port: This may be required.  I have seen some servers run on port 5061
Connection type: SSL/TLS
User Agent: Leave as is
Auth User: The username you use to log into your domain (not your email address)
Auth Domain: The domain your Windows workstation logs into.

**Determining your Server:**

You can usually find out your server by typing the following command:

netstat -na | more

Look for any entries that have a remote address of 5060 or 5061.  That is a dead giveaway.

**Build instructions:**

If anyone manages to re-build this package, some instructions would be good.  I used a strange combination of a pre-built tar file and some portions of the git repository.  It was difficult to reproduce, hence me sharing the package.

Where I need to run netstat command? Sorry but i am complete noob here. I am having Pidgin 2.6.6 in Ubuntu 10.04 and also installed LCS plugin 1.8 from synaptic. I see different options than described here for settings.

Please help.

---

