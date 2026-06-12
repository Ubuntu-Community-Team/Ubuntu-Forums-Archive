---
title: "VMWare Server in 7.10 x86_64"
date: 2007-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by netbandit on 2007-10-30
Howdy,

I just bought new drives for my computer in anticipation  of installing 7.10 x86_64 Ubuntu on them.  formerly I was running 7.04 ok, but on smaller drives. So, I did a fresh install of 7.10, and after installing ubuntu-desktop, I started on VMWare.

Anyway, As usual I had to add the repositories to my /etc/apt/sources.list
```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```

Then I tried to install VMWare as I did in 7.04
```

apt-get update&&apt-get install vmware-server

```

However, I am not successful:
> 
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vmware-server: Depends: vmware-server-kernel-modules but it is not installable
                 Depends: libssl0.9.7 but it is not installable
E: Broken packages


I realize that VMWare Server is in the repositories, but the required packages are not.  If the required packages are going to be available soon I can wait, but if it is going to be more than a month, I might as well figure out the least BOFH way to do it.

Anyone know when it is coming out, and if not, or if its going to be a while, what is the best (in an Ubuntu sense) way to install it?

-nb

---

### Post by dabl on 2007-10-30
This is kind of a semi-answer ...

The VMWare Player in the repos, a Ver. 1.something, is still broken, AFAIK (I haven't tried it for a couple of weeks now).  But the free Player download for 64-bit Debian, which is actually a newer version (2.something), installed and works flawlessly on my 64-bit Kubuntu system.

Don't know whether this tidbit is relevant to the problems you observed, or not.

:)

---

### Post by netbandit on 2007-10-30
Thanks,

That is not a bad alternative... but unfortunately, I need to create virtual machines.  Although I might be able to create them elsewhere, but I'm not sure if going from a 32bit host to a 64bit host would hose them.  Probably not because the VMWare P2V tool works in this manner.

-nb

---

### Post by fjgaude on 2007-10-30
Well, for VMware Server, I went to there home page and downloaded binary file. Moved it to my home folder, uncompressed, moved over to the new folder created, cd'ed in a terminal to the new folder and ran the install file using ./.

Then called all the questions with simply a return, using the defaults. Moved my old vmdx folder into the new one (/var/lib/vmware, used to be vmware-server), and everything worked as before except the USBs.

I trust something will change and the USB connections will work soon.

---

### Post by netbandit on 2007-10-30
Yeah, I might try that if I don't find a viable alternative to the 'ubuntu method'.

I do worry about things like USB, networking, etc. not working, or worse, causing instability.  

Hell, i might just try this, because I want to reinstall using reiserfs or xfs anyway, and at this point I have nothing invested in this system.
-nb

---

### Post by netbandit on 2007-11-01
Since vmware-server is in the repositories, could I bypass the dependencies and just install with apt-get?

```
apt-get install vmware-server -f
```
or
```
apt-get install vmware-server --nodeps
```
or
```
apt-get install vmware-server --ignore-missing
```

-nb

---

### Post by Didjit on 2007-11-01
Sidebar, have you looked at Virturalbox? [http://www.virtualbox.org/](http://www.virtualbox.org/)

I was an avid VMWare lover until I took Virturalbox for a spin. On my system, it runs much faster then VMWare ever did.

Didjit

---

### Post by netbandit on 2007-11-01
I haven't looked at virtualbox specifically.  My original goal was to migrate to Xen (eventually).  What I really want to do is be able to move virtual guests between hosts, without powering off the guest.  I know vmware can do that in their virtual infrastructure product (requiring vmotion), and it is my understanding that Xen can do that as well.  I'm not sure if Xen is all that free anymore as they've been bought by Citrix... so, I'm in a holding pattern with VMWare unless I find something else.  VirtualBox might be what I am looking for tho.  I guess I need to read up.

thanks for the suggestion!
-nb

---

### Post by Chuckels550 on 2007-11-02
> Anyway, As usual I had to add the repositories to my /etc/apt/sources.list

Code:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

If you are installing into Ubuntu 7.10 Gutsy Gibbon, is this not the wrong commericial source repository?

---

### Post by netbandit on 2007-11-02
> If you are installing into Ubuntu 7.10 Gutsy Gibbon, is this not the wrong commericial source repository?

If there is a new repository for 7.10 I'd like to know about it, however according to the following article, this is the correct repository for 7.04:

[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

Regarding VirtualBox, I was well impressed with it, but it is lacking a couple features that are going to make it only a temporary solution for now:
-RAM support for guests over 2GB
-USB support
-Multiple virtual CPU's (although I didn't check)
-I couldn't get bridged networking to work

-nb

---

### Post by dirkmegabyte on 2007-11-04
Here is what I did to get VMware Server running on 7.10 Gutsy x86_64....the only thing that doesn't work is bridged networking which I haven't figured out yet:

1. Install latest version

2. Grab patch:
wget [http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz](http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz)

3. Extract out the patch  to any directory, then run: runme.pl

4. Rerun ./vmware-install.pl  (this is prolly overkill..could've just run /usr/bin/vmware-config.pl)

5. To get httpd.vmware (vmware-mui-distrib) working, edit the /etc/init.d/httpd.vmware script as follows:
 
comment out the vmware_exec and split it into two commands so it now looks exactly like this:

# See how we were called.
case "$1" in
start)
# vmware_exec "Starting httpd.vmware:" vmware_start_httpd
echo "Starting httpd.vmware:"
vmware_start_httpd
;;
stop)
# vmware_exec "Shutting down http.vmware: " vmware_stop_httpd
echo "Shutting down http.vmware: "
vmware_stop_httpd
;;

Good luck!

---

### Post by Didjit on 2007-11-04
> **netbandit said:**
> 
Regarding VirtualBox, I was well impressed with it, but it is lacking a couple features that are going to make it only a temporary solution for now:
-RAM support for guests over 2GB
-USB support
-Multiple virtual CPU's (although I didn't check)
-I couldn't get bridged networking to work

-nb

I never ran into USB issues? But I use Winblows as the guest. You can always go here a dig around for support.  [http://forums.virtualbox.org/](http://forums.virtualbox.org/)

Didjit

---

### Post by netbandit on 2007-11-04
> I never ran into USB issues? But I use Winblows as the guest.

Hmm.

I am also using Windows as the guest.

Are you using VirtualBox-OSE or the commercial version?  I'm sure that USB Keyboards and Mice are not a problem, but I don't see any place in the virtual system config that allows USB.  I also tried plugging in my USB Flash Drive while inside the virtual system, and it did not pick it up.

Also, USB is one of the things that is only supported in the commercial version from what I see on this page:
[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

-nb

---

### Post by Didjit on 2007-11-04
> **netbandit said:**
> 
Also, USB is one of the things that is only supported in the commercial version from what I see on this page:
[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

-nb
I'm using the commercial version (which is free for personal use). There is a setting for USB device filters.

Didjit

---

### Post by netbandit on 2007-11-04
> I'm using the commercial version (which is free for personal use). There is a setting for USB device filters.

Cool, Did you find an apt repository for that or did you install it the hard way?

-nb

---

### Post by Didjit on 2007-11-04
> **netbandit said:**
> Cool, Did you find an apt repository for that or did you install it the hard way?

-nb

There is a deb for it and a repo. Look at [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) under Debian systems.

Didjit

---

