---
title: "Netatalk - No encrypted authentication"
date: 2005-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by tjm on 2005-12-10
Hm, I cannot get encrypted authentication into work with netatalk... Some modules seem to be missing in /usr/lib/netatalk/.

The only available ones are uams_gss.so, uams_guest.so, uams_krb4.so (does not work), uams_pam.so, uams_passwd.so.

None of them lead to encrypted authentification. So what do I do wrong?

---

### Post by gruepig on 2005-12-10
It's been a long time since I've used netatalk, but if you are just trying to set up communications between Linux and OS X (no OS 9 or earlier), you might consider using samba instead of netatalk.  Both OS X and Linux have good support for samba.

---

### Post by tjm on 2005-12-11
I read about this. But the issue is that I need access over the internet to my server from Mac OS 9.1 up to X 10.4.3 from several machines.

OK, I have FTP running but it is not that comfortable. Netatalk works over TCP, but IMHO Samba does not? Do I think correctly?

---

### Post by gruepig on 2005-12-12
> **tjm]I read about this. But the issue is that I need access over the internet to my server from Mac OS 9.1 up to X 10.4.3 from several machines.
[/QUOTE]

You can use samba from Mac OS 9.1.  It's just awkward (and likely slow).  There are a number of samba/SMB clients said:**
> http://www.anders.com/projects/netatalk/passwords.html[/url] is helpful?  (I'm guessing you've already looked at that though.) 

[QUOTE]
OK, I have FTP running but it is not that comfortable. Netatalk works over TCP, but IMHO Samba does not? Do I think correctly?

Both netatalk and samba run over TCP/IP.  Netatalk and AppleTalk in OS 9 (but not 8?) can run over TCP; older AppleTalk runs over it's own protocol (AppleTalk/DDP).  Windows SMB historically ran over NetBEUI and other non-TCP protocols, but Linux samba and modern Windows use TCP.

By the way, FTP is not encrypted.  You might consider scp/sftp which is part of ssh and is encrypted.  There are a number of GUI sftp clients for OS X (e.g., fugu).  I don't know of any sftp clients for Mac classic, but NiftyTelnet SSH supports a (clunky) scp client.

If none of those methods are sufficient, another way to tranfer files might be to set up apache and webdav on your Linux box and upload/download files via web browsers on the macs.

Sorry, I don't think I'm really helping here ....

---

### Post by AlexMorin on 2006-03-09
We are having the same issues over here : [http://www.ubuntuforums.org/showthread.php?t=44535&highlight=uams_dhx.so](http://www.ubuntuforums.org/showthread.php?t=44535&highlight=uams_dhx.so)

Problem seems to be that the uam necessary for encryption (uams_dhx.so) is not included in the Ubuntu package of Netatalk.

If anyone can help us compile it from source, we'd be glad! 'Cause, clear text passwords are not my cup of tea!

---

### Post by AlexMorin on 2006-03-20
Bump... Ideas anyone?

I can't turn on a server with clear-text passwords. Can't we build the missing module from source?

---

### Post by gruepig on 2006-04-04
Crossposting.

I just installed netatalk with the following:

apt-get source netatalk
sudo apt-get build-dep netatalk
sudo apt-get install cracklib2-dev
cd netatalk-2.0.3
DEB_BUILD_OPTIONS=ssl debuild
sudo dpkg -i ../netatalk-*.deb

I think the passwords are being sent encrypted. tcpflow indicates that the password was being sent "AFP3.1.DHCAST128". It looks like directory contents (ls) is sent clear text, but file contents is sent encrypted.

---

### Post by AlexMorin on 2006-04-04
[QUOTE=gruepig]Crossposting.

I just installed netatalk with the following:

apt-get source netatalk[/QUOTE]

That command returns an error (running edubuntu 5.10) : 

```
sh: dpkg-source: command not found
```

Am I to understand that you had this error and used ```
sudo apt-get build-dep netatalk
``` to get around it?

---

### Post by AlexMorin on 2006-04-04
[QUOTE=AlexMorin]Am I to understand that you had this error and used ```
sudo apt-get build-dep netatalk
``` to get around it?[/QUOTE]
I suppose that was the case.

apt-get source netatalk **OK, I guess. dpkg command not found error**
sudo apt-get build-dep netatalk **OK, aside from lots of non-authenticated packages**
sudo apt-get install cracklib2-dev **OK, same**
cd netatalk-2.0.3 ***What, where?***
DEB_BUILD_OPTIONS=ssl debuild ***Where do I define this?***
sudo dpkg -i ../netatalk-*.deb

The issue I now have, which is a real noob one : where is that directory? In the current directory, there are three files (netatalk_2.0.3-1ubuntu1.diff.gz, netatalk_2.0.3-1-1ubuntu1.dsc and netatalk_2.0.3.orig.tar.gz). No Netatalk directory. I know it's somewhere, but I can't remember where. ](*,) 

