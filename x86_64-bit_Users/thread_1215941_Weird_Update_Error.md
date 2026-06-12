---
title: "Weird Update Error"
date: 2009-07-17
forum: x86 64-bit Users
---

### Post by Mangopork on 2009-07-17
I got this message after installing the updates and some canonical software for my system:

"apt-file update needed

You may need to update or create the apt-file cache. Running this command likely needs an active internet connection."

I clicked "take this action now" and the terminal keeps looping failed downloads....


Terminal:

About to execute /usr/share/apt-file/do-apt-file-update.
This command needs root privileges to be executed.
Using sudo...
Enter mangopork password at prompt.
Calculating old sha1sum...
Downloading Index [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Contents-amd64.diff/Index:](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Contents-amd64.diff/Index:)
curl: (22) The requested URL returned error: 404
Download of [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Contents-amd64.diff/Index](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Contents-amd64.diff/Index) failed
Command exited with code 22

Downloading complete file [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Contents-amd64.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Contents-amd64.gz)



It's able to download the amd64.gz, but not the "diff" file.

Help!

---

### Post by psycho5 on 2009-07-18
I think what you are describing is a reported bug, [https://bugs.launchpad.net/debian/+source/apt-file/+bug/220396](https://bugs.launchpad.net/debian/+source/apt-file/+bug/220396) but I may be mistaken.

---

