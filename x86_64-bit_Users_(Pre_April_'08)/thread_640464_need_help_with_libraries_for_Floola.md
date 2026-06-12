---
title: "need help with libraries for Floola"
date: 2007-12-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sukarn on 2007-12-14
[Floola]("http://www.floola.com/") is a 32 bit ipod manager. It requires some 32 bit libraries to be installed in order to run on a 64 bit system.
Under Linux on the [FAQ page]("http://www.floola.com/modules/wiwimod/index.php?page=docs_troubleshooting"), they say
```

**I'm running a x64 linux distro and Floola doesn't work**
You'll need to have proper 32bit version of some libraries (libcups, libgcrypt, libgnutls, libgpg-error, libtasn1).
```
They also link to a rar file that is supposed to contain the libraries for simple extraction, but that link is down. The file no longer exists on the server.

So, could anyone tell me whether there are any packages that I could install to get the 32 bit versions of the above mentioned libraries or exactly which commands I need to execute with [getlibs]("http://ubuntuforums.org/showthread.php?t=474790") to get the correct 32 bit libraries?

oh, btw, **getlibs Floola** doesn't work. It just says all dependencies satisfied.

The problem occurs when Floola is started with my iPod connected to the computer and configured in Floola. Floola just exits and prints (if started from console) -
```

Cannot find libgstreamer
Cannot find libxine
Segmentation fault (core dumped)

```

If the iPod is not connected, Floola remains open until I connect the iPod or manually close Floola.

The iPod model I have is iPod Classic.

---

### Post by Kilz on 2007-12-14
> **Sukarn said:**
> [Floola]("http://www.floola.com/") is a 32 bit ipod manager. It requires some 32 bit libraries to be installed in order to run on a 64 bit system.
Under Linux on the [FAQ page]("http://www.floola.com/modules/wiwimod/index.php?page=docs_troubleshooting"), they say
```

**I'm running a x64 linux distro and Floola doesn't work**
You'll need to have proper 32bit version of some libraries (libcups, libgcrypt, libgnutls, libgpg-error, libtasn1).
```
They also link to a rar file that is supposed to contain the libraries for simple extraction, but that link is down. The file no longer exists on the server.

So, could anyone tell me whether there are any packages that I could install to get the 32 bit versions of the above mentioned libraries or exactly which commands I need to execute with [getlibs]("http://ubuntuforums.org/showthread.php?t=474790") to get the correct 32 bit libraries?

oh, btw, **getlibs Floola** doesn't work. It just says all dependencies satisfied.

The problem occurs when Floola is started with my iPod connected to the computer and configured in Floola. Floola just exits and prints (if started from console) -
```

Cannot find libgstreamer
Cannot find libxine
Segmentation fault (core dumped)

```

If the iPod is not connected, Floola remains open until I connect the iPod or manually close Floola.

The iPod model I have is iPod Classic.

The problem appears to be that the application (foola) was most likely not compiled on Ubuntu. So it is looking for the libraries as it was named on the system it was compiled for. Those libraries are available under different names in Ubuntu. You could probably with trial and error create sysmlinks to the files with the name you need. 
But, you have a segfault (it crashed). This is a major problem that cant be fixed as easy. Since the source doesnt appear to be available from foola, you are going to have to contact them and tell them of your problems. Then wait as they fix it.

---

### Post by daengbo on 2007-12-14
Since you're down for a while with Floola, consider using [Hipo]("apt:hipo") in the meantime.

---

### Post by Sukarn on 2007-12-14
Thanks for responding guys/gals.

> **daengbo said:**
> Since you're down for a while with Floola, consider using [Hipo]("apt:hipo") in the meantime.

How do you open these **apt:** links? Firefox just tells me that it does not know how to open the address because the protocol (apt) isn't associated with any program.
Now, I'm not completely Ubuntu-illiterate. I understand that you are directing me to install hipo using apt, I just want to know how to associate the protocol to run the command its supposed to run.

EDIT:
Hipo doesn't seem to support iPod Classic, and yes, I tried the latest version from getdeb.com
apart from that, I guess I'll have to stick to using gtkpod, although it doesn't handle podcasts as flexibly as Floola, I'll have to use it since its the only application I've found to support video transfer to and from the iPod.

---

### Post by Cappy on 2007-12-14
You should try
```
sudo getlibs -32 libgstbase-0.10.so.0 libxine.so.1
```

The dependencies weren't added in to the program in such a way that ldd can see them. You can see this in that it uses non-default error messages.

To solve this problem I searched on the packages.ubuntu.com on the two packages and found the library name. Very round about. Installing by package name is a feature that will be added in the next getlibs.

---

### Post by daengbo on 2007-12-14
Sukarn,

Gutsy is set up to handle apt: links by default. When you click on the link, your computer should just ask you if you want to install the program or not, which is why I use them in my suggestions: it's a lot easier for the user.

I didn't realize that Hipo only supported later iPods.

Sorry that it didn't work for you.

---

### Post by Sukarn on 2007-12-15
> **Cappy said:**
> You should try
```
sudo getlibs -32 libgstbase-0.10.so.0 libxine.so.1
```

The dependencies weren't added in to the program in such a way that ldd can see them. You can see this in that it uses non-default error messages.


Before you replied (thanks for taking out the time to reply), I had already run the following command -
```
getlibs -32 libgstreamer-0.10.so.0
```
Yes, I did that without **sudo** (saw it in my terminal logs). The installation seemed to succeed but since then Floola has been giving me the error -
```
Incompatible version of libgstreamer
```
instead of the original -
```
Cannot find libgstreamer
```

After running the command you suggested (with root privileges), the error about libxine and the segmentation fault stopped but I still get the error about incompatible version of libgstreamer, and Floola freezes instead of crashing.

Any idea what I could do about this?



> **daengbo said:**
> Gutsy is set up to handle apt: links by default. When you click on the link, your computer should just ask you if you want to install the program or not, which is why I use them in my suggestions: it's a lot easier for the user.
It wasn't set up to handle apt: links by default for me, and it still isn't handling those links in FF-3.0 alpha 8 after installing the apturl package. It started working in FF 2 after installing the apturl package though.
I'll look through the files that apturl installs to check what it changes and implement that into my FF-3.0

---

### Post by Cappy on 2007-12-15
It seems Floola won't work with Gutsy unless you install older libraries.

I searched and I can't find what gstreamer package it needs. You'll have to go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and search under Feisty for libgstreamer.

The two that come up for Feisty are:
[http://packages.ubuntu.com/feisty/libs/libgstreamer0.8-0](http://packages.ubuntu.com/feisty/libs/libgstreamer0.8-0)
[http://packages.ubuntu.com/feisty/libs/libgstreamer0.10-0](http://packages.ubuntu.com/feisty/libs/libgstreamer0.10-0)

download the i386 package. 
```
dpkg -x packagename.deb extractfolder
sudo cp -R extractfolder/usr/lib/* /usr/lib32/
```

Try it for both packages. If it makes you feel any better I think a 32-bit user will have to do the same thing. I don't know how old this package is - it may require older ubuntu distros!? Hopefully it shouldn't require you to delete any newer (the Feisty) gstreamer libraries in /usr/lib32 but it couldn't hurt.

---

### Post by daengbo on 2007-12-15
> It wasn't set up to handle apt: links by default for me, and it still isn't handling those links in FF-3.0 alpha 8 after installing the apturl package. It started working in FF 2 after installing the apturl package though.
I'll look through the files that apturl installs to check what it changes and implement that into my FF-3.0
Interesting. The ubufox package depends on apturl. Ubufox is the package which makes Ubuntu-specific changes to Firefox and is installed in Gutsy by default.

I wonder why you don't have it.

---

### Post by blurryone on 2007-12-17
nearly there guys... am still getting this msg when launching floola

Cannot find libgstreamer
Cannot find libxine
Segmentation fault (core dumped)

but have got the link on the floola website fixed so we can get the libs they think we need from the floola faq...

___________________________________________________________

I'm running a x64 linux distro and Floola doesn't work

You'll need to have proper 32bit version of some libraries (libcups, libgcrypt, libgnutls, libgpg-error, libtasn1). If you don't know how to do this simply copy as root files contained in [this]("http://www.floola.com/download/click.php?action=go&to=32bitlib-lin") package to /usr/lib32 (Thanks Adam Thayer)

__________________________________________________________

---

### Post by Sukarn on 2007-12-18
> **blurryone said:**
> nearly there guys... am still getting this msg when launching floola

Cannot find libgstreamer
Cannot find libxine
Segmentation fault (core dumped)

but have got the link on the floola website fixed so we can get the libs they think we need from the floola faq...

___________________________________________________________

I'm running a x64 linux distro and Floola doesn't work

You'll need to have proper 32bit version of some libraries (libcups, libgcrypt, libgnutls, libgpg-error, libtasn1). If you don't know how to do this simply copy as root files contained in [this]("http://www.floola.com/download/click.php?action=go&to=32bitlib-lin") package to /usr/lib32 (Thanks Adam Thayer)

__________________________________________________________

Did you run the command **sudo getlibs -32 libgstbase-0.10.so.0 libxine.so.1** that Cappy posted earlier?
You need getlibs for using this command. Read my first post if you don't know where to get getlibs.

**EDIT:**
With gstreamer-0.8 from feisty, Floola complains that it cannot find libgstreamer.
With gstreamer-0.10, Floola complains that the version of libgstreamer is incompatible.
In either case, Floola stops responding when the iPod has been configured.

---

### Post by stinkinrich88 on 2008-04-02
so it's not possible at all then?

---

### Post by radosd on 2008-04-08
I think I have a solution for this problem.

Actually, the message
```
Incompatible version of libgstreamer
```
is not about incompatibility. It complains because of missing gst-plugins-base and gst-plugins-good.

For me, installing these two solved it.

---

### Post by stinkinrich88 on 2008-04-08
what are those packages? where do we get them? thanks!

---

### Post by radosd on 2008-04-08
Not sure how do you install software, I'm a Gentoo user. Download page of GStreamer has some links:
```
http://gstreamer.freedesktop.org/download/
```

And I found them also in ubuntu package search
```
http://packages.ubuntu.com/search?keywords=gstreamer&searchon=names&suite=all&section=all
```

---

### Post by Floola on 2008-04-08
Floola was compiled using REALBasic 2007r3 you should refer  to [http://forums.realsoftware.com/viewforum.php?f=8](http://forums.realsoftware.com/viewforum.php?f=8) as there seem to be other people with the same issue. REALBasic 2007r3 is a nice tool but doesn't give you any control on compilation so there's nothing I can do about it.

If you find out how to fix this please let me know by email if possible.

---

### Post by sistoviejo on 2008-05-08
I tried that but getlibs isn't found on my system.
```

silvio@silvio-laptop:~$ sudo getlibs -32 libgstbase-0.10.so.0 libxine.so.1
sudo: getlibs: command not found

```
UPDATE:
I've solved my problem.
Please read this post if you are still struggling to transfer video and audio podcasts to your ipod:
[http://ubuntuforums.org/showpost.php?p=4912018&postcount=3](http://ubuntuforums.org/showpost.php?p=4912018&postcount=3)

---

### Post by eznet on 2008-05-21
> **Floola said:**
> ... so there's nothing I can do about it.

If you find out how to fix this please let me know by email if possible.

First, I just want to say, what little bit I have actually been able to get Floola to run, I loved it - bang up job.  Really nice program with some really neat features.  

Now, with that out of the way, there is something you can do about the problems and I do have a solution to fix the problem - apply a license that you are comfortable with to the source, and release it so that the community can have a swing at knocking these bugs out.  I understand you want to keep hold of your baby, so do, but in its current state (and how it has been for most of its time out) it is largely useless to a large percentage of the Linux community... Windows doesn't really need it, so good luck securing much there.  If you could get this thing running on more machines, you stand a very real possibility at securing the largest share of the Linux/iPod userbase of any of the iPod apps - but again, in its current state it is mostly serving to give hope to iPod Linux users and then dashing these hopes a couple of clicks later.

Just my opinion.  It is a daunting task to maintain an app like this alone - why not get some assistance?  Its not like you are charging here.  If you opened it up and generated some interest you could even stand to generate revenue via pagehits and support services...

-Matt

---

### Post by Floola on 2008-06-15
Since many users were complaining of problems with Ubuntu x86-64bits I tried myself.

I posted steps (actually nothing particular) to make Floola work under 64bit enviroment here:

[http://www.floola.com/modules/newbb/viewtopic.php?topic_id=660&start=0#forumpost2881](http://www.floola.com/modules/newbb/viewtopic.php?topic_id=660&start=0#forumpost2881)

Hope this helps others,
Tomas

---

### Post by Sukarn on 2008-06-15
Hey, thanks for trying, but what I can see from your post on that page is that you only tried as far as checking whether Floola was running or not.

Floola opens fine on my computer as long as my 6th Generation iPod (sorry, I don't have an older one to test it) is not connected to my PC. No error messages are displayed on the terminal either.

However, if I open Floola while my iPod is connected, or if I connect my iPod after opening Floola, then Floola opens up a new window with title ":: Fast mode ::" which has a progress bar. While this window is open, it seems that the iPod is being read, and the computer uses 100% CPU (I suppose it is reading all the files on the iPod). After this is done, this new window closes, and returns me to the main Floola window which becomes un-responsive. and remains empty like it is when no iPod is connected.

Just after connecting the iPod to the PC, or just after opening Floola if the iPod is already connected to the PC, I get this output in the terminal -
```

$ ./Floola 
Incompatible version of libgstreamer

```
If I close Floola without connecting the iPod, then there is no output from the program.

---

### Post by Floola on 2008-06-16
Follow up:
1) Clean install of Ubuntu 8.04 x86-64bit
2) Update system using System->Administrator->Update Manager
3) Download, double click and install: [http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
4) Download Floola-linux.tar.gz and save it to Desktop
5) Open Applications->Accessories->Terminal
6) in Terminal type cd Desktop; tar zxvf Floola-linux.tar.gz; cd Floola-linux
7) in Terminal type getlibs ./Floola
8) in Terminal type getlibs -p gstreamer0.10-alsa
9) in Terminal type getlibs -p libgstreamer0.10-0
10) in Terminal type getlibs -p libgstreamer-plugins-base0.10-0
11) in Terminal type getlibs -p gstreamer0.10-plugins-ugly
12) in Terminal type getlibs -l libmad.so.0 libmpeg2.so.0 libdvdread.so.3 liboil-0.3.so.0 libsidplay.so.1