And the build options? What are they? :oops:

Thanks for your time! :) :)

---

### Post by gruepig on 2006-04-05
>apt-get source netatalk **OK, I guess. dpkg command not found error**

dpkg-source command not found?  'sudo apt-get install dpkg-dev'.  (By the way, to find out what package dpkg-source is in, run 'dpkg -S dpkg-source'.)

If the error was that the package was not found, you'll need to add universe to your repositories.  (Should have documented this for the sake of completeness.)
 
Add the following lines to your /etc/apt/sources.list:
```

deb-src http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

and then run 'apt-get update' to update the package index files.  (Note: this doesn't update packages, just the list of packages which are available.)

> sudo apt-get build-dep netatalk **OK, aside from lots of non authenticated packages**
> sudo apt-get install cracklib2-dev **OK, same**

Without knowing what specific errors you were getting, this is probably okay.

> cd netatalk-2.0.3 ***What, where?***

'apt-get source netatalk' just put it in my current directory.  I have that directory and the three netatalk files you mentioned.

> DEB_BUILD_OPTIONS=ssl debuild ***Where do I define this?***

You just run it.  That sets the $DEB_BUILD_OPTIONS environment variable and runs debuild (which reads the environment variable).  I copied the command from netatalk-2.0.3/debian/README.Debian.

>sudo dpkg -i ../netatalk-*.deb

> The issue I now have, which is a real noob one : where is that directory? > In the current directory, there are three files
> (netatalk_2.0.3-1ubuntu1.diff.gz, netatalk_2.0.3-1-1ubuntu1.dsc and 
> netatalk_2.0.3.orig.tar.gz). No Netatalk directory. I know it's somewhere, > but I can't remember where. ](*,) 

> And the build options? What are they? :oops:

See above.

> Thanks for your time! :) :)

Hope it works for you.

BTW, I'm running this on breezy powerpc.

---

### Post by AlexMorin on 2006-04-10
apt-get source netatalk **OK after installing dpkg-dev**
sudo apt-get build-dep netatalk **OK, already done**
sudo apt-get install cracklib2-dev **OK, same**
cd netatalk-2.0.3 **OK, since step one worked this time around**
DEB_BUILD_OPTIONS=ssl debuild ***This does not seem to work***
sudo dpkg -i ../netatalk-*.deb <--- Not done yet.


The build options command, the way I tried it:

# DEB_BUILD_OPTIONS=ssl debuild[B]
-bash: debuild: command not found[/B]

If I try this:

# $DEB_BUILD_OPTIONS=ssl debuild[B]
-bash: =ssl: command not found[/B]

So this is where I stand. It's probably nothing, but I'll be more than glad if you help me out. :)

---

### Post by AlexMorin on 2006-04-10
Status:
DEB_BUILD_OPTIONS=ssl debuild **OK**
sudo dpkg -i ../netatalk-*.deb ***No such file error***

The build options command, the way I tried it:

```
# DEB_BUILD_OPTIONS=**"**ssl debuild**"**
```
It works! With the **double quotes**, the environment variable is set properly.

```
# echo $DEB_BUILD_OPTIONS
ssl debuild
```

Now, the last command: 

# dpkg -i ../netatalk-*.deb
dpkg cannot find the archive...

This assumes that we stayed in the netatalk directory right? Because there are no .deb files in that directory.

We are close to the end! :D

---

### Post by gruepig on 2006-04-12
No quotes.  You want to set the DEB_BUILD_OPTIONS to ssl and then run the command debuild. Looks like you don't have debuild, so run 'sudo apt-get install devscripts' to install debuild, then cd, set the options variable, run debuild to create the package, and dpkg -i to install.

Summary of the whole process (corrected and commented):
sudo apt-get install dpkg-dev devscripts # install needed deb devel tools
apt-get source netatalk # get the netatalk source
sudo apt-get build-dep netatalk # get netatalk dependencies
sudo apt-get install cracklib2-dev # get cracklib library headers (another dependency)
cd netatalk-2.0.3 # change directories to the source directory
DEB_BUILD_OPTIONS=ssl debuild # build a deb package with ssl support
sudo dpkg -i ../netatalk-*.deb # install the package

---

### Post by AlexMorin on 2006-04-12
Thanks piggy! I think it worked! But, wouldn't the whole thing be easier using aptitude in CLI? I thought aptitude was the way to go now?

> DEB_BUILD_OPTIONS=ssl debuild # build a deb package with ssl support
Now, it's complaining that it can't sign.

```
Now signing changes and any dsc files...
Could not find a signing program (pgp or gpg)!
debuild: fatal error at line 788:
running debsign failed
```
The .deb is created, so I just plowed ahead anyway.

> sudo dpkg -i ../netatalk-*.deb # install the package
This is wrong. It's an underscore before the *.
So the line should be:
```
sudo dpkg -i ../netatalk_*.deb # install the package
```

The services are started properly! And my OS X can connect using encrypted passwords now! No pop-up complaining of clear-text! Yahoo!

---

### Post by gruepig on 2006-04-13
Yay!

---

### Post by AlexMorin on 2006-04-13
[QUOTE=gruepig]Summary of the whole process (corrected and commented):[/QUOTE]

Allow me to re-post the instructions, since Gruepig and I worked hard on this. I made one change, to correct the -/_ confusion at the last command, and separated some commands for clarity for noobs like me.

Anyway, this is what worked for me, running **Edubuntu 5.10 "Breezy", minimal server install** (which could explain why I needed some extra packages, or not). As always, your mileage may vary. Please post if it does!

You'll be running most commands as root. Since Edu/Ubuntu does not activate root by default, sudo is needed.

**sudo apt-get install dpkg-dev** # Needed to get the source in step #3
**sudo apt-get install devscripts** # Needed for the 'debuild' command
**apt-get source netatalk** # Get the netatalk source
**sudo apt-get build-dep netatalk** # Get netatalk dependencies
**sudo apt-get install cracklib2-dev** # Get cracklib library headers (another dependency)
**cd netatalk-2.0.3** # Change directories to the source directory. Of course if the version changes, so will the directory name.
**DEB_BUILD_OPTIONS=ssl debuild** # This is two commands. Setting the 'ssl' option, and then build a deb package (debuild) with ssl support. You will get a 'signing' error here, but should be fine.
**sudo dpkg -i ../netatalk_*.deb** # Install the package. Note that underscore...

You're done, and now you've got the services running and encryption support. All you need to do is configure it to match your setup. The default settings will work for most. There is excellent documentation in netatalk-version#/doc/htmldocs and at [http://netatalk.sourceforge.net/2.0/htmldocs/](http://netatalk.sourceforge.net/2.0/htmldocs/) .

Again, thanks to gruepig for helping out! Karma points to you! :) 

Enjoy![LEFT][/LEFT]

---

### Post by Kadin2048 on 2006-04-13
Great work Alex and Gruepig!

I just thought I'd add my two cents: it is possible to suppress that GPG signing error (although it's not fatal and doesn't really hurt anything I guess) by building the package using:

sudo dpkg-buildpackage -us -uc

Apparently the -us and -uc flags must disable keychecking. (To be honest I don't know, but it does suppress the error.) Then dpkg -i installs it.

Anyway, great to have gathered the information together.

---

### Post by Kadin2048 on 2006-04-13
System duped the post.

---

### Post by scarecro on 2006-06-18
not sure if this applies to everyone, but i just followed AlexMorin's directions in Dapper (dist-upgraded from breezy) and couldn't get any dhx uams to build. turned out i needed to add:
**sudo apt-get install libssl-dev**
after the installation of cracklib2-dev.

you can also change the last instruction to:
**sudo debi**
to install the package&#8230;

---

### Post by n8gray on 2006-07-14
> **scarecro said:**
> not sure if this applies to everyone, but i just followed AlexMorin's directions in Dapper (dist-upgraded from breezy) and couldn't get any dhx uams to build. turned out i needed to add:
**sudo apt-get install libssl-dev**
after the installation of cracklib2-dev.

you can also change the last instruction to:
**sudo debi**
to install the package&#8230;
Aha!  Thank you!

---

### Post by Kadin2048 on 2006-07-19
So I had Netatalk working perfectly under Breezy, and now that I upgraded to Dapper, it seems to be totally borked.

I posted a message to the netatalk-admins list and haven't gotten any responses, so I thought I'd ask here as well. The error I'm getting is the following, whenever I try to start netatalk:
```
Starting AppleTalk services (this will take a while): nbp_rgstr: Connection timed out
Can't register keyhole:Workstation@*
nbp_rgstr: Connection timed out
Can't register keyhole:netatalk@*
 atalkd papd afpd cnid_metad.
