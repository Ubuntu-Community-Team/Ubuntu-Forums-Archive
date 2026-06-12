---
title: "MSN with Wine"
date: 2007-09-10
forum: Wine
---

### Post by Julianito on 2007-09-10
Hi,

I'm trying to install MSN via Ubuntu and I got a "1603 error". Here are my logs : 
```

~/Desktop$ wine Install_Messenger.exe 
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:advapi:LookupAccountNameW (null) L"sarah" (nil) 0x33e8b4 (nil) 0x33e8b8 0x33e8ac - stub
fixme:advapi:LookupAccountNameW (null) L"sarah" 0x1bd500 0x33e8b4 0x172ab0 0x33e8b8 0x33e8ac - stub
fixme:shell:URL_ParseUrl failed to parse L""
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 7 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 7 ignored L"Upgrade" table values
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 2 ignored L"MsiAssembly" table values
fixme:msi:msi_unimplemented_action_stub StopServices -> 2 ignored L"ServiceControl" table values
fixme:msi:msi_unimplemented_action_stub RemoveRegistryValues -> 2 ignored L"RemoveRegistry" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 3 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub DeleteServices -> 2 ignored L"ServiceControl" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 4 ignored L"CreateFolder" table values
fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
fixme:shell:DllCanUnloadNow stub
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
err:ole:CoGetClassObject class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
err:ole:create_server class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {4e14fba2-2e22-11d1-9964-00c04fbbb345} could be created for context 0x15
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
This program tried to use a DOMDocument object, but
libxml2 support was not present at compile time.
fixme:ole:CoCreateInstance no instance created for interface {2933bf81-7b36-11d2-b20e-00c04f983e60} of class {2933bf90-7b36-11d2-b20e-00c04f983e60}, hres is 0x80004001
fixme:advapi:CheckTokenMembership ((nil) 0x16b1e8 0x33fc94) stub!
fixme:setupapi:CMP_WaitNoPendingInstallEvents 100
fixme:advapi:CheckTokenMembership ((nil) 0x16b1e8 0x33fa88) stub!
fixme:setupapi:pSetupGetGlobalFlags stub
fixme:wintrust:CryptCATAdminCalcHashFromFileHandle 0x40 0x33f320 0x33f994 0
fixme:wintrust:WinVerifyTrust (nil) {f750e6c3-38ee-11d1-85e5-00c04fc295ee} 0x33f2e4
fixme:crypt:CryptQueryObject 00000001 0x185998 00000004 0000000e 00000000 (nil) (nil) (nil) (nil) (nil) 0x33f9a0
fixme:setupapi:pSetupGetGlobalFlags stub
fixme:msxml:DllCanUnloadNow 
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
err:msi:custom_get_thread_return Invalid Return Code 203
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603
~/Desktop$ fixme:shell:DllCanUnloadNow stub

```

PS: I know about Gaim, aMSN, and others but my sister wants "this" application and it is the last thing that could block her to use Ubuntu so, if anyone can help, thanks. :-)

---

