---
title: "Using Citrix Client 10.0 - help, anyone have this working"
date: 2007-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by juanhunglow on 2007-03-05
_Edit: October 16, 2007 - ICAclient in Ubuntu 7.10 GG_
I am amazed at how easy this was on my 64 bit install of 7.10 GG RC1.  Forced to do this install prior to final release because of hard drive changes I was nervious.  Installed on vanilla Firefox 64 (not 32) using the Linux ICAclient, all defaults accepted for install.  Worked.  Amazing.  I'll make a new post for GG and the fact that the client is 10.6.

New post [Using Citrix Client 10 with Ubuntu 7.10 (64-bit) - Gutsy Gibbon]("http://ubuntuforums.org/showthread.php?p=3570204#post3570204")

_EDIT: April 24, 2007 - Kubuntu Feisty 64 success and script working_
See post number [53 ]("http://ubuntuforums.org/showpost.php?p=2514388&postcount=53")for a step by step process for setup of citrix v10 if you use Kubuntu Feisty 64.  Looks similar to the Ubuntu setup, but proof that it works on Kubuntu is good as well.
Also, ICA connections widow problems relating to text size/spacing are being resolved by using the script.  See the wiki provided by the scripts creator [here]("http://codtech.com/wiki/index.php/Citrix_ICA_Client_on_Ubuntu").  Thanks to dtmilano.

_EDIT: April 10, 2007 - script posted_
See post number [**_28 _**]("http://ubuntuforums.org/showpost.php?p=2429884&postcount=28")of this thread for a script that, according the author, can be used to help fix problems with a citrix client install.  I have not tried it myself so can't attest to it's magic.  If you try it please let us know.

_EDIT: April 4, 2007 - Feisty 64-bit edit._
I successfully got citrix presentation server to load on 64-bit Feisty after an install of the beta version.  After a clean install of the beta this is what I did:
1. ```
sudo apt-get install libxaw6 libmotif3
```
I'm not sure step 1 was necessary because of step 2, but I did this first.

