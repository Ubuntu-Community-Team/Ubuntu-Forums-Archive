---
title: "Trying to install Office 2007"
date: 2008-04-25
forum: Wine
---

### Post by WeeManDan on 2008-04-25
Hi all,

I'm currently trying to follow [this tutorial]("http://www.quicktweaks.com/2008/04/09/install-ms-office-2007-in-linux/") for installing Office 2007

I followed the instructions for the unable to access the first megabyte problem from [http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem) but now when I try to run msiexec /i msxml.msi I get the following error:

err:msi:copy_package_to_temp failed to copy package L"msxml.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"msxml.msi"

Any thoughts on how to get around this?

Thanks for any ideas,

Dan

---

### Post by jimv on 2008-04-25
Try renaming your drive_c folder in the .wine directory to harddiskvolume0.  After you rename it, make sure you go into Wine Config and update the mapping under the Drives tab.

---

### Post by WeeManDan on 2008-04-25
Where can I rename it as when I run winecfg I now get the error:

Warning: the specified Windows directory L"C:\\windows" is not accessible.
Warning: the specified System directory L"C:\\windows\\system32" is not accessible.

Thanks,

Dan

---

### Post by WeeManDan on 2008-04-25
Found a way to rename it, just created a new link under the dosdevices folder ran winecfg and it all looked fine but when trying to run msiexec /i msxml.msi I still got the error:

err:msi:copy_package_to_temp failed to copy package L"msxml.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"msxml.msi"

Dan

---

### Post by jimv on 2008-04-25
I'd try installing MSXML through WineTricks.

Go here to get it:
[http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

Just copy all the text on that page into a text file called "winetricks"

Then, open a terminal and go to the folder you made that file in.  Type "sh winetricks".  In the window that pops up, check all the msxml stuff and click install.  After it's done, try the Office 2007 install again.

---

### Post by WeeManDan on 2008-04-25
Thanks that worked great :)

Just one little problem now, it's installed but when I try to run it I get a Microsoft Visual C++ Runtime Library Error saying:

Program: C:\Program Files\Microsoft Office\Office12\WINWORD.EXE

R6034
An application has made an attempt to load the C runtime library incorrectly.
Please contact the applications's support team for more information.

Any thoughts?

Thanks for the help so far,

Dan

---

### Post by WeeManDan on 2008-04-25
Managed to fix it by installing some more of the winetricks, thanks :D

Dan

---

### Post by WeeManDan on 2008-04-25
Annoyingly it was working and now I get the following: 

fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:system:SetProcessDPIAware stub!
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.

Any ideas?

Dan

---

### Post by RyanKage on 2008-04-26
Hey man, I was wondering if you could write up a review (an easy one lol) on how to get it to work in 8.04. I plan on installing Ubuntu on this desktop soon and I'm sick of Open Office. I know I'll probably run into a bunch of problems because I'm still kind of a newbie with Ubuntu... Thanks in advance!

---

### Post by stinger30au on 2008-04-26
i dont understand why you would need office 2007 when you can have open office for free and with out the install hassle.

can you please explain your reasoning behind this ???

---

### Post by WeeManDan on 2008-04-26
RyanKage, I will do when I get it running! I kind of broke it, it was working but then I got a little carried away and things started to go wrong at that point!

Stinger30au, I've always found OpenOffice slow and sluggish compared to Office. I also quite like the ribbon and actually think that Office is one product that Microsoft got right recently. Finally, whilst there's no doubt a linux converter for it, I quite often get Office 2007 type docs to open so for convnience I want Office on Ubuntu.

Dan

---

### Post by ugm6hr on 2008-04-26
> **stinger30au said:**
> i dont understand why you would need office 2007 when you can have open office for free and with out the install hassle.

can you please explain your reasoning behind this ???

This is a common question in threads like this.

I have been using Linux almost exclusively for about a year now, and find booting into Windows a pain.  I also use FOSS almost exclusively now (in Ubuntu).

However, there are still rare occasions when Windows is necessary for me, and the main one is Office.

