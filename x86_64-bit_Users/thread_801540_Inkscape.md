---
title: "Inkscape"
date: 2008-05-20
forum: x86 64-bit Users
---

### Post by DachaArh on 2008-05-20
is there anyway that Inkscape opens or imports .cdr files ?

---

### Post by DachaArh on 2008-05-21
can someone help please ?
I wanted to download s1K application, but there is no 64 bit version :(


Now I'm thinking of downloading ubuntu 32bit because it will support more apps, right ?

---

### Post by gsmanners on 2008-05-21
Actually, you can just build UniConverter from source.

```
sudo apt-get install build-essential alien
wget http://sk1project.org/downloads/uniconvertor/v1.1.2/uniconvertor-1.1.2.tar.gz
tar -xzf uniconvertor-1.1.2.tar.gz
cd UniConvertor-1.1.2
python setup.py bdist_rpm
cd dist
sudo alien UniConvertor-1.1.2-1.x86_64.rpm
sudo dpkg -i uniconvertor_1.1.2-2_amd64.deb
```

Then, just uniconv whatever you want to convert.

---

### Post by brunoscunha on 2008-05-21
While doing python setup.py bdist_rpm
I get this error

RPM build errors:
    Bad exit status from /var/tmp/rpm-tmp.83024 (%build)
error: command 'rpmbuild' failed with exit status 1


What can I do to correct it?

Thanks

---

### Post by DachaArh on 2008-05-22
I too got that error :

RPM build errors:
    Bad exit status from /var/tmp/rpm-tmp.78484 (%build)
error: command 'rpmbuild' failed with exit status 1

---

### Post by gsmanners on 2008-05-22
Might be missing a dependency. I think I neglected to notice that you need this:

python-imaging

I think there was an older issue where it needed xlibs, but I doubt it has that anymore.

---

### Post by brunoscunha on 2008-05-22
> **gsmanners said:**
> Might be missing a dependency. I think I neglected to notice that you need this:

python-imaging

I think there was an older issue where it needed xlibs, but I doubt it has that anymore.

I have python-imaging installed. Still doing the same error.

Is it possible to compile the sK1 source for hardy 64?

---

### Post by gsmanners on 2008-05-22
It would help if I knew what the stack trace was on that error. The source compiles just fine on my end (Hardy 64-bit), so I guess maybe there's some xlib stuff still in the code.

Try installing libx11-dev and xorg-dev. Maybe it needs some of that. (I have tons of dev stuff installed here, so it's kind of hard to nail it down.)

It could possibly need some more python stuff like python-dev or python-central (or both).

EDIT: Odd, but I think I may have found a package for this.

[http://security.ubuntu.com/ubuntu/pool/universe/p/python-uniconvertor/](http://security.ubuntu.com/ubuntu/pool/universe/p/python-uniconvertor/)

---

### Post by DachaArh on 2008-05-22
too much to work on :)

I got my CorelDraw X3 portable fully working on ubuntu :)

---

### Post by brunoscunha on 2008-05-22
> **DachaArh said:**
> too much to work on :)

I got my CorelDraw X3 portable fully working on ubuntu :)

How did you do that?

---

### Post by DachaArh on 2008-05-22
I have thinstalled X3
I installed MSXML 4.0 with winetricks, that was all I needed to do ;)
I had to run that thinstalled Corel once in windows XP , to create profile and all the files, and then copied all the files to ubuntu and installed MSXML 4.0.
and all is working now ;)
I tested almost all the features it's saving and opening files nice ;)

Here is the screenshoot :

[IMG]http://i29.tinypic.com/2v2ia8k.png[/IMG]

---

### Post by brunoscunha on 2008-05-22
hmm I see.

I installed some missing packages, and now uniconverter works just fine.

I had to run python setup.py bdist_rpm with sudo.

To bad sK1 does not has a amd64 deb package

---

### Post by DachaArh on 2008-05-23
> To bad sK1 does not has a amd64 deb package


I so agree with you on this , I hope they will make it ....

---

### Post by ArtInvent on 2008-07-22
Don't know why there are no good instructions for installing this nice little package. I finally got it working on Hardy AMD64. It will open my CDR v9 and v11 files (finally - thank heavens.) It will not open bitmaps or text; bitmaps are not that big a deal for me, but the text thing kind of sucks. If you have a working copy of CorelDraw, I find it's a little better to export from CorelDraw as an SVG file and then open in Inkscape. Bitmaps are still missing that way but text is present if you embed the complete font on exporting to SVG. Artistic text with special formatting will even be there but each letter will be a separate object.

INSTALLATION 

First, make sure you have the following packages, some of these are probably duplicates but what the h. I got hints from the debian site [http://packages.debian.org/en/source/lenny/python-uniconvertor]("http://packages.debian.org/en/source/lenny/python-uniconvertor") -

debhelper (>= 5.0.51)
dpatch
perl 
python2.5
python2.5-dbg
python2.5-dev
python-all-dbg (>= 2.4)
python-all-dev (>= 2.4)
python-central (>= 0.6)

then download the source from the sk1 site for UniConverter - I used 1.1.2 -
[http://sk1project.org/modules.php?name=Products&product=uniconvertor]("http://sk1project.org/modules.php?name=Products&product=uniconvertor")

Extract this directory and cd to it. I tried running the python install command as instructed in the readme, but permissions error, so used sudo -
```
$ sudo python setup.py install
```
This seemed to do the trick. Restart Inkscape and use Import command, you can now open CDR's.

---