2. Then install firefox32 using kilz script found [**_here_**]("http://ubuntuforums.org/showthread.php?p=1174435") which gets  you the 32 bit stuff you need.  Note the issues with not using the script for java and mplayer plugin just yet.  [I did the manual install of java and everything is fine, I don't use the mplayer plugin so no problem]

3. Download the citrix client (currently v10) from the webpage, the tar.gz file [http://www.citrix.com/site/SS/downloads/downloads.asp?dID=2755](http://www.citrix.com/site/SS/downloads/downloads.asp?dID=2755)

4. Extract the tar.gz

5.  In a terminal 'cd' to the extracted folder.  When in the proper folder type this:
```
./setupwfc
```
You will presented with a series of promps that you must answer.  I selected the default location for ICAClient.  I allowed it to create the folder. I accepted the license.  Finally, when asked to integrate with kde or gnome I selected yes.  Finally, I chose to quit the installer.

6.  After this, I went to the website were I launch my citrix session from and clicked on the link.  The citrix session started and I didn't even have to tell it where the wfica file was located.  Cleanest install to date.

[COLOR="Red"]** NO changes to the files/code per the Readme (Edgy is another story).
[/COLOR]
Some who use the wfmgr may still have issues.  Since I don't use it I can't test it.  If those who do use it have success please let us know.

_EDIT: March 29, 2007_: - Feisty and Edgy related Edit
Using Feisty 32-bit (herd 5 with all updates) Citrix client v10 was installed by using the ./setupwfc command in a terminal.  All values were left at default. No modifications were made to any of the font files and the presentation server launched for my citrix session perfectly.  Easiest citrix client setup on any flavor of Ubuntu to date...!!!

Also, see posts [_**16**_]("http://www.ubuntuforums.org/showpost.php?p=2257344&postcount=16") and [_**17**_]("http://www.ubuntuforums.org/showpost.php?p=2257344&postcount=17") of this thread, also have had success with these. (not feisty related)

_EDIT: March 8, 2007_:  - Edgy related Edit
This is turning into a bit of how-to so I'll keep the first post updated.

The following info in the quote is working for some.:  
> 
by: joeindo
I did a standard install as well. Reading the readme file in the install folder explains something about :

4.9 The client may not start correctly on Ubuntu or other Debian-derived systems
---------------------------------------------------------------------------------
When using UTF-8 locales on Debian or Debian-derived systems such as Ubuntu, the
client may not start correctly when the X libraries try to load the necessary
Unicode font. You can avoid this issue either by running the client in a non
UTF-8 locale, or by removing the following lines from the Wfcmgr*fontList section
of the Wfcmgr resource file in the $ICAROOT/nls/{language}/UTF-8 directory:
-gnu-*-*-*-*-*-*-120-*-*-*-*-iso10646-1;\

-*-helvetica-medium-r-*-*-*-120-75-75-*-*-*-*;\
-*-*-medium-r-*-*-*-120-75-75-*-*-*-*;\
-*-*-medium-r-*-*-*-120-*-*-*-*-*-*:

Removing these lines prevents the client from trying to use any Unicode fonts,
which can cause certain characters in published application names or window names
to display incorrectly.
[#154155]

If I could find $ICAROOT/nls/{language}/UTF-8 directory and delete the lines mentioned above - I probably wouldn't have to run xset fp rehash...

I got the xset fp rehash idea from the citrix forum link:
[http://support.citrix.com/forums/thr...threadID=86630](http://support.citrix.com/forums/thr...threadID=86630)



_**ORIGINAL POST**_:
As of February 22, 2007, Citrix client for Linux was upgraded to version 10.
Prior to this update I had no problem using citrix client version 9.0 with Firefox32 installed with Kilz script.  And this guide to set it up: [http://www.ubuntuforums.org/showthread.php?t=333534&highlight=citrix]("http://www.ubuntuforums.org/showthread.php?t=333534&highlight=citrix")

However, this guide does not work with version 10 of the client.  The readme that comes with the client specifically refers to Ubuntu and files that should be changed to make it work.  Despite making these changes it still does not work.

Does anyone have this working properly?  My usage involves logging into a webpage/server and then launching a presentation server/client with the wfica program.

In the alternative, does anyone have a copy of version 9 of the client saved.  I did a new install and that is how I lost this.

Thanks in advance for any help.

NOTE: this if for my Edgy install, not for Feisty testing.

---

### Post by Didjit on 2007-03-05
Are you getting an Error at run time or install? What is the error?

Didjit

---

### Post by juanhunglow on 2007-03-05
> **Didjit said:**
> Are you getting an Error at run time or install? What is the error?

Didjit

There did not appear to be any errors on the setup.

When I click the launch.asp and select wfica nothing happens.  Normally the presentation server would open up a new window.

I bet there is an error going on in the background but I don't know how to document it.
Any suggestions?

---

### Post by Didjit on 2007-03-05
Not sure, I used this guide for 9, worked fine. See if it helps [http://wass.homelinux.net/howtos/Citrix_ICA_How-To.shtml](http://wass.homelinux.net/howtos/Citrix_ICA_How-To.shtml)

HTH Didijti

---

### Post by joeindo on 2007-03-06
I have had version 9 working on a previous install... I have since then reinstalled Ubuntu 6.06 and have just tried to install version 10 of citrix - I am unable to get it to work - I have followed several guides/suggestions for version 9.... When I get to my presentation server and attempt to execute one of the applications - nothing happens...:confused:

---

### Post by joeindo on 2007-03-06
Maybe this will help?

It hasn't helped me yet...

[http://support.citrix.com/forums/thread.jspa?forumID=16&threadID=86630](http://support.citrix.com/forums/thread.jspa?forumID=16&threadID=86630)

---

### Post by joeindo on 2007-03-06
Where is this????
[B]
Wfcmgr*fontList section 
of the Wfcmgr resource file in the $ICAROOT/nls/{language}/UTF-8 directory:[/B]

---

### Post by joeindo on 2007-03-06
I ran this in a terminal - and it worked ?


**xset fp rehash**

---

### Post by juanhunglow on 2007-03-06
> **joeindo said:**
> I ran this in a terminal - and it worked ?


**xset fp rehash**

Any chance you could give a more detailed description of how you made this work?  What steps did you follow with the install and what modifications did you do other than the "xset" command in the terminal.  I'll add it to the original post.  The more detail the better.

I did what I thought was a standard install, modified the files according to the readme file and did try to run 'xset' in the terminal but no love.

Please pass along your success and maybe we can help others.

---

### Post by joeindo on 2007-03-06
I did a standard install as well. Reading the readme file in the install folder explains something about :

4.9  The client may not start correctly on Ubuntu or other Debian-derived systems
---------------------------------------------------------------------------------
When using UTF-8 locales on Debian or Debian-derived systems such as Ubuntu, the 
client may not start correctly when the X libraries try to load the necessary 
Unicode font. You can avoid this issue either by running the client in a non 
UTF-8 locale, or by removing the following lines from the Wfcmgr*fontList section 
of the Wfcmgr resource file in the $ICAROOT/nls/{language}/UTF-8 directory:
-gnu-*-*-*-*-*-*-120-*-*-*-*-iso10646-1;\

-*-helvetica-medium-r-*-*-*-120-75-75-*-*-*-*;\
-*-*-medium-r-*-*-*-120-75-75-*-*-*-*;\
-*-*-medium-r-*-*-*-120-*-*-*-*-*-*:

Removing these lines prevents the client from trying to use any Unicode fonts, 
which can cause certain characters in published application names or window names 
to display incorrectly.
[#154155]

If I could find $ICAROOT/nls/{language}/UTF-8 directory and delete the lines mentioned above - I probably wouldn't have to run xset fp rehash...

I got the xset fp rehash idea from the citrix forum link:
[http://support.citrix.com/forums/thread.jspa?forumID=16&threadID=86630](http://support.citrix.com/forums/thread.jspa?forumID=16&threadID=86630)

---

### Post by joeindo on 2007-03-06
Another potentially helpful link:
[http://support.citrix.com/forums/forum.jspa?forumID=16](http://support.citrix.com/forums/forum.jspa?forumID=16)

---

### Post by kygil on 2007-03-06
I need help installing citrix onto ubuntu 6.10.
Here's the steps I've done so far:

downloaded v10.0 from citrix
gunzip <file>.tar.gz
tar -xvf <file>.tar
./setupwfc
finished install and closed
opened firefox & logged into citrix
clicked on link where it asked to "open with"
I selected this location: ....../ICAClient/linuxx86/wfica.sh
The small download box opens up but nothing else happens and the application doesn't load.

I'm new to linux and any help would be greatly appreciated.
Thanks

---

### Post by juanhunglow on 2007-03-08
> **kygil said:**
> I need help installing citrix onto ubuntu 6.10.
Here's the steps I've done so far:

downloaded v10.0 from citrix
gunzip <file>.tar.gz
tar -xvf <file>.tar
./setupwfc
finished install and closed
opened firefox & logged into citrix
clicked on link where it asked to "open with"
I selected this location: ....../ICAClient/linuxx86/wfica.sh
The small download box opens up but nothing else happens and the application doesn't load.

I'm new to linux and any help would be greatly appreciated.
Thanks

kygil,
I have been unable to get v10 of citrix working.  I have made the change according to the readme and run the rehash but still get nothing.  However, joeindo has had luck, so it does appear to be working for some.

I don't know that feisty will make a difference but I will be testing this in feisty just the same and let you know of the results.

In the meantime, I am using a combination of wine and IE4Linux to get access to my citrix server. If you need to know how to do that look at this post [http://www.ubuntuforums.org/showthread.php?t=314938]("http://www.ubuntuforums.org/showthread.php?t=314938")

---

### Post by manro on 2007-03-08
> **joeindo said:**
> I did a standard install as well. Reading the readme file in the install folder explains something about :

4.9  The client may not start correctly on Ubuntu or other Debian-derived systems
---------------------------------------------------------------------------------
When using UTF-8 locales on Debian or Debian-derived systems such as Ubuntu, the 
client may not start correctly when the X libraries try to load the necessary 
Unicode font. You can avoid this issue either by running the client in a non 
UTF-8 locale, or by removing the following lines from the Wfcmgr*fontList section 
of the Wfcmgr resource file in the $ICAROOT/nls/{language}/UTF-8 directory:
-gnu-*-*-*-*-*-*-120-*-*-*-*-iso10646-1;\

-*-helvetica-medium-r-*-*-*-120-75-75-*-*-*-*;\
-*-*-medium-r-*-*-*-120-75-75-*-*-*-*;\
-*-*-medium-r-*-*-*-120-*-*-*-*-*-*:

Removing these lines prevents the client from trying to use any Unicode fonts, 
which can cause certain characters in published application names or window names 
to display incorrectly.
[#154155]

If I could find $ICAROOT/nls/{language}/UTF-8 directory and delete the lines mentioned above - I probably wouldn't have to run xset fp rehash...

I got the xset fp rehash idea from the citrix forum link:
[http://support.citrix.com/forums/thread.jspa?forumID=16&threadID=86630](http://support.citrix.com/forums/thread.jspa?forumID=16&threadID=86630)

It works, thanks!!!

---

### Post by juanhunglow on 2007-03-08
> **joeindo said:**
> I did a standard install as well. Reading the readme file in the install folder explains something about :


joindo,
can you give me some information on what guide, or information, you used when installing the 32-bit libraries.  Also, links created to the 32-bit stuff as well as what directory you installed ICAClient.
Thanks.

---

### Post by TripleWithCheese on 2007-03-08
Here is what I did to get 10.0 to work with edgy, it took me couple days of searching the Citrix support site to get everything working

sudo apt-get install libxaw6 libmotif3

downloaded the .tar and unpackaged it.

cd to the directory you unpacked the tar to

then 

sudo ./setupwfc

accept all the defaults

the default install path is /usr/lib/ICAClient if yours is different the path below will change

cd /usr/lib/ICAClient/nls/en/UTF-8
sudo nano Wfcmgr

remove the lines under fontlist that read

-*-helvetica-medium-r-*-*-*-120-75-75-*-*-*-*;\
-*-*-medium-r-*-*-*-120-75-75-*-*-*-*;\
-*-*-medium-r-*-*-*-120-*-*-*-*-*-*:

These are the last three lines under the fontlist heading.

save and exit

finally
xset fp rehash

Fired up the Presentation Server Client, add a connection and away I went.

---

### Post by Esa on 2007-03-10
Had trouble with fonts also... following Citrix guide with one correction:

.........................         iso8859-6**[COLOR="Red"]:[/COLOR]**
!-*-helvetica-medium-r-*-*-*-120-75-75-*-*-*-*;\
!-*-*-medium-r-*-*-*-120-75-75-*-*-*-*;\
!-*-*-medium-r-*-*-*-120-*-*-*-*-*-*:

Moved the colon to the end of the new last line, that is.

No xset fp rehash was needed :)

---

### Post by acemics4 on 2007-03-23
Spent about 2 hours trying to figure it out.  Followed the instructions in the last 2 posts nad was finally able to fire up the Citrix client.  Thanks for your help guys, it worked!

Vin

---

### Post by firecat53 on 2007-03-29
I'm running fully updated Feisty (as of today) on AMD-64.

Followed all the instructions so far ... installed libmotif3, removed the font lines from the Wfcmgr file as directed, as shifted the colon to the end of the new line. Ran xset fp rehash. Restarted browser. Tried both firefox-64 and firefox32. Ran the wfcmgr program in /usr/lib/ICAClient. Nothing working!

When I run wfcmgr program I get:
```
./wfcmgr: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory

```

If a make a link to libXm.so.3 in /usr/lib32 and run wfcmgr, I get:
```
./wfcmgr: error while loading shared libraries: libXm.so.3: wrong ELF class: ELFCLASS64

```

When I run './wfica /tmp/launch.ica' to see why it won't start from the browser, I get:
```
Warning: locale not supported by C library, locale unchanged
Warning: locale not supported by Xlib, locale set to C
Warning: X locale modifiers not supported, using default
Warning: Unable to load any usable fontset
Error: Aborting: no fontset found

```

I'm using whatever the default locale is (American English, etc).

Any ideas??

thanks, Scott

---

### Post by juanhunglow on 2007-03-29
> **firecat53 said:**
> I'm running fully updated Feisty (as of today) on AMD-64.



I am also running Feisty 32-bit and have been meaning to update the original post with the fact that I installed v10 of the client, made no modifications to anything, and was/are able to use the citrix presentation client.  To my surprise the easiest install of citrix on any flavor of Ubuntu since I started using Ubuntu a few months ago.

Because your on 64-bit your going to have get the 32-bit environment going b/c there is no Linux 64-bit client for citrix.  You can try using the 64-bit guide mentioned in the first post of this thread, then try an install of citrix without making any modifications to the font files, etc..  

I believe the modifications (removing font lines, etc.) was a problem with citrix as it applied to versions of Ubuntu prior to Feisty.

Let us know if this works.

---

### Post by firecat53 on 2007-03-29
I am running 64-bit Feisty with the 32-bit libraries for Firefox, etc installed. I've tried it both with no modifications and with all the modifications outlined in this post. Still no dice.

Thanks for the input. 

Scott

---

### Post by firecat53 on 2007-04-01
Well, it finally decided to start working without any other interventions. Not sure what changed, but it works now!  I'll come back to this thread when I reinstall Feisty final :)

thanks!

Scott

edit:  Well, client works, but the wfcmgr still gives the error:
```
./wfcmgr: error while loading shared libraries: libXm.so.3: wrong ELF class: ELFCLASS64
```

I'd like to set my mapped drives without config file editing!  :)

Any ideas?

thanks.

---

### Post by juanhunglow on 2007-04-02
> **firecat53 said:**
>   I'll come back to this thread when I reinstall Feisty final :)



Sorry, no answers for you yet, although strange that you got some of it working without doing anything.  

I am currently using feisty 32 but have not tested 64.  However, since this is the 64-bit forum section, this will move from an edgy to feisty post (feisty centered/related I mean) once the final release comes, which is also when I plan to move to feisty 64 full time.

---

### Post by juanhunglow on 2007-04-03
> **firecat53 said:**
> Well, it finally decided to start working without any other interventions. Not sure what changed, but it works now!  I'll come back to this thread when I reinstall Feisty final :)

thanks!

Scott

edit:  Well, client works, but the wfcmgr still gives the error:
```
./wfcmgr: error while loading shared libraries: libXm.so.3: wrong ELF class: ELFCLASS64
```

I'd like to set my mapped drives without config file editing!  :)

Any ideas?

thanks.

Scott,

have you seen this post/site?
[http://zwhlug.org/HOWTO_Citrix]("http://zwhlug.org/HOWTO_Citrix")
refers to linking your problem file 'libXm.so.3'

---

### Post by firecat53 on 2007-04-03
That must be for an older version of Ubuntu.   libXm.so.3 and libXm.so.3.0.2 already exist in /usr/lib, and not in /usr/X11R6/lib.  I even tried making a link to libXm.so.3 in /usr/lib32.  Where else would wfcmgr look for libXm.so.3??

Thanks, Scott

---

### Post by juanhunglow on 2007-04-04
Edit to [OP ]("http://ubuntuforums.org/showpost.php?p=2250944&postcount=1")re: working citrix client in Feisty 64 (using beta CD with all updates as of April 3, 2007).

---

### Post by pluto1111 on 2007-04-05
I followed the directions from previous posts to edit the Wfcmgr file located at /usr/lib/ICAClient/nls/en/UTF-8/.  Citrix works only when I run xset fp rehash prior to running Citrix.  I was also able to run Citrix without editing the WFcmgr file by running xset fp rehash prior to running Citrix.  How can I get Citrix to run without having to run xset fp rehash everytime?

Thanks,

Troy

---

### Post by dtmilano on 2007-04-10
If you're having problems running Citrix ICA Client 10.0 for Linux in Ubuntu you can give citrix-icaclient-10-ubuntu script a try. The intention of this script is to solve most common problems found in running the client also providing some of the solutions described in this thread.
Download the script from [http://codtech.com/downloads/citrix-icaclient-10-ubuntu]("http://codtech.com/downloads/citrix-icaclient-10-ubuntu")
.

You must have Citrix ICA Client 10.0 for Linux installed before running the script.
If Citrix is installed in a system location use sudo to run it, and if the installation directory is not /usr/lib/ICAClient set ICAROOT=/path/to/your/dir in the environment.

```

diego@bruce$ export ICAROOT=/usr/lib/ICAClient
diego@bruce$ sudo bash /tmp/citrix-icaclient-10-ubuntu

```

---

### Post by juanhunglow on 2007-04-10
> **dtmilano said:**
>  The intention of this script is to solve most common problems found in running the client also providing some of the solutions described in this thread.


dtmilano,
thanks for adding this, i'll link it to the OP.  Can you let us know if this is 64-bit specific?

Also,  if anyone who is having problems tries this let us know the outcome.

---

### Post by dtmilano on 2007-04-11
I've tested it only in 32-bit, but should work on 64-bit too.
Please, let me know if you have encountered any problem.

---

### Post by dtmilano on 2007-04-12
Be sure that you are using latest citrix-icaclient-10-ubuntu script. Version 0.3 or higher (version is printed when the script runs).

---

### Post by pluto1111 on 2007-04-12
I ran the script posted by dtmilano, and Citrix now launches fine; thank you dtmilano!

I still have a problem inside of Citrix.  When I minimize a window inside of Citrix, there is no bottom panel displayed on my screen, therefore, when I want to bring the minimized application back to the desktop I have to re-launch the application.  Has anyone else experiences this?  Is there a solution?


Thanks!

---

### Post by dtmilano on 2007-04-12
Could you please elaborate ?
Are you running a full Citrix desktop or an application window ?
There's no button on the local or remote panel ?

---

### Post by juanhunglow on 2007-04-12
pluto,

I was going to ask the same thing and dtmilano

When I use the presentation server I had to adjust the size b/c it's a PIA to scroll up and down to see minimized windows.  Doesn't sound like you have the same problem.

---

### Post by techstop on 2007-04-13
> **pluto1111 said:**
> I followed the directions from previous posts to edit the Wfcmgr file located at /usr/lib/ICAClient/nls/en/UTF-8/.  Citrix works only when I run xset fp rehash prior to running Citrix.  I was also able to run Citrix without editing the WFcmgr file by running xset fp rehash prior to running Citrix.  How can I get Citrix to run without having to run xset fp rehash everytime?

Thanks,

Troy

I am having the same issue....

I am running ICA Client v10 on Edgy 32bit. I have run the script above and it works (although I couldn't work out which version of the script, I only downloaded it in the last couple of days and it doesn't display the version when I run it.) once. However, if I reboot, I can't get Citrix running again unless I run

```
xset fp rehash
```

Once I do that it works until the next reboot.

Why did Citrix have to go and break it? v9 worked perfectly!!! ](*,) ](*,) ](*,) 

PS. Citrix is "affectionately" known at our workplace as "Sh*trix"

EDIT: I just downloaded the script above again and it is now labelled "VERSION="0.3"" so I guess I have an older script. I'll run the new one and see how I go...

---

### Post by dtmilano on 2007-04-13
Yes, VERSION="0.3" solves the problem across reboots.

PS. Very funny the Sh*trix thing

---

### Post by techstop on 2007-04-13
> **dtmilano said:**
> Yes, VERSION="0.3" solves the problem across reboots.

PS. Very funny the Sh*trix thing

Unfortunately the reboot issue remains for me...

I have downloaded the latest script (v 0.3). I uninstalled the ICA client, and then installed it again. I have then run the new patch. I can then connect to a Citrix session, but only until I reboot. If I run the xset fp rehash command it works again, but only until a reboot. So, it seems that the reboot issue remains. I have tried uninstalling / installing / patching a couple of times, same result each time.

Any pointers?

---

### Post by pluto1111 on 2007-04-13
> **dtmilano said:**
> Could you please elaborate ?
Are you running a full Citrix desktop or an application window ?
There's no button on the local or remote panel ?

I am running  Citrix Presentation Server Client for Unix Version 10 on Ubuntu 6.10.  I believe the direct answer to your question would be an application window, since I'm opening a new window (application) inside Ubuntu.

Thanks!:)

---

### Post by bmcage on 2007-04-17
For the error on AMD64 version of edgy:

```
./wfcmgr: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
```

This is due to this library missing in /usr/lib32. You need to add it. 
Go to [http://packages.ubuntu.com/edgy/libs/libmotif3](http://packages.ubuntu.com/edgy/libs/libmotif3) and download the i386 .deb file. You need to have installed dpkg-dev (sudo apt-get install dpkg-dev)
Then in konsole:

```

dpkg-deb -X libmotif3_2.2.3-1.4_i386.deb libmotif3
cd libmotif3/
cd usr/lib
sudo cp libXm.so.3.0.2 /usr/lib32/
sudo ln -s /usr/lib32/libXm.so.3.0.2 /usr/lib32/libXm.so.3

```

Now the error with libXm not found will be away, and you can enjoy all the other errors with this package.

I had the following error: running /usr/lib/ICAClient/wfcmgr gives a segfault, after a lot of warnings related to fonts. 
My locale is nl, which apparently complicates things even more.  

The following solved that font problem: go to /usr/lib/ICAClient/nls/C/Wfcmgr and /usr/lib/ICAClient/nls/C/UTF-8/Wfcmgr, make sure they can be edited by the superuser (sudo chmod u+x filename), and open them as superuser in your favorite texteditor. In my case I need to change the fontsection by the following to make it work:

```

Wfcmgr*fontList:\
-*-gothic-medium-r-normal-*-*-120-*-*-*-*-ksc5601.1987-0;\
-*-helvetica-medium-r-*-*-*-120-75-75-*-*-iso8859-1;\
-*-ming-*-*-*-*-*-140-*-*-*-*-big5-0;\
-isas-fangsong ti-medium-r-normal--16-160-72-72-c-160-gb2312.1980-0;\
-*-helvetica-medium-r-normal--0-*-75-75-p-*-koi8-r;\
-*-helvetica-medium-r-*-*-*-120-75-75-*-*-iso8859-6;\
-*-arial-medium-r-*-*-*-120-75-75-*-*-iso8859-6;\
-*-*-medium-r-*-*-*-120-75-75-*-*-*-*;\
-*-kacstbook-medium-r-*-*-*-120-75-75-*-*-iso8859-6;\

```

and now /usr/lib/ICAClient/wfcmgr is working. Note that I needed to add -*-*-medium-r-*-*-*-120-75-75-*-*-*-* to the list of fonts which on other sites is said has to deleted... I think much depends on your installed locale and fonts. If changing this fontlist still gives you font errors, check the top of the error where the fontlist is given to see if the wfcmgr file used is the one you are editing

---

### Post by bmcage on 2007-04-17
Can somebody post his 
~/.ICAClient/wfclient.ini
file?

That is, if stuff related to fonts is present in it, as here wfcmgr works, but wfica still throws an error:

```

Warning: locale not supported by C library, locale unchanged
Warning: locale not supported by Xlib, locale set to C
Warning: X locale modifiers not supported, using default
Error: 12 (E_MISSING_INI_ENTRY)
Please refer to the documentation.
Warning: Unable to load any usable fontset
Error: Aborting: no fontset found

```

---

### Post by dtmilano on 2007-04-17
Have you run citrix-icaclient-10-ubuntu script ?
What is the output of locale cmd ?

---

### Post by firecat53 on 2007-04-17
bmcage:

  I attached my wfclient.ini as you requested. I made no manual changes to it. It was all generated automatically and only changed from wfcmgr.

   Which, by the way, thank you for the libmotif3 trick! That got wfcmgr running for me.

Scott

---

### Post by allenmaher on 2007-04-18
Hi folks I have tried the instructions above, and the bash script was unable to make patches... then the thing did not work afterwards.  This is what the output looks like 

```
Warning: 
    Name: FilterText
    Class: XmTextField
    Character '\164' not supported in font.  Discarded.

Warning: 
    Name: FilterText
    Class: XmTextField
    Character '\164' not supported in font.  Discarded.

Warning: 
    Name: FilterText
    Class: XmTextField
    Character '\171' not supported in font.  Discarded.

Warning: 
    Name: FilterText
    Class: XmTextField
    Character '\123' not supported in font.  Discarded.

Warning: 
    Name: FilterText
    Class: XmTextField
    Character '\52' not supported in font.  Discarded.

Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Error: Aborting: no fontset found

```

The last set of warnings coming when I try and connect to a server.  I tried the font modification above, but to no avial...  I had version 9 working on a dapper machine last year, it was simple...:popcorn:  this is very odd/frustrating.  Any ideas what I am doing wrong?:confused:

---

### Post by techstop on 2007-04-18
> **techstop said:**
> Unfortunately the reboot issue remains for me...

I have downloaded the latest script (v 0.3). I uninstalled the ICA client, and then installed it again. I have then run the new patch. I can then connect to a Citrix session, but only until I reboot. If I run the xset fp rehash command it works again, but only until a reboot. So, it seems that the reboot issue remains. I have tried uninstalling / installing / patching a couple of times, same result each time.

Any pointers?

dtmilano, I downloaded the script again and this time it is marked version 0.5. It now works across reboots. I never would have found it except for downloading again. Maybe put the version number in the filename, or edit your post when you release a new version? Thanks for your work in getting it working though! :mrgreen:

---

### Post by dtmilano on 2007-04-19
Thanks for having suggested this.
There's now a note on top of the wiki page ([http://codtech.com/wiki/index.php/Citrix_ICA_Client_10_on_Ubuntu_6.10_Edgy_Eft](http://codtech.com/wiki/index.php/Citrix_ICA_Client_10_on_Ubuntu_6.10_Edgy_Eft)).

> 
IMPORTANT:

Latest version of the script is available always at [http://codtech.com/downloads/citrix-icaclient-10-ubuntu](http://codtech.com/downloads/citrix-icaclient-10-ubuntu) and previous versions are always available at the same folder citrix-icaclient-10-ubuntu-version (i.e.: citrix-icaclient-10-ubuntu-0.4)

---

### Post by spidie on 2007-04-19
Hi All

Some useful tips here in this thread - thanks to everyone for all the hard work I have a edgy and a feisty box and have box of them running ICAClient now - however access to our citrix servers is all through a webpage and it doesn't look like the firefox plugin is working correctly for me. 

If I navigate to our [http://mycitrix](http://mycitrix) page I get the error:

ERROR: There are no authentication methods currently available.

And all the login boxes are greyed out.

Any ideas? I am running full updated feisty (kubuntu) with ICA 10 - I have also tried it with ICA 9 with same result.

Alternatively, does anyone know if is there a way that I can find out the underlying Citrix server address from this page?

Steve

ps. Another thing I noticed - wfcmgr looks fine for me with ICA9 - but with ICA10 all the characters are double spaced out - works fine, just looks weird!

---

### Post by juanhunglow on 2007-04-20
> **spidie said:**
> Hi All

Some useful tips here in this thread - thanks to everyone for all the hard work I have a edgy and a feisty box and have box of them running ICAClient now - however access to our citrix servers is all through a webpage and it doesn't look like the firefox plugin is working correctly for me. 

If I navigate to our [http://mycitrix](http://mycitrix) page I get the error:

ERROR: There are no authentication methods currently available.

And all the login boxes are greyed out.

Any ideas? I am running full updated feisty (kubuntu) with ICA 10 - I have also tried it with ICA 9 with same result.

Alternatively, does anyone know if is there a way that I can find out the underlying Citrix server address from this page?

Steve

ps. Another thing I noticed - wfcmgr looks fine for me with ICA9 - but with ICA10 all the characters are double spaced out - works fine, just looks weird!

I'm a little shaky on what might be your problem.  Don't suppose you could supply a screenshot??

---

### Post by firecat53 on 2007-04-20
Steve...Try going in a changing the file association for .ica files in Firefox to /usr/lib/ICAClient/wfica (or wherever your wfica is) instead of using the plugin.  You can test that it works by finding the ica file (under /tmp, or something) and running 'wfica /tmp/launch.ica' from the command line. At least then you can see what errors are coming up.

Good luck!

Scott

---

### Post by bbrewerg on 2007-04-20
i had v10 running fine under Edgy Eft... upgraded to Feisty last night and now my ICA connections window is all effed up (spacing on the fonts is insane, a 8 letter word takes up an entire field)... anyone have any ideas on how to get my fonts back to normal?

[IMG]http://files.bbrewer.net/Pics/citrix.png[/IMG]

---

### Post by pluto1111 on 2007-04-22
Hello, 



I'm wondering if anyone has found a solution to the problem I'm experiencing with no task bar displayed.  I've attached 2 screen shots of what I'm  seeing.



> I still have a problem inside of Citrix. When I minimize a window inside of Citrix, there is no bottom panel displayed on my screen, therefore, when I want to bring the minimized application back to the desktop I have to re-launch the application. Has anyone else experiences this? Is there a solution?



I am running Citrix Presentation Server Client for Unix Version 10 on Ubuntu 6.10. I believe this is occurring inside the application window, since I'm opening a new window (application) inside Ubuntu.



Thanks for the help!

---

### Post by juanhunglow on 2007-04-22
> **pluto1111 said:**
> Hello, 

I'm wondering if anyone has found a solution to the problem I'm experiencing with no task bar displayed.  I've attached 2 screen shots of what I'm  seeing.

Thanks for the help!

On the right you have a scroll bar.  It's a PIA b/c it doesn't work like normal, you actually have to right click to scroll up and down.

I remedied this problem by changing my settings on my log in page.  Play with those settings until you get one that fits everything on the page.  my magic number is 1024x768.  This way I have no scroll bars to deal with.

Hope this helps.  If your having other issues let us know.

---

### Post by dtmilano on 2007-04-23
> **bbrewerg said:**
> i had v10 running fine under Edgy Eft... upgraded to Feisty last night and now my ICA connections window is all effed up (spacing on the fonts is insane, a 8 letter word takes up an entire field)... anyone have any ideas on how to get my fonts back to normal?

[IMG]http://files.bbrewer.net/Pics/citrix.png[/IMG]


The latest version of the script citrix-icaclient-10-ubuntu (0.7) supports Ubuntu 7.04 and solves this problem, AFAIK.
You can donwload it from [http://codtech.com/downloads/citrix-icaclient-10-ubuntu](http://codtech.com/downloads/citrix-icaclient-10-ubuntu).
As usual, information on this script can be found at [http://codtech.com/wiki/index.php/Citrix_ICA_Client_on_Ubuntu](http://codtech.com/wiki/index.php/Citrix_ICA_Client_on_Ubuntu).

Comments, suggestions and bug reports are gladly welcome.

---

### Post by bmcage on 2007-04-23
Ok, I have Citrix working on AMD64, Kubuntu Feisty, with link in firefox working, and starting up the client automatically. 

What I did different with my previous post: 
1. upgraded Kubuntu edgy to Kubuntu Feisty, AMD64
2. run ```
./setupwfc
``` to **UNINSTALL** the previous citrix client
3. run ```
./setupwfc
``` to **INSTALL** the citrix client

So now I have citrix installed in /usr/lib/ICAClient 
Go to that directory, running ./wfcmgr starts the citrix manager, but the fonts are doublespaced. So I played with the font setting to get this corrected. I ended up with changing in */usr/lib/ICAClient/Wfcmg*r and */usr/lib/ICAClient/UTF-8/Wfcmgr* the fontList section to (use *sudo gedit* or *sudo kate*, make a backup copy of the file first):

```

Wfcmgr*fontList:\
-*-helvetica-medium-r-normal--0-*-75-75-p-*-koi8-r;\
-*-helvetica-medium-r-*-*-*-120-75-75-*-*-iso8859-6;\
-*-helvetica-medium-r-*-*-*-120-75-75-*-*-*-*:
-*-gothic-medium-r-normal-*-*-120-*-*-*-*-ksc5601.1987-0;\
-*-ming-*-*-*-*-*-140-*-*-*-*-big5-0;\
-isas-fangsong ti-medium-r-normal--16-160-72-72-c-160-gb2312.1980-0;\
-*-arial-medium-r-*-*-*-120-75-75-*-*-iso8859-6;\
-*-kacstbook-medium-r-*-*-*-120-75-75-*-*-iso8859-6;\
-*-*-medium-r-*-*-*-120-75-75-*-*-*-*;\

```

This works on Feisty, and now shows the manager with correct fonts (no double space). I think the manager uses the first font, so the order of these fonts is important.

In the standard firefox install of Feisty (for Kubuntu package firefox must be installed **before** you install the citrix client, this is 2.0.0.3 in my case), I go to the citrix page of my university [https://athena.ugent.be](https://athena.ugent.be), and yes firefox suggests to open the links with *wfica.sh*, it works, Office 2007 starts, ... 

So, note that I did NOT run any script, only manual edit  of the config file! 
Note that for citrix you need 32 bit libs installed, so see my post [http://ubuntuforums.org/showpost.php?p=2467386&postcount=39](http://ubuntuforums.org/showpost.php?p=2467386&postcount=39) for installing libXm.so.3

---

### Post by bbrewerg on 2007-04-23
> **dtmilano said:**
> The latest version of the script citrix-icaclient-10-ubuntu (0.7) supports Ubuntu 7.04 and solves this problem, AFAIK.
You can donwload it from [http://codtech.com/downloads/citrix-icaclient-10-ubuntu](http://codtech.com/downloads/citrix-icaclient-10-ubuntu).
As usual, information on this script can be found at [http://codtech.com/wiki/index.php/Citrix_ICA_Client_on_Ubuntu](http://codtech.com/wiki/index.php/Citrix_ICA_Client_on_Ubuntu).

Comments, suggestions and bug reports are gladly welcome.

FANTASTIC!  Thanks for the assistance, it worked like a charm!

---

### Post by juanhunglow on 2007-04-24
Updated OP with script wiki link and info re: success on Kubuntu Feisty

---

### Post by eholcroft on 2007-04-26
I'm still struggling with this. The installation was successful and the script (v7 on Feisty) ran without errors. The display of the fonts in the client is now fixed. But when I run 

/usr/lib/ICAClient/wfcmgr

I still get this when I click on the connect button:

Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Error: Aborting: no fontset found

Any ideas?

ed

---

### Post by feniix on 2007-05-06
Here is doing some strange stuff

```

Error: 11 (E_MISSING_INI_SECTION)
Please refer to the documentation.
Error: 12 (E_MISSING_INI_ENTRY)
Please refer to the documentation.
Error in configuration file:
  "AccessGatewayClientLaunch.vcagc"
Cannot find section "ApplicationServers".

```

Any ideas ??


Thanks in advance

---

### Post by pluto1111 on 2007-05-07
> I remedied this problem by changing my settings on my log in page. Play with those settings until you get one that fits everything on the page. my magic number is 1024x768. This way I have no scroll bars to deal with.

Thank you for your help.  I figured out the scroll bars, but I'm not sure where I change the settings on my log in page to make the window larger to eliminate the need to scroll.  Are you referring to the citrix log in page?

Thanks again:)

---

### Post by nicksukharev on 2007-05-11
> **eholcroft said:**
> 

Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Error: Aborting: no fontset found
ed

I finally fixed it as described in this [thread]("http://ubuntuforums.org/showthread.php?t=387682&highlight=ICAClient"). I am still on Edgy, upgraded from Dapper.

---

### Post by juanhunglow on 2007-05-11
> **pluto1111 said:**
> Thank you for your help.  I figured out the scroll bars, but I'm not sure where I change the settings on my log in page to make the window larger to eliminate the need to scroll.  Are you referring to the citrix log in page?

Thanks again:)

Yes, mine provides a few icons.  one is settings.  from there i pick the correct size.

---

### Post by doctoss on 2007-05-26
I did not have to add any script. I downloaded the citrix client 10 and just double clicked it on the desktop, then ran the setup file. I chose all the defaults.  When I opened firefox and went to the webpage needing citrix and it asked me with which file to open launch.ica I directed it to the wfica file and it opened fine. I hope that is all there is. I am using feisty 7.04

---

### Post by vbmds on 2007-05-28
Well, I've had a sucessful run through of the initial posts steps and have been able to log into the wife's works web portal, logging onto her work PC :popcorn:

My linux is as follows: Ubuntu 7.04 64 running KDE 3.5.2 - thus I opted to install IceWeasel for the 32bit web browser. 

And yes before anyone makes the obvious remark, I have found kubuntu unstable on my system...but ubuntu is stable.

---

### Post by pluto1111 on 2007-06-04
Hello.  I am going crazy trying to figure out how I can have the Citrix window the same size as my desktop.  Please see post #50 for screen shots.  

The strange this is, everyone once in awhile the Citrix screen fills my desktop like one would expect it to do.  However, I am unable to duplicate the "filling of the desktop", it happens sporadically.  

I tried modifying the wfclient.ini file in the /home/user/.ICAClient directory, but this still does not solve the problem.  I even modified the /usr/lib/ICAClient/config/wfclient(Root) and changed desired HRES to 1024 and VRES to 768, but this still did not work.  I read in the Citrix Admin Guide that version 10.x+ requires a change to the All_Regions.ini file in addition to the wfclient.ini file for changes to take affect.  I looked at the All_Regions file, but I'm not sure what I would have to change. 

> Important From Version 10.x of the client, for each entry in appsrv.ini and
wfclient.ini, there must be a corresponding entry in All_Regions.ini for the
setting to take effect. In addition, for each entry in the [Thinwire3.0],
[ClientDrive], and [TCP/IP] sections of wfclient.ini, there must be a
corresponding entry in canonicalization.ini for the setting to take effect. See the
All_Regions.ini and canonicalization.ini files in the $ICAROOT/config directory
for more information.


Any help would be much appreciated.

Thank you.

---

### Post by Mäx1 on 2007-06-14
PLZ PLZ help me!

I tried out all of these Tips and more, but ICA 10 doesnt work on my Ubuntu 7.04.

I tried:
- the tips in the readme
- the script version 0.7
- "xset fp rehash"


wfcmgr is working fine, i can add a new connection, when i connect i get:
[B]
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Error: Aborting: no fontset found
[/B]

i dont know what to do now!  :(

---

### Post by gene74 on 2007-06-19
im able to login to my employer's initial citrix login
then i click on another link to open up and connect to a server
but i get a small pop up window with this error

could not find the file in /home/computername/.ICACLIENT/All_regions.ini 
i checked the location, i do not have it
does any one have a copy of it?

---

### Post by cognitive on 2007-06-19
Hallo,

I am happy to find some help here - I have a problem with both Java & and the Client (vers. 10)
I alway get the following Error: 

*"You have not chosen to trust "GlobalSign Root CA", the issuer of the server's security certificate"*


Did anyone encounter the same problem? Thanks a lot in advance.

**Okay, Problem Solved**

Found the certificate

---

### Post by juanhunglow on 2007-06-19
> **gene74 said:**
> im able to login to my employer's initial citrix login
then i click on another link to open up and connect to a server
but i get a small pop up window with this error

could not find the file in /home/computername/.ICACLIENT/All_regions.ini 
i checked the location, i do not have it
does any one have a copy of it?

gene74, have you found an answer to your problem yet.  I think, depending on your browser, you need to tell it to launch wfica in the icaclient folder (wherever you told it to install).  if the browser is trying to user some other program, remove the association, or browse to wfica.  It should then launch the presentation server.

Let us know if this is not the problem or does not solve your problem.

---

### Post by gene74 on 2007-06-19
how do you remove the association?


well i saved the file to the desktop and right to use another app.
then i went to the usr/lib/icaclient and pointed to wfica
still got the same error

---

### Post by juanhunglow on 2007-06-20
> **gene74 said:**
> how do you remove the association?


If you are using Firefox it is in the preferences/options under file types.

---

### Post by gene74 on 2007-06-22
can anyone just post their all regions.ini file and see if i can just save it on my comp?

---

### Post by Joe325 on 2007-06-29
im able to login to my employer's initial citrix login
then i click on another link to open up and connect to a server
but i get a small pop up window with this error

could not find the file in /home/computername/.ICACLIENT/All_regions.ini
i checked the location, i do not have it
does any one have a copy of it?

Hi Gene74

Heres a copy of the 'All regions' file.

Enjoy ;)

---

### Post by gene74 on 2007-06-29
TY will try this tonite.

---

### Post by gene74 on 2007-06-30
well it worked but now its prompting me for the trusted_regions.ini


LOL

---

### Post by aspen on 2007-08-13
hello, 
today i got some strange messages from my citrix client.
i`m running an ubuntu feisty, fully updated with an ICA client v.9
and i had never problems with fonts or something like that.

i tried to connect to our terminalserver, but it didn`t work.
i got an message like "network or dial-up problems are preventing communiction with the server"

i never had this message before, so i updated my ica client to the newest version which is 10.6
the installation was simple and straight forward.

i also get no error message when running ~/ICAClient/linuxx86/wfcmgr.
the gui pops up, but as soon as i try to login i get the network error.

i searched he forum and used google.
i found a link [http://misconfig.blogspot.com/2007/05/installing-citrix-on-linux-ubuntu.html](http://misconfig.blogspot.com/2007/05/installing-citrix-on-linux-ubuntu.html)
but this didn`t help either.

this all happens on my fujitsu-siemens notebook, running an up2date feisty and the latest citrix client.

from now, i have to log into my vpn@home and have to use my old workstation running dapper lts and citrix client v.9

this works like charm. but its a little odd to log into a vpn, open rdesktop, to log on to another mashine to use citrix.

maybe some of you have a clue or a trick which can help to solve my problem.

thx and best regards
aspen

---

### Post by waruskta on 2007-11-11
I too had this issue and just created the files blank (touch filename) ..
That took care of the inital issue and then the files populated themselfs..

Now, the app just core dumps.

I get the inital desktop from my citrix site, then click on the app i want to start and save the "file" .. I then went to a terminal and ran the app and it starts to initalize.. after a few moments, I get a core dump..

---

### Post by infurnus on 2007-11-12
"The Citrix ICA client version installed from this workstation does not meet minimum requirements for security and support. Please report this non-compliancy to your local technical support to upgrade your system with ICA client 10.0 or later"

I have just installed the ICAClient to /usr/lib/ICAClient if i echo $ICAROOT i get /usr/lib/ICAClient. Steps i took: logged via web interface it runs all the scripts and at the end it fails with the error above i have installed the patch and followed the directions here [http://misconfig.blogspot.com/2007/0...ux-ubuntu.html](http://misconfig.blogspot.com/2007/0...ux-ubuntu.html)
I have also looked through citrix's knowledge base and cannot find an answer i did download all the certs off their website and put them under /usr/lib/ICAClient/keystore/cacerts to make sure that wasnt a problem and i still receive the same error above. Can anyone shed light on my problem?

I am running Ubuntu 7.10 now and i have got the latest version of Citrix client from their website.
This was working with dapper before some update was done. Since it happened in dapper it has to be something with the recent release.

---

### Post by aceghostwind on 2007-11-17
Hi,
You best check that the logon point is web interface and not a Citrix Advanced Access Control (via a Citrix Access Gateway Advanced)  because if it is the latter they may have endpoint scanning (very windows dependent) enabled which may rule you out using Linux. If the logon point is AAC and you want the Admin to make an exception for you (Linux) you could get them to try the Client-less Client Scan for Citrix AAC 4.5 and 4.5.1 from [www.EPAFactory.com](www.EPAFactory.com). This detects OS based on the browser User-Agent string so will work for any OS with out the need for a client  Endpoint scan.
:)

---

### Post by Devastator9 on 2007-11-18
First post here worked great for me on new install of 7.10 thanks for the post.

Dev

---

### Post by drodiger on 2007-12-19
Hi guys,

I found out why my wfica wasn't starting.
First I fixed font issue, but I was still getting Error: Aborting: no fontset found.
Then I checked my locale. LANG="en_US.UTF-8"
You now see that this is not locale for Citrix 10.6 wfica. It should be en.UTF-8 or en only.
So solution was 
% export LANG=en.UTF-8
% firefox

After that launch.ica was starting, but now I have to get my CA since I am getting SSL error 61.

So set your locale LANG

I will also try to copy /usr/lib/ICAClient/nls/en to en_US if it will help.

---

### Post by evilhomer on 2007-12-28
yesssssssssssssssssssssssssssss!!!!

you're the man!

% export LANG=en.UTF-8

fixed this prob on 7.04 w/10.7

Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Error: Aborting: no fontset found

I have looked *everywhere* for this fix.  How can I make it persist after reboot?

Thanks.

---

### Post by kpurrucker on 2008-02-10
I had a simular problem. I could configure a ica connection, but i couldn't start the connection. The wfcmgr-program says only "Cannot load font" and "no fontset found", if i start it on the commandline. A look in the x-server log told me, that I had some wrong paths in the file "/etc/X11/xorg.conf". The paths should be "/usr/share/fonts/X11/<fontname>". In my xorg.conf were some fonts in the section "Files" with the wrong path "/usr/share/X11/fonts/". I thing it is, because i update my Ubuntu from a older version, as Gutsy.

You find a smarter (but german :)) version of the resulotion in my blog [http://blog.purrucker.de/2008/02/04/installation-eines-ica-clients-106-unter-ubuntu-710/](http://blog.purrucker.de/2008/02/04/installation-eines-ica-clients-106-unter-ubuntu-710/)

---

### Post by crjackson on 2008-02-10
> **kpurrucker said:**
> I had a simular problem. I could configure a ica connection, but i couldn't start the connection. The wfcmgr-program says only "Cannot load font" and "no fontset found", if i start it on the commandline. A look in the x-server log told me, that I had some wrong paths in the file "/etc/X11/xorg.conf". The paths should be "/usr/share/fonts/X11/<fontname>". In my xorg.conf were some fonts in the section "Files" with the wrong path "/usr/share/X11/fonts/". I thing it is, because i update my Ubuntu from a older version, as Gutsy.

You find a smarter (but german :)) version of the resulotion in my blog [http://blog.purrucker.de/2008/02/04/installation-eines-ica-clients-106-unter-ubuntu-710/](http://blog.purrucker.de/2008/02/04/installation-eines-ica-clients-106-unter-ubuntu-710/)

It would be great if I could read German...

---

### Post by kpurrucker on 2008-02-11
> **crjackson said:**
> It would be great if I could read German...

I'm sorry for that. I will try to say it better in englisch. :-k

The essential of my operating experience is: The ICA-Client does'nt start in some case, because the files-section of the file "/etc/X11/xorg.conf" contains wrong paths. The paths from the fonts in this section should be "/usr/share/fonts/X11/<fontname>" and not /usr/share/X11/fonts/". I have this problem on two pc's, witch are upgraded from an older Ubuntu Version. I have'nt this problem on a other new installed pc with Ubuntu 7.10. I find also descriptins from other users with the same problem. It seems to be a problem on many ubuntu-installations, witch are upgraded from older ubuntu-versions.

---

### Post by michiel33 on 2008-02-18
I had Citrix working one time after having installed the client! However now when I connect to my company Citrix portal and start an application, it asks me what to do with the launch.ica file! I have no clue what to do with it! Should I associate it with something? With what?

Help is appreciated!
Regards, Michiel

---

### Post by mkasun on 2008-02-18
I have tried to get the new Citrix client working and I can connect to the server at work but when I try to launch an application I get a window that says "Citrix Presentation Server" and the tile bar has
Connected to server ; 40; STACD4C......

after awhile it times out and a dialog box comes saying 
Network or dialup problems are preventing communications with the server.
An attempt to automatically restore the connection will begin after a delay to let the network recover.

If the problem persists, contact your network administrator.

---

### Post by stash1071 on 2008-03-27
Hello, I've followed as much as the advice as I could in this post.  I think I'm pretty close, but I can find nothing on the error I'm now getting when running launch.ica with wfica.
I'm running 7.10.

```

Error: 235 (E_LOCKDOWN_ERROR_GENERIC)
Please refer to the documentation.
Client Configuration Manager: Internal error -1

```

Thanks

---

### Post by stash1071 on 2008-03-27
I removed all my *Region*.ini files, and it worked fine, weird...

---

### Post by matogrosso on 2008-05-12
No luck for me. Please anyone help.

oscar@oscar:~/tmp/Citrix/Client$ cd /usr/lib/ICAClient
oscar@oscar:/usr/lib/ICAClient$ ./wfcmgr
./wfcmgr: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
oscar@oscar:/usr/lib/ICAClient$

---

### Post by stankopp on 2008-05-14
I am trying to install the 10.6 version of the Citrix ICAClient in Ubuntu 8.04 and I can not even get ICAClient to install.  I have downloaded and upacked the tar and when I execute "sudo ./setupwfc", I get the following output and not any of the installation options:
/home/kopp/Citrix/en.linuxx86/linuxx86/hinst: 236: /home/kopp/Citrix/en.linuxx86/linuxx86/echo_cmd: not found
/home/kopp/Citrix/en.linuxx86/linuxx86/hinst: 237: /home/kopp/Citrix/en.linuxx86/linuxx86/echo_cmd: not found
/home/kopp/Citrix/en.linuxx86/linuxx86/hinst: 238: /home/kopp/Citrix/en.linuxx86/linuxx86/echo_cmd: not found
/home/kopp/Citrix/en.linuxx86/linuxx86/hinst: 239: /home/kopp/Citrix/en.linuxx86/linuxx86/echo_cmd: not found
/home/kopp/Citrix/en.linuxx86/linuxx86/hinst: 4011: /home/kopp/Citrix/en.linuxx86/linuxx86/echo_cmd: not found
/home/kopp/Citrix/en.linuxx86/linuxx86/hinst: 4027: /home/kopp/Citrix/en.linuxx86/linuxx86/echo_cmd: not found
/home/kopp/Citrix/en.linuxx86/linuxx86/hinst: 4043: /home/kopp/Citrix/en.linuxx86/linuxx86/echo_cmd: not found
/home/kopp/Citrix/en.linuxx86/linuxx86/hinst: 4043: /home/kopp/Citrix/en.linuxx86/linuxx86/echo_cmd: not found
/home/kopp/Citrix/en.linuxx86/linuxx86/hinst: 4043: /home/kopp/Citrix/en.linuxx86/linuxx86/echo_cmd: not found
/home/kopp/Citrix/en.linuxx86/linuxx86/hinst: 4043: /home/kopp/Citrix/en.linuxx86/linuxx86/echo_cmd: not found

I have tried several different unpack options.  I have tried the rpm package installer.  I have tried converting the rpm to a deb and that also fails.

Anyone have any ideas?

---

### Post by stankopp on 2008-05-15
I have solved my problem.  These errors were the result of NOT having the 32-bit libraries installed.  I thought that I had installed them, but apparently I had not.

I got the necessary libraries by opening a terminal and executing the command:

sudo apt-get install ia32-libs

I got that command from another thread that I found by searching the Ubuntu fora for "echo_cmd"  Thanks to that responder!

I was then able to execute the ./setupwfc

I chose to install, accept the license and also chose to integrate with KDE - Gnome.

I now am able to connect to my Citrix desktop at work with my Hardy Heron 64-bit laptop!

---

### Post by ahbart on 2008-05-26
> **mkasun said:**
> I have tried to get the new Citrix client working and I can connect to the server at work but when I try to launch an application I get a window that says "Citrix Presentation Server" and the tile bar has
Connected to server ; 40; STACD4C......

after awhile it times out and a dialog box comes saying 
Network or dialup problems are preventing communications with the server.
An attempt to automatically restore the connection will begin after a delay to let the network recover.

If the problem persists, contact your network administrator.

Hello Mkasun and others, 
I have exactly the same problem. last week it worked great, but now it suddenly stopped working with the above messages. 
Is there a solution for this?
Bart

---

### Post by dseeto on 2008-06-23
> **ahbart said:**
> Hello Mkasun and others, 
I have exactly the same problem. last week it worked great, but now it suddenly stopped working with the above messages. 
Is there a solution for this?
Bart

I am having the exact same problem. I am able to connect to servers with VMWare Server 1.06, running XP and 10.2 Window ICA client. So it's not the connection.
I am able to connect to a previous version of my co. Citrix using Ubuntu directly with Firefox 3 on one tab. So it would seem that ICA client is also ok?
Any Citrix gurus?

---

### Post by mtrainer on 2008-06-24
> **joeindo said:**
> I did a standard install as well. Reading the readme file in the install folder explains something about :

4.9  The client may not start correctly on Ubuntu or other Debian-derived systems
---------------------------------------------------------------------------------
When using UTF-8 locales on Debian or Debian-derived systems such as Ubuntu, the 
client may not start correctly when the X libraries try to load the necessary 
Unicode font. You can avoid this issue either by running the client in a non 
UTF-8 locale, or by removing the following lines from the Wfcmgr*fontList section 
of the Wfcmgr resource file in the $ICAROOT/nls/{language}/UTF-8 directory:
-gnu-*-*-*-*-*-*-120-*-*-*-*-iso10646-1;\

-*-helvetica-medium-r-*-*-*-120-75-75-*-*-*-*;\
-*-*-medium-r-*-*-*-120-75-75-*-*-*-*;\
-*-*-medium-r-*-*-*-120-*-*-*-*-*-*:

Removing these lines prevents the client from trying to use any Unicode fonts, 
which can cause certain characters in published application names or window names 
to display incorrectly.
[#154155]

If I could find $ICAROOT/nls/{language}/UTF-8 directory and delete the lines mentioned above - I probably wouldn't have to run xset fp rehash...

I got the xset fp rehash idea from the citrix forum link:
[http://support.citrix.com/forums/thread.jspa?forumID=16&threadID=86630](http://support.citrix.com/forums/thread.jspa?forumID=16&threadID=86630)

I was getting Chinese or Korean fonts running wfcmgr so I commented out the lines above in the wfcmgr resource file as above.  That fixed the problems with the fonts in wfcmgr but when I connect a session the connection messages and dialog when I close the session are still in the foreign font.  I tried editing/changing the font related entries in the Wfica file without any success.  Has anybody had/fixed that issue?

Thanks

Murray

---

### Post by dmac71 on 2008-07-12
Can anyone tell me how to install citrix v. 10 on Hardy?  I am new to linux and I can find the tar download, but I do not understand how to install it.  I am using the 64 bit version of Hardy on an HP Pavilion 9720us laptop.  Also, does the citrix client work with a network that is using windows xp?

---

