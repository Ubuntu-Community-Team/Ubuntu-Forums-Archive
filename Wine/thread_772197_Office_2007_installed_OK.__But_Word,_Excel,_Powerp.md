---
title: "Office 2007 installed OK.  But Word, Excel, Powerpoint all crash on load..!!"
date: 2008-04-28
forum: Wine
---

### Post by rtandon87 on 2008-04-28
Hi,

I am using Ubuntu 8.04 and have Wine 0.9.60 installed.
I followed the instructions here to install Office 2007.
[http://www.quicktweaks.com/2008/04/0...2007-in-linux/](http://www.quicktweaks.com/2008/04/0...2007-in-linux/)

Everything installed properly.

After the install finished I changed wine config to Windows XP and now, when I try to open anything - word, excel, powerpoint or onenote....
IT CRASHES with error:
Microsoft Office Word encountered a problem and needs to close. We are sorry for the inconvenience.

PLEASE HELP.

---

### Post by situz on 2008-04-28
sorry for being offtopic and not really helpful, but is there any good reason to why you want ms office?

imo openoffice, which is included in ubuntu, works fine =)

why did you change windows version to xp btw?
 
come to think of it, cd into your office installation directory in a terminal, you should be in this dir, i think
> ~/.wine/drive_c/Program Files/Microsoft Office/Office12$
then type a command like this:
> wine WINWORD.exe

post the output of this please

---

### Post by Joeb454 on 2008-04-28
The link in the original post is broken :(

I found it anyway so if anybody wants to check the instructions followed by the OP - [check here]("http://www.quicktweaks.com/2008/04/09/install-ms-office-2007-in-linux/") :)

---

### Post by Kinst on 2008-04-28
Installing it as Windows vista has always been really buggy for me. I'd remove the .wine folder, reinstall wine and start over as windows xp.

---

### Post by timcredible on 2008-04-28
is there something specific that openoffice doesn't do that ms office does?  if you post what doesn't work, maybe someone has a solution, then you don't have to go through the hassle of trying to get ms office working.

---

### Post by wingnux on 2008-04-28
Geez! Haven't you ever heard of OpenOffice??

---

### Post by rtandon87 on 2008-04-28
I am so new to Ubuntu Forums.  Can someone please tell me if there is a way I can delete one of my own posts?

---

### Post by rtandon87 on 2008-04-28
> **Kinst said:**
> Installing it as Windows vista has always been really buggy for me. I'd remove the .wine folder, reinstall wine and start over as windows xp.

Ok I'll try doing that and see how that goes.
Thanks for the advice.  I'll post my results soon.

Rajat

---

### Post by rtandon87 on 2008-04-28
> **Kinst said:**
> Installing it as Windows vista has always been really buggy for me. I'd remove the .wine folder, reinstall wine and start over as windows xp.

Now that I installed office 2007 as Windows XP, when I open Word, I get an error:
Microsoft Visual C++ Runtime Library - Runtime Error!
R6034 An application has made an attempt to load the C runtime library incorrectly.

Here is what I see in the terminal:
[email]rajat@rajat-tablet:~/.wine[/email]/drive_c/Program Files/Microsoft Office/Office12$ wine WINWORD.EXE
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Microsoft Office\\Office12\\WINWORD.EXE" failed, status c0000142

--------------------------------------------------------------------------------------

UPDATE: I installed all the vbruns and .net2.0 using winetricks and now I am back to square one.
When I try to open anything - word, excel, powerpoint or onenote....
IT CRASHES with error:
Microsoft Office Word encountered a problem and needs to close. We are sorry for the inconvenience.
 
Rajat

---

### Post by rtandon87 on 2008-04-28
Do I need to have anything else in the libraries besides msxml3 - windows(native) and rpcrt4 - windows(native)?

Rajat

---

### Post by WeeManDan on 2008-04-28
Have you tried running wine winword.exe from the terminal? 

You might find there's an error there and you need to install msxml another way, also you might need to install .Net2

Dan

---

### Post by rtandon87 on 2008-04-28
> **situz said:**
> 
 [HTML][/HTML]
come to think of it, cd into your office installation directory in a terminal, you should be in this dir, i think

then type a command like this: wine WINWORD.EXE

post the output of this please

