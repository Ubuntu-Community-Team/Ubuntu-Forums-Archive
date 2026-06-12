---
title: "WoW Launcher.exe crash - Ubuntu 11.10 - Wine 1.3"
date: 2011-11-10
forum: Wine
---

### Post by pai natal on 2011-11-10
Hey there,

i have done some hours of researching without any luck concerning my specific problem.

When i start the Launcher.exe to download the remaning % of my WoW installation, it loads and crashes about when the text pops up. Sometimes later. Really random.
Also it starts downloading a bit before crashing. This text appearing when it crashes:

[B]The  program Launcher.exe has encountered a serious problem and needs to  close. We are sorry for the inconvenience. This can be caused by a  problem in the program or a deficiency in Wine. You may want to check [http://appdb.winehq.org]("http://appdb.winehq.org/") for tips about running this application.

If this problem is not present under Windows and has not been reported yet, you can report it at [http://bugs.winehq.org]("http://bugs.winehq.org/").[/B] 

I  can run Wow.exe just fine but that's not going to do me any good since it  has to download more data to be playable.
A curious fact is: after crashing the Launcher stays open, and i can access all the options.

Also when trying to avoid the Launcher, and trying to download it with the "BackroundDownloader.exe" it generates a "WowError". I can't play since my game is not up to date, but i can't avoid the Launcher because of the BackroundDL WowError.

I am a noob concerning Linux, and programming and so on. I know just about enough to cause serious damage ; - |
If anyone has a solution for me, I'd be grateful. Let me know if you need more information.

pai natal

---

### Post by dolphin194 on 2011-11-10
I would suggest that you re-install wine and try it again.
```
sudo apt-get remove wine
```then try installing wine again and see if you can get your World of Warcraft to download with the Launcher and Background Downloader.

If you have experience with Windows 7, this "serious error" problem is labeled as "stopped working"

---

### Post by pai natal on 2011-11-10
Oh, sorry, forgot to mention that i already tried that. Several times. Used the older Wine1.2 version also. The same error, no change at all.
edit: No, no experience with W7 and WoW not working, but haven't played it lately on W7.

---

### Post by gnal on 2011-11-10
I have the same exact error. I don't know what to do... I'll keep searching and let you know if I find something.

---

### Post by dolphin194 on 2011-11-10
So the Cataclysm launcher and background downloader will not work in wine on your machine, no matter what version you are using.

I would suggest that you run Windows in a virtual machine to get the launcher going, then copy all files to your wine installation. That should get the background downloader going. 

If you can't use a virtual machine, then I would suggest that you use a computer with Windows installed on it temporarily, just to get the patch at least *going* in the launcher. Then, copy the files to a flash drive before the installation gets too large, and copy it into your Wine installation.

Once it is in your Wine partition, *then* you can use the Background Downloader to download the game.

Make sure that the launcher in Windows is on the actual downloading part, and that it isn't preparing to download (downloading updated tools).

---

### Post by pai natal on 2011-11-10
I will try that with the idea concerning the virtual machine. The WoW folder is already in the /.wine directory, under "Program Files".

edit: 1.Ok, but, well, as stated, WoW id in my wine, hm, directory, and yet it doesn't work... or is the wine partition something else, and i'm not getting it?
2. Do i need virtual box to start my Windows virtually?

---

### Post by dolphin194 on 2011-11-10
> **pai natal said:**
> I will try that with the idea concerning the virtual machine. The WoW folder is already in the /.wine directory, under "Program Files".

edit: 1.Ok, but, well, as stated, WoW id in my wine, hm, directory, and yet it doesn't work... or is the wine partition something else, and i'm not getting it?
2. Do i need virtual box to start my Windows virtually?

1: The Wine's C:\ directory is located at ~/.wine/dosdevices/c:

2: You will need VirtualBox **and** a Windows install disc to make a virtual machine

**If you don't want to do that, just use a different computer with Windows already on it to start the launcher.**

---

### Post by pai natal on 2011-11-10
> **dolphin194 said:**
> 
1: The Wine's C:\ directory is located at ~/.wine/dosdevices/c:

2: You will need VirtualBox **and** a Windows install disc to make a virtual machine

**If you don't want to do that, just use a different computer with Windows already on it to start the launcher.**
  
1: I just copy pasted it there, and tried to start the BackgroundDL without any success,
2: Well, getting the Virtual Box to run is tricky . . .

And to the mist convenient option, which you wrote fatly: I got no PC with windows around.

---

### Post by Stephan Volkmann on 2011-11-10
for me it helps to start the Game using an older natty, back in Precis it starts without problems..

---

### Post by dolphin194 on 2011-11-10
You will still need to use Windows to get the background downloader to work. It doesn't know what patch to apply because the launcher didn't assign a patch.

 You will need to run the launcher in windows first before you can use the background downloader.

---

### Post by pai natal on 2011-11-10
Yeah . . . working on that, finally got VB running . . . what a drag, oh gosh.
I am going to look for a Windows cd . . . maybe i will be lucky. I will bump in again when i know more about the Launcher and the starting in Windows.

---

### Post by dolphin194 on 2011-11-10
By the way, if you can't find a Windows cd, there are Windows 7 images provided by Microsoft. They give you 30 days before you must activate, and i'd say that's plenty of time. 

You can find them here: [http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/](http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/)

---

### Post by pai natal on 2011-11-11
I had some upodates pending . . . after upgrading the system VB didn'T work anymore, but reinstalling did the trick.
So now i am installing a Win XP (i had an .iso file stored on some exterior HD). I will see how it will work with WoW once i get the internet configured.

I think i learned more about Ubuntu in the last hours than ever since using it, hehe.

---

### Post by pai natal on 2011-11-11
Ok, finally got there after a marathon of installing drivers, giving permissions, sharing folders etc. 
I have everything set; I didn't yet try to enter the game, just the Launcher. 
Now, this little message pop's up:

"Launcher requires write permission on the Z:\ directors to successfully patch the game. Please enable write access to the directory using an administrator account." (Any idea how to fix this little problem? I know it's a VB/Windows issue, but maybe.)

Well, I'm logged in as admin, but i am not getting any sharing done. The Z:\ directory is the mounted network drive where i have shred my WoW folder.
I tried to launch the BackroundDL, and that is working and happily downloading the last 3 Gigs of the game. So far it seems kind of solved, but still it is a mystery to me why make such detours to get it going. Isn't there a simpler way? (Not complaining, just asking ;-))

---

### Post by dolphin194 on 2011-11-11
Well, like I said, you could have used a Windows computer to do that. That would have let it go without problems. But then, you have to transfer the game to your computer.

You could have used an older Ubuntu distribution and try it on there, but that would prevent you from using the computer.

You also could have torrented the game. That would have worked no doubt. But then you couldn't play while it downloads.

---

### Post by pai natal on 2011-11-12
I see. Well, thanks for your help! It*s running now, everything downloaded. Now i just have to get rid of the "fatal wow error" . . . There is lways something to fix, isn't there... sigh.
The game tends to crash when i enter an area which has first to be loaded for  second or two.

---

### Post by ironchefchopchop on 2011-11-15
nvm

---

### Post by logikone on 2011-11-15
fwiw, I was able to get Launcher.exe and BackgroundDownloader.exe to both run w/o crashing by disabling p2p transfers in BackgroundDownloader.exe

---

### Post by EmyrB on 2011-11-16
I can confirm what logikone said, disable p2p transfer and it works.

To do this, launch **BackgroundDownloader.exe > View > Preferences... > Remove tick from Enable peer-to-peer Transfer > OK**

You should have enough time to do this before it crashes.

Edit: - It takes ages to download the patch data through background downloader. I have an 8MB connection and it's reporting that downloading 3.9GB will take 60 hours! Use the Launcher, much quicker, averaging 700KB a second.

---

### Post by Kaboom3009 on 2011-11-16
> **pai natal said:**
> Hey there,

i have done some hours of researching without any luck concerning my specific problem.

When i start the Launcher.exe to download the remaning % of my WoW installation, it loads and crashes about when the text pops up. Sometimes later. Really random.
Also it starts downloading a bit before crashing. This text appearing when it crashes:

[B]The  program Launcher.exe has encountered a serious problem and needs to  close. We are sorry for the inconvenience. This can be caused by a  problem in the program or a deficiency in Wine. You may want to check [http://appdb.winehq.org]("http://appdb.winehq.org/") for tips about running this application.

If this problem is not present under Windows and has not been reported yet, you can report it at [http://bugs.winehq.org]("http://bugs.winehq.org/").[/B] 

I  can run Wow.exe just fine but that's not going to do me any good since it  has to download more data to be playable.
A curious fact is: after crashing the Launcher stays open, and i can access all the options.

Also when trying to avoid the Launcher, and trying to download it with the "BackroundDownloader.exe" it generates a "WowError". I can't play since my game is not up to date, but i can't avoid the Launcher because of the BackroundDL WowError.

I am a noob concerning Linux, and programming and so on. I know just about enough to cause serious damage ; - |
If anyone has a solution for me, I'd be grateful. Let me know if you need more information.

pai natal

I did a search for run World of Warcraft in ubuntu wich gave me a forum  with a 4 mile long explanation of how to install cata 4.2 with wine .. it's a very concise explanation and I would link it here if I wasnt using the page I had it on to  read

The sounds of your troubles MAY be addressed by the very start of this explanation as the person describes a little preinstall check to run for Wine that makes things ready for later they also explain that you will see errors and probable crashes ...  but to wait and be patient as its the windows portions failing NOT the underlying system, which appears to still run.

> **Re: Ubuntu 11.10 Linux: how to install WoW Cataclysm 4.2**             
                                                                Taken from [http://www.wowwiki.com/World_of_Warc...nality_on_Wine]("http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine")


Introduction Edit
This article primarily talks about setting up Wine for running the MS Windows version of  World of Warcraft. Wine also runs on Macintosh computers with x86 CPUs under Mac OS X, but since Blizzard makes a Mac OS X native World of Warcraft client, running it under Wine is unnecessary and even silly.
World of Warcraft  had a client for Linux while it was in the beta phase of development,  but it was later dropped and never officially released.[1] Currently,  WoW is run on Linux by use of Windows compatibility layers. Given that the World of Warcraft  client is no longer officially developed to work in Linux, the  installation of it on Linux is a somewhat more involved process than on  Windows, which it is streamlined to install more easily on. However,  with some careful research, and a bit of patience, it's very possible to  do so.

Alternatively a streamlined process of installation and Windows installation conversion is available via Play On Linux.

While this guide will only cover the Wine compatibility layer, WoW is fully compatible with Crossover.

Here is the begining of the text from the forums I saved a copy for my use later on since I think I will be reading this a few million times while installing WOW.

---

### Post by dolphin194 on 2011-11-18
> **EmyrB said:**
> I can confirm what logikone said, disable p2p transfer and it works.

To do this, launch **BackgroundDownloader.exe > View > Preferences... > Remove tick from Enable peer-to-peer Transfer > OK**

You should have enough time to do this before it crashes.

Edit: - It takes ages to download the patch data through background downloader. I have an 8MB connection and it's reporting that downloading 3.9GB will take 60 hours! Use the Launcher, much quicker, averaging 700KB a second.

It does not take ages to download with the Background Downloader. By default, it throttles the speed that it downloads at. To fix this problem, go and tick the "Don't Throttle Background Download" and that will get your speed of the download back up.

---

### Post by kayris on 2011-11-19
Just wanted to throw my two cents in and confirm that disabling the p2p feature stopped the game from crashing. Also, make sure you install your graphics driver - that was a little bug I chased around after getting the game to launch.

---

### Post by andy80 on 2011-11-22
I want to confirm that disabling p2p download, the BackgroundDownloader doesn't crash anymore. I'm using Ubuntu 11.10 32 bit with Wine 1.3.32 version. 

p.s: the Launcher.exe keeps crashing!

---

### Post by Immolatus on 2011-11-24
you can increase the speed of the background downloader by disabling throttling in the same menu as disable p2p.

Man....mine was running like a top until about a week ago. I have tried "winetricks ie7" to no avail. I'm told running ie and changing the LAN setting to auto detect proxy could fix this but it wont let me apply the setting, so when I close to dialogue it goes back...grrr.

---

### Post by drewbond on 2011-11-25
I think I have fixed it, turn off Peer-to-Peer Networking.  Working so far only got about 1 GB so far.  Was crashing at 48MB

---

### Post by MikeyPooh on 2011-11-25
This is From Winehq

What works
Wow.exe
BackgroundDownloader.exe


What does not
Launcher.exe  

What was not tested
Installation from beginning.

Additional Comments
Slackware64 13.37, add multilib for 32bit support.
Nvidia 64 bit driver version: 290.10. opengl works slightly better, but framerate drops some compare to D3D.
No problem with sound.

Link [http://appdb.winehq.org/objectManager.php?sClass=version&iId=23843](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23843)

According to Winehq Launcher.exe will not work, However WoW.exe will as will Backgrounddownloader

Try Launching with WoW.exe and see if this works for you

Hope This Helps :)

Mike

---

### Post by Arminius on 2011-12-05
I was having the same problem, of the launcher crashing, I disabled peer to peer and the launcher hasn't crashed since.

---

### Post by carnytom on 2012-01-04
disabling peer o peer does the trick

---

### Post by vacc73 on 2012-01-20
***[COLOR="Blue"]I had the same thing happen to me with WoW in 10.04. I use Playonlinux, and was poking around in the settings section and I clicked on the install packages header and started to scroll down the list. On a hunch I downloaded diectx9 even though I thought wine already had it . I the rebooted and started the WoW launcher again. It worked just fine!!! Maybe this would work for you:popcorn:[/COLOR]***

---

