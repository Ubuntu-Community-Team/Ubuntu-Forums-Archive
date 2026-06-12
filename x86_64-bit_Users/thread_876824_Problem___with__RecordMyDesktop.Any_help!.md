---
title: "Problem   with  RecordMyDesktop.Any help!?"
date: 2008-08-01
forum: x86 64-bit Users
---

### Post by radopenev on 2008-08-01
Hi everybody!
Thanks to the deb for Dapper from 
[http://ubuntuforums.org/showthread.php?t=294605&highlight=recordmydesktop](http://ubuntuforums.org/showthread.php?t=294605&highlight=recordmydesktop)

and
 
sudo dpkg -i --force-architecture recordmydesktop_0.3.1-1_i386.deb
sudo dpkg -i --force-architecture gtk-recordmydesktop_0.3.1-1_i386.deb

it seems to install without any problems (no error mess...).Bin-file:

/usr/bin/recordmybesktop
After running in terminal :
$recordmybesktop
recordmydesktop: error while loading shared libraries: libvorbisenc.so.2: cannot open shared object file: No such file or directory

Thanks to Cappy :[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
$getlibs recordmydesktop
Not able to connect to [http://packages.ubuntu.com](http://packages.ubuntu.com) to find package name
No match for libvorbisenc.so.2
Not able to connect to [http://packages.ubuntu.com](http://packages.ubuntu.com) to find package name
No match for libvorbisfile.so.3
Not able to connect to [http://packages.ubuntu.com](http://packages.ubuntu.com) to find package name
No match for libXdamage.so.1

But I see there are correctly installed :
/usr/lib/libvorbisenc.so.2-------link to ------/usr/lib/libvorbisenc.so.2.0.2
/usr/lib/libvorbisfile.so.3-------link to ------/usr/lib/libvorbisenc.so.3.1.1
/usr/lib/libXdamage.so.1-------link to ------/usr/lib/libXdamage.so.1.0.0
it's the same for /usr/lib32  and  /usr/lib64

Yes, I know and agree ...my Ubuntu is too old!
Many thanks for any help!:)

---

### Post by Kilz on 2008-08-01
> **radopenev said:**
> Hi everybody!
Thanks to the deb for Dapper from 
[http://ubuntuforums.org/showthread.php?t=294605&highlight=recordmydesktop](http://ubuntuforums.org/showthread.php?t=294605&highlight=recordmydesktop)

and
 
sudo dpkg -i --force-architecture recordmydesktop_0.3.1-1_i386.deb
sudo dpkg -i --force-architecture gtk-recordmydesktop_0.3.1-1_i386.deb

it seems to install without any problems (no error mess...).Bin-file:

/usr/bin/recordmybesktop
After running in terminal :
$recordmybesktop
recordmydesktop: error while loading shared libraries: libvorbisenc.so.2: cannot open shared object file: No such file or directory

Thanks to Cappy :[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
$getlibs recordmydesktop
Not able to connect to [http://packages.ubuntu.com](http://packages.ubuntu.com) to find package name
No match for libvorbisenc.so.2
Not able to connect to [http://packages.ubuntu.com](http://packages.ubuntu.com) to find package name
No match for libvorbisfile.so.3
Not able to connect to [http://packages.ubuntu.com](http://packages.ubuntu.com) to find package name
No match for libXdamage.so.1

But I see there are correctly installed :
/usr/lib/libvorbisenc.so.2-------link to ------/usr/lib/libvorbisenc.so.2.0.2
/usr/lib/libvorbisfile.so.3-------link to ------/usr/lib/libvorbisenc.so.3.1.1
/usr/lib/libXdamage.so.1-------link to ------/usr/lib/libXdamage.so.1.0.0
it's the same for /usr/lib32  and  /usr/lib64

Yes, I know and agree ...my Ubuntu is too old!
Many thanks for any help!:)

You have force in a 32bit application, it needs 32bit libraries. Libraries in /usr/lib/ are 64bit. Never force in libraries. Use getlibs. But it is entirly possible that the libraries didnt exist in Dapper or the ones installed are to old for the application you forced in. [Look here to search for them. ]("http://packages.ubuntu.com/")

---

### Post by radopenev on 2008-08-01
Thank you Kilz!
I love Dapper...but it's time to upgrade

---

