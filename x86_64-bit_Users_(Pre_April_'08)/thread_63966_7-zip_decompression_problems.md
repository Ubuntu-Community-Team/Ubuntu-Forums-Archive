---
title: "7-zip decompression problems"
date: 2005-09-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by thundertoad on 2005-09-09
Hey y'all,
Just wandering here... is there any applications other than File-roller that support 7-zip decompression? I downloaded this file that has a .7z extension and it seems that file-roller doesnt want to decompress it for some odd reason even though I did a search on the forum and several posts say that file-roller does decompress the... maybe its a newer format or something... any ideas?

I am running ubuntu for amd64 so is there any other application ported that can handle this extension.

Thanks,
ThunderToad

---

### Post by DJ_Max on 2005-09-09
Have you looked at [https://wiki.ubuntu.com/FileCompression](https://wiki.ubuntu.com/FileCompression) ?

---

### Post by thundertoad on 2005-09-09
[QUOTE=DJ_Max]Have you looked at [https://wiki.ubuntu.com/FileCompression](https://wiki.ubuntu.com/FileCompression) ?[/QUOTE]
 Actually, no... Thanks for bringing it to my attention... ran a few search strings but nothing came up.. at least nothing I could use.. i'll take a look and tell you if found anything... thanks

---

### Post by thundertoad on 2005-09-09
yeah it said I needed to install p7zip and then associate the files from the properties (right clicking on them gets you the submenu... choose properties) problem is that I have the universe repository but I tells me this:

Reading package lists... Done
Building dependency tree... Done
Package p7zip is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package p7zip has no installation candidate


so .. is this because this package is no longer available or is it because I am running the Hoary Hedgehog (aka ron jeremy) amd64 version

any ideas?

---

### Post by negatory on 2005-09-09
I can't seem to find it also...Even in the chroot so it's not a 32bit only package.Maybe the package was removed for some reason...I really don't know...
Pedro Carrico

---

### Post by DJ_Max on 2005-09-09
[QUOTE=negatory]I can't seem to find it also...Even in the chroot so it's not a 32bit only package.Maybe the package was removed for some reason...I really don't know...
Pedro Carrico[/QUOTE]
 Hrmm, I can't find it either. It must be bundled with another package.

---

### Post by matthew on 2005-09-09
The best I can do for you is redirect you to the p7zip official site at [http://p7zip.sourceforge.net/](http://p7zip.sourceforge.net/)

I have never used it, so I don't know a thing about it, but there is a forum link there where hopefully you can find help.

---

### Post by thundertoad on 2005-09-09
Checked out that link... no amd64 builds in the debian section.
Hey at least I am not the only one who didnt find that file.. it was freaking me out there for a second... well freaking me out is a tad melodramatic... it was more annoying me... like when you got water in your ears..

what the hell am I talking about... I need sleep

any other suggestions? any amd64 ports of p7zip? anyone at all?

Th'Undertoad

---

### Post by matthew on 2005-09-09
[QUOTE=thundertoad]Checked out that link... no amd64 builds in the debian section.
Hey at least I am not the only one who didnt find that file.. it was freaking me out there for a second... well freaking me out is a tad melodramatic... it was more annoying me... like when you got water in your ears..

what the hell am I talking about... I need sleep

any other suggestions? any amd64 ports of p7zip? anyone at all?

Th'Undertoad[/QUOTE]
I took a bit of a look around and I think if you want to use it you will have to download the source and compile it yourself.

Get some sleep first...it might look like an appealling option in the morning and really isn't as hard as it sounds.

---

### Post by thundertoad on 2005-09-10
hmm... ok then I guess I better go teach myself how to compile stuff for AMD64. 
was trying to keep that till I get a little more familiar with the command line... but hey! have to learn sometime huh!

Mathew man, thanks for taking the time to look around, much obliged.

Th'undertoad

---

### Post by thundertoad on 2005-09-10
ok so I did some searching and I found this file:

p7zip_4.20-2_amd64.deb

so I tried to use alien to install it but it gives me the following errors

me@machinename:~ alien -i p7zip_4.20-2_amd64.deb
dpkg: dependency problems prevent configuration of p7zip:
 p7zip depends on libc6 (>= 2.3.5-1); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
 p7zip depends on libgcc1 (>= 1:4.0.1); however:
  Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.
 p7zip depends on libstdc++6 (>= 4.0.1); however:
  Package libstdc++6 is not installed.
dpkg: error processing p7zip (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 p7zip

so is this some strange repository problem... did I download an application meant for breezy badger or whatever the next distro version is gonna be?

cause I tried to update those packages and it just says that I have the latest... wuzz goin on hea? :neutral: 

Th'Undertoad

---

### Post by matthew on 2005-09-10
[QUOTE=thundertoad]so is this some strange repository problem... did I download an application meant for breezy badger or whatever the next distro version is gonna be?

cause I tried to update those packages and it just says that I have the latest... wuzz goin on hea? :neutral: 

Th'Undertoad[/QUOTE]

The version of p7zip you are trying to install needs a newer version of the 3 library files, just as you surmised. It's my wife's birthday and people will be arriving for her party in just a short while, so I can't do anything right now, but either late tonight (party ending time depending) or Monday I can look and see how hard/easy it would be for youto install/upgrade those. 

In the meanwhile, two suggestions: you can check and make sure you have all the repositories enabled by looking at the ubuntu guide (see my signature) and following the appropriate directions. If they are all enabled (including backports) then I would recommend looking for a slightly older version of p7zip and trying to use it...one that will be satisfied with the versions of the libraries you already have installed.

Hope it works!

---

### Post by thundertoad on 2005-09-10
[QUOTE=matthew]The version of p7zip you are trying to install needs a newer version of the 3 library files, just as you surmised. It's my wife's birthday and people will be arriving for her party in just a short while, so I can't do anything right now, but either late tonight (party ending time depending) or Monday I can look and see how hard/easy it would be for youto install/upgrade those. 

In the meanwhile, two suggestions: you can check and make sure you have all the repositories enabled by looking at the ubuntu guide (see my signature) and following the appropriate directions. If they are all enabled (including backports) then I would recommend looking for a slightly older version of p7zip and trying to use it...one that will be satisfied with the versions of the libraries you already have installed.

Hope it works![/QUOTE]
 HAPPY BIRTHDAY TO WIFEY!!!

And thanks mathew... thats a great suggestion... i'll go look for an older version of p7zip. That makes the most sense though dunno how successfull that will be.

Yeah I am up to date on my repositories (hehe sound so much like suppository.. I cant help but pause every single time I say it.. what can I say... always a kid at heart) I even have a few repos in there that arent on that guide.

I dunno.. i'll make a search for an earlier version and hope it works out.. Thanks for all the help and I wish you and the wife many more years of health and prosperity.

Regards,
Th'undertoad

---

### Post by matthew on 2005-09-11
I was able to check in for a minute tonight...thanks for the kind birthday wishes. We had a nice time with lots of extended family at the house. I'm too tired to think tonight so I'm heading to bed. I'll look in late tomorrow or on Monday and check on your progress. Hopefully you will have already found success.

---

### Post by thundertoad on 2005-09-11
Still looking... I'm big on extended family. Where I come from your family IS your extended family.. not the nuclear family. Glad you had fun. So far ... i've found a few ports for Debian... i'll include the links... but the supporting C library files that they had listed had issues when I tried to install them.

I tried downloading (did actually download) and try to install libc6 for debian... and basically got a conflict error so I had to abandon that path... there is a java applet that they had on the sf.net site... but its like 38 kb... dunno what its good for... maybe just creating lmza or whatever the compression method is called.

let me go hunt down those links quickly and post them:
( a minute passes )

[http://packages.debian.org/unstable/utils/p7zip](http://packages.debian.org/unstable/utils/p7zip)
here we go... I downloaded the AMD64 version... thats the 20-2 version that required these libs:

•  libc6 (>= 2.3.5-1) [not alpha, ia64]
    GNU C Library: Shared libraries and Timezone data
•  [dep] libc6.1 (>= 2.3.5-1) [alpha, ia64]
    GNU C Library: Shared libraries and Timezone data
•  [dep] libgcc1 (>= 1:4.0.1) [not hppa, m68k]
    GCC support library
•  [dep] libgcc2 (>= 4.0.1) [hppa, m68k]
    GCC support library
•  [dep] libstdc++6 (>= 4.0.1)
    The GNU Standard C++ Library v3
•  [dep] libunwind7 (>= 0.98.5-6) [ia64]
    A library to determine the call-chain of a program - runtime 

its listed under the unstable appz section... (yeay).
I actually contacted (or attempted) the guy who ported p7zip to Debian but so far no response...

So the libraries wont install and the main unstable app wont either... I looked for older versions...
again the sf.net site
[http://sourceforge.net/project/showfiles.php?group_id=111810](http://sourceforge.net/project/showfiles.php?group_id=111810)
cant find an AMD64 port... which means I gotta compile... phew....
I gotta get back to work. I'll check in later see if you saw something I didnt.

muchos gracias.
Th'undertoad

---

### Post by DJ_Max on 2005-09-11
[QUOTE=thundertoad]Still looking... I'm big on extended family. Where I come from your family IS your extended family.. not the nuclear family. Glad you had fun. So far ... i've found a few ports for Debian... i'll include the links... but the supporting C library files that they had listed had issues when I tried to install them.

I tried downloading (did actually download) and try to install libc6 for debian... and basically got a conflict error so I had to abandon that path... there is a java applet that they had on the sf.net site... but its like 38 kb... dunno what its good for... maybe just creating lmza or whatever the compression method is called.

let me go hunt down those links quickly and post them:
( a minute passes )

[http://packages.debian.org/unstable/utils/p7zip](http://packages.debian.org/unstable/utils/p7zip)
here we go... I downloaded the AMD64 version... thats the 20-2 version that required these libs:

•  libc6 (>= 2.3.5-1) [not alpha, ia64]
    GNU C Library: Shared libraries and Timezone data
•  [dep] libc6.1 (>= 2.3.5-1) [alpha, ia64]
    GNU C Library: Shared libraries and Timezone data
•  [dep] libgcc1 (>= 1:4.0.1) [not hppa, m68k]
    GCC support library
•  [dep] libgcc2 (>= 4.0.1) [hppa, m68k]
    GCC support library
•  [dep] libstdc++6 (>= 4.0.1)
    The GNU Standard C++ Library v3
•  [dep] libunwind7 (>= 0.98.5-6) [ia64]
    A library to determine the call-chain of a program - runtime 

its listed under the unstable appz section... (yeay).
I actually contacted (or attempted) the guy who ported p7zip to Debian but so far no response...

So the libraries wont install and the main unstable app wont either... I looked for older versions...
again the sf.net site
[http://sourceforge.net/project/showfiles.php?group_id=111810](http://sourceforge.net/project/showfiles.php?group_id=111810)
cant find an AMD64 port... which means I gotta compile... phew....
I gotta get back to work. I'll check in later see if you saw something I didnt.

muchos gracias.
Th'undertoad[/QUOTE]
 Well, you can't expect a package made for Debian to work on another operating system, in this case Ubuntu. Compiling it doesn't take much. You can even use checkinstall and make a simple .deb

---

### Post by thundertoad on 2005-09-11
Dj man... I dunno how to compile...and for that matter I dunno what to download to compile the file.. I am pure n00b... I am so n00b that I am currently readin Sam's teach yourself linux in 24 hours (more like 24 days) so I didnt know that debian appz wouldnt work on ubuntu... I mean I know ubuntu is based on debian... thats about all I know. I've been using linux for like 3 weeks straight... well not continiously... I try to learn as much as I can when I get back from work.

so what is checkinstall... and why is it that the files made for ubuntu are .deb files (I am guessing thats a debian extension) not .ubu or something. Although I know that breezy badger is gonna fix alot of this installation jitters I have... I still wanna learn. matter of fact I wont install breezy once its out... unless I know how to compile and install appz for ubuntu.

Man I hope my learning curve gets better.

Thundertoad

---

### Post by DJ_Max on 2005-09-11
I understand, I was in your situation a few years ago. Ubuntu is based on Debian, as it uses it's custom package format, where the packages end in .deb. Denoting a "Debian Package Format", it's similar to RPM. Also, Ubuntu follows some of the Debian standards and methods, where Debian does extensive testing for packages, and after a stable release, no longer release feature updates, just security patches, as does Ubuntu.

Even though Ubuntu is Debian based, Ubuntu has different package versions. So if I build a package on my Debian version, that has a specific version of libc, and you have a Ubuntu system, with a different version of libc, there will be problems, as I've build the package for my OS, and you're trying to use my package on your OS, with different libraries and such.
A package ending in .deb, which I've said, denotes a "Debian Format". Now, whoever created the package, which is called the maintainer, has to build it against a OS.

I really should write a tutorial, but I'll give you the jist of compiling, without boring you with C/C++ optimizations, and static/dynamic stuff.

Basically C/C++ programs, since they are low-level (meaning more CPU specific code), require you to "compile" on your computer, so that you will have a binary of it on your computer (your computer understands binary). You will of course, need a "compiler", the most popular, are gcc (for C), and g++ (for C++).
```
sudo apt-get install build-essential
```
Will install those tools.

Usually the commands are
```

./configure # Configuration of GNU make stuff
make # Build it
make install # Actually install it

```

This is not always the case, a quick look at p7zip, requires a little more. There's a README in the p7zip_4.20_src.tar.bz2 file. If you want, I could make a little BASH script to install it. Since this p7zip requires multiple "make", and has a install script afterwards.

---

### Post by thundertoad on 2005-09-12
Hey Thanks!!!

That makes sense ... yeah I took a look at the p7zip file ... I probably wont be able to figure it out at my level... 

oh on a side note... I tried vncing from my mac at work to my machine at home... GOD WAS IT SLOW... even at 256 colours it was torture.

so cant do much with that except maybe monitor downloads or something... useless.

DJ would be much obliged for either a script (say thankya) or a slightly more detailed compile tutorial (thankya big big).

I gotta get back to work... 
thanks for the mini tutorial

Th'undertoad
(no stephen kings were hurt in the making of this post)

---

### Post by matthew on 2005-09-12
Hey, just checking in. It looks like DJ_Max is helping out. Thanks, DJ! I was thinking of either doing a quick how to or script myself but I just got hammered at work so I won't be around as much for a few days.

 Just a quick word of encouragement--thundertoad, I know it's intimidating to think about compiling for yourself. With a little time and some expereince (like you are acquiring right now) you will learn how and you will have a great sense of accomplishment and pride in your growing skills. Hang in there.

---

### Post by thundertoad on 2005-09-12
[QUOTE=matthew]Hey, just checking in. It looks like DJ_Max is helping out. Thanks, DJ! I was thinking of either doing a quick how to or script myself but I just got hammered at work so I won't be around as much for a few days.

 Just a quick word of encouragement--thundertoad, I know it's intimidating to think about compiling for yourself. With a little time and some expereince (like you are acquiring right now) you will learn how and you will have a great sense of accomplishment and pride in your growing skills. Hang in there.[/QUOTE]
 Thanks Mathew... sorry about the work crunch... I just got through one myself ... I work in advertising... health care devision... medical companies run through bi-yearly or quarterly Cycles... and I just went through the wringer on the last one... we did great... me and my team... but man we got through some seriously impressive chunck of work.

You know what... I think I lucked out by choosing UBUNTU.. cause the people who use it are just awesome... I greatly appreciate your help and the patience you guys are showing with a n00b like moi.

If you guys are ok with it i'll keep asking y'all any questions that I can think of.

Th'undertoad

---

### Post by matthew on 2005-09-13
[QUOTE=thundertoad]You know what... I think I lucked out by choosing UBUNTU.. cause the people who use it are just awesome... I greatly appreciate your help and the patience you guys are showing with a n00b like moi.

If you guys are ok with it i'll keep asking y'all any questions that I can think of.[/QUOTE]
Hey. Just checking in for a couple of minutes. I think you will find this to be one of the most friendly of forums around. There are other places with a larger number of techno-wizards, but I haven't found many places nearly as welcoming. Feel free to ask any questions you have--take a look at the links in my sig as they will help you to post in a way that makes it *even more likely* you will receive a quick and helpful response.

Hopefully DJ will have time to get you set up with this problem soon. I'll check back when I can.

---

### Post by DJ_Max on 2005-09-14
School has been owning me for the past few days.

Anyhow, I've installed it on my iMac in OS X. The README file is very straightforward. Here's what you should do. After you decompress
```

cd /path/to/dir/
nano install.sh #Change DEST_HOME=/usr/local to DEST_HOME=/usr
cp makefile.linux_amd64 makefile.machine
make && make all
sudo ./install.sh

```

That should do it. For some reason, make SFX make 7Z wasn't arguments for me, though it may be for you. So be sure to read the readme.

BTW, thanks for the comments, I do what I can.  :-P

---

### Post by thundertoad on 2005-09-15
Very Nice!!... thanks man... I will give it a go once I get home from work... tell you how it works out.
ok... back to the grind..

incidently ... anyone know when breezy is comin out?.. the official release?

Th'undertoad

---

### Post by DRF on 2005-09-15
The release schedule for breezy is in the wiki. The address is:
[https://wiki.ubuntu.com/BreezyReleaseSchedule?highlight=%28Schedule%29](https://wiki.ubuntu.com/BreezyReleaseSchedule?highlight=%28Schedule%29)

With the final release being the 13th of October (if all goes well).

Compiling things aren't as hard as they sound. Most of the time it's just a matter of decompressing the file you download and then reading the readme to find out what commands you have to type at the prompt.

Daniel

---

### Post by thundertoad on 2005-09-15
thanks Dan... yeah problem with that package is that it didnt include any sort of info I can utilize. or at least as far as I can remember... finding it hard to type... accidently sliced my index finger on the left hand making a tuna salad.. learning to type with 9 finger... grrrr.

well cant blame anyone but myself really.
still a b!tch though

Th'undertoad
... still at work... its just one of those days

---

### Post by thundertoad on 2005-09-15
hey hey,
ok I got home and am typing with all 9 fingers...
which file did you use to install p7zip?

did you use this one:

p7zip_4.20-2_amd64.deb ?

ok now for some other qestions ... stupid and sad but necissary to figure out what you did:

cd /path/to/dir/
(place the downloaded p7zip file in a directory somewhere and cd into it)

nano install.sh #Change DEST_HOME=/usr/local to DEST_HOME=/usr
(open nano.. a text editor and open the file install.sh with it.. then... change a line in the install file from DEST_HOME=/use/local to DEST_HOME=/usr)

cp makefile.linux_amd64 makefile.machine
copy file somwhere and rename it something else?)

make && make all
(command to compile?)

sudo ./install.sh
(run the install file)

er... am I even close with this breakdown? 

DJ... I know you're busy with school and all so if you got time then I'd appreciate a break down... thanks)

Thundertoad

---

### Post by DRF on 2005-09-15
If you go to the p7zip project page on sourceforge ([http://sourceforge.net/projects/p7zip/](http://sourceforge.net/projects/p7zip/)) I found in there files section a download called:
p7zip_4.20_src.tar.bz2

I think (not having done this myself) that you probably want to download that one and decompress (you can probably use the default graphical app for this that appears when you double click in gnomes file manager).

Then if you run those commands that are described in the earlier posts you should hopefully get somewhere.

Your description of the commands is on the whole correct.
*cd /path/to/dir/* <- Will take to the location you extracted the downloaded file to. (prob have to write something like cd /home/username/p7zip_4.20_src/ obviously you should replace that with the correct location for your computer)

[i]nano install.sh #Change DEST_HOME=/usr/local to DEST_HOME=/usr
(open nano.. a text editor and open the file install.sh with it.. then... change a line in the install file from DEST_HOME=/use/local to DEST_HOME=/usr)[/i]

Unfortunatly it looks like it's default install values need to be changed (or at least thats what this instruction does). If your not used to nano you can replace the word nano with gedit for the graphical text editor (then make the same modifications save and quit the text editor. else your terminal prompt won't let you type the next command in while gedit is still running)

*cp makefile.linux_amd64 makefile.machine*

I'm not quite sure why you need to copy the file (which is what cp stands for) I'm guessing that the default install file is setup for 32bit not 64bit.

*make && make all*

make is the most common command you will come across when compiling downloaded programs. 'make' will run a script made by the programs creators compiling everything all at once (else you would end up having to compile every file individually).

*sudo ./install.sh*

This command could do all sorts of things but it probably moves a few files around and setups some config files. (a file ending in .sh is a script running commands though the terminal prompt, if your used to DOS it's like the .bat files)
The 'sudo' part of that tells the computer to run that command as administrator and by putting './' in front of the file tells the computer to run/execute that file.

Sorry if this is a bit vague (I've seen easier programs to compile, if your lucky you normally just have the 'make' command and './install' to run and don't have to edit any files).

Hope that helps even if it is a little technical/vague/complicated.

Daniel

---

### Post by DJ_Max on 2005-09-15
DRF pretty much nailed it.

You need to copy makefile.linux_amd64 to makefile.machine (as stated in the README), is because there's different compiling needed for each architecture & OS.

---

### Post by DJ_Max on 2005-09-15
Ok, I made this, and tested it on Ubuntu.

be sure to
```
chmod a+x p7zip-installer.sh
```. That way you can just ./p7zip-installer.sh to run.

[http://files.d-jacobs.com/p7zip-installer.sh](http://files.d-jacobs.com/p7zip-installer.sh)

---

### Post by thundertoad on 2005-09-15
[QUOTE=DJ_Max]Ok, I made this, and tested it on Ubuntu.

be sure to
```
chmod a+x p7zip-installer.sh
```. That way you can just ./p7zip-installer.sh to run.

[http://files.d-jacobs.com/p7zip-installer.sh](http://files.d-jacobs.com/p7zip-installer.sh)[/QUOTE]
 AMAZING!!! I have never seen an application getting compiled... it took like 4 minutes or something... man that script was wicked... worked like a charm.

DRF.. kudos brotha for the explination... I got the gist of it... but i'll reread the postes a few times and try to piece it together.

man... it works!!!.. I am uncompressing a 19 meg file.. and so far its reached 650 megs... thats some kinda compression... geez... hey since this thing is practically ported maybe you should contact tamir and and stick this up on his repository.

I'm sure a few more folk would love to get their hands on this.

much thanks... from the 9 fingered typing wonder.

Thundertoad

---

### Post by DJ_Max on 2005-09-15
Thats what I wanted to hear, makes me feel special. :-P It's a simple BASH script.

P7ZIP is a pretty small library, so it doesn't take very long to compile. Compilation times, also depend on your CPU make and architecture. For example, it takes about 1hour for me to install Wesnoth on my iMac. But I would imagine it doesn't take as long on an x86 machine.

Also, the different makefiles, as I've looked, are for C++ CPU optimizations and such.

Regards

---

### Post by matthew on 2005-09-15
Hey, guys,

I've been in and out a lot, looked in here occasionally but I haven't really had time for much more. It looks like things are getting back to normal now for me. I'm glad to see that you were able to help out DJ and that everything seems to have had a successful outcome.

BTW, I think wesnoth took about 30 minutes on my machine, give or take a few.

---

