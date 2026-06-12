---
title: "** Before asking for help with Wine &lt;&lt; PLEASE READ BEFORE POSTING **"
date: 2008-08-09
forum: Wine
---

### Post by YokoZar on 2008-08-09
[SIZE="5"]**How do I use Wine?**[/size]
[list][*]First, install Wine by going to Applications->Add/Remove.  Search for Wine and select it.
[*]Then, install the programs you want to by selecting their installer, right clicking, and selecting open with Wine. Note that double clicking the program doesn't work due to [this bug.](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/351429) *If you receive cryptic warnings about the executable bit, you can [enable the Wine PPA](http://ubuntuforums.org/showthread.php?t=871535) to never see them again.*
[*]After that, you can run the program like you would in Windows.  Your "start menu" is in Applications->Wine->Programs, and you can also open individual executable files manually using right click->open with Wine.
[/list]

[SIZE="5"]**Things you should try before asking for help:**[/SIZE]
[LIST=1]
[*]***Use the proprietary drivers for your video card*** - many graphics issues in Wine are due to missing features in the free drivers for various video cards.  Try enabling the proprietary drivers for your video card, if available, using System->Administration->Additional Drivers.
[*]***Check AppDB*** - Wine's [Application Database](http://appdb.winehq.org/) is one of the best sources for help with running apps in Wine. First and foremost, it will tell you when an application is not worth trying at all. Secondly, but almost as important, an application's AppDB entry may include how-to information on a working way to install and run your application.
[*]***Never run Wine with sudo*** - Do not run Wine as root or by using sudo.  Doing so doesn't help anything and will break your fake Windows installation entirely.
[*]***Do not try and install DirectX*** - Wine already has its own implementation of DirectX, and attempting to install the Windows version might break some things.  Cancel or skip the install if an application prompts you.
[*]***Reinstalling Wine won't help*** - Reinstalling the same Wine package in Synaptic or Software Center won't do anything - your virtual Windows drive and applications will be just the same unless you manually remove them.  What you probably wanted to do is erase your fake Windows install entirely; to do this, you must remove (or rename) the hidden .wine folder in your home directory (view->show hidden files).  This will erase all Windows applications you've installed with Wine and let you start fresh.  Note that you'll still have (nonworking) start menu entries for the removed apps in Applications->Wine unless you first removed them with Wine's uninstaller.
[*]***Update Wine*** - Unless you have specific information that the latest version of Wine won't work, you should try updating to the most current version of Wine. Each update includes many bugfixes that can correct your issue. However, it is important to note that an update could include new bugs or regressions that will cause problems with some applications.  If you are manually selecting versions, please note that they are two digit numbers: Wine 1.1.10 is newer than 1.1.9.
[*]***Search the forums*** - There are many, many posts on running specific applications in Wine already. Chances are really good that someone has already asked the same question you have.
[*]***Try different Windows versions*** - Much like Windows itself, Wine supports different "compatibility modes" for different versions of Windows.
[*]***Check the terminal output*** - Perhaps I should say "*Use the terminal*" first. When run from the terminal, Wine outputs any error messages to the terminal window, which may tell you exactly what is wrong. This is especially useful for identifying when a DLL is missing and using winetricks may be needed. Check the output for details like that and anything else that may identify where your error is occurring.
[/LIST]

[SIZE="5"]**Things to include when asking for help:**[/SIZE]
[LIST=1]
[*]***Wine and Ubuntu version*** - Wine betas are updated roughly every two weeks. Each update includes numerous changes and fixes. Knowing which version you are using can often lead to very specific fixes for whatever problem you may be having.
[*]***Terminal output*** - Run your application from the terminal and include the output in your post (make sure you use the forum CODE tags). The informational and error messages provided in the terminal can be very helpful in pinpointing where the problem is occurring.
[*]***Wine configuration*** - How you have Wine configured changes how Wine behaves greatly and may be the cause of whatever issue you may be having. Configuration changes you should mention are anything you've modified in winecfg or the registry, any winetricks steps you've done, and any other special software you've installed (eg, .NET framework).
[*]***Hardware specs/drivers*** - Name your video card and say whether you're using the proprietary or stock drivers. lspci on a terminal can help identify the chipset if needed (it'll show up as VGA compatible controller, display adapter, or something similar).
[*]***Other Wine applications*** - Include any other apps you may have installed in your Wine directory.  Be sure to mention if you've used third party tools like winetricks or PlayOnLinux.
[/LIST]
Providing this info will greatly increase the chances that someone on these forums will be able to help solve your problem.

[SIZE="5"]**If Wine is causing complete system crashes:**[/SIZE]
[INDENT]If using Wine causes very nasty problems like system freezes requiring a hardware reset or the xserver crashing and dumping you back to the login screen, then there is a deeper problem with your system that Wine is simply exposing.  The most common cause of this is problematic drivers.  Upgrading to the latest Ubuntu release can often solve these problems.[/INDENT]

---