Office 2007 is available for under £20 to NHS employees in the UK, which is excellent value.  I would buy it if I knew it would work in Ubuntu without a lot of messing around (i.e. struggling with wine).

OO.org is excellent for most users, particularly with regard to word processing.  But the spreadsheet graphing options are rubbish compared to Excel (important when creating research posters for conferences, where visual impact is the key), Impress is much less intuitive than Powerpoint, and seems to put occasional carriage return marks at the end of lines when saved in ppt (which is necessary when presenting in hospitals using Windows unless I take my laptop everywhere with me)...

The ppt export problem is clearly a problem with Microsoft using proprietary formats, but the NHS powers don't care about that.  So from my personal perspective (i.e. for my needs), it means OO is not as good as Office.

So if anyone can successfully get 2007 working without requiring huge efforts, I'm definitely interested.

PS: Apologies if I am distracting from the support request here - but I just wanted to offer support to those people trying to get this sorted, and dissuade any further comments about how rubbish MS is.

---

### Post by SunnyRabbiera on 2008-04-26
> **WeeManDan said:**
> RyanKage, I will do when I get it running! I kind of broke it, it was working but then I got a little carried away and things started to go wrong at that point!

Stinger30au, I've always found OpenOffice slow and sluggish compared to Office. I also quite like the ribbon and actually think that Office is one product that Microsoft got right recently. Finally, whilst there's no doubt a linux converter for it, I quite often get Office 2007 type docs to open so for convnience I want Office on Ubuntu.

Dan

well if flashy effects like office 2007's ribbon is your main interest you really have no business using linux.
If office 2007 doesnt work for you what would that mean for you?
Granted open office can be sluggish sometimes but I rather have that then some bloated garbage of a office suite with a corrupt file format as its default...
There are other office like apps for linux if open office isnt quite doing it for you, you must understand that as a community we can only do so much.
I am hoping that not being able to run office 2007 will deter you, there are other office suites out there if you need them for linux other then OO.
have you tried koffice?
by default it runs smoother as it does not run java.

---

### Post by WeeManDan on 2008-04-26
I don't get your first comment about 'flashy effect's as I find the ribbon far more intuitive than the old style of bars. Also, is it wrong to want a nice enviroment to work in? If you're working on/in something for hours surely it makes sense for it to be as nice as possible. If not then why would Ubuntu ship with lots of customizable GUI features?

Out of curiosity do you know if OpenOffice has built in ODBC support? Will it happily speak to a Mocrosoft SQL Server?

ugm6hr resonates with me as well that I just don't think OO is there really and in the three main applications I use Word/Excel/Powerpont Office 2007 blows away OO. 

What do you find bloated in Office out of curiosity? I think I'd prefer OO to be larger and more complete and polished than the state it is in at the moment.

---

### Post by SunnyRabbiera on 2008-04-26
the thing is that my experiences it office 2007 was not so nice, I actually liked MS office XP better in many ways (though office 2000 was the best of the lot)

and open offices biggest weakness is java, but that wont be a weakness anymore, soon open office 3 will be out and java will be fully open source so we can make it lighter.

---

### Post by WeeManDan on 2008-04-26
Let me know when OO3 is out. I'm willing to give it a go by all means but right now Office 2007 does what I want and need for me.

---

### Post by SunnyRabbiera on 2008-04-26
and if it cant work in ubuntu then what?
I hope it wont deter you, its not our fault MS hates us.

---

### Post by ugm6hr on 2008-04-26
> **WeeManDan said:**
> Finally, whilst there's no doubt a linux converter for it, I quite often get Office 2007 type docs to open so for convnience I want Office on Ubuntu.

