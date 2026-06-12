---
title: "New Install"
date: 2007-03-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tuxaby on 2007-03-29
I see from some of the  posts I read here that using 64 bit Ubuntu can be fun.  I just installed 6.01 LTS 64 bit on my laptop.  Tried Mandrake some years back and have tried Suse 9.2 Pro and 10.1 recently so I have a little experience with Linux.  I need to install a Linuxant driver for my modem and the only one available needs to be built from a tar.gz. .  I know nothing about this so I started with the Debian Maintainers Guide and found I'm in a little deep.  It tells me I need several packages installed to do this.  How do I find if any or all are already installed and if not where can I get them ?  I learned to deal with rpms  but this looks like this will have a longer learning curve.  I'm not a tech, just a old machinist who wants to learn everything Linux.  Is it possible I'm in over my head?    Thanks, Lee

---

### Post by Kilz on 2007-03-29
> **Tuxaby said:**
> I see from some of the  posts I read here that using 64 bit Ubuntu can be fun.  I just installed 6.01 LTS 64 bit on my laptop.  Tried Mandrake some years back and have tried Suse 9.2 Pro and 10.1 recently so I have a little experience with Linux.  I need to install a Linuxant driver for my modem and the only one available needs to be built from a tar.gz. .  I know nothing about this so I started with the Debian Maintainers Guide and found I'm in a little deep.  It tells me I need several packages installed to do this.  How do I find if any or all are already installed and if not where can I get them ?  I learned to deal with rpms  but this looks like this will have a longer learning curve.  I'm not a tech, just a old machinist who wants to learn everything Linux.  Is it possible I'm in over my head?    Thanks, Lee

To find out if a package is installed, or to install it the easy way,[ use synaptic.]("http://www.monkeyblog.org/ubuntu/installing/#installing_with_synaptic") No matter what version of make of linux, eventualy you learn how to compile code. You are just learning that now. The site I linked to above also has info on compiling and other forms applications come in. [Take a look if you want to.]("http://www.monkeyblog.org/ubuntu/installing/")

---

### Post by Tuxaby on 2007-03-29
Thanks Kilz! The links are great.  Thorough and easy to follow.  Began by checking for build-essential and find it is not in the initial installation.    Searched the Ubuntu site for build-essential and came up empty.  Can I access the online repositories from a windows pc  to get the necessary packages until I can set up online access and if so where do I go?  Lee

---

### Post by Kilz on 2007-03-29
> **Tuxaby said:**
> Thanks Kilz! The links are great.  Thorough and easy to follow.  Began by checking for build-essential and find it is not in the initial installation.    Searched the Ubuntu site for build-essential and came up empty.  Can I access the online repositories from a windows pc  to get the necessary packages until I can set up online access and if so where do I go?  Lee

You should be able to install build-essential with synaptic. Synaptic is configured to get packages from the repositories for you. The reason its recommended is that it will solve all dependencies. With build-essential this is important because it installs other packages, it isnt an application in itself, but a list of packages that are essential to build applications. [You can go here to get packages]("http://packages.ubuntu.com/") Here is [the build-essential page]("http://packages.ubuntu.com/dapper/devel/build-essential") just make sure to get all the required packages.

---

### Post by Tuxaby on 2007-03-29
This is why I think forums are great.  Great people, fast replys and on the mark help.  Thanks Kilz, lets see how far I get without any more help. Will post back with results.  Many Thanks, Lee

---

### Post by Tuxaby on 2007-03-29
was so focused on getting things right I did not notice the thread I was on, so I posted this to the wrong thread "
Reload this Page Downloading Repositories Without...(Help Please)"  Tried to delete and repost here but could not find means to do so.  Meant to post "Downloaded alien for dapper and tried to open in synaptic package manager in "file/add downloaded packages" and found it unavailable. Tried to open alien directly and got [COLOR="Red"]"error: dependency is not satisfiable: debhelper"[/COLOR] What do I do now? Lee

---

### Post by Kilz on 2007-03-29
You are running into a problem that used to be called dependency hell. Before we had applications like synaptic and apt to download and install the dependencies we had to do it manually. Sadly some dependencies will have dependencies and so on and on.
The reason you are running into this problem is that you may not have internet access. Without access synaptic and apt(the command line application synaptic is a front end for) wont work. So you have to manually download all the applications and install them, installing the dependencies first.

---

### Post by Tuxaby on 2007-03-29
how do I check the dependancies?  Lee

---

### Post by Kilz on 2007-03-29
> **Tuxaby said:**
> how do I check the dependancies?  Lee

