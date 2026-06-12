---
title: "Gstreamer Problems"
date: 2007-02-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by xeocub on 2007-02-24
Hello all, first time here and just finished the base install of Ubuntu (new to this). 

I've been trying to get all my files to work, be it video, mp3s etc.. basically the same problem that many other people are having when switching from windows over to *nix. I've read up on it, and everything has failed so far for (to me) unexplainable reasons. 

For example the instructions followed in:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) 
did not work for me, because apparently those packages don't exist..

"E: Couldn't find package gstreamer0.10-pitfdll" for example

I've done some more poking around, and have been trying to install gstreamer by itself, and then the lib packages.. after getting all the Dev tools, I was finally able to compile gstreamer.

Now, when I attempt to compile the "Good the bad and the ugly" packages, it gives me an error stating that gstreamer could not be found, read: it hasn't been installed.

After some further search, I realized that the ./configure was attempting to find gstreamer in the /usr/lib folder, while gstreamer was installed into the /usr/lib64 folder...

So it looked like a 64 bit problem, and I did some more searching and finally gave up after reading a few posts about the horrid problems with the amd64 Ubuntu edition..

What should I do? Will I only be able to get full support if I switch to the 32bit version?

Cheers

Ulrich

---

### Post by xeocub on 2007-02-24
Fixed. I merely didn't have the synaptic Package manager set to include multiverse and universe repositories. 

Now the only thing remaining is mounting my existing ntfs windows raid0 setup so I can get at all my files!

---

### Post by John.Michael.Kane on 2007-02-24
Frist make sure all the repos enabled.You can uncomment the lines running the command listed.
```
sudo gedit /etc/apt/sources.list 
``` you should see a few lines with # next to it remove that symbol.

save the file,and run 

```
sudo aptitude update
```


Next up installing the files you want.

Run the command listed:
```
sudo aptitude install totem-xine acidrip brasero libdvdread3 gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui 

```

After that.

Run this:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

You should now have dvd playback.

Note: if playback has issues you can try installing vlc
```
sudo aptitude install vlc
```

Options for mounting windows partitions:

[** Mounting Windows Partitions in Ubuntu**]("http://www.psychocats.net/ubuntu/mountwindows")

[**ntfs-3g how to**]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntsf-3g")


Hope this helps.

---

### Post by JimmyME on 2007-02-24
SD,

Thank you!

I now have Sound Juicer working for MP3s and DVDs playing.

Thanks for the info!

JimmyME

---

### Post by John.Michael.Kane on 2007-02-24
JimmyME no problem glad it help.

---

### Post by xeocub on 2007-02-24
Howdy.. and thanks for the info too!

The only files that do not seem to work now are .wmv files. I thought gstream would have them included in the "ugly" package?

Mounting my NTFS drive was possible as read only after a long time... now I'm trying to get ntsf-3g to work. So far in vain..

---

### Post by John.Michael.Kane on 2007-02-24
you try installing vlc to test if it can read .wmv files.

As for ntsf-3g you can give this how to a look over.[**ntfs-3g how to**]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntsf-3g")

---

### Post by capecove on 2007-06-06
This really came through, thanks for all the help! Now, onto James Bond...:popcorn:

---

