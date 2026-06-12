---
title: "FIX:  k3b requires cdrdao"
date: 2004-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by jsubl2 on 2004-10-13
k3b from universe does not work becuase cdrdao is missing.

apt-get source --build cdrtools
install the debs from this build
apt-get source --build cdrdao

you may have to apt-get install missing dependencies.  This worked for me I hope it helps someone.

---

### Post by goatboy on 2004-10-14
[quote=jsubl2]you may have to apt-get install missing dependencies.  This worked for me I hope it helps someone.[/quote]
If you "apt-get build-dep cdrdao" first it should grab everything you need automatically.

---

### Post by smoothrt on 2004-10-21
I tried this and got:

ross@demo:~ $ sudo apt-get source --build cdrtools
Reading Package Lists... Done
Building Dependency Tree... Done
Need to get 1811kB of source archives.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main cdrtools 4:2.0+a30.pre1-1ubuntu2 (dsc) [763B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main cdrtools 4:2.0+a30.pre1-1ubuntu2 (tar) [1704kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main cdrtools 4:2.0+a30.pre1-1ubuntu2 (diff) [106kB]
Fetched 3B in 0s (7B/s)
Skipping unpack of already unpacked source in cdrtools-2.0+a30.pre1
dpkg-buildpackage: source package is cdrtools
dpkg-buildpackage: source version is 4:2.0+a30.pre1-1ubuntu2
dpkg-buildpackage: source maintainer is Matt Zimmerman &lt;mdz@canonical.com&gt;
dpkg-buildpackage: host architecture is amd64
dpkg-checkbuilddeps: Unmet build dependencies: smake dpatch
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
Build command 'cd cdrtools-2.0+a30.pre1 &amp;&amp; dpkg-buildpackage -b -uc' failed.
E: Child process failed

Similar child error with the other command.  Can anoyone help, this cdrdao error is very frustrating.

---

### Post by K6-III on 2004-10-21
Use synaptic to install smake and dpatch and try again.

---

### Post by smoothrt on 2004-10-27
I used synaptic to install smake and dpatch, and got the following error message during the sudo apt-get source --build cdrtools.

dh_testdir
/usr/bin/make
make[1]: Entering directory `/home/ross/cdrdao-1.1.9'
/usr/bin/make  all-recursive
make[2]: Entering directory `/home/ross/cdrdao-1.1.9'
Making all in scsilib
make[3]: Entering directory `/home/ross/cdrdao-1.1.9/scsilib'
RULES/rules1.top:234: incs/Dcc.x86_64-linux: No such file or directory
RULES/rules.top:39: RULES/x86_64-linux-cc.rul: No such file or directory
RULES/rules.cnf:56: incs/x86_64-linux-cc/Inull: No such file or directory
RULES/rules.cnf:57: incs/x86_64-linux-cc/rules.cnf: No such file or directory
Makefile:18: warning: overriding commands for target `install'
RULES/rules1.dir:27: warning: ignoring old commands for target `install'
p incs/x86_64-linux-cc
make[3]: p: Command not found
make[3]: [incs/x86_64-linux-cc/Inull] Error 127 (ignored)
/bin/sh: line 1: incs/x86_64-linux-cc/Inull: No such file or directory
make[3]: *** [incs/x86_64-linux-cc/Inull] Error 1
make[3]: Leaving directory `/home/ross/cdrdao-1.1.9/scsilib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ross/cdrdao-1.1.9'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/ross/cdrdao-1.1.9'
make: *** [debian/build-stamp] Error 2
Build command 'cd cdrdao-1.1.9 && dpkg-buildpackage -b -uc' failed.
E: Child process failed

Any further suggestions on what I can try to get this working?

---

### Post by polka2038 on 2004-11-29
I build this package last week : 
in cdrdao-1.1.9/scsilib/RULES directory :
I duplicated i386-linux-cc.rul in x86_64-linux-cc.rul

I forgot, if I did other things.

Regards

---

### Post by agsansoo on 2004-12-22
OK .... I had the same problems ... no cd burning software, no xmms, etc ....
So I decided to CHEAT !!! LOL

commented out all of Ubuntu's repositories and added

pure64/dists/sid

contrib
main
non-free 

Now all my programs are available ...   :D  :D  :D 

If you want the exact link, let me know ?

If you think this wasn't a good idea, let me know why ?

---

### Post by HankB on 2004-12-30
[QUOTE=jsubl2]k3b from universe does not work becuase cdrdao is missing.

apt-get source --build cdrtools
install the debs from this build
apt-get source --build cdrdao

you may have to apt-get install missing dependencies.  This worked for me I hope it helps someone.[/QUOTE]

The first two parts seemed to work find but trying to make cdrdao still winds up with: 
root@toonsinator:~ # cd cdrdao-1.1.9/
root@toonsinator:~/cdrdao-1.1.9 # make
make  all-recursive
make[1]: Entering directory `/root/cdrdao-1.1.9'
Making all in scsilib
make[2]: Entering directory `/root/cdrdao-1.1.9/scsilib'
RULES/rules1.top:234: incs/Dcc.x86_64-linux: No such file or directory
RULES/rules.top:39: RULES/x86_64-linux-cc.rul: No such file or directory
RULES/rules.cnf:56: incs/x86_64-linux-cc/Inull: No such file or directory
RULES/rules.cnf:57: incs/x86_64-linux-cc/rules.cnf: No such file or directory
Makefile:18: warning: overriding commands for target `install'
RULES/rules1.dir:27: warning: ignoring old commands for target `install'
p incs/x86_64-linux-cc
make[2]: p: Command not found
make[2]: [incs/x86_64-linux-cc/Inull] Error 127 (ignored)
/bin/sh: line 1: incs/x86_64-linux-cc/Inull: No such file or directory
make[2]: *** [incs/x86_64-linux-cc/Inull] Error 1
make[2]: Leaving directory `/root/cdrdao-1.1.9/scsilib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/cdrdao-1.1.9'
make: *** [all] Error 2

---

### Post by LongTooth on 2004-12-31
I've given up on K3B. I've had nothing but trouble with it. On my previous PC it would lock up my machine. I found I could not log back into it. Had to reinstall Ubuntu. There was a post saying just that but did I listen? Oh, no. Had to find out on my own. 

 On my newly built PC I didn't want to go that hassle again. So I installed XCDRoast. And now I'm burnning ISO files. I find XCDRoast somewhat cumbersome to operate but I've just about got it down pat. I think I'll wait untill Hoary is out and see if they've got the K3B problems ironed out before give K3B a try again.

---

### Post by HankB on 2004-12-31
[QUOTE=LongTooth]So I installed XCDRoast. [/QUOTE]

Does that burn DVDs?

What kind of burner do you have and what modules do you load to make it visible? Or did it "just work."

thanks,
hank

---

### Post by LongTooth on 2004-12-31
First of all I used Synaptic to install it. If XCDRoast doesn't 'see' your optical drives when it does a scan, you'll have to manually added them. Not knowing what information to input, I did a cat etc/fstab at the CLI. That gave me these results: 

longtooth@ubuntu:~ $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
longtooth@ubuntu:~ $

Launch XCDRoast. Enter Setup. As you can see from above, I used the designation of /dev/hdd for the CDRom (cdrom0) and /dev/hdc for the burner (cdrom1). If the information is correct, XCDRoast will populate that window with your drives. It will list vendor, type, etc. If not, you have to try another designation. You will also have to list the user permission (you) so you can open it as user rather than root. 

Under the HD Settings tab, you will have add a directory path so the software know where to look for files, ISO, etc, to burn. I made a 'temp' file to store downloaded ISO files to and listed it as /home/longtooth/temp in the HD Setting tab.  

XCDRoast is a recent install and as such I've only burn ISO files. And they are correctly done. I've downloaded, burn and run several live CD distros on a test box to see if they work. They do. I've yet to copy any audio CDs or burn downloaded music files. That is next on the to-do list. This is still a works in progress. 

Can't help you with the DVD question. I don't have one.

Let me emphasize XCDRoast is cumbersome. At least I found it so. You might not. Its not at all friendly. But I am getting the hang of it. I can burn ISO files (and I presume copy audio CDs) so it can't be all that bad. 

One other thing, no icon was put on the menu when installed. I had to put one in by hand. To launch, Alt&F2> Run Application> xcdroast.

---

