---
title: "simple64: testers wanted"
date: 2006-09-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by kuja on 2006-09-27
**[SIZE="4"]Survey[/SIZE]**
Okay, I've written up a pretty little survey. If you use and/or like simple64, would you mind filling it out? Pretty please :D
[http://www.xnowherex.net/simple64/survey.html](http://www.xnowherex.net/simple64/survey.html)


Okay, so I started a project a while ago under the uncreative, generic name simple64. It provides a simple cli interface for installing a variety of programs.

Whether you're an Ubuntu N00b or you really know your way around, give it a try! I find that it beats doing things manually, and I definitely know my way around 8)

Right now it supports installation of the following programs: Adobe Acrobat Reader, Brasero(formerly bonfire), dvd::rip, Firefox32, Adobe Flashplayer, Sun Java(32-bit version), Listen, Mplayer32 (w/ or w/out win32 codecs), Opera, PartImage, Rar, Skype, Wengophone, and Wine.

**[SIZE="4"]Known Issues[/SIZE]:**
At the moment, I think there might be an issue with starting it from the GNOME menu ... not a major problem. Just start it from the terminal.

**[SIZE="4"]How to Install it:[/SIZE]**
For information on how to install it, click [this link.](http://www.xnowherex.net/simple64/index.php)
(Note: I keep it off this page because it's much easier to keep things up to date if I keep that on my own webspace ... in fact, it updates itself!)

**[SIZE="4"]How to Run it:[/SIZE]**
Select Simple64 from the Kmenu>System, in GNOME, it is under System>Administration. Alternatively, you can run it from a terminal by simply typing "simple64" and pressing enter.

**[SIZE="4"]If you encounter a problem[/SIZE]**
Reply to this thread with a description of the problem, be sure to attach the file /var/log/simple64.log to the post.

---

### Post by Kilz on 2006-09-27
Im testing it on a 64bit Ubuntu dapper virtual machine. so far its going ok, im going to instaall all the mentioned applications and then test them. Ill post back here in a little with how they behave.
Wengophone only launches if I open a terminal and type in sudo wengophone.
Firefox32 didnt install
mplayer didnt install

---

### Post by kuja on 2006-09-27
Hey Kilz, seeing as you seem to be the only person testing, I've got an update up, all the links in the post are updated. Fixed some bugs, mostly involving repository handling.

---

### Post by Pinoy915 on 2006-09-27
I had most of the things installed already but I have installed rar successfully. When I tried to install DVDrip, it just hangs.

---

### Post by kuja on 2006-09-27
I've looked into things, and I just uploaded 0.6.2.
Keep in mind, the Interface WILL stop responding, that's another problem that I'm having trouble finding a solution for.

---

### Post by Pinoy915 on 2006-09-27
Actually, I think it's just the server. I can't even install DVDrip correctly from the sticky posted. I was trying to use wget but it's not connecting at all. Oh, and for GNOME, the simple64 is under System/Administration.

---

### Post by kuja on 2006-09-27
That's entirely possible. I noticed that it wasn't downloading properly, but hadn't tested again after I changed a few things. At any rate, the next release will have better error handling...

Anyhow, thanks for telling me where it's at under GNOME, I had forgotten. I did a (GNOME) Ubuntu install earlier on another partition for testing purposes... allowed me to fix quite a lot of stuff today.

---

### Post by Kilz on 2006-09-28
> **kuja said:**
> That's entirely possible. I noticed that it wasn't downloading properly, but hadn't tested again after I changed a few things. At any rate, the next release will have better error handling...

Anyhow, thanks for telling me where it's at under GNOME, I had forgotten. I did a (GNOME) Ubuntu install earlier on another partition for testing purposes... allowed me to fix quite a lot of stuff today.

Vmware is another good tool for testing, if you dont want to install to hard disk.
I just downloaded 0.6.2 and tested firefox32, it instals great. But the flash plugin doesnt work. Neither dose the java plugin. I cant even find the plugin files.
There is no icon for simple64 in the menu, not a biggie, but thought Id mention it for the future.
Installing the Adobe acrobat froze it, after 15 minutes I killed it.

---

### Post by kuja on 2006-09-28
Major update guys, 0.6.3, not sure how many problems I fixed. Mostly I was just putting in better error handling and for the most part better logging, but that still has a few "human errors" in it to remove, but overall, it should be worth looking into. Groundwork for building multiple packages (dapper + edgy) is there also.

---

### Post by jngtt on 2006-09-29
nice app but it keeps on sticking at the repos

i will keep an eye out on this thread on future updates

nice work :D :D

---

### Post by fatsheep on 2006-09-29
Good work, this should be useful for new 64-bit users.

---

### Post by learnjunk on 2006-09-30
I have installed Ubuntu couple of days back and tryong to Install Skype, Flash plugin, and some media player to play music. I tried doing from several sources but nothing is working so far. This application seems good to have all the incompatible applications for 64 bit processors at one place. However I was NOT able to succeed so far...

Followig is the inforamtion form log file:


##Running Flashplayer Installation##install_flash_player_7_linux/
install_flash_player_7_linux/flashplayer.xpt
install_flash_player_7_linux/flashplayer-installer
install_flash_player_7_linux/Readme.htm
install_flash_player_7_linux/Readme.txt
install_flash_player_7_linux/libflashplayer.so

##Ending FlashPlayer Installation##
##Running Firefox Installation##
##Running Mplayer32 Installation##
##Running Java Installation##
##Running Mplayer32 Installation##
##Running Mplayer32 Installation##
##Start Skype Installation##
##Start Skype Installation##
##Start Skype Installation##
##Start Skype Installation##
##Running Mplayer32 Installation##
##Running Rar Installation##

Every time I start trying to install any applicaion it is getting stuck...

Thank you

---

### Post by kuja on 2006-09-30
I'm thinking you're just not being patient, perhaps.

As I stated, in bold, in the main post, When the GUI stops responding, it HAS NOT stopped. It's just working. I'm looking for a resolution to this, I've got a good idea why it's doing it, it's just a matter of figuring out how to fix the problem.

---

### Post by Kilz on 2006-09-30
> **kuja said:**
> I'm thinking you're just not being patient, perhaps.

As I stated, in bold, in the main post, When the GUI stops responding, it HAS NOT stopped. It's just working. I'm looking for a resolution to this, I've got a good idea why it's doing it, it's just a matter of figuring out how to fix the problem.

If you cant stop it from happening , can you put up something that says "wait working".

---

### Post by kuja on 2006-09-30
Yes. I should do that, I guess that's a fairly simple message to deliver, though, painting of the application stops entirely while it's working, so much as say, minimizing the app and restoring it to original size, blanks it :\

---

### Post by R3linquish3r on 2006-10-01
Hey Kilz I setup VM Server on my x64 desktop but it wont let me setup an x64 virtual mahine. Didd you have to do anything special to be able to do that?

---

### Post by /carlito on 2006-10-01
I got an error on running the program for the first time.
```
python: can't open file '/usr/lib/simple64.py': [Errno 2] No such file or directory

```

I had to link the file from /usr/lib/simple64 to /usr/lib o fix it. ```
sudo ln -s /usr/lib/simple64/simple64.py /usr/lib
```

---

### Post by /carlito on 2006-10-01
I've encountered some more errors.

```
##Running Firefox Installation##
Traceback (most recent call last):
  File "/usr/lib/simple64.py", line 96, in Install
    self.installFirefox32()
  File "/usr/lib/simple64.py", line 286, in installFirefox32
    message = message + " Failed\n"
UnboundLocalError: local variable 'message' referenced before assignment

```

```
##Running Mplayer32 Installation##
Traceback (most recent call last):
  File "/usr/lib/simple64.py", line 102, in Install
    self.installMplayer32()
  File "/usr/lib/simple64.py", line 404, in installMplayer32
    if mp32downloaded == "success":
NameError: global name 'mp32downloaded' is not defined

```

```
Traceback (most recent call last):
  File "/usr/lib/simple64.py", line 98, in Install
    self.installSunJava5BrowserPlugin()
  File "/usr/lib/simple64.py", line 346, in installSunJava5BrowserPlugin
    self.appendmessage("Installing debconf graphical frontend...")
AttributeError: appendmessage

```

```
Traceback (most recent call last):
  File "/usr/lib/simple64.py", line 108, in Install
    self.installRar()
  File "/usr/lib/simple64.py", line 488, in installRar
    self.labelMessage.setText(message)
NameError: global name 'message' is not defined

```

No Errors where found in /var/log/simple64.log.

Acroread and Opera installed without a hitch.

---

### Post by kuja on 2006-10-01
Yeah... I rewrote a lot of it the other day, so it only figures that I missed something, (especially considering that I was up til ten working on it, and I had to be up at 4 the next day :rolleyes:)  thanks, I'll have that stuff fixed in a jiffy... Fixed, I'll upload the changes soon.

Oh, and in my haste a few days ago, I botched up the logging. blah. Oh well, at least it's fixed now.

---

### Post by Kilz on 2006-10-01
> **R3linquish3r said:**
> Hey Kilz I setup VM Server on my x64 desktop but it wont let me setup an x64 virtual mahine. Didd you have to do anything special to be able to do that?

My vm workstation lets me setup a 64bit Ubuntu when setting up a vm.

---

### Post by /carlito on 2006-10-01
> **kuja said:**
> Yeah... I rewrote a lot of it the other day, so it only figures that I missed something, (especially considering that I was up til ten working on it, and I had to be up at 4 the next day :rolleyes:)  thanks, I'll have that stuff fixed in a jiffy... Fixed, I'll upload the changes soon.

Oh, and in my haste a few days ago, I botched up the logging. blah. Oh well, at least it's fixed now.

No problem! I'll check the other apps tomorrow...if I can find some time...

---

### Post by kuja on 2006-10-01
Version 0.6.4 Is up now. Please download/install it before doing any testing. 
It includes many fixes to logging, several small bugfixes, cleaned up a bit of the code.

Two things I still need to work on are fixing the main problem (the painting issue), and error handling with the downloading...

---

### Post by kuja on 2006-10-03
I'm going to put up 0.6.5 in a few minutes.
It has:
  * some small fixes
  * fixed the /usr/sbin/simple64 shell script
  * Redid the building scripts - edgy build now available :D
  * Pointed Wine at the latest release, 0.9.22 as 0.9.21 is no longer a valid link

However, this is just a hold-me-over. There's a major release coming soon. I'll give you a hint on its changes-to-be:

"You know how the GUI hangs currently when installing"
:D:D:D

---

### Post by kuja on 2006-10-03
Even though it doesn't look like anyone has had a chance to try 0.6.5 yet, I've already got 0.7.0 out the door!

The promised fixed for the GUI not responding while it works is indeed fixed. This leaves only a couple of things to do yet. One: I need better error handling for the downloads. Two: I need to finish implementing the mplayer32 installer, as it doesn't do any browser plugins yet. Three: I don't think there is a three.

---

### Post by JRaz on 2006-10-03
Installation went fine but installation of skype seemed to hang (15mins+) on this display (updating repos).

---

### Post by tymek666 on 2006-10-03
Thx a lot! It works great (at least 0.70 :) ).

---

### Post by JRaz on 2006-10-03
firefox32 went without a hitch, still no skype though :(

---

### Post by kuja on 2006-10-03
> **JRaz said:**
> Installation went fine but installation of skype seemed to hang (15mins+) on this display (updating repos).

I hear ya'. I ran into a similar problem, though it wasn't in the skype install. Looking at it do it in a terminal shows you what it's really doing, and it's really, really odd. The command the program uses where it's taking forever at is a regular "apt-get update"... but it just goes, and goes, really, really slow, taking forever at all the stuff that apt-get update normally does much faster.


Edit: I just took a look at what skype was doing, and I got an error. I fixed it and the install went without a hitch.
Expect 0.7.1 within a few minutes.

---

### Post by kuja on 2006-10-03
Version 0.7.1 is up

2 changes this time:
  * Skype is back to installing without a hitch.
  * Install button is disabled during the install process.

---

### Post by holy_bazooka on 2006-10-03
hi.
i am running edgy.
i tried to install mplayer32 but it gave the following error:

```
(Reading database ... 118205 files and directories currently installed.)
Unpacking mplayer32 (from mplayer32_1.0pre7-1_amd64.deb) ...
dpkg: error processing mplayer32_1.0pre7-1_amd64.deb (--install):
 trying to overwrite `/usr/lib32/liblzo.so.1.0.0', which is also in package ia32-libs-openoffice.org
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 mplayer32_1.0pre7-1_amd64.deb
```

so i backed up that file (lilzo) and after taking the package from /tmp/ did a force-overwrite.

now it gives the error :

```

mplayer32: error while loading shared libraries: libgnutls.so.13: cannot open shared object file: No such file or directory
```

so then i uninstall ia32-libs-openoffice and reinstall mplayer32, it gives this error:

```

mplayer32: error while loading shared libraries: libaudio.so.2: cannot open shared object file: No such file or directory

```

so uninstalled mplayer32 and reinstalled ia32-libs-openoffice.org
my question is whats going on here?

==>also posting this on wmv9 on amd64 thread

---

### Post by kuja on 2006-10-03
> **holy_bazooka said:**
> hi.
i am running edgy.
i tried to install mplayer32 but it gave the following error:

```
(Reading database ... 118205 files and directories currently installed.)
Unpacking mplayer32 (from mplayer32_1.0pre7-1_amd64.deb) ...
dpkg: error processing mplayer32_1.0pre7-1_amd64.deb (--install):
 trying to overwrite `/usr/lib32/liblzo.so.1.0.0', which is also in package ia32-libs-openoffice.org
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 mplayer32_1.0pre7-1_amd64.deb
```

so i backed up that file (lilzo) and after taking the package from /tmp/ did a force-overwrite.

now it gives the error :

```

mplayer32: error while loading shared libraries: libgnutls.so.13: cannot open shared object file: No such file or directory
```

so then i uninstall ia32-libs-openoffice and reinstall mplayer32, it gives this error:

```

mplayer32: error while loading shared libraries: libaudio.so.2: cannot open shared object file: No such file or directory

```

so uninstalled mplayer32 and reinstalled ia32-libs-openoffice.org
my question is whats going on here?

==>also posting this on wmv9 on amd64 thread

Congratulations, you seem to be the first person who has tested on edgy! (that I know about anyway) The first problem is that two packages can never have the same file, that creates a conflict because which one gets to install their version of the file to that location? 

The second problem is saying that it's missing the file libaudio.so.2, in other words, that the file it's looking for doesn't exist. The reason why it doesn't exist is because you uninstalled ia32-libs-openoffice.org, the provider of the file libaudio.so.2.

I'll help look into a fix for the problem, but it looks like the real problem hear is that mplayer32 statically linked many files, including gnutls, and the edgy version of ia32-libs-openoffice includes that file (whereas I don't think dapper did). The solution may be some sort of force install.

I'm not running Edgy, at least not yet, so I want you to try this for me:

```

sudo apt-get install ia32-libs-openoffice
wget http://folk.ntnu.no/grannas/debs/mplayer32_1.0pre7-1_amd64.deb /tmp/mplayer32_1.0pre7-1_amd64.deb
dpkg --install --force-overwrite  /tmp/mplayer32_1.0pre7-1_amd64.deb

```

I can't guarantee that this will work, but I think it's worth a shot.

---

### Post by holy_bazooka on 2006-10-04
already did that.
gives the second error. one about gnutls.
so i copied the linlzo(ia32 one) to my home dir and did a force install. it didn't work. i copied the orig liblzo(ia32) over the mplayer 32 one that didn't work either. i would give u the exact errors but i closed that terminal long time ago.

open to suggestions....

edit:
i did try some 'things' with dpkg-divert couldn't make any sense of it. i would appreciate some pointers on that.

---

### Post by kuja on 2006-10-04
Well, Mplayer32 was built specifically for Dapper, until there is an Edgy build of it I'm not sure if you're going to get too lucky. If you don't mind doing a little work, it might be better to try using mplayer from SVN. It seems to be rather stable at the moment, and it solves the problem with more grace than does the mplayer32 package. It's a real 64-bit build... Look at this post if you're interersted : [http://www.ubuntuforums.org/showthread.php?t=270066](http://www.ubuntuforums.org/showthread.php?t=270066)

---

### Post by Foechoer on 2006-10-04
Howdy,

i used yout simple64 and it's a very handy tool,  specialy for new ubuntu64 users..  In stead of al the tutorials this is the best all-in-one-tool.  
But still I have a idea..  

Could you make like an autoupdate tool for simple64 itself?   I had this problem when you made the new version, but first I had still installed the older version and had no idea there was a new one..

I'm sorry if there is some bad spelling, I live in Belgium and I'm 16,5 years old.
What's the problem betwen age and Ubuntu,  it's for all human beings no?;)

---

### Post by kuja on 2006-10-04
Well, I suppose I could implement something like that, in fact, I had already been thinking about it before you mentioned it. Unless I later put it into a repository of some sort, this would be a very solid approach to the problem.

---

### Post by HeresJohnny on 2006-10-04
It's a good set of tools, Kuja.  When I install Ubuntu on my home computer (currently now only on my laptop), I'll use Simple to get everything set up.  Man, I wish I had that when I first got Ubu'ed...:-D 

Maybe you could do a Knight Rider light thing while it's installing, so folks know it's still working.  Flashing lights moving back and forth rhythmically... now that's sexy!

---

### Post by JRaz on 2006-10-04
> **kuja said:**
> Version 0.7.1 is up

2 changes this time:
  * Skype is back to installing without a hitch.
  * Install button is disabled during the install process.

Skype installation went without a hitch. However I go to Applications and its not there, check edit menus and still no luck. So i fire up terminal and type 'skype' and I get the following error message.

raz@razbuntu:~$ skype
skype: error while loading shared libraries: libaudio.so.2: cannot open shared object file: No such file or directory

Any help would be appreciated.

---

### Post by kuja on 2006-10-04
Try installing ia32-libs-openoffice.org ```
sudo apt-get install ia32-libs-openoffice.org
```and see if you still get this error. I might need to get the program to install that along with skype.... Tell me how it goes.

---

### Post by JRaz on 2006-10-04
Thanks the package worked perfectly. One question why did I need an open office package to use Skype, especially since I have writer installed without that package.

---

### Post by kuja on 2006-10-04
> **JRaz said:**
> Thanks the package worked perfectly. One question why did I need an open office package to use Skype, especially since I have writer installed without that package.
I guess it's because that's where the devs felt like putting that file, not really sure why OOo is working without it, but I bet sound in OOo wouldn't work if you tried it... before installing that package that is.

---

### Post by kuja on 2006-10-04
0.7.2 is now up
* added ia32-libs-openoffice.org for skype
* disabled installation of mplayer32 in edgy
* disabled clicking on the selection box when it's installing
* various small fixes
******Added an Auto-updater********** (not sure if it works yet, but we'll see soon won't we?)

---

### Post by weird_c00kie on 2006-10-05
i tried doing it through the terminal first... came up with errors

then i tried downloading one of the packages. seems to install fine, but it doesn't come up under System > Administration :/


with the terminal commands, i get up to the last one and then it shows this:

> mp/simple64-data_1_amd64.deb
dpkg: error processing /tmp/simple64_0.7.2-dapper_amd64.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing /tmp/simple64-data_1_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /tmp/simple64_0.7.2-dapper_amd64.deb
 /tmp/simple64-data_1_amd64.deb


---

### Post by kuja on 2006-10-05
Do you get those errors when trying to install simple64, or after having it installed?

If you get those errors while trying to install it, well, it's looking like those files (/tmp/.....) don't exist, which would mean the download of the packages via wget failed?

One thing that you might try is downloading the files manually with your browser, and installing them from the GUI. Do simple64-data_1_amd64.deb first, then simple64-dapper_0.7.2_amd64.deb second.

---

### Post by weird_c00kie on 2006-10-05
i get up to the last command, the
> sudo dpkg -i /tmp/simple64_0.7.2-dapper_amd64.deb /tmp/simple64-data_1_amd64.deb
and then it gives me that

i'll try the wget commands again, but i'm pretty sure they finished successfully

*edit*
i tried it again. the wgets work fine. the last command is the only thing that doesn't work.


could it be that i don't have the 'daper' version or whatever? how do i check for that?i just know i have ubuntu 6.06 :p

---

### Post by kuja on 2006-10-05
5.04 = hoary, 5.10 = breezy, 6.06 = dapper, 6.10 = edgy

---

### Post by weird_c00kie on 2006-10-05
ah, thank you. so it's not that. such a hassle, this 64bit processor crap :(
i've regretting buying it since the start.
should've gone with a single core intel instead...

---

### Post by StandardBlueCaboose on 2006-10-05
It -might- be easier to just use the 32-bit Ubuntu... I know a lot of people here hate the though of it, but it might be easier for you. There were times I wanted to turn back... I still kind of do. Do you know how impossible it is to install ZSnes on a 64-bit OS with Xgl?

---

### Post by weird_c00kie on 2006-10-05
i don't even know what zsnes is, unless i deduce by the name that it's a snes emulator, in which case it would be inconsequential to me, but i get your point. is the 32bit version that much more limited in terms of functionality?

i mean, it would suck an awful lot having to do all the updates again, but i just keep running from one brick wall into another. if i didn't have experienced linux-loving friends coming online and pitching a helping hand at me from time to time and everyone else here, i'd be back to my XP comfort zone already :p

---

### Post by kuja on 2006-10-05
> **StandardBlueCaboose said:**
> It -might- be easier to just use the 32-bit Ubuntu... I know a lot of people here hate the though of it, but it might be easier for you. There were times I wanted to turn back... I still kind of do. Do you know how impossible it is to install ZSnes on a 64-bit OS with Xgl?
Do you know how impossible (or rather, difficult) it is to get XGL working with any opengl app... insanely so, thus why I don't use XGL.

> **weird_c00kie said:**
> i don't even know what zsnes is, unless i deduce by the name that it's a snes emulator, in which case it would be inconsequential to me, but i get your point. is the 32bit version that much more limited in terms of functionality?

i mean, it would suck an awful lot having to do all the updates again, but i just keep running from one brick wall into another. if i didn't have experienced linux-loving friends coming online and pitching a helping hand at me from time to time and everyone else here, i'd be back to my XP comfort zone already :p

You've already got a nice start, not much point in stopping now the way I see it.

Also, with regards to the problem, I've changed the little script on the front post, might be worth a try, I'm *hoping* it will work for you, even though I don't have a 100% solid idea of what's going on there.


In other news though, 0.7.3 is up
It contains one small fix for the auto-updater, and not much else was changed, but it should be a decent opportunity to test the auto-updater, I think.

---

### Post by StandardBlueCaboose on 2006-10-05
> **kuja said:**
> Do you know how impossible (or rather, difficult) it is to get XGL working with any opengl app... insanely so, thus why I don't use XGL.

I know, it's crazy. At least from what I've experienced. It's pretty darn frustrating when I have to chroot to a 32-bit root and run something on the underlying X-server, and all that crazy whatnot. 

The cube is just so pretty though... :-D

Edit: Btw, I don't really know the difference (in performance) between 32-bit and 64-bit, I was hoping somebody else would take over and explain it more thoroughly. I just suggested it because I'd imagine it would be easier.

---

### Post by kuja on 2006-10-05
I would rather watch a Strogg's head explode, or similar :D

---

### Post by kuja on 2006-10-05
> **StandardBlueCaboose said:**
> I know, it's crazy. At least from what I've experienced. It's pretty darn frustrating when I have to chroot to a 32-bit root and run something on the underlying X-server, and all that crazy whatnot. 

The cube is just so pretty though... :-D

Edit: Btw, I don't really know the difference (in performance) between 32-bit and 64-bit, I was hoping somebody else would take over and explain it more thoroughly. I just suggested it because I'd imagine it would be easier.

Wait a minute, that is pretty crazy o.O 32-bit chroot?  Why would you need one of those again exactly? I've not dealt with chroots outside of debootstrapping an install, since..... Breezy?

---

### Post by StandardBlueCaboose on 2006-10-05
> **kuja said:**
> Wait a minute, that is pretty crazy o.O 32-bit chroot?  Why would you need one of those again exactly? I've not dealt with chroots outside of debootstrapping an install, since..... Breezy?

Haha, well, to be honest, I don't really know either. I tried a lot of crazy things trying to get that to work. I had to compile from source into 32-bit and when I ran any other way it always segfaulted. I was just trying to follow what they were telling me on the zsnes forums. I just ended up getting really confused and frustrated. 

I'm still a noob. I probably will be for a good while yet.

Edit: This is really off-topic, though...

---

### Post by JRaz on 2006-10-05
Just a heads up but skype is out of beta now. Any chance you could update your program to include it? The change log is here [http://www.skype.com/download/skype/linux/changelog.html](http://www.skype.com/download/skype/linux/changelog.html)

---

### Post by kuja on 2006-10-05
Version 0.7.4 is up.

 * Made the descriptions version agnostic

data Version 2 is up

 * Updated Skype URL

---

### Post by JRaz on 2006-10-06
slight problem, went to install version 0.7.4 by downloading the 2 debs.

simple64_0.7.4-edgy_amd64.deb - wont install without the data file installed

simple64-data_2_amd64.deb - says failed to install package, and the terminal part doesn't go any further than unpacking.

---

### Post by tomdkat on 2006-10-06
> **kuja said:**
> I'm looking for a resolution to this, I've got a good idea why it's doing it, it's just a matter of figuring out how to fix the problem.How about a "wait cursor":

[http://lists.trolltech.com/qt-interest/2003-06/thread00004-0.html](http://lists.trolltech.com/qt-interest/2003-06/thread00004-0.html)
[http://lists.trolltech.com/qt-interest/2001-02/thread00920-0.html](http://lists.trolltech.com/qt-interest/2001-02/thread00920-0.html)

EDIT:  Here is an example of a wait cursor in Python using Qt:

[http://www.commandprompt.com/community/pyqt/x7601](http://www.commandprompt.com/community/pyqt/x7601)

Look above the "Saving Unicode Files" table.

I just installed simple64 and installed Opera without any problems!  Thanks!

EDIT #2: Ok, I just installed MPlayer32 and the installation went fine but I think I'm still running the 64-bit version I had installed previously.  Where do I find the right app to run to run it?  When I run "mplayer32" in a terminal, I get the command line options.  I think the Ubuntu menu uses gmplayer to run the GUI version of mplayer, but I can't find a similar ap for Mplayer32.

Also, I installed the Flashplayer and it reported installing for Opera but Opera prompts me to install the plugin each time I view a page with Flash content.  Any ideas?

Peace...

---

### Post by kuja on 2006-10-06
> **JRaz said:**
> slight problem, went to install version 0.7.4 by downloading the 2 debs.

simple64_0.7.4-edgy_amd64.deb - wont install without the data file installed

simple64-data_2_amd64.deb - says failed to install package, and the terminal part doesn't go any further than unpacking.

Really? Try removing both, then installing simple64-data FIRST (if you try to install it second, it could leave both packages broken, possibly, I've not tried that though). 

If this is not the case then I really do need to look into it though.

> **tomdkat said:**
> How about a "wait cursor":

[http://lists.trolltech.com/qt-interest/2003-06/thread00004-0.html](http://lists.trolltech.com/qt-interest/2003-06/thread00004-0.html)
[http://lists.trolltech.com/qt-interest/2001-02/thread00920-0.html](http://lists.trolltech.com/qt-interest/2001-02/thread00920-0.html)

EDIT:  Here is an example of a wait cursor in Python using Qt:

[http://www.commandprompt.com/community/pyqt/x7601](http://www.commandprompt.com/community/pyqt/x7601)

Look above the "Saving Unicode Files" table.

I just installed simple64 and installed Opera without any problems!  Thanks!

EDIT #2: Ok, I just installed MPlayer32 and the installation went fine but I think I'm still running the 64-bit version I had installed previously.  Where do I find the right app to run to run it?  When I run "mplayer32" in a terminal, I get the command line options.  I think the Ubuntu menu uses gmplayer to run the GUI version of mplayer, but I can't find a similar ap for Mplayer32.

Also, I installed the Flashplayer and it reported installing for Opera but Opera prompts me to install the plugin each time I view a page with Flash content.  Any ideas?

Peace...

Thanks for the idea, I'll probably implement that when I get time (tomorrow night or Sunday)

I haven't used mplayer32 in a while, well, not since I switched to SVN, so I forget where exactly it installs to, but it does have a gmplayer thing, maybe its symlink is in /usr/local/bin? 

Hmm, As per Opera, seeing as it worked fine for me, I'll remove the plugin from /usr/lib/opera/plugins and try a reinstall of it myself, then check back with you, maybe I broke something somewhere along the line? Also, be sure the site doesn't have a flash 8+ requirement, as simple64 is installing flash7 (of course.)

Oh, and be sure that it actually installed okay, I think you can see the installed plugins by using the url "opera:plugins"

---

### Post by JRaz on 2006-10-06
Removed the old simple64 and the new one installed just fine. However I cant get flash to work, it says its installed but no flash sites work under firefox32. I know youtube for instance works on flash 7 so thats not the problem. Is there a way of viewing installed plugins in firefox.

---

### Post by kuja on 2006-10-06
> **JRaz said:**
> Removed the old simple64 and the new one installed just fine. However I cant get flash to work, it says its installed but no flash sites work under firefox32. I know youtube for instance works on flash 7 so thats not the problem. Is there a way of viewing installed plugins in firefox.
The url about:plugins

---

### Post by tomdkat on 2006-10-06
> **kuja said:**
> I haven't used mplayer32 in a while, well, not since I switched to SVN, so I forget where exactly it installs to, but it does have a gmplayer thing, maybe its symlink is in /usr/local/bin? I'll look there.  /usr/bin/gmplayer symlinks to the 64-bit version of mplayer.

> Hmm, As per Opera, seeing as it worked fine for me, I'll remove the plugin from /usr/lib/opera/plugins and try a reinstall of it myself, then check back with you, maybe I broke something somewhere along the line? Also, be sure the site doesn't have a flash 8+ requirement, as simple64 is installing flash7 (of course.)I don't think so. Even the [Adobe home page](http://www.adobe.com/) results in a prompt to install the Flash plugin.

> Oh, and be sure that it actually installed okay, I think you can see the installed plugins by using the url "opera:plugins"Looks like it didn't since "opera : plugins" (with no embedded spaces) didn't list it:

```
application/x-opera-nsplugin	-
/usr/lib/opera/plugins/libnpp.so
```

Any ideas?

Peace...

---

### Post by JRaz on 2006-10-07
Typed in about:plugins and like I thought there are no plugins installed which means flash isn't installing for me, any ideas?

---

### Post by kuja on 2006-10-07
Looks like I need to fix it tomorrow night...Thanks for letting me know JRaz, tomdkat.

---

### Post by tomdkat on 2006-10-07
Well, I was able to get Flash sort-of working with Opera last night.  I found the Flash shared library in /tmp:

/tmp/install_flash_player_7_linux.tar.gz
/tmp/install_flash_player_7_linux
/tmp/install_flash_player_7_linux/flashplayer.xpt
/tmp/install_flash_player_7_linux/flashplayer-installer
/tmp/install_flash_player_7_linux/libflashplayer.so

So, I copied libflashplayer.so to /usr/lib/opera/plugins and Flash applets now load.  They don't always run right but they at least load now.

Audio works, which is a good sign.

Peace...

---

### Post by Draknats on 2006-10-07
Hi.

Simple64 looks like quite a promising life/timesaver, but I've yet to get it working.

I download the package, and it appears to install fine, but afterwards it's not listed under System>Administration, and when I enter "simple64" into the terminal, it says that it's an invalid command.

Anyone have any idea as to why this isn't working?

This doesn't seem particularly relevant, but once the package downloads (using the terminal), it says that I lack the superuser privileges required in order to depackage it.  This is what it says:

22:35:01 (1.15 MB/s) - `/tmp/simple64-data_2_amd64.deb' saved [1574/1574]
dpkg: requested operation requires superuser privilege

And so, I simply go to the tmp folder and install it manually.  As previously stated, it appears to install seamlessly.

---

### Post by kuja on 2006-10-08
There are two packages. simple64-data, and simple64-dapper/edgy. You need to have both installed.

---

### Post by jbernardo on 2006-10-08
Great,
Just installed it and got acrobat and opera installed. the only strange thing is that I didn't get a adobe icon anywhere on the kmenu. But it works well when called from the command line or when I open a pdf file.
Now, if you added a nvidia-beta drivers installation it would also rock... :p

---

### Post by kuja on 2006-10-08
jbernardo, I think, for me at least, it put Adobe Reader's icon in the Office menu (KDE). 

Also, is there some 64-bit specific issue with the nvidia-beta drivers? If not, it really falls outside the projects goal, in which case, maybe asking tseliot to include it in his "envy" script would be more appropriate?

In other news, 0.7.5 is out. Flash install is fixed. It looks like I had never fully implemented it to begin with. My memory is kinda flaky like that... I went and implemented a wait cursor too. I redid much of the autoupdater. A manual update to the program is required. Most of the other changes are either code or organization related.

---

### Post by kuja on 2006-10-09
0.7.6 is up now too. Small changes related to the package itself.

---

### Post by MetalMusicAddict on 2006-10-09
Im installing Edgy 64 tomorrow on my 4600+. Ill test this out first thing.

---

### Post by compwiz18 on 2006-10-09
I'm gonna give this a shot.  I'll let you know how it goes.  And FYI, all the deb links in your original post don't work :P

EDIT: I take that back.  This first 2 don't, the third one does.

---

### Post by compwiz18 on 2006-10-09
OK:

My experience was basically not-so-simple.

I found a link that worked (the tarball), downloaded, extracted, and then ran simple64.py using the command **sudo simple64.py**.  Output logs are attached (one from my terminal output and the other log that you told me to attach (actually that didn't exist so I just attached simple64error.log instead)  If you need any more info or want me to test it again, just ask.

---

### Post by kuja on 2006-10-09
Great, I went and broke the links, okay. Now I feel like an idiot again. Yay.

Anyhow, they should be fixed now. Oh, and compwiz, if you want to do it from the tarball, the easiest thing to do is run ./auto.sh, assuming you have everything you need to build the package. (fakeroot, dpkg-deb, &c) That's because you can't directly run the program by just extracting the tarball, but the scripts (build.sh, build-data.sh, install.sh, simple64, and most importantly auto.sh) automate the process of building, installing, and running the package rather nicely.

---

### Post by compwiz18 on 2006-10-09
> **kuja said:**
> Great, I went and broke the links, okay. Now I feel like an idiot again. Yay.

Anyhow, they should be fixed now. Oh, and compwiz, if you want to do it from the tarball, the easiest thing to do is run ./auto.sh, assuming you have everything you need to build the package. (fakeroot, dpkg-deb, &c) That's because you can't directly run the program by just extracting the tarball, but the scripts (build.sh, build-data.sh, install.sh, simple64, and most importantly auto.sh) automate the process of building, installing, and running the package rather nicely.
OK, I'll give that a shot later.  Although I think I may have run auto.sh before simple64.py...I don't remember.

---

### Post by kuja on 2006-10-09
Rather than doing that, why not just install the packages now that the links are fixed?

---

### Post by compwiz18 on 2006-10-09
> **kuja said:**
> Rather than doing that, why not just install the packages now that the links are fixed?
Sounds good.

---

### Post by jbernardo on 2006-10-09
Kuja, Acrobat isn't in my office menu in kde, that was the first place I checked. I'll try again later with your new version.
Thanks!

---

### Post by kuja on 2006-10-09
Really? It is for me.... Screenshot attached

---

### Post by pony-tail on 2006-10-10
I just installed it , I will see how it goes

---

### Post by s_spiff on 2006-10-10
hey, installed the program successfully. Used it to install Firefox32. I got the 'try it out' msg. So I figured it was done. Then I went on to install Flash, and I got a error neither firefox nor opera was found on my pc, hence flash wasn't installed. :( what to do?

---

### Post by kuja on 2006-10-10
Well, at the moment, I have it set up so that it installs this 32-bit flash into a 32-bit browsers plugin directory. The fix is quite simply to install a 32-bit browser before installing flash, something which simple64 can also do. Firefox32 or Opera, take your pick. 

I've heard that ndiswrapper (I think that's the wrapper I'm thinking of...) is unstable , if what I heard is a load of FUD, somebody let me know, and I'll see what I can do about setting up simple64 to use it to get flash & friends working in a 64-bit browser. If it really is unstable however, then I'd rather wait until it stabilizes.

---

### Post by pentarinfosys on 2006-10-10
Just installed DD 64bit on a new Gateway laptop, so I'm trying simple64 out. Although I've been a Linux user for several years, this is my first 64bit machine, and the first Ubuntu install. (I was an OpenSUSE user, but its 64bit install kept coredumping on this hardware.)

I'll let you know what I come up with.

---

### Post by pentarinfosys on 2006-10-10
> **pentarinfosys said:**
> Just installed DD 64bit on a new Gateway laptop, so I'm trying simple64 out. Although I've been a Linux user for several years, this is my first 64bit machine, and the first Ubuntu install. (I was an OpenSUSE user, but its 64bit install kept coredumping on this hardware.)

I'll let you know what I come up with.

Well, that didn't do so good. After getting the package installed, I ran it to install Acroread. I let it sit for almost 20 minutes, and nothing happened. I quit out of the application. I don't have any other dataa, yet, but will try it again when I can grab some diagnostic data.

---

### Post by kuja on 2006-10-10
As the initial post says, the log is /var/log/simple64VERSION.log Where VERSION is the version #. Sometimes running simple64 from a terminal will let you see more information that you otherwise wouldn't see. Also, do keep in mind that the acroread download is not small by any means. It's like, 20 meg or something like that, and if I remember right the adobe website doesn't serve it out terribly fast, maybe 50kbs? But still, at that rate it should only take about 7 minutes, so perhaps something is wrong, do tell when you get the chance.

---

### Post by kuja on 2006-10-10
Simple64 version 0.7.7 has been uploaded, and it contains a small fix for the acrobat reader installation that was introduced while I was reorganizing some things to make the code a bit less redundant. 

At any rate, the Adobe Reader problem has been fixed. If anyone would care to try something for me, why not try updating simple64 simply by running it? I've personally never tried it so I don't know if it works or not, seeing as I'm always running the latest version (or often even newer yet 8))

---

### Post by StandardBlueCaboose on 2006-10-10
Let me just say that I finally got a chance to try out your program, and it was... well... friggin' sweet.

I have a few suggestions just for the heck of it. 

I have some repositories that sometimes work and sometimes don't. When they don't work it takes a long time to download stuff. So why not have "Update and upgrade repositories" as a button somewhere, so they don't have to update/upgrade 3 times to install rar, wine, and mplayer. 

I don't know what kind of icon you could have for it, but you might as well have something.

When I installed wine it told me something before the install. Then I forgot it by the end of the install... I think it should be after the install and copyable (made that word up). Since the whole point is simplicity and all.

Also... A progress bar? Not really necessary or anything... In fact I'm not even sure I would prefer it, but why not?

EDIT: Much awesomer idea than my other ones -- check boxes. Check the programs you want to install and click one button and they all install for you. This way requires one apt-get update/upgrade and it's even simpler. Also more Windows-like, which is what the people using this program most likely would prefer.

Double EDIT: I think this should be stickied soon.

---

### Post by tomdkat on 2006-10-10
Well, I just installed version 0.7.7 and and when I start it, it checks for updates and just sits there.  The wait cursor did work, though.  :)

Did I need to re-install the data file?

Peace...

---

### Post by kuja on 2006-10-11
Thanks for the feedback. Yeah, I know about Wine, that one popup is a temporary workaround until I find a better place to put that message. The reason why I don't just put it at the end is has to do with a technical issue with the PyQt bindings. 

I don't think a progressbar would be doable in many areas due to the way I am accomplishing the tasks (just a regular old apt-get in many areas). 

I think I might be able to do something about the enabling of the repositories. It has actually gotten some improvement, but I agree that it should be optional to update the repositories if you already have them enabled. (what the program is doing is checking that you have the right lines in your /etc/apt/sources.list, and then adding to it if it needs to, then updating afterwards). The way that I'm doing it at the moment is the reason I haven't already fixed it. I need to do something a bit more complicated for it.

As per the checkbox idea, I like the idea, and I'll look into it, though for some of this stuff it may overcomplicate things if I do.

I probably won't get a chance to work on any of this for a while though. I'm working on getting Edgy up and going right now. It looks like the cd I burned had some minor corruption issues, so that's hurting me right now. Plus, I'm also working on my resume and portfolio. I'm trying to get out of my current job and all, so the portfolio is priority #1 for the moment.

---

### Post by JRaz on 2006-10-11
> **kuja said:**
> Simple64 version 0.7.7 has been uploaded, and it contains a small fix for the acrobat reader installation that was introduced while I was reorganizing some things to make the code a bit less redundant. 

At any rate, the Adobe Reader problem has been fixed. If anyone would care to try something for me, why not try updating simple64 simply by running it? I've personally never tried it so I don't know if it works or not, seeing as I'm always running the latest version (or often even newer yet 8))

Opened 0.7.6 but it didnt detect an update :(

---

### Post by JRaz on 2006-10-11
Having a slight issue with Java, it says its installed (try it out etc) but I find no record of it installed in about:plugins (firefox32). The only possible issue is I didnt know what to select between GNOME and KDE since i dont use either so I pressed GNOME.

---

### Post by Linux&amp;Lizards on 2006-10-11
hey im trying it out now so far so good.

---

### Post by kuja on 2006-10-11
> **JRaz said:**
> Having a slight issue with Java, it says its installed (try it out etc) but I find no record of it installed in about:plugins (firefox32). The only possible issue is I didnt know what to select between GNOME and KDE since i dont use either so I pressed GNOME.

I guess I need to work on the auto-updater some more, oh well, no biggie. As per the java installation, seeing as you're having a problem, can I see your /var/log/simple640.7.7.log file? Also, check if there is a file libjavaplugin.so or similar in your /usr/local/firefox32/plugins directory.

---

### Post by JRaz on 2006-10-11
log file is attached, and there is no java plugin in the plugins folder.

---

### Post by kuja on 2006-10-11
Alrighty, I've spotted the problem, I'll have a fix up for it soon.

---

### Post by kuja on 2006-10-12
0.8.0 is  up
 * Completely re-wrote the repository handling functions
 * Repositories only update if the sources.list file is modified by the program
 * Fix to the Java Plugin installation.
 * Possibly other small fixes

Let me know if there are any problems with the repositories section, it really hasn't seen much testing.

data 3 is up
 * Added a url

---

### Post by JRaz on 2006-10-12
still no luck with java, i tried running simple64 from terminal and saw this error.

cp: missing destination file operand after `/usr/lib/jvm/ia32-jaa-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so'

---

### Post by kuja on 2006-10-12
d'oh!! Curse my absentmindedness! I've got it fixed this time though! I think o_O ... 0.8.1 is up. I repeat, 0.8.1 is up.

Edit: I _promise_ that the java plugin installation for firefox32 goes smooth now :)

---

### Post by JRaz on 2006-10-12
no errors in the java installation this time, but still no firefox32 plugin :(. my log is attached if it helps.

---

### Post by kuja on 2006-10-12
that's weird, well, I did upload it with a small fix not long after the original upload. Try redownloading/removing/reinstalling simple64 and see if it will do it for you, because at this point it's doing it fine for me.

---

### Post by JRaz on 2006-10-13
removed simple64 and java and did a reinstall but still no luck.

---

### Post by kuja on 2006-10-13
With this reinstall though, did you *redownload*? That was the whole point really. I'll look into it, but everything looks right...

```
		self.appendMessage("Downloading/Installing 32-bit Sun Java binaries...")
		os.system("sudo apt-get --yes --force-yes install ia32-sun-java5-bin >> " + self.logfile)
		os.system("update-alternatives --set java  /usr/lib/jvm/ia32-java-1.5.0-sun/jre/bin/java")
		self.appendMessage(" Done\n")
		
		if os.path.isdir("/usr/local/firefox32/plugins"):
				installed = True
				if os.path.isfile("/usr/lib/jvm/ia32-java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so"): 
					os.system("cp /usr/lib/jvm/ia32-java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/local/firefox32/plugins")
					self.appendMessage("Java Plugin installed for Firefox32\n")
				else:
					self.appendMessage("Error! Sun Java 5 not installed properly!!!\n")
		if os.path.isdir("/usr/lib/opera/plugins"):
			try:
				installed = True
				open("/usr/lib/jvm/ia32-java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so")
				self.appendMessage("Java for Opera instructions placed in your home directory.\n")
				os.system("cp /usr/lib/simple64/resources/JavaForOpera.txt " + self.home)
			except IOError:
				self.appendMessage("Error! Sun Java 5 not installed properly!!!\n")
		if not installed:
			self.appendMessage("Simple64 could not install java plugin.\n")
		
		self.appendMessage("Java Install completed. Try it out!")
		self.log("##Ending Java Installation##")
```

---

### Post by StandardBlueCaboose on 2006-10-13
I just downloaded the newest version like 5 minutes ago. Firfox32 didn't install (that I'm aware of, what's the best way to open it?) and so my java plugin also didn't work. (I have no firefox32 folder in my /usr/local/ btw)

You promised!

---

### Post by kuja on 2006-10-14
eeeeeeeeeee............. I'll look into it when I get home from work in about 14 hours, besides, my promise was regarding the Java code. Maybe a link for Firefox32 is out-of-date or something?

---

### Post by JRaz on 2006-10-14
I went to synaptic and removed java and simple64. I then re downloaded simple64. Installed simple 64 and then java.

---

### Post by kuja on 2006-10-15
> **StandardBlueCaboose said:**
> I just downloaded the newest version like 5 minutes ago. Firfox32 didn't install (that I'm aware of, what's the best way to open it?) and so my java plugin also didn't work. (I have no firefox32 folder in my /usr/local/ btw)

Also, If I'm going to be able to figure out what's going on, I _NEED_ to see the logfile...

You promised!
> **JRaz said:**
> I went to synaptic and removed java and simple64. I then re downloaded simple64. Installed simple 64 and then java.

That should do it. I guess I'll have to experiment from a clean install later or something, even though I really don't have the bandwidth to be doing that.

---

### Post by Qwertinsky on 2006-10-15
I installed this today and it took several attempts before it was sucsessful

The command  "sudo apt-get install ubuntu-minimal python2.4-qt3 && wget -O /tmp/simple64-data_3_amd64.deb [http://www.xnowherex.net/ubuntu/simple64-data_3_amd64.deb](http://www.xnowherex.net/ubuntu/simple64-data_3_amd64.deb) && dpkg -i /tmp/simple64-data_3_amd64.deb && wget -O /tmp/simple64-dapper_0.8.1_amd64.deb [http://www.xnowherex.net/ubuntu/simple64-dapper_0.8.1_amd64.deb](http://www.xnowherex.net/ubuntu/simple64-dapper_0.8.1_amd64.deb) && dpkg -i /tmp/simple64-dapper_0.8.1_amd64.deb"

Ended part way through with some message about needing to be superuser to procede and I did use sudo and enter my password?](*,) 

[http://www.xnowherex.net/ubuntu/simp....8.1_amd64.deb](http://www.xnowherex.net/ubuntu/simp....8.1_amd64.deb)
[http://www.xnowherex.net/ubuntu/simp....8.1_amd64.deb](http://www.xnowherex.net/ubuntu/simp....8.1_amd64.deb)

Links ended with some message about an unfufilled dependency](*,) 

[http://www.xnowherex.net/ubuntu/simp...ta_3_amd64.deb](http://www.xnowherex.net/ubuntu/simp...ta_3_amd64.deb)

Seemed to work but now I can not find it? :confused: 

I am running gnome in dapper 6.06

---

### Post by Qwertinsky on 2006-10-15
Nevermind, I figured it out.

You have to install the support files first then the main program...

I guess I missed that part

---

### Post by StandardBlueCaboose on 2006-10-15
Hey Kuja, did you get your name from FFIX? If so, are you still going to be working on this so much after October 31? (Assuming you're American)

---

### Post by kuja on 2006-10-15
> **Qwertinsky said:**
> Nevermind, I figured it out.

You have to install the support files first then the main program...

I guess I missed that part

Yep, that's right, as per the errors you were getting, I see what's going on. It looks like I wrote down dpkg, instead of sudo dpkg. I didn't notice because I have that set up as an alias in my bash profile.... Thanks for letting me know!

> **StandardBlueCaboose said:**
> Hey Kuja, did you get your name from FFIX? If so, are you still going to be working on this so much after October 31? (Assuming you're American)
Yes I did. I'm indeed an American, but why would you expect me to stop working on it in December?

---

### Post by StandardBlueCaboose on 2006-10-15
> **kuja said:**
> Yes I did. I'm indeed an American, but why would you expect me to stop working on it in December?

FFXII comes out on the 31 of October, man. I'd imagine that would take up some of your time... :D

---

### Post by kuja on 2006-10-16
You've got a point there. Maybe it will take up some of my time... I've just not been paying much attention lately since I pre-ordered it back in may :D

---

### Post by cesera on 2006-10-23
> **kuja said:**
> 
 
[http://www.xnowherex.net/ubuntu/simple64-dapper_0.8.1_amd64.deb](http://www.xnowherex.net/ubuntu/simple64-dapper_0.8.1_amd64.deb)
[http://www.xnowherex.net/ubuntu/simple64-data_3_amd64.deb](http://www.xnowherex.net/ubuntu/simple64-data_3_amd64.deb)
 

 
 
Downloaded and installed the above two debs (for dapper), ran simple64 and tried to install wine. Errors in attached log file (seems to try to download version 9.21 instead of 9.23).

---

### Post by cesera on 2006-10-24
> **cesera said:**
> Downloaded and installed the above two debs (for dapper), ran simple64 and tried to install wine. Errors in attached log file (seems to try to download version 9.21 instead of 9.23).

Changed the version number in url.py that solved the problem.

Also: when you run from the menu sidenet does not install, from shell it does (don't know why, but thought I let you know anyway).

---

### Post by kuja on 2006-10-24
I started up working on it earlier today, after noticing that problem with wine when I went to install it last night. 
All that simple64 really does with sidenet is place a copy in your home directory. I'd love for it to run the script automatically, but it's really not feasible to do so :( I really don't know much about sidenet, all I know is that it works. 
Anyway, I've got a smattering of improvements coming. 

**Error Handling**
**Status:** Implemented and working in my local copy
**Description:** Error handling for the downloading of files. (granted, the way I'm doing it is more complicated than I would have hoped, but oh well, it shall work)
 
**Python-Apt**
**Status:** Looked at sample code, ran that sample code, and was overjoyed that it seemed to work without error
**Description:** I'm also considering using python-apt to handle downloading of apt-gettable dependencies, pending a stability test(In the package description it  notes that it may be unstable?). 

**Progress Bar**
**Status:** Played with the code, but not yet implemented
**Description:** A progress bar, as soon as I can figure out where in the interface I want to put it... It will be on a per-file/get basis. If I can't switch to python-apt for apt-getting, it won't be able to do progress on apt-getting of things, so I really hope it's stable enough to use.
 
**High Capacity Message Box**
**Status:** Looked into how to do it, haven't done it yet
**Description:** going to switch the little crammed box for displaying messages to a scrollable log-style rich-text box (could be so much nicer/prettier/easier with qt4, but that's not really an option seeing as I want this program to work with dapper as well)

Bug Fixes: Fixed a problem with the enabling of Main/Restricted, figures I didn't have everything right with that eh?

---

### Post by cesera on 2006-10-24
> **cesera said:**
> Also: when you run from the menu sidenet does not install, from shell it does (don't know why, but thought I let you know anyway).

One more thing on sidenet. I had to run

```
cd sidenet
./setup
```instead of

```
sidenet/setup
```otherwise I get an error saying:

> ERROR: Please run setup in the wine-config-sidenet directory.Just realised that setup hangs (at least for the last two hours) at "setting up default registry ..."

---

### Post by kuja on 2006-10-25
Okay, I made some decent progress today. Not a whole lot, but progress is progress.

I've made some pretty major changes:

Introduction of a config file (to replace simpleVersion, simpleDataVersion, distribution, and also to allow for custom logfile location) using python-configobj, a configuration menu will go with this before release.

I mentioned before that error handling for download is already implemented, works well.

simple64 will replace simple64-dapper and simple64-edgy, seeing as I've found a much better approach to the problem.

Doesn't sound like a lot, but I had to rip a lot of stuff apart to make these seemingly minor changes. 

The todo list:
Configuration Menu
Progress Bar
Allow for multiple programs to be selected/installed at the same time
Log style box for message display

PostPoned:
Switch to python-apt, until I get the chance to test it for stability.

---

### Post by beneedict on 2006-10-25
Thanks!!!!
I just installed skype with simple64 and it works like a charm! I had big troubles to install it before!!!!
I will try some other of the softwares available in the list. but so far, so great!!!

Benedikt

---

### Post by ksc1 on 2006-10-29
Hi,

This is a neat tool. I tried to install Opera on Edgy, but I get errors trying to run it. It can't find libraries. The first problems were solved by installing the ia32-libs-openoffice.org. But it still won't load, looking for an Xcursor library. Here's the message I get:

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.02-20060919.6/opera: error while loading shared libraries: libXcursor.so.1: cannot open shared object file: No such file or directory

Any ideas?

---

### Post by kuja on 2006-10-29
That's a file in the package libxcursor1, try copying the file /usr/lib/libXcursor1.so.1 to /usr/lib/32. I don't know what's up with it really. I know once or twice when installing opera I ran into this, and other times I didn't. Pretty weird.

---

### Post by ksc1 on 2006-10-29
Dear Kuja,

I tried it, and now get a problem with the ELF class. It's not a crucial problem to fix--I just want to have a browser with flash-player, and don't want to lose my 64bit Firefox.

Here's the current message:
/usr/lib/opera/9.02-20060919.6/opera: error while loading shared libraries: libXcursor.so.1: wrong ELF class: ELFCLASS64

---

### Post by kuja on 2006-10-29
Okay, I suppose that makes sense. I think I know why it's doing that. Try downloading the 386 architecture version of libxcursor1, extracting it (dpkg -x), and then copying that version of it over to /usr/lib32.

---

### Post by kuja on 2006-10-29
On second thought, I've changed my mind. I found out what package it's in, but it doesn't really seem like a logical place to be finding it if you ask me. It's in ia32-libs-gtk.
P.S. When I finally get the next version of simple64 done, that will be included in the Opera installation. It's a wonder I didn't catch it sooner, really.
P.P.S. Sorry!

---

### Post by ksc1 on 2006-10-29
Thanks! It worked.

---

### Post by /carlito on 2006-10-31
More errors here on edgy. +++ simple64-8.1-edgy +++

+++ Firefox 32 +++

```
##Running Firefox Installation##
Downloading gsfonts...
 Done

Downloading Firefox32...
 Done

Enabling/Updating Repositories...
 Done

Installing dependencies...
 Done

Installing gsfonts...
(Reading database ... 96400 files and directories currently installed.)
Preparing to replace gsfonts-x11 0.17ubuntu4 (using .../gsfonts-x11_0.17ubuntu4_all.deb) ...
Unpacking replacement gsfonts-x11 ...
Setting up gsfonts-x11 (0.17ubuntu4) ...
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory

 Done

Installing Firefox32...
dpkg-deb: `/tmp/firefox32-1.5.0.7_amd64.deb' is not a debian format archive
dpkg: error processing /tmp/firefox32-1.5.0.7_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /tmp/firefox32-1.5.0.7_amd64.deb
chmod: cannot access `/usr/local/bin/firefox32': No such file or directory
 Done

Firefox32 Installed. Try it out!
##End Firefox Installation##

```

+++ Wine +++

```
##Start Wine Installation##
Downloading Wine...
 Done

Downloading Fix...
 Done

Enabling/Updating Repositories...
 Done

Downloading Dependencies
 Done

Installing Wine...
dpkg-deb: `/tmp/wine_0.9.21~winehq0~ubuntu~6.06-1_i386.deb' is not a debian format archive
dpkg: error processing /tmp/wine_0.9.21~winehq0~ubuntu~6.06-1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /tmp/wine_0.9.21~winehq0~ubuntu~6.06-1_i386.deb
 Done

Installing Fix...
 Done

Downloading Sidenet...
 Done

mv: inter-device move failed: `/tmp/sidenet' to `/home/youri/sidenet/sidenet'; unable to remove target: Is a directory
Wine Installed. Try it out!
Exception in thread Thread-3:
Traceback (most recent call last):
  File "/usr/lib/python2.4/threading.py", line 442, in __bootstrap
    self.run()
  File "/usr/lib/simple64/simple64install.py", line 77, in run
    self.installWine()
  File "/usr/lib/simple64/simple64install.py", line 722, in installWine
    self.labelMessage.setText(message)
AttributeError: labelMessage

```

---

### Post by hk_2999 on 2006-10-31
Thanks kuja, simple64 made my 64-bit life a breeze!

---

### Post by tymek666 on 2006-10-31
Thx kuja for this app.
I've installed Kubuntu 6.10 and simple64 save me a lot of time :)
I remember that installation of some programs under 6.06 without simple64 took me many hours. Thx!

---

### Post by wazzie on 2006-11-03
i wish there was a straight up guide to what you need to know about the basics of dapper and 64bit architect, and simple basic linux commands. this thing rocks.](*,)

---

### Post by kuja on 2006-11-03
> **wazzie said:**
> i wish there was a straight up guide to what you need to know about the basics of dapper and 64bit architect, and simple basic linux commands. this thing rocks.](*,)

Thanks, though I think it still needs work. A couple of the URLs, namely for Wine, are probably dead right now. Once I get the time I'll be rewriting some of it, and it should prove to be a bit nicer....

---

### Post by Linux&amp;Lizards on 2006-11-06
i only have on question i got a pentium 111 not a amd64 
do you have a terminal command for that?

---

### Post by kuja on 2006-11-06
what do you mean?

---

### Post by Linux&amp;Lizards on 2006-11-06
what i mean is simplys this.
i dont have a amd processor i gota intel pentium 111
so ill need a i386 architecture correct?

---

### Post by kuja on 2006-11-06
This program is for any computer running 64-bit (k)(x)(ed)ubuntu. If you're using 32-bit, this program is not designed with you in mind, because the issues this program is designed to solve aren't present in 32-bit ubuntu.

---

### Post by dacovale on 2006-11-07
Tried to install dvd::rip, but it failed when it tried to apply the fix (4th action). Used ver 0.8.1 (dapper)

and even though it's probably a stupid question... whwere's the newly installed firefox? I can only find the old one that says "dapper security"-something in the UA. (yes, I have tried closing all instances of firefox before I tried again)

---

### Post by almalaci on 2006-11-07
Hi,
I tried simple64 with the following error after trying to run it:

>Failed to run python -O /usr/lib/simple64/simple64.py kuja /home/kuja<
>Unable to copy the user's Xauthorization file.<

Any ideas?

Laszlo Almasi

---

### Post by kuja on 2006-11-07
> **almalaci said:**
> Hi,
I tried simple64 with the following error after trying to run it:

>Failed to run python -O /usr/lib/simple64/simple64.py kuja /home/kuja<
>Unable to copy the user's Xauthorization file.<

Any ideas?

Laszlo Almasi

Hmm, it looks like I have something me-specific in there somewhere, but I forget where. Anyhow, it can wait til I've finished working on the next release, which has all sorts of improvements going into it... I really need to put that on the first page, that I'm working on it, that is.

---

### Post by Linux&amp;Lizards on 2006-11-07
how do i know if my system is 64 bit or a 32 bitter?

---

### Post by kuja on 2006-11-08
Yeah, you said you have a pentium 3 right? That's 32-bit alright, and you'll need Linux for the 386/x86 architecture.

---

### Post by /carlito on 2006-11-12
Any solutions to my problems yet?

> **/carlito said:**
> More errors here on edgy. +++ simple64-8.1-edgy +++

+++ Firefox 32 +++

```
##Running Firefox Installation##
Downloading gsfonts...
 Done

Downloading Firefox32...
 Done

Enabling/Updating Repositories...
 Done

Installing dependencies...
 Done

Installing gsfonts...
(Reading database ... 96400 files and directories currently installed.)
Preparing to replace gsfonts-x11 0.17ubuntu4 (using .../gsfonts-x11_0.17ubuntu4_all.deb) ...
Unpacking replacement gsfonts-x11 ...
Setting up gsfonts-x11 (0.17ubuntu4) ...
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory

 Done

Installing Firefox32...
dpkg-deb: `/tmp/firefox32-1.5.0.7_amd64.deb' is not a debian format archive
dpkg: error processing /tmp/firefox32-1.5.0.7_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /tmp/firefox32-1.5.0.7_amd64.deb
chmod: cannot access `/usr/local/bin/firefox32': No such file or directory
 Done

Firefox32 Installed. Try it out!
##End Firefox Installation##

```

+++ Wine +++

```
##Start Wine Installation##
Downloading Wine...
 Done

Downloading Fix...
 Done

Enabling/Updating Repositories...
 Done

Downloading Dependencies
 Done

Installing Wine...
dpkg-deb: `/tmp/wine_0.9.21~winehq0~ubuntu~6.06-1_i386.deb' is not a debian format archive
dpkg: error processing /tmp/wine_0.9.21~winehq0~ubuntu~6.06-1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /tmp/wine_0.9.21~winehq0~ubuntu~6.06-1_i386.deb
 Done

Installing Fix...
 Done

Downloading Sidenet...
 Done

mv: inter-device move failed: `/tmp/sidenet' to `/home/youri/sidenet/sidenet'; unable to remove target: Is a directory
Wine Installed. Try it out!
Exception in thread Thread-3:
Traceback (most recent call last):
  File "/usr/lib/python2.4/threading.py", line 442, in __bootstrap
    self.run()
  File "/usr/lib/simple64/simple64install.py", line 77, in run
    self.installWine()
  File "/usr/lib/simple64/simple64install.py", line 722, in installWine
    self.labelMessage.setText(message)
AttributeError: labelMessage

```

---

### Post by kuja on 2006-11-12
You can tell I have a lot of work to do on it right now. Just look at this staggering amount of procrastination :P

---

### Post by dacovale on 2006-11-13
I've figured it out. The download points to the wring URI, and the downloaded file is simple the 404-page. (in other words, a HTML-doc, not the firefox install file)

---

### Post by dacovale on 2006-11-13
to answer myself...
the dvd::rip install now works fine, dunno what went wrong the first 50 times.

Firefox doesn't install since the install script points to 404, but there's no errormessage given.

---

### Post by VFiend on 2006-11-16
Well, since you seem to want feedback.. Just tried installing the 32bit mplayer on Edgy using this, no luck
```
$ mplayer32 
mplayer32: error while loading shared libraries: libaudio.so.2: cannot open shared object file: No such file or directory

```

The file's in ia32-libs-openoffice.org, which can't be installed because of a file conflict with mplayer32. Oh well, looks like I'll just manually copy the libraries over.

---

### Post by dacovale on 2006-11-16
Is this still developed?
It's been a month since you posted the last update to the program.

---

### Post by kuja on 2006-11-16
I've kinda sorta been procrastinating. I'm working on it right now. I'm having trouble finding (good) documentation on the libaptpkg API. I guess I should break down and ask in the forums now :rolleyes:

---

### Post by Lukian on 2006-11-17
If this program is still being updated you'll need the following packages (or similar) to run Opera (9.02) shared-qt (so we can have sexy fonts too):

apt-get install lib32asound2 (probably a debian package, but I took this route)

From packages.debian.org download the following from "testing" "i386":
libxcursor1
libxfixes3
libxft2

If you wish to manually install follow the above steps and:

cd /usr/lib/opera/9.02-20060919.6/
sudo ln -s /usr/lib32/libasound.so.2 libaudio.so.2
dkpg -x *.deb ./
sudo mv usr/lib/* /usr/lib32/

And run Opera (9.02 shared-qt) on AMD64 Ubuntu 6.10 Edgy 6.10!
Enjoy the sexy new fonts!

---

### Post by Zilog Jones on 2006-11-23
Just tried this program to install Opera (in Kubuntu Edgy AMD64), but it won't load and gives these errors:

```
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.02-20060919.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
```

OK, I know I haven't set up Java yet - do I need to install the 32-bit version of the Java RE for the plugins to work in Opera?

However, it should still start if it wasn't for the last error. I have libqt3-mt, libqt4-core, libqt4-gui, libqt4-qt3support and libqt4-sql installed - is there anything else I should have?

Lukian: How would I install those debian i386 packages?

---

### Post by PatsM on 2006-11-23
Hi,
Just installed "simple64". Installation was simple enough; i'll start using it later today.

---

### Post by eco751 on 2006-11-28
I'm going to give this a shot tomorrow, when I think I'll have some free time...

---

### Post by eco751 on 2006-11-28
Testing, as promised.  (Edgy, Dell E1405, core2duo, 2.6.17-10.)




OPERA: no errors on installation, but it will not run until fixed, as below.
```
$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.02-20060919.6/opera: error while loading shared libraries: libaudio.so.2: cannot open shared object file: No such file or directory

```

OPERA fix: the solution was posted [in this thread]("http://ubuntuforums.org/showthread.php?p=1789367#post1789367")
```
cd /usr/lib/opera/9.02-20060919.6/
sudo ln -s /usr/lib32/libasound.so.2 libaudio.so.2
```


FIREFOX 32: errors during install
```
##Running Firefox Installation##
Downloading gsfonts...
 Done

Downloading Firefox32...
 Done

Enabling/Updating Repositories...
 Done

Installing dependencies...
 Done

Installing gsfonts...
dpkg - warning: downgrading gsfonts-x11 from 0.20build1 to 0.17ubuntu4.
(Reading database ... 138048 files and directories currently installed.)
Preparing to replace gsfonts-x11 0.20build1 (using .../gsfonts-x11_0.17ubuntu4_all.deb) ...
Unpacking replacement gsfonts-x11 ...
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
Setting up gsfonts-x11 (0.17ubuntu4) ...
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory

 Done

Installing Firefox32...
dpkg-deb: `/tmp/firefox32-1.5.0.7_amd64.deb' is not a debian format archive
dpkg: error processing /tmp/firefox32-1.5.0.7_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /tmp/firefox32-1.5.0.7_amd64.deb
chmod: cannot access `/usr/local/bin/firefox32': No such file or directory
 Done

Firefox32 Installed. Try it out!
##End Firefox Installation##

```


FLASH PLAYER: installed and works in opera!
```
##Running Flashplayer Installation##
Downloading Flashplayer...
 Done

Installing Flashplayer...

Flash installed for Opera

Finished installing FlashPlayer - Try it out!
##Ending FlashPlayer Installation##

```

---

### Post by Zilog Jones on 2006-11-29
Yeah, installing Flash for Opera with Simple64 worked fine for me. However, Java was a complete disaster! It started working, informed me I'd have to choose between KDE and and GDE in a setup screen - but then a scrambled-up set up screen appeared (in the terminal box) asking a different question (couldn't make out the question, but there were three checkbox options). Then it stopped responding. I terminated the terminal session and Simple64, but Simple64 would refuse to restart if I tried launching it again (haven't tried after a reboot yet). 

Sorry I forgot to take down any error messages. I will try it again when I get home. Maybe it was because Opera was running at the time? Am I right to believe that Opera uses the same JRE plugin as Firefox?

---

### Post by /carlito on 2007-01-18
I see that you have a lot of work for the moment, but i have one question.

Is this program still in development at the moment??

---

### Post by kuja on 2007-01-22
It's still being developed, in fact, things are looking pretty good for it at the moment. I just haven't been too good about updating this post. I had started another, but I think it's dead. Maybe I should just have it merged with this one, or something. Anyway, the current version is 0.9.5 if I remember right. I've converted it to a cli app because PyQT had me very frustrated at the time, and this seems to be working better anyway. Give it a whirl, if you so desire. Oh, and I updated the original post, just for you ;)

---

### Post by /carlito on 2007-01-22
> **kuja said:**
> Oh, and I updated the original post, just for you ;)

You're the best! I'll give the new version a try when i get home. I'll keep you posted.

Regards.

---

### Post by Smitje on 2007-01-22
Hi Kuja

I've just downloaded and installed jour script.
I skipped the line :
```
sudo aptitude install python
```
because I have python installed allready (that is what it does right? I'm stil a bit of a noob here, and feel like a fool in a strange land sometimes)

I installed Acrobat reader no problems. It opened one test document just fine.

But then I tried Flash player and I get the folowing error:
```
#######################################################
###        Running FlashPlayer9 Installation        ###
#######################################################
Downloading http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz ...
Remote file flashplayer9 does not exist
 Failed
FlashPlayer download failed. Aborting FlashPlayer Install
#######################################################
###        Ending FlashPlayer Installation          ###
#######################################################
### Would you like to install more programs? (y/n):
n
#######################################################

```

Thanks so far and keep up the good work.
Cheers,
Smitje

PS my system is a core duo with edgy eft, and I had firefox32 with java running alreaddy before installing simple64 (but I don't think that relates to the error I got)

---

### Post by kuja on 2007-01-22
Okay smitje, it looks like my flash9 link is out of date, I'll check it out and update the link.

---

### Post by kuja on 2007-01-22
> This is it. This is the officially blessed version of the Adobe Flash Player 9 for Linux (x86). Not a beta version; the final version. It's released. Today.
About bloody time!! I'll update simple64 to point to this immediately!

---

### Post by dad311 on 2007-01-23
Nice program.  Below are my results.  thx


GUI didnt work.
System-Administration-Simple64  flashes something quickly on the screen. To fast to read. 

Acrobat worked

Opera worked

Brasero returns the following error message:

Reading package lists... Done
Traceback (most recent call last):
  File "./simple64.py", line 1240, in ?
    MainLoop()
  File "./simple64.py", line 87, in MainLoop
    handleSelection(selection)
  File "./simple64.py", line 104, in handleSelection
    installBrasero()
  File "./simple64.py", line 598, in installBrasero
    manageRepositories(["MainRestricted","UpdatesMainRestricted","Janvitus"])
  File "./simple64.py", line 312, in manageRepositories
    janvitusWantedUpdate = enableJanvitus()
  File "./simple64.py", line 423, in enableJanvitus
    janvitusEnabled = checkJanvitus()
  File "./simple64.py", line 535, in checkJanvitus
    for n in range(len(strippedlines)):
NameError: global name 'strippedlines' is not defined

---

### Post by t_anjan on 2007-01-23
I installed WINE using Simple64. It works perfectly, but now I'd like to know how to uninstall any program that was installed using simple64. The program doesn't show in Synaptic.

---

### Post by crazedgremlin on 2007-01-23
Can't download firefox32

```
*---snip---*
###        Running Firefox Installation             ###
#######################################################
Downloading http://home.comcast.net/~ubuntu64user/ia32-lib-firefox-amd64.deb ...
 Done
Downloading http://home.comcast.net/~deletebox/firefox32-1.5.0.7_amd64.deb ...
Remote file firefox32 does not exist
 Failed
Downloading failed. Firefox32 installation aborted.
#######################################################
###        End Firefox Installation                 ###
```

---

### Post by kuja on 2007-01-23
Okay, I've got an update up.

GTK -> System -> Administration now launches correctly.
Flash 9 link updated.

ToDo list: Fix the checkJanvitus function
ToDo list: Update firefox32 link

---

### Post by kuja on 2007-01-23
Okay, I've got 0.9.7 up.
checkJanvitus function fixed
Firefox32 link updated.

I've not tested those, but it should work, I think.

---

### Post by kuja on 2007-01-24
simple64 0.9.8 is up, featuring removal functionality for anything that simple64 installed.

---

### Post by Smitje on 2007-01-24
Hi Kuja

Just opdated simple64, but stil no joy with the flash plugin:

```
#######################################################
###        Running FlashPlayer9 Installation        ###
#######################################################
Downloading http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz ...
Remote file flashplayer9 does not exist
 Failed
FlashPlayer download failed. Aborting FlashPlayer Install
#######################################################
###        Ending FlashPlayer Installation          ###
#######################################################
### Would you like to install more programs? (y/n):
n
#######################################################

```

cheers,
Smitje

---

### Post by kuja on 2007-01-24
It doesn't look like your upgrade went well, by what means did you do it? (I've personally not tested the self updating enough to know how well it works ... I tend to be ahead of the curve, if you know what I mean) Also, what is the contents of your /usr/lib/simple64/simple64.conf file? and perhaps the /var/log/simple64.log?

Anyhow, you need to have simple64 0.9.6+ and simple64-data 9+, I believe,  installed for the flash installation to work. Current simple64  is 0.9.8 and simple64-data is 10.

---

### Post by Smitje on 2007-01-24
Hi Kuja

I used the built in updating in simple64
and it dounloaded some stuff, it all looked successfull.

my simple64.conf looks like this:
simpleVersion = 0.9.8
simpleDataVersion = 10 

the log shows simple0.9.8 was installed successfully and then the the same error I quoted earlier.

I had a look in the python url.py file, and that dousn't have a version number, what should the correct url for flash9 be? that way I could check if it was updated correctly or repair it myself.
--EDIT-- I chanhed the url url.py but it didn't help --/EDIT--

 thanks for your efforts
cheers Smitje


PS one small suggestion, now that you have an updating feature, it may be a good idea to show the version numbers when simple64 is run.

---

### Post by funkenstein on 2007-01-24
hey there, just got here, on feisty 64 herd 2 and I have a couple of notes about the website:

the cli text is too big so doesn't fit on one line 
and
it installs simple64_0.9.8_amd64.deb  before simple64-data_10_amd64.deb, but the latter is a dep of the former. no biggie, just thought you might like to know...

---

### Post by kuja on 2007-01-24
funkenstein, so long as they're both on the same dpkg -i line it doesn't really matter (I tested it, just to be sure). I'll see about making the font in the textarea smaller though (or perhaps enlarging the textarea, so everything fits on one line though, thanks for the suggestion.

smitje: I'll look into it, as well as test it myself and make sure the thing works. Also, thanks for the suggestion, I think I'll do just that.  I agree that it should show the version when run. From the looks of the simple64.conf file you showed the update went fine though, good to know that the self-updating works.

---

### Post by kuja on 2007-01-24
Okay, smitje: I just tested it for myself, and I look at the link from your url.py ([http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz) ...) and it doesn't match the link in the url.py in the current version.  I've got no idea why ... but something is definitely wrong on _your_ end. It went without a hitch for me.

---

### Post by Smitje on 2007-01-25
Hi Kuja

Apearantly I made a typo when editing the file, i fixed that and now it works. The question remains why the url.py file was not updated correctly.

I havent tested it extencively jet but it seems to have worked.
Keep up the good work.

--EDIT-- At first it didn't work. But I tried installing flash 9 again and now it does :D  --/EDIT--

Many thanks, 
Smitje

---

### Post by kuja on 2007-01-31
Simple 64 0.9.9 is up
  * Highlights: Mplayer32 for Edgy (many thanks to Conq for making the MPlayer32 packages!)
Simple64-data 11 is up

---

### Post by kingcharles1666 on 2007-01-31
kuja, many thanks!!
I have tried to get opera working in 64 before and never managed. with your tool perfect.
many thanks!
how about adding google earth? I have not managed that one to get working yet....

thanks again, Charles

---

### Post by Smitje on 2007-02-03
Hi kuja

Just tried to update (Mplayer would fimally let me see some movie files I have lying around and I am on Edgy)
but unfortunately I get an error:

```
16
#######################################################
###        Starting Simple64 Update Process         ###
Downloading http://www.xnowherex.net/simple64/simple64.conf ...
Downloading http://www.xnowherex.net/simple64/simple64_0.9.9_amd64.deb ...
(Reading database ... 106083 files and directories currently installed.)
Preparing to replace simple64 0.9.8 (using /tmp/simple64_0.9.9_amd64.deb) ...
Unpacking replacement simple64 ...
Setting up simple64 (0.9.9) ...
Downloading http://www.xnowherex.net/simple64/simple64-data_0.9.9_amd64.deb ...
Remote file dataDeb does not exist
There was an error downloading simple64-data, it won't be updated.
Simple64 has been updated, it will now close.

```

thanks for the good work so far (flash 9 works now)

Cheers Smitje

---

### Post by graylion on 2007-02-04
Hmmm

I have a rather bizarre problem:

graylion@lionscage:~$ sudo dpkg -i simple64-data_11_amd
dpkg: error processing simple64-data_11_amd (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 simple64-data_11_amd

but python is installed:

graylion@lionscage:~$ sudo aptitude install python
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  libggi2 mplayer 
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

any ideas?

simply64 install obviously fails because simply data isn't installed

Thanks

-----------------------
Graylion's fetish & Fashion Store
[http://www.graylion.net](http://www.graylion.net)

---

### Post by kuja on 2007-02-04
> 
graylion@lionscage:~$ sudo dpkg -i simple64-data_11_amd
 dpkg: error processing simple64-data_11_amd (--install):


Perhaps a copy+paste mistake? should go out a bit further than amd (should go out to amd64.deb). If that's not it, try removing the package (dpkg -r simple64-data) and installing again (dpkg -i simple64-data_11_amd64.deb).

Smitje: Looks like the updating thing still isn't right :\ It wasn't all too high on my priority list, but I'll get it fixed now, the updating thing has aggravated me quite a bit now, time I fix it/get it out of the way.

---

### Post by Smitje on 2007-02-07
Hi Kuja 

Good to see you will be working on the updating, good luck hunting bug!! If there is any particular part of the code I can have a look at for you I would be happy to. I'm not a very experienced but have done a little python hacking before.

I am sad to say flash9 doesn't appear to be working as well as I thought. most youtube videos work but other interactive stuff dousn't appear to find the plugin. here is one example link that doesn't work:
[http://www.quieroverunfantasma.com/eng/post_1f76379.html](http://www.quieroverunfantasma.com/eng/post_1f76379.html)
The firefox error console says: "Flash has no propperties"

Cheers
Smitje

---

### Post by David Valentine on 2007-02-19
I am having some serious java issues, and I had hoped that simple64 would solve them.  I got rid of Sun java (versions 5 & 6) in adept, downloaded simple64, ran it, and got the following output:```
#######################################################
###        Running Java Installation                ###
#######################################################
Enabling/Updating Repositiories...
Done
Downloading/Installing 32-bit Sun Java binaries...
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Using `/usr/lib/jvm/ia32-java-1.5.0-sun/jre/bin/java' to provide `java'.
Done
Traceback (most recent call last):
  File "./simple64.py", line 1192, in ?
    MainLoop()
  File "./simple64.py", line 88, in MainLoop
    handleSelection(selection)
  File "./simple64.py", line 113, in handleSelection
    installSunJava()
  File "./simple64.py", line 796, in installSunJava
    if not installed:
UnboundLocalError: local variable 'installed' referenced before assignment
```On the off chance the installation had actually been successful, I checked by running a java application I run every day, which returned the following ```
$ /usr/lib/jvm/ia32-java-1.5.0-sun/jre/bin/java -jar $DIR/lib/jfs.jar $*
current locale is not supported in X11, locale is set to CX locale modifiers are not supported, using defaultWarning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Starting JFileSync GUI...
Exception in thread "main" java.lang.InternalError: Current locale is not supported
        at sun.awt.motif.MWindowPeer.pSetTitle(Native Method)
        at sun.awt.motif.MWindowPeer.init(MWindowPeer.java:102)
        at sun.awt.motif.MFramePeer.<init>(MFramePeer.java:58)
        at sun.awt.motif.MToolkit.createFrame(MToolkit.java:231)
        at java.awt.Frame.addNotify(Frame.java:491)
        at java.awt.Window.show(Window.java:513)
        at java.awt.Component.show(Component.java:1300)
        at java.awt.Component.setVisible(Component.java:1253)
        at jfs.gui.JFSMainView.<init>(Unknown Source)
        at jfs.JFileSync.main(Unknown Source)
```Any ideas?  Thanks!

---

### Post by kuja on 2007-02-20
The answer, part 1.
Okay, I think I have that fixed, the error, that is... was simple, not too serious either.
The answer, part 2.
For now, simple64 expects you to have a 32 bit browser installed to use with the 32-bit java (with plugin) that it's installing. Java installed okay, but simple64 didn't find a 32-bit browser for which to install the plugin (currently it looks in /usr/lib/opera/plugins and /usr/local/firefox32/plugins) So, you'll need to install a 32-bit browser to use it with ... (Simple64 can do Opera or Firefox for you) After installing the browser, you'll either need to copy or symlink the file "/usr/lib/jvm/ia32-java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so" to your 32-bit browser's plugin directory, or rerun the java installation in simple64.

---

### Post by antonio97b on 2007-02-23
Opera is having issues. I used Simple64 to install Opera. Everything appears okay but when I go to open it, it just sits in the taskbar in KDE loading. It loads for about 30 seconds and then disappears. No errors or warnings. Any idea on what is causing the situation?

```
#######################################################
###        Beginning Opera Installation             ###
#######################################################
Downloading http://opera.gundari.net/linux/910/final/en/i386/shared/opera_9.10-20061214.6-shared-qt_en_i386.deb ...
1%
...
99%
 Done
Enabling/Updating Repositories...
 Done
Downloading and Installing ia32-libs...
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for ia32-libs-kde
No candidate version found for ia32-libs-gtk
No candidate version found for ia32-libs-openoffice.org
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
 Done
Setting up Opera...
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 132637 files and directories currently installed.)
Preparing to replace opera 9.10-20061214.6 (using .../opera_9.10-20061214.6-shared-qt_en_i386.deb) ...
Unpacking replacement opera ...
Setting up opera (9.10-20061214.6) ...

 Done
Opera installation finished. Try it out!
#######################################################
###        Ending Opera Installation                ###
#######################################################

```


6.10
Kubuntu.

---

### Post by firekat on 2007-02-27
Thanx for this app.  I am very much a newbie, so your patience is greatly appreciated.  I started by trying to install the acrobat reader.  Unfortunately it would hang on download.  I tried installing Wine.  Everything seemed to go ok.  I tried running winecfg and got the following:

```
firekat@ubuntu:~$ winecfg
wine: creating configuration directory '/home/firekat/.wine'...
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\rundll32.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\rundll32.exe" failed, status c0000135
wine: wineprefixcreate failed while creating '/home/firekat/.wine'.
firekat@ubuntu:~$ 

```


Any ideas here?

I take it (from what I have seen) that running winecfg is the first step to setting up Wine.


Edit:

I installed ia32-libs.  That got the configurator  to work.  Will try it in a little bit.

My question now would be is there some dependencies/packages that should be installed prior to utilizing Simple64?

---

### Post by firekat on 2007-02-28
After having to rebuild my system after some wine issues I have come up with the following:

On the first installation of wine a small windows program ran pretty well.  I tried loading some other programs and ran into trouble.

Some of my programs are audio and require access to the audio driver.  On initial running of winecfg I was able to access the audio tab.  After loading one of the windows programs I tried running it and had some problems.  I then tried running winecfg and could not select the audio tab.  That's when h*ll broke loose.  I had a hard crash, could not do anything - move the mouse, anything.  I did the ctrl alt backspace to see if that would help.  Then all the control panels disappeared and could not be found again.  After a reboot the system was unstable so I elected to reload after attempts to uninstall wine with Simple64 failed - that is when checking the file system after toggling the uninstall in Simple64 I found that the .wine files were all still there.

After my reload I installed Simple64 and reloaded wine.  This time when starting winecfg I saved the start up info.

This is what I got:

```
firekat@ubuntu:~$ winecfg
wine: creating configuration directory '/home/firekat/.wine'...
Failed to open the service control manager.
err:module:load_builtin_dll failed to load .so lib for builtin L"msxml3.dll": libxslt.so.1: wrong ELF class: ELFCLASS64
wine: '/home/firekat/.wine' created successfully.
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: wrong ELF class: ELFCLASS64
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
err:module:load_builtin_dll failed to load .so lib for builtin L"winenas.drv": libaudio.so.2: wrong ELF class: ELFCLASS64

```

You help and assistance is greatly appreciated.

On a side note I got adobe reader installed it seems to be working fine though it come up with a missing java script message.  I will have to check into this a little later.

Otherwise thank you for all your work on making a lot of this stuff easier for us newbies.

---

### Post by kuja on 2007-03-01
> **antonio97b said:**
> Opera is having issues. I used Simple64 to install Opera. Everything appears okay but when I go to open it, it just sits in the taskbar in KDE loading. It loads for about 30 seconds and then disappears. No errors or warnings. Any idea on what is causing the situation?

```
#######################################################
###        Beginning Opera Installation             ###
#######################################################
Downloading http://opera.gundari.net/linux/910/final/en/i386/shared/opera_9.10-20061214.6-shared-qt_en_i386.deb ...
1%
...
99%
 Done
Enabling/Updating Repositories...
 Done
Downloading and Installing ia32-libs...
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for ia32-libs-kde
No candidate version found for ia32-libs-gtk
No candidate version found for ia32-libs-openoffice.org
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
 Done
Setting up Opera...
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 132637 files and directories currently installed.)
Preparing to replace opera 9.10-20061214.6 (using .../opera_9.10-20061214.6-shared-qt_en_i386.deb) ...
Unpacking replacement opera ...
Setting up opera (9.10-20061214.6) ...

 Done
Opera installation finished. Try it out!
#######################################################
###        Ending Opera Installation                ###
#######################################################

```


6.10
Kubuntu.

An odd problem indeed!! It said that there was no candidate version found for the ia32 libs ... that should have been taken care of. Apparantly It wasn't. Could you attach your /etc/apt/sources.list file for me so I could take a look at it. I think that would be a start anyway.

---

### Post by kuja on 2007-03-01
> **firekat said:**
> Thanx for this app.  I am very much a newbie, so your patience is greatly appreciated.  I started by trying to install the acrobat reader.  Unfortunately it would hang on download.  I tried installing Wine.  Everything seemed to go ok.  I tried running winecfg and got the following:

```
firekat@ubuntu:~$ winecfg
wine: creating configuration directory '/home/firekat/.wine'...
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\rundll32.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\rundll32.exe" failed, status c0000135
wine: wineprefixcreate failed while creating '/home/firekat/.wine'.
firekat@ubuntu:~$ 

```


Any ideas here?

I take it (from what I have seen) that running winecfg is the first step to setting up Wine.


Edit:

I installed ia32-libs.  That got the configurator  to work.  Will try it in a little bit.

My question now would be is there some dependencies/packages that should be installed prior to utilizing Simple64? wasn'

No, but perhaps there are more things I should have simple64 when running, for example, the wine installation. I think the first problem was caused because lib32stdc++6 wasn't installed. 

> **firekat said:**
> After having to rebuild my system after some wine issues I have come up with the following:

On the first installation of wine a small windows program ran pretty well.  I tried loading some other programs and ran into trouble.

Some of my programs are audio and require access to the audio driver.  On initial running of winecfg I was able to access the audio tab.  After loading one of the windows programs I tried running it and had some problems.  I then tried running winecfg and could not select the audio tab.  That's when h*ll broke loose.  I had a hard crash, could not do anything - move the mouse, anything.  I did the ctrl alt backspace to see if that would help.  Then all the control panels disappeared and could not be found again.  After a reboot the system was unstable so I elected to reload after attempts to uninstall wine with Simple64 failed - that is when checking the file system after toggling the uninstall in Simple64 I found that the .wine files were all still there.

After my reload I installed Simple64 and reloaded wine.  This time when starting winecfg I saved the start up info.

This is what I got:

```
firekat@ubuntu:~$ winecfg
wine: creating configuration directory '/home/firekat/.wine'...
Failed to open the service control manager.
err:module:load_builtin_dll failed to load .so lib for builtin L"msxml3.dll": libxslt.so.1: wrong ELF class: ELFCLASS64
wine: '/home/firekat/.wine' created successfully.
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: wrong ELF class: ELFCLASS64
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
err:module:load_builtin_dll failed to load useso lib for builtin L"winenas.drv": libaudio.so.2: wrong ELF class: ELFCLASS64

```

You help and assistance is greatly appreciated.

On a side note I got adobe reader installed it seems to be working fine though it come up with a missing java script message.  I will have to check into this a little later.

Otherwise thank you for all your work on making a lot of this stuff easier for us newbies.

libxslt.so.1 - ia32-libs-openoffice.org 
libesd.so.0 - libesd-also0 or libesd0 (might nened to take this from the 32-bit package too, not sure)
libjack.so - libjack0.100.0-dev (You may need to take this from the 32-bit package, extract it with dpkg -x, then copy the file(s) into /usr/lib32)
libaudo.so.2 - ia32-libs-openoffice.org

I'm not at home, so I can't really verify anything (using my friends laptop, much to my dismay.), but I'm fairly confident that's the things it's complaining about, try it and let me know, I may have to add these things to simple64's wine installation.

---

### Post by dirtvoyles on 2007-03-01
I just installed this to help out my 64 install until official items are available on Feisty, and it dies when I try to install Mplayer w/win32.

I'll post output if this is a new bug.

---

### Post by firekat on 2007-03-03
> libxslt.so.1 - ia32-libs-openoffice.org
libesd.so.0 - libesd-also0 or libesd0 (might nened to take this from the 32-bit package too, not sure)
libjack.so - libjack0.100.0-dev (You may need to take this from the 32-bit package, extract it with dpkg -x, then copy the file(s) into /usr/lib32)
libaudo.so.2 - ia32-libs-openoffice.org

Where would I source these and how would I install them?  I am confused about the 32/64 thing going on here and if I find something in synaptic I don't know if installing it is going to fix Wine.  For instance, I found jackd installed that - it did not fix Wine.

I am very much of a newbie.

I am taking it that my soundcard is probably the big culprit here.  It's a M-Audio 2496.  When it's installed it overrides and disables the integral motherboard sound processor.  There's got to be a way to get it to work.

Thanx for your help!

---

### Post by kuja on 2007-03-04
> **dirtvoyles said:**
> I just installed this to help out my 64 install until official items are available on Feisty, and it dies when I try to install Mplayer w/win32.

I'll post output if this is a new bug.Probably won't work, seeing as Conq hasn't made a package for it yet. Actually, I'm not sure if he's planning to do so at all or not. I guess we'll wait and see eh?

---

### Post by kuja on 2007-03-04
> **firekat said:**
> Where would I source these and how would I install them?  I am confused about the 32/64 thing going on here and if I find something in synaptic I don't know if installing it is going to fix Wine.  For instance, I found jackd installed that - it did not fix Wine.

I am very much of a newbie.

I am taking it that my soundcard is probably the big culprit here.  It's a M-Audio 2496.  When it's installed it overrides and disables the integral motherboard sound processor.  There's got to be a way to get it to work.

Thanx for your help!


Well, for starters, you'll need to install the ia32-libs-openoffice.org package.
```
sudo apt-get install ia32-libs-openoffice.org
``` will do the trick. The others will take a little more work:

The next one is going to be libesd.so.0, you'll need to download the **32-bit** libesd-alsa0 package. One easy way to do so is to search for it on launchpad, another is to go to [http://archive.ubuntu.com](http://archive.ubuntu.com) in your browser and navigate to it.

After you have it, place it in your home folder. Now, open up a shell and run this command: ```
sudo dpkg -x thepackagesname.deb
``` to extract the package. It should have created a new folder with the name of the package, now, open up a root file browser with either this command: ```
kdesu konqueror
``` or ```
gksudo nautilus
``` and navigate to the new folder. Inside there should be a folder "usr", and inside it a folder "lib". Inside the "lib" folder there is a file libesd.so.0, copy it to your /usr/lib32 folder. 

The next one is *much* like the previous. You'll need to download the libjack0.100.0-dev in much the same manner as the last one, placing it in your home folder too. Pull up a shell again, and run ```
dpkg -x thepackagesname.deb
```. It will have created a new folder. Open a root file browser (as described before) and navigate to the new folder, the file should be in the same place ("usr/lib"), if not, look for a file  libjack.so, and copy it to /usr/lib32.

After all of this, try to run it again and see if it works. I hope it will.

---

### Post by firekat on 2007-03-05
Ok,

Did as you instructed.  There were some things that I had to do in addition.  First off it was easier to download the files to the desktop, right click on them "extract", sudo nautilus and drag them to the usr/lib32 folder.  In the archival packages it showed the so.0 files as being "link to shared library" so I dragged the addition shared library to the directory.

I did this with libjack but I got the following message after startup of winecfg:

```
firekat@ubuntu:~$ winecfg
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
firekat@ubuntu:~$ 
```

Navigating back to /usr/lib32 it showed libjack.so as being "link (broken).  Right clicking on it and selecing open brought up this message: 

This link can't be used, because its target "/usr/lib32/libjack-0.100.0.so.0.0.23" doesn't exist.

Navigating through the libjack package I could not find that file.  Trying it with the command line interface did not net anything either.  I even tried getting the Debian package that did not have the libjack-0.100.0.so.0.0.23 file in it either.

So close yet so far!

---

### Post by kuja on 2007-03-05
That file, and perhaps others that you may need, could quite possibly be in one of the other jack related packages. I'm not sure which one... I've never played with jack. All of the stuff about things actually being links sounds very odd to me. Then again, I've never tried to play with it with the GUI, oh well.

---

### Post by CaveRat on 2007-03-05
Thanks for this program. I tried to get Wine installed soon after installing Fiesty 64 Herd 4 with no luck using intructions from another thread. I installed Simple64 this morning with no problems. I then installed Wine without a hitch as far as I can tell so far. 

Edit: Flash 9 and Firefox32 smooth installs.
 Mplayer & extras a no go. Oh well hopefully soon.

---

### Post by kuja on 2007-03-06
> **CaveRat said:**
> Thanks for this program. I tried to get Wine installed soon after installing Fiesty 64 Herd 4 with no luck using intructions from another thread. I installed Simple64 this morning with no problems. I then installed Wine without a hitch as far as I can tell so far. 

Edit: Flash 9 and Firefox32 smooth installs.
 Mplayer & extras a no go. Oh well hopefully soon.

The URL for the WINE deb is probably out of date, that'll be fixed before long (I'm on somewhat of a vacation right now, not sure when I'll finish making the changes I've been working on. ) There is currently no MPlayer32 package for Feisty, see the thread "WMV9 on 
AMD64" for details, Conq makes the packages. I guess I'd best get to work on getting it (s64)to play nice with Feisty too though.

---

### Post by CaveRat on 2007-03-06
> **kuja said:**
> The URL for the WINE deb is probably out of date, that'll be fixed before long (I'm on somewhat of a vacation right now, not sure when I'll finish making the changes I've been working on. ) There is currently no MPlayer32 package for Feisty, see the thread "WMV9 on 
AMD64" for details, Conq makes the packages. I guess I'd best get to work on getting it (s64)to play nice with Feisty too though.

Thanks for the reply. Simple64 is an excellent program. Seems the URL for Wine was working fine considering it installed here without a hitch and works like a charm. I especially like the Wine>Programs Tab in Applications. It allows me to see parts of my system I would otherwise have to do an extensive search to find. Also Wine activates quicker,and is more responsive and smoother running in Fiesty64 compared to Edgy32. 

Keep up the fantastic work Kuja and get this Stickied ASAP.

---

### Post by SickNick on 2007-04-02
this thing is amazing, i was so mad cuz i just installed ubuntu today, just moved over from suse, nd with suse all i had to do was check, 32 bit support when installing, nd it was ready. But this made it sooooo easy nd worked flawlesly, great job, i cant wait till it comes into a final version. I really feel that ubuntu should move to DVD nd support 32 bit on 64 from install, even raid, nd also add something to configure dual monitors with.  Baisically thats what Suse has over Ubuntu, im sticking with ubuntu because of beatiful update ability, and also i feel more stability. On suse i would udpate my kernel through auto updater, nd when i restarted i got big errrors. Also ubuntu should add a Boot Load Manager. Other than that, its programs liek these that make ubuntu a good user friendly system

---

### Post by kuja on 2007-04-02
> **SickNick said:**
> this thing is amazing, i was so mad cuz i just installed ubuntu today, just moved over from suse, nd with suse all i had to do was check, 32 bit support when installing, nd it was ready. But this made it sooooo easy nd worked flawlesly, great job, i cant wait till it comes into a final version. I really feel that ubuntu should move to DVD nd support 32 bit on 64 from install, even raid, nd also add something to configure dual monitors with.  Baisically thats what Suse has over Ubuntu, im sticking with ubuntu because of beatiful update ability, and also i feel more stability. On suse i would udpate my kernel through auto updater, nd when i restarted i got big errrors. Also ubuntu should add a Boot Load Manager. Other than that, its programs liek these that make ubuntu a good user friendly system
Good to  hear that it worked for you. Tonight in particular I got a lot done :) The 1.0 release will be soon, but I'll need people willing to test to make it happen. I simply don't have that much time and bandwidth :(

---

### Post by kuja on 2007-04-02
Speaking of things, 0.90 is now up. I've made a fair amount of changes. Added a functional manpage, knocked out the lintian errors, added on all of the things that you really need to run it in the dependencies, changed lots of stuff around that you'll likely never see (but it was essential for it to be changed around anyhow)

Importantly I've changed some things to do with wine. It now pulls in a few more things that it didn't before, which should be useful. 

Umm, and as usual, I updated some of the links. 

Fairly big update I'd say. I hope to have 1.0 out by the time feisty is out. Any help would be appreciated.

---

### Post by SickNick on 2007-04-02
honestly for this to be really really popular for people i think u shud make it into a very simply graphic applet tool, kind of like easy ubuntu. It shudnt take much time to do, just baisically make all the commands into buttons on an applet. Personally i love it the way it is, im just recommending this if you want it to become well known, again great job though, even up to here im gonna use it on every comp i put it on

---

### Post by kuja on 2007-04-02
> **SickNick said:**
> honestly for this to be really really popular for people i think u shud make it into a very simply graphic applet tool, kind of like easy ubuntu. It shudnt take much time to do, just baisically make all the commands into buttons on an applet. Personally i love it the way it is, im just recommending this if you want it to become well known, again great job though, even up to here im gonna use it on every comp i put it on
It originally was a graphical app (PyQT), but I found myself fighting the language too much and eventually converted it to a terminal app for the sake of the apps robustness and my own productivity.

---

### Post by tjotser on 2007-04-02
I tried your stuff a couple of days ago, now when i try to download i get this : 

 wget [http://www.xnowherex.net/simple64/simple64_0.90_amd64.deb](http://www.xnowherex.net/simple64/simple64_0.90_amd64.deb)
--23:19:22--  [http://www.xnowherex.net/simple64/simple64_0.90_amd64.deb](http://www.xnowherex.net/simple64/simple64_0.90_amd64.deb)
           => `simple64_0.90_amd64.deb'
Resolving [www.xnowherex.net](www.xnowherex.net)... 70.86.137.98
Connecting to www.xnowherex.net|70.86.137.98|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
23:19:22 ERROR 404: Not Found.

I would really like to give it a try again...
THX and GOOD LUCK !:biggrin:

---

### Post by kuja on 2007-04-02
> **tjotser said:**
> I tried your stuff a couple of days ago, now when i try to download i get this : 

 wget [http://www.xnowherex.net/simple64/simple64_0.90_amd64.deb](http://www.xnowherex.net/simple64/simple64_0.90_amd64.deb)
--23:19:22--  [http://www.xnowherex.net/simple64/simple64_0.90_amd64.deb](http://www.xnowherex.net/simple64/simple64_0.90_amd64.deb)
           => `simple64_0.90_amd64.deb'
Resolving [www.xnowherex.net](www.xnowherex.net)... 70.86.137.98
Connecting to www.xnowherex.net|70.86.137.98|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
23:19:22 ERROR 404: Not Found.

I would really like to give it a try again...
THX and GOOD LUCK !:biggrin:
Sorry, it should be up now.

---

### Post by diesel1 on 2007-04-03
Should this work on Fiesty64?

Diesel1.

---

### Post by UltimaDude on 2007-04-03
Yes, i'm using this on Fiesty 64 right now, Wine works perfect!

Along with flash on Firefox 32 bit

---

### Post by kuja on 2007-04-03
> **diesel1 said:**
> Should this work on Fiesty64?

Diesel1.
Most of it yes, some of it needs a bit of work yet.

---

### Post by RayH on 2007-04-03
kuja - Thank you for creating this script.

I followed the install instructions on your website.  However, if I run it I get the following error:

File "./simple64.py", line 797
    else:
       ^
SyntaxError: invalid syntax


I double checked everything, even uninstalled/reinstalled with the same results.  

TIA

---

### Post by kuja on 2007-04-03
> **RayH said:**
> kuja - Thank you for creating this script.

I followed the install instructions on your website.  However, if I run it I get the following error:

File "./simple64.py", line 797
    else:
       ^
SyntaxError: invalid syntax


I double checked everything, even uninstalled/reinstalled with the same results.  

TIA
I knew I got this funny feeling that I had broken something about 30 minutes ago. I must have. There will be a big update sometime tonight (it's 11pm here right now), so if you don't mind checking back later, it should be fixed and then some then :lolflag:

I should have 0.91 up sometime tonight, that is.

---

### Post by kuja on 2007-04-04
0.91 is up, with lots more changes, along with data 14.

So much has changed, it'd be nice if *hint hint* people could test it ... not just with Feisty ( where a lot of the changes were), but with Dapper and Edgy also.

---

### Post by Biochem on 2007-04-04
Seems to me like ther is a problem with the server (if you didn't already knew). This is the message I get when I want to upgrade from 0.9.

```
#######################################################
###        Starting Simple64 Update Process         ###
Downloading http://www.xnowherex.net/simple64/simple64.version ...
Remote file http://www.xnowherex.net/simple64/simple64.version does not exist
Downloading http://www.xnowherex.net/simple64/simple64-data.version ...
Remote file http://www.xnowherex.net/simple64/simple64-data.version does not exist
Simple64 failed to recieve the server's version information
There were no updates to Simple64 found.
#######################################################
```

I have similar message when I want to install something.

---

### Post by kuja on 2007-04-04
0.9? that was certainly a while ago. The files are definitely present. All I can say is try again later ... .I just wnet over and looked and it seems to be fine right now ... I'll look into the updating thing. I probably messed it up when I rewrote it a few weeks ago. Or perhaps it was more general a problem still. We'll see.

---

### Post by kuja on 2007-04-04
Fixed. You'll have to reinstall with 0.92 manually to get it to work (obviously updatings not going to do a bit of good), that, or if you are lazy and want to just upgrade, you should be able to do so if you first create the directory "/tmp/simple64" ...  (It's kind of hard to write files to that directory if it doesn't exist ... eheheh)

---

### Post by RayH on 2007-04-04
Thanks kuja, I have to go to work soon but I'll try and test this as soon as I get back.

---

### Post by RayH on 2007-04-04
Fixed.  I'm able to load it now.  I'm trying firefox32 now.  I'll keep you posted.

---

### Post by RayH on 2007-04-04
kuja - You got it.  I installed Firefox32 and the flash and java plugins and all is working great!

---

### Post by Biochem on 2007-04-04
It works perfectly, Thanks kuja.
Keep up the good work it is really, really appreciated.

By the way is it me or are you missing a wget in your manual installation instruction? It might confused people who cut and paste line by line and doesn't know bash yet.

---

### Post by kuja on 2007-04-04
> **Biochem said:**
> It works perfectly, Thanks kuja.
Keep up the good work it is really, really appreciated.

By the way is it me or are you missing a wget in your manual installation instruction? It might confused people who cut and paste line by line and doesn't know bash yet.
I didn't know I could before (because I had never tried), but it turns out you can wget multiple files at once, so I just moved it onto the same line :)

---

### Post by Medieval_Creations on 2007-04-04
Worked like a charm... No worries... On my Desktop w/ Feisty Beta.

---

### Post by noenter1 on 2007-04-07
This isnt a problem with you program(tried installing by hand had same problem), but the wine install doesnt make a "c drive" like it should so it can run(on feisty beta anyway).

---

### Post by rajeev1204 on 2007-04-07
hello

i cant install this thing

it says missing dependencies -- simple 64 data

Did i miss something?

---

### Post by RavanH on 2007-04-11
After a lot of searching to fix the Firefox/flash problem on AMD64 machines, I found Simple64.

Installed Simple64 in Feisty Fawn beta with Gnome. Installation went smoothly. Icon under System > Management (or whatever it is in English - sorry, I have a Dutch language version) is there and Simple64 starts up in a terminal window like it should.

I succesfully installed Skype and Firefox32. They worked straigh away, although I had to figure out that Firefox32 does not replace the original Firefox (64) and I had to change my quick-menu links and Preferred Programs (or is is Standard Programs) under System > Management manually.

The Flash player plugin seemd to work fine but it turned out that sound was not working. After another search for a fix, I got it working with sound too :)

Sadly, Acrobat Reader and Sun Java still do not work... :(
I read other posts complaining about Java not working on 64 systems. Are there any users that have Java running? And if so, how did they get it to?

---

### Post by alinuxfan on 2007-04-11
I tested on kubuntu fiesty beta and everything seemed to work before i left.
I am on my 32bit laptop now.  I will check back later if something isn't working right on my desktop.
I know skype, firefox and wine were all working
Thanks for the awesome script!

alinuxfan

---

### Post by alinuxfan on 2007-04-14
Awesome, back at home...everything that I installed seems to work.
I did a little searching of your scripts...changed .9.34 to .9.35 in the url.py file and downloaded the newest wine...your scripts already had it to make backups and such...worked great...testing wine as  i type this

thanks again

---

### Post by rvbhute on 2007-04-15
Installed and ran it on Feisty Beta - well, I needed it only for Firefox32 which I needed only for Flash... but hell, it ran smooth. Works as Said on The Box (tm)!

Wish list - Can you add Thunderbird32 to it? I need to try out Lightning extension which works only on the 32 bit one.

---

### Post by stealth17 on 2007-04-21
I can't seem to install Python in my Feisty release, is it not in the repositories yet or something?

---

### Post by kuja on 2007-04-23
> **stealth17 said:**
> I can't seem to install Python in my Feisty release, is it not in the repositories yet or something?

It should be.

---

### Post by kuja on 2007-04-23
Okay, I've put up a survey and would really, really like it if people who use simple64 would fill it out for me ... should only take a few minutes to do, and it will influence what directions it will take in the future. The link for it is on the first page.

---

### Post by t_anjan on 2007-04-23
Opera 9.20 is out. Any updates to simple64 in the offing?

---

### Post by oyofeld on 2007-04-23
I've succesfully installed symple 64 and used it to install wine it siad wine was succesfully installed but I cant find wine is there a command I could use in terminal to start wine.  by the way I'm using ubuntu fiesty 64

---

### Post by kuja on 2007-04-23
> **oyofeld said:**
> I've succesfully installed symple 64 and used it to install wine it siad wine was succesfully installed but I cant find wine is there a command I could use in terminal to start wine.  by the way I'm using ubuntu fiesty 64

Yeah, if it really successfully installed, you should be able to type "wine" in a terminal to run the program.
To check if it really installed, type "dpkg --list | grep --ignore-case wine"

---

### Post by kuja on 2007-04-23
> **t_anjan said:**
> Opera 9.20 is out. Any updates to simple64 in the offing?

Sorry that updates have come slow lately. I'll get my butt in gear :lolflag: 

(in truth, pulling together that survey is what has killed my time lately)

---

### Post by oyofeld on 2007-04-23
doesn't apear to be installed attempting reinstall I'll get bk too you with the result.

---

### Post by oyofeld on 2007-04-23
Downloading [http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb) ...
Remote file wine does not exist
 Failed, WINE will not be installed.
Wine Installed. Try it out!

didn't work see above for details

---

### Post by kuja on 2007-04-23
> **oyofeld said:**
> Downloading [http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb) ...
Remote file wine does not exist
 Failed, WINE will not be installed.
Wine Installed. Try it out!

didn't work see above for details
uggh, I had a feeling it could have been something like that, I'll look into it.

found the problem. It'll be fixed with the next update. Anyhow, if you update the simple64-data pacakage now, the problem should be remedied. Should. (let me know if it's not!)

---

### Post by oyofeld on 2007-04-23
did update, first file downloaded fine but did the same on second download i.e. it sez file doesn't exist agen. Tried it several times so I'm pretty sure it aint going to get past the second download. Post when you have an update or a way to fix the prob.  oh an by the way installed skype fine tested it all works good.

---

### Post by kuja on 2007-04-23
> **t_anjan said:**
> Opera 9.20 is out. Any updates to simple64 in the offing?

It is now.

---

### Post by t_anjan on 2007-04-23
> **kuja said:**
> It is now.

Great! Thanks!

---

### Post by stealth17 on 2007-04-23
I selected the install for Listen and it crashed as soon as I hit enter.

The last lines in the log file are:

```
###        Running Listen Installation              ###
#######################################################
```

That's all it has about it :confused:

---

### Post by eponymous on 2007-04-24
another satisfied customer, kuja.

However, opera did not work. looks like a broken link. the firefox 32 w\ plugins worked fine though, i'll just switch whenever it becomes available. i will try again today.

---

### Post by kuja on 2007-04-24
> **eponymous said:**
> another satisfied customer, kuja.

However, opera did not work. looks like a broken link. the firefox 32 w\ plugins worked fine though, i'll just switch whenever it becomes available. i will try again today.

Links break all the time, that's why I keep them in a second package ... makes it easier to update that more often. For example, WINE breaks very frequently.

---

### Post by t_anjan on 2007-04-27
A probling when trying to upgrade:

```
###  Selection:  
16
#######################################################
###        Starting Simple64 Update Process         ###
Downloading [http://www.xnowherex.net/simple64/simple64.version](http://www.xnowherex.net/simple64/simple64.version) ...
Downloading [http://www.xnowherex.net/simple64/simple64-data.version](http://www.xnowherex.net/simple64/simple64-data.version) ...
Traceback (most recent call last):
  File "./simple64.py", line 1395, in <module>
    MainLoop()
  File "./simple64.py", line 88, in MainLoop
    handleSelection(selection)
  File "./simple64.py", line 135, in handleSelection
    updateSimple64()
  File "./simple64.py", line 316, in updateSimple64
    serverDataDeb = "http://www.xnowherex.net/simple64/simple64-data_%s_amd64.deb" % str(serverConfig["simpleVersion"])
NameError: global name 'serverConfig' is not defined
```

---

### Post by t_anjan on 2007-04-27
As I couldn't update from Simple64, I did it manually. But the link to Opera is broken. It would be nice if I could download the file manually and then make simple64 install it.

---

### Post by arsadogi on 2007-04-27
kuja first of all great job
i want to download the source from the link at your signature and i can't.there is posibly an alternative way to get it?
beacause i am a starting python programmer and i am intrested.

---

### Post by kuja on 2007-04-28
arsa, well, technically if you install the package you already have it, however,  it's a bit more convenient to have that little tarball, so here you go:  [http://www.xnowherex.net/simple64/simple64-0.92.tar.bz2](http://www.xnowherex.net/simple64/simple64-0.92.tar.bz2)

Good luck with python and have fun :)

---

### Post by arsadogi on 2007-04-28
thanks, i download it
:)

---

### Post by kuja on 2007-05-03
Announcement:

Well, no, today it's not a release, but I swear it's getting there. Lots of work going on on simple64, it's just not release quality yet. Seeing as I switched to debian last week I decided to throw in support for debian with this next release. (Don't worry, that's not the cause of the hold-up, it only took a couple hours) 
Notable points of the next release will be:
* Simple64 won't download the same file twice anymore ... probably saves me more trouble than you, but oh well 
* Bundling NSPluginWrapper support into the flash installation portion, might put it in seperately too (haven't actually implemented this one yet, but it looks easy so I'll be doing it)
* Updating is fixed ... I think, has been for a while actually (just not released)
* Probably some updated links as always
* Support for Debian Etch+Lenny+Sid
* A higher version # (best point yet right?)
* Sun Java 6
* More work on handling obsolete stuff

Expect a release sometime next week.

---

### Post by RavanH on 2007-05-09
I'm running Simple64 on Feisty and it has been working like a charm for me so far. I've used the '16 Check for Simple64 updates' before without any updates beeing found... but now this happens:
> root@ravan-laptop:~# simple64
#######################################################
###               Welcome to Simple64               ###
#######################################################
###  Which program do you wish to install?          ###
###   0. Exit without installing anything           ###
###   1. Adobe Acrobat Reader - PDF Viewer          ###
###   2. Brasero - CD burning utility               ###
###   3. DVD::Rip - DVD ripping utility             ###
###   4. Adobe FlashPlayer - Flash plugin           ###
###   5. Firefox32 - a 32-bit firefox               ###
###   6. Sun Java                                   ###
###   7. Listen - Music Player                      ###
###   8. Mplayer32 - 32 bit MPlayer                 ###
###   9. Opera - a 32-bit web browser               ###
###  10. PartImage - Partition imaging/backup       ###
###  11. Rar - non-free RAR, 32-bit                 ###
###  12. Skype - VoIP client                        ###
###  13. Wengophone - VoIP client                   ###
###  14. WINE - run windows *.exe's in Linux        ###
###  15. Run 'aptitude update'                      ###
###  16. Check for Simple64 Updates                 ###
###  17. Remove applications installed by Simple64  ###
###  Selection:  
16
#######################################################
###        Starting Simple64 Update Process         ###
Downloading [http://www.xnowherex.net/simple64/simple64.version](http://www.xnowherex.net/simple64/simple64.version) ...
Downloading [http://www.xnowherex.net/simple64/simple64-data.version](http://www.xnowherex.net/simple64/simple64-data.version) ...
Traceback (most recent call last):
  File "./simple64.py", line 1395, in <module>
    MainLoop()
  File "./simple64.py", line 88, in MainLoop
    handleSelection(selection)
  File "./simple64.py", line 135, in handleSelection
    updateSimple64()
  File "./simple64.py", line 316, in updateSimple64
    serverDataDeb = "http://www.xnowherex.net/simple64/simple64-data_%s_amd64.deb" % str(serverConfig["simpleVersion"])
NameError: global name 'serverConfig' is not defined
root@ravan-laptop:~# 

Any ideas why?

---

### Post by RavanH on 2007-05-09
ok, after getting the latest version from [http://www.xnowherex.net/simple64/](http://www.xnowherex.net/simple64/) the error has disappeared...

---

### Post by ctothej on 2007-05-12
Installed Adobe Reader on Feisty 64 and it works wonderfully. I was missing its directory search features. I love evince, but the broad search feature of acrobat is too nice. Thank you!

---

### Post by kingcharles1666 on 2007-05-24
Hi,

The opera install does not work anymore :-(:
```
###  Selection:  
9
#######################################################
###        Beginning Opera Installation             ###
#######################################################
Downloading http://opera.gundari.net/linux/910/final/en/i386/shared/opera_9.20-20070409.6-shared-qt_en_i386.deb ...
Remote file opera does not exist
 Failed
Installation of Opera failed.
#######################################################
###        Ending Opera Installation                ###
#######################################################
### Would you like to install more programs? (y/n):
```
any ideas how to fix it?

---

### Post by kuja on 2007-05-24
I'll get to that as soon as I can. I've been kinda busy lately, and I have to work Friday/Saturday/Sunday, so it might be til Monday til I can get to that, but it should be quick.

---

### Post by T'sora on 2007-05-24
kuja, just wanted to say a big thanks for Simple64 =D> - worked like a charm for me today - first day using 64bit Feisty.

---

### Post by Clochard on 2007-05-30
I've just discovered simple64 and am really excited to get it running.  However after installing it (and using it to check for updates) I find I cannot install Firefox32.  Here's the output:

```
#######################################################
###        Running Firefox Installation             ###
#######################################################
Downloading http://home.comcast.net/~ubuntu64user/ia32-lib-firefox-amd64.deb ...
 Done
Downloading http://home.comcast.net/~next/firefox32-2.0-ubuntu-amd64.deb ...
1%
2%
3%
4%
5%
6%
7%
8%
9%
10%
11%
12%
13%
14%
15%
16%
17%
18%
19%
20%
21%
22%
23%
24%
25%
26%
27%
28%
29%
30%
31%
32%
33%
34%
35%
36%
37%
38%
39%
40%
41%
42%
43%
44%
45%
46%
47%
48%
49%
50%
51%
52%
53%
54%
55%
56%
57%
58%
59%
60%
61%
62%
63%
64%
65%
66%
67%
68%
69%
70%
71%
72%
73%
74%
75%
76%
77%
78%
79%
80%
81%
82%
83%
84%
85%
86%
87%
88%
89%
90%
91%
92%
93%
94%
95%
96%
97%
98%
99%
 Done
Enabling/Updating Repositories...
 Done
Installing dependencies...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  lib32gcc1 lib32stdc++6 lib32z1 libc6-i386 
The following NEW packages will be installed:
  ia32-libs ia32-libs-gtk ia32-libs-sdl lib32asound2 lib32gcc1 
  lib32ncurses5 lib32stdc++6 lib32z1 libc6-i386 linux32 
0 packages upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.2MB of archives. After unpacking 73.5MB will be used.
Writing extended state information... Done
Get:1 http://ca.archive.ubuntu.com feisty/main libc6-i386 2.5-0ubuntu14 [3617kB]
Get:2 http://ca.archive.ubuntu.com feisty/main lib32gcc1 1:4.1.2-0ubuntu4 [22.7kB]
Get:3 http://ca.archive.ubuntu.com feisty/main lib32stdc++6 4.1.2-0ubuntu4 [311kB]
Get:4 http://ca.archive.ubuntu.com feisty/main lib32z1 1:1.2.3-13ubuntu4 [52.8kB]
Get:5 http://ca.archive.ubuntu.com feisty/main ia32-libs 1.5ubuntu9 [17.9MB]    
Get:6 http://ca.archive.ubuntu.com feisty/universe ia32-libs-gtk 25 [3668kB]    
Get:7 http://ca.archive.ubuntu.com feisty/main lib32asound2 1.0.13-1ubuntu5 [319kB]
Get:8 http://ca.archive.ubuntu.com feisty/universe ia32-libs-sdl 1.0ubuntu3 [1074kB]
Get:9 http://ca.archive.ubuntu.com feisty/main lib32ncurses5 5.5-5ubuntu2 [305kB]
Get:10 http://ca.archive.ubuntu.com feisty/main linux32 1-3 [5416B]             
Fetched 27.2MB in 2m37s (173kB/s)                                               
Selecting previously deselected package libc6-i386.
(Reading database ... 166139 files and directories currently installed.)
Unpacking libc6-i386 (from .../libc6-i386_2.5-0ubuntu14_amd64.deb) ...
Selecting previously deselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.1.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package lib32stdc++6.
Unpacking lib32stdc++6 (from .../lib32stdc++6_4.1.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package lib32z1.
Unpacking lib32z1 (from .../lib32z1_1%3a1.2.3-13ubuntu4_amd64.deb) ...
Selecting previously deselected package ia32-libs.
Unpacking ia32-libs (from .../ia32-libs_1.5ubuntu9_amd64.deb) ...
Selecting previously deselected package ia32-libs-gtk.
Unpacking ia32-libs-gtk (from .../ia32-libs-gtk_25_amd64.deb) ...
Selecting previously deselected package lib32asound2.
Unpacking lib32asound2 (from .../lib32asound2_1.0.13-1ubuntu5_amd64.deb) ...
Selecting previously deselected package ia32-libs-sdl.
Unpacking ia32-libs-sdl (from .../ia32-libs-sdl_1.0ubuntu3_amd64.deb) ...
Selecting previously deselected package lib32ncurses5.
Unpacking lib32ncurses5 (from .../lib32ncurses5_5.5-5ubuntu2_amd64.deb) ...
Selecting previously deselected package linux32.
Unpacking linux32 (from .../archives/linux32_1-3_amd64.deb) ...
Setting up libc6-i386 (2.5-0ubuntu14) ...

Setting up lib32gcc1 (4.1.2-0ubuntu4) ...

Setting up lib32stdc++6 (4.1.2-0ubuntu4) ...

Setting up lib32z1 (1.2.3-13ubuntu4) ...
Setting up ia32-libs (1.5ubuntu9) ...

Setting up ia32-libs-gtk (25) ...

Setting up lib32asound2 (1.0.13-1ubuntu5) ...

Setting up ia32-libs-sdl (1.0ubuntu3) ...

Setting up lib32ncurses5 (5.5-5ubuntu2) ...

Setting up linux32 (1-3) ...
 Done
Installing Firefox32...
Selecting previously deselected package firefox32.
(Reading database ... 166824 files and directories currently installed.)
Unpacking firefox32 (from .../firefox32-2.0-ubuntu-amd64.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /tmp/simple64/firefox32-2.0-ubuntu-amd64.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/local/firefox32/extensions/talkback@mozilla.org/components/talkback/talkback')
Selecting previously deselected package ia32-lib-firefox.
Unpacking ia32-lib-firefox (from .../ia32-lib-firefox-amd64.deb) ...
Setting up ia32-lib-firefox (0.1) ...
Errors were encountered while processing:
 /tmp/simple64/firefox32-2.0-ubuntu-amd64.deb
chmod: cannot access `/usr/local/bin/firefox32': No such file or directory
 Done
Firefox32 Installed. Try it out!
#######################################################
###        End Firefox Installation                 ###
#######################################################

```

Edit: note that I then asked simple64 to try installing again and it reports success.   I'll restart my browser to test out Firefox32 now - thanks!

---

### Post by t_anjan on 2007-05-31
To anyone who may be faced with a problem where a new version of a software is out, but simple64 hasn't been updated yet, and if you know the link to the new version, then just edit /usr/lib/simple64/url.py . Change the link and then execute simple64 to install the latest version.

---

### Post by Rizlaw on 2007-06-07
I installed Simple64 version 0.92 on my Ubuntu 7.04 AMD64 system. I then tried to install Flash 9. Couldn't do it because I didn't have a 32bit version of Firefox  or Opera Installed. I guess my version of Firefox is 64bit.

Then I tried to install Opera, which I prefer over Firefox, and got the message that the program couldn't be found or didn't exist. So without Opera, I guess I can't install Flash 9.

My log file is attached; I hope. If not, here it is:


###        Running FlashPlayer9 Installation        ###
#######################################################
Downloading [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz) ...
5%
10%
15%
20%
25%
30%
35%
40%
45%
50%
55%
60%
65%
70%
75%
80%
85%
90%
95%
 Done
Installing FlashPlayer...
Simple64 could not detect Opera or Firefox32 on your system, Flash was not installed.
#######################################################
###        Ending FlashPlayer Installation          ###
###        Beginning Opera Installation             ###
#######################################################
Downloading [http://opera.gundari.net/linux/910/final/en/i386/shared/opera_9.20-20070409.6-shared-qt_en_i386.deb](http://opera.gundari.net/linux/910/final/en/i386/shared/opera_9.20-20070409.6-shared-qt_en_i386.deb) ...
Remote file opera does not exist
 Failed
Installation of Opera failed.
#######################################################
###        Ending Opera Installation                ###
###        Starting Simple64 Update Process         ###
Downloading [http://www.xnowherex.net/simple64/simple64.version](http://www.xnowherex.net/simple64/simple64.version) ...
Downloading [http://www.xnowherex.net/simple64/simple64-data.version](http://www.xnowherex.net/simple64/simple64-data.version) ...
There were no updates to Simple64 found.
###        Beginning Opera Installation             ###
#######################################################
Downloading [http://opera.gundari.net/linux/910/final/en/i386/shared/opera_9.20-20070409.6-shared-qt_en_i386.deb](http://opera.gundari.net/linux/910/final/en/i386/shared/opera_9.20-20070409.6-shared-qt_en_i386.deb) ...
Remote file opera does not exist
 Failed
Installation of Opera failed.
#######################################################
###        Ending Opera Installation                ###

BTW, I originally installed Simple64 by copying and pasting the script on the authors webpage into a terminal. It appeared to work, but I found no listing for the program in  the System>Administration menu; nor, could I run the program from a terminal window. I finally resorted to using Gdebi to install both deb packages to get the program properly installed.

---

### Post by kuja on 2007-06-07
Okay, I've got a new version up. Give it a try. 

I'd like to know what's working, and what isn't ... I've not tested anything since the ton of changes, sooooooooo, well, you get the idea. 

Oh come to think of it .... that function isn't complete, damn, oh well, no nspluginwrapper for now I guess. It'll fit into the next release though, which hopefully wont' be far away. 
Umm, switched it to use Java6 too. Yeah. 
Fixed a bunch of broken links, I hate broken links. 
Played with the wine installation ... hopefully didn't mess anything up, but we'll see about that too won't we?

Those are a few areas begging for testing right about now. Oh well, I need to go to bed, and then it's a three day marathon of little else but work for me.  Tah tah for now.

---

### Post by Rizlaw on 2007-06-07
I still can't download and install Opera. I selected check for program update first. Apparently, I downloaded and installed your new update. I say "apparently" because there is no program feedback stating that the update has successfully completed. Nevertheless, I still can't download and install Opera.

It would be a good idea, if somewhere on the text screen, the version of Simple64 is displayed so that we can be sure what version is running and whether an update has actually successfully occurred. Something like:

Welcome to Simple64 - Version x.xx

Here's my log:

###        Running FlashPlayer9 Installation        ###
#######################################################
Downloading [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz) ...
5%
10%
15%
20%
25%
30%
35%
40%
45%
50%
55%
60%
65%
70%
75%
80%
85%
90%
95%
 Done
Installing FlashPlayer...
Simple64 could not detect Opera or Firefox32 on your system, Flash was not installed.
#######################################################
###        Ending FlashPlayer Installation          ###
###        Beginning Opera Installation             ###
#######################################################
Downloading [http://opera.gundari.net/linux/910/final/en/i386/shared/opera_9.20-20070409.6-shared-qt_en_i386.deb](http://opera.gundari.net/linux/910/final/en/i386/shared/opera_9.20-20070409.6-shared-qt_en_i386.deb) ...
Remote file opera does not exist
 Failed
Installation of Opera failed.
#######################################################
###        Ending Opera Installation                ###
###        Starting Simple64 Update Process         ###
Downloading [http://www.xnowherex.net/simple64/simple64.version](http://www.xnowherex.net/simple64/simple64.version) ...
Downloading [http://www.xnowherex.net/simple64/simple64-data.version](http://www.xnowherex.net/simple64/simple64-data.version) ...
There were no updates to Simple64 found.
###        Beginning Opera Installation             ###
#######################################################
Downloading [http://opera.gundari.net/linux/910/final/en/i386/shared/opera_9.20-20070409.6-shared-qt_en_i386.deb](http://opera.gundari.net/linux/910/final/en/i386/shared/opera_9.20-20070409.6-shared-qt_en_i386.deb) ...
Remote file opera does not exist
 Failed
Installation of Opera failed.
#######################################################
###        Ending Opera Installation                ###
###        Starting Simple64 Update Process         ###
Downloading [http://www.xnowherex.net/simple64/simple64.version](http://www.xnowherex.net/simple64/simple64.version) ...
Downloading [http://www.xnowherex.net/simple64/simple64-data.version](http://www.xnowherex.net/simple64/simple64-data.version) ...
###        Beginning Opera Installation             ###
#######################################################
Downloading [http://opera.gundari.net/linux/910/final/en/i386/shared/opera_9.20-20070409.6-shared-qt_en_i386.deb](http://opera.gundari.net/linux/910/final/en/i386/shared/opera_9.20-20070409.6-shared-qt_en_i386.deb) ...
Remote file opera does not exist
 Failed
Installation of Opera failed.
#######################################################
###        Ending Opera Installation                ###
###        Starting Simple64 Update Process         ###
Downloading [http://www.xnowherex.net/simple64/simple64.version](http://www.xnowherex.net/simple64/simple64.version) ...
Downloading [http://www.xnowherex.net/simple64/simple64-data.version](http://www.xnowherex.net/simple64/simple64-data.version) ...

---

### Post by kuja on 2007-06-07
Odd. At any rate, it doesn't seem it  updated, as that link is definitely out-of-date. My attempt at an auto-update feature has been nothing but trouble from the beginning :\
Edit:
(at least the rest of it seems to work pretty well :) (when the links are up-to-date) (sorry about this odd edit ... just some needed self-reassurance)

---

### Post by Alek900 on 2007-06-13
I'm having some problems, when i try to install 32firefox or opera, it just shuts down :(
and i couldn't find the log file 8-[

---

### Post by kuja on 2007-06-14
Erm, the log file should be /var/log/simple64.log. If it's absent, try running the install for either of them again, and just copy and paste anything it says about it into a new reply so I can figure out what's going on.

---

### Post by _simon_ on 2007-06-16
When will you be releasing a new version with working flash for Firefox 64?

I just swapped Ubuntu 32 for 64 today, saw mention of your script, tried it but it wants FF32 to install flash for FF64?

```

###        Starting Simple64 Update Process         ###
Downloading http://www.xnowherex.net/simple64/simple64.version...
Downloading http://www.xnowherex.net/simple64/simple64-data.version...
There were no updates to Simple64 found.
###        Running FlashPlayer9 Installation        ###
#######################################################
### Would you also like to install nspluginwrapper  ###
### (nspluginwrapper will allow you to use flash    ###
###  in a 64-bit browser) (Y/N)                     ###
Downloading http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz ...
5%
10%
15%
20%
25%
30%
35%
40%
45%
50%
55%
60%
65%
70%
75%
80%
85%
90%
95%
 Done
Installing FlashPlayer...
Simple64 could not detect Opera or Firefox32 on your system, Flash was not installed.
#######################################################
###        Ending FlashPlayer Installation          ###

```

EDIT: INSTALLED USING SCRIPT HERE: [http://wakeless.net/archive/2007/05/flash-player-on-amd64-ubuntu](http://wakeless.net/archive/2007/05/flash-player-on-amd64-ubuntu)

---

### Post by kuja on 2007-06-21
Well, it's not time for my much needed next release just yet, but here's where I stand: 

Progress Report
- Packaging improvements, should remove things properly when purged: - not yet
- formatting & logging improvements - very good progress
- option to put many options down on one line and have simple64 do it all at once - deferred
- nspluginwrapper completion - some progress
- adobe reader fix + plugin - very good progress

---

### Post by jw5801 on 2007-06-22
Great work with the script kuja! Installs everything else but I can't seem to get wine to run properly... this is what comes up when I run it:
```
###  Selection:  
14
#######################################################
###        Start Wine Installation                  ###
#######################################################
Traceback (most recent call last):
  File "./simple64.py", line 1520, in <module>
    MainLoop()
  File "./simple64.py", line 93, in MainLoop
    handleSelection(selection)
  File "./simple64.py", line 134, in handleSelection
    installWine()
  File "./simple64.py", line 1487, in installWine
    manageRepositories(["Universe","Wine"])
  File "./simple64.py", line 430, in manageRepositories
    wineWantedUpdate = enableWine()
  File "./simple64.py", line 576, in enableWine
    if not wineEnabled:
NameError: global name 'wineEnabled' is not defined
```
I'm kinda new at the linux thing so I'm not to sure what to make of all that. Any help would be vastly appreciated!
Cheers,
Jason

---

### Post by kuja on 2007-06-22
> **jw5801 said:**
> Great work with the script kuja! Installs everything else but I can't seem to get wine to run properly... this is what comes up when I run it:
```
###  Selection:  
14
#######################################################
###        Start Wine Installation                  ###
#######################################################
Traceback (most recent call last):
  File "./simple64.py", line 1520, in <module>
    MainLoop()
  File "./simple64.py", line 93, in MainLoop
    handleSelection(selection)
  File "./simple64.py", line 134, in handleSelection
    installWine()
  File "./simple64.py", line 1487, in installWine
    manageRepositories(["Universe","Wine"])
  File "./simple64.py", line 430, in manageRepositories
    wineWantedUpdate = enableWine()
  File "./simple64.py", line 576, in enableWine
    if not wineEnabled:
NameError: global name 'wineEnabled' is not defined
```
I'm kinda new at the linux thing so I'm not to sure what to make of all that. Any help would be vastly appreciated!
Cheers,
Jason

Looks like a bug I hadn't caught. I'll probably have the fix up tonight. Anyhow, if you want a qucker fix, edit the file /usr/lib/simple64/simple64.py, and on that line (shows for you as 576?) change "wineEnabled" to "wineUpdated" and it should work.

---

### Post by jw5801 on 2007-06-22
Cheers! Appears to have installed correctly, however there's another little programming bug for you to fix up:

```
Setting up wine (0.9.39~winehq0~ubuntu~7.04-1) ...

 Done
Downloading http://www.xnowherex.net/simple64/sidenet.tar.gz ...
got here
0
http://www.xnowherex.net/simple64/sidenet.tar.gz
Traceback (most recent call last):
  File "./simple64.py", line 1520, in <module>
    MainLoop()
  File "./simple64.py", line 93, in MainLoop
    handleSelection(selection)
  File "./simple64.py", line 134, in handleSelection
    installWine()
  File "./simple64.py", line 1495, in installWine
    downloaded = download("sidenet")
  File "./simple64.py", line 244, in download
    temp.close()
UnboundLocalError: local variable 'temp' referenced before assignment
```
That all appears when attempting to return to the simple64 menu after installing wine.

---

### Post by mhacleth on 2007-06-23
Hello,
Thanks for the piece of software. :-)
However, I was not able to install Adobe Reader. Here's the log
```
mhacleth@office-desktop:~$ sudo simple64
#######################################################
###               Welcome to Simple64               ###
#######################################################
###        Starting Simple64 Update Process         ###
Downloading http://www.xnowherex.net/simple64/simple64.version...
Downloading http://www.xnowherex.net/simple64/simple64-data.version...
There were no updates to Simple64 found.
###  Which program do you wish to install?          ###
###   0. Exit without installing anything           ###
###   1. Adobe Acrobat Reader - PDF Viewer          ###
###   2. Brasero - CD burning utility               ###
###   3. DVD::Rip - DVD ripping utility             ###
###   4. Adobe FlashPlayer - Flash plugin           ###
###   5. Firefox32 - a 32-bit firefox               ###
###   6. Sun Java 6 32-bit - Sun JRE w/plugin       ###
###   7. Listen - Music Player                      ###
###   8. Mplayer32 - 32 bit MPlayer                 ###
###   9. Opera - a 32-bit web browser               ###
###  10. PartImage - Partition imaging/backup       ###
###  11. Rar - non-free RAR, 64-bit feisty package  ###
###  12. Skype - VoIP client                        ###
###  13. Wengophone - VoIP client                   ###
###  14. WINE - run windows *.exe's in Linux        ###
###  15. Run 'aptitude update'                      ###
###  99. Remove applications installed by Simple64  ###
###  Selection:  
1
#######################################################
##Running Acrobat Reader Installation##
#######################################################
Downloading Acrobat Reader...
Downloading http://us.archive.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread_7.0.9-0.0.ubuntu0.6.10_i386.deb ...
got here
0
http://us.archive.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread_7.0.9-0.0.ubuntu0.6.10_i386.deb
22912134
Okay, downloading now
1%
2%
3%
...
99%
 Done
Enabling/Updating repositories...
Traceback (most recent call last):
  File "./simple64.py", line 1520, in <module>
    MainLoop()
  File "./simple64.py", line 93, in MainLoop
    handleSelection(selection)
  File "./simple64.py", line 108, in handleSelection
    installAcrobatReader()
  File "./simple64.py", line 738, in installAcrobatReader
    manageRepositories(["MainRestricted"])
  File "./simple64.py", line 432, in manageRepositories
    if wineWantedUpdate:
UnboundLocalError: local variable 'wineWantedUpdate' referenced before assignment
mhacleth@office-desktop:~$ 
```

---

### Post by EdUbun on 2007-06-23
Hi. I installed this to be able to run skype. How ever once the install is down, my toolbar disappears and when making a new launcher it appears again.

how ever my skype won't launch. In the terminal in will say:

```
skype: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

```

---

### Post by kuja on 2007-06-27
> **EdUbun said:**
> Hi. I installed this to be able to run skype. How ever once the install is down, my toolbar disappears and when making a new launcher it appears again.

how ever my skype won't launch. In the terminal in will say:

```
skype: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

```

This one honestly sounds like an i ssue with your repositories. I can't be sure unless I see your /var/log/simple64.log though.

--

Simple64 0.9.4 with Data 17 is now up. 

- Fixed a lot of things
- Rewrote the download function
- Rewrote the logging and printing functions
- Added Adobe Reader plugin installation
- Now have simple64 install flash in directories of 64-bit browsers if nspluginwrapper is to be installed
- Finished nspluginwrapper install, that automatically wraps both flash and acroread if present. 

Roadmap:
- Near Future
- - May Switch to python-apt for apt functions (instead of aptitude)
- - Multi-install function that's been requested time and time again.
- Distant Future
- - Maybe a port to PyQT4 (GUI stuff), we'll see.

---

### Post by jw5801 on 2007-06-27
When attempting to install wine:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for wine
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
###  Done                                           ###
### Downloading sidenet.tar.gz...                   ###
### Remote file sidenet.tar.gz does not seem to     ###
###  exist or can't be reached.                     ###
###  Failed. Sidenet will not be run.               ###
#######################################################
###              End Wine Installation              ###
#######################################################

```
I was getting errors from the "wine-update" repository after the last install so I ran the "SimpleRemove" function which worked awesomly, then attempted to install again and this is what happened.
I did install DVD::Rip however, and am currently ripping Scrubs! So cheers to that!

---

### Post by kuja on 2007-06-27
Simple64 0.95 is up with Data 18

A few small bugs fixed
I caught a problem with flash & nspluginwrapper and decided to fix it as fast as I could, and it looks like I succeeded. 
I think I've got the sidenet problem fixed, it was a bad link, should be fixed now. 
At any rate, looking at the thread title I see "testers wanted"
This is still true. 

I'd say Acroread, Flash, Java, Nspluginwrapper, and Wine are the things that problably need tested most right now.  :popcorn:

---

### Post by AnObfuscator on 2007-06-27
Hey, I'm playing around with it now.
Opera's install was successful. However, it's painfully slow.
Flash plugin: Works in opera, but doesn't work in Firefox 64, even with nspluginwrapper.

Acrobat: went into infinite loop spitting out "##"'s. Ctrl+C just made it start installing again. I had to close the terminal window. When I installed Acrobat, I told it to install the nswrapper, even though I already had it installed. I'll try it again, without reinstalling nspluginwrapper.

I will also try installing Firefox32.

 Thanks for this, btw. It's really, really helpful.

UPDATES: 
Firefox32 failed: S64 can't find the file.
Acrobat: still won't install -- spits out lots of "###" garbage
Java: installed fine. Haven't tested the plugin yet. It shows up as "java 6 32 bit" in the system->preferences menu.
Wine: it says it installed, but I can't find it installed on my system.

---

### Post by AnObfuscator on 2007-06-27
> **AnObfuscator said:**
> Hey, I'm playing around with it now.
UPDATES: 
Firefox32 failed: S64 can't find the file.
Acrobat: still won't install -- spits out lots of "###" garbage
Java: installed fine. Haven't tested the plugin yet. It shows up as "java 6 32 bit" in the system->preferences menu.
Wine: it says it installed, but I can't find it installed on my system.


Java works in Opera; I just had to enable java and set the path in Opera's preferences.
Java path: /usr/lib/jvm/ia32-java-6-sun-1.6.0.00/jre/lib/i386

No biggie.

---

### Post by kuja on 2007-06-27
> **AnObfuscator said:**
> Hey, I'm playing around with it now.
Opera's install was successful. However, it's painfully slow.
Flash plugin: Works in opera, but doesn't work in Firefox 64, even with nspluginwrapper.

Acrobat: went into infinite loop spitting out "##"'s. Ctrl+C just made it start installing again. I had to close the terminal window. When I installed Acrobat, I told it to install the nswrapper, even though I already had it installed. I'll try it again, without reinstalling nspluginwrapper.

I will also try installing Firefox32.

 Thanks for this, btw. It's really, really helpful.

UPDATES: 
Firefox32 failed: S64 can't find the file.
Acrobat: still won't install -- spits out lots of "###" garbage
Java: installed fine. Haven't tested the plugin yet. It shows up as "java 6 32 bit" in the system->preferences menu.
Wine: it says it installed, but I can't find it installed on my system.
It looks like it could be a really serious problem. Can I see your /var/log/simple64.log please. Yes, just attach the WHOLE thing.

---

### Post by AnObfuscator on 2007-06-27
Ok: here's the log:

```


######################################################
Welcome to Simple64
  Version 0.95              Data 18            
Distribution = ubuntu
Codename = feisty
######################################################
Starting Simple64 Update Process
Downloading http://www.xnowherex.net/simple64/simple64.version...
Downloading http://www.xnowherex.net/simple64/simple64-data.version...
Server Version: 0.95     Server Data: 18      
######################################################
There were no updates to Simple64 found.
Running FlashPlayer9 Installation
######################################################
wantsNspluginwrapper: True
Downloading http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz...### 5% 10% 15% 20% 25% 30% 35% 40% 45% 50% 55% 60%  ###
### 65% 70% 75% 80% 85% 90% 95%                     ###

Installing FlashPlayer...
Flash installed to /usr/lib/firefox/plugins
Flash installed to /usr/lib/mozilla/plugins
Finished installing FlashPlayer - Try it out!
######################################################
Ending FlashPlayer Installation
######################################################
Running Nspluginwrapper Installation
######################################################
Enabling/updating repositories
Downloading http://janvitus.interfree.it/ubuntu/2C4C84CC.gpg...
Wrapped /usr/lib/mozilla/plugins/libflashplayer.so
######################################################
Ending NSpluginwrapper Installation
Beginning Opera Installation
######################################################
Downloading http://opera.gundari.net/linux/921/final/en/i386/shared/opera_9.21-20070510.6-shared-qt_en_i386.deb...### 1% 2% 3% 4% 5% 6% 7% 8% 9% 10% 11% 12% 13% 14%  ###
### 15% 16% 17% 18% 19% 20% 21% 22% 23% 24% 25%     ###
### 26% 27% 28% 29% 30% 31% 32% 33% 34% 35% 36%     ###
### 37% 38% 39% 40% 41% 42% 43% 44% 45% 46% 47%     ###
### 48% 49% 50% 51% 52% 53% 54% 55% 56% 57% 58%     ###
### 59% 60% 61% 62% 63% 64% 65% 66% 67% 68% 69%     ###
### 70% 71% 72% 73% 74% 75% 76% 77% 78% 79% 80%     ###
### 81% 82% 83% 84% 85% 86% 87% 88% 89% 90% 91%     ###
### 92% 93% 94% 95% 96% 97% 98% 99%                 ###

 Done
Enabling/Updating Repositories...
 Done
Downloading and Installing ia32-libs...Aptitude 0.4.4: log report
Wed, Jun 27 2007 22:55:55 -0400

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 2 packages, and remove 0 packages.
36.9MB of disk space will be used
===============================================================================
[HOLD] compiz
[HOLD] compiz-core
[HOLD] compiz-gnome
[HOLD] compiz-gtk
[HOLD] compiz-plugins
[HOLD] gaim
[HOLD] gnome-btdownload
[HOLD] gthumb
[HOLD] libbeagle0
[HOLD] libdecoration0
[HOLD] libnotify1
[HOLD] libwnck-common
[HOLD] libwnck18
[HOLD] nautilus-sendto
[HOLD] notification-daemon
[HOLD] rhythmbox
[HOLD] sound-juicer
[HOLD] tomboy
[INSTALL] ia32-libs-kde
[INSTALL] lib32asound2
===============================================================================

Log complete.

 Done
Setting up Opera...2007-06-27 22:56:00 install opera <none> 9.21-20070510.6
2007-06-27 22:56:00 status half-installed opera 9.21-20070510.6
2007-06-27 22:56:01 status unpacked opera 9.21-20070510.6
2007-06-27 22:56:01 status unpacked opera 9.21-20070510.6
2007-06-27 22:56:01 status unpacked opera 9.21-20070510.6
2007-06-27 22:56:01 status unpacked opera 9.21-20070510.6
2007-06-27 22:56:01 status unpacked opera 9.21-20070510.6
2007-06-27 22:56:01 status half-configured opera 9.21-20070510.6
2007-06-27 22:56:01 status installed opera 9.21-20070510.6

 Done
Opera installation finished. Try it out!
######################################################
Ending Opera Installation
Running Acrobat Reader Installation
######################################################
wantsNspluginwrapper: True
Downloading http://us.archive.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread_7.0.9-0.0.ubuntu0.6.10_i386.deb...### 1% 2% 3% 4% 5% 6% 7% 8% 9% 10% 11% 12% 13% 14%  ###
### 15% 16% 17% 18% 19% 20% 21% 22% 23% 24% 25%     ###
### 26% 27% 28% 29% 30% 31% 32% 33% 34% 35% 36%     ###
### 37% 38% 39% 40% 41% 42% 43% 44% 45% 46% 47%     ###
### 48% 49% 50% 51% 52% 53% 54% 55% 56% 57% 58%     ###
### 59% 60% 61% 62% 63% 64% 65% 66% 67% 68% 69%     ###
### 70% 71% 72% 73% 74% 75% 76% 77% 78% 79% 80%     ###
### 81% 82% 83% 84% 85% 86% 87% 88% 89% 90% 91%     ###
### 92% 93% 94% 95% 96% 97% 98% 99%                 ###

Downloading http://us.archive.ubuntu.com/ubuntu/pool/multiverse/a/acroread/mozilla-acroread_7.0.9-0.0.ubuntu0.6.10_i386.deb...### 5% 10% 15% 20% 25% 30% 35% 40% 45% 50% 55% 60%  ###
### 65% 70% 75% 80% 85% 90% 95%                     ###

Downloading http://us.archive.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread-plugins_7.0.9-0.0.ubuntu0.6.10_i386.deb...
######################################################
Welcome to Simple64
  Version 0.95              Data 18            
Distribution = ubuntu
Codename = feisty
######################################################
Starting Simple64 Update Process
Downloading http://www.xnowherex.net/simple64/simple64.version...
Downloading http://www.xnowherex.net/simple64/simple64-data.version...
Server Version: 0.95     Server Data: 18      
######################################################
There were no updates to Simple64 found.
Running Firefox Installation
######################################################
Downloading http://home.comcast.net/~ubuntu64user/ia32-lib-firefox-amd64.deb...
Downloading http://home.comcast.net/~next/firefox32-2.0-ubuntu-amd64.deb...
Remote file http://home.comcast.net/~next/firefox32-2.0-ubuntu-amd64.deb does not seem to exist or can't be reached.
Downloading failed. Firefox32 installation aborted.
######################################################
End Firefox Installation
Running Firefox Installation
######################################################
Downloading http://home.comcast.net/~ubuntu64user/ia32-lib-firefox-amd64.deb...
Cached file found, not downloading again.
Downloading http://home.comcast.net/~next/firefox32-2.0-ubuntu-amd64.deb...
Remote file http://home.comcast.net/~next/firefox32-2.0-ubuntu-amd64.deb does not seem to exist or can't be reached.
Downloading failed. Firefox32 installation aborted.
######################################################
End Firefox Installation
Running Acrobat Reader Installation
######################################################
wantsNspluginwrapper: False
Downloading http://us.archive.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread_7.0.9-0.0.ubuntu0.6.10_i386.deb...
Cached file found, not downloading again.
Downloading http://us.archive.ubuntu.com/ubuntu/pool/multiverse/a/acroread/mozilla-acroread_7.0.9-0.0.ubuntu0.6.10_i386.deb...
Cached file found, not downloading again.
Downloading http://us.archive.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread-plugins_7.0.9-0.0.ubuntu0.6.10_i386.deb...
Failed to read file
Downloading http://us.archive.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread-escript_7.0.9-0.0.ubuntu0.6.10_i386.deb...
Failed to read file
The installation failed for reasons noted above.
######################################################
Ending Acrobat Reader Installation
######################################################
Welcome to Simple64
  Version 0.95              Data 18            
Distribution = ubuntu
Codename = feisty
######################################################
Starting Simple64 Update Process
Downloading http://www.xnowherex.net/simple64/simple64.version...
Downloading http://www.xnowherex.net/simple64/simple64-data.version...
Server Version: 0.95     Server Data: 18      
######################################################
There were no updates to Simple64 found.
Running Java Installation
######################################################
Enabling/Updating Repositiories...
Done
Downloading/Installing 32-bit Sun Java binaries...Aptitude 0.4.4: log report
Wed, Jun 27 2007 23:09:53 -0400

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 4 packages, and remove 0 packages.
93.5MB of disk space will be used
===============================================================================
[INSTALL, DEPENDENCIES] gsfonts-x11
[INSTALL, DEPENDENCIES] java-common
[INSTALL, DEPENDENCIES] sun-java6-jre
[HOLD] compiz
[HOLD] compiz-core
[HOLD] compiz-gnome
[HOLD] compiz-gtk
[HOLD] compiz-plugins
[HOLD] gaim
[HOLD] gnome-btdownload
[HOLD] gthumb
[HOLD] libbeagle0
[HOLD] libdecoration0
[HOLD] libnotify1
[HOLD] libwnck-common
[HOLD] libwnck18
[HOLD] nautilus-sendto
[HOLD] notification-daemon
[HOLD] rhythmbox
[HOLD] sound-juicer
[HOLD] tomboy
[INSTALL] ia32-sun-java6-bin
===============================================================================

Log complete.

Done
Java for Opera instructions placed in your home directory.
Java Install completed. Try it out!
######################################################
Ending Java Installation
Start Wine Installation
######################################################
Downloading http://wine.budgetdedicated.com/apt/387EE263.gpg...
Downloading and Installing Wine & FriendsAptitude 0.4.4: log report
Wed, Jun 27 2007 23:15:14 -0400

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.

 Done
Downloading http://www.xnowherex.net/simple64/mirror/sidenet.tar.gz...### 12% 24% 36% 48% 60% 70% 82% 94%                 ###

 Donesidenet/inf/wcscn.inf
sidenet/inf/wcsen.inf
sidenet/inf/wcsja.inf
sidenet/inf/wine.inf
sidenet/inf/w32codecs.inf
sidenet/inf/wcs.inf
sidenet/shelllink/shelllink.exe
sidenet/true/Makefile
sidenet/true/trueocx.ocx
sidenet/true/true.exe
sidenet/true/readme
sidenet/true/true.c
sidenet/true/trueocx.c
sidenet/fonts/Makefile
sidenet/fonts/wine_sans_serif.ttf
sidenet/fonts/Makefile.in
sidenet/fonts/wine_system.ttf
sidenet/fonts/wine_courier.ttf
sidenet/fonts/readme
sidenet/fonts/genttf.ff
sidenet/fonts/wine_marlett.ttf
sidenet/wineconfig/config.sidenet
sidenet/wineconfig/config.sidenet.ja
sidenet/wineconfig/config.safe
sidenet/readme.en~
sidenet/setup
sidenet/wineshelllink.ja
sidenet/COPYING
sidenet/readme.en
sidenet/setup~

######################################################
End Wine Installation

```

---

### Post by kuja on 2007-06-28
Could you give me a sample of the ### garbage that it spits out? just copy and paste it out of the terminal, I need to see exactly where it starts so I can fix any problems that their  may be with it.

On another note, It seems when it wanted to install wine, aptitude said it wasn't going to do anything! That's really weird! Do you by chance already have wine installed? Or perhaps it didn't add the repository correctly. Do you see an entry for wine.budgetdedictated in your /etc/apt/sources.list?

So many odd problems popping up today :(

In other news, I think I might switch the repository that it's pulling acroread from - perhaps that will solve the problem with it failing to download the acroread files correctly.

---

### Post by AnObfuscator on 2007-06-28
Ok... it gets to 99%, then the terminal flashes, and spits out this stuff:
Nevermind. Terminal won't let me copy it; the #'s disappear when I try to copy.
but it spits out 
"###           [blank space]       ###"
endlessly. once it flashed this:
"### eb...      ###"
followed by the download percent text box, then started spitting out the #'s again.

No, I don't have wine installed; this is a fresh ubuntu install. 

Oh crap, you might cry a little when you see the line in my sources.list:
```

deb http://janvitus.interfree.it/ubuntu/ feisty-upure64 main-amd64deb http://wine.budgetdedicated.com/apt feisty main

```

I fixed that in my list, and wine works now. :)
forget a \n ? ;)

---

### Post by jw5801 on 2007-06-28
okedy dokey! With the new version (0.96 data 19) wine installs properly but the Adobe Reader still spits out a never ending loop of #'s (I got the same error as above).
After ctrl+c-ing a few times this is what happens:
```
###                                                 ###
###                                                 ###
###                                                 ###
###                                                 ###
###                                                 ###
Traceback (most recent call last):
  File "./simple64.py", line 1671, in <module>
    MainLoop()
  File "./simple64.py", line 114, in MainLoop
    handleSelection(selection)
  File "./simple64.py", line 138, in handleSelection
    installAcrobatReader()
  File "./simple64.py", line 877, in installAcrobatReader
    downloaded3 = download(remote["acrobatreader-plugins-edgy"])
  File "./simple64.py", line 291, in download
    logURL("Downloading ^^...",file) 
  File "./simple64.py", line 260, in logURL
    print "### %s ###" % messageBuffer
UnboundLocalError: local variable 'messageBuffer' referenced before assignment

```
I'm thinking the number of "ctrl+c"s added up to the number of commands that would have executed without the infinite loop.

---

### Post by kuja on 2007-06-28
> **jw5801 said:**
> okedy dokey! With the new version (0.96 data 19) wine installs properly but the Adobe Reader still spits out a never ending loop of #'s (I got the same error as above).
After ctrl+c-ing a few times this is what happens:
```
###                                                 ###
###                                                 ###
###                                                 ###
###                                                 ###
###                                                 ###
Traceback (most recent call last):
  File "./simple64.py", line 1671, in <module>
    MainLoop()
  File "./simple64.py", line 114, in MainLoop
    handleSelection(selection)
  File "./simple64.py", line 138, in handleSelection
    installAcrobatReader()
  File "./simple64.py", line 877, in installAcrobatReader
    downloaded3 = download(remote["acrobatreader-plugins-edgy"])
  File "./simple64.py", line 291, in download
    logURL("Downloading ^^...",file) 
  File "./simple64.py", line 260, in logURL
    print "### %s ###" % messageBuffer
UnboundLocalError: local variable 'messageBuffer' referenced before assignment

```
I'm thinking the number of "ctrl+c"s added up to the number of commands that would have executed without the infinite loop.

" in logURL"

Eureka! I finally know where the problem is at! Many thanks jw5801

---

### Post by kuja on 2007-06-28
Umm, well, the problem should be worked around for now, I also fixed a tentative problem with the auto-updating (which has always been rather troublesome  for me ...), anyhow, both the autoupdating and acroread installs should be working for now.

---

### Post by jw5801 on 2007-06-29
Adobe Reader installs correctly now! Complete with firefox plugin. Great work kuja! I think I might need to clean up my source list though... there's a few duplicate entries after running these installs so many times (is there an automated way to remove these?). One other thing... the repository that gets added when installing is telling me that it has newer verisons of a bunch of packages I have installed. These updates are labelled ~upure64, similar to the tag after the repository which is feisty-upure64/main-amd64. I'm assuming these updates are ones that haven't been deemed ready for the main repositories yet? If so are there any advantages or disadvantages to installing them?
Cheers for the working code!

---

### Post by AnObfuscator on 2007-06-29
jw:

to remove the sources, you can either edit them through Synaptic's repository manager, or you can edit the sources list directly.

sudo gedit /etc/apt/sources.list

I don't know much about the upure64 repo, other than it's 3rd party, and it offers cutting-edge backports of various packages not kept so up-to-date in ubuntu. it also offers these packages to older distros.

I see no problem in using them. If they break, just remember: 

sudo apt-get --purge remove <offending package>  

In trying to set up a "cutting edge" system, that command is your friend. ;-)

---

### Post by jw5801 on 2007-06-29
Cool, thanks! Was hoping there was a one-line command I could enter into command line to let apt-get do it for me :p I s'pose I'll just have to do it manually then... all that highlighting and deleting is a struggle though... ;)

---

### Post by kuja on 2007-06-29
Which line was there multiple of? That's something I should look at fixing. I've managed to avoid having that happen with most of them, but a couple of the things that I added or changed more recently may not be quite right.  (ie: when I changed the broken janvitus source with the new one, or perhaps with the wine repo.)

---

### Post by jw5801 on 2007-06-29
Most of them were good but I had about 5 or 6 of the wine repo (wine.budgetdedicated... etc).
One other thing now that I look at apt-get update more closely, that wine repo is returning an error for some reason (have no idea whether it's related or not):
```
99% [12 Packages gzip 0] [Waiting for headers] [Waiting for headers]
gzip: stdin: not in gzip format
Err http://wine.budgetdedicated.com feisty/main Packages            
  Sub-process gzip returned an error code (1)
```
```
Failed to fetch http://wine.budgetdedicated.com/apt/dists/feisty/main/binary-amd64/Packages.gz  Sub-process gzip returned an error code (1)
```

---

### Post by kuja on 2007-06-29
It's not related to anything I did; however, I bet it could cause a load of problems. I'll fix it so it doesn't throw a bunch of entries in tomorrow or the next day (busy with work for now)

---

### Post by caryb on 2007-06-30
Went to use it tonight 8:10 EST (Aust) 30/06/07 It comes up says something about updating & crashes!


Cary

---

### Post by kuja on 2007-06-30
caryb, can you attach your /var/log/simple64.log for me?

---

### Post by caryb on 2007-06-30
I manually upgraded it after I posted this! I also had problems with wine install it hung on the setting up the registry part! attached is my log file!


Cary

---

### Post by kuja on 2007-06-30
> **caryb said:**
> I manually upgraded it after I posted this! I also had problems with wine install it hung on the setting up the registry part! attached is my log file!


Cary

Wow! Quite the long log! I'm sure it will prove most useful :)

As per the Wine Registry thingy, That's actually part of another script (sidenet). Assuming it downloaded & installed okay, Wine should be installed.

---

### Post by themainliner on 2007-07-04
Rocking - this is the business.  I have no objection to hacking around in a Terminal window, but why bother? :)

Simple is best, simple64 does exactly what it says on the tin! :KS

Except...(didn't you just know that was coming)...for Flash.  I have got know where with it!  I tried to install and wrap for 64-bit, but with no joy.  So I installed Firefox32 and tried to install flash for that...not the ideal solution, but hey!  That doesn't work either.  Now I'm sad. :(

I downloaded and installed  nspluginwrapper and to be honest it was so easy I can't really complain, I now have Flash playback...sweet! :D

---

### Post by morequarky on 2007-08-17
I just installed simple64 on my ubuntu and everything seemed to work fine, but I can't find the programs I installed in the menus.  How do I get them there?

32bit Firefox with working plugins isn't available.  How do I create a launcher for it?  I don't even know where it is in my system.
partimage is not in the menus either

THanks...

CORRECTION:  firefox wget didn't work...not installed.   PartImage was installed, but I don't know where the file is that I need to run it.

---

### Post by tgm4883 on 2007-08-17
Survey needs updating.  The repos wouldn't work right for me, so I just used simple64 on my gutsy install and it installed flash perfectly for me.

---

### Post by kuja on 2007-08-18
Sorry I haven't been around lately folks. I'd been rather busy and I also just took a vacation :) I'll see what I can do with things ... morequarky

---

### Post by NullHead on 2007-09-05
Either it's just me ... or Kuja's websight has something wrong with it. It seams to be a web search sight now... I was going to reinstall simpe64 but I couldn't because of it.

---

### Post by kuja on 2007-09-06
Yes, it's definitely down. My account expired, and I figured this would be a good time to switch hosts .. It may be down for a few more days, for now I'll see if I can post a few of the packages attached to oh, how about the main post?

---

### Post by paradoxni on 2007-09-06
and I thought I was just being stupid not being able to find where to actually download this! :)

---

### Post by rubbsdecvik on 2007-09-27
so not to be stupid or anything, but is this package ever going to be available again?  I loved it, but now since there is no website, it won't update.  It seems that noone has said anything for 2 weeks here and I was wondering if the project was dead... and if it was, is anyone willing to help out a development newbie (myself) start something up again?

---

### Post by NullHead on 2007-09-29
kuja are you going to get a sight back up? I like your simple64 but it isn't available anymore:( If there is anything I can do to help ...

---

### Post by tropikai on 2007-10-19
i can't download it, can anyone help me??? :( sent it to me thru email or write link to it, I'd be pleased. Thank you

---

### Post by rubbsdecvik on 2007-10-19
It's not working at all.  The program will try to connect to the website before it runs, so even if I sent it to you, it wouldn't work.  

That's why I was trying to find out if the original person was no longer developing.

---

### Post by kuja on 2007-10-19
Yeah, I'm thinking about dropping it ... Seems a lot of it isn't really needed anymore in gutsy. I'm probably going to drop it in favour of a few smaller scripts for anything that hasn't been taken care of.

on a side not, I really do need to get around to getting my domain back up ... or a domain, guess that wouldn't really matter ... ummm, more on this note later. Need to get to bed.

---

### Post by rubbsdecvik on 2007-10-21
[https://www.nearlyfreespeech.net/]("https://www.nearlyfreespeech.net/") has some decent hosting plans.  I haven't used them myself, but I know people who have, and love it.  It's great for a site that pays for only what it uses.  Just an idea. 

If you want some help with scripts, you can always send something to me, I'm willing to help and learn.

I do agree with the fact that Gutsy takes care of most of it.  especially with the nswrapper-plugin fix.

---

