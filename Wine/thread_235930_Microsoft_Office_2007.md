---
title: "Microsoft Office 2007"
date: 2006-08-13
forum: Wine
---

### Post by Sethro on 2006-08-13
I have been using Microsoft Office 2007 Beta for a while on my Windows XP computer and that about the only reason I turn it on. I really want to be able to use it on my Ubuntu box. Thats why I need to ask the experts, do think it will work if I use Wine? Or do you suggest I try with Crossover Office. And also has anyone ever tried this before and if so did you get lucky?

---

### Post by JerMe on 2006-08-14
That's a tough call.  Even with crossover office, Office 2003 support was sketchy.  My guess is that it won't work...

---

### Post by Sethro on 2006-08-14
Yeah I guess your right, but I will give it a try and report my findings. Its a really amazing piece of software.


PS - Do all hackers use Linux?

---

### Post by rejser on 2006-08-14
What's the difference from earlier office?
Havn't tried the -07 but got curious now.

---

### Post by patrickfromspain on 2006-08-14
I can say it won't work. Office 2007 needs windows XP at least, and crossover office doesn't support XP settings. And as said, Office 2003 support is tricky. In my case, I got it installed with all option but Outlook and Access. Also, the installer would work if I only installed word but not with word, excel and powerpoint.

---

### Post by andb on 2006-08-14
Virtual Machine + XP + Office

If this is the only reason you need windows, and Open Office wont suffice, then you can use some virtual machine software (qemu, vmware) to run an xp machine under linux and install office on that. Its easier than it may sound :) 

VMware is technicaly the superior product, but its commercial. The server version is free at the moment as its beta. Qemu does everything you need, is opensource, but its a bit more simple. I use qemu most of the time.

Try these links: 
Qemu HOWTO:
[http://www.ubuntuforums.org/showthread.php?t=187413&highlight=qemu+howto](http://www.ubuntuforums.org/showthread.php?t=187413&highlight=qemu+howto)
VMware HOWTO:
[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=VMware+HOWTO](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=VMware+HOWTO)

This will let you avoid rebooting all the time ;)

---

### Post by Sethro on 2006-08-14
Awsome thanks so much, you know what I think thats what Iam going to do.



Thanks so much guys...:KS

---

### Post by njzillest on 2006-08-14
Yes the perfered operating system for a white/blackhat hacker is Linux. Linux is for the most part an open source project, aimed to all computer users. As the time has progressed, linux has become alot more user friendly. 

Hackers use linux because 
A- It has less vulnerablities than XP
B- Its security privilages are prefect *as apposed to XP's
C- All the code is open
D- It helps get you away from the evil GUI

when i say hackers- I mean white hat hackers. I am not a supporter of any black hat hacker. [-X

---

### Post by Sethro on 2006-08-14
So what is the difference between whit hat hackers and black hat hackers?

---

### Post by Hg80 on 2006-08-14
> **Sethro said:**
> So what is the difference between whit hat hackers and black hat hackers?


From wiki
> # Black hat hacker, a hacker who commits criminal intrusions into technological systems for some real or perceived gain
# White hat hacker, those who attempt to break into systems or networks in order to help the owners of the system by making them aware of security flaws, etc.

And yes office 2007 has some nice features and the new Tabed UI is so sexy....
But then again its a Microsoft product
/me goes back to Openoffice

---

### Post by florizs on 2006-09-08
I've tried MS office 2007 and I have to say, give credit where it's deserved and in this case it truely is. 
Only the 400 dollar pricetag or so is'nt that nice. 
But to conclusion, if it ran under Linux i'd use it, simply because at my school all the documents we reed come in .doc format and they don't always open perfectly in Openoffice.

> 
Well, if your school is a university, check the bookstore or the computer science department for any discounts that you might be able to get. Sometimes you can get the suite for as low as $15, or FREE. Some schools will sell the suite for $100. It depends on the university, so check with yours or your friends.

right forgot about that :)

---

### Post by JerMe on 2006-09-08
Well, if your school is a university, check the bookstore or the computer science department for any discounts that you might be able to get.  Sometimes you can get the suite for as low as $15, or FREE.  Some schools will sell the suite for $100.  It depends on the university, so check with yours or your friends.

---

