---
title: "Official Nowshining WINE UPDATE THREAD (June 18 2008)"
date: 2008-06-19
forum: Wine
---

### Post by nowshining on 2008-06-19
This thread is the official thread on this site/forum that will updated to show when I compiled a deb, etc.. of WINE  So please check this thread after a new WINE version has been released to see if I created a deb file, etc.. and when and where to download it if the hosting site has changed. 

If you don't see a newer version - please keep checking about at least once a day as it may take me some time to know when a new version has been released and to compile/debify/upload it.

Ty. Here is the Readme (modified for forums) I included in the zip file: Remember My speciality now is for i386 and for the Ubuntu GutsyGibbon 7.10 of the Ubuntu Operating System so I don't offer a guarantee of it working  on any other distro/ubuntu version smoothly. again Ty and I do hope it works for you. 

A new reply (bump) if it gets kicked to the next page on the forums will be added and the date i updated the thread with a new WINE ver. will be in the title. Dates are in PST time.

...................................................

1.) Important: FIRST Remove the older WINE version from synaptic, apt-get, adept, etc.. -

What's Diff. in this one from the last one I compiled (besides the differences/bug fixes, etc.. in the actual WINE program, etc..) - well the rc5 of 1.0 didn't incl. scanner, etc.. development files/programs when installing, however this time I got all the needed lib-devs before compile time so it should of compiled for everything. 

That I'm going to start to include this readme and zip it up with it before I upload to a site to host it however the above what's diff. will either be the same or diff. Prob. diff. on the next compile and the same on the rest.

FAQ: 

Q: Do you optimize the code for your specific cpu, etc..?

A: No I just usually do make and then sudo checkinstall -D make install - this time I'm learning how to do make dependency first when doing a make so that way my programs that I make/compile work better for others example: make depend && make.

Q: I use RPM, slackware, etc.., Can I use debs on my system?

A: No, however install alien from your local repo and it should be able to convert the deb to an rpm, slackware, etc.. but I don't guarantee anything.

Q: I installed alien how do I do the conversion?

A: Use sudo if you can and do the following in the temrinal/CLI depending on your distro.

...........................................

RPM:

sudo alien -r pathtofile/file
............................................

Stampede slp package:

sudo alien --to-slp pathtofile/file

...........................................

LSB package:

sudo alien -l pathtofile/file..

..............................................

Slackware Tgz package:

sudo alien -t pathtofile/file

................................................

  -r, --to-rpm              Generate a Red Hat rpm package.
      --to-slp              Generate a Stampede slp package.
  -l, --to-lsb              Generate a LSB package.
  -t, --to-tgz              Generate a Slackware tgz package.

................................................

Q: Okay above I see nothing about what to do for the package my distro uses, what do I do?

A: Sorry do a search on the net to see if there is a program that will convert to your local distro, etc.. I don't know how to convert to those kind of packages, again sorry.

Q: How do I install this baby?

A: Look at your distros Documentation if you converted to see how, however in a GUI the usual way is to double-click and it should bring up a graphical way to do so. If using ubuntu a double-click should do the trick and follow the directions from there.

Q: Okay I finally got this thing installed, what do I do now?

A: Do what you did before - start a Windows game, program, etc.. if you want u can see if it installed properly by going into the wine config program and going to the about tab of which it should show the version you were trying to install.

Q: I use a 64-bit OS what do I do?

A: Do what I did for i386 if using ubuntu checkinstall should be installed by default and become a maintainer for the 64-bit platform like I did for the i386 one.

Q: Okay on ur 64-bit Q and Answer - does that mean I'll have to compile from source?

A: Yes it does, once you get the needed libraries it's quite easy - when compiling in ubuntu or another disto if can install build-essential from the repos and if the ./configure has errors, remeber any libs needed are the -dev or development versions which can usually be found in your distros local repository.

Q: Okay I compiled for the 64-bit platform, distro, etc.. What do I do now?

A: Upload it to a sharing host, etc.. or if your on a fast connection and/or can have high uptimes of being connected onto the inernet then you can host it on your computer. Then go to winehq.com and sign up for the forums and announce it for everyone and the link to download (one post if can allow one for letting others know of any updates). Then go onto the linux forums, etc.. that your on and let everyone know of your compile (one post if can allow one for letting others know of any updates) and give a bit of time and u'll see a lot downloads. :).
...................................................

Order is Oldest to Newest ie: oldest version I compiled will be @ top & newest will be the last one.

Wine 1.0 rc5 - [Download](http://www.4shared.com/file/51265421/803d9f4/wine-10-rc5_rc5-1_i386.html)

Wine 1.0 final - [Download](http://www.4shared.com/file/51889527/b4df3449/wine10_i386.html)

---

### Post by Alex Carroll on 2008-06-19
Wine 1.0 has already been released for both i386 and AMD64 on Gutsy.

---

### Post by nowshining on 2008-06-19
yeah i know i just saw that afterwards but i think it's going to be the only version and it seems they released and official winehq build for all dis-continued debian distros even on the real ol' ones they have.

So well see how things go and if they just did it to make it a stable thing for 1.0 and release it for all distro versions of ubuntu/debain and won't make anymore - 'cause if u go to the download page u'll have to go into the older debs to see it and gutsy, etc.. is not shown with an howtwo get an update.

---

### Post by cogadh on 2008-06-19
Since Wine has gone stable with the 1.0 release, any future stable releases will likely be distributed through the official Ubuntu backports. Unstable development releases will probably not get packaged at all and most people really shouldn't use them anyway, unless they are working on testing or developing Wine.

---