In case you need to open in OO.org - it can be done (apparently):
[http://ubuntuforums.org/showthread.php?t=698711](http://ubuntuforums.org/showthread.php?t=698711)

This isn't an issue for me, so haven't tried it.

> **SunnyRabbiera said:**
> I hope it wont deter you, its not our fault MS hates us.

From my point of view, OO does almost what I need.  Hence I use it.

It just isn't good enough for *everything* I need it to do.

As a whole package though, Ubuntu is still my preference.  But I can't wean myself off a dual-boot for those once every month or two requirements.

---

### Post by WeeManDan on 2008-04-26
If it can't work on Ubuntu then I guess I'll just have to keep with dual boot but for everything else (so far, that I can think of) I'll be spending my time in 8.04

Dan

---

### Post by SunnyRabbiera on 2008-04-26
well like i said openoffice is not the only office app for linux, try koffice and use it to export your doccuments to odt files and only use open office as a swing between... or try abiword, its not a full office suite but its good for word documents.

---

### Post by WeeManDan on 2008-04-26
I'll try them, do you know if they have support for ODBC?

---

### Post by WeeManDan on 2008-04-28
Hi all,

As I got asked earlier in this thread to do a 'how to' here it is, well this is how I successfully got Office 2007 working:

[LIST=1]
[*]Install Wine - sudo apt-get install wine
[*]Follow the instructions [here]("http://wiki.winehq.org/PreloaderPageZeroProblem"), I suggest making the permanent file change as else you'll have to run it after every reboot
[*]At the terminal run winecfg and change the under libraries change rpcrt4.dll and msxml3.dll to Windows native.
[*]Go to /home/username/.wine/drive_c/windows/system32 and delete the two dll's above
[*]Add this [dll]("http://www.mediafire.com/?njtut9aswdk") to the folder above
[*]Get [this text]("http://www.kegel.com/wine/winetricks"), save it to a file locally and run the file by sh filename
[*]When this runs, select the 3 msxml options and let the installs for these run
[*]Now run setup.exe from your Office 2007 installation disk
[*]Following this, run the winetricks script from before again and run dotnet2
[*]All being well, success!
[/LIST]

Hopefully this will work for you, this is the order I did and it works for me now, if you run into any difficulties let me know and I'll help where I can.

Also, following installation you might notice that you can't access all the shortcuts as the GNOME window gets in the way, you can get around this by disabling 'Allow the window manager to control the windows' in the wine config.

Hope this helps,

Dan

---

### Post by VMan on 2008-04-29
Thanks; by following your detailed instructions, I was able to get Office 2007 installed.  I just tested Word and Excel.  Both started and I was able to perform simple tasks.  I will be finding out how well they work (and how stable) in the near future.  PowerPoint did not start.  Those are the only apps I need out of the MS Office suite.

---

### Post by WeeManDan on 2008-04-29
Ok, so far I've only tested Word and Excel but I'll have a look at Powerpoint and post back in a bit.

---

### Post by the8thstar on 2008-05-03
Has anyone tried Powerpoint? Does it work?

---

### Post by Kinst on 2008-05-03
Yes powerpoint works. However it won't work for actually viewing slideshows. To do that you can use powerpoint viewer, which works fine.

If you're having trouble with powerpoint try this:

```
wget http://www.kegel.com/wine/winetricks
sh winetricks riched20 riched30
```

---

### Post by corticalaxon on 2008-05-03
> **WeeManDan said:**
> Managed to fix it by installing some more of the winetricks, thanks :D

Dan

What did you install from winetricks and how did you do it (exactly what did you enter into terminal)?

I have the same error when I try to open programs, although I already have the msvcr80.dll file and msxml3 files.

I am a linux novice, so I can't interpret what you're saying when you mean you installed more from winetricks.

---

### Post by WeeManDan on 2008-05-04
Ok corticalaxon, what you need to do is go to [this page]("http://www.kegel.com/wine/winetricks") and copy all the text. Then create a new document and paste the text and save it (without a file extension), I saved mine as winetricks. In a terminal navigate to the folder where you saved the text and type type sh winetricks or whatever you called it and a dialogue type box should come up and just tick the boxes of the features you want to install.

Hope that helps,

Dan

---

### Post by corticalaxon on 2008-05-04
Yes, that did work to open the dialog box with the installs...

so I installed dotnet2 and msxml3, and now ms office 2007 is actually recognized and filed under wine, and but whenever I start any of the office apps, I get an error message saying it has encountered a problem and needs to shut down - the dialog box that asks you if you want to send an error report to microsoft. I believe I read about this problem in earlier posts, and I'm guessing the solution may be to install a few more winetricks. I also went into winecfg and changed the windows version to vista (from 2000), vista being the other OS I have, but that didn't solve it. Then again, I didn't restart my computer -- maybe I'll try that, and then perhaps some more winetricks.

Edit: Unfortunately the restart didn't work. Now when I load word, nothing even happens. the loading cursor comes up for a while, and then goes away and nothing happens. Perhaps additional winetricks would help...

Yep --- I'm kinda lost once again....I re-added "vista" and "richedit20," which were familiar terms with wine, using winetricks, didn't work..

---

### Post by Winsbreaker on 2008-05-04
> **ugm6hr said:**
> 

OO.org is excellent for most users, particularly with regard to word processing.  But the spreadsheet graphing options are rubbish compared to Excel (important when creating research posters for conferences, where visual impact is the key), Impress is much less intuitive than Powerpoint, and seems to put occasional carriage return marks at the end of lines when saved in ppt (which is necessary when presenting in hospitals using Windows unless I take my laptop everywhere with me)...


I agree, OO.org is great for basic needs yet, I live in a MS Word and Excel dominated world, and as far as the ribbion goes I like it. It's very intuitive once you get use to it. But if anyone knows how to install MS Office 2007 without a lot of headaches please share.

---

### Post by the8thstar on 2008-05-04
Okay, I tried the method... I can get to the install screen and then it freezes. **[COLOR="Red"][SIZE="4"]HELP![/SIZE][/COLOR]**

---

### Post by cometa2k7 on 2008-05-04
I did get Office 2007 to run in Wine, but I recently updatd to Hardy, and it won't work, and I haven't had much time to be honest.

I did run Word, several times, I ran Excel, but didn't use it, but I couldn't get PowerPoint of OneNote to work, which is no big loss to me.

At the time I had Gutsy, with Wine 0.9.59, I think. And I used this tutorial [http://wine-review.blogspot.com/2008/03/office-2007-on-linux-with-wine-install.html]("http://wine-review.blogspot.com/2008/03/office-2007-on-linux-with-wine-install.html").

I haven't downloaded the CrossOver Games again, to get the files needed, but I have tried it in Ubuntu, with the files tat I copied from my .wine directory before I switched, and it didn't work.

It's pretty similar to the technique used in the first post actually.

---

### Post by WeeManDan on 2008-05-04
corticalaxon it sounds like you've got stuck in the same position I did, as I had a new instsall and hadn't really set too much up I just did a reinstall, sorted it all out.

Dan

---

### Post by x00n on 2008-05-04
I followed Dan's tuto and manage to install office 2007 suite....
I tried Word and it works really nice, but when onenote crashes when I open/create new notebook. I would really like to get onenote working because I take class notes on onenote and powerpoint too.

UPDATE: I'm so stupid, followed this and both works pretty well

```
wget http://www.kegel.com/wine/winetricks
sh winetricks riched20 riched30
```

---

### Post by the8thstar on 2008-05-04
I can't make winetricks work. I get an error message every time:

> Winetricks error: Note: command 'wine regedit /home/the8thstar/.wine/drive_c/winetrickstmp/geckopath.reg' returned status 1. Aborting.

Bummer.

---

### Post by corticalaxon on 2008-05-05
By new install, you mean a new Ubuntu install or a new office install? (I'm guessing the latter). I'm assuming you mean that because I hadn't used winetricks before, I didn't have much of the stuff installed added. Which is true. 

So by reinstalling, what do you suggest? Deleting the whole office suite and winetricks and reinstalling everything? Or keeping office suite but installing every single winetrick (just to make sure that I might get one that is relevant to office and might make it work, because I don't know what any of them do)? If I was to delete and reinstall, or reinstall in general, how would I go about doing that? I'm assuming it would be through terminal, but I don't know.

---

### Post by MadsRH on 2008-05-05
Does anyone know if the Wine team are planning to make Word 2007 (or Office2007) run on Wine without any workarounds?

I tried the guide too, but I get a "...You need Windows 3.1 or later to run..." message! :(

I really hope someone will make an easy way to make this work for us Linux newbies.

[B]
MadsRH[/B]

---

### Post by Kinst on 2008-05-05
> 
I tried the guide too, but I get a "...You need Windows 3.1 or later to run..." message! If you got that message you need to open winecfg and switch to windows XP or windows Vista mode.





Okay, for people using Onenote:

Do this and it should fix most of the onenote bugs, you should be able to see all notes perfectly (like on the getting help with onenote slide you should see an arrow) and you should be able to use the line, shape and arrow tools.

[LIST]
[*]Put a native copy of MSVP60.DLL and GDIPLUS.DLL in the /windows/system32 folder.
[*]You can get a copy from these spots (I hope): [http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60]("http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60")
and [http://www.dll-files.com/dllindex/dll-files.shtml?gdiplus]("http://www.dll-files.com/dllindex/dll-files.shtml?gdiplus")
[*]Make gdiplus.dll native only for onenote.
[*]Tell me if this works.
[/LIST]

The only thing that doesn't work still is the ink tool. I've tried to figure that out with no luck. Also this will work best with wine 0.9.58.

---

### Post by WeeManDan on 2008-05-06
Sorry corticalaxon I meant a new Hardy install, I got frustrated by it and as it only took 20 mins to install last time just did a complete re-install as I got into a loop of errors where I'd been installing the wrong stuff etc

---

### Post by corticalaxon on 2008-05-06
OK...I can probably do that...what would you then recommend installing to make office actually work? Did you follow a particular tutorial, etc?

---

### Post by WeeManDan on 2008-05-06
If you go to page 3 on here and follow my instructions that should get you all set up :)

---

### Post by MadsRH on 2008-05-07
The guide on page 3 worked perfectly for me :)
I'm really surprised how fast Word 2007 runs. It takes only seconds from when I click the Word 2007 icon, until it is ready for writing :D Compared to Vista witch is about 15-20 seconds to load it!

The only thing is (and this is not just Word) that the text is kind of hard to read. Especially compared to running Word in Vista. This is also a problem in Firefox. Does anyone know if the is because of my display driver or what???

Anyway, now I have all my windows programs running on 8.04 (PhotoShop, Word2007, Finale) - thank you so much!

**MadsRH**

---

### Post by pencilcheck on 2008-05-08
A command to the installation on page 3....
I don't need netdot20 to install and I reverse the override instructions steps.

---

### Post by Kinst on 2008-05-10
Hey guys! The new version of wine (0.9.62) fixed all the regressions. It looks like 1.00 is going to be a very good release indeed.

---

### Post by MadsRH on 2008-05-12
Hi
I just tried the guide from page 3 with the Wine rc1, and now it freezes at 50%!!! :confused:

Can anyone help???

---

### Post by le_vainqueur on 2008-05-13
> **the8thstar said:**
> I can't make winetricks work. I get an error message every time:



Bummer.

I received a similar error on setp #9, but I was able to run Office anyway.  I would suggest you give it a try.  I would be curious to know the meaning of this error, though, if anyone has that information


LV

---

### Post by cometa2k7 on 2008-05-15
> **MadsRH said:**
> Hi
I just tried the guide from page 3 with the Wine rc1, and now it freezes at 50%!!! :confused:

Can anyone help???

I get that freeze with Wine 0.9.62. It annoying, because starts the instal, everything works fine, it just jams just past 50%, and won't continue. You also can't cancel it, so I have to force it to quit.

---

### Post by WeeManDan on 2008-05-15
Sorry I haven't tried the install with this version of WINE, if I get the opportunity I'll give it a go

Dan

---

### Post by oninjao on 2008-05-15
wow very peculiar it installed instantely for me

---

### Post by VMan on 2008-05-15
Although I got Office 2007 (Word and Excel) to work under an earlier version of Wine, I couldn't get it to work under the newer versions.  The two versions prior to release candidate one didn't work.  The two versions prior to that worked.  This is of course relying on my less than perfect memory.  I haven't had time to try out anything under rc1 yet.  Maybe this weekend I will be able to give a report on that.  Sit back, grab some :popcorn: and I'll eventually have some information.

---

### Post by MadsRH on 2008-05-16
I removed the Wine rc1 and installed the version that comes default with 8.04 - that did the trick!

I really hope MS Office 2007 will work with the final Wine release.

---

### Post by Redscare on 2008-05-17
Please help. I followed the directions to the letter, but when I install i get errors and the install crashes at the setup...initializing files stage. Then i get the send/do not send error report dialog. I am running Ubuntu 8.04 with the default wine version. Here is the output:
```
redscare@redscare-desktop:/media/20070509_184613$ wine setup.exe
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:system:SetProcessDPIAware stub!
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:richedit:REExtendedRegisterClass semi stub
fixme:richedit:RichEditWndProc_common EM_SETEDITSTYLE: stub
fixme:richedit:RichEditWndProc_common EM_SETBIDIOPTIONS: stub
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:richedit:RichEditWndProc_common EM_SETEDITSTYLE: stub
fixme:richedit:RichEditWndProc_common EM_SETBIDIOPTIONS: stub
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:richedit:RichEditWndProc_common EM_SETEDITSTYLE: stub
fixme:richedit:RichEditWndProc_common EM_SETBIDIOPTIONS: stub
fixme:hook:IsWinEventHookInstalled (32785)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32785)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:richedit:RichEditWndProc_common EM_SETEDITSTYLE: stub
fixme:richedit:RichEditWndProc_common EM_SETBIDIOPTIONS: stub
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32785)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32785)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32785)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
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
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
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
fixme:hook:IsWinEventHookInstalled (32772)-stub!
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
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
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
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
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
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
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
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:reg:GetNativeSystemInfo (0x32d9a8) using GetSystemInfo()
fixme:advapi:CheckTokenMembership ((nil) 0x1a7440 0x32d9a8) stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
err:msi:MSI_OpenDatabaseW unknown flag 0x20
fixme:htmlhelp:HtmlHelpW HH case HH_UNINITIALIZE not handled.
fixme:powrprof:DllMain (0x7df50000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:netapi32:NetGetJoinInformation Stub (null) 0x32f0dc 0x32f0d0
fixme:advapi:CheckTokenMembership ((nil) 0x164638 0x32f0b8) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x164638 0x32f0b8) stub!
fixme:powrprof:DllMain (0x7df50000, 0, (nil)) not fully implemented
redscare@redscare-desktop:/media/20070509_184613$ err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:imm:ImmDisableIME (-1): stub
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00001388,(nil),0x000b,0x00000124,0x300bcf54,0x7e1349fc): stub
err:eventlog:ReportEventW L"office12setup"
err:eventlog:ReportEventW L"{10120000-0f00-0000-0000--0000000ff1ce}"
err:eventlog:ReportEventW L"12.0.4518.1014"
err:eventlog:ReportEventW L"x"
err:eventlog:ReportEventW L"msiapicallfailure"
err:eventlog:ReportEventW L"enterprise.ww_enterpriseww.xml"
err:eventlog:ReportEventW L"x"
err:eventlog:ReportEventW L"x"
err:eventlog:ReportEventW L"NIL"
err:eventlog:ReportEventW L"NIL"
err:eventlog:ReportEventW L"NIL"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:reg:GetNativeSystemInfo (0x33fc5c) using GetSystemInfo()
fixme:powrprof:DllMain (0x7e020000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7e020000, 0, (nil)) not fully implemented
fixme:netapi32:NetGetJoinInformation Stub (null) 0x33fc84 0x33fc78
fixme:advapi:CheckTokenMembership ((nil) 0x163608 0x33fc60) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x163608 0x33fc60) stub!

```

---

### Post by ergoen on 2008-05-19
I'm getting the same error as above, could it be something about user rights? (Cause it looks like some database cannot be opened "err:msi:MSI_OpenDatabaseW unknown flag 0x20"?

---

### Post by splitsch on 2008-05-21
Hello !
I have the exact same error here...

(for the first error, it is linked to winbind: sudo apt-get install windbind )

But about err:msi:MSI_OpenDatabaseW unknown flag 0x20, i don't know...

Any clue?

Thanks

---

### Post by bblagoev on 2008-05-21
exactly the same here

---

### Post by Redscare on 2008-05-21
I fixed it by downloading the trial off the site then entering the key.

---

### Post by corticalaxon on 2008-05-21
Ok...weemeedan, I reinstalled ubuntu (although now the actual vista partition doesn't exist anymore)....and I followed all of your steps exactly up until the installation step, but when I put in office 2007 and click on setup.exe, it says there is an error and it brings up the "Please tell microsoft/don't send" screen.

---

### Post by LaSaDa on 2008-05-22
I have managed to install the best office suite on the market (office 2007, and if someone reading this disagrees, then they shouldn't be reading this)

Everything works as it should except for one thing i really need; the equation editor in word. I use it for almost all my math homework and a lot of chemistry to.

Is there anyone that has a trick or two left in the pocket?

---

### Post by Kinst on 2008-05-22
No one has ever figured out equation editor. People try. Hell you could try, just open things in the terminal and guess what the readout means.

---

### Post by _DD_ on 2008-05-28
EDIT: ok, working now :D

---

### Post by johsch on 2008-06-17
OK you lucky people who have this running (assuming you haven't all left cause you don't need to read this forum anymore):

What version of Wine exactly?
Which rpcrt4.dll did you use? Compiled? XP? Vista?
What flavor of Windows set in winecfg? For setup.exe? For running Office?
Which winetricks did you install? dotnet20? riched20? riched30? ..?

There are so many combinations of these things that it helps to get specific on some of them at least.

_DD_?  LaSaDa?

---

### Post by arcik on 2008-06-18
Hello everybody!

This is how it looks on my PC:

Following the guide I found at [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992), I installed the software with no problems. Powerpoint seems to work all right. Word only until you start typing, which makes it pretty useless.

I tried everything recommended in this thread and feel pretty tired right now. Tomorrow, I am leaving for a business trip to Poland and hope to find a solution when I am back on Sunday.

If anybody has encountered a similar problem and found a solution, please let me know.

Thanks in advance and enjoy the beginning summer (if you are in the Northern hemisphere)!

Wine: 1.0
Ubuntu: 8.04

---

### Post by crjackson on 2008-06-18
Okay - I'm subscribed to and watching this thread also.  I MUST use Office 2007 for the wifes school classes.  I do use OOo for most things, but I must begrudgingly admit that 2007 is a more polished program set.  I don't like the propriotary junk in principal, but it just works better and fits in more seamlessly with mainstream business / school needs.

Don't hate on me for this, but if a Linux version were made, I would buy it without hesitation.  By the same token, if OOo could and would produce a suite that actually MATCHES all the functions with full compatiability, I would gladly buy their wares instead.

---

### Post by arashiko28 on 2008-06-28
Mine is stuck from the beginning it has been 2 hours now since I started following this tutorial. I get this message constantly repeating itself > fixme:xrender:X11DRV_AlphaBlend not a dibsection
 on the other side, the dotnet20 gave me only 2 choices, repair and uninstall, i chose repair, but it's also at 0% with this message: 
> Setting Windows version to win2k
Executing wine regedit /home/****/.wine/drive_c/winetrickstmp/set-winver.reg
Executing cp -f /home/****/.winetrickscache/dotnet20/l_intl.nls /home/****/.wine/drive_c/windows/system32/
Executing wine /home/****/.winetrickscache/dotnet20/dotnetfx.exe
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advapi:LsaOpenPolicy ((null),0x33f3c0,0x00000001,0x33f3e8) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LookupAccountNameW (null) L"****" (nil) 0x7e1df4f8 (nil) 0x7e1df4fc 0x7e1df4f0 - stub
fixme:advapi:LookupAccountNameW (null) L"****" 0x14fff0 0x7e1df4f8 0x150140 0x7e1df4fc 0x7e1df4f0 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"


any ideas?

---

### Post by Kinst on 2008-06-28
Yes. You have a bad rpcrt4. I had one of those from vista.

---

### Post by arashiko28 on 2008-06-28
Well... Can I use one from a windows XP computer that used to have office 2007 installed?

Now that I remember, this one I got it from the link on this same post, the 3rd page tutorial.

---

### Post by Kinst on 2008-06-29
Totally. Course there's no guarantee it'll work, this process is very delicate sometimes. I had one rpcrt4 from xp that worked fine with wine 0.9.58 but it doesn't work for the later versions. I started looking today for one that works well with the latest wine.

---

### Post by johsch on 2008-06-29
Well, well, well.  I have Word 2007 running beautifully (except for problems like the equation editor which has been reported before).  All I did was to reinstall Wine 0.9.58-0ubuntu4 (trying to follow madsRH's advice).  Here's my theory of what really happened:

To *install* Office 2007, you need a native rpcrt4.dll from somewhere (various guides suggest various sources) and override it as Windows native in winecfg.  See WeeManDan's post on page 3: [http://ubuntuforums.org/showthread.php?p=4826323](http://ubuntuforums.org/showthread.php?p=4826323) With luck, setup.exe should run from the Office CD and install what you want.  However...

To *run* Office 2007, you need to go back into winecfg and set rpcrt4.dll back to Wine builtin.

This crucial step has been missing from most of the guides, but it is now clearly stated in the latest recipe on the Wine AppDB page [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

I don't think the actual version of Wine matters much.  People have reported success with different versions.  I suspect much confusion was caused by people doing what I did and thinking that they had fixed it by installing a different version of Wine, when all that really mattered was that rpcrt4.dll reverted to Wine builtin.

I am going to test my theory with a fresh installation of everything.  I'll let you know how it goes.

---

### Post by rdiaztushman on 2008-06-29
After getting frustrated at a number of failed Office2007 installations, I finally got it but needed to do much more than any single tutorial said.  So, I've collected it all here:

[http://ubuntuforums.org/showthread.php?t=844309](http://ubuntuforums.org/showthread.php?t=844309)

Hope it helps!

---

### Post by johsch on 2008-07-06
Word 2007 (the only app from MS Office I'm interested in) is still working after I updated wine to 0.9.59-0ubuntu5 (the latest version from the ubuntu repos).  I think the latest recipes (see above and on the Wine AppDB site) have the right idea.

Something else to be aware of: Codeweavers [http://www.codeweavers.com/](http://www.codeweavers.com/) have recently released Crossover Office 7 which supports MS Office 2007.  The Linux version is about $40 which may be well worth the time you'll save.  Codeweavers are a major supporter of Wine.

---

### Post by nik fariza on 2009-06-01
i waan to know,if there any other network manager tool other than wine and crossover lunix to install microsoft office 2007?
...i want to do thin client to my PC so i need to install network manager that can easily install application in one places without install for each PC

---

### Post by nwarrenfl on 2009-06-01
You must install it with Wine 1.x, because with the latest versions it is broken :(
Then you can just use the latest Wine, you'll see it runs fine.

Can nobody fix that? It was running fine in the past, is there any skilled developer who could try to fix it, please... ;)

---

### Post by jhoeijao on 2009-06-02
> **nwarrenfl said:**
> You must install it with Wine 1.x, because with the latest versions it is broken :(
Then you can just use the latest Wine, you'll see it runs fine.

Can nobody fix that? It was running fine in the past, is there any skilled developer who could try to fix it, please... ;)

I'm not an expert but give this a try, [http://ubuntuforums.org/showthread.php?t=1173365](http://ubuntuforums.org/showthread.php?t=1173365)

> **nik fariza said:**
> i waan to know,if there any other network manager tool other than wine and crossover lunix to install microsoft office 2007?
...i want to do thin client to my PC so i need to install network manager that can easily install application in one places without install for each PC

I've been researching on that too but what I i came up with OFFLINE MSOFFICE 2007 installation all the needed files are saved in one file folder with a complete guide.

---

