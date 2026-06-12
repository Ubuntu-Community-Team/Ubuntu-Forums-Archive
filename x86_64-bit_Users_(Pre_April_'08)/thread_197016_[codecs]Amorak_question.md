---
title: "[codecs]Amorak question"
date: 2006-06-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by mwells on 2006-06-15
Hi all!

Just setting up my dapper 64 bit install (running KDE) at the moment, and it seems to be going relatively easily so far . .

I am however running into problems getting amorak to play mp3's, I've read lots about multimedia support in 64bit being lacking, but I cant seem to find any one place that tells me just HOW to achieve it (as i see plenty of people that have)

I always used to use XMMS but could i get this working on 64bit?

Also I was thinking that as I encounter these (probaby easy) problems I may keep a log of them (and the solutions) and start to piece together one of the "Dapper Start up Guides" but for 64bit, as so far my searching seems to of been fruitless . . 

Many thanks

/Matt

---

### Post by th3james on 2006-06-15
Easy Ubuntu and automatix both work with amd64

[Easy Ubuntu]("http://easyubuntu.freecontrib.org/")
[Automatix]("http://ubuntuforums.org/showthread.php?t=185604")

either of these can setup all your codecs, along with some other useful stuff

---

### Post by mwells on 2006-06-15
Thanks a lot for your links!

I tried the easy Ubuntu link first (as i had heard of this before), however it seemed to generate a lot of errors, and unfortunately mp3's still dont seem to work through Amorak.

The errors are below, any ideas?

Thanks again

/Matt

```

apt-get  -o=dir::etc=/home/matthew/easyubuntu/conf -o=dir::etc::sourcelist=sources.list update
apt-get  -o=dir::etc=/home/matthew/easyubuntu/conf -o=dir::etc::sourcelist=sources.list --yes --allow-unauthenticated  install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad libxine-extracodecs libxine-main1 faad sox lame ffmpeg mjpegtools vorbis-tools libxvidcore4 libdvdcss2 timidity timidity-interfaces-extra freepats sun-java5-bin sun-java5-plugin kaffeine-mozilla
echo "sun-java5-jre shared/accepted-sun-dlj-v1-1 boolean true" | debconf-set-selections -
Executing: 
apt-get  -o=dir::etc=/home/matthew/easyubuntu/conf -o=dir::etc::sourcelist=sources.list update
Get: 1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get: 2 http://security.ubuntu.com dapper-security Release [27.0kB]
Get: 3 http://gb.archive.ubuntu.com dapper Release.gpg [189B]
Get: 4 http://gb.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get: 5 http://gb.archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://gb.archive.ubuntu.com dapper Release
Get: 6 http://gb.archive.ubuntu.com dapper-updates Release [27.0kB]
Get: 7 http://security.ubuntu.com dapper-security/main Packages [21.4kB]
Get: 8 http://gb.archive.ubuntu.com dapper-backports Release [19.6kB]
Get: 9 http://security.ubuntu.com dapper-security/restricted Packages [14B]
Get: 10 http://security.ubuntu.com dapper-security/main Sources [5105B]
Hit http://gb.archive.ubuntu.com dapper/main Packages
Get: 11 http://gb.archive.ubuntu.com dapper/restricted Packages [4408B]
Hit http://gb.archive.ubuntu.com dapper/universe Packages
Get: 12 http://gb.archive.ubuntu.com dapper/multiverse Packages [85.8kB]
Get: 13 http://security.ubuntu.com dapper-security/restricted Sources [14B]
Hit http://gb.archive.ubuntu.com dapper/main Sources
Get: 14 http://gb.archive.ubuntu.com dapper/restricted Sources [1478B]
Hit http://gb.archive.ubuntu.com dapper/main Sources
Get: 15 http://gb.archive.ubuntu.com dapper/restricted Sources [1478B]
Hit http://gb.archive.ubuntu.com dapper/universe Sources
Get: 16 http://gb.archive.ubuntu.com dapper/multiverse Sources [46.6kB]
error: 
error: 
bzip2: Compressed file ends unexpectedly;
error: 
	perhaps it is corrupted?  *Possible* reason follows.
error: 
bzip2: Resource temporarily unavailable
Errhttp://gb.archive.ubuntu.com dapper/restricted Sources
  Could not open file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_dapper_restricted_source_Sources - open (2 No such file or directory)
Get: 17 http://gb.archive.ubuntu.com dapper-updates/main Sources [19.6kB]
Get: 18 http://gb.archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get: 19 http://gb.archive.ubuntu.com dapper-backports/main Sources [14B]
Get: 20 http://gb.archive.ubuntu.com dapper-backports/restricted Sources [14B]
Get: 21 http://gb.archive.ubuntu.com dapper-backports/universe Sources [14B]
Get: 22 http://gb.archive.ubuntu.com dapper-backports/multiverse Sources [14B]
error: 
	Input file = (stdin), output file = (stdout)
Fetched 260kB in 1s (141kB/s)
Reading package lists...

error: 
error: 
It is possible that the compressed file(s) have become corrupted.
error: 
You can use the -tvv option to test integrity of such files.
Executing: 
apt-get  -o=dir::etc=/home/matthew/easyubuntu/conf -o=dir::etc::sourcelist=sources.list --yes --allow-unauthenticated  install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad libxine-extracodecs libxine-main1 faad sox lame ffmpeg mjpegtools vorbis-tools libxvidcore4 libdvdcss2 timidity timidity-interfaces-extra freepats sun-java5-bin sun-java5-plugin kaffeine-mozilla
Reading package lists...
Building dependency tree...

error: 
error: 
error: 
error: 
error: 
E: Package libdvdcss2 has no installation candidate
error: 
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
libxine-main1 is already the newest version.
vorbis-tools is already the newest version.
libxvidcore4 is already the newest version.
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
Executing: 
echo "sun-java5-jre shared/accepted-sun-dlj-v1-1 boolean true" | debconf-set-selections -
EasyUbuntu is finished. You may copy this log for debugging purposes.
"sun-java5-jre shared/accepted-sun-dlj-v1-1 boolean true" | debconf-set-selections -
EasyUbuntu is finished. You may copy this log for debugging purposes.
EasyUbuntu is finished. You may copy this log for debugging purposes.
EasyUbuntu is finished. You may copy this log for debugging purposes.

```

---

### Post by Lil_Eagle on 2006-06-15
I have amorak working fine playing mp3s.  I used the 64 bit version of Automatix to install the codecs.  

See this page:

[http://www.ubuntuforums.org/showthread.php?t=185604](http://www.ubuntuforums.org/showthread.php?t=185604)

---

### Post by mwells on 2006-06-15
Well, thanks for all the help but i just noticed the thread currently above this one [http://www.ubuntuforums.org/showthread.php?t=187930]("http://www.ubuntuforums.org/showthread.php?t=187930") which seems to answer my question (that the required codec is not in the repositiories), so I will look at that next time i get a chance!

Thanks again

/Matt

*edit* this did indeed solve my problem *edit*

---

