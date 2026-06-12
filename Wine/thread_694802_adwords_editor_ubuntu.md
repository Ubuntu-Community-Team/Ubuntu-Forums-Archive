---
title: "adwords editor ubuntu"
date: 2008-02-12
forum: Wine
---

### Post by mommalomas on 2008-02-12
I'm totally newbie with wine and Ubuntu at all.

Is there any possibility to install and use [Adwords Editor]("http://www.google.com/intl/en/adwordseditor/")?

I've got this error when trying to install:
> ~/Desktop$ wine adwords_editor_en-US.msi
wine: could not load L"Z:\\home\\ingvar\\Desktop\\adwords_editor_en-US.msi": Bad EXE format for](*,)

---

### Post by hyperair on 2008-02-12
That's an msi file you're trying to run. Instead of "wine", use "msiexec". ```
msiexec adwords_editor_en-US.msi
```
msiexec is a program included with Wine to open msi files.

---

### Post by timzak on 2008-02-12
Why not just install Abiword from Synaptic?  Go to System->Administration->Synaptic Package Manager and search for Abiword.  Click the box to the left of it and select Install and it will automate the process for you.  It also makes removing and updating the software easy.

EDIT:  forgive me!  I read your post wrong (obviously).  Disregard this post.

---

### Post by mommalomas on 2008-02-12
It's looks like everything working just fine.
Big thanks \\:D/

---

### Post by sorak on 2008-04-01
```
[~/downloads]
sorak@shivalaptop: msiexec /i adwords_editor_en-US.msi 

err:wineboot:ProcessRunKeys Error running cmd #0 (2)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:sfc:SfcIsKeyProtected ((nil), (null)) stub
fixme:advapi:RegisterEventSourceA ((null),"MsiInstaller"): stub
fixme:advapi:RegisterEventSourceW (L"",L"MsiInstaller"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x000003f5,(nil),0x0006,0x00000000,0x32e4b0,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003f5,(nil),0x0006,0x00000000,0x14c7e8,(nil)): stub
err:eventlog:ReportEventW L"=====================================================rnException code: C0000005 ACCESS_VIOLATIONrnFunction: 0x0rn=====================================================rnrnRegisters:rnEAX:00000000  EBX:004BEF2D  ECX:0032E4EC  EDX:00000031  ESI:0032E674  EDI:00000000rnCS:EIP:0073:00000000 "...
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
```

...thoughts? google isnt helping much on this one.

---

### Post by kriketini on 2008-04-13
> **hyperair said:**
> That's an msi file you're trying to run. Instead of "wine", use "msiexec". ```
msiexec adwords_editor_en-US.msi
```
msiexec is a program included with Wine to open msi files.

I did exactly that, installer did installation, but when i tried to open the editor, nothing happens. I looks like the editor is starting up, then nothing. Thanks for any suggestions.

---

### Post by Jonathan Métillon on 2008-06-30
Hi,

I think web marketing tools are essential features for professionnal adoption of Ubuntu. These issues should be fixed.

I also have trouble starting AdWords Editor 6.0 on Ubuntu 8.04. It installed correctly using

