---
title: "Wine and Livescribe"
date: 2008-06-27
forum: Wine
---

### Post by IamReck on 2008-06-27
Hey all - 

I just got the Livescribe Pulse Smart pen for my Graduation, and I was wondering if anyone has successfully gotten the software that comes with it working in Ubuntu?

If not, I am open to getting a group together to try and figure it out, and other Pulse Smart Pen users out there?

---

### Post by Julolidine on 2008-07-14
I was only able to get it working using VMWare.  For whatever reason VirtualBox didn't work....lame.  It never picked up that I had hardware attached, even though I followed directions for getting VirtualBox to recognize USB devices.  

Hopefully one of these days they port it to linux, although I won't hold my breath.  Considering its written in Java I believe, it should be easier than the average port.

---

### Post by orph on 2008-07-14
Hy there,
I just got my Smartpen running on Windows. Sweeet ;-)
(Does anyone know, how to delete one single Page of a Notebook that's in the Memory of the Pen?)
However, I'm going to try the VMware soon and hope it works.

greez

---

### Post by drspockbr on 2008-08-18
Hi,

I'm using Kubuntu 7.10 (Gutsy) and VirtualBox 1.6.2 with Windows XP SP3 as guest operational system.

I installed the livescribe desktop 1.3 into the guest windows xp running on the vitualbox. The windows XP detects the Livescribe Smartpen. The device manager screen from windows shows an USB controller called "Pulse Smartpen" and a COM device called "Smartpen Communications (COM3)".  But, the livescribe desktop does not detect the pulse smartpen.

Anyone has any advice to solve that problem?

Thanks in advance.

---

### Post by Zipster90 on 2008-08-19
Hey. Just wondering if you ever got livescribe desktop installed in wine. Did it work?

---

### Post by teolemon on 2009-06-11
I received the following from Livescribe, after having asked for Linux support:
> [FONT=Shruti][SIZE=2][COLOR=black][FONT=Times New Roman]Hi Pierre,[/FONT][/COLOR][/SIZE][/FONT]
  [FONT=Shruti][SIZE=2][COLOR=black][FONT=Times New Roman][/FONT][/COLOR][/SIZE][/FONT] 
 [FONT=Shruti][SIZE=2][COLOR=black][FONT=Times New Roman]There is no current timeframe for when Linux will have it's own Livescribe Desktop. Since the Livescribe Desktop is freeware, and has it's own SDK, it is expected that someone in the Linux community will create the needed drivers to operate the Livescribe Desktop in a Linux environment.[/FONT][/COLOR][/SIZE][/FONT]
 [FONT=times new roman][SIZE=2][COLOR=black][FONT=Times New Roman][/FONT][/COLOR][/SIZE][/FONT] 
 [FONT=times new roman][SIZE=2][COLOR=black][FONT=Times New Roman]Please check out the Linux Forums for more information.[/FONT][/COLOR][/SIZE][/FONT]
 [FONT=times new roman][SIZE=2][COLOR=black][FONT=Times New Roman][/FONT][/COLOR][/SIZE][/FONT] 
 [FONT=Shruti][SIZE=2][COLOR=black][FONT=Times New Roman][/FONT][/COLOR][/SIZE][/FONT][FONT=Shruti][SIZE=2][COLOR=black][FONT=Times New Roman]Thank you,[/FONT][/COLOR][/SIZE][/FONT]
 [FONT=Shruti][SIZE=2][COLOR=black][FONT=Times New Roman][/FONT][/COLOR][/SIZE][/FONT] 
 [FONT=Shruti][SIZE=2][COLOR=black][FONT=Times New Roman]Ethan[/FONT][/COLOR][/SIZE][/FONT]
 [FONT=Shruti][SIZE=2][COLOR=black][FONT=Times New Roman][/FONT][/COLOR][/SIZE][/FONT][FONT=Shruti][SIZE=2][COLOR=black][FONT=Times New Roman][FONT=Shruti][SIZE=2][COLOR=black][FONT=Times New Roman][FONT=Shruti][SIZE=2][COLOR=black][FONT=Times New Roman][FONT=Shruti][SIZE=2][COLOR=black][FONT=Times New Roman]Livescribe[/FONT][/COLOR][/SIZE][/FONT][/FONT][/COLOR][/SIZE][/FONT][/FONT][/COLOR][/SIZE][/FONT]  Customer Support[/FONT][/COLOR][/SIZE][/FONT]
 [FONT=Shruti][SIZE=2][COLOR=black][FONT=Times New Roman][/FONT][/COLOR][/SIZE][/FONT] 


---

### Post by Rrory on 2009-12-18
Any news? I got my livescribe pen and myscript now supports Mac
[http://www.visionobjects.com/handwriting_recognition/pulse/pulse.htm](http://www.visionobjects.com/handwriting_recognition/pulse/pulse.htm)

can Ubuntu support the pen and now Myscript? I'm a write and I'd love it. I know the zillion students where I live would love it.

---

### Post by srwalter on 2010-02-09
[https://launchpad.net/~stevenrwalter/+archive/ppa](https://launchpad.net/~stevenrwalter/+archive/ppa)

If you're using karmic ubuntu, add ppa:stevenrwalter/ppa to your software sources and install smartpen-browser. That's a GUI app (pygtk) that will connect to your pen and render the pages (mostly) that are stored in it. The parsing isn't perfect, but give it a try and let me know what you think.

---

### Post by teolemon on 2010-02-14
Do you know where the dev website is ? I have a permissions problem.

---

### Post by srwalter on 2010-02-14
> **teolemon said:**
> Do you know where the dev website is ? I have a permissions problem.
If you just installed the package, try rebooting.  The package adds a configuration file for udev, which may need to be restarted.  Additionally, you can make sure you are in the "plugdev" group.

---

### Post by teolemon on 2010-02-14
It outputs : "Ambiguous device"
I've rebooted, and checked that both root and the user were in plugdev. I've tried launching the app as both.

---

### Post by srwalter on 2010-02-15
> **teolemon said:**
> It outputs : "Ambiguous device"
I've rebooted, and checked that both root and the user were in plugdev. I've tried launching the app as both.

Aha, that means you have more than one OBEX device installed.  For now, you can remove that other device; cell-phone, most likely.  I'll try to come up with a more graceful solution for that case.  I had to defunction that part of the code slightly when I backported to Karmic's libopenobex.

---

### Post by tablettweet on 2010-04-04
If you want to buy a Livescribe this is a good chance. Amazon just offers one day 38 percent deal. [Check this out. ]("http://www.tablettweet.com/2010/04/04/one-day-deal-for-livescribe-1gb-38-percent-off/")

---

### Post by Cjmkee on 2010-11-04
Steven,
I have tried to follow your directions, I got smartpen-browser installed via synaptic but I can't seem to launch it. I am running Meerkat, does that make a difference? Any help would be greatly appreciated, I am trying to get this livescribe pulse working before I have to take it back.

Thanks

---

### Post by srwalter on 2010-11-07
I've had another report of trouble launching the program on Meerkat.  I'm running 10.10 now, too, so I should be able to fix it.  Meanwhile, you should by able to start it by running "smartpen-browser.py" from either the Terminal or the Alt-F2 "Run Application" window.

---

### Post by jago25_98 on 2010-11-11
Id like to buy an alternative that works... or at least has a standard masstorage option. What do you recommend?

---

### Post by Ad1217 on 2010-11-17
I am thinking of buying one of these but don't want to get it if it does not work with Ubuntu. So... does it currently work?

---

### Post by srwalter on 2010-11-18
There is no official support for Linux from Livescribe.  The software I've written has some limited support, however parsing the handwriting (STF) files is not generally useful at this time.

---

### Post by sillyfrog on 2010-11-24
Hello

I am testing smartpen-browser.py in 10.04. It opens up a window, the pen indicates it is transfering stuff to the pc (same indication as in windows) and after a while all my notebooks appear as tabs with the correct number of pages. However, the pages themselves appear to be completely blank. I guess the step of communicating with the pen was achieved but there is still a lot to be done. Keep up the good work!

---

### Post by inportb on 2010-12-21
Hm... then, is there any possibility of developing/installing custom firmware for this thing? I'm looking into writing a Penlet for communicating data over USB, but that's a less-than-complete solution.

---

### Post by philcolbourn on 2011-02-13
> **sillyfrog said:**
> Hello

I am testing smartpen-browser.py in 10.04. It opens up a window, the pen indicates it is transfering stuff to the pc (same indication as in windows) and after a while all my notebooks appear as tabs with the correct number of pages. However, the pages themselves appear to be completely blank. I guess the step of communicating with the pen was achieved but there is still a lot to be done. Keep up the good work!

I only get the Tutorial tab, and both pages are blank.

Update:

The tutorial pages don't load. It seems that the first force parameter in the file on my pen (E0 is the byte) does not match a force codeword. Other pages do load error free - it seems you have to write on a page for the pen to register it (I don't know why some people say I am so dumb). So my previous post is just wrong - the code works. Thanks Steven.

I added '1110000', 99 as a code word to the force method and it seems to process the E0. I added a few other codewords and I can now parse the tutorials - although the existing and my added codewords are not right.

I can, however, see a pattern to the codewords that may help sort them out and make them computable.

---

### Post by asoto on 2011-02-17
I am using ubuntu 10.10 Maverick Meerkat, and I have a Livescribe Echo 4G smartpen.

I have tried the program smartpen-browser.py from srwalter, but after complaining about some permissions I did
sudo smartpen-browser.py

but the program crashed right after I clicked on the "connect pen" icon in the program.

After typing usb-devices it spits many things, amongst which is:
T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1cfb ProdID=1030 Rev=02.01
S:  Manufacturer=Livescribe
S:  Product=Pulse(TM) Smartpen
C:  #Ifs= 3 Cfg#= 1 Atr=80 MxPwr=250mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=02(commc) Sub=0b Prot=00 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=00 Driver=(none)

The program started displaying the window and this in the terminal:

/usr/bin/smartpen-browser.py:343: GtkWarning: Ignoring the separator setting
  builder.add_from_file("/usr/share/smartpen-browser/smartpen-browser.glade")

After I clicked in the "connect pen" icon, the program crashed and displayed this in the terminal.

swizzle
python2.6: smartpen.c:125: swizzle_usb: Assertion `dev' failed.
Aborted


I would appreciate if someone has managed to have it working on ubuntu 10.10.  I would like to know.

Peace.
-Adrian.

---

### Post by philcolbourn on 2011-03-16
I don't have an Echo (I have the Pulse) but if I remember I will try with a friend's Echo - no promises...

---

### Post by asoto on 2011-03-28
Any luck?

Thanks!
-Adrian.

---

### Post by philcolbourn on 2011-03-28
> **asoto said:**
> Any luck?

Thanks!
-Adrian.

Sorry, I forgot.

Thanks for the nudge.

---

### Post by asoto on 2011-04-10
I just tried with the newest version of smartpen-browser, and the pen now does connect, and the audio is indeed downloadable, but the pages appear blank.   Again, this is an echo 4g running in Ubuntu maverick Meerkat. 

Thanks to srwalter!!

Peace.
This is the output I got:

$ smartpen-browser.py 
swizzle
swizzle
swizzle
Connection ID: 1
Unknown force code
bad header d0
bad header 60
bad header c0
bad header f0
bad header a0
bad header e1
bad header 81
bad header 83
bad header 44
bad header e1
bad header 3
Unknown force code
code too long
bad header 20
Unknown force code
bad header 50
bad header 70
bad header a
bad header 40
bad header 1c
bad header 20
bad header d1
bad header 14
bad header 2a
bad header 28
bad header 61
bad header 46
bad header 89
bad header 90
bad header 1e
bad header c0
bad header 77
bad header 83
bad header 46
bad header 6
bad header 8d
bad header 6
bad header 4
bad header c
bad header a
bad header 28
code too long
bad header 6
code too long
bad header 44
Unknown force code
bad header a1
bad header 81
Unknown force code
bad header 34
bad header 4e
bad header 20
bad header c1
bad header 14
Unknown force code
bad header 14
code too long
bad header e0
bad header 7
Unknown force code
bad header 14
bad header 50
bad header 2
Unknown force code
bad header 8b
bad header cd
bad header 26
bad header fe
Unknown force code

-Adri'an.

---

### Post by asoto on 2011-04-16
Hi, I read that you got blank pages with smartpen-browser but managed to see the pages later.  Is there an easy way to do it?

The program smartpen-browser now works, connects and can download the audio; but the pages appear blank.  

Any ideas?

---

### Post by philcolbourn on 2011-05-05
> **asoto said:**
> Hi, I read that you got blank pages with smartpen-browser but managed to see the pages later.  Is there an easy way to do it?

The program smartpen-browser now works, connects and can download the audio; but the pages appear blank.  

Any ideas?

Not all the stroke codes are decoded yet.

The tutorials don't seem to download.

Have you tried a fresh page?

---

### Post by asoto on 2011-05-27
I just tried it with a new notebook, but nothing.  All pages are blank.

Thanks for the reply!

Peace.
-Adrian.

---

### Post by holycalamity on 2011-06-13
Many thanks to the developer working on this.  It's much needed.

I've got 0.2-1 running under AMD64 and Natty, connecting to an Echo pen. It shows only blank pages, though, and there is no sign of audio.  How does audio appear when it works?

---

### Post by asoto on 2011-06-13
You just connect the pen and in file->download audio you can do it.

Give it a try with the version you are using.

I did not use version 0.2-1 but one that srwalter sent me instead (coded 0.3-1) since mine would not even show. I put it here [http://dl.dropbox.com/u/529307/smartpen-browser_0.3-1_all.deb](http://dl.dropbox.com/u/529307/smartpen-browser_0.3-1_all.deb)


You would still need the ppa from srwalter to fulfill the dependencies.  He might have a newer version since then.  I am using Maverick, and the sound can be downloaded.  I hope this helps you.

---

### Post by ReyBrujo on 2011-07-07
A pity I missed this thread! I installed the latest library from Maverick and the 0.3.1 version posted before, and end in a similar situation as asoto was: the program crashes as soon as I click connect. The pen shows the logo for connecting, but then disconnects.

reybrujo@ansalon:~$ python2.6 `which smartpen-browser.py`
swizzle
Connection ID: 1
FAIL 0 4
python2.6: smartpen.c:83: obex_event: Assertion `0' failed.
Aborted

The latest Ubuntu uses Python 2.7, so I had to manually call 2.6 (which is where the modules are installed).

---

### Post by asoto on 2011-07-07
Have you tried with the link I put?  Try to contact srwalter.  That  did it for me.  

I can download audio; but pages are still blank...

Peace.

---

### Post by ReyBrujo on 2011-07-07
I think the problem was not having the modified obex libraries, downloaded them and the module code, compiled it, and got it running. Just as you, I got the empty pages (program took too long to load the notebook tab, so I just removed the pen).

Didn't notice about downloading the audio (my mind is still fighting against the global menu bar from natty), but yes, it is saying it downloads audio, although haven't seen anything yet.

The pages are not being drawn because there are lots of codes that are not handled yet. I know C, but little Python... I wish I could understand the main idea (looks like he is transforming the bit stream into timed coordinates for later drawing, although I am not completely sure).

---

### Post by ReyBrujo on 2011-07-07
After a bit of search, I noticed [abrasive's fork](https://github.com/abrasive/libsmartpen) of hassan2050's library (which in itself appears to be a clone of srwalker's library), where he mentioned back in March that he finished working in the decoder. And indeed, it is true, it works.

What I did (I am on Natty):

[list][*]# sudo updatedb (updates search database)
[*]# locate parsestf.py (this will find where the Python modules have been installed. In Natty, in /usr/lib/pymodules/python2.6 it installs a link to /usr/share/pyshared/parsestf.py. There is also a parsestf.pyc, which is the compiled parsestf.py).
[*]sudo rm -rf /usr/lib/pymodules/python2.6/parsestf.pyc (not sure if necessary)
[*]wget [https://raw.github.com/abrasive/libsmartpen/a2ddd3ed3bed87f59353a56038253c90a77365d5/parsestf.py](https://raw.github.com/abrasive/libsmartpen/a2ddd3ed3bed87f59353a56038253c90a77365d5/parsestf.py) (get the new decoder from abrasive's commit. Note that the link in my post appears shrank, you need to copy the link and not copy the text, otherwise you won't get the file).
[*]sudo mv parsestf.py /usr/lib/pymodules/python2.6 (overwrite the installed one with the new one. You could also overwrite the one in /usr/share/pyshared instead)
[/list]

Done. Now, launch the smartpen browser, and the pages should be rendered. Under Natty, since the libraries are installed in Python 2.6 while the current version is 2.7, you need to run it as # python2.6 `which smartpen-browser` to get it working.

As you can faintly see in my screenshot, it works (of course, there is no play yet, but it is only a matter of time). Note that it seems the canvas is a bit too short for the page (at least in my case) and the sentences look like cut just before the end of line.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=196904&stc=1&d=1310043398[/IMG]

---

### Post by srwalter on 2011-07-07
Holy cow that's awesome!  Somehow no one bothered to tell me this :-)

You are correct, abrasive's code is a fork of mine.  I just merged his changes back into my repo and have uploaded new packages to my PPA.  Page rendering should actually work now!

Everyone, please try the newest packages (0.6-1 and 0.3-3) and see if they work for you.

---

### Post by katja on 2011-07-07
It does not work for me with the latest packages; I get a crash upon attempting to connect the smartpen (I'm using Natty & the Echo 4GB):

```
python /usr/bin/smartpen-browser.py
swizzle
swizzle
swizzle
swizzle
Connection ID: 1
FAIL 0 4
python: smartpen.c:83: obex_event: Assertion `0' failed.
Aborted
```

Edit: it works after installing the modified obex libraries (sorry for missing that); the pages are rendering.

---

### Post by davidwees on 2011-07-17
I noticed that the code in the parser seems to be taking the information directly from the stf file and turning it into a png. If we could get the time information from the stf file we could turn the individual pngs into a series of pngs, and then string them into a video file with FFMPEG, and presumably then we would get play to work.

Given that importing, and then playing the pencasts is all we really want to do, why don't we skip the additional features in the Livescribe pencast player, and focus on trying to import the pencasts in Theora (or MP4) format? Can we build a script which will import the pencasts, and then convert them to video, and then not use the Livescribe software at all?

---

### Post by fimasava on 2011-08-02
> **srwalter said:**
> Holy cow that's awesome!  Somehow no one bothered to tell me this :-)

You are correct, abrasive's code is a fork of mine.  I just merged his changes back into my repo and have uploaded new packages to my PPA.  Page rendering should actually work now!

Everyone, please try the newest packages (0.6-1 and 0.3-3) and see if they work for you.

Well Srwalter, first of all, I would like to say you thanks for the effort you are doing for helping us. 

I intalled the last packages (I am using ubuntu 11), and my comments are:

a) It is working the connection and I am able for download the audio and it works.

b) Also it appears a document *.odb (* is the same name of the folder I have my audio files). The application that is able for opening this odb file is Libreoffice Base, but the document is empty.

c) It is not posible checking the documents I have in the pen and deleting files using your application. Any suggestions?

Best Regards and once again, thank you a lot...

---

### Post by MariosYanni on 2011-08-03
[COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=arial]I was planning to buy a Pulse Smartpen by Livescribe. I saw their other product, Livescribe Desktop, as I browse the graphics of the Smartpen. Is it okay if i connect the smartpen in any kind of computer or it is exclusive only to the LiveScribe Desktop.[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by ReyBrujo on 2011-08-04
The Livescribe desktop is necessary for importing, exporting, playing and doing everything with the pen. Here srwalter and a few others have created a Linux compatible framework that loads some information and displays it, plus exports the audio files, but it is not still as complete as the desktop itself.

---

### Post by ewr2san on 2011-12-10
There is a project called librescribe (linux native) that is making progress as well:

[http://dylanmtaylor.com/2011/09/02/significant-librescribe-progress-made/](http://dylanmtaylor.com/2011/09/02/significant-librescribe-progress-made/)
[https://github.com/aliendude5300/LibreScribe](https://github.com/aliendude5300/LibreScribe)

He's got it downloading pages and mp3.

---