### Post by homegrown on 2006-09-08
I've not spent any time with 2007, but would be interrested to find out which features are the most attractive -- We can then see if these features or even improvements on them can be made to / added to Open Office -- why should people have to fork out mega $$$ on an office suite?!

This is a perfect example --> This is a student who should be encouraged, NOT asked to pay a $100 for the tools they need.

---

### Post by greywolf79 on 2007-02-24
Has any progress been made getting office 2007 to work on ubuntu? I wish I could stay away from MS products but my employer requires documents to be done in word and excel. It is mostly because of the font choices and what not that make it their choice, and Openoffice just does not support as wide a variety. So I need office 2007 since they just updated to that at the office... I have a legitimate package of office 2007 and am only using xp now in order to use that. I have 0 available money so the solution has to be free, though not necessarily open source. Hope someone has a solution for me... Thanks ahead of time. Ubuntu is by far my favorite OS of all time (and I have used a few)!!!

---

### Post by siefer132 on 2007-04-06
is it just me, or does the VMware server beta not work for other people?

If there is another way to emulate, office on ubuntu, it would be nice if someone posted it here.

thanks.

---

### Post by pooslinger on 2007-04-07
Vmplayer:
1. [http://www.easyvmx.com/](http://www.easyvmx.com/)
2. sudo apt-get install vmware-player
3. Install

KVM (same thing but faster and requires newer processors):
[http://ubuntuforums.org/showthread.php?t=350691&highlight=kvm](http://ubuntuforums.org/showthread.php?t=350691&highlight=kvm)

---

### Post by kornface13 on 2007-08-27
Office 2007 is one impressive piece of Microsoft work.  They did a fantastic job.  i just hate how I can't view my .ppsx presentations in OpenOffice.  Anyone know a way I can still view my 07 Powerpoint files???

---

### Post by SigmaSteve on 2007-09-14
> **homegrown said:**
> 
This is a perfect example --> This is a student who should be encouraged, NOT asked to pay a $100 for the tools they need.

As far as I know, Microsoft hasn't asked him to buy their product.

Look, it's admirable when people contribute their time and effort towards producing a product and then give it away for free; but you can't compel everyone to act this way, and you shouldn't be surprised or angered when some don't.  Bill Gates has done more good for the world than an average man, by a magnitude of thousands.  Remember [|this|]("http://en.wikipedia.org/wiki/Bill_%26_Melinda_Gates_Foundation") thing?

---

### Post by carusoswi on 2007-09-15
> **andb said:**
> Virtual Machine + XP + Office

If this is the only reason you need windows, and Open Office wont suffice, then you can use some virtual machine software (qemu, vmware) to run an xp machine under linux and install office on that. Its easier than it may sound :) 

VMware is technicaly the superior product, but its commercial. The server version is free at the moment as its beta. Qemu does everything you need, is opensource, but its a bit more simple. I use qemu most of the time.

Try these links: 
Qemu HOWTO:
[http://www.ubuntuforums.org/showthread.php?t=187413&highlight=qemu+howto](http://www.ubuntuforums.org/showthread.php?t=187413&highlight=qemu+howto)
VMware HOWTO:
[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=VMware+HOWTO](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=VMware+HOWTO)

This will let you avoid rebooting all the time ;)

I know this is an old thread, but, think the question still valid.  I have crossover installed, and run MS Office - I think my version is 2000.  Anyhow, the easy stuff works fine (excel, word), and, access works, except that if I copy that database and take it from home to my office, it will not run properly on my xp machine.  If I try to open an xp created database (created on my dual boot machinei) in crossover, it will not work correctly.  The reverse is also true with databases created in crossover not functioning on the XP dual boot.

So, it works, sort of.  But isn't totally compatible.

For that matter, I have the same problem with just about everything I run in Crossover.  Photshop 7 is supported, but, many features won't work, some will lock the program up.

Just the state of the Ubuntu art, I suppose.

Caruso

---

### Post by thommango on 2007-10-02
Yeah, I need to use MS-Office 2007 for compatibility with some classmates (they gave us a copy with enrollment!).  I gotta say, it's growing on me.  It takes a while to find some old features, but overall it feels better than earlier versions.  I find myself using open office much less, but hopefully, they'll adopt a similar interface.

---

### Post by xRes on 2008-01-28
Just to let you all know regarding office 2007 - If you have an email address ending in .ac.uk (To prove your at college or Uni) you can have office 2007 for a much more reasonable price:

[URL="http://www.microsoft.com/education/ultimatesteal.mspx"]
http://www.microsoft.com/education/ultimatesteal.mspx[/URL]

[http://www.theultimatesteal.co.uk/]("http://www.theultimatesteal.co.uk/")

I bought mine the other day.

---

### Post by simpleboy on 2008-03-27
Office 2007 can be installed in Ubuntu without a glitch. Here is how. A nice video tutorial [http://goodbutbad.blogspot.com/2008/03/install-m-office-2007-in-ubuntu.html]("http://goodbutbad.blogspot.com/2008/03/install-m-office-2007-in-ubuntu.html")

---

### Post by bigbooger on 2008-04-01
[http://wine-review.blogspot.com/2008/03/microsoft-office-2007-update.html](http://wine-review.blogspot.com/2008/03/microsoft-office-2007-update.html)

If you want to tweak it out a bit using office 2007 this site will help:

> Microsoft Office 2007 Update

TWICKLINE asked me to write up a howto on some of the workarounds I sent him after he got Microsoft Office 2007 (Office12) working. So without any further interruptions I return you to your regular scheduled program.

First of all anyone who used TWICKLINE’s method of using CrossOver Games 7 must either

   1. Buy a copy of CrossOver Games 7
   2. Buy a copy of CrossOver Office, which comes with CrossOver Games 7 for free!
   3. Build CrossOver Games from source

The reason behind this is because using the rpcrt4.dll from CX Games for more than 7 days violates the evaluation license with CodeWeavers for a free trial of CX Games not to mention floating their work around is warez and illegal! That being said there are some other methods to accomplish the goal of getting Office12 to work in Wine.

You can either:

   1. Use the rpcrt4.dll and install Microsoft Office 2007 to get it installed and then delete rpcrt4.dll and go back to original builtin (don’t worry Office12 will work just fine with out it) or
   2. Download CX Games Source and compile the builtin rpcrt4.dll.so and not worry about it being illegal since it is opensource

Follow these procedures to use CX Games opensource rpcrt4.dll.so using the terminal:

wget [http://media.codeweavers.com/pub/crossover/source/crossover-games-wine-src-7.0.0.tar.gz](http://media.codeweavers.com/pub/crossover/source/crossover-games-wine-src-7.0.0.tar.gz)
tar –xvf crossover-games-wine-src-7.0.0.tar.gz
cd crossover-games-wine-src-7.0.0/source/wine
./configure
make depend && make
sudo cp /usr/lib/wine/rpcrt4.dll.so /usr/lib/wine/rpcrt4.dll.so.bak
sudo cp dlls/rpcrt4/rpcrt4.dll.so /usr/lib/wine

Now you don’t even need to specify rpcrt4.dll as native in winecfg since you compiled the builtin rpcrt4.dll.so and a much cleaner winecfg.

Now that we are legal lets talk about what does and doesn’t work right now and some workarounds to get some things working better. Right now the following programs work:

    * Excel
    * OneNote
    * PowerPoint (degraded – can’t use presentation portion)
    * PowerPoint Viewer
    * Picture Manager
    * Publisher
    * WinWord

Which still leaves the following programs on the broken list:

    * Access
    * Groove
    * InfoPath
    * Outlook

If you are a user who is unable to use PowerPoint because it crashes after install. Delete your .wine directory > rm –rf ~/.wine and then follow the method above to get the builtin rpcrt4.dll.so and change wincfg to run as Windows Vista and then reinstall Microsoft Office 2007. After installation run winecfg and change back to Windows XP.

The reason you need to be in Windows Vista for install is because I noticed registry values are getting inputed incorrectly during the install under Windows XP.

PowerPoint will now work fine, but it has one really bad flaw in Wine’s current state in that you can edit presentations but you cannot view them full screen as a presentation. You’ll be able to view two slides and then nothing will happen when you advance or reverse. The workaround here is to use the PowerPoint Viewer 2007 which works flawlessly.

I also wanted to give you users who like Microsoft Office 2007 better then OpenOffice some tips on how to integrate it into your system so you can open documents, presentations and spreadsheets from anywhere and have them open correctly.

Open your favorite text editor and make the following 5 scripts:

excel
#!/bin/bash
wine "c:\\Program Files\\Microsoft Office\\OFFICE12\\EXCEL.EXE" "`winepath -w "$@"`"

onenote
#!/bin/bash
wine "c:\\Program Files\\Microsoft Office\\OFFICE12\\ONENOTE.EXE" "`winepath -w "$@"`"

powerpoint
#!/bin/bash
wine "c:\\Program Files\\Microsoft Office\\OFFICE12\\POWERPNT.EXE" "`winepath -w "$@"`"

pptviewer
#!/bin/bash
wine "c:\\Program Files\\Microsoft Office\\OFFICE12\\PPTVIEW.EXE" "`winepath -w "$@"`"

publisher
#!/bin/bash
wine "c:\\Program Files\\Microsoft Office\\OFFICE12\\MSPUB.EXE" "`winepath -w "$@"`"

winword
#!/bin/bash
wine "C:\Program Files\Microsoft Office\Office12\WINWORD.EXE" "`winepath -w "$@"`"

sudo chmod a+x word excel onenote powerpoint pptviewer pubisher
sudo cp word excel onenote powerpoint pptviewer pubisher /usr/local/bin/

There are two methods to make associations for the following file types: .doc .docx .xls .xlsx .ppt .pptx .one .onetoc .pub

   1. Use your favorite file browser and right click on document ie: .doc and then click open with and then point to the associated script that you placed in /usr/local/bin/winword and repeat this method for all the other file types.
   2. Follow KDE or GNOME portion for file associations

KDE users follow this portion to integrate the script you just made

Run the Configure Desktop (Personal Settings) > KDE Componentes > File Associations

click in the "Find filename pattern" box and type in the box .doc then click on application. You'll see two items one for .doc and the other is for .docx. Click the Add button on the lower right and point to the scripts we made above /usr/local/bin/winword and then click ok

Repeat this method for .ppt .xls

For .one .onetoc and .pub you'll have to add from scratch click the add on the bottom left and give a name for this profile say for Microsoft OneNote we'll call it msonenote click on application for type. Then at click Add at the top right to specify the file type *.one and then click add again and add *.pub and click ok. Then click the Add button on the bottom right and specify the script /usr/local/bin/onenote

Repeat this method for .pub

GNOME users follow this portion to integrate the script you just made

Use nautilus file browser and right click on a document ie: .doc and then click open with and click on custom application then point to the associated script that you placed in /usr/local/bin/winword and repeat this method for all the other file types.

Summary
All in all you can get some usability from Microsoft Office 2007 from using the rpcrt4.dll.so from CodeWeavers CrossOver suite, but it’s crippled at best. I recommend that you all buy CrossOver Office which comes with a free copy of CrossOver Games which will allow you to use the entire Microsoft Office 7 suite with no hiccups.

Additionally, anyone who uses Wine should buy CrossOver Office because not only do you get a good product but it supports Wine! All the code that CodeWeavers makes minus the hacks make their way back into Wine and it pays for the developers who spend days on end writing code for Wine.

---

### Post by tettayes on 2008-04-04
can i use an .exe file to install rather than using a CD?

---

### Post by jso2897 on 2008-04-05
I have both XP and Ubuntu machines, and I have both Office 2007 and OpenOffice on the XP machines. While documents can't be readily exported between the two, it's a small matter to merely cut and past the DATA from any document to one in the other format, and even formulas copy correctly - so it's no trouble for me to duplicate all my documents in both Office and OpenOffice. :)

---

### Post by Brian96 on 2008-04-05
> **xRes said:**
> Just to let you all know regarding office 2007 - If you have an email address ending in .ac.uk (To prove your at college or Uni) you can have office 2007 for a much more reasonable price:

[URL="http://www.microsoft.com/education/ultimatesteal.mspx"]
http://www.microsoft.com/education/ultimatesteal.mspx[/URL]

[http://www.theultimatesteal.co.uk/]("http://www.theultimatesteal.co.uk/")

I bought mine the other day.

And state-side it is theultimatesteal.com and you need a valid .edu e-mail address. You get M$ Office 2007 Ultimate for $60 (retail $678). The offer ends 4/30/2008 and this is the full software, not a trial or otherwise time-delimited license or key.

Not many people need this feature, but M$ Excel 2007 has significantly increased the number of columns available.

I am trying to migrate (slowly, albeit) to a pure FOSS system, but the advancements in Office 2007 are pretty significant. My hope is that Office 2007 will last me a good 6-7 years, and that by that time OpenOffice or the like will have made significant gains.

And for the original point of this thread, I highly doubt Office 2007 will work in WINE or Crossover. I highly recommend VMWare server with XP (if you own a legal copy) for your holdover M$ must-have programs. It is way more convenient than a dual-boot system.

---

### Post by p_quarles on 2008-04-05
Moved to Wine section.

---

### Post by tettayes on 2008-04-06
I get an error when installing with office2k7.exe.
I got that office 2007 through my school online, but it does not seem to work... 
anyone know how to deal with it??
Many thanks to all of you.

---

### Post by Gary_inNYC on 2008-04-08
After considerable googling on the topic, I'm glad to report that Office 2007 Enterprise works near flawlessly in Wine!

I gathered steps to install correctly from these links (tab them now, you won't regret it :))

[http://wine-review.blogspot.com/2008/03/office-2007-on-linux-with-wine-install.html](http://wine-review.blogspot.com/2008/03/office-2007-on-linux-with-wine-install.html)
[http://goodbutbad.blogspot.com/2008/03/install-m-office-2007-in-ubuntu.html](http://goodbutbad.blogspot.com/2008/03/install-m-office-2007-in-ubuntu.html)
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

special thanks to twickline, medo, and a-s-h-o-k for your contributions and steps.  

NOTES:  from those sources, I found that twickline's steps differentiated from ashok's in that the latter downloaded rpcrt4.dll and msxml3.dll instead of installing CrossOver Games to copy the dlls over to the system32 folder.  Ashok's way was much simpler and less messy, but nonetheless derivative of twickline's methods.  Finally, to get PowerPoint to run, I followed medo's reply to Dan's comment from twickline's how-to page.  

So, here are the steps I subsequently used (in order of use):

1) I added the apt wine repository, installing wine subsequently
2) I followed ashok's method of replacing the 2 dlls in system32; credit to twickline's discoveries of course.
3) I then followed medo's fix: install winetricks and then from terminal, sh winetricks riched20 riched30
4) finally, I popped in my CD and ran setup.exe by selecting from the context menu to run it with wine.

it was smooth sailing from there.  all i had to do was type up my serial and everything works flawlessly so far except an odd anomaly in MSWord: i tested times new roman font and found that bold didn't work.   If anyone can an provide explanation and fix, I'd appreciate it!

- Gary_inNYC

---

### Post by Gary_inNYC on 2008-04-08
I figured a way to fix the Times New Roman bold font anomaly...

For some reason Times New Roman didn't work properly in my installation of MSWord 2007, however I found that "Times" worked as expected.  Essentially "Times" (is) Times New Roman so I set that as my default font.

To change the default font in MSWord, I read through this how-to:
[http://support.microsoft.com/kb/291291](http://support.microsoft.com/kb/291291)

Now my Office07 in wine setup is complete... cheers!  If only there were less reliance on M$ Office, but that's another story.

- Gary_inNYC

---

### Post by dd12 on 2008-04-16
I am having an issue when trying to install msxml3.msi
When I type $ msiexec /i msxml3.msi in terminal I get this error message:
err:msi:copy_package_to_temp failed to copy package L"msxml3.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"msxml3.msi"

any suggestions?

---

### Post by thepossiblehuman on 2008-04-17
I'm having some issues with this as well.  I run through the wine install, the dll change, the msxml3.msi execution, and wine tricks setup without an issue (although I did need to get cabextract for wine tricks).

It's the actual Office setup that I have issues with.  Enterprise 2007 doesn't install completely.  It appears to get 3/4 of the way through and then bails out saying it encountered errors:

```
 fixme:xrender:X11DRV_AlphaBlend not a dibsection
fixme:xrender:X11DRV_AlphaBlend not a dibsection
fixme:xrender:X11DRV_AlphaBlend not a dibsection
fixme:xrender:X11DRV_AlphaBlend not a dibsection
fixme:xrender:X11DRV_AlphaBlend not a dibsection
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:htmlhelp:HtmlHelpW HH case HH_UNINITIALIZE not handled.
fixme:reg:GetNativeSystemInfo (0x33f174) using GetSystemInfo()
fixme:powrprof:DllMain (0x7da80000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:netapi32:NetGetJoinInformation Stub (null) 0x33f19c 0x33f190
fixme:advapi:CheckTokenMembership ((nil) 0x12f170 0x33f178) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x12f170 0x33f178) stub!
fixme:nls:GetUserGeoID 16
fixme:powrprof:DllMain (0x7da80000, 0, (nil)) not fully implemented

```

Above is the last thing I see in the terminal window.  

I tried installing just Groove as my work uses that for collaboration, and that install actually completed.  However when I try to run it, it says that it isn't installed "for the current user. please rerun setup."

Since Groove gets installed, the Office Tools also get installed and they actually work.  

I tried both XP and Vista emulation for these setups.  XP is what actually gives me that Groove error.  When emulating Vista, the install (for Groove) goes through but the process starts and freezes upon execution... No error.  The Office install bails at the same regardless of emulation.  

Any help is appreciated.  I'd love to get away from needing a XP VM.

---

### Post by thepossiblehuman on 2008-04-17
BTW, this is what I see when I try to run Groove:

```

fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:process:IsWow64Process (0xffffffff 0x34fc7c) stub!
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
... (this line repeats a lot)...
wine: Call from 0x68f249c5 to unimplemented function KERNEL32.dll.RtlCaptureContext, aborting
err:ntdll:RtlpWaitForCriticalSection section 0x68fabce4 "?" wait timed out in thread 0010, blocked by 000f, retrying (60 sec)

```

It then just keeps popping up that retrying line every 60 seconds.

---

### Post by d4ng3r on 2008-04-23
I seem to have the same problem with my Enterprise, it installs about 3/4 of the way, and then jumps to installation complete, but I cannot connect to the internet to activate, so it won't work for more than 12 uses, since I only have the serial number provided by my company's IT guy.  Does this only work with Professional?

---

### Post by Gary_inNYC on 2008-05-03
Since I have installed Hardy, the same methods that otherwise worked in Gutsy to install Office 2007 no longer work for me.  I now receive a series of errors stemming from issues like:

preloader: Warning: failed to reserve range 00000000-00010000

I got the preloader error fixed using this thread:
[http://ubuntuforums.org/showthread.php?p=4809920#post4809920](http://ubuntuforums.org/showthread.php?p=4809920#post4809920)
----------------------

I now also get the same error mentioned in another reply when installing msxml3.msi:

err:msi:copy_package_to_temp failed to copy package L"msxml3.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"msxml3.msi"

----------------------

While in terminal during installation, I now get repeated messages such as:

fixme:xrender:X11DRV_AlphaBlend not a dibsection

fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet

err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded

err:ole:CoUninitialize Mismatched CoUninitialize

------------

Finally, the whole installation ends prematurely with this in terminal:

err:heap:HEAP_ValidateInUseArena Heap 0x110000: bad back ptr 0x650063 for arena 0x5182db8
err:heap:HEAP_ValidateInUseArena Heap 0x110000: in-use arena 0x5182d70 next block has PREV_FREE flag
wine: Unhandled page fault on write access to 0x05382e14 at address 0x7bc422f3 (thread 001a), starting debugger...
err:ntdll:RtlpWaitForCriticalSection section 0x110048 "heap.c: main process heap section" wait timed out in thread 0009, blocked by 001a, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x110048 "heap.c: main process heap section" wait timed out in thread 0009, blocked by 001a, retrying (60 sec)

---------------

The end result is an incomplete installation that doesn't work.  It ends abruptly at about 75-80% into the installation process.  

- Gary_inNYC

---

### Post by nitewulf on 2008-05-16
I got office 2007 installed using Wine 1.0 beta on Hardy 8.04.  Which absolutely amazed me, i just didn't think it was possible.  Just one question, maybe two.  

1.  All of the fonts are unclear and slightly distorted, is there anyway to make the fonts look sharp and clear?

2.  Has any one had success getting any of the other programs to work, such as Access?

---

### Post by Brian96 on 2008-05-17
> **nitewulf said:**
> I got office 2007 installed using Wine 1.0 beta on Hardy 8.04.  Which absolutely amazed me, i just didn't think it was possible.  Just one question, maybe two.  

1.  All of the fonts are unclear and slightly distorted, is there anyway to make the fonts look sharp and clear?

2.  Has any one had success getting any of the other programs to work, such as Access?

Which Office programs did you test? Were there other issues besides the fonts?

---

### Post by smink75 on 2008-05-20
Im using Hardy too and i get this same error non stop!

> fixme:xrender:X11DRV_AlphaBlend not a dibsection

It never installs anything...
has anyone found a fix to this yet? Ive done alot so far to come to this point.

---

### Post by MadsRH on 2008-05-21
Hi
I'm running Office2007 on Ubuntu 8.04 and it works great :)
I also tried installing it with the Wine RC1, but it won't work. I've seen that it can work with RC1 [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992&iTestingId=24954")...
Anyway, I tried with the Wine version that comes default with 8.04 and followed this guide:

[http://anotherubuntu.blogspot.com/2008/05/microsoft-office-2007-on-ubuntu.html](http://anotherubuntu.blogspot.com/2008/05/microsoft-office-2007-on-ubuntu.html)
[B]
MadsRH[/B]

---

### Post by porkrind427 on 2008-06-10
> **smink75 said:**
> Im using Hardy too and i get this same error non stop!

> fixme:xrender:X11DRV_AlphaBlend not a dibsection

It never installs anything...
has anyone found a fix to this yet? Ive done alot so far to come to this point.
I get about 3/4 installed and get the same error. I also get

> err:msidb:msi_table_load_transform no matching row to transform

several times right before that loop. Have you noticed that? Anyways, I reran "msiexec /i msxml3.msi" thinking I might have done that wrong and saw that I am getting a whole string of errors. Is this expected?

> fixme:advapi:LookupAccountNameW (null) L"clint" (nil) 0x32f7fc (nil) 0x32f800 0x32f7f4 - stub
fixme:advapi:LookupAccountNameW (null) L"clint" 0x12c1c0 0x32f7fc 0x12b598 0x32f800 0x32f7f4 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 2 ignored L"Upgrade" table values
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 2 ignored L"Upgrade" table values
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 2 ignored L"Upgrade" table values

I'll be honest, I'm a newb and these messages mean very little to me. Maybe (hopefully) someone can help point me in the right direction on what to do next.

---

### Post by Amarsingh0793 on 2008-09-03
Office 2007 is very easy to install on Ubuntu if you have Play On Linux installed. It took 2 minutes for the installation to complete and all of the programs work (except Access).

---

### Post by killer_d76 on 2008-09-14
> **tettayes said:**
> can i use an .exe file to install rather than using a CD?

same question here.. i have the free trial version that i have been using for quite sometime now, i still have 30days remaining, but i don't want to go to the hassle of starting my Vbox to have an access to it all the time.

---

### Post by killer_d76 on 2008-09-15
hehehe.. Crossover Linux was the answer to my querry if anyone would like to know.. i was able to make MS Office 2007 trial version works properly on my Ubuntu desktop! ;)

---

### Post by killer_d76 on 2008-09-19
...okey i was able to install MS Office 2007 properly using Wine 1.1.4 since my CrossOver Linux is just a trial version..

click here for the thread that i have created on how to do it: [http://ubuntuforums.org/showthread.php?t=922963]("http://ubuntuforums.org/showthread.php?t=922963")

---

### Post by athoopal on 2008-11-08
installed office 2007 on my xubuntu with crossover. works great. need help in the desktop integration. the cxmenu (Applications>Other) doesnt work. starts from /cxoffice/bin/{winword/excel etc}.sh and the file associations are also perfect. could anybody help with the launcher.

---

### Post by digi2112 on 2008-12-01
Everything works here except Powerpoint - I have Ubuntu 8.10 and wine-1.1.8 running Office 2007 Enterprise.

Doesn't run too bad - Fonts and buttons work correctly. Still testing...

---

### Post by CloudSportRacer on 2008-12-02
> **digi2112 said:**
> Everything works here except Powerpoint - I have Ubuntu 8.10 and wine-1.1.8 running Office 2007 Enterprise.

Doesn't run too bad - Fonts and buttons work correctly. Still testing...

How may I ask did you do this? I was trying to install this for preparation of a presentation due in class in the next coming week. I kept getting an error stating I was missing a file. Install would not even begin. Thanks!

---

### Post by digi2112 on 2008-12-02
> **CloudSportRacer said:**
> How may I ask did you do this? I was trying to install this for preparation of a presentation due in class in the next coming week. I kept getting an error stating I was missing a file. Install would not even begin. Thanks!

Install Playonlinux (its free and works good) - I setup an adminfile for Office 2007 and named it full.msp 

I used "wine setup.exe /adminfile full.msp" and it completely installed without a hitch.

I did try to use playonlinux's installer but I could not figure out how to run the setup.exe with all the parameters (/adminfile full.msp) so I just tried it straight out of a terminal (command line) and everything seems to work but Powerpoint.

G'luck

---

### Post by siriusb_hun on 2008-12-06
Hi,
I succesfully installed excel and word 2007 on intrepid. I have only one issue: some xls files (originally created 1-2 years ago who knows with which office)  i can't save: no such a directory blablabla the message. When I save as xlsx it is saved, then save as xls again, and it is saved!
Any idea why is that? Thx

---

### Post by Anbin89 on 2008-12-07
> **Amarsingh0793 said:**
> Office 2007 is very easy to install on Ubuntu if you have Play On Linux installed. It took 2 minutes for the installation to complete and all of the programs work (except Access).

I am a newbie man.. can you like explain it in details please.. i have found and installed the PlayOnLinux... but it shows some errors during the installation.. can i have like a step by step instructions... thanks man..

---

### Post by Amarsingh0793 on 2008-12-07
Ok :),

1) Open PlayonLinux
2) **Click** the **install** button (on the top)
3) **Click** on the link which says **"Install a .pol package or an unsupported application"**
4) Continue with **"Manual Installation"** selected
  **The wizard for Manual Installation should now appear**
5) **Click "Forward"** and **Click "Forward"** again **after** **"Install a program in a new prefix" is selected**
6) For your prefix, you can type pretty much anything you want, but let's keep it simple :) Try using "MSOFFICE07" as a prefix. Then **click "Forward"** again.
7) Wait for the wine prefix to be created (it tells you when it is doing this)
8. Now it should say **"Please choose the file to execute"**. **Click "Browse"** and **navigate to your "setup.exe" file **(whether it is on disc or not).
9) _Follow the instructions of the Microsoft Installer_
10) **Enjoy** :)

