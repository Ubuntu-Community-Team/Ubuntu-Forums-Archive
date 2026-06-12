---
title: "Could not find Wine Gecko. HTML rendering will be disabled."
date: 2023-02-03
forum: Wine
---

### Post by off-track on 2023-02-03
Sorry but I'm a relative newbie to Ubuntu after getting frustrated with it ~ ten years ago.  After my last Win machine died I decided to try Ubuntu once again.  So far it seems to be working fairly smooth.  I'm installed Libreoffice and Evolution to bypass the need for Office and Outlook and they seem to be working flawlessly/

Ubuntu 
Description:    Ubuntu 22.04.1 LTS
Wine:
wine-6.0.3 (Ubuntu 6.0.3~repack-1)

I'm trying to run a Windows app and am getting the above error even though I installed both the 32 and 64 bit Gecko files.  I searched around and found some suggestions that indicated that I might need winbind and winetweaks but neither made any difference. FWIW I also get the same error from "wine iexplore".  It starts and shows a "normal" Wine Internet Explorer window but is just a blank sheet below the toolbar.  Specifying a fully qualified URL does nothing  The windows app I'm trying to run does the same from the CLI.

Terminal yields the following error for "wine iexplore": 
"Could not find Wine Gecko. HTML rendering will be disabled.
0024:err:mshtml:create_document_object Failed to init Gecko, returning CLASS_E_CLASSNOTAVAILABLE"

