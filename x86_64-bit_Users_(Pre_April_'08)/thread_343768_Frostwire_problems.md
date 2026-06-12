---
title: "Frostwire problems"
date: 2007-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by greyghostx on 2007-01-22
If there are any 64 bit frostwire setup walkthroughs please direct me, I've been searching the forums for awhile now. If not here's my problem.

greyghost@Owner:~/Desktop$ sudo dpkg --force-architecture -i frostwire-4.13.1.5.i586.deb
Password:
(Reading database ... 70791 files and directories currently installed.)
Unpacking frostwire (from frostwire-4.13.1.5.i586.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing frostwire-4.13.1.5.i586.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/frostwire/daap.jar')
Errors were encountered while processing:
 frostwire-4.13.1.5.i586.deb

---

### Post by cmost on 2007-01-22
Use Automatix2 to install Frostwire.  (The instructions for using this are everywhere in these forums.  Search for details.)  Then; if you're using Beryl or Compiz, you'll need to launch it with a little script in order to get  to run without displaying a blank window.  Here's the code:

Create a file named: launch_frostwire_Beryl
File contents (paste in the following:)
#!/bin/bash
export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost
/usr/bin/frostwire

NOTE:  You may need to change the location of the binary if you installed with Automatix2 (might be something like /opt/frostwire/runFrostwire.sh)  Just modify the script according to your specific case.

Save the file;
Right-click --> properties --> permissions --> tick the box for executable.

Run the file to launch Frostwire!

Enjoy!

---

### Post by jamesford on 2007-01-22
works for me without --force-architecture, always has, just double clicking it

---