Good Luck

---

### Post by tntxx9 on 2008-12-08
Thanks Amarsingh0793 !
I was searching for something easy to install because i only rebooted by pc to go to vista because office 2007 and now it's link using ubuntu 4ever hehe (today it's my 6st day using ubuntu and it's amazing ! without any erros, nothing ! beautiful hehe)
Thanks again Amarsingh0793 :p

---

### Post by Amarsingh0793 on 2008-12-09
> **tntxx9 said:**
> Thanks Amarsingh0793 !
I was searching for something easy to install because i only rebooted by pc to go to vista because office 2007 and now it's link using ubuntu 4ever hehe (today it's my 6st day using ubuntu and it's amazing ! without any erros, nothing ! beautiful hehe)
Thanks again Amarsingh0793 :p

No problem. Glad I could help :)

---

### Post by JonyBoyct on 2009-04-21
Kamusta!
This Helped me to install Office 2007.
Really easy. Check it out.
It's an up to date version. Using wine version 1.1.16.
There are links there for both version 8.08 and 8.10.  Have fun!!
[http://ubuntuforums.org/showthread.php?t=1102840](http://ubuntuforums.org/showthread.php?t=1102840)

---

### Post by jhoeijao on 2009-05-30
I have an alternative guide I hope this will work for those people who are still having problem in installing MS Office 2007.

[http://ubuntuforums.org/showthread.php?t=1173365&highlight=microsoft](http://ubuntuforums.org/showthread.php?t=1173365&highlight=microsoft)

---

### Post by dhtseany on 2009-05-31
OK, while I'm sure the other methods worked for people, I used the following:

[http://ubuntuforums.org/showthread.php?t=844309&highlight=office+2007](http://ubuntuforums.org/showthread.php?t=844309&highlight=office+2007)
(Remember to swap steps 9 & 10).

Then, instead of the crazy scripts that people are talking about (that in the end didn't work for me at ALL), I just right-clicked on a .doc file -> Open With tab -> and selected "Wine Windows Program Loader" (If it's not there, click add and select it). You'll have to do that for every file associated with Office (ie. .doc, .docx, .xls, etc.)

Hope this helped

Peace
Sean

---

