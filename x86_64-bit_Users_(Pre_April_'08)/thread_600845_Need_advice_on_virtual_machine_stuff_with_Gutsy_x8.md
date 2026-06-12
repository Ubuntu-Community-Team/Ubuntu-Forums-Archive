---
title: "Need advice on virtual machine stuff with Gutsy x86 64-bit"
date: 2007-11-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by timzak on 2007-11-02
I just installed Gutsy 64-bit and am interested in running Win2k through a virtual machine.  I have limited experience in Linux (been using Ubuntu since Feisty was released in April), zero experience with any 64-bit OSes, and zero experience with any virtualization software.

I have one main app I want to run in Win2k:  MS Money 2006.  I also use Win2k to backup DVD movies so my 3-year-old scratches up the copy and not the original.  I know it is possible to backup DVDs in Ubuntu, but I find it (at the moment) more convenient to do so in Win2k via DVDFabDecrypter and Nero.  I'm always looking for ways to shed off my dependence in Windows, but these are two areas that have forced me to remain in a dual-boot scenario.

I'd like to try running Win2k in a virtual machine in Gutsy 64bit.  I don't hear a lot about virutalizing in a 64-bit environment, so I wanted to ask if there are any issues I should be aware of before I dive in, and if the kind people here have any recommendations for which virtualization software will fit my bill.  I'm pretty saavy, but I have little experience in Linux, and little time to devote to tinkering, so I'd prefer the simplest route.  And if it can't be done, I'd like to know that to so I don't waste my time.  :)

Thanks so much in advance.

Tim

---

### Post by FG123 on 2007-11-02
I run Vista using the 64-bit version of VMware workstation. Works absolutely flawlessly, no errors or troubles. Only thing to remember - you need to download the 64-bit version of whatever virtualization software you want to use, otherwise you may have issues and/or won't be utilizing the full capabilities of your system.

For example: [http://www.virtualbox.org/debian/pool/non-free/v/virtualbox/](http://www.virtualbox.org/debian/pool/non-free/v/virtualbox/)

You can download the free (as in beer) version of VirtualBox, another good virtualization tool, for 64-bit without any issues, so long as you specifically install the **virtualbox_1.5.2-25433_Ubuntu_gutsy_amd64.deb** package. In this case the kernel drivers will match the 64-bit architecture of your system.

---

### Post by bdamon on 2007-11-02
I have run Win2k with Virtualbox on Gutsy 64 bit with no issues so far. I am not sure about specifics as to what you want to do in a Win2k vm but you should have no problems using Virtualbox on 64bit. I used the 64bit Virtualbox deb provided from their site.

---

### Post by netbandit on 2007-11-02
VMWare is great, and it's fit and finish is excelent as well.  VirtualBox is good, and for your purposes might work, except for burning from inside the virtual system.

Longterm, I hope to migrate to Xen, as it supposedly has the capability to move running guest systems between hosts (but I do not know about this for sure).

I hope you can find a suitable Burning application for backing up your DVD's in Linux.  I would expect that once you are able to do that you will be in good shape.

Additionally, you might be able to run MS Money 2006 in Wine.... completely eliminating your need for virtualization.

-nb

---

### Post by timzak on 2007-11-02
Thanks so much for the quick responses.

It sounds like I need to manually download and install any 64-bit versions of VM software?  Do they not offer a version I can install through Synaptic?

netbandit,

Could you expand on your comment about burning from inside a virtual system?  Does it not work in any VM software, or is it a limitation of VirtualBox?

Thanks for the tip on Wine.  I checked a compatibility list at one time and almost none of the Money versions work through Wine (I think a couple of the older versions like 2002 do work).  So VM or dual-boot are my only options.

---

### Post by FG123 on 2007-11-02
> **timzak said:**
> It sounds like I need to manually download and install any 64-bit versions of VM software?  Do they not offer a version I can install through Synaptic?
Starting with Gutsy, they do.

Go into Synaptic and do a search for **virtualbox**, you'll find an entry for **virtualbox-ose** - the open source edition of the program. It will run fine so long as you don't have any requirement for accessing USB devices in the virtual machine. If you do, you'll need to go to the link I provided and download the .deb file for the non-open source version, which provides the extra functionality. Deb files are pretty easy to install though, you just double-click them once they're download, click Install and the rest is automated.

---

### Post by brianbarry on 2007-11-03
There are a couple of programs in linux used to "backup" DVDs, k9copy and  dvd:rip, they both work very well.  The only problem is the need for decss, I use automatix to solve this.

Brian

---

### Post by ViRMiN on 2007-11-03
libdvdcss2 is in the Medibuntu repository.

---

### Post by snkmad on 2007-11-04
I plan to install vbox 1.52 adm64 here too.
Do i need to do any kernel modification?
Ive heard i have to do something with kernel module.
Sorry im new to kernel on linux.

---

### Post by vgrisham on 2007-11-04
> **timzak said:**
> I just installed Gutsy 64-bit and am interested in running Win2k through a virtual machine.  I have limited experience in Linux (been using Ubuntu since Feisty was released in April), zero experience with any 64-bit OSes, and zero experience with any virtualization software.

I have one main app I want to run in Win2k:  MS Money 2006.  I also use Win2k to backup DVD movies so my 3-year-old scratches up the copy and not the original.  I know it is possible to backup DVDs in Ubuntu, but I find it (at the moment) more convenient to do so in Win2k via DVDFabDecrypter and Nero.  I'm always looking for ways to shed off my dependence in Windows, but these are two areas that have forced me to remain in a dual-boot scenario.

I'd like to try running Win2k in a virtual machine in Gutsy 64bit.  I don't hear a lot about virutalizing in a 64-bit environment, so I wanted to ask if there are any issues I should be aware of before I dive in, and if the kind people here have any recommendations for which virtualization software will fit my bill.  I'm pretty saavy, but I have little experience in Linux, and little time to devote to tinkering, so I'd prefer the simplest route.  And if it can't be done, I'd like to know that to so I don't waste my time.  :)

Thanks so much in advance.

Tim

Tim,

Hi. I realize you're using Microsoft Money right now, but I want to encourage you to try kMyMoney. I switched from Money 2005 last year when I dumped Windows and I love it. Also, try pybackpack for your backup program. I just started using it and I like it a lot.

Both programs are available from the repos, and neither require any command line tweaking.

Good Luck,
Vaughn

---

### Post by netbandit on 2007-11-04
> Could you expand on your comment about burning from inside a virtual system? Does it not work in any VM software, or is it a limitation of VirtualBox?

According to the VirtualBox site, this feature is experimental:
[http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)
see section 12.12

-nb

---

### Post by timzak on 2007-11-04
Thanks, Vaughn.  I've actually looked at a few financial programs that look nice.  My problem is the time it would take to migrate to a new program.  I've tried importing my Money files into a couple of other programs and it never works out cleanly.  I'd basically have to either start from scratch or manually input a couple years worth of receipts!  I wish I had more time, this would be an easy decision if that were the case.

The DVD backups aren't as important.  It's not often we buy a new movie, and my wife and I generally don't watch the same movie more than once, but our son loves his Disney movies, so the discs take a beating between the home and the car players.  I like the ease of DVDFabDecryptor and it's updated often so it works with most of the latest movies.  But I'll try out pybackback (I'd never heard of it) and see how it works.

Thanks again,
Tim

---

### Post by vgrisham on 2007-11-05
> **timzak said:**
> Thanks, Vaughn.  I've actually looked at a few financial programs that look nice.  My problem is the time it would take to migrate to a new program.  I've tried importing my Money files into a couple of other programs and it never works out cleanly.  I'd basically have to either start from scratch or manually input a couple years worth of receipts!  I wish I had more time, this would be an easy decision if that were the case.

The DVD backups aren't as important.  It's not often we buy a new movie, and my wife and I generally don't watch the same movie more than once, but our son loves his Disney movies, so the discs take a beating between the home and the car players.  I like the ease of DVDFabDecryptor and it's updated often so it works with most of the latest movies.  But I'll try out pybackback (I'd never heard of it) and see how it works.

Thanks again,
Tim]

Sorry Tim, I misunderstood. Pybackback is for backing up your data to filesystems or removable media. For backing up DVD's, you'll want k9copy. It beats any Windows DVD duplication program hands down (at least the ones I tried before switching). 

As for converting, kmymoney will import QIF files, so you might give it a shot. I went ahead and started from scratch only to find out later that it is possible to convert. They have a great user e-mail list. Visit [here]("http://kmymoney2.sourceforge.net/index-gen.html") and sign up for the user list; there, you can ask the developers anything and they will respond within promptly to your requests.

---