```

I have tried rebuilding and reinstalling the netatalk package from source completely, and still get the error. I'm totally at a loss for what to do. I haven't changed anything in my network...but I'm really screwed if I can't get file sharing going with my Mac.

**EDIT: Found the problem!!**
Naturally, only after posting about this could I actually figure out what was up. Turns out the problem was *not *the upgrade to Dapper after all, but my simultaneous installation of VMWare.

Turns out Netatalk has issues when you have more than one network interface connected, and you have an empty atalkd.conf file (which is A-OK when you just have one interface). Not sure exactly what happens, but basically it is a Bad Thing.

In installing VMWare, I created several psuedo-devices (vmnet1, etc.) which are aliased to my real network device (eth0).

Long story short, the problem got solved by me adding a line to my atalkd.conf (heretofore empty) that reads "eth0" and nothing else. This tells Netatalk to only use that interface and ignore the other ones.

Found this solution because it was mentioned in passing in a [very old Usenet posting]("http://groups.google.com/group/comp.os.linux.networking/browse_thread/thread/90a2d83dca774d46/c3da79796bf595e8%23c3da79796bf595e8")...more info on my error message there.

---

### Post by rjsquire on 2006-10-20
Thank you for this posting.  I was experiencing the same thing.  Your suggestion fixed my problem.

---

### Post by halstead on 2006-11-28
On my dapper install I had to modify the file debian/rules like so,
#vi /usr/local/src/netatalk-2.0.3/debian/rules
DEB_CONFIGURE_EXTRA_FLAGS += --with-ssl-dir \
becomes
DEB_CONFIGURE_EXTRA_FLAGS += --with-ssl-dir=/usr/include/openssl \

After this the directions given above worked.

---

### Post by JayDoubleM on 2007-02-25
I had to use 
> sudo dpkg-buildpackage -us -uc
for it to work, then I installed using
> sudo debi
just for the record

---

### Post by MoreCalories on 2007-04-05
I'm having trouble getting this to work under Dapper. Could someone post step by step instructions?

---

### Post by thornomad on 2007-04-15
I tried to put together step-by-step instructions from [this thread]("http://ubuntuforums.org/showthread.php?p=1273565") (it worked for me on Dapper and Edgy) and I posted it here:

**_[[COLOR="Red"][SIZE="2"]How To: Install Netatalk (AFP) on Ubuntu with Encrypted Authentication[/SIZE][/COLOR]]("http://www.damontimm.com/blog/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/")_**

Will also try and put it on the Tutorials & Tips section.

---

