---
title: "How I installed Adobe Reader 9.1 in Kubuntu Jaunty"
date: 2009-05-10
forum: x86 64-bit Users
---

### Post by dwightpaige79 on 2009-05-10
This is how I installed Adobe Reader 9.1 in Kubuntu 9.04 amd64:

1. You must remove any other installations of Adobe Reader/acroread ie. remove **_[SIZE="4"][COLOR="Blue"]completely[/COLOR][/SIZE]_** anything previously installed from Adobe Reader website or **_ANY repositories_**. To remove anything installed from repositories:

$ sudo aptitude purge acroread acroread-debian-files acroread-plugins acroread-escript mozilla-acroread acroread-l10n-en acroread-dictionary-en

This *MAY* be what is needed to remove any other installation of Adobe Reader [if someone who knows better would please inform?]:

$ sudo dpkg -P adobereader-enu

To remove previous paths to acroread plugin for firefox/mozilla:

$ sudo rm -rf /usr/lib64/firefox/plugins/nppdf.so && sudo rm -rf /usr/lib/firefox/plugins/nppdf.so && sudo rm -rf /usr/lib64/mozilla/plugins/nppdf.so && sudo rm -rf /usr/lib/mozilla/plugins/nppdf.so

$ sudo rm -rf /usr/lib64/firefox/plugins/npwrapper.nppdf.so && sudo rm -rf /usr/lib/firefox/plugins/npwrapper.nppdf.so && sudo rm -rf /usr/lib64/mozilla/plugins/npwrapper.nppdf.so && sudo rm -rf /usr/lib/mozilla/plugins/npwrapper.nppdf.so

1. Install package getlibs following instructions here:

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

2. $ sudo dpkg -i getlibs-all.deb

3. Get the latest .deb package from Adobe then cd to <directory_where you_downloaded_Adobe_Reader.deb-package> and install [in my case]:

$ cd /home/dwight/Download

$ sudo dpkg -i --force-all AdbeRdr9.1.0-1_i386linux_enu.deb

4. $ sudo getlibs /usr/bin/acroread
select 'Y' and it installs the needed dependencies [in my case 7 packages]. 

Open the application in my case in KDE >Kmenu>Applications>Office and open Adobe Reader 9.1 and accept license. 

Then if you wish to install browser plug-in for Firefox:

6. $ sudo aptitude install nspluginwrapper

7. $ sudo nspluginwrapper -i /opt/Adobe/Reader9/Browser/intellinux/nppdf.so

To test browser plug-in in Firefox restart Firefox then go to >Tools>Add-ons>Plugins or type 'about:plugins' in url line and check and see if Adobe Reader plug in is installed. If it is installed Google or Scroogle 'pdf test' and select a few links to test your newly installed Adobe Reader plug in.

Note: In packages 'acroread-l10n-en acroread-dictionary-en' '-en' is for English language packages. Substitute what ever is correct for your language.

Edit May 15, 2009 to make more Ubuntu/Kubuntu centric. If anyone sees anything that needs correction or could be improved please inform. I'm not close to an Ubuntu/Kubuntu expert... Also *NOTE* I use aptitude as a matter of habit/preference. I *BELIEVE* using apt-get should work also.

---

