---
title: "[HOWTO] Set up a 32 bit chroot to work seamlessly (for Hardy, and probably Gutsy)"
date: 2008-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by jhnphm on 2008-03-24
WIth Hardy, I've noticed that some pixmaps don't load correctly on the 32 bit version of Firefox 3 (window icon missing), or for any window icons for any other GTK app (ia32-libs is broken or something). Therefore I decided to set up a chroot environment to run everything in, which also allows me to apt-get 32 bit applications and easily install 32 bit debs. The advantage is that everything is tracked by some package manager somewhere, no forcing package installs is required, and you get an environment for compiling 32 bit stuff. This solves all 32 bit compatibility problems, with the caveats below:

The limitations of this is that apps inside the chroot won't be able to read fuse-mounted filesystems mounted in locations in /home, since bindmounts won't transfer the fuse-mounts under them [EDIT]Fixed, see [http://ubuntuforums.org/showpost.php?p=4625551&postcount=7](http://ubuntuforums.org/showpost.php?p=4625551&postcount=7)[/EDIT]. Also, I don't know how to call 64 bit applications from a 32 bit application inside a chroot, other than chrooting back into the root 64-bit install, which is a PITA due to the number of launch scripts required. This is a problem when one wants to open something with Firefox. If anybody knows how to fix these please post.

I've created an _[ubuntu blueprint](https://wiki.ubuntu.com/BluePrints/32BitChroot)_ and proposal for this, but until then, here's how I went about it:

**Step 1: Setup chroot**
First, make sure you have all the 3rd party apt sources such as mediubuntu you want set up in sources.list. You need to have both cdebootstrap and schroot installed. As root, make an empty directory at /var/lib/chroot, and cd into it. From there, run 'cdebootstrap -a i386 lenny ubuntu32' and wait for it to complete the base install. Next, 'cp -r /etc/apt ubuntu32/etc' to copy the base install's apt sources over. Then 'chroot /var/lib/chroot/ubuntu32', run apt-get update and apt-get upgrade inside the chroot, and exit.

**Step 2: Setup bindmounts**
Append this to /etc/fstab in your root installation.
```

##chroot
/home             /var/lib/chroot/ubuntu32/home           none    rbind          0          0
/dev              /var/lib/chroot/ubuntu32/dev            none    rbind          0          0
/etc              /var/lib/chroot/ubuntu32/etc/.root      none    bind           0          0
/proc             /var/lib/chroot/ubuntu32/proc           none    rbind          0          0
/media            /var/lib/chroot/ubuntu32/media          none    rbind          0          0
/mnt              /var/lib/chroot/ubuntu32/mnt            none    rbind          0          0
/tmp              /var/lib/chroot/ubuntu32/tmp            none    rbind          0          0

```

Next, run 'mount -a' to mount all of these, and again 'chroot /var/lib/chroot/ubuntu32'. Then symlink the following files in /etc/.root to /etc (from inside the chroot). Then exit the chroot
```

hosts
passwd
shadow
group
gshadow
hosts.allow
hosts.deny
resolv.conf

```
**Step 3: Setup schroot**
'apt-get install schroot' and add this to your /etc/schroot/schroot.conf, making the appropriate substitution for the username
```


[ubuntu32]
aliases=default
type=plain
location=/var/lib/chroot/ubuntu32
priority=3
users=username1,username2,username3,...
run-setup-scripts=false
personality=linux32


```

To enter the chroot as a normal user, do 'schroot -p' . To execute a command from the chroot, do 'schroot -p [command]'. To enter the chroot as root, do 'schroot -p -u root'. To execute something in the chroot as root, 'schroot -p -u root [command]'. 

**Step 4: Install packages within chroot**

Now, apt-get synaptic to install the GUI package manager, if you need it (aptitude should already be in the chroot). Obviously, if you want to be running a 32 bit chroot, you probably have 3rd party 32 bit only applications you want to run, so add those to /etc/apt/sources.list as you would on a 32 bit system from the command line. Then run either synaptic or aptitude and select the packages you need. To install loose packages, copy them to /tmp in the base install, and 'dpkg -i' them in /tmp from the chroot. The easiest way would be to simply install ubuntu-desktop and the packages needed on top of that, such as skype or acroread or java and whatnot.

**Step 5: Integration**
Now create launch scripts to start the app from the chroot. Assuming you want to use a 32 bit firefox by default, create a file in /usr/local/bin/firefox and make it's contents this and make it executable:
```

#! /bin/sh
COMMAND=`basename $0`
USERS=`schroot -i ubuntu32|grep '  Users'|awk '{print substr($0,index($0,$2))}'`
USECHROOT=0
for F in $USERS; do
    if [ $F = $USER ]; then
        USECHROOT=1
        break
    fi  
done
if [ $USECHROOT -eq 0 ];then
    for F in $GROUPS; do
        for G in `groups`; do
            if [ $G = $F ]; then
                USECHROOT=1
                break
            fi  
        done
    done
fi

if [ $USECHROOT -eq 1 ];then
    schroot -c ubuntu32 -p $COMMAND "$@"
else
#if no permissions to run apps inside the chroot, run 64 bit version
    /usr/bin/$COMMAND "$@"
fi

```
Copy or symlink the script to /usr/local/bin/skype, /usr/local/bin/acroread, /usr/local/bin/opera, etc for your other executables you want to run from the chroot. Also copy or symlink the .desktop files for the relevant applications from /var/lib/chroot/ubuntu32/usr/share/applications to /usr/local/share/applications.

That should be it, and you should be able to launch the 32 bit apps from the application menu or the command line

---

### Post by jhnphm on 2008-03-24
Correction to the launcher script, it should be:
```
#! /bin/sh
COMMAND=`basename $0`
USERS=`schroot -i ubuntu32|grep '  Users'|awk '{print substr($0,index($0,$2))}'`
USECHROOT=0
for F in $USERS; do
    if [ $F = $USER ]; then
        USECHROOT=1
        break
    fi  
done
if [ $USECHROOT -eq 0 ];then
    for F in $GROUPS; do
        for G in `groups`; do
            if [ $G = $F ]; then
                USECHROOT=1
                break
            fi
        done
    done
fi

if [ $USECHROOT -eq 1 ];then
    schroot -c ubuntu32 -p $COMMAND -- "$@"
else
#if no permissions to run apps inside the chroot, run 64 bit version
    /usr/bin/$COMMAND "$@"
fi
```


Note the two dashes

---

### Post by jhnphm on 2008-03-24
How does one edit a thread title? Some people might not know what a chroot is good for (although they should if they're using Ubuntu x64)

---

### Post by Kilz on 2008-03-24
> **jhnphm said:**
> How does one edit a thread title? Some people might not know what a chroot is good for (although they should if they're using Ubuntu x64)

You cant edit a threads title. 
The use of chroots has gone down after Breezy. Because its possible to install 32bit applications to the 64bit version from Dapper on up. Your work around is only applicable to Hardy, Gutsy doesn't have these issues. Did you file a bug report on the problem in launchpad?
Secondly, the fix, installing the 32bit gtk files is probably less work than setting up a chroot. Getlibs should install 32bit packages to the 64bit version without taking up all the space a chroot does.
Lastly, why were you installing 32bit firefox?

---

### Post by jhnphm on 2008-03-24
> **Kilz said:**
> You cant edit a threads title. 
The use of chroots has gone down after Breezy. Because its possible to install 32bit applications to the 64bit version from Dapper on up. Your work around is only applicable to Hardy, Gutsy doesn't have these issues. Did you file a bug report on the problem in launchpad?
Secondly, the fix, installing the 32bit gtk files is probably less work than setting up a chroot. Getlibs should install 32bit packages to the 64bit version without taking up all the space a chroot does.

Yeah, I did file a bug report- the problem seemed to be that the version in ia32-libs would look at /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm and fail before looking at /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so. Haven't tried taking apart the 32 bit gtk package and dumping the files in lib32, or using getlibs, (I don't like leaving anything in /usr other than /usr/local not under package management), since I was under the impression the problem was with paths compiled into GTK and that the version of gtk in ia32-libs is the same as the deb for i386.

I also find it preferable to have everything under package management, apt-gettable and most importantly easily kept up to date. AFAIK from skimming the script, getlibs just repackages loose i386 debs and moves /usr/lib to /usr/lib32 removing other files to prevent conflicts. Easier to use a solution that fixes everything rather than fixing problems piecemeal (and since the chroot is on a seperate partition, it'll survive upgrades, reformats, etc.). Also I encountered a file that mplayer64 wouldn't play but mplayer32 did due to a missing codec in w64codecs- [http://download.microsoft.com/download/4/8/b/48bd7a96-b1c6-4bf4-a251-359359a382d7/HaloWarsCannedDemo_RatedRP_720p59.94_6500kbps.wmv](http://download.microsoft.com/download/4/8/b/48bd7a96-b1c6-4bf4-a251-359359a382d7/HaloWarsCannedDemo_RatedRP_720p59.94_6500kbps.wmv)

I was using 32 bit firefox since I needed stable Java support and nspluginwrapper is broken for flash r115 [https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/177856](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/177856).

---

### Post by Kilz on 2008-03-24
> **jhnphm said:**
> Yeah, I did file a bug report- the problem seemed to be that the version in ia32-libs would look at /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm and fail before looking at /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so. Haven't tried taking apart the 32 bit gtk package and dumping the files in lib32, or using getlibs, (I don't like leaving anything in /usr other than /usr/local not under package management), since I was under the impression the problem was with paths compiled into GTK and that the version of gtk in ia32-libs is the same as the deb for i386.

I also find it preferable to have everything under package management, apt-gettable and most importantly easily kept up to date. AFAIK from skimming the script, getlibs just repackages loose i386 debs and moves /usr/lib to /usr/lib32 removing other files to prevent conflicts. Easier to use a solution that fixes everything rather than fixing problems piecemeal (and since the chroot is on a seperate partition, it'll survive upgrades, reformats, etc.). Also I encountered a file that mplayer64 wouldn't play but mplayer32 did due to a missing codec in w64codecs- [http://download.microsoft.com/download/4/8/b/48bd7a96-b1c6-4bf4-a251-359359a382d7/HaloWarsCannedDemo_RatedRP_720p59.94_6500kbps.wmv](http://download.microsoft.com/download/4/8/b/48bd7a96-b1c6-4bf4-a251-359359a382d7/HaloWarsCannedDemo_RatedRP_720p59.94_6500kbps.wmv)

I was using 32 bit firefox since I needed stable Java support and nspluginwrapper is broken for flash r115 [https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/177856](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/177856).

But chroots are difficult to setup, and take up a lot of hard drive space. Good luck with it.

---

### Post by jhnphm on 2008-03-31
Figured out how to make fuse mounts show up in the chroot after posting on the fuse-devel list:

Add the following lines into /etc/rc.local (the root installation)
```

mount --make-rshared /
mount /var/lib/chroot/ubuntu32/home

```
"noauto" has to be under the options column in /etc/fstab.

---

### Post by Kapitan on 2008-04-23
I'm interested in this, cause
i have to work with a 32 bit only
library and i have to download
the 32 bit version of libglut,
libGL etc etc.

At first i tougth to chroot, then
i've red the post about lib32.

But how can i apt-get a 32 library?
With the -arch option? Will this copy
that lib directly in /usr/lib32?

---

### Post by Kilz on 2008-04-23
> **Kapitan said:**
> I'm interested in this, cause
i have to work with a 32 bit only
library and i have to download
the 32 bit version of libglut,
libGL etc etc.

At first i tougth to chroot, then
i've red the post about lib32.

But how can i apt-get a 32 library?
With the -arch option? Will this copy
that lib directly in /usr/lib32?

The solution is [Getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs"). With it you can install 32bit libs to your 64bit install without a chroot.

---

### Post by Kapitan on 2008-05-04
thanks, getlibs works great. but now i have another question about ld, but i'll open a new post.

---

### Post by sipickles on 2008-05-13
Hi,

after following the instructions I got this far before getting an error:

simon@simon-ubuntu:/var/lib/chroot$ sudo mount -a
mount: mount point /var/lib/chroot/ubuntu32/etc/.root does not exist

Did I miss something?

Thanks

Si

---

### Post by rleigh-debian on 2008-07-05
Some comments on the original post.  The current schroot (1.2.0 and above) have some new features which remove the need for much of the configuration.  Additionally, some of the recommendations are rather sub-optimal; I've suggested how to rectify these.

* No extra mounts and bindmounts in [FONT="Lucida Console"]/etc/fstab[/FONT].
  With all but the "plain" chroot type, this is all automatic (it uses the FSTAB file specified in script-config, defaulting to [FONT="Lucida Console"]/etc/schroot/mount-defaults[/FONT]):

[FONT="Lucida Console"]% **cat /etc/schroot/mount-defaults**
# mount.defaults: static file system information for chroots.
# Note that the mount point will be prefixed by the chroot path
# (CHROOT_PATH)
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/pts        /dev/pts        none    rw,bind         0       0
tmpfs           /dev/shm        tmpfs   defaults        0       0
/home           /home           none    rw,bind         0       0
/tmp            /tmp            none    rw,bind         0       0[/FONT]

You can obviously add more and change it as you like.  Suggestions for improvements are always welcome.

* "symlink the following files in [FONT="Lucida Console"]/etc/.root[/FONT] to [FONT="Lucida Console"]/etc[/FONT] (from inside the chroot)."
  Yech, I don't know where that came from, but it's never been necessary.  Most of those files are already copied in on chroot session startup, which you have disabled--there's no need to make things this complex!  It's also unsafe, because the host's /etc can be purged from the chroot--it's an accident waiting to happen...  Additionally, you can now customise it simply by editing COPYFILES in script-config, which defaults to a file list in [FONT="Lucida Console"]/etc/schroot/copyfiles-defaults[/FONT]:

[FONT="Lucida Console"]% **cat /etc/schroot/copyfiles-defaults**
/etc/group
/etc/hosts
/etc/passwd
/etc/resolv.conf
/etc/shadow[/FONT]

Again, suggestions for improvement are welcome.  For example, you are adding [FONT="Lucida Console"]/etc/(gshadow|hosts.allow|hosts.deny)[/FONT], which I would have added had it been suggested.

* "type=plain"
  You almost never want this; this is a minimal chroot, using this with schroot is equivalent to "[FONT="Lucida Console"]**sudo chroot /some/where**[/FONT]".  Set it to "directory", and enable running of setup scripts, and you'll get all the nice features mentioned above.

* "run-setup-scripts=false"
  Set this to "true", or the scripts won't run!  Enable exec scripts as well while you're at it.


I hope this is useful.  As upstream and Debian maintainer for schroot, I would like to make it as user-friendly and simple as possible to set up and use.  Please do tell us what's missing, either by mail to buildd-tools-devel at lists.alioth.debian.org or as wishlist bug reports in the Debian BTS, and we'll do our best to improve things!


Regards,
Roger

---

