---
title: "I am considering moving from 8.10 to 8.04"
date: 2008-12-30
forum: x86 64-bit Users
---

### Post by Robster2 on 2008-12-30
I have been using 8.04 from a 32 bit desktop machine for some time and am very happy with it.

I bought a new laptop Satellite Toshiba L300 AMD 64x2 and installed Ubuntu 8.10.  64 as a dual boot.

I have experienced the following problems.

1.  Poweroff/ Shutdown does not work.
    Poweroff hangs with a "_" on a black screen
    in a terminal shutdown -P now
    I get APICD : Exiting  and it hangs.

2.  On odd occasions the Laptop will suddenly simply power for no reason

3.  Cannot restore activity after Hibernate.

4.  I have not been able to get new features such as the create USB start up disk I have not been able to get it to work once

I have run Hardy Hereon 32 bit from a live CD shutdown /power off worked normally.

---

### Post by oldos2er on 2008-12-30
Have you installed all the updates for 8.10? I had the same situation with 8.10 hanging on shutdown, but updating seems to have fixed it.

---

### Post by -=-+ w1r1zu +-=- on 2008-12-30
I have installed all the updates for Ubuntu Intrepid 8.10 but I don't have any problems at all even on Shut Down.

I'm just annoyed whenever I boot my Ubuntu, so the Ubuntu logo and progresss bar loads right? Then comes all this error messages about the USB.

it's got like this format [Date Here] SOME WIERD TEXT : error -32

something like that.

then some loading messages and OK status at the end of the line.

those things spawn everytime I load ubuntu and same on shutting down.

---

### Post by Robster2 on 2008-12-30
I have clicked on System -> Administration -> Update Manager.

"Your system is up to date  System has been updated 13 days ago"

---

### Post by oldos2er on 2008-12-31
> **Robster2 said:**
> I have clicked on System -> Administration -> Update Manager.

"Your system is up to date  System has been updated 13 days ago"

 You might want to check for new updates then.

---

### Post by caeroe on 2008-12-31
I cannot even get into Hibernate or Suspend since the 8.10 upgrade.  My hardware didn't change, I initially was using the same drivers for Nvidia.  I've since been using 180.x beta drivers now.  That didn't fix it either.  All I get is a blinking cursor and I'm forced to power down.  I never had that with 8.04.

No one ever, ever, answers my questions in IRC or here.  I've been trying to figure out subpar Flash performance and the above issue.

This is just entirely frustrating that the simple things do not work on this OS.  On my notebook I have to worry every time there's a kernel header update, for fear my wireless would be broken again (happened twice in the past couple months).

---

### Post by Robster2 on 2009-01-01
I forced an update (the update manger used prompt me if there were any new files)  I got the error message below.


The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://www.bashterritory.com](http://www.bashterritory.com)  Release: The following signatures were invalid: NODATA 1 NODATA 2Failed to fetch [http://www.bashterritory.com/pytube/releases/Packages.bz2](http://www.bashterritory.com/pytube/releases/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by dcstar on 2009-01-01
> **Robster2 said:**
> I forced an update (the update manger used prompt me if there were any new files)  I got the error message below.


The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://www.bashterritory.com](http://www.bashterritory.com)  Release: The following signatures were invalid: NODATA 1 NODATA 2Failed to fetch [http://www.bashterritory.com/pytube/releases/Packages.bz2](http://www.bashterritory.com/pytube/releases/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.

That is a problem with some dodgy 3rd party repository you have in your system, and has nothing to do with the issue that this thread is about.

It will not stop any updates from the working repositories.

---

### Post by Ehtetur on 2009-01-01
> **Robster2 said:**
> I have been using 8.04 from a 32 bit desktop machine for some time and **am very happy with it**.

I think you may have already answered your own question about upgrading or not... tho you may want to try the the x64_86 version of 8.0.4 :twisted:

BTW, that's what I'm running and have had no problems - that is after the +200 updates completed after install.

---

### Post by Sef on 2009-01-03
> dcstar 	 		**Re: I am considering moving from 8.10 to 8.04**
 		 	Quote:
 	 	 		 			 				 					Originally Posted by **Robster2** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=6472145#post6472145") 				
 				[I]I forced an update (the update manger used prompt me if there were any new files)  I got the error message below.


The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://www.bashterritory.com]("http://www.bashterritory.com/")  Release: The following signatures were invalid: NODATA 1 NODATA 2Failed to fetch [http://www.bashterritory.com/pytube/...s/Packages.bz2]("http://www.bashterritory.com/pytube/releases/Packages.bz2")  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.[/I]
 			 		 	 	 
That is a problem with some dodgy 3rd party repository you have in your system, and has nothing to do with the issue that this thread is about.

It will not stop any updates from the working repositories. 	

Remove those repositories and see what happens.   I once had an update problem resolve by removing some bad repositories.

---

### Post by cacycleworks on 2009-01-05
When I have issues, I try different ways...

Like for 8.04, I install ubuntu desktop x86_64 and then apt-get install kubuntu-desktop to get KDE. I always have /home on its own partition, which allows me to reinstall ubuntu on a whim. I tar-gz my home dir and install away.

My Dell D630 core duo intel laptop doesn't like the ubuntu live cd (won't boot from it) but does ok with the alternative disc with the command line installer.

I recently tried 8.10 and ended up going back to 8.04. 8.10 and KDE4 didn't agree with me, so I'm back to Hardy now. :-)

Chris

---