### Post by BryanFRitt on 2009-05-11
In trying this, when I type
*getlibs /usr/bin/acroread*
I get
[FONT="Courier New"]getlibs /usr/bin/acroread
Cannot determine the dependencies required by this program, it may be a script:
If this program needs a 32-bit library use:
getlibs -l i386librarytoinstall.so
If this program needs a 64-bit library use:
getlibs -64l amd64librarytoinstall.so[/FONT]
If I try 
*getlibs -l /usr/bin/acroread*
I get
[FONT="Courier New"]No match for acroread
No packages to install[/FONT]
I also get the 1st error message when I try the command with 
*sudo*
, and with 
*-64l*
I get
[FONT="Courier New"]getopt: unrecognized option `-64l'[/FONT]
...
I also tried 
*sudo getlibs -w [http://ardownload.adobe.com/pub/adobe/reader/unix/9.x/9.1/enu/AdbeRdr9.1.0-1_i386linux_enu.deb](http://ardownload.adobe.com/pub/adobe/reader/unix/9.x/9.1/enu/AdbeRdr9.1.0-1_i386linux_enu.deb)*
which gave me
[FONT="Courier New"]Downloading ...
Installing libraries ...[/FONT]
and that still didn't change anything.

Now what do I do?

p.s.
*sudo* maybe required by
[I]aptitude purge acroread acroread-debian-files acroread-plugins acroread-escript mozilla-acroread acroread-l10n-en acroread-dictionary-en
rm -rf /usr/lib64/firefox/plugins/nppdf.so
rm -rf /usr/lib/firefox/plugins/nppdf.so
rm -rf /usr/lib64/mozilla/plugins/nppdf.so
rm -rf /usr/lib/mozilla/plugins/nppdf.so
dpkg -i --force-all AdbeRdr9.1.0-1_i386linux_enu.deb[/I]
So that you would get
[I]sudo aptitude purge acroread acroread-debian-files acroread-plugins acroread-escript mozilla-acroread acroread-l10n-en acroread-dictionary-en
sudo rm -rf /usr/lib64/firefox/plugins/nppdf.so
sudo rm -rf /usr/lib/firefox/plugins/nppdf.so
sudo rm -rf /usr/lib64/mozilla/plugins/nppdf.so
sudo rm -rf /usr/lib/mozilla/plugins/nppdf.so
sudo dpkg -i --force-all AdbeRdr9.1.0-1_i386linux_enu.deb[/I]

p.s.2.
I'm on KUbuntu 8.04 64 bit, Hardy, and I had?/have? a compiled version in
*/opt/Adobe/Reader9/*

*which acroread*
[FONT="Courier New"]/usr/bin/acroread[/FONT]

*ls -alF /usr/bin/acroread*
[FONT="Courier New"]lrwxrwxrwx 1 root root 31 2009-05-11 15:11 /usr/bin/acroread -> /opt/Adobe/Reader9/bin/acroread[/FONT]

*ls -alF /opt/Adobe/Reader9/bin/acroread*
[FONT="Courier New"]-rwxr-xr-x 1 10490 floppy 16900 2009-02-27 19:14 /opt/Adobe/Reader9/bin/acroread*[/FONT]

---

### Post by BryanFRitt on 2009-05-11
Now I've really screwed things up...
[http://ubuntuforums.org/showthread.php?p=7260770#14](http://ubuntuforums.org/showthread.php?p=7260770#14)
I've got a feeling Adobe Acrobat Reader will never be installed on my system now.

Update:
*sudo dpkg -P adobereader-enu*
fixed so I can install Acrobat again, still the same error on running though

*acroread*
[FONT="Courier New"]terminate called after throwing an instance of 'ASErrException'
Aborted[/FONT]

I did try this, looks like it could have done something, but the same error still occurs

---

### Post by BryanFRitt on 2009-05-12
Here's something new, _still doesn't fix the problem_, but looks like it could have done something.

Note: the ***-l64*** and ***-l32*** is not what the message says to use ***-64l***, and ***-l***, they don't match like it's supposed to, and the *-l* option still does nothing.

*getlibs **-l64** /usr/bin/acroread*
[FONT="Courier New"]64: wims-extra-all
No match for acroread
The following i386 packages will be installed:
wims-extra-all
Continue [Y/n]?[/FONT] *n*

*getlibs **-l32** /usr/bin/acroread*
[FONT="Courier New"]32: startalk
No match for acroread
The following i386 packages will be installed:
startalk
Continue [Y/n]?[/FONT] *Y*
[FONT="Courier New"]Downloading ...
Installing libraries ...[/FONT]

The same thing will happen if I replace
*/usr/bin/acroread*
with
*/opt/Adobe/Reader9/bin/acroread*
even though there isn't a file there anymore.
It'll even do the above even if I leave it as 
*getlibs -l32*
or
*getlibs -l64*
.
It will do this every time, even if it's done this before.

*getlibs /opt/Adobe/Reader9/Reader/intellinux/bin/**
or 
*getlibs /opt/Adobe/Reader9/Reader/intellinux/bin/acroread*
(maybe others?)
produce:
[FONT="Courier New"]No match for libBIB.so
No match for libBIBUtils.so
libACE.so: libace-dev
No match for libAGM.so
No match for libCoolType.so
No match for libAXE8SharedExpat.so
No match for libJP2K.so
No match for libAdobeXMP.so
No match for libicuuc.so.36
No match for libResAccess.so
The following i386 packages will be installed:
libace-dev
Continue [Y/n]?[/FONT] *Y*
[FONT="Courier New"]Downloading ...
Installing libraries ...[/FONT]

Again, It will do this every time, even if it's done this before.

I not sure what's going on. If I look for the names of the ones it said it tried to install using Adept, it says none of them are installed. For those three it says install 22, download 99M, and installation 439M.

in 
*/opt/Adobe/Reader9/Reader/intellinux/bin*
*getlibs ./acroread*
[FONT="Courier New"]No match for libBIB.so
No match for libBIBUtils.so
libACE.so: libace-dev
No match for libAGM.so
No match for libCoolType.so
No match for libAXE8SharedExpat.so
No match for libJP2K.so
No match for libAdobeXMP.so
No match for libicuuc.so.36
No match for libResAccess.so
The following i386 packages will be installed:
libace-dev
Continue [Y/n]?[/FONT] *Y*
[FONT="Courier New"]Downloading ...
Installing libraries ...[/FONT]

Now, when I run
*sudo /opt/Adobe/Reader9/Reader/intellinux/bin/acroread*
I get
[FONT="Courier New"]/opt/Adobe/Reader9/Reader/intellinux/bin/acroread: error while loading shared libraries: libBIB.so: cannot open shared object file: No such file or directory[/FONT]

Any ideas on what to do next?

---

### Post by portis on 2009-05-12
It's been packaged in debian multimedia repo,
[http://debian-multimedia.org/](http://debian-multimedia.org/)
All you have to do is add this repo, and apt-get install.

---

### Post by dwightpaige79 on 2009-05-15
> **BryanFRitt said:**
> 

p.s.
*sudo* maybe required by
[I]aptitude purge acroread acroread-debian-files acroread-plugins acroread-escript mozilla-acroread acroread-l10n-en acroread-dictionary-en
rm -rf /usr/lib64/firefox/plugins/nppdf.so
rm -rf /usr/lib/firefox/plugins/nppdf.so
rm -rf /usr/lib64/mozilla/plugins/nppdf.so
rm -rf /usr/lib/mozilla/plugins/nppdf.so
dpkg -i --force-all AdbeRdr9.1.0-1_i386linux_enu.deb[/I]
So that you would get
[I]sudo aptitude purge acroread acroread-debian-files acroread-plugins acroread-escript mozilla-acroread acroread-l10n-en acroread-dictionary-en
sudo rm -rf /usr/lib64/firefox/plugins/nppdf.so
sudo rm -rf /usr/lib/firefox/plugins/nppdf.so
sudo rm -rf /usr/lib64/mozilla/plugins/nppdf.so
sudo rm -rf /usr/lib/mozilla/plugins/nppdf.so
sudo dpkg -i --force-all AdbeRdr9.1.0-1_i386linux_enu.deb[/I]

Apologies. And well yes if you use sudo. I'm primarily an openSUSE/Mandriva user so I find it more convenient to use 'sudo -i' to change completely to superuser/root [the equivalent of 'su -' in other distros]. And the # signs do indicate that the commands are run as root/superuser. I shall attempt to use proper Ubuntu form in future posts. Unless of course this old brain forgets... And I will edit my original post to, hopefully, make it easier for Ubuntu/Kubuntu users to use.

---

### Post by dwightpaige79 on 2009-05-15
> **portis said:**
> It's been packaged in debian multimedia repo,
[http://debian-multimedia.org/](http://debian-multimedia.org/)
All you have to do is add this repo, and apt-get install.

Indeed it is. Adobe Reader 9.1  packages for amd64 are here:

[http://debian-multimedia.org/dists/testing/main/binary-amd64/package/acroread.php](http://debian-multimedia.org/dists/testing/main/binary-amd64/package/acroread.php)

I'll have to study on that. Should be much easier to add the proper repo and install using 'aptitude' or 'apt-get' than what I demonstrate in my how to. Is installing the debian-multimedia.org repos in Ubuntu or Kubuntu documentation? If so I I've missed it so far... But that's very possible...

---

### Post by dwightpaige79 on 2009-05-15
> **BryanFRitt said:**
> Here's something new, _still doesn't fix the problem_, but looks like it could have done something.

Unfortunately no at this time. Still looking though. Also I'm wondering if I should have posted an attempt at a how to anyway. Because:

1. I'm not very experienced or knowledgeable with Ubuntu/Kubuntu at this point.

2. I have a very limited amount of time to deal with this stuff and haven't been able to help others solve problems as much as I would like.

3. And very importantly there may be a better way to install Adobe Reader anyway. Possibly by installing 'debian-multimedia.org' repos.

One suggestion would be a fresh install of Ubuntu or which ever flavor you have. Mine is Kubuntu. Don't know if that's possible in your situation. Sorry for not having better answers. Yet.

---

### Post by ken78724 on 2009-05-15
> **portis said:**
> It's been packaged in debian multimedia repo,
[http://debian-multimedia.org/](http://debian-multimedia.org/)
All you have to do is add this repo, and apt-get install.

So, for short is this "the shortcut method for installing Adobe 9.1." I've used the .pdf reader found in jaunty 9.04 w/o difficulty but may wish to do this install if I see the necessity.

Many thanks for the hard work on each one's part!  

Kenneth Koym;)

---

### Post by brodiepearce on 2009-06-05
Thank you for posting this up!  

I've just used this on a plain Ubuntu installation to stop myself from tearing out my hair.  Just about every time I reinstall Ubuntu I run into the issue sooner or later where Firefox will not embed PDFs regardless of whatever arrangement of firefox and acroread I use.  :D

---

### Post by marianlibrarian on 2009-07-27
I read these threads and it seems that there is a way to 
sudo apt-get install .....

but what do you call it? No one mentions the name of the thing you want to install. 

The reader that comes with kubuntu hardy heron doesn't quite work for us. and nothing in the add / remove programs has the word adobe in the list.

We need the real adobe reader.

---

### Post by philinux on 2009-07-27
> **marianlibrarian said:**
> I read these threads and it seems that there is a way to 
sudo apt-get install .....

but what do you call it? No one mentions the name of the thing you want to install. 

The reader that comes with kubuntu hardy heron doesn't quite work for us. and nothing in the add / remove programs has the word adobe in the list.

We need the real adobe reader.

1. enable medibuntu - link below.
2. sudo apt-get install acroread

---

### Post by GroovyBear on 2009-08-10
> **ken78724 said:**
> So, for short is this "the shortcut method for installing Adobe 9.1." I've used the .pdf reader found in jaunty 9.04 w/o difficulty but may wish to do this install if I see the necessity.

Many thanks for the hard work on each one's part!  

Kenneth Koym;)
Umm, guys I think acroread isn't avaliable in medibuntu right now. I checked it out today in

[http://packages.medibuntu.org/jaunty/index.html](http://packages.medibuntu.org/jaunty/index.html)

Anyone knows why?

---

### Post by Cresho on 2009-08-12
ya this post is old.  medibuntu has the acroread stuff but hidden.  look for these and they work fine in hardy and jaunty.  download these

acroread_8.1.2-0medibuntu6_amd64.deb
acroread-escript_8.1.2-0medibuntu6_amd64.deb
acroread-plugins_8.1.2-0medibuntu6_amd64.deb
mozilla-acroread_8.1.2-0medibuntu6_amd64.deb

google em and install them in this order.  reboot so firefox can see them.  The first time i installed them, acroread did not work in firefox.  so i closed firefox looking for an answer.  after dinner i came back and i accidently opened up something and the pdf opened in firefox in jaunty jackalope.  it works.  also flash 10 works for those who are un aware.  if you look for these debs, you will find also the ones for 32 bit and also other versions of ubuntu.  these work on a 64bit ubuntu jaunty jackalope.  i guess it didnt work the first time since i am assuming firefox must of been still running in the background so i recommend a reboot.

---

### Post by Chemical Imbalance on 2009-08-12
> **brodiepearce said:**
> Thank you for posting this up!  

I've just used this on a plain Ubuntu installation to stop myself from tearing out my hair.  Just about every time I reinstall Ubuntu I run into the issue sooner or later where Firefox will not embed PDFs regardless of whatever arrangement of firefox and acroread I use.  :D

Give **Mozplugger** a try (in the repos).

No need for that bloated, exploit-loaded Adobe Reader/Acrobat (more like Acrofat, how big does a pdf reader need to be)?

---

### Post by jahLux on 2009-10-04
> **ken78724 said:**
> So, for short is this "the shortcut method for installing Adobe 9.1." I've used the .pdf reader found in jaunty 9.04 w/o difficulty but may wish to do this install if I see the necessity.

Many thanks for the hard work on each one's part!  

Kenneth Koym;)

I have just used this method to install Acrobat Reader 9.1 on my 64-bit Karmic Koala - which by the way was successfully and flawlessly upgraded last night from Jaunty Jackalope.
This is indeed a massive statement of the maturity of UBUNTU.
Thanks to all the Developers and of course this Forum community as well.
Rock-on !!

---

