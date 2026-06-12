---
title: "Amazon mp3 downloader"
date: 2009-08-15
forum: x86 64-bit Users
---

### Post by schpunty on 2009-08-15
Anybody have any ideas as to how to get the Amazon mp3 downloader working in 64bit?
It won't install because it sees the 64 bit system.
Any help greatly appreciated!

---

### Post by Yellow Pasque on 2009-08-15
[http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

---

### Post by Yellow Pasque on 2009-08-15
On second thought, I gave the actual amazonmp3 downloader a shot.

It wasn't that hard to install with the use of getlibs ( [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) ). I'm not sure if the first command is necessary (it installs 64-bit libraries, which this program ultimately doesn't use), but it should make life easier as far as the .deb dependencies.

```
sudo apt-get install libgtkmm-2.4-1c2a libboost-thread1.34.1 libboost-iostreams1.34.1 libboost-signals1.34.1 libboost-date-time1.34.1 libcurl3 libssl0.9.8 xdg-utils
cd <WHEREVER YOU SAVED THE .DEB>
sudo dpkg -i --force-architecture amazonmp3.deb
sudo getlibs /usr/bin/amazonmp3
```

---

### Post by schpunty on 2009-09-11
Okay, I'm back and feeling incredibly stupid.
First and foremost, thanks for your time and help.
My guess is that I need to run the code you're including above and then after that is installed, then download and install the MP3 downloader.
Did I get it right?
Thanks again, the help is greatly appreciated!

---