```
msiexec /i adwords_editor_fr-FR.msi
```(don't forget the /i !!)

But when trying to run the installed binary:

```
$ wine adwords_editor.exe 
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\Google\\Google AdWords Editor\\adwords_editor.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Google\\Google AdWords Editor\\adwords_editor.exe" failed, status c0000135
```Any idea how to fix that? Thanks!

---

### Post by Jonathan Métillon on 2009-04-03
I don't get the point of building a XUL app if it's not to be cross platform...

---

### Post by NightMKoder on 2009-04-04
> **Jonathan Métillon said:**
> Hi,

I think web marketing tools are essential features for professionnal adoption of Ubuntu. These issues should be fixed.

I also have trouble starting AdWords Editor 6.0 on Ubuntu 8.04. It installed correctly using

```
msiexec /i adwords_editor_fr-FR.msi
```(don't forget the /i !!)

But when trying to run the installed binary:

```
$ wine adwords_editor.exe 
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\Google\\Google AdWords Editor\\adwords_editor.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Google\\Google AdWords Editor\\adwords_editor.exe" failed, status c0000135
```Any idea how to fix that? Thanks!

Ignoring the preloading warnings (shouldn't matter), you need `winetricks vcrun2003`. That's all I can tell you from that log file.

---

### Post by Jonathan Métillon on 2009-04-05
> **NightMKoder said:**
> Ignoring the preloading warnings (shouldn't matter), you need `winetricks vcrun2003`. That's all I can tell you from that log file.

Hi,

Thank you NightMKoder.

I think the updated version of Wine I use includes *vcrun2003*. At least I don't encounter the *dosmem* error. But now I get this:

```
$ wine adwords_editor.exe 
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\Google\\Google AdWords Editor\\xulrunner\\xul.dll") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\Google\\Google AdWords Editor\\xulrunner\\xul.dll") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\Google\\Google AdWords Editor\\xulrunner\\xul.dll") not found
err:module:import_dll Library xul.dll (which is needed by L"C:\\Program Files\\Google\\Google AdWords Editor\\xulrunner\\xpcom.dll") not found
```

And I get a *XULRunner* error alert telling me "**Couldn't load XPCOM**".

How can I fix that?

---

### Post by gbinal on 2009-04-27
Good news, folks.  

I'd hit the same roadblocks as above, reaching the 'Couldn't Load XPCOM' error after a successful install (Thank you,  Jonathan Métillon).  The solution though, is described at the bottom of this page:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10174&iTestingId=18654](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10174&iTestingId=18654)    (courtesy of a saint called Xin).  

At issue are two missing windows files:


msvcp71.dll
msvcr71.dll 

By googling the file name, I found options that allow you to download those two files. That is what I did, though if you have a windows machine, you can install Adwords Editor on it, then look in c:/Windows/system32.  Once you have these files, then:


[INDENT]...copy them to .wine/drive_c/windows/system32 under your home director  * [Note that on my computer, I had to copy them to /home/username/.wine/dosdevices/c:/windows/system32 ]*

6) start winecfg  *[I just type winecfg in terminal]*

7) click on libraries tab. Add those two libraries. Set to 'native,builtin'. When adding libraries, simple type in the name(without .dll) and click on add.

8) try 'wine adwords_editor.exe' again, and after 10 seconds of loading, it should work!
[/INDENT]

Also note that in terminal, I had to change directory to /home/username/.wine/dosdevices/c:/Program Files/Google/Google AdWords Editor before typing 'wine adwords_editor.exe' but by this point, the Adwords Editor entry under Wine in my Main Menu was working fine.  

I am running Ubuntu 9.04 and using Adwords Editor 7.0.  

Thanks to everyone above for helping me figure this out.

---

### Post by sunshin3 on 2009-07-30
New adwords editor 7.5 does not function under 9.04. After started, it displays 
multiple runtime errors R6034 followed by "Couldn't load XPCOM".
In the console log i see:
...
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"

The above trick with replacing DLLs doesn't help anymore. Any ideas?

---

### Post by fdsfjdshj on 2009-08-25
gibney.org published the solution:

[http://en.gibney.org/google_adwords_editor_7.5_on_wine/](http://en.gibney.org/google_adwords_editor_7.5_on_wine/)

---

### Post by intrepidibex on 2009-10-08
> **fdsfjdshj said:**
> gibney.org published the solution:

[http://en.gibney.org/google_adwords_editor_7.5_on_wine/](http://en.gibney.org/google_adwords_editor_7.5_on_wine/)

I am new to using the command line with Ubuntu.  Learning how to run Wine is changing that.  I am hoping someone can help me with a few questions.  In the solution at the quoted link, the proper command reads:

[B][I]When trying to run wine adwords_editor.exe you will get several "R6034" errors and one "Couldn't load XPCOM" error. 

Solution (tested on Ubuntu 9.04): 

apt-get install cabextract 
wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks) 
chmod +x winetricks 
./winetricks vcrun2005 vcrun2005sp1

Now wine adwords_editor.exe works.[/I][/B]    

My questions.  Do you have to type sudu to assume administrative powers?  From what I am understanding from Ubuntu Kung Fu, root administrative powers precede the command 'apt-get'.

how exactly do you enter the prompts outlined here?

line by line?
apt-get install cabextract
then
wget [http://www.kegel.com/wine](http://www.kegel.com/wine) winetricks

or do you enter all the text as one long prompt?

Does this make sense?

I am running release 8.10 Intrepid Ibex.

---

### Post by nolajohn on 2010-01-11
Google Adwords Editor is the only application that I have missed since I switched to Linux.  I have tried this in the past, with no success, but now, it works!!  Ubuntu 8.04 LTS.  Here is exactly what I did:

1. Installed Wine. From the terminal:

$ sudo apt-get install wine

2. Then I found the latest version information for Wine and followed the guide here (in my case for Hardy):

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

3. I waited for Ubuntu Update Manager to tell me I had an update and then let it install.

4. Next I ran "Configure Wine", which on my system is:

Applications -> Wine -> Configure Wine

5. Wine Config threw an alert that I needed something (sorry missed what it was) but it proceeded to download it.  I let it finish.  Now my Wine version (under the "About" tab) is: Wine 1.1.36

6. Back to the terminal, I navigated to the "C:" drive, which on my system is:

$ cd ~/.wine/drive_c

7. Created a directory for the Adwords Editor installation files:

$ mkdir ADWE_Install

8. Found the latest Windows version of Adwords Editor on the Google site, and downloaded it to the directory I created.  Just "Google it" and download to the right place.

9. Changed to the install directory:

$ cd ADWE_Install

10. Confirmed that the file is there, by:

$ ls

The installation file is: adwords_editor_en-US.msi

11. Typed the following to install:

msiexec /i adwords_editor_en-US.msi

12. Followed the instructions, accepted the license etc.

13. Ran Adwords Editor:

Applications -> Wine -> Programs -> Google Adwords Editor -> Adwords Editor

That's it!!  It works.  At least on my system.  The fonts look like hell, but I don't care.

This is my first post. I really hope this helps somebody. :P

---

### Post by gual0s on 2010-02-16
Just tested with Ubuntu 9.10

Install Wine from regular repos:
```
sudo aptitude install wine
```

Get winetricks script:
```
wget http://www.kegel.com/wine/winetricks
```

Install vcrun2005:
```
sh winetricks vcrun2005
```

Download AdWords Editor from google 
[http://www.google.com/intl/en/adwordseditor/](http://www.google.com/intl/en/adwordseditor/)

and install it:
```
msiexec /i adwords_editor_en-US.msi
```

That's it!

---

### Post by SanjoEel on 2010-02-27
Thanks gual0s that worked great!

---

### Post by xndrei on 2010-06-18
AWESOME ! one more fear disappeared ...

---

### Post by DutchSherpa on 2010-07-06
After entering the msiexec command, an alert pops up: "Invalid command line parameters". What can be the cause? Thanks in advance.
(I am using Lucid, all updates installed, etc.)

---

### Post by jabz on 2010-10-18
I can confirm that gual0s' solution also works with Ubuntu 10.04

---

### Post by jamesjcrum04 on 2011-10-09
> **gual0s said:**
> Just tested with Ubuntu 9.10

Install Wine from regular repos:
```
sudo aptitude install wine
```Get winetricks script:
```
wget http://www.kegel.com/wine/winetricks
```Install vcrun2005:
```
sh winetricks vcrun2005
```Download AdWords Editor from google 
[http://www.google.com/intl/en/adwordseditor/](http://www.google.com/intl/en/adwordseditor/)

and install it:
```
msiexec /i adwords_editor_en-US.msi
```That's it!


When I insert this "msiexec /i adwords_editor_en-US.msi" into the terminal nothing happens that I can tell. Please help. If I cannot get adwords to work I will have to switch back to windows and I don't want that to happen!
:confused:

---

### Post by ergo-proxy on 2011-10-10
Make sure you have the latest beta/stable wine installed, then run: 
wine start whatever.msi

---

### Post by peterx14 on 2012-05-10
I'm trying to get my new Ubuntu 12.04 (64 bit) install usable but I can't get Google Adwords Editor (9.7.1) working.
```

$ sudo apt-get install wine
$ msiexec /i adwords-editor-en-GB.msi
```
Works this far; I can install AdWords editor okay, but it complains about not being able to check for updates. So I ignore that, and try to set up my accounts, but again it complains it can't access them. So I try launching from a terminal:
```

$ wine start "C:\users\peterx14\Local Settings\Application Data\Google\Google Adwords Editor\adwords_editor.exe"

```
and I see:
```

fixme:exec:SHELL_execute flags ignored: 0x00000100
peterx14@ubuntu:~/.wine$ p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:system:SetProcessDPIAware stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x138e994, overlapped 0x138e978): stub
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:resource:GetGuiResources (0xffffffff,0): stub

```
I'm guessing it looking for an i386 module on my 64-bit Ubuntu isn't a good sign?

Anyone got any ideas? It seems to be _almost_ working perfectly... but not quite!

---

