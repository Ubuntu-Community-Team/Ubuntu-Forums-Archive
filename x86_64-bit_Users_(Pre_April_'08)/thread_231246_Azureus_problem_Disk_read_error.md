---
title: "Azureus problem: Disk read error"
date: 2006-08-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by mr.f on 2006-08-07
Hi,

I've encountered a problem with Azureus. After a while (this can happen after anything between a few minutes to a few hours after starting the download) the torrent is always interrupted by an error: Disk read error, NullPointerException.

This is with the Azureus and Java versions included with 64-bit dapper drake, ie Azureus 2.4.0.2 and FSF Java 1.4.2. I've not had any problems with other applications (for instance Bittornado) so I don't think it is a hardware problem.

Has anyone else encounterd this? Any ideas what the problem is?

I've not yet tried the latest Azureus or Sun Java.

---

### Post by Kilz on 2006-08-07
> **mr.f said:**
> Hi,

I've encountered a problem with Azureus. After a while (this can happen after anything between a few minutes to a few hours after starting the download) the torrent is always interrupted by an error: Disk read error, NullPointerException.

This is with the Azureus and Java versions included with 64-bit dapper drake, ie Azureus 2.4.0.2 and FSF Java 1.4.2. I've not had any problems with other applications (for instance Bittornado) so I don't think it is a hardware problem.

Has anyone else encounterd this? Any ideas what the problem is?

I've not yet tried the latest Azureus or Sun Java.

Then you might want to report the error to [Azerus]("http://azureus.sourceforge.net/") and/or try the newest one.

---

### Post by RAOF on 2006-08-07
Just a stab in the dark: Are you saving the torrent on to a FAT32 partition, and have you got the "sparse file support" option enabled (I think it's enabled by default)?  From memory that combination won't work.

If not, then latest azureus would be a good idea :).

---

### Post by Cosmik Debris on 2006-08-08
I've had similar problems with Azureus on a 32 bit machine, saving the torrent to a ext3 filesystem.

I've uninstalled the Azureus package, downloaded and installed the Azureus package from the azureus site. I also use JDK 1.5.0_07 downloaded from Sun, and the problem didn't occur anymore. 

Azureus runs for over a week without any error.

Not sure what is causing the issue, whether it is the Azureus package, the Java package, or maybe the GCJ/GIJ packages.

---

### Post by beefcurry on 2006-11-09
i think this deserves a closer look, Im having this problem as well, any way around it?

---

### Post by FluffyElmo on 2006-11-09
I'd recommend installing Sun Java, I've run Azureus for ages and saved files to all sorts of file systems (ext3, xfs, reiser) without any issues. Just download the latest 64bit JVM from [http://java.sun.com]("http://java.sun.com") and change the Azureus shell script to use the new JVM.

As a side note, I had issues running Eclipse with GCJ and they went away with the traditional JVM. I'd say it's not yet perfect but it's interesting for smaller projects...

---

### Post by theonhighgod on 2006-11-22
im having the problem described here, tho im not sure what version of java im using, this is the only thing in Google that seems to make much sense on the issue, all i can tell is the error is quite an internal java ish error, and i know nothing of java!? the filesystem is ext3, and its the latest azureus from the repositories with the java that the azureus package automatically marks,

---

### Post by beefcurry on 2006-11-23
well ive got my azureus working :). It seems to be a known bug on Edgy, if youve got the newest azureus installed from the actual azureus site then just install sun-java for it to work. The Synaptic Sun-Java should work.

---

### Post by usererror on 2006-12-20
> **beefcurry said:**
> well ive got my azureus working :). It seems to be a known bug on Edgy, if youve got the newest azureus installed from the actual azureus site then just install sun-java for it to work. The Synaptic Sun-Java should work.

I've installed Azureus from their site, but i'm using Sun Java from their website...and I am getting this error.  I guess i'll try the Apt Java install..

UPDATE:  I kept my Sun Java I downloaded from Sun...Removed my Azureus that I had installed from the package from Azureus' website, and then installed Azureus from apt-get and now I am no longer having the problem!

---

