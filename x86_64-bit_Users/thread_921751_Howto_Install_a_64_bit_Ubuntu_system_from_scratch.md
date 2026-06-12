---
title: "Howto: Install a 64 bit Ubuntu system from scratch"
date: 2008-09-16
forum: x86 64-bit Users
---

### Post by mpve on 2008-09-16
Hi All,

As a, not so newbie, Linux user with a few years experience using AIX I thought it was nice to pay the Linux community back for the wonderfull software they produced. Yes, I am a Linux fan!! So what is the payback?

I am going to install a full 64 bit Ubuntu system on my home PC. I got an extra disk and swapped it in. And as this is a fun and learning thing I decided to go for a commandline version only for starters and then build up my system step by step until I can get rid of my Vista installment.

You can expect me to update this thread every time I made a new step and tested it. It is meant to be as a guideline for doing things like this. I will add references to problem resolutions for problems I might encounter. It will not be a complete newbie install guide though. I will make things in short so that a user with a little Linux experience will be able to copy what I have done (and hey, which newbie user starts by installing a commandline system only ;-)?).

So my first step:
[LIST]
[1]Downloaded the Ubuntu 64 bit alternate CD (the live CD does not give the opportunity to install a command line system only)
[/LIST]
[LIST]
[2]Removed the SATA cables from my other disks, started from the Ubuntu CD and installed a commandline system (15 minutes will do for this)
[/LIST]
[LIST]
[3]From the command line:
  [a]sudo apt-get update
  [b]sudo apt-get upgrade
  [c]sudo apt-get install
  [d]sudo apt-get autoclean
  [e]These steps will update your newly installed system to the latest versions of all installed files
[/LIST]

Next steps I took were to install a GUI and get it to work with a desktop environment. I could not find 64 bit version of X11 and a 64 bit display manager so I choose to install the usual X11 and GDM. 
From the command line:
sudo apt-get install xorg       [will install X11]
sudo apt-get install gdm        [will install the Gnome Display Manager]
sudo apt-get install gnome-core [will install the core Gnome desktop environment without any programs added]

----I choose to install the Gnome core version as I want to choose every program myself as a deliberate decision. The core version installs the Gnome desktop but NO additional programs----

To be continued

---

