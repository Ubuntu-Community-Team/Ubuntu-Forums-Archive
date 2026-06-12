---
title: "RealPlayer 10 in Feisty and AMD64"
date: 2007-04-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by David Jenkins on 2007-04-26
Touch wood - I'm having mostly good experiences with Feisty on my AMD64 machine (it'll all fall apart now I've said that!)

Following something said in another thread, I tried to install RealPlayer 10.  The stand-alone version now runs successfully and will play a local .ram file.

However, Firefox reports 'you do not have realplayer installed' or similar. Also the application is not  shown in the list of available players. This suggests that there is a setup problem.

Can someone give me a clue, or point me to help/guidance/another thread where I can gain enlightenment?

Many thanks,
David

---

### Post by kuja on 2007-04-29
If I remember right RealPlayer is 32-bit. Firefox is 64-bit. That never mixes well. Try and see if you can't get it to work in Firefox32 or perhaps Opera.

---

### Post by David Jenkins on 2007-04-30
Thanks - I've decided to leave it alone for a while, until a stable solution appears.

It's a shame, as I like to listen to streaming channels from the BBC, but I'll cope! :D

---

### Post by kuja on 2007-04-30
Who says Opera and/or Firefox32 aren't stable?

---

### Post by slowcoach on 2007-04-30
If you install MPlayer and it's Browser plugin from the repo's you will be able to stream REAL Audio files at the BBC site, video images don't work though unless they are available as wmf as well. If you install the 32bit files you can get the full monte but as the BBC are cutting down on showing video these days I just stuck with the 64bit option, ie. REAL sound only.

---

### Post by kinemagician on 2007-04-30
I have Feisty running on a 32 bit machine.  I could not install realplayer on firefox.....What if I try to install it on another browser?  Does anybody have any hint?  Thanks

---

### Post by David Jenkins on 2007-04-30
> **slowcoach said:**
> If you install MPlayer and it's Browser plugin from the repo's you will be able to stream REAL Audio files at the BBC site, video images don't work though unless they are available as wmf as well. 

That's probably all I'll need - I have mplayer, but I may not have the plugin - investigation required!

As for stability - I was generalising about 64-bit code, not 32-bit.  I'm happy to wait until a 64-bit solution eventually appears.

Many thanks,
David

---

### Post by dptxp on 2007-04-30
64 bit code is very stable.
It is just that some packages are available in 32 bit only.
Soon they too shall be made in 64 bit.

---

### Post by David Jenkins on 2007-04-30
OK - wrong terminology - I'll load the new functionality once it's available in 64-bit.  I can wait until then.

:D

---

### Post by fabertawe on 2007-05-01
You might want to try the **[MediaPlayerConnectivity xpi]("http://membres.lycos.fr/sethnakht/")** for Firefox. I find this very useful for launching RealPlayer itself to handle the links. It also works well for playing video with VLC that can't be handled by a plugin. This is with 64bit FF of course.

Paul

---

### Post by David Jenkins on 2007-05-01
Ah - that works very well - many thanks.

I now have all the functionality I need, thanks to everyones' contributions! :D

I can also say that Ubuntu Feisty is far better than the Mandriva setup I've just over-written! :)

---

### Post by Das Goat on 2007-05-10
> **kuja said:**
> Who says Opera and/or Firefox32 aren't stable?

Is there a file missing from your script?

