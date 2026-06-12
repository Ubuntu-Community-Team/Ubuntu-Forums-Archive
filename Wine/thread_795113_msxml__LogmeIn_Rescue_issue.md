---
title: "msxml / LogmeIn Rescue issue"
date: 2008-05-15
forum: Wine
---

### Post by TheMightyGirth on 2008-05-15
Hi All,

I am trying to get Logmein Rescue running on Firefox under wine. Logmein is a piece of remote support software which runs from within your web browser.

I have tried the following
linxu + firefox -> it tells me I need a Win32 OS
linux + wine + firefox -> it tells me it needs a newer version of msxml

I have downloaded and installed msxml3, msxml4 and msxml6 from microsoft, this doesn't seem to have fixed it.

I have also copied ms*xml* from c:\windows\system32 on my windoze box to the same dir in wine and ran regsvr32 on all of them.

I have included all the output from the console, the error happens just after the double blank line in the log. There is an obvious reference to fixme:msxml:saxxmlreader_QueryInterface but I don't know what it means.

Any help or pointers would be appreciated.

---

### Post by GreenNet_user on 2008-05-16
Hi There!

I have the same problem so any feedback on how to get around this would be great. I spoke to Logmein and for some (ridiculous) reason they have NO plans to make Logmein Rescue compatible with Linux...

Running it in Wine or QMU would be great if you could get around these little errors... Tried everything, feedback would be appreciated!

Cheers.
Sharif

---

### Post by happyhamster on 2008-05-16
After installing msxml3, try running wine with msxml3.dll set to native. From within the program's folder:

WINEDLLOVERRIDES="msxml3.dll=n" wine program_name.exe

[edit: in addition, a good way to install msxml3 is to use the winetricks script. See: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)]

[edit2: fixed link, bleh]

---

### Post by GreenNet_user on 2008-05-16
Thanks for the tip happy hampster!

But I did all that (eventually) and it STILL says I need a newer version of MSXML even though I chose the latest one MSXML6!)??

Any reason? 

I used the command

WINEDLLOVERRIDES="msxml3.dll=n" wine firefox

In the .wine/drive_c/Program Files/Mozilla Firefox/ folder and tried using LOGMEINRESCUE in the window that opened and still the same error?!?! :( Disappointing, because I was getting excited..

Any other tips anyone??

---

### Post by Dunt on 2008-06-28
I got past the msxml issue running Firefox in wine.
I added "firefox.exe" to "Application Settings" and threw every dll from system32 that had "xml" in it.
[IMG]http://i25.tinypic.com/2rr9zf7.jpg[/IMG]

[IMG]http://i28.tinypic.com/rjle1w.jpg[/IMG]

I also tried LogMeIn Rescue after installing ies4linux.
[http://www.howtoadvice.com/UbuntuIE]("http://www.howtoadvice.com/UbuntuIE")
[IMG]http://i25.tinypic.com/33jtt21.jpg[/IMG]

LogMeInRescue does work in IE and Firefox running under Wine by using these two methods.
The only issue I had was in IE.  The "Session: Client" displays in another language.
I didn't trial and error what XML dll's were required to get LogMeIn Rescue to work in Wine for Firefox.  You more then likely don't need to add all of them.

---

### Post by GreenNet_user on 2008-07-02
Great Work! It DOES work!! Very helpful, can't believe I've been so close to getting it working, but these last few steps you suggested did the trick! Thanks again!

---

### Post by island on 2008-08-16
I have Firefox working on Wine but the only thing that I get problems with trying to run Rescue Gateway is that once I login, it sits there for a few seconds then shuts down.

Is there a guide to a proper way to install Firefox 3 on the latest Wine or am I missing something? Here is a clip of the end of the log.

[email]island@isl-nix:~/.wine[/email]/drive_c/Program Files/Mozilla Firefox$ fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0001,0xc0020066,0x642c00,0x0001,0x00000000,0x33fc74,(nil)): stub
err:eventlog:ReportEventW L"81ac3fd8525f706af5bb73e045d16bf2"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub

---

### Post by Lawkout on 2010-01-16
I know this was created in 2008 but I was trying to get this going (new to ubuntu and loving it) but I can not seem to get it working. All the dll's are in and firefox launches with logmein. Clients can connect but one I get them to download and run the applet it it disconects after a few seconds.

Any help would be appreciated.

---

### Post by papimigas on 2011-05-22
Hi

Today I had to find a solution and just installed firefox 3.6 "onthefly" for Wine 1.2.2, under Ubuntu 10.04.

Logmein rescue just works great!:D

---

### Post by ingramproductions on 2012-12-24
Here is a tutorial on to run LogMeIn Rescue on Linux using more current versions (It's much easier now):

[http://itswapshop.com/tutorial/linux-how-use-logmein-rescue-remote-support-technician-console-ubuntu]("http://itswapshop.com/tutorial/linux-how-use-logmein-rescue-remote-support-technician-console-ubuntu")

---