wine iexplore [https://www.google.com](https://www.google.com) gives the same error in terminal

I tried to create a .desktop icon entry but it does nothing at all (figure it wouldn't but thought the full path might be required).

From searching I see similar problems over the years but can't seem to find a solution.  Any suggestions how to proceed?

---

### Post by TheFu on 2023-02-03
[https://appdb.winehq.org/objectManager.php?sClass=application&iId=25](https://appdb.winehq.org/objectManager.php?sClass=application&iId=25) has the available information for running IE under WINE.  Appears to be mostly "garbage" level with no versions for OS later than Win7 listed.  There was 1 report that claimed "bronze" level support, but no how-to has been shared.

---

### Post by DuckHook on 2023-02-03
There may be many reasons that you don't want to divulge the app you keep referring to. Understandable if so. However, without knowing what app you are having trouble with, it is pretty much impossible to help you.

Speaking in general, here are my observations:

[LIST]
[*]Trying to run Windows apps in Linux is basically forcing a round peg into a square hole. The real miracle is that it can be done at all. With WINE, there is a fighting chance, but that is the WINE developers' gift to us; not a default set of expectations to which we have any right.
[*]Most people who simply must run a particular Windows app, but who wish to use Linux on their base system for its power, flexibility and security, will run Windows inside a VM. That way, they don't have to compromise on their base OS and have the additional benefit of sandboxing Windows inside a security silo where it cannot do any damage. However, this is not a viable alternative on low&#8209;end or resource&#8209;limited machines.
[*]If you really want to run the app in WINE irrespective of the above, then you need to check it against the WINEHQ App Database where others have stress tested the app and posted any known workarounds. If that database rates the app as anything less than "silver" status, you are unlikely to be happy with the results.
[*]I do run WINE quite successfully with many old Windows games. But games are not mission&#8209;critical and, after many years, I know my way around WINE, especially when it comes to obscure workarounds that general users are unlikely to either understand or be capable of implementing. For example, CIV 3 cannot use the latest version of WINE and can run on an older version only by disabling MESA. I can accommodate this without breaking my base system by running that specific instance of WINE within a LXD container. Such a setup is not for the faint of heart.
[*]I would not consider running mission&#8209;critical Windows apps in WINE. A simple update could break the app, which is not a risk worth taking for something on which my livelihood might depend.
[/LIST]

---

### Post by off-track on 2023-02-03
Fair enough Duck.  

Specifically the app I'm trying to get running is HRB Taxcut 2022.  From browsing the WINEHQ app database (and googling) the last reference I could find was back to 2017 and nothing more recent.

No, I know it isn't critical but, the alternatives I've looked at appear less than ideal.

---

### Post by TheFu on 2023-02-03
I run that app inside a Windows VM.

---

### Post by DuckHook on 2023-02-03
> **TheFu said:**
> I run that app inside a Windows VM.
+1

TheFu beat me to it. The app does not appear to be resource&#8209;hungry and should run nicely within a Windows VM.

---

### Post by off-track on 2023-02-05
Hmm.  

Ok so I get that Wine isn't the way to go..  I installed VirtualBox according to the installing Windows 10/11 tutorial.  I got l several warnings about incompatible settings until I fell back to a minimum 32 bit Win10 config.  After starting the VM and selecting the Win 10 iso I get the following error?

"Failed to open a session for the virtual machine **Windows**.

AMD-V is disabled in the BIOS (or by the host OS) (VERR_SVM_DISABLED).

[TABLE="width: 100%"]
[TR]
[TD]Result Code: 
[/TD]
[TD]NS_ERROR_FAILURE (0x80004005)
[/TD]
[/TR]
[TR]
[TD]Component: 
[/TD]
[TD]ConsoleWrap[/TD]
[/TR]
[TR]
[TD]Interface: 
[/TD]
[TD]IConsole {872da645-4a9b-1727-bee2-5585105b9eed}"
[/TD]
[/TR]
[/TABLE]

Is the old computer I'm using is too outdated/limited or am I missing something?

---

### Post by monkeybrain20122 on 2023-02-05
For your wine problem.maybe you have 32 bit gecko for 64 bit wine  [https://forum.winehq.org/viewtopic.php?t=36011](https://forum.winehq.org/viewtopic.php?t=36011)

For your VM problem [https://appuals.com/fix-amd-v-is-disabled-in-the-bios-verr_svm_disabled/](https://appuals.com/fix-amd-v-is-disabled-in-the-bios-verr_svm_disabled/)

---

### Post by DuckHook on 2023-02-05
> **off-track said:**
> …Is the old computer I'm using is too outdated/limited…
To answer this question, we would need to know the details of your HW.

Please post those details:

[LIST]
[*]Age, make/model of machine (at least the motherboard)
[*]Amount of RAM
[/LIST]
Windows is a resource pig. When you run it in a VM, it slows down even further. If you switched to Ubuntu because your machine was performing poorly when running Windows, then it will almost certainly be unbearable running in a VM, hence my original caveat:
> **DuckHook said:**
> …However, this is not a viable alternative on low&#8209;end or resource&#8209;limited machines.
The single biggest improvement comes from adding more RAM. The next biggest improvement comes from switching the HDD for an SSD. Then comes replacing the GPU. The least payback is upgrading the CPU/MOBO. At that point, it makes more sense to invest in a new computer.
> …or am I missing something?
To run a VM effectively, your CPU must be configured to allow virtualization. This is usually a setting in your BIOS that is turned off by default because, as a general security precaution, the less "stuff" that is enabled in your system BIOS, the smaller your attack surface. You must find this setting and turn it on. Your VM won't run unless you do that.

monkeybrain has kindly linked to a good article that contains further steps if the above is not enough.

---

### Post by off-track on 2023-02-06
Please forgive me as I'm new to this forum and haven't fooled with Ubuntu for at least 10 years.  Also, it was in a past life when I used a Windows VM under RHeL

My old PC died and I didn't want to support MS and their office subscription model.  I had this old HP down in the storeroom and thought I'd give it a shot?  So far it seems to be working well for my limited needs (internet browsing, routine documents, e-mail & CPAP).  I am unable to post screenshots from hardinfo but it indicates that it's a HP 2AFE and there's only 3Gb memory.  I'll have to pop the top to see if it's expandable but I kind of doubt it?

Thanks monkey for the info.  Yes, VM was disabled in BIOS.  With that enabled the VM machine does start but the dialog window appears scrambled with only a title bar and a message about "Auto-capture keyboard enabled".  Again, I can't post screenshot..

.. edit .. Arrgh!  obviously I posted too soon as I found there was a loose nut behind the wheel.   Somehow VirtualBox changed the VM to Win7??  When I deleted it and corrected to Win 10 the install started

---

### Post by DuckHook on 2023-02-06
> **off-track said:**
> Please forgive me as I'm new to this forum and haven't fooled with Ubuntu for at least 10 years.
Nothing to forgive. You are very welcome here and it's good to see old users peering under the hood to check out what's new. Ubuntu has come a long way over the last decade. It is now slick enough for general users.
> I didn't want to support MS and their office subscription model.
I find it mind&#8209;cramping that the consuming public lets them get away with this. But hey… I stopped understanding Windows users years ago.
> …I had this old HP down in the storeroom and thought I'd give it a shot?…it indicates that it's a HP 2AFE and there's only 3Gb memory.  I'll have to pop the top to see if it's expandable but I kind of doubt it?
Based on your description of the machine, even though it is now set to enable VMs, it will just choke and die if you try to run Windows.

I'm may be wrong, but I believe that Win10 won't even install with any less than 4GB RAM. Therefore, 3GB to run it in a VM is a non&#8209;starter.

I'm afraid that you will have to either buy a new machine (even if you choose to run Windows on bare metal, your current box won't qualify), or try some fancier solution like PlayOnLinux.

I don't use PlayOnLinux so my info is hearsay, but I understand it to be an extension of WINE that adds some common elements (like dlls) that make some games playable. These games won't play on WINE. The same add&#8209;ons may allow your tax app to run. No promises, but it may be worth a try.

To be honest, if I were you, I would invest in a proper box that could easily do everything that I wanted it to.

I recently set up a separate gaming computer for my grandkids. It was a refurbished Lenovo ultra slim mini box with a two generation's&#8209;old Core i5, 16 GB RAM and a 500GB SSD. The thing retailed for US$125. I already had the monitor (as do you) so my total investment was absurdly low for a decent machine that had more than sufficient horsepower for anything that I cared to throw at it.

If you nose around your locel computer stores, I'm sure you can get refurbished or abandoned gear that's even less than what I paid. Stuff has gotten so cheap that it has become pointless to wrestle with problems imposed purely by resource limitations.

---