[http://www.xnowherex.net/simple64/simple64-data_15_amd64.deb](http://www.xnowherex.net/simple64/simple64-data_15_amd64.deb)

dasgoat@dasgoat-laptop:~$ sudo [http://www.xnowherex.net/simple64/simple64-data_15_amd64.deb](http://www.xnowherex.net/simple64/simple64-data_15_amd64.deb)
sudo: [http://www.xnowherex.net/simple64/simple64-data_15_amd64.deb:](http://www.xnowherex.net/simple64/simple64-data_15_amd64.deb:) command not found
dasgoat@dasgoat-laptop:~$ [http://www.xnowherex.net/simple64/simple64-data_15_amd64.deb](http://www.xnowherex.net/simple64/simple64-data_15_amd64.deb)
bash: [http://www.xnowherex.net/simple64/simple64-data_15_amd64.deb:](http://www.xnowherex.net/simple64/simple64-data_15_amd64.deb:) No such file or directory

---

### Post by Das Goat on 2007-05-10
> **fabertawe said:**
> You might want to try the **[MediaPlayerConnectivity xpi]("http://membres.lycos.fr/sethnakht/")** for Firefox. I find this very useful for launching RealPlayer itself to handle the links. It also works well for playing video with VLC that can't be handled by a plugin. This is with 64bit FF of course.

Paul

ok, I downloaded the file, but I don't know how to install it. give a brother a hint please?

---

### Post by Das Goat on 2007-05-24
Well, no one seems to have anything to add, so let me tell you what i have been able to figure out.

It seems that you can't run Realplayer 10 on 64-bit Unbuntu. All of the installation instruction seem to be the same, and when I do them I get unrecoveralbe errors. Mostly, the installer doesn't seem to find the additional files it needs and synaptics can't find those EXACT files either. All of the success stories I found refer to 32 bit Unbuntu. So..... it seems we are stuck.

---

### Post by John Jason Jordan on 2007-05-24
> **Das Goat said:**
> Well, no one seems to have anything to add, so let me tell you what i have been able to figure out.
It seems that you can't run Realplayer 10 on 64-bit Unbuntu. All of the installation instruction seem to be the same, and when I do them I get unrecoveralbe errors. Mostly, the installer doesn't seem to find the additional files it needs and synaptics can't find those EXACT files either. All of the success stories I found refer to 32 bit Unbuntu. So..... it seems we are stuck.
I don't know what you tried, but I have had it running on 64-bit Ubuntu since at least Dapper, maybe earlier. I just built myself a new desktop on which I installed Feisty amd64, and the first thing I installed was RealPlayer. I've never had a problem installing or running it.

Did you try Automatix?

---

### Post by Das Goat on 2007-06-05
J.J.J.

Can you point me where you got your files from?

---

### Post by John Jason Jordan on 2007-06-05
> **Das Goat said:**
> J.J.J.
Can you point me where you got your files from?[
I got it from here:

[http://www.real.com/linux/]("http://www.real.com/linux/")

However, I don't recall the procedure for installing it. I'm sure there's an instruction file somewhere, but I can't remember where it was. I've had it installed for so long I've forgotten the details.

---

### Post by fabertawe on 2007-06-06
> **Das Goat said:**
> ok, I downloaded the file, but I don't know how to install it. give a brother a hint please?

My apologies for being away from this thread so long... scroll down to the 'install now' link and if you're actually in Firefox it will automatically install. Relaunch FF. Go to 'Tools->Add-ons->MediaPlayerConnectivity-Preferences' and set 'Real Media' to '/usr/bin/X11/realplay'. Add it's icon to the toolbar and when you find a Realplayer link click on the toolbar icon and 'list all media links of page' and when you select the link you want it will launch the stand alone RealPlayer (presuming you can install this but it was easy for me, there are a few threads in the 64bit forum, do a search).

Cheers ... Paul

---

### Post by Das Goat on 2007-06-09
> **fabertawe said:**
> My apologies for being away from this thread so long... scroll down to the 'install now' link and if you're actually in Firefox it will automatically install. Relaunch FF. Go to 'Tools->Add-ons->MediaPlayerConnectivity-Preferences' and set 'Real Media' to '/usr/bin/X11/realplay'. Add it's icon to the toolbar and when you find a Realplayer link click on the toolbar icon and 'list all media links of page' and when you select the link you want it will launch the stand alone RealPlayer (presuming you can install this but it was easy for me, there are a few threads in the 64bit forum, do a search).

Cheers ... Paul

"install now" ?

Am I just blind? ( it has been known to be the case)

---

### Post by fabertawe on 2007-06-09
> **Das Goat said:**
> "install now" ?

Am I just blind? ( it has been known to be the case)

About half way down **[the page]("http://membres.lycos.fr/sethnakht/")** it says "current version 0.8.3 (november 25 2006) (Release Notes)" and directly under this is a graphic of a brown opened box with a green arrow pointing down into it and "Install now". If you already have it on your drive then try dragging and dropping into a Firefox window.

Paul

---

### Post by Das Goat on 2007-06-11
> **fabertawe said:**
> About half way down **[the page]("http://membres.lycos.fr/sethnakht/")** it says "current version 0.8.3 (november 25 2006) (Release Notes)" and directly under this is a graphic of a brown opened box with a green arrow pointing down into it and "Install now". If you already have it on your drive then try dragging and dropping into a Firefox window.

Paul

If I am reading this correctly, this only works on Firefox 0.9-2.0

Firefox is currently on version 2.0.4. I don't think this is going to work. It also says nothing about Firefox 64 bit. I downloaded it anyway, extracted the files, but I don't see how to install it. :(

---

### Post by fabertawe on 2007-06-12
> **Das Goat said:**
> If I am reading this correctly, this only works on Firefox 0.9-2.0

Firefox is currently on version 2.0.4. I don't think this is going to work. It also says nothing about Firefox 64 bit. I downloaded it anyway, extracted the files, but I don't see how to install it. :(

I don't understand why you're having a problem with this... I'm using FF 2.0.0.4 (64 bit) and it works for me. It should work on any version of FF that uses .xpi (version number of the xpi permitting of course).

What happens when you just click the link?!

Paul

---

### Post by tkrisz on 2007-06-12
what if you copy the xpi file into .mozilla/firefox/(something).default/extensions and restart firefox?

***

My problem is the following: i have amd64 dapper. I installed Realplayer from the site following the instructions. It works but it plays streams ragged. And the gui often freezes.

---

### Post by Das Goat on 2007-06-12
> **fabertawe said:**
> I don't understand why you're having a problem with this... I'm using FF 2.0.0.4 (64 bit) and it works for me. It should work on any version of FF that uses .xpi (version number of the xpi permitting of course).

What happens when you just click the link?!

Paul

I'm a noob, I admit. 

Here are this file contained in the tar ball:

install.js
install.rdf
In the Chrome Directory
mediaplayerconnectivity.jar
openLocationOSX.pl

what am I supposed to be clicking? Install files 1) doesn't seem to have instructions and 2) has a script that doesn't launch.

---

### Post by tkrisz on 2007-06-12
Was that this one?
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)
Are you sure that there was no install button at the middle of the page?
If not here's the direct link:
[https://addons.mozilla.org/en-US/firefox/downloads/file/2285/mediaplayerconnectivity-0.8.3-fx+fl+mz+ns+zm.xpi](https://addons.mozilla.org/en-US/firefox/downloads/file/2285/mediaplayerconnectivity-0.8.3-fx+fl+mz+ns+zm.xpi)

---

### Post by Das Goat on 2007-06-17
> **tkrisz said:**
> Was that this one?
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)
Are you sure that there was no install button at the middle of the page?
If not here's the direct link:
[https://addons.mozilla.org/en-US/firefox/downloads/file/2285/mediaplayerconnectivity-0.8.3-fx+fl+mz+ns+zm.xpi](https://addons.mozilla.org/en-US/firefox/downloads/file/2285/mediaplayerconnectivity-0.8.3-fx+fl+mz+ns+zm.xpi)

Ok, I'm confused (that is normal). 

I followed the first link, installed the package. seemed fine. tried to launch NPR. Mplayer can't quite figure it out. It gives me an error saying that it can't resolve the [site name] of the npr.org program I am trying to play. (this is using the player that pops un in the browser).

when I tell the pop up to load the stand alone player, the dialog box pops up and asks if I want to open with mplayer. I say yes, but then it loads Totem. I don't know why. the first time, totem wanted to down load codex that played .wax files. These were restricted, but I said to do it anyway. It loaded the first one fine, then got caught in a loop loading the second one. It finally finished, and when I re-launched the stand alone player, this time it worked.

With one caveat: Totem says it is buffereing, takes a few seconds, then sits there doing nothing. From a time I almost got this working before, I remembered that at this point Totem is buffering the WHOLE segment. that means if the story is 3:50 long, then i have to wait until Totem downloads the whole thing, exactly 3:50 minutes later, then it will play. I can't figure out how to make it buffer like 15 seconds and then play. Does anyone have a clue? On the plus side, when the whole thing is downloaded, then the pause and RW and FF buttons work. the down side is that if  NPR is 2 hours long, i have to take 4 hours listening to it.

Oddly enough, this seems to only be a problem with NPR. Is i go to [www.live365.com](www.live365.com) Then the same kind of pop-up opens, I get the same error about not being able to resolve the URL of the channel I am playing, but it starts playing anyway and there is no delay. Weird huh?

:(

---

### Post by fabertawe on 2007-06-18
Can you give a link to the NPR file you are trying to play?

Paul

---

### Post by Das Goat on 2007-06-19
Sure, just go to [www.npr.org](www.npr.org)

Pick a show, I usually listen to "all things considered". Click the listen button.

The broswer player will try to load first, then I click the "Launch stand alone player"

this has been driving me crazy since I first tried to make the move to Ubuntu last year.

Thanks in advance.

---

### Post by fabertawe on 2007-06-20
> **Das Goat said:**
> Sure, just go to [www.npr.org](www.npr.org). Pick a show, I usually listen to "all things considered". Click the listen button.

I couldn't get this to play from the browser. The only thing that would play the stream at all was gxine (a xine frontend) after extracting the link and manually entering it. It seems the feed is embedded in some kind of XML file which may be of a Windows Media Player proprietary structure. I don't know much about these things though, hopefully someone else will have a better idea. Sorry :(

Paul

---

### Post by Das Goat on 2007-06-24
hey, thanks for trying.

Currently, I have the work around. Got to this thread: [http://ubuntuforums.org/showthread.php?t=340113&page=13](http://ubuntuforums.org/showthread.php?t=340113&page=13)

I now have a native Ubuntu distro, with a WinXP Virtual Box that I play NPR through.

---

### Post by Das Goat on 2007-06-24
Oh, just so you know, this seems to be the HARDEST stream to listen to. No matter where I look, I get the same answer. From 32 users to 64 bit users, no one can seem to get this stream to play like it should.

I am hoping that as 64 bit applications become the norm, eventually the stream will be easily read but common applications.

Until then, it is just one of the handful of applications that requires me to run a VM of WinXP. 

Lord, won't it be grand when we NEVER have to load Windows?

---

### Post by kzm. on 2007-06-25
may i ask how to get the standalone player installed?

---

### Post by kzm. on 2007-06-25
found it:
chmod +x ~/Desktop/RealPlayer10GOLD.bin
~/Desktop/RealPlayer10GOLD.bin
sudo mv ~/RealPlayer /usr/local/realplayer32
sudo ln -s /usr/local/realplayer32/realplay /usr/local/bin/realplay
realplay

[https://help.ubuntu.com/community/FirefoxAMD64FlashJava](https://help.ubuntu.com/community/FirefoxAMD64FlashJava)

---

### Post by Das Goat on 2007-06-27
dasgoat@dasgoat-laptop:~$ chmod +x ~/Desktop/RealPlayer10GOLD.bin
dasgoat@dasgoat-laptop:~$ ~/Desktop/RealPlayer10GOLD.bin
bash: /home/dasgoat/Desktop/RealPlayer10GOLD.bin: No such file or directory

Huh? what did you do?

---

### Post by Das Goat on 2007-06-27
dasgoat@dasgoat-laptop:~/Desktop$ chmod +x RealPlayer10GOLD.bin
dasgoat@dasgoat-laptop:~/Desktop$ sudo mv ~/RealPlayer /usr/local/realplayer32
Password:
mv: cannot stat `/home/dasgoat/RealPlayer': No such file or directory
dasgoat@dasgoat-laptop:~/Desktop$ 


Still no Joy :-(

---