Well take a look at [the build essential page]("http://packages.ubuntu.com/dapper/devel/build-essential"). You see all the packages with red dots beside them? Those are dependencies of the package. If you click on them, it will being up their page, which might also have dependencies on it.

---

### Post by Tuxaby on 2007-03-29
Ok, then, since what I am trying to do is get my modem up and running and need all of the packages I find I need.  Is there a DVD available I can order with most or even all of the packages available for Ubuntu.  The only driver I can find for my modem comes in a tar.gz package and needs to be converted so I can use it.  It is becoming  very discouraging trying to do this.  If I can ever get the modem up and running then I feel the rest of  whatever problems I run into can be easily resolved.  Lee

---

### Post by Kilz on 2007-03-29
> **Tuxaby said:**
> Ok, then, since what I am trying to do is get my modem up and running and need all of the packages I find I need.  Is there a DVD available I can order with most or even all of the packages available for Ubuntu.  The only driver I can find for my modem comes in a tar.gz package and needs to be converted so I can use it.  It is becoming  very discouraging trying to do this.  If I can ever get the modem up and running then I feel the rest of  whatever problems I run into can be easily resolved.  Lee

Not that I know of, but I will offer to try and compile the driver for you if you give me a link to the tar.gz.

---

### Post by nss0000 on 2007-03-29
BigT:

GOTO the UBUNTU home_page:   [http://www.ubuntu.com/](http://www.ubuntu.com/)

Request free delivery of the 3-pack ( Camel straights, filters, lights ... ) .. er,  U_6.06x64, U_6.20x32, U_Mac .

They say delivery of CDs  within 6-weeks ... I got mine in a couple days. Comes with a lb of Belgin chocolate. No cost to you for anything, except the 6000-hours opportunity cost to drain this gravel onto the roadbed.

nss
************

---

### Post by Tuxaby on 2007-03-30
Well folks I'm sending this from my 32 bit desktop computer via its Ubuntu OS.  Got it working this morning.  Finally downloaded all dependancies for my laptop, the subject of this thread, transfered files via a fat 32 partition on it and began installing.
 when I got to ,I think it was called imagic, and started installing it I got an error message and then was told I had a broken package.  Went to package manager  and the package "file" was broken tried to fix it with  package manager  and was not able.  I work weekends out of town which begins tonight, so will have to drop this till I get back.  At least now I can compile the driver on this computer and then network  it to the laptop.  I'm determined to get the full 64 bit potential from my laptop.  I want to solve my 64 bit problems on it before I build my new 64 bit dual core AMD processor desktop.  This one will be built around Linux.  By the way, I also have Kubuntu coming soon  for these two computers and am thinking I will switch to it as I am much more familiar with KDE  than Gnome.  Thanks for all the help, see you sometime next week.  Thanks again, Lee

PS  Kilz, the offer to compile the driver was above the call to duty and is highly appreciated.  If I am unsuccessful doing this I may still take you up on the offer.  Many thanks!!!!

---

### Post by Kilz on 2007-03-30
> **Tuxaby said:**
> 
PS  Kilz, the offer to compile the driver was above the call to duty and is highly appreciated.  If I am unsuccessful doing this I may still take you up on the offer.  Many thanks!!!!

Not a problem , it seemed like a circular problem, you couldnt compile the driver because you couldnt get the packages, you couldnt get the packages, because you didnt have the driver.
One of the best parts about Ubuntu is that most people try and help other Ubuntu users. Compiling the driver may not help just you, but other people with the same problem. If you manage to get it compiled please post it here so others can get it. If you cant, the offer remains open.

---

### Post by wesley_of_course on 2007-03-30
Wesley here ;

   Kilz  your alright in my book !

                      Many Thanks ! ,  may God bless You .

---

### Post by Kilz on 2007-03-30
> **wesley_of_course said:**
> Wesley here ;

   Kilz  your alright in my book !

                      Many Thanks ! ,  may God bless You .

Thanks, 
great verse, and great chapter.

---

### Post by Tuxaby on 2007-04-03
Wanted to let everyone that  my modem problem is no more.  Finally bit the bullet and had high speed internet provided by a locally owned wireless provider installed.  Once I was up and running I switched to Ubuntu and activated my network card and was on the internet instantly.   That was just a couple of hours ago.  I have already run all updates ad installed several packages I wanted to try.  This has got to be the most user friendly Linux I have tried to date. Thanks for all the help trying to get my dialup working.  Still have networking my computers and setting up wireless to learn about.  For  now  am going to do a little surfing and enjoy getting around the net at a decent pace. Peace and Prosperity to All, Lee

---