This should make Floola start with an iPod attached, but (at least on the virtual box were I installed x86-64bit) there will be no audio.

It's all about finding the mysterious missing lib: the trick is (more or less) to try to add 32bit libs using getlibs -p <packagename> or getlibs -l <libfilename>. I guess it has to be some gstreamer extension or libstreamer. 

After using getlibs -p <package>, start Floola in terminal. If some libs are missing they should be reported with an error message. Quit Floola and use getlibs -l <missinglibfilename>.

Hope this helps. It's a first step. If anybody finds out something let me know, by email directy.

---

### Post by stinkinrich88 on 2008-06-16
Fook sake. Sukarn, what program are you using for your iPod atm? I'm blatantly going to have to forget about Floola, it's been months. I've tried gtkpod and rhythmbox and I lost all my album art SOOO ANNOYING!! I'd appreciate some recommendations if there are any. Cheers

---

### Post by Cappy on 2008-06-16
I don't have an ipod, so I can't test this out but try
```
sudo getlibs -p libgstreamer0.10-0
```
> sudo ln -s /usr/lib32 /usr/l32; sudo sed -i -e 's+/usr/lib+/usr/l32+g' /usr/lib32/libgstreamer-0.10.so.0

---

### Post by Sukarn on 2008-06-17
After getting a few of the above mentioned 32 bit gstreamer packages (upto step 10 in Floola's post) with getlibs (thanks guys), I got this error after the "Fast mode" window from Floola -

```

init error: 
Your iPod wasn't properly setup. You'll need to restore it with iTunes before using Floola

```

I did not submit a bug report from the feedback window because I would have to include some background information that you already know in this thread.

That error is kind of weird because my iPod works with gtkpod and gpodder. I don't have a backup of my music collection (lack of HD  space) so I'm not going to format the device because its working with some other softwares.

After getting the packages from step 11 and step 12, I now just get a blank box in place of the above mentioned error. I did a "sudo getlibs -l liba52-0.7.4.so libid3tag.so.0" as well because of a couple of errors that popped up in the terminal, but that did not change anything other than removing all errors from terminal.

Cappy's suggestion did not yeild a fruitful result either.

Thanks a lot for the effort though. It seems like a great application, and I suppose that you've got a lot of happy 32-bit users.


> **stinkinrich88 said:**
> Fook sake. Sukarn, what program are you using for your iPod atm? I'm blatantly going to have to forget about Floola, it's been months. I've tried gtkpod and rhythmbox and I lost all my album art SOOO ANNOYING!! I'd appreciate some recommendations if there are any. Cheers

Right now I'm just using my iPod with gPodder (podcast software) because my music collection is kind of stable and has not changed in a while, and because I mostly use the iPod for listening to podcasts.

For the odd album or video that I want to add to the iPod I just use gtkpod and it works with album artwork for me.

I did not write anything to the iPod with rhythmbox because it does not read the iTunes.db file on the iPod. It scans the iPod for media files. It was showing me the original tags on the files that were present an the iPod instead of showing me the tags present in the iTunes.db file.

I tried Amarok for transferring music (it does not handle Videos) to my iPod in December last year and it messed up album artwork by giving random album artwork to a lot of files that previously did not have any artwork.

So, because I don't transfer a lot of music/videos to the iPod, I'm happy with gtkpod. All my audio podcasts are handled by gPodder.

The latest songbird (available on getdeb) promises iPod support with a plugin. The plugin page says that 6th generation ipods are supported but I haven't tried it out myself.

Lastly, so far I have not seen a single application on linux that can handle photo transfer on 6th gen ipods. Those that show previews (the right side of split screen view) and actual full size photos, do not show the thumbnails, and those that show the thumbnails, do not show the previews and actual photos.

---

### Post by Floola on 2008-06-18
Hi,

that error appears since you've been using those other iPod softwares (it has nothing to do with libraries this time). These don't write the db exactly in the same way iTunes does. To avoid problems Floola expects a 100% iTunes like db, if it doesn't it gives that error. Connecting the iPod to iTunes once, fixes this issue. Recently (ver. 3.0beta1) support for adding photos was added to Floola too.

About the libraries a user reported ([http://www.floola.com/modules/newbb/viewtopic.php?topic_id=660&start=10](http://www.floola.com/modules/newbb/viewtopic.php?topic_id=660&start=10)) that installing via synaptic ia32libs, lib32gcc1, libc6i386 is enough.

HTH,
Tomas

---

### Post by Sukarn on 2008-06-19
> **Floola said:**
> Hi,

that error appears since you've been using those other iPod softwares (it has nothing to do with libraries this time). These don't write the db exactly in the same way iTunes does. To avoid problems Floola expects a 100% iTunes like db, if it doesn't it gives that error. Connecting the iPod to iTunes once, fixes this issue. Recently (ver. 3.0beta1) support for adding photos was added to Floola too.

About the libraries a user reported ([http://www.floola.com/modules/newbb/viewtopic.php?topic_id=660&start=10](http://www.floola.com/modules/newbb/viewtopic.php?topic_id=660&start=10)) that installing via synaptic ia32libs, lib32gcc1, libc6i386 is enough.

HTH,
Tomas

Thanks. Since I do not own a Windows system, I'll try connecting my iPod with a friend's Windows system with iTunes and removing a couple of songs to write the db with iTunes. However. it will take me till the 22nd of June to report back (got an important upcoming exam).

---

### Post by stinkinrich88 on 2008-06-22
Thanks, Floola. I can confirm that your solution works!

---

### Post by stinkinrich88 on 2008-06-22
Just one problem, though: I can't load my flacs onto my iPod anymore because when I drag them across Floola freezes (it's fine with MP3s). I think this is because it doesn't think I have FFmpeg (it says so in my preferences) but I do have it installed. Do I need a fancy 32bit version or summut? If so, how? 

thanks!

---

### Post by stinkinrich88 on 2008-07-01
It'd be so cool if flac conversion would work again. 

I tried version 3.0 today and it's better but still doesn't work: preferences recognises I have the converter installed. When I drag a flac to add files it loads the conversion thing. I click "convert" and an orange dot appears then the conversion window disappears and the flac is lost from the add files thing. 

Any ideas? this would be super cool

---

### Post by stinkinrich88 on 2008-07-04
ahh, I can't even add AACs. It doesn't do anything at all when I drag/drop them. any ideaz?

---