Here is what my terminal looks like:
[HTML]rajat@rajat-tablet:~/.wine/drive_c/Program Files/Microsoft Office/Office12$ wine WINWORD.EXE
fixme:advapi:RegisterEventSourceA ((null),"MDM"): stub
fixme:advapi:RegisterEventSourceW (L"",L"MDM"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0xc0001002,(nil),0x0000,0x00000000,(nil),0x7e55d9e0): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:advapi:CheckTokenMembership ((nil) 0x132cb8 0x32e918) stub!
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x000007d1,(nil),0x0002,0x00000000,0x32f2ac,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000007d1,(nil),0x0002,0x00000000,0x13b9f8,(nil)): stub
err:eventlog:ReportEventW L"Microsoft Office Word"
err:eventlog:ReportEventW L"Word failed to start correctly last time.  Starting Word in safe mode will help you correct or isolate a startup problem in order to successfully start the program.  Some functionality may be disabled in this mode.\n\nDo you want to start Word in safe mode?"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:psdrv:PSDRV_DeviceCapabilities DC_BINADJUST: stub.
fixme:psdrv:PSDRV_DeviceCapabilities DC_BINADJUST: stub.
fixme:psdrv:PSDRV_ExtEscape QUERYESCSUPPORT(25) - not supported.
fixme:psdrv:PSDRV_DeviceCapabilities DC_BINADJUST: stub.
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:imm:ImmReleaseContext (0x10054, 0x138f88): stub
wine: Call from 0x7b844440 to unimplemented function rpcrt4.dll.I_RpcExceptionFilter, aborting
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Sessions"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00001b59,(nil),0x0006,0x00000000,0x32c444,(nil)): stub
err:eventlog:ReportEventW L"0"
err:eventlog:ReportEventW L"Microsoft Office Word"
err:eventlog:ReportEventW L"12.0.4518.1014"
err:eventlog:ReportEventW L"12.0.4518.1014"
err:eventlog:ReportEventW L"2"
err:eventlog:ReportEventW L"0"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:imm:ImmDisableIME (-1): stub
fixme:powrprof:DllMain (0x7e190000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:thread:NtQueryInformationThread Cannot get kerneltime or usertime of other threads
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:powrprof:DllMain (0x7e190000, 0, (nil)) not fully implemented
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Diagnostics"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x000000c9,(nil),0x0000,0x00000000,0x604000,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:OpenEventLogW ((null),L"Application") stub
fixme:advapi:CloseEventLog (0xcafe4242) stub
fixme:advapi:OpenEventLogW ((null),L"System") stub
fixme:advapi:CloseEventLog (0xcafe4242) stub
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Diagnostics"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x000000d5,(nil),0x0000,0x00000000,0x604000,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:OpenEventLogW ((null),L"Microsoft Office 12 Sessions") stub
fixme:advapi:ReadEventLogW (0xcafe4242,0x00000009,0x00000000,0x930000,0x0007d000,0x33fdc4,0x33fdcc) stub
fixme:advapi:CloseEventLog (0xcafe4242) stub
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Diagnostics"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000140,(nil),0x0002,0x00000000,0x649010,(nil)): stub
err:eventlog:ReportEventW L"2kgl"
err:eventlog:ReportEventW L"N/A"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Diagnostics"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x000000cd,(nil),0x0000,0x00000000,0x604000,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Diagnostics"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x000003e7,(nil),0x0000,0x00000000,0x604000,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:reg:GetNativeSystemInfo (0x33fddc) using GetSystemInfo()
fixme:powrprof:DllMain (0x7e130000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7e130000, 0, (nil)) not fully implemented
fixme:netapi32:NetGetJoinInformation Stub (null) 0x33fe04 0x33fdf8
fixme:advapi:CheckTokenMembership ((nil) 0x138110 0x33fde0) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x138110 0x33fde0) stub!
[email]rajat@rajat-tablet:~/.wine[/email]/drive_c/Program Files/Microsoft Office/Office12$ fixme:reg:GetNativeSystemInfo (0x33fc5c) using GetSystemInfo()
fixme:powrprof:DllMain (0x7e070000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7e070000, 0, (nil)) not fully implemented
fixme:netapi32:NetGetJoinInformation Stub (null) 0x33fc84 0x33fc78
fixme:advapi:CheckTokenMembership ((nil) 0x13a2f0 0x33fc60) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x13a2f0 0x33fc60) stub![/HTML]

Rajat

---

### Post by doorknob60 on 2008-04-29
UNless you have a really good reason not to, try this: Applications -> Office -> Progam of your choice :)

---

### Post by Kinst on 2008-04-29
Hard to tell, but it doesn't look like it likes your rpcrt4.dll. Also there's a couple sometimes necessary things you can do that sometimes fix problems:

