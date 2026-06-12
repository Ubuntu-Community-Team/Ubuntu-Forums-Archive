---
title: "amazonmp3 released for linux x86 32.. no go for x64"
date: 2008-03-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by jamesrdorn on 2008-03-01
They did not release the source, so I forced the architecture install via dpkg, now it wont start because it cant find libgtkmm-2.4.so.1... but it's clearly in the filesystem

/usr/lib/libgtkmm-2.4.so.1


amazonmp3: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory

---

### Post by soxs on 2008-03-01
I don't know how often I said this (don;t car, just a phrase): *Have a look at [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) it automates dowloading missing 32bit libs on 64 bit debian distributions

---

### Post by Kilz on 2008-03-01
> **jamesrdorn said:**
> They did not release the source, so I forced the architecture install via dpkg, now it wont start because it cant find libgtkmm-2.4.so.1... but it's clearly in the filesystem

/usr/lib/libgtkmm-2.4.so.1


amazonmp3: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory

The application cant see it because that is a 64bit library. You need a 32bit version in /usr/lib32/ .As SOXS said, use getlibs. Never ever force install libraries.

---

### Post by milas on 2008-03-01
I used getlibs and it still isn't working:

```
$ getlibs /usr/bin/amazonmp3
This application isn't missing any dependencies
$ amazonmp3
terminate called after throwing an instance of 'Gdk::PixbufError'
Aborted (core dumped)

```

Running as root makes no difference.

Any ideas?

---

### Post by baryonyx on 2008-03-01
Interesting..

When I run it on my gutsy amd64 box I get the following:

sudo getlibs /usr/bin/amazonmp3
libcairomm-1.0.so.1: BinaryfileXmatches
libglibmm-2.4.so.1: BinaryfileXmatches
libcurl.so.4: BinaryfileXmatches
libboost_date_time-gcc41-1_34_1.so.1.34.1: BinaryfileXmatches
libboost_signals-gcc41-1_34_1.so.1.34.1: BinaryfileXmatches
libboost_iostreams-gcc41-1_34_1.so.1.34.1: BinaryfileXmatches
libboost_thread-gcc41-mt-1_34_1.so.1.34.1: BinaryfileXmatches
libglibmm-2.4.so.1: BinaryfileXmatches
libcairomm-1.0.so.1: BinaryfileXmatches
libglibmm-2.4.so.1: BinaryfileXmatches
libcairomm-1.0.so.1: BinaryfileXmatches
libglibmm-2.4.so.1: BinaryfileXmatches
libglibmm-2.4.so.1: BinaryfileXmatches
libcairomm-1.0.so.1: BinaryfileXmatches
The following i386 packages will be installed:
BinaryfileXmatches
Continue [Y/n]? Y
W: Unable to locate package BinaryfileXmatches
E: No packages found
BinaryfileXmatches was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install


As far as I can tell, there's no such package called BinaryfileXmatches

---

### Post by crjackson on 2008-03-01
Seriously, garb the script by cappy called [getlibs]("http://ubuntuforums.org/showthread.php?t=474790") follow the instructions and run them.  It will install the needed files and AmazonMP3 works great with Ubuntu 7.10 x64.  I've got it installed on all my machines now.

---

### Post by firenurse4 on 2008-03-01
> **baryonyx said:**
> Interesting..

When I run it on my gutsy amd64 box I get the following:

sudo getlibs /usr/bin/amazonmp3
libcairomm-1.0.so.1: BinaryfileXmatches
libglibmm-2.4.so.1: BinaryfileXmatches
libcurl.so.4: BinaryfileXmatches
libboost_date_time-gcc41-1_34_1.so.1.34.1: BinaryfileXmatches
libboost_signals-gcc41-1_34_1.so.1.34.1: BinaryfileXmatches
libboost_iostreams-gcc41-1_34_1.so.1.34.1: BinaryfileXmatches
libboost_thread-gcc41-mt-1_34_1.so.1.34.1: BinaryfileXmatches
libglibmm-2.4.so.1: BinaryfileXmatches
libcairomm-1.0.so.1: BinaryfileXmatches
libglibmm-2.4.so.1: BinaryfileXmatches
libcairomm-1.0.so.1: BinaryfileXmatches
libglibmm-2.4.so.1: BinaryfileXmatches
libglibmm-2.4.so.1: BinaryfileXmatches
libcairomm-1.0.so.1: BinaryfileXmatches
The following i386 packages will be installed:
BinaryfileXmatches
Continue [Y/n]? Y
W: Unable to locate package BinaryfileXmatches
E: No packages found
BinaryfileXmatches was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install


As far as I can tell, there's no such package called BinaryfileXmatches

I am getting the same brickwall.

---

### Post by jamesrdorn on 2008-03-01
> **baryonyx said:**
> Interesting..

When I run it on my gutsy amd64 box I get the following:

