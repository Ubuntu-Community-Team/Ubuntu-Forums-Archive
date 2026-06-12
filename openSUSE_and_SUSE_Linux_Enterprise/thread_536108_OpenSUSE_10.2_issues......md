---
title: "OpenSUSE 10.2 issues....."
date: 2007-08-27
forum: openSUSE and SUSE Linux Enterprise
---

### Post by ElEdwards on 2007-08-27
I've been a Ubuntu/Kubuntu user for several months now.  I tried a few others during that time (Fedora, Slack) but always came back to Ubuntu/Kubuntu.

 One of the things that impressed me about Ubuntu from the beginning is how (on both my laptop and my desktop), it just works, which in my opinion, will make the difference in folks changing from Windows to Linux.

This weekend I tried OpenSUSE 4.2 on my laptop and rain into a wall regarding my wireless PCMCIA card.  While I can see that OpenSUSE is quite robust, I became quite lost/confused in the whole 'ndiswrapper' issue regarding my wireless card..... I finally gave up, reinstalled Kubuntu and once again, everything just worked!

Perhaps it was a "forest for the trees" type of thing, but I couldn't find any clear docs or a 'howto' regarding installation of software in OpenSUSE.  Note the word 'clear'... I found some things but they all spoke in language that assumed I knew what I was reading..... as opposed to docs I find for Ubuntu/Kubuntu, which are clearly defined step-by-step instructions.

Has anyone else hit this wall with OpenSUSE?  Thanks for reading. :)

---

### Post by dca on 2007-08-27
This was the how-to I used for 10.2:
 
[http://nextgen.no-ip.org/~andrew/linux/ndiswrapper/ndiswrapperinfo.php](http://nextgen.no-ip.org/~andrew/linux/ndiswrapper/ndiswrapperinfo.php)
 
He's one of the admins over at suse forums, the link is also in his signature...

---

### Post by ElEdwards on 2007-08-27
Wow!  What a great set of docs that is!!  Thanks! :)

---

### Post by Erunno on 2007-08-27
If you're PCMCIA card works in Ubuntu out of the box then ndiswrapper shouldn't be needed at all. Either Ubuntu works because it has a newer kernel with native drivers or ships binary drivers with the CD. 

Either way, openSUSE is much more reluctant to add software to the default installation that is not free (as in speech) and Ubuntu has been criticized in the past for their willingness to ship closed source drivers / firmware in the past in order to increase their market share.

---

### Post by ElEdwards on 2007-08-27
My card is a Linksys WPC54G that has always worked right off the bat in all flavors of Ubuntu (U/Kubuntu, Mint, Mint XFCE, Mint KDE) and even Fedora. :)

---

### Post by dca on 2007-08-27
If the Linksys uses Atheros chips than I can see why it'd work out of the box in Ubuntu....
 
I had an Intel ProWireless in my old laptop, a miniPCI dealie.  That worked out of the box in Ubuntu but req'd the non-oss CD from SuSE to get the ipw2200bg firmware installed...

---

