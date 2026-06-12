---
title: "Where are Wine 1.7.x Debian Archives and How are they manually installed?"
date: 2014-07-08
forum: Wine
---

### Post by Nistegmos on 2014-07-08
hello,

I am currently running Ubuntu Studio v14.04 LTS and it comes with Wine v1.6.2.  I would like to update Wine to v1.7.x since it now has better realtime support.  This is important and relevant to me because I use Wine to run Reaper and FL Studio, which are digital audio workstation programs requiring better management of resources to prevent buffer underruns (or xruns, as people call them in Linux) to and from any audio interface.  I am already having some limited success with Reaper on Wine v1.6.2 but the newer version of Wine has been specifically upgraded for the purposes of handling digital audio and VSTi virtual instruments.  

My main computer doesn't have any internet access, and won't ever; it's too expensive in my area.  I rely upon downloading from a laptop at a public library during weekdays.  

When Debian archives are available, I'm able to download and install those.  I tried to install some Debian archives of the new Wine from the KX Studio Repository on SourceForge, but both i386 files, one large and one small failed to install due to some vague message about unresolveable dependencies.  If the Debian archives were just made available in a format appropriate for Ubuntu Studio, I think it would be a better solution, since KX Studio is a different distro and it has it's own issues.  (I tried it and didn't like it; I prefer Ubuntu Studio).  

Please let me know of somehow I can update my offline Digital Audio Workstation computer with the newest Wine with the RealTime patch, and/or perhaps a better location to try and download them from.  My computer is an HP dc5800 Core2Duo, from around 2008 I think.  It has an Intel dual core CPU.  

Thanks in advance.

---

### Post by patsev-anton on 2014-07-12
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.7

---

### Post by Nistegmos on 2014-07-15
yes, i already knew that about the sudo apt-get stuff.  But I mentioned two or three times in my main post that my computer is NOT CONNECTED TO THE INTERNET.  So that will not work.  Please re-read what I wrote.  I need an offline install.

---

### Post by R33D3M33R on 2014-07-27
Download files here: [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/)

---

### Post by Nistegmos on 2014-07-29
> **R33D3M33R said:**
> Download files here: [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/)

Hey thanks, Redeemer.  Those actually look promising.  The other sites I had looked at didn't seem to have those listings.  I'm downloading from the "Trusty" folder right now.  I wasn't sure which version I was supposed to get, so I chose both of two different folders.  Hopefully one of them will work.  I had been discouraged for a while because I had read that the dependency resolving for Wine packages is really difficult and not even really worth trying to do manually.  But maybe this will work.  Peace. 

EDIT: didn't work :-( ...files were download scripts only.

---

### Post by Nistegmos on 2014-07-31
Well the linked files turned out to be just filed with download scripts and were not the actual files.  So I have given up for now.  If anybody else knows a working solution for an offline install, please post.

---