### Post by igster on 2007-09-10
This isn't necessarily helpful but I don't think MSN Messenger works with wine.  The Wine HQ AppDB has it rated as "Garbage".  See [http://appdb.winehq.org/appview.php?iAppId=127](http://appdb.winehq.org/appview.php?iAppId=127) for more details.

FWIW, have her give the alternatives a try. She may actually like them better.

---

### Post by Ferrat on 2007-09-10
aMSN has more or less the exakt same functions and there are skins to make it look just like the ordinary MSN

---

### Post by KhaaL on 2007-09-11
lets not forget Mercury IM, a crossplatform client with webcam-support and a lot of other features. far superior to microsofts client IMO!

---

### Post by Ebuntor on 2007-09-11
> **KhaaL said:**
> lets not forget Mercury IM, a crossplatform client with webcam-support and a lot of other features. far superior to microsofts client IMO!

Ditto, I've used it for years before i switched to Gaim/Pidgin. However IIRC Mercury is freeware but it's not open source. So if that's a problem for you you're better of with aMSN.

---

### Post by Ferrat on 2007-09-11
Mercury is good but it hogs resources due to running in Java enviro..

---

### Post by mostwanted on 2007-09-11
> **Ebuntor said:**
> Ditto, I've used it for years before i switched to Gaim/Pidgin. However IIRC Mercury is freeware but it's not open source. So if that's a problem for you you're better of with aMSN.

aMSN is ugly though, Tk's fault :)

Pidgin does MSN just fine if you don't need video chat and it's GTK.

---

### Post by Pikestaff on 2007-09-11
[KMess]("http://www.kmess.org/") is my preferred Linux version of MSN, it's certainly not perfect but I prefer it over aMSN personally... so you might give that a shot also.

---

### Post by Kundalinux on 2007-11-14
The Linux world is in need of a high class IM program! AMSN is a piece or crap. Try typing Chinese in there and you'll see what I mean. Besides, it's buggy. My favorite is Pidgin but still I am frustrated with the Linux IM programs. Not to mention webcam support. Oh God!

---

### Post by scrooge_74 on 2007-11-14
Kopete does a nice job with web cams. And Pidgin would probably be a lot further on the develpment road if it wasn't delay due to lawsuits pending on the heads of the developers

---

### Post by Vitamin-Carrot on 2007-11-14
Ive Got A Question..
Its A Really Good Question...
Its A Single Word Question...

WHY!!????

---

### Post by stuart.crouch on 2007-11-15
Ive Got An Answer...
Its A Really Good Answer...
Its A Single Word Answer...

BECAUSE!

:lolflag:

---

### Post by Vitamin-Carrot on 2007-11-15
Whats the point of using msn on wine when you have Pigeon or kopete?
 why would you double up on apps like that and waist your space and time.

if your that attached to it why dont you just use windows?

---

### Post by Beren Camlost on 2007-11-15
> **Vitamin-Carrot said:**
> Whats the point of using msn on wine when you have Pigeon or kopete?
 why would you double up on apps like that and waist your space and time.

if your that attached to it why dont you just use windows?

Why didn't you simply read the original poster's reasoning?

---

### Post by Vitamin-Carrot on 2007-11-15
I never really liked my sister enough to do somehting like that, kudos to him for trying but its not like the alternatives available takes a phd to use.

Yet another issue to over come for the linux world

The stigma that linux is too hard to use for your average joe/jane blogs.

---

### Post by stuart.crouch on 2007-11-16
Something that hasn't been mentioned is not having to play catch up.

Which IM has sharing folders?
Which IM has cameras working by default?
Which IM can play winks?
What happens if MS add something new?  

There is only one IM that can do all of these, and it isn't open source. You've got to wait whilst the all the linux clients play catch up, and lets be honest, they are a long way behind the feature list that MSN boasts.

If you get MSN working via WINE and microsoft add something new that your friends want to use, you'll be able to use it instantly too.

---

### Post by scrooge_74 on 2007-11-16
Things my friends, suppliers and customers use:

1. chat
2. file transfer (from time to time)
3. chat
4. video (once in a blue moon)
5. chat with jumping things (which I hate)

So what is a list ot things a IM client should have besides giving you the ability to connect to others, without beeing heavy on the resources.

Rember Open Source has to play catch because MSN is a closed program so everybody has to reverse engineer stuff

---

### Post by imon9 on 2007-11-16
i highly recommend emesene

[www.emesene.org](www.emesene.org)

Almost 1.0 now, file transfer is able to accept but not send at the moment, other function is being worked on too...very intensively develeped...

may interest those who doesnt like aMSN slow responds

---

### Post by Ubuninja on 2007-11-17
Just install internet explorer first via wine and then msn via wine (msn needs IE to function) and it should work. I can understand why the OP wants this as webcam and game support for the big instant messenger clients sucks in linux.  If your worried about the viruses that IE brings, simply don't use it as your browser, just let MSN use it and even if you do use it, 80% of the time viruses you get from IE when using wine, will only effect wine. I use pidgin mainly, but I do have MSN, Yahoo, AIM and other IM clients installed via wine, just incase someone wants to show me webcam. It's not great promotion for linux if every person who wants to webcam you, cannot. (Yes I know about mercury but it doesnt support all clients).

Warning though, windows programs take up a heck of a lot more space than linux ones. For example on my 40gb laptop which I've had linux installed on for 2 years, I've only used 25gb despite being a power user whereas on my vista machine with 120gb which I've had 6 months, I've already used 68gb.

Average windows program size = 1/4 a gigabyte
Average linux program size = a few megabytes

---

### Post by snowstorm167 on 2008-01-05
If u really want to use msn and not use wine there is always this to use and it has all of msn features    [http://webmessenger.msn.com/](http://webmessenger.msn.com/)  this is used right on the net so no install needed

---

### Post by snowstorm167 on 2008-01-05
I just tryed to use my web cam from this mess and there is no cam there

---

### Post by trash on 2008-01-05
Y'all seem to think it's so easy to convert a windows junkies LOL.

I have a couple of neighbors connected to my wireless, sadly MSN is incompatible with SOME wireless routers! After a week of searching for a solution I told them to download Amsn to see if the problems persisted, sure enough THEY ALL HATED IT! BUT it worked flawlessly.

For sure your best bet is the webmessenger thingy but just get her to try Amsn for a few days, she'll get used to the change... BTW Amsn 0.97 is WAY BETTER than the previous versions

---

### Post by mike-laptop-dot-local on 2008-01-05
I was in similar circumstances as the OP - my wife just *can't* do without the MSN voice chat (only voice 'blurbs' in aMSN right now).

I pacified her with a VirtualBox install of Windows and MSN.

And then gave strict instructions to ONLY use MSN in the Windows VM. :)

---

### Post by kurotenshi on 2008-01-14
So, no live messenger on Wine but I did manage to install MSN Messenger 7.5 and Plus! the problem now is that I can't write on the user name and password boxes. Any suggestion?

---

### Post by weblordpepe on 2008-01-15
What really??? 7.5?? How did you get that going????

---

### Post by provenzano on 2008-01-15
> **kurotenshi said:**
> So, no live messenger on Wine but I did manage to install MSN Messenger 7.5 and Plus! the problem now is that I can't write on the user name and password boxes. Any suggestion?

same i get it work but i can not write ....

---

### Post by kurotenshi on 2008-01-15
> **weblordpepe said:**
> What really??? 7.5?? How did you get that going????

Well, just downloaded it and installed, no more messing around. I use Wine 9.46 with XP simulation.

---

### Post by Dericu on 2008-01-26
Can anyone give the fix to not being able to type in the login window as I have the same problem??

---

### Post by Scorpion2k5 on 2008-02-02
I was able to get MSN Messenger 8.5 to install just fine one my computer with Ubuntu 7.`0 running Wine 0.9.53. 

Here is what I did:
1. I went to [www.oldversion.com](www.oldversion.com), and downloaded version 7.0 first.
2. Then I went ahead, and had IE4linux running with IE6 to install MSN Messenger, cause version 7.0 needs IE5.5 or better to run. 
3. Then I went ahead and installed MSN Messenger 7 as a "run" not Save. Otherwise it will say that you need to download Internet Explorer. 
4. While having IE4linux running with IE6 I then, installed MSN Messenger 7 without fail. 
5. Then I logged in with my screen name, MSN told me that I needed to update before logging in, so I clicked yes to update, and it install MSN Version 8 on my computer without fail.

Now I have MSN Messenger 8.x installed and it wasn't really all that hard... Once I found out the Wine has classified the MSN Messenger 8.x installer as garbage, when used with Wine, it was rather simple to decide to go with 7 first and then update to 8.x when it asked... LOL :guitar:

---

### Post by OHJOY90 on 2008-02-02
Just get her to use one of the other programs, just tell her it it's hard to get it working and even then you'd have to use an old version, and sometimes after a while because of security threats, depending on which version you use, you're forced to update, silly I know but true. Then suggest one of those other programs, aMSN, Pidgin, or Trillian. In that order, from best to last.

---

### Post by kurotenshi on 2008-02-03
> **Scorpion2k5 said:**
> I was able to get MSN Messenger 8.5 to install just fine one my computer with Ubuntu 7.`0 running Wine 0.9.53. 

Here is what I did:
1. I went to [www.oldversion.com](www.oldversion.com), and downloaded version 7.0 first.
2. Then I went ahead, and had IE4linux running with IE6 to install MSN Messenger, cause version 7.0 needs IE5.5 or better to run. 
3. Then I went ahead and installed MSN Messenger 7 as a "run" not Save. Otherwise it will say that you need to download Internet Explorer. 
4. While having IE4linux running with IE6 I then, installed MSN Messenger 7 without fail. 
5. Then I logged in with my screen name, MSN told me that I needed to update before logging in, so I clicked yes to update, and it install MSN Version 8 on my computer without fail.

Now I have MSN Messenger 8.x installed and it wasn't really all that hard... Once I found out the Wine has classified the MSN Messenger 8.x installer as garbage, when used with Wine, it was rather simple to decide to go with 7 first and then update to 8.x when it asked... LOL :guitar:

The problem is now worst. IE4linux installs with minor trouble but IE6 has many graphical abnormalities so as everything I open with it. Other software in wine and crossover are just fine. I have no toolbars, check boxes, buttons..... Compiz off and probs remain

Also tried something similar with crossover, IE6 installs ok but messenger tells me that the setup can't continue and to download the file from microsoft

---

### Post by Scorpion2k5 on 2008-02-21
> **kurotenshi said:**
> The problem is now worst. IE4linux installs with minor trouble but IE6 has many graphical abnormalities so as everything I open with it. Other software in wine and crossover are just fine. I have no toolbars, check boxes, buttons..... Compiz off and probs remain

Also tried something similar with crossover, IE6 installs ok but messenger tells me that the setup can't continue and to download the file from Microsoft


Okay did you save the program or did you do an "Open from Location" if you did a Save that might be your problem. I will tell you now, that I am not very happy with the way that 8.x is running on my machine. It is very quirky and the support from Wine is rated very low "garbage" as the Wine Application Support Page says...

I am having such issues as, not being able to connect, to connecting and seeing people on-line but people not getting my IMs... 8.x only work when IT want to work... Typical MS crap. Which is why I switched over to Ubuntu in the first place.

Also the issues you are having with IE on IEs4Linux, has to do with the fact that it is not running IE on Linux, and your not getting the full use out of the browser. IE the Browser engine is throttled for Windows 98SE,2000, and XP SP1+... So that is one reason why things look the way they do. There is also the problem of CLASSIC driver support for a lot of Video cards out there on Linux. Like mine I am Using a GMA945 Intel Chip and Ubuntu is using i810 chipset drivers to push the card. Which works to an extent...

---

### Post by msghaleb on 2008-03-22
Got to step 4 but then it says if I want to download the new version, after that if yes can't connect or verify update!


> **Scorpion2k5 said:**
> I was able to get MSN Messenger 8.5 to install just fine one my computer with Ubuntu 7.`0 running Wine 0.9.53. 

Here is what I did:
1. I went to [www.oldversion.com](www.oldversion.com), and downloaded version 7.0 first.
2. Then I went ahead, and had IE4linux running with IE6 to install MSN Messenger, cause version 7.0 needs IE5.5 or better to run. 
3. Then I went ahead and installed MSN Messenger 7 as a "run" not Save. Otherwise it will say that you need to download Internet Explorer. 
4. While having IE4linux running with IE6 I then, installed MSN Messenger 7 without fail. 
5. Then I logged in with my screen name, MSN told me that I needed to update before logging in, so I clicked yes to update, and it install MSN Version 8 on my computer without fail.

Now I have MSN Messenger 8.x installed and it wasn't really all that hard... Once I found out the Wine has classified the MSN Messenger 8.x installer as garbage, when used with Wine, it was rather simple to decide to go with 7 first and then update to 8.x when it asked... LOL :guitar:

---

### Post by jav_ on 2008-03-23
hey guys how do i uninstall kmess?

i downloaded the independent installer to test it..i still prefer amsn over this program..
when i goto my synaptic package manager to uninstall it...the box for kmess isnt even checked marked..when i went to Applecations>add/remove then went to installed programs..kmess is not even there...
i know its still installed because its in Applications>Internet>kmess

anyone know the solution?
thanks

---

### Post by Peter Great on 2008-04-20
Does Linux have any MSN client program which supports voice chat? I searched for hours and couldn't find one.

---

### Post by kurotenshi on 2008-04-22
I find it interesting that Skype (that was intruduced to me as THE voice chat software a long time ago) doesn't support voice on linux.

---

### Post by imon9 on 2008-04-23
> **kurotenshi said:**
> I find it interesting that Skype (that was intruduced to me as THE voice chat software a long time ago) doesn't support voice on linux.

that is certainly not true.. U better have a good reason why u came up with a comment like that. It iwll mislead a lot of ppl. 

Skype is a telephony & video call program. It DOES support voice. What u need is your sound card to be supported by linux (and ur microphone to be configured correctly) dude

---

### Post by BlueEagle_NL on 2008-04-23
> **jav_ said:**
> hey guys how do i uninstall kmess?
 
i downloaded the independent installer to test it..i still prefer amsn over this program..
when i goto my synaptic package manager to uninstall it...the box for kmess isnt even checked marked..when i went to Applecations>add/remove then went to installed programs..kmess is not even there...
i know its still installed because its in Applications>Internet>kmess
 
anyone know the solution?
thanks
 
If you try to run kmess from the menu, will it run? If it won't, just delete the menu entry. If it will, then kmess is pretty baked into kubuntu I'd think... I don't use Kubu myself, I'm with Ubu, so that last line probably won't be true...

---

### Post by kurotenshi on 2008-04-24
> **imon9 said:**
> that is certainly not true.. U better have a good reason why u came up with a comment like that. It iwll mislead a lot of ppl. 

Skype is a telephony & video call program. It DOES support voice. What u need is your sound card to be supported by linux (and ur microphone to be configured correctly) dude

UPS....sorry, I was missled by what I was reading and writen VOICE insted of VIDEO CHAT sorry my bad

---