[LIST]
[*]Make riched20 and riched32 native, delete them from /.wine/drive_c/windows/system32 then install this: [http://media.codeweavers.com/pub/crossover/office/support/richedit30.exe](http://media.codeweavers.com/pub/crossover/office/support/richedit30.exe)
[*]Make sure you have a folder in /.wine/drive_c/Program Files that mentions the gecko engine.
[*]Run wine-doors once and then turn it off; it's initial configure thing changes some stuff.
[/LIST]

---

### Post by coolmanlg on 2008-04-29
It takes forever for Openoffice to come up. Its really heavy. I have increased the memory and also disabled java and it still take time to come up! Is there anything I can do to speed it up?

M$ Office interface is cleaner and I have been looking for ways to make the openoffice icons smaller like in M$ office. Can anybody here help?

Also, I have not been able to get mail merge feature to work. I can see the display of my fields like in words.

---

### Post by WeeManDan on 2008-04-29
Replace the rpcrt4.dll in system32 with [this one]("http://www.mediafire.com/?njtut9aswdk")

I got Office 2007 working and this is one step I had to do, you can see how I did it [here]("http://ubuntuforums.org/showthread.php?t=767423&page=3").

Dan

---

### Post by rtandon87 on 2008-04-30
> **WeeManDan said:**
> Replace the rpcrt4.dll in system32 with [this one]("http://www.mediafire.com/?njtut9aswdk")

I got Office 2007 working and this is one step I had to do, you can see how I did it [here]("http://ubuntuforums.org/showthread.php?t=767423&page=3").

Dan

I used the exact same rpcrt.dll that you are using..(downloaded from the same exact website.)

Rajat

---

### Post by rtandon87 on 2008-04-30
FINALLY GOT IT WORKING.. after spending close to 25 hours on it.

In short, simple solution... use wine 0.9.58 only.
I had problems with wine 0.9.59 and 0.9.60.  

Besides that...
Make sure you have .net 2.0 and msxml3 installed(using winetricks) before you start the setup for Office 2007. 
To get the powerpoint working you have to install riched 20 and riched 30 (using winetricks).

Rajat
:KS

---

### Post by seizer on 2008-05-02
rtandon87, what version of Ubuntu are you using? For Hardy Heron only 0.9.60 is supported by WineHQ. I've got one more question. What windows profile are you using? I've read somewhere that Vista profile is buggy and I'm getting the same error output as you used to.

---

### Post by Kinst on 2008-05-02
Actually I've been reinstalling and I've come to the same conclusion. 0.9.60 has a regression in it. 0.9.58 will work.

---

### Post by seizer on 2008-05-02
Is there any chance to install 0.9.58 on Hardy?  Package dedicated to Gutsy complains about libldap2, which is recently unavailable :(

---

### Post by johsch on 2008-06-29
I have it working with wine 0.9.59-0ubuntu4 that comes on the Hardy CD.  I'll soon test to see if updating to 0.9.59-0ubuntu5 (the latest from the ubuntu repositories) breaks it or not.  See the Wine AppDB page [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992) for the latest installation guide.

---

### Post by johsch on 2008-06-29
What I meant to say was that I also tried 0.9.58 on Hardy and got the same dependency problem you mentioned.  Judging by the number of people who say they have it working on later version of Wine, I would not bother with 0.9.58.

---

### Post by rdiaztushman on 2008-06-29
Got it all working with the newest Wine and Ubuntu:
[http://ubuntuforums.org/showthread.php?t=844309](http://ubuntuforums.org/showthread.php?t=844309)

HTH!

---

### Post by Nico0020 on 2008-06-29
I know a lot of people are asking why dont they just use open office.  I love open office, but I am a student and a major problem I run into is that sometimes when I have to print stuff on campus when converting the file to work on office07, problems come out of it.  I will be installing Office 07 later this month when I buy crossover finally just for that reason.

---

### Post by starcannon on 2008-06-29
I'm a college student as well, I've gotten to where I save my OOo documents in the latest MS .doc format available in the drop down menu.

On those very rare occasions where I must use MS Office Suite for some particular assignment, I just run a strip down version of WinXP in Virtual-Box and have a full Office install there, no dependency issues or other weirdness that way.

Anyway, go with the method that seems best for you, theres probably at least 3 ways to skin this particular cat, I like running it natively so to speak in a virtual box.

---

### Post by Random_Dude on 2010-04-17
I'm sorry for digging up this thread, but I've got a similar problem running powerpoint.
I've installed Office 2007 using wine and it works fine (so far), except for Powerpoint which crashes on startup.

Does anyone had the same problem?

Thanks :biggrin:


**EDIT:**
Nevermind, I found the answer here: [http://www.wine-reviews.net/wine-reviews/microsoft/office-2007-in-ubuntu-910-with-wine-1132.html](http://www.wine-reviews.net/wine-reviews/microsoft/office-2007-in-ubuntu-910-with-wine-1132.html)

All I had to do was this.
> Step 2. Download Winetricks

[LIST]
[*]wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
[/LIST]
 Step 3. Install Cabextract to run the Winetricks smoothly

[LIST]
[*]sudo aptitude install cabextract
[/LIST]
 Step 4. Run Winetricks

[LIST]
[*]sh winetricks
[/LIST]
 In the Winetricks window, install each of the following *individually*,  which means check & install one, then re-run Winetricks and do the  next:

* dotnet11
* gdiplus
* vb3run
* vb4run
* vb5run
* vb6run
* msxml3
* msxml4
* msxml6
* riched20
* riched30
* vcrun6

---

