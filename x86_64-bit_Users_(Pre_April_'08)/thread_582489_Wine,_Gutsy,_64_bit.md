---
title: "Wine, Gutsy, 64 bit"
date: 2007-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by chrishere01 on 2007-10-19
so yeah im trying to run wine with 64 bit wine
can someone help me out because
im trying to install steam and the steam msi file cant be opened by wine

so yeah i think its a 32 bit wine running on my 64 bit system
some please help me :D

---

### Post by chrishere01 on 2007-10-19
Sigh

---

### Post by JensenDied on 2007-10-19
I'm having issues myself on 32bit after the transition from 7.04 -> 7.10.

the following versions have failed to be of use so far:
0.9.46-0ubuntu1 (ubuntu repos)
0.9.46 (winehq source tarball)
0.9.47 (winehq gutsy .deb)

---

### Post by chrishere01 on 2007-10-20
errr, what do i do with that stuff

---

### Post by beanzapper on 2007-10-20
If wine is installed, navigate to where you downloaded the installer and use: ```
msiexec /i SteamInstall.msi
```.

---

### Post by chrishere01 on 2007-10-20
hmm
i installed it throught console sooooo yeah
i dunno if that works 
but i tried it and it doesnt
so any other suggestion would be helpful

---

### Post by conjur3r on 2007-10-21
I'm having wine issues too.  First time using a 64bit OS but have had everything working nicely on 32bits before.

I installed wine using the same method I used previously, which was to add the apt repos as mentioned for gutsy somewhere on winehq.org, updated the packages, and apt-get wine.  It installs fine.

$ wine --version
wine-0.9.47

But nothing runs.  Not even notepad, which comes with wine:

$ wine notepad
Segmentation fault (core dumped)
$ wineprefixcreate 
Segmentation fault (core dumped)

---

### Post by PmDematagoda on 2007-10-21
I installed wine for x64 using only the repos, it should work for you as well.

---

### Post by chrishere01 on 2007-10-21
> **PmDematagoda said:**
> I installed wine for x64 using only the repos, it should work for you as well.

uh... what do you mean only repos

and how would i do this

---

### Post by chrishere01 on 2007-10-21
> **conjur3r said:**
> I'm having wine issues too.  First time using a 64bit OS but have had everything working nicely on 32bits before.

I installed wine using the same method I used previously, which was to add the apt repos as mentioned for gutsy somewhere on winehq.org, updated the packages, and apt-get wine.  It installs fine.

$ wine --version
wine-0.9.47

But nothing runs.  Not even notepad, which comes with wine:

$ wine notepad
Segmentation fault (core dumped)
$ wineprefixcreate 
Segmentation fault (core dumped)

what do i do...

---

### Post by chrishere01 on 2007-10-21
*sigh*

---

### Post by bonestonne on 2007-10-21
If you want WINE on 64 Bit, use the Synaptic Package Manager. if you don't know that, you shouldn't be using 64 bit.

I'm running Adobe Photoshop [copied from my Windows drive with a registry export]. runs great, no complaints.

my erk with noobs is not understanding something simple about Ubuntu. my reason for using it is the ease of use. Ubuntu is very user friendly, so become more in-tune with your OS.

Repos: Repositories. install via Synaptic or use termal via "apt-get install [program name]"

as per the failing launch etc, i have no advice for you, my install works perfectly. i did not use "apt-get" i use Synaptic. in Ubuntu 7.04 x64, Wine was not an option, i checked again after the upgrade, works fine.

my system specs are in the sig, if you have questions about my install/system/installed apps/usage, PM me, i have no problem giving advice.
---------
i have Ubuntu Studio installed on my Thinkpad t22 with Wine emulating Photoshop 7, so wine is easy coming to me. while i'm not a Ubuntu pro by any means, i know my way around, and i use my resources wisely. 
[B][I][U][SIZE="4"]
in any forum "google" is your best friend.[/SIZE][/U][/I][/B]

---

### Post by bonestonne on 2007-10-21
- Fire up a terminal session and type the next commands;

TIP: Instead of using apt-get, you can install them with the Synaptic Package Manager located in the System/Administration menu

    * $ sudo apt-get install recode


- Then you need to copy all the necessary files from the Windows box;


    * Copy the whole Steam folder from &#8220;c:\Program Files\&#8221; to &#8220;/home/"YOURNAME"/.wine/drive_c/Program Files/&#8221;
^
with this, you can go into your applications menu, Wine>Browse C:/
-that will open the emulated C:/ drive
--this is not your windows partition!!!

-open your windows drive [you should have NTFS-3g installed for this along with ntfs-config]
--browse to where you have Steam installed in the Program Files folder, and copy the WHOLE FOLDER not just one file into the "Program Files" folder in Wine. DO NOT COPY INTO A SUB-FOLDER!
---------

- Now you need to export the registry keys of the Steam;


    * In your Windows box, type &#8220;regedit&#8221; in the command-line and export the whole &#8220;HKEY_LOCAL_MACHINE/Software/Valve/Steam/&#8221; to &#8220;steam.reg&#8221;.
^
checked that with chrishere01, so its right.

    * The next step is to copy that file to your Ubuntu box and convert it to the encoding of YOUR system. For example, if your Ubuntu box has as default charset ascii and your Windows box has ucs-2 then "recode ucs-2..ascii steam.reg&#8221; would do the trick.

After you converted your steam.reg file, type &#8220;$ sudo wine regedit steam.reg&#8221; to import it to wine.
^
**always recode the file, no matter what**

    * That&#8217;s it!
Right click on Applications > Edit Menu ---- create the new launcher where you want it...this is how my Photoshop CS2 launcher is configured.

Type: Application
Name: Photoshop CS2
Command: env WINEPREFIX="/home/james/.wine" wine "C:\Program Files\Adobe\Adobe Photoshop CS2\Photoshop.exe"
Comment: (doesn't matter what)

upon completing this launcher, Photoshop gets an unrecoverable error...as soon as i find the answer to this, i'll let you all know. this same launcher worked on my laptop for Photoshop 7, so i'll have to get back to you all as to where the failure occurs.
--------------------------------------------------------------------
now, i just tweaked this from a guide to installing Photoshop in wine because i had trouble doing a clean install. this should work for anyone.

***_a note to keep in mind is that its much easier to do all of this through a dual boot, not two different machines, because the registry could be off [rare but possible]. this worked the first time for me, so it should work for anyone else easily. you can adapt this method to any program really, so just keep the basic steps in mind!_***

also, when you install Wine in 32bit vs 64bit, its different. don't expect the menus or application to behave the same way in all cases.

--cheers to chrishere01 for getting it finally and helping me fine tune this.

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)
^refer to that for further issues with steam or installing from scratch
---------------------------------
[B]
any installer file should have no spaces in its name
for .msi, use "wine msiexec /i "filename".msi
Photoshop is very bitchy about this, while i'm close to getting it to work again, i'm having issues installing from scratch.
64bit Wine is sketchy! you'll need tons of patience for this
when installing anything, close all other applications, give it no room for the 'lack of memory' excuse
i'm trying to fine-tine this stat for you all, but school will interfere...give me time.
[/B]


"For the Photoshop-crashes because of &#8220;Hard or Softwareerror&#8221;

I was able to run PS once (via the copy from winbox-method) but on the second launch it crashed.

I found, that it created some cfg&#8217;s under the folder c:\windows\profile\[name]\Application Data\Adobe\Photoshop\9.0\Adobe Photoshop CS2 Settings\&#8230;

If you delete this folder (especially Adobe Photoshop CS2 Prefs.psp) PS works again&#8230; seems, that it stores some wrong values&#8230;"
^found that for photoshop people...will help immensely
---------
while the import of steam is successful, this may need to be imported from an XP machine to work!

The disadvantage is, you can change no settings - it will always run with defaults

---

### Post by Lurker_ on 2007-10-21
I've got Kubuntu Gutsy 7.10 AMD64 installed on my laptop and it seems to be working so far, but I haven't installed too much yet.  However, when I try to go to the System Settings Advanced tab and select "Windows Applications" I can't configure anything and the machine complains that wine isn't installed.  

While I don't mind too much about doing things manually, I would like to eventually get this control panel working properly just to save time in the long run.  Any ideas?

---

### Post by bonestonne on 2007-10-21
where are you opening System Settings from?

7.10 is edging the native Wine support, but if you don't have wine installed you wont be able to easily work with Windows Applications...

---

### Post by ravirdv on 2007-10-22
well i dont know much but wat i did was sudo apt-get install wine and its working perfectly on my 64bit gusty i get 100 fps on cs :D with my onboard nvidia 6150 graphics

---

### Post by beanzapper on 2007-10-22
I used to have a problem with Nvidia drivers and Wine back on Feisty, but I didn't have this problem on Gutsy. It wouldn't hurt to try this though (assuming you have an Nvidia card): reinstall your Nvidia drivers after having installed Wine.

-Hope this helps,
bean.

:popcorn:

---

### Post by YokoZar on 2007-10-22
Hey chris, I make the Wine packages for Ubuntu.  I understand Wine is a bit nonintuitive to use at the moment - that's why I've been so interested in making it better.  Anyway, I think I can help you.

> **chrishere01 said:**
> so yeah im trying to run wine with 64 bit wine
can someone help me out because
im trying to install steam and the steam msi file cant be opened by wine

so yeah i think its a 32 bit wine running on my 64 bit system
some please help me :DSince Gutsy, there is nothing special about the 64 bit package of Wine - it just works like the 32 bit version.  Install Wine like any other Universe package, such as by using the Synaptic package manager (under System->Administration).

While Wine (sometimes) works by simply double clicking .exe files, it isn't yet setup to handle .msi files from the interface.  I'm working on fixing this for the next Ubuntu release.  In the meantime, you'll have to use a terminal window to install steam.

Applications->Accessories->Terminal
navigate to wherever you put the steam installer using the cd command (hitting tab a few times after typing part of the directory name helps here).

The rest of the instructions are here: [http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

> **bonestonne said:**
> huge wall of outdated informationDon't bother with any of this, it is completely unnecessary.  Steam will work without such weird workarounds in Wine.  If you want current information and howtos for Apps that don't "just work", the [Wine AppDB](http://appdb.winehq.org/appview.php?iVersionId=1554) is the best place to get them.

---

### Post by Lurker_ on 2007-10-22
> **bonestonne said:**
> where are you opening System Settings from?

7.10 is edging the native Wine support, but if you don't have wine installed you wont be able to easily work with Windows Applications...

Wine is installed.  I used Synaptic to get it running.  I can pull up konsole and type "wine notepad" and it just works.  That said, when I hit the K-Menu there's an option right there called "System Settings".  When that loads, I hit the Advanced tab and there's a selection there for Wine.  However, that button doesn't seem to recognize that Wine is installed. 

Again, I'm capable of getting Wine configured manually, but I would like to have access to the nice, easy to use interface and keep the manual configuration to only when necessary.

:)

---

### Post by ttynjala on 2007-10-22
I have both Ubuntu 7.04 x64 and 7.10 x64 installations. In the 7.04 I got the wine installed from some repos I dont remember now and abt. 2 days ago it got upgraded to 0.9.47 (and broke some of the stuff in the process..). Now I get segmentation faults there. Not sure if its a problem with the ubuntu build though or not.

In the gutsy I got the wine from the main repos (i.e. no additional sources added to repos, just sudo apt-get install wine) and it's still in version 0.9.46 (and I get no crashes with that).

With gutsy now that the wine is in the main repos it seems its propably better go with the main repos.

---

### Post by Dmitri on 2007-10-22
> **Lurker_ said:**
> Wine is installed.  I used Synaptic to get it running.  I can pull up konsole and type "wine notepad" and it just works.  That said, when I hit the K-Menu there's an option right there called "System Settings".  When that loads, I hit the Advanced tab and there's a selection there for Wine.  However, that button doesn't seem to recognize that Wine is installed. 

Again, I'm capable of getting Wine configured manually, but I would like to have access to the nice, easy to use interface and keep the manual configuration to only when necessary.

:)

I run Kubuntu 7.10 and have the same problem with Wine as Lurker here.

Although I installed Wine with System Setting/Advanced/Windows Applications when it proposed to.

---

### Post by greatwhitemonkey on 2007-10-24
> **beanzapper said:**
> If wine is installed, navigate to where you downloaded the installer and use: ```
msiexec /i SteamInstall.msi
```.

that worked perfectly for me, i'm on a amd64 with gutsy. thanks :D  now if only i could run VB express for my programming homework i'd be able to do away with windows all together

---

### Post by Lurker_ on 2007-10-25
Wouldn't Mono be able to replace the VB express?

---

### Post by FUbuf on 2007-10-26
I crashed my Gnome several times With 64 bit ubuntu and Wine. I don't know why that happens, but it just happens.

Also 64 bit version Gnome hanged when I were browsing Screensavers. Screensaver was left running and I couldn't do anything else than shut power off.

---

### Post by biovore on 2007-11-12
I have noticed that wine won't run under my custom kernel.  It only seems to run under 2.6.22-14-generic.  I am using a E6850.  I think there might be an programing issue with wine.  Can't seem to handle the differences between AMD64 and EMT64.   If you have a EMT64 machine and a custom kernel, I suggest you use the -generic for you processor family type.  The Intel selection here tends to break things, because most everything on *ubuntu 64bit is compiled using the AMD way of operating, and not EMT64 way of operating.  

This is only based a few observations though.  Wine runs with the generic kernel and causes segfault on my custom kernel.
 
The only differance between mine and the ubuntu -generic kernel is the processor family and the kernel tickrate.  I doublt its the kernel tickrate.

Else its all the same built from the sources from the ubuntu kernel using the .config from the ubuntu kernel.

---

### Post by simon_ives on 2008-02-15
I installed Wine fine via Synaptic but I'm having this issue where when a wine app (notepad, configure wine, etc.) is started the wine window is just gray.  I haven't tried installing any other apps yet as I'd like to sort this issue out first.  Any suggestions?

(See attached screenshot)

---

### Post by Kilz on 2008-02-16
> **biovore said:**
> I have noticed that wine won't run under my custom kernel.  It only seems to run under 2.6.22-14-generic.  I am using a E6850.  I think there might be an programing issue with wine.  Can't seem to handle the differences between AMD64 and EMT64.   If you have a EMT64 machine and a custom kernel, I suggest you use the -generic for you processor family type.  The Intel selection here tends to break things, because most everything on *ubuntu 64bit is compiled using the AMD way of operating, and not EMT64 way of operating.  

This is only based a few observations though.  Wine runs with the generic kernel and causes segfault on my custom kernel.
 
The only differance between mine and the ubuntu -generic kernel is the processor family and the kernel tickrate.  I doublt its the kernel tickrate.

Else its all the same built from the sources from the ubuntu kernel using the .config from the ubuntu kernel.

More likely the problem is the build of the custom kernel if it runs fine under the stock kernel.

---