sudo getlibs /usr/bin/amazonmp3
libcairomm-1.0.so.1: BinaryfileXmatches
libglibmm-2.4.so.1: BinaryfileXmatches
libcurl.so.4: BinaryfileXmatches
libboost_date_time-gcc41-1_34_1.so.1.34.1: BinaryfileXmatches
libboost_signals-gcc41-1_34_1.so.1.34.1: BinaryfileXmatches
libboost_iostreams-gcc41-1_34_1.so.1.34.1: BinaryfileXmatches
libboost_thread-gcc41-mt-1_34_1.so.1.34.1: BinaryfileXmatches
libglibmm-2.4.so.1: BinaryfileXmatches
libcairomm-1.0.so.1: BinaryfileXmatches
libglibmm-2.4.so.1: BinaryfileXmatches
libcairomm-1.0.so.1: BinaryfileXmatches
libglibmm-2.4.so.1: BinaryfileXmatches
libglibmm-2.4.so.1: BinaryfileXmatches
libcairomm-1.0.so.1: BinaryfileXmatches
The following i386 packages will be installed:
BinaryfileXmatches
Continue [Y/n]? Y
W: Unable to locate package BinaryfileXmatches
E: No packages found
BinaryfileXmatches was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install


As far as I can tell, there's no such package called BinaryfileXmatches


I got the same problem. here was my fix
```

sudo getlibs libcairomm-1.0.so.1 libglibmm-2.4.so.1 libcurl.so.4 libboost_date_time-gcc41-1_34_1.so.1.34.1 libboost_signals-gcc41-1_34_1.so.1.34.1 libboost_iostreams-gcc41-1_34_1.so.1.34.1 libboost_thread-gcc41-mt-1_34_1.so.1.34.1 libglibmm-2.4.so.1 libcairomm-1.0.so.1 libglibmm-2.4.so.1 libcairomm-1.0.so.1 libglibmm-2.4.so.1 libglibmm-2.4.so.1 libcairomm-1.0.so.1
```

works like a charm.

---

### Post by Cappy on 2008-03-01
I uploaded a new getlibs that fixes this. Install the new one! =)

You can also use
> sudo getlibs -p libboost-date-time1.34.1 libboost-iostreams1.34.1 libboost-signals1.34.1 libboost-thread1.34.1 libcairomm-1.0-1 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a

---

### Post by firenurse4 on 2008-03-01
I was struggling with this but found an answer.
[LIST=1]
[*]Remove amazonmp3
[*]Download and intalll the amazonmp3 for debian sid
[*]Use getlibs for some of the dependencies
[*]By running amazonmp3 in the terminal, you will find some additional dependencies that need installed with getlibs. I did those one at a time
[/LIST]

Unfortunately I didn't document all of them, but will try to recreate them later.

**Update**
After looking back, I added the following
> sudo getlibs libcom_err.so.2 libgssapi_krb5.so.2 libboost_thread-gcc-mt-1_33_1.so.1.33.1 libboost_iostreams-gcc-mt-1_33_1.so.1.33.1 libboost_signals-gcc-mt-1_33_1.so.1.33.1  libboost_date_time-gcc-mt-1_33_1.so.1.33.1 libssl.so.0.9.8

---

### Post by crjackson on 2008-03-02
> **firenurse4 said:**
> I was struggling with this but found an answer.
[LIST=1]
[*]Remove amazonmp3
[*]Download and intalll the amazonmp3 for debian sid
[*]Use getlibs for some of the dependencies
[*]By running amazonmp3 in the terminal, you will find some additional dependencies that need installed with getlibs. I did those one at a time
[/LIST]

Unfortunately I didn't document all of them, but will try to recreate them later.

**Update**
After looking back, I added the following

I actually didn't download any of these as they weren't available when I installed.  Amazon emailed me the deb file and I didn't seem to have so many issues.  I have a few missing dependencies that were slamed in by getlibs without any problems.  I'm going to download the deb posted on the site and see what the difference is if any.

---

### Post by Triptol on 2008-03-03
> **milas said:**
> I used getlibs and it still isn't working:

```
$ getlibs /usr/bin/amazonmp3
This application isn't missing any dependencies
$ amazonmp3
terminate called after throwing an instance of 'Gdk::PixbufError'
Aborted (core dumped)

```

Running as root makes no difference.

Any ideas?

Same one here. Did you fix it? I thought it might have to do with the fact that I'm running hardy.

---

### Post by vgrisham on 2008-03-23
> **Triptol said:**
> Same one here. Did you fix it? I thought it might have to do with the fact that I'm running hardy.

It must have something to do with Hardy. I installed via Gutsy 64 and getlibs, and it worked fine. I installed Hardy today, and I get:
> 
(amazonmp3:6902): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64
terminate called after throwing an instance of 'Gdk::PixbufError'
Aborted (core dumped)


---

