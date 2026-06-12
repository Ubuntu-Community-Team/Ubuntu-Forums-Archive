---
title: "Open office 3 deb for 64 bit - other operating systems"
date: 2008-09-22
forum: x86 64-bit Users
---

### Post by lonniehenry on 2008-09-22
The deb link for the openoffice3 release candidate version2 works for the 32 bit but if you need other versions (for 64 bit for example) you need the following link: [ftp://ftp.ussg.iu.edu/pub/openoffice...b/rc/3.0.0rc2/](ftp://ftp.ussg.iu.edu/pub/openoffice...b/rc/3.0.0rc2/) to get your version. Then follow the instructions in the following link: [http://tombuntu.com/index.php/2008/0...e-candidate-1/](http://tombuntu.com/index.php/2008/0...e-candidate-1/) (the link in the instructions is broken.)

You will have to change the version numbers in the terminal command to match the version of the deb you downloaded. It works so faster than the 2.4 version of oo and so far I haven't run into any problems.

---

### Post by Sef on 2008-09-23
Moved to x86 forums.

---

### Post by lonniehenry on 2008-09-23
Thanks for moving this.  I had posted in the intrepid area as that is where the discussion about the OO3 being included was going on.  I hope the intrepid testers think to look in the regular forums as sometimes the  wheel doesn't need reinventing.

---

### Post by zorkerz on 2008-10-14
can't seem to find an amd64 bit version of openoffice 3 right now
its a bummer

---

### Post by vikramsharma on 2008-10-14
Try this link [ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/](ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/) I could find the 64 bit version.  Hope this helps.

---

### Post by istblacken on 2008-10-14
-get the 64 bit openoffice.org from the download site [ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz](ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz)
-extract the contents of the compressed archive to desktop
-in the terminal "cd" to the desktop
-then write 
```
sudo dpkg --install --recursive ./DEBS

``` in the terminal
-before doing all this, first make sure you unistall anything related to openoffice.org 2.4.1
i did this in my system and now i am using openoffice.org 3.0 with no problem.

---

### Post by zorkerz on 2008-10-14
Thanks for all the replies. Its odd that a amd64 deb packages is not on the main site right now. Though I guess they have other issues to worrie about. They do have a link to an amd64 torrent file though which is what I ended up using. 

Just FYI you do not need to uninstall 2.4. If you don't you will have to start ooo3 with ```
/opt/openoffice.org3/program/soffice
```
you would also then need to add it to your menu if you desire.

---

### Post by fballem on 2008-10-14
> **zorkerz said:**
> Thanks for all the replies. Its odd that a amd64 deb packages is not on the main site right now. Though I guess they have other issues to worrie about. They do have a link to an amd64 torrent file though which is what I ended up using. 

Just FYI you do not need to uninstall 2.4. If you don't you will have to start ooo3 with ```
/opt/openoffice.org3/program/soffice
```
you would also then need to add it to your menu if you desire.

The advantage to uninstalling 2.4 first is that Open Office will be added directly to your menus as part of the installation process. As well, using the recursive install process mentioned in a prior post will result in a conflict - the menus won't install.

By the way, I don't know if anyone else has noticed, but after the installation is complete, the Open Office 3 items do show up in Synaptic. Not sure what that means - I'm relatively new to Linux/ubuntu.

---

### Post by zorkerz on 2008-10-14
If you do not want OOO2.4 around any more you are right you should uninstall it first because that allows the menus to be added automatically rather than doing it manually as I mentioned above.

Any package you install will show up in synaptic in the "installed (local or obsolete)" section. This is part of the beauty of the package management system, that it can keep track of all of your installed applications even ones you installed manually.

I don't know if this applies to things installed from source however.

---

### Post by David Valentine on 2008-10-14
> **zorkerz said:**
> If you do not want OOO2.4 around any more you are right you should uninstall it first because that allows the menus to be added automatically rather than doing it manually as I mentioned above.That didn't work for me installing the 64-bit version of Ooo3 on Hardy, even though I had removed Ooo2.4.  Is there a way to use the /opt/openoffice.org3/xdg files for this?  
[update]
Oops, the answer is to go into the "DEBS/Desktop-integration" directory and sudo dpkg -i its .deb file.

---

### Post by lduperval on 2008-10-14
Guess I'll wait for an official release. I tried the DEBs and I get all sorts of crashes.

L

---

### Post by PatrickMoore on 2008-10-14
i cant find a stable release for 64 bit are the servers overwhelmed???

---

### Post by John Jason Jordan on 2008-10-14
> **lduperval said:**
> Guess I'll wait for an official release. I tried the DEBs and I get all sorts of crashes.
I've been told in another thread here that 3.0 will be in the backports. It's not there yet, however. Nevertheless, I am not going to install 3.0 yet. Frankly, there is little in it of benefit to me. It still doesn't recognize OpenType fonts, for example. 

I think I'll wait until Intrepid and hope that Intrepid manages to include 3.0. I have data in autocorrect entries and dictionaries that would take a hundred hours to redo manually, if it is even possible to do so at all. I need to wait until there are enough responses from people who upgrade to ensure that such things will be transferred to 3.0.

---

### Post by menothim on 2008-10-14
istblacken, thanks it has worked perfect

---

### Post by zorkerz on 2008-10-15
> **PatrickMoore said:**
> i cant find a stable release for 64 bit are the servers overwhelmed???

The openoffice.org home page is overwhelmed and has been for over a day now. As you can see they only provide some download links strangly non of which appear to be amd64 packages. The very first link on the page, however, provides you with torrent files. There is an amd64 torrent file. I would recommend downloading by bittorrent as well because the OOO3 servers and mirrors are under high load and will be slow whereas bittorrent only gets faster as more people use it.

John Jason Jordan: OOO3 is not in intrepid and I do not believe it will be because it came out to close to the final release and they have not been using a release candidate as they did with firefox3.  It will likely/hopefully make it into the intrepid backports as you say.

---

### Post by kford on 2008-10-15
Good instructions.  I used this helpful blog [post]("http://www.tectonic.co.za/?p=3363").  It's similar, but slightly different.  

After removing Oo2, Oo3 installed without a hitch, complete with menu links (I'm on Kubuntu, but it will work for Ubuntu, naturally).  

Of course, this is all predicated on finding the AMD64 debs.  I got mine from [here]("http://gulus.usherbrooke.ca/pub/appl/openoffice/stable/3.0.0/").

---

### Post by stchman on 2008-10-20
I was doing a little looking around and apparently the ftp site that OO uses ftp.spnet.net also has the 64 bit version ready to go.

[ftp://ftp.spnet.net/openoffice/stable/3.0.0/](ftp://ftp.spnet.net/openoffice/stable/3.0.0/)

The DEB x86-64 is there, just click on it.

---

### Post by edrace562 on 2008-10-22
works great!  thank you!:)

---

### Post by agathian on 2008-10-23
will 3.0 be officially released for hardy?

thanks!

---

### Post by Yellow Pasque on 2008-10-23
> **agathian said:**
> will 3.0 be officially released for hardy?

thanks!
Probably not for Hardy and including it in Intrepid is still up in the air depending on how soon the OOo devs get the rc out.
> From Chris Cheney, the OOo developer-maintainer for ubuntu: If the RC1 release doesn't slip too much we will upload it into Intrepid. Please see: [http://wiki.ubuntu.com/OOo30Schedule](http://wiki.ubuntu.com/OOo30Schedule)

---

### Post by zorkerz on 2008-10-23
Wait a minute maybe i have misread this. The final release of open office 3 is already out, you can download it at their website. Considering that the release of intrepid is due in 7 days and openoffice 3 has not yet made it into the intrepid repositories, i think it extremely unlikely openoffice 3 will make it into intrepid. Hardy has already been released openoffice 3 will not make it into hard. 

There is another option. Both hardy and intrepid have a backports repository. I think it pretty likely that openoffice 3 makes it into intrepid's backports and also possibly hardy's.

---

### Post by MaindotC on 2008-10-26
I downloaded the deb and I'm having problems installing:
```

amd64@amd64-desktop:~/OOO300_m9_native_packed-1_en-US.9358/DEBS$ sudo dpkg -i ooobasis3.0-core06_3.0.0-9_amd64.deb 
(Reading database ... 161311 files and directories currently installed.)
Unpacking ooobasis3.0-core06 (from ooobasis3.0-core06_3.0.0-9_amd64.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing ooobasis3.0-core06_3.0.0-9_amd64.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./opt/openoffice.org/basis3.0/share/gallery/sg3.sdg')
Errors were encountered while processing:
 ooobasis3.0-core06_3.0.0-9_amd64.deb
amd64@amd64-desktop:~/OOO300_m9_native_packed-1_en-US.9358/DEBS$

```

What does this mean?

---

### Post by blakzer0 on 2008-10-26
If anyone is having any issues try this link from the main website:
[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxx86-64deb&lang=en-US&version=3.0.0](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxx86-64deb&lang=en-US&version=3.0.0)

I didn't find a version on the download page for 64bit so I just changed the URL and it directed me to the right version. I hope this helps for all the 64 bit users out there. This should also provide a proper mirror.

To install just extract the tar.gz then open a console and cd to the DEBS directory. After that just:
```
sudo dpkg -i *.deb
```

Then remove the old open office and cd to the Desktop Intergration and install that package using:
```
sudo dpkg -i *.deb
```

---

### Post by MaindotC on 2008-10-26
I keep getting the following:
```

amd64@amd64-desktop:~$ tar xvf OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz 
OOO300_m9_native_packed-1_en-US.9358/
OOO300_m9_native_packed-1_en-US.9358/DEBS/
OOO300_m9_native_packed-1_en-US.9358/DEBS/ooobasis3.0-core06_3.0.0-9_amd64.deb

gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

```

When I cd into the directory there's only 1 deb and it doesn't install - same output as I posted earlier.

---

### Post by Calida on 2008-10-27
I would recommend to redownload the file, i think something went wrong there, but that is just a guess comming from the unexpected end of file thing.

---

### Post by MaindotC on 2008-10-27
Re-downloaded it three times now, same result :(  What is my  majour malfunction?

---

### Post by mjwood0 on 2008-10-27
Works great for me.

I found the download here: [ftp://ftp.spnet.net/openoffice/stable/3.0.0/](ftp://ftp.spnet.net/openoffice/stable/3.0.0/)

Be sure to not only install all the debs in the DEBS folder, but also the desktop integration deb located in DEBS/desktop-integration.

---

### Post by John Jason Jordan on 2008-10-27
> **mjwood0 said:**
> Works great for me.
Be sure to not only install all the debs in the DEBS folder, but also the desktop integration deb located in DEBS/desktop-integration.
If you are going to leave 2.4.1 installed, then do not install the desktop integration deb file. That's why it's in a separate folder - so you can just navigate to the folder with the rest of the debs and give a dpkg -i *.deb command.

---

### Post by MaindotC on 2008-10-27
> **strAlan said:**
> Re-downloaded it three times now, same result :(  What is my  majour malfunction?

There did seem to be an issue in the uncompressing of the file.  I downloaded from the link specified in the above post and unpacked it to find many .deb's.  I installed them, then tried to install the desktop-integration deb but it conflicted with openoffice.org-core.  Holding my breath, I uninstalled openoffice.org-core, updatedb, and then installed the desktop-integration.deb.  It was success, and I started Writer and opened a recent document.  Thanks for all your help.

---

### Post by jp_coll2003 on 2008-10-28
I found this little gem which I found a lot easier. I am now using Ibex and I  wanted to upgrade to version 3 of Open Office as I always save as PDF and like the new option of importing PDF files.

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by Zarafet on 2008-10-30
> **istblacken said:**
> -get the 64 bit openoffice.org from the download site [ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz](ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz)
-extract the contents of the compressed archive to desktop
-in the terminal "cd" to the desktop
-then write 
```
sudo dpkg --install --recursive ./DEBS

``` in the terminal
-before doing all this, first make sure you unistall anything related to openoffice.org 2.4.1
i did this in my system and now i am using openoffice.org 3.0 with no problem.

[COLOR="Red"]WOW, this worked. Thank you so much for this. I have been trying to install Open Office 3 since it's release date, and have been ONLY getting error after error. 

For those of you who dont understand these directions, you need to type in the terminal sudo dpkg --install --recursive ./(here is where you put the name of the folder that was extracted to your desktop)

Again, thank you!!![/COLOR]

---

### Post by OldTimeTech on 2008-11-07
Finally after downloading the wrong package, downloaded the right package, followed instructions and I now have Openoffice 3....YES!!!!

Thanks to All!!!

---

### Post by PatrickMoore on 2008-11-08
following the directions on this post i cannot install i am getting this error

```
sudo dpkg --install --recursive ./DEBS
[sudo] password for patrick: 
find: `./DEBS': No such file or directory
dpkg: find for --recursive returned unhandled error -1

```

anyone else with this issue

---

### Post by 73ckn797 on 2008-11-08
> **PatrickMoore said:**
> following the directions on this post i cannot install i am getting this error

```
sudo dpkg --install --recursive ./DEBS
[sudo] password for patrick: 
find: `./DEBS': No such file or directory
dpkg: find for --recursive returned unhandled error -1

```anyone else with this issue

Look at this link for my solution. If you are using the 64 bit the download location may be different though it seems you already have the package. Just substitute any file name differences.

[http://ubuntuforums.org/showthread.php?p=6090196#post6090196](http://ubuntuforums.org/showthread.php?p=6090196#post6090196)

---

### Post by zika on 2008-11-27
Yesterday I've been usin OpenOfifice happily.

Today I've found today that my OpenOffice is missing from menu and that it won't open files anymore. I have upgraded openoffice to 3.0 from the one that came with Ibex (2.*) some time ago via:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
sudo apt-get update
sudo apt-get dist-upgrade


i've tried to do sudo apt-get install opennoffice.org but that gave me:
 
when I go through directories the files are there but how to re-activate them. When I click on OOfile (like .odt) openoffice is not mentioned. It all worked yesterday ... :(

sudo apt-get install openoffice.org
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openoffice.org: Depends: openoffice.org-writer but it is not going to be installed
                  Depends: openoffice.org-calc but it is not going to be installed
                  Depends: openoffice.org-impress but it is not going to be installed
                  Depends: openoffice.org-draw but it is not going to be installed
                  Depends: openoffice.org-math but it is not going to be installed
                  Depends: openoffice.org-base but it is not going to be installed
                  Depends: openoffice.org-report-builder-bin but it is not going to be installed
E: Broken packages

Is there any help?

I've tried just a minute ago to reinstall it using [ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz](ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz) and everything went well except menus could not be installed. But, the situation is the same, I can not start OpenOffice.

Where are the files that start writer etc?

---

### Post by zika on 2008-11-27
I've just checked and the same thing happened on the other machine on my LAN. They are totally independent, this second one was not ON until yesterday whei it was just updated ... maybe the updates are to blame?

---

### Post by zika on 2008-11-27
I think I know what happened: after update Cruft Remover suggested to delete uno-libs3 package. So I did. It seems that it is needed for OO3.0.

Any ideas how to undo that operation?

Should I reinstall (before uninstalling all of OO2.* originally from Ibex)?

---

### Post by whistlerspa on 2008-12-18
I've tried all of this and it just isn't working on my system. I keep having to reove the entire installation as 'broken packages'. Back to version 2.4.1 I guess.

---

### Post by zika on 2008-12-18
> **whistlerspa said:**
> I've tried all of this and it just isn't working on my system. I keep having to reove the entire installation as 'broken packages'. Back to version 2.4.1 I guess.

take a look at the thread [http://ubuntuforums.org/showthread.php?p=6377894](http://ubuntuforums.org/showthread.php?p=6377894) where we did find a solution, also in [http://ubuntuforums.org/showthread.php?p=6390179](http://ubuntuforums.org/showthread.php?p=6390179).

---

### Post by John Jason Jordan on 2008-12-18
> **whistlerspa said:**
> I've tried all of this and it just isn't working on my system. I keep having to reove the entire installation as 'broken packages'. Back to version 2.4.1 I guess.

First, here is a link to instructions for installing OOo 3.0 on Hardy. The instructions are the same for Intrepid.

[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04]("http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04")

Second, if you are installing on Ubuntu x86_64 make sure you download the 64-bit tar file.

Third, you can install 3.0 *in addition to* 2.4.1 - that is, have both installed. But to do so make sure you do *not* install the desktop integration deb file. Or you can install them all (using the --recursive option mentioned by others in this thread), which will cause an upgrade of your 2.4.1. Afterwards you will have only 3.0.

Fourth, all of your settings for 2.4.1 (entries added to your dictionary, personal autocorrect entries, toolbar locations and items on them, and a ton of other stuff) will be migrated to 3.0 when you launch it for the first time. That is, there is an option migrate and you can tell it no if you don't want your old configurations used by 3.0.

---

### Post by BLTicklemonster on 2009-02-03
> **zika said:**
> take a look at the thread [http://ubuntuforums.org/showthread.php?p=6377894](http://ubuntuforums.org/showthread.php?p=6377894) where we did find a solution, also in [http://ubuntuforums.org/showthread.php?p=6390179](http://ubuntuforums.org/showthread.php?p=6390179).

Thank you, that worked great for me!

---

### Post by Weidbrewer on 2009-09-02
> **Zarafet said:**
> [COLOR="Red"]WOW, this worked. Thank you so much for this. I have been trying to install Open Office 3 since it's release date, and have been ONLY getting error after error. 

For those of you who dont understand these directions, you need to type in the terminal sudo dpkg --install --recursive ./(here is where you put the name of the folder that was extracted to your desktop)

Again, thank you!!![/COLOR]

Hey, are these instructions still the best way to go, or have things been fixed to the point where it's now good to go in the repos?

---

### Post by John Jason Jordan on 2009-09-02
> **Weidbrewer said:**
> Hey, are these instructions still the best way to go, or have things been fixed to the point where it's now good to go in the repos?

The version in the repos for Jaunty is 3.0.1. The latest and greatest version 3.1.0, but to get it you have to download it from OOo and install it manually. 

But be careful, because there are things that Ubuntu does to the version in the repository to make it work better with Ubuntu, plus Ubuntu uses the GoOO version instead of the official version. The GoOO version is modified by some group (I forget who). 

Sometimes the Ubuntuized version will have differences, although usually trivial. For example, when I had 3.0.1 from OOo on Intrepid I noticed that right after saving a document the File > Save option would be grayed out until I made another change to the document. When I upgraded to Jaunty I automatically got the 3.0.1 version from the repos and I discovered that this feature no longer worked. That particular change was from the GoOO version. The GoOO group decided that Excel does not have that feature, so they disabled it in order to make OOo look more like Excel. (Yeah, lame.) 

I am currently using 3.0.1 from the Jaunty repos and it does everything I need. I'm sure the 3.1.0 version will be included in Karmic, so I'll just wait until I do a dist-upgrade in October. If you're running an older version of Ubuntu and don't want to do a dist-upgrade you'll have to get the .deb from OOo and install it manually if you want a newer version than what is in your repositories. As an alternative, you can follow the instructions above in this thread and add the special OOo repository - then you can just install the new version with Synaptic.

---

### Post by Weidbrewer on 2009-09-02
So...uh...Maybe? ;)

---

### Post by P.KO on 2009-09-02
Hi,

Or you can use the directions from here to add their [PPA]("https://edge.launchpad.net/~openoffice-pkgs/+archive/ppa") and have 3.1.0 and soon will 3.1.1 be available.

EDIT: 3.1.1 is now in this repository

---