### Post by mtownbelgium on 2007-01-02
Well i just installed azureus from apt-get on a clean fresh 6.10 ubuntu, and i'm having the same problem, saving my torrents on a ext3 partition...

i just used "apt-get install azureus", which came with some java stuff. i'm gonna try to install sun's java from synaptic and see what's up with that

*now downloading*

well, i'll write more later to tell you guys if the same error has happened.

---

### Post by beefcurry on 2007-01-02
you will need to install Sun-java for it to work.

---

### Post by mtownbelgium on 2007-01-02
> **mtownbelgium said:**
> Well i just installed azureus from apt-get on a clean fresh 6.10 ubuntu, and i'm having the same problem, saving my torrents on a ext3 partition...

i just used "apt-get install azureus", which came with some java stuff. i'm gonna try to install sun's java from synaptic and see what's up with that

*now downloading*

well, i'll write more later to tell you guys if the same error has happened.

ok, it's been running for about 8 hours now, and it's doing good !

---

### Post by xthaparian on 2007-01-02
By Default AZUREUS will create FILE DATA beforehand and then download the file.

Its like creating EMPTY bucket to create space and then slowly fill the bucket.

But if you enalbe this option on FAT32 it will give error.

Try disabling this option in Azureus..and the problem should go away.

:neutral:

---

### Post by mtownbelgium on 2007-01-03
> **xthaparian said:**
> By Default AZUREUS will create FILE DATA beforehand and then download the file.

Its like creating EMPTY bucket to create space and then slowly fill the bucket.

But if you enalbe this option on FAT32 it will give error.

Try disabling this option in Azureus..and the problem should go away.

:neutral:
I had the problem with ext3 anyway..

---

### Post by jon_liverpool on 2007-03-01
Yep. I've had this problem for a while now. I used apt-get today to install Azureus and all of it's dependencies (automatically) on a fresh install of Ubuntu 6.1 (Edgy) using the ext3 filesystem. I've just had the error message pop up, "disk read error - nullpointerexception".

I'm going to try and get Azureus to use Sun Java....

---

### Post by moon2js on 2007-04-17
I'm not up with the politics, but is there a reason why Sun Java isn't used by default? Is it not GNU-compatible?

---

### Post by FluffyElmo on 2007-04-17
Sun Java was never open source, you had to agree to a Sun licensing agreement which among other things put restrictions on redistribution. The gcj project was started to create an open source alternative and when it became functional enough was included in most Linux distributions. 

Now that Sun has open sourced the JVM I'd expect it to be included by default or at the very least easier to install. I don't know if it is planned for Feisty but the JVM now seems to be in the standard Universe repositories.

---

### Post by arsadogi on 2007-04-21
yeap.Fesity fawn amd64 user and after a great deal of effort setting up my router-firewall i am facing exactly the same problem that mentioned above.if you guy's find any solution let us know,so i am gonna keep an eye on the forum.

---

### Post by bLUEbYTE on 2007-04-23
> **arsadogi said:**
> yeap.Fesity fawn amd64 user and after a great deal of effort setting up my router-firewall i am facing exactly the same problem that mentioned above.if you guy's find any solution let us know,so i am gonna keep an eye on the forum.

Exactly same here.

---

### Post by swswka on 2007-05-12
> **arsadogi said:**
> yeap.Fesity fawn amd64 user and after a great deal of effort setting up my router-firewall i am facing exactly the same problem that mentioned above.if you guy's find any solution let us know,so i am gonna keep an eye on the forum.


xm , geia sou volioti xristi linux ! 
Egw eimai neos xristis twn linux (polles oi apories loipon :confused:  , alla rwtwntas pas stin poli ) 
kai sigekrimena exw to xaroumeno elafaki. Exw loipon afto to problima, me to azureus pou ksafnika leei : 
Disk write error, NullPointerException. Den kserw an einai diaforetiko epeidi oi ipoloipoi anaferoun oti anti gia write, tous bgazei read. tespa.
Lpz se neotera kai se lisi tou problimatos!

---

