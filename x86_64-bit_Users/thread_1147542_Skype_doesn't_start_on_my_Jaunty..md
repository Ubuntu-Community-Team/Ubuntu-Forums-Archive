---
title: "Skype doesn't start on my Jaunty."
date: 2009-05-03
forum: x86 64-bit Users
---

### Post by laplace/d on 2009-05-03
I just installed skype by forcing the architecture to amd64. it asked me to install some libraries and the installation went without problems, but when i try to start it i get the following.

Could not launch 'Skype'
Failed to execute child process "skype" (No such file or directory)

---

### Post by Yellow Pasque on 2009-05-03
Where did you get skype from (medibunt?) and what do you mean that you forced the architecture to amd64?
[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

---

### Post by jespdj on 2009-05-04
The easiest way to install Skype is from the [Medibuntu repository](http://www.medibuntu.org). If you have a 64-bit system, this will automatically install the necessary 32-bit libraries (Skype is a 32-bit program).

---

### Post by laplace/d on 2009-05-04
> **Temüjin said:**
> Where did you get skype from (medibunt?) and what do you mean that you forced the architecture to amd64?
[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

it means i typed the following in the shell
sudo dpkg --force-architecture -i skype-debian_2.0.0.72-1_i386.deb

i got the installation file from skype.com

---

### Post by beetlejuice321 on 2009-05-17
I am running Jaunty (9.04) 64bit version.  

Typing "sudo dpkg --force-architecture -i skype-debian_2.0.0.72-1_i386.deb" with the downloaded file from the Skype website work for me.

Installation is very fast. Did you look in your "Internet" menu on Ubuntu?  It should be there and launch for you successfully.

If you get some missing dependency errors.  Just install those dependencies through "Synaptic Package Manager" first (under the System - Administration menu).

The program seems fine and my webcam is detected and working successfully.  I just have yet to test and actual Skype call.

But damn, I just wish Skype would get it together and finally release a new 64bit Linux client!  Including updating the version of their Linux client altogether!

---

### Post by RemoteUser on 2009-05-19
For Skype on AMD64, go here.  Anything else is either wrong or the hard way.
[http://www.madox.net/blog/2009/04/24/ubuntu-skype904-jaunty-jackalope-amd64-64-bit/](http://www.madox.net/blog/2009/04/24/ubuntu-skype904-jaunty-jackalope-amd64-64-bit/)

---

### Post by drkitty on 2009-06-11
I'm also having difficulty with skype on ubuntu jaunty 64 bit machine. I'd installed it for hardy from medibuntu, and it was fine. After upgrading to jaunty it was no longer working. I **completely removed** skype and tried reinstalling from the jaunty medibuntu repository. I get a launcher in the menu, but it doesn't actually launch. I tried "usr/bin/skype" and get this error: "/usr/bin/skype.real: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory" - I'd tried various guides:[http://ubuntuguide.org/wiki/Ubuntu:Jaunty#How_to_install_Skype_on_a_64-bit_system](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#How_to_install_Skype_on_a_64-bit_system), [http://ubuntuforums.org/showthread.php?t=1127221](http://ubuntuforums.org/showthread.php?t=1127221) etc -  no joy.  Any suggestions?

---

### Post by merlinus on 2009-06-11
You can get the 64-bit version from the skype website, although there are no apparent links to it.  Search for:

skype_ubuntu-2.0.0.72-1_amd64.deb

---

### Post by Yellow Pasque on 2009-06-11
drkitty, do you have lib32asound2 installed?

---

### Post by BugBuster on 2009-06-20
> **merlinus said:**
> You can get the 64-bit version from the skype website, although there are no apparent links to it.  Search for:

skype_ubuntu-2.0.0.72-1_amd64.deb


Well its anything but a 64-bit version..
I downloaded the same and when I tried to install it using

sudo dpkg -i skype_ubuntu-2.0.0.72-1_amd64.deb

it asks for the ia32-libs package as dependency

So how does this become a 64-bit version?
However would like to add that it works fine after doing all the dependencies though on my 64 bit Jaunty.

---