### Post by Cappy on 2008-03-23
Yes, it is hardy, look here:
[http://ubuntuforums.org/showthread.php?t=613087&page=5#41](http://ubuntuforums.org/showthread.php?t=613087&page=5#41)

---

### Post by Rogers on 2008-03-24
> **milas said:**
> I used getlibs and it still isn't working:

```
$ getlibs /usr/bin/amazonmp3
This application isn't missing any dependencies
$ amazonmp3
terminate called after throwing an instance of 'Gdk::PixbufError'
Aborted (core dumped)

```

Running as root makes no difference.

Any ideas?

I used getlibs and it worked fine.  Here is what i did [http://runithard.com](http://runithard.com) .

---

### Post by vgrisham on 2008-03-24
> **Cappy said:**
> Yes, it is hardy, look here:
[http://ubuntuforums.org/showthread.php?t=613087&page=5#41](http://ubuntuforums.org/showthread.php?t=613087&page=5#41)

Thanks Cappy. I looked at the thread you cite above. Do you have any recommendations? Would it be wise to downgrade GTK? Is there way to just spoof the library that it's looking for?

---

### Post by computx on 2008-04-21
You don't need to downgrade gdk
I found a solution for my gdkpixbufferror on this thread.

[http://ubuntuforums.org/showpost.php?p=4660832&postcount=7](http://ubuntuforums.org/showpost.php?p=4660832&postcount=7)

I have an amd64 system and therefore the following commands fixed me up.
```
sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9
```

note: I found on my system that I needed to substitute  /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9 for /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.8 in the thread linked above.

---

### Post by mrfuzzemz on 2008-04-21
> **computx said:**
> You don't need to downgrade gdk
I found a solution for my gdkpixbufferror on this thread.

[http://ubuntuforums.org/showpost.php?p=4660832&postcount=7](http://ubuntuforums.org/showpost.php?p=4660832&postcount=7)

I have an amd64 system and therefore the following commands fixed me up.
```
sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9
```

note: I found on my system that I needed to substitute  /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9 for /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.8 in the thread linked above.


Great find! Works great as of now.

---

### Post by jeromio on 2008-05-05
No go for me. I grabbed the later version of getlibs, which pulled the .so files. 
> getlibs /usr/bin/amazonmp3
libgtkmm-2.4.so.1: libgtkmm-2.4-1c2a
libgdkmm-2.4.so.1: libgtkmm-2.4-1c2a
libatkmm-1.6.so.1: libgtkmm-2.4-1c2a
libpangomm-1.4.so.1: libgtkmm-2.4-1c2a
libcairomm-1.0.so.1: libcairomm-1.0-1
libglibmm-2.4.so.1: libglibmm-2.4-1c2a
libcurl.so.4: libcurl3
libboost_date_time-gcc41-1_34_1.so.1.34.1: libboost-date-time1.34.1
libboost_signals-gcc41-1_34_1.so.1.34.1: libboost-signals1.34.1
libboost_iostreams-gcc41-1_34_1.so.1.34.1: libboost-iostreams1.34.1
libboost_thread-gcc41-mt-1_34_1.so.1.34.1: libboost-thread1.34.1
The following i386 packages will be installed:
libboost-date-time1.34.1
libboost-iostreams1.34.1
libboost-signals1.34.1
libboost-thread1.34.1
libcairomm-1.0-1
libcurl3
libglibmm-2.4-1c2a
libgtkmm-2.4-1c2a

I also used the l32 --> sed etc. fix form the post above. But I still get this
> jeromio@blirp:/home/downloads$ amazonmp3

(amazonmp3:10136): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64

(amazonmp3:10136): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64
terminate called after throwing an instance of 'Gdk::PixbufError'
Aborted
Any other debug steps I can try? Thanks.

---

### Post by computx on 2008-05-06
You stated you tried the sed line above. You are using a newer version of libs so did you type it exacctly as I had it?
```


sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9

``` 
or did you substitute for your version libs? like this.
```


sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.10

```
if not try that last line.

---

### Post by jeromio on 2008-05-07
> **computx said:**
> You stated you tried the sed line above. You are using a newer version of libs so did you type it exacctly as I had it?
```


sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9

``` 
or did you substitute for your version libs? like this.
```


sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.10

```
if not try that last line.One thing I had not done was run getlibs on /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so. Not sure why running getlibs on the amazonmp3 file didn't pick that up. SO that takes care of that issue. I still have problems though. I actually have 
/usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9
on my system, not 
/usr/lib32/libgdk_pixbuf-2.0.so.0.1200.10

I was getting 
> terminate called after throwing an instance of 'Gdk::PixbufError'
AbortedSince then I rebooted and now I get
> (amazonmp3:10911): Gtk-WARNING **: libqt-mt.so.3: cannot open shared object file: No such file or directory

(amazonmp3:10911): Gtk-WARNING **: libqt-mt.so.3: cannot open shared object file: No such file or directory
terminate called after throwing an instance of 'Gdk::PixbufError'
AbortedSO, then I ran getlibs on that. Very strange. Anyhow, I'm back to plain old
> terminate called after throwing an instance of 'Gdk::PixbufError'
AbortedOut of desperation, I did try
> sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.10but I get 
> sed: can't read /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.10: No such file or directory
Which makes sense, b/c I don't have that file.

---