### Post by beefcurry on 2007-05-13
If you guys read the previous posts, then you should know what to do. Just install Sun Java and it will work, you can get it from automatix if you are lazy

---

### Post by mhudson on 2007-05-21
hey gang...

In my particular circumstance I was stupid enough to have two copies of Java installed (yes, yes, I know, leave me alone) and after doing the following procedure I have Azureus working like it used to. OH! Yes, I am lazy. I have Automatix and for anyone who is time crunched or is just learning Ubuntu Automatix is a life saver. 

I am fairly sure that this does NOT install the SUN Java but I am not positive.  It turns out that, if not, it will but Java-common in and it will work.

These instructions are for Ubuntu and Synaptic.  You will have to adjust as necessary. 

If you have automatix then please do this. This will uninstall azureus.
1.  Open Automatix
2.  Click on uninstall
3.  Click on File Sharing
4.  Check on Azureus
5. Click the Start button.
Azureus is now be uninstalled.

Ok open your favorite Package Manager in my case its Synaptic.
1. Click System
2. Click Administration
3. Click on Synaptic
4. Type in your password
5. Click Search
6. Type java
7. Right click on the Java-common button, 
8. Left Click on Mark for Removal.
9. Click the Apply button. It **might** ask you to remove Azureus too, go ahead and do so.
10. Close when done.

Ok, now if you don't already have Automatix installed go do so right now.
Let me know when you are done.
Ready?  Good.

Installing Azureus.
1. Click Applications
2. Click System Tools
3. Click Automatix
4. Click Yes you agree and login as required.
5. Click the install tab.
6. Click on File sharing.
7. Click on the box for Azureus.
8. Click on the start button.

Ok, what this does is installs Azureus and Java 1.6 from the Ubuntu repositories.  For me this was all that was needed.  The same procedure could be done easily from the command line but I am not that good with it and since the folks at Automatix have done the work anyway well lets let the program do it.

BTW. Thanks to all the people who post to the forums and thanks to the folks at Automatix who are doing cool stuff too.

---

### Post by bryan986 on 2007-06-03
I am also having this problem, but on a Reiserfs partition. I am saving the torrent files to the same partition that azureus is installed on. I have installed Sun's Java, how do I make sure Azureus is using this and not something else?

---

### Post by brynjarh on 2007-06-08
> **bryan986 said:**
> I am also having this problem, but on a Reiserfs partition. I am saving the torrent files to the same partition that azureus is installed on. I have installed Sun's Java, how do I make sure Azureus is using this and not something else?

I'm having this same problem on festy, ext3, I think installing sun java will probably fix this but according to [https://help.ubuntu.com/community/AzureusHowTo](https://help.ubuntu.com/community/AzureusHowTo) you also need to tell programs to use it by doing sudo update-alternatives --config java , going to try it out and see if it helps.

---

### Post by shrikel on 2007-06-25
> **brynjarh said:**
>  you also need to tell programs to use it by doing sudo update-alternatives --config java

Thanks, brynjarh, that did it for me.  You learn something new every day. :D

---

### Post by truse on 2007-08-01
I had the same error message that you guys had.. all i had to do was to install sun`s java:
$sudo aptitude install sun-java6-plugin

After you have downloaded and installed sun`s java, you have to make the system acually USE sun`s java:
$sudo update-alternatives --config java

Here you will have a choice to use the new java versjon. weeeeeeeee you are done.

---

### Post by mr297 on 2007-08-24
> **brynjarh said:**
> you also need to tell programs to use it by doing **sudo update-alternatives --config java**

Thanks, this solved the "disk read error - NullPointerException" for me.

---

### Post by sdezeix on 2007-09-09
that works for me too!!!
thanks...:lolflag:

---

### Post by treeko11 on 2007-09-13
So, if i was to uninstall azureus and reinstall, would i have to restart my download?

---

### Post by Totzo on 2007-09-13
I realise this is probably going to annoy someone as it is not really a solution  but why not just use Deluge?

I used azureus for a while but although it is feature rich it is a pretty weighty app too.

Deluge is really simple and has all sorts of cool plugins, they even host debs on the site!

---

