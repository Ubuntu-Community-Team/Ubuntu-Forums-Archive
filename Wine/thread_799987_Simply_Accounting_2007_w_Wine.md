---
title: "Simply Accounting 2007 w/ Wine"
date: 2008-05-19
forum: Wine
---

### Post by angloman on 2008-05-19
Hi all,

So I tried installing Simply Accounting Basic 2007 with wine and it installed fine. The program loads to the point that lets me choose which file / database I want to load.

Whenever I try to load an existing database or create a new one, simply says either it can't open the file or an error occurred while trying to create a new one. This is the readout I get from the terminal.

```
err:ole:CoGetClassObject class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:CoGetClassObject class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:create_server class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:CoGetClassObject no class object {00000514-0000-0010-8000-00aa006d2ea4} could be created for context 0x7

```

I'm running Ubuntu 8.04 AMD64 on a Core 2 Quad. I have the most up to date version of wine I believe. I tried installing as myself and as root and both ways give me the same error. Any suggestions would be great!

---

### Post by edsshop on 2008-08-11
I had a similar problem. Everything is fine until I try to import my backup files from my old Windows installation. Nothing happens but my poor little CPU damn near kills itself trying. I tried installing a few other Windows apps and frankly, none worked very well. I unintalled Wine. Good riddance! 

edsshop

---

### Post by qwertymn on 2008-08-13
err:ole:CoGetClassObject class {00000514-0000-0010-8000-00aa006d2ea4} not registered


looks like it looks for mdac

try this:

wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks) && sh winetricks mdac28

---

### Post by Ceyx on 2008-11-11
Hello, and thanks for your recent post re: Simply Accounting 2007.  I ran the code in terminal and now I get an error message " error in Visual C++ Runtime library.

Any ideas ?

Regards

---

### Post by Ceyx on 2008-11-13
Update:

I got Simply Accounting 2007 to run perfectly Ubuntu 8.10 with Wine.  In short:

Installed Wine.
Installed and ran Winetricks ( [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks) )
In Winetricks selected Win 98 environment and mdac25.

Installed Simply and updates.

Simply Accounting ran just as it does in Windoze !

I am also working on Quickbooks.  I do not expect it to be any harder.

Hope this is of some help.....

---

### Post by Chris Ahern on 2009-10-21
I ran into exactly the same problems posted above.  It installed fine but I get a 'Microsoft Visual C++ Runtime Library' error when attempting to open a Company.  This error appears as a window popup also stating 'abnormal program termination'.  

I tried the various options, e.g. run as Win 95, etc. but not change. 

I was also able to restore a backup (at least is appears to have worked) but it's unable to read the SBD/SDW files which were generated from the restore, stating the C++ Runtime error as above.

The messages printed on the terminal, when clicking on the 'Open' button are:
> 
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {2206cdb0-19c1-11d1-89e0-00c04fd7a829} not registered
err:ole:CoGetClassObject no class object {2206cdb0-19c1-11d1-89e0-00c04fd7a829} could be created for context 0x1
err:ole:CoGetClassObject class {c8b522cf-5cf3-11ce-ade5-00aa0044773d} not registered
err:ole:CoGetClassObject no class object {c8b522cf-5cf3-11ce-ade5-00aa0044773d} could be created for context 0x1
err:ole:CoGetClassObject class {c8b522cf-5cf3-11ce-ade5-00aa0044773d} not registered
err:ole:CoGetClassObject no class object {c8b522cf-5cf3-11ce-ade5-00aa0044773d} could be created for context 0x1
err:ole:CoGetClassObject class {c8b522cf-5cf3-11ce-ade5-00aa0044773d} not registered
err:ole:CoGetClassObject no class object {c8b522cf-5cf3-11ce-ade5-00aa0044773d} could be created for context 0x1
I'm running Ubuntu 9.04 with the latest version of wine.

Any help would be appreciated.

---

### Post by Ceyx on 2009-10-21
Hey Chris,

I eventually got lazy - tweaking Wine after each Distribution Upgrade (8 to 9) and installed Virtual Box OSE.  In case you haven't heard of it, it is a virtual computer within a computer, available from the Synaptic package manager.

[http://www.virtualbox.org/wiki/Screenshots](http://www.virtualbox.org/wiki/Screenshots)

I installed Virtual Box, then a copy of Vista ( yuk, but it will run W2k, XP and even Mac OS 10 ) and within that installed Simply Accounting, Quickbooks, Firefox etc.

Virtual Box is from Sun - and you can tell.  When I need to run Windows stuff I fire it up, and for the great majority of my work I use Ubuntu, all on the same notebook ( not dual boot )

I have never had a problem with this setup...works great.

Hope this helps ..... let me know - I'd be happy to assist.

Ciao for now

---

### Post by Chris Ahern on 2009-10-23
Hi

I've been considering the virtual machine option for a while but hoping I wouldn't have to do it.  I've now exhausted the number of fixes I am willing to try to get Simply to work on wine.

Installing DCOM98 (using winetricks) seemed to fix the registry errors and I tried a few wine versions but I'm still unable to open the Simply database/company files.

I guess Windows programs were designed and tested on Windows, so that's the most appropriate platform for them.  It's a pity, I was hoping to kick the windows habit for good!  For the moment, I'm stuck with it.  So setting up a virtual machine is the next step (I agree with you, it's more preferable than dual boot).

Thanks for your help.
Chris

---

### Post by Ceyx on 2009-10-24
Hey,

I certainly remember the frustration.

A hint for you - if you install Simply using the 60 day trial it will work, but if you try to authenticate your install over the net it will not allow any company to open until it can verify your key .... it has to do with internet access in Wine.  Using the 60 day thing on an ongoing basis was a pain.

Actually, Virtual Box is no trouble once it is set up, and seems to work better.  You do not need a crash in the middle of an accounting session I presume.

Let me know how it goes...

---

