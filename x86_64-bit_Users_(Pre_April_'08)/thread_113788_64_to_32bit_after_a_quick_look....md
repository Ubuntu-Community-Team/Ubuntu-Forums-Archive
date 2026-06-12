---
title: "64 to 32bit after a quick look..."
date: 2006-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by handy on 2006-01-07
I've just installed 32bit Breezy, (last night / early this morning).  After only ever having used 64bit, for a month or so) I thought I'd have a look at the 32bit distro'. 

What follows is very much first impressions at this early stage.

It all started when I followed the Firefox upgrade wiki, here:

[https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29)

I don't believe I made any typo's, but I lost Firefox completely!  

I wasn't happy with my very recent (forced 64bit) Wine install,  due to having made the mistake of installing IE6, which due to it's glorious code, causes display aberrations when DVDShrink is run?!?

So, I decided to look at the 32bit Breezy, I installed from a Ubuntu install CD which only arrived a couple of days ago in the snail mail.  I backed up copy's of my /etc/fstab, /etc/X11/xorg.conf, /etc/modprobe.d/aliases, these were all files that I had modified.  I copied /home/handy/ as well.  These files all went onto the fat32 partition.

The initial install went perfectly, then I had to start organising things the way I like them.  In doing so I noticed that there are quite a few more files available in the Menu:  Applications/Add Applications program.  To be expected.

I had to turn off IPv6 in Firefox & /etc/modprobe.d/aliases, or internet does NOT work.  Then make sure connection settings is DHCP not Static IP Address ('cause I don't have one, so changing servers is slow if not set to DHCP.

& do the following to be able to access repostitories?!?  This must be caused by some strange quirk bought about by my router?  In 64 or 32bit Breezy, without the following changes, NO repository access!

Courtesy of Python  :KS 
****************************************************************
Go to Menu:  SYSTEM /ADMINISTRATION/NETWORKING (you will need your password)

Then go to the DNS tab (probably 192.168.blah.blah as entry)

Find out your ISPs DNS nameservers, for example, Tiscali is 212.74.112.66 and 212.74.112.67.

Enter those bad boys in. Take 192.168.blah.blah OUT!


Then go to /etc/resolv.conf
Make sure that these two entries are there:

nameserver 212.74.112.66
nameserver 212.74.112.67

Your ISPs nameservers replacing mine ;-P
Nameserver 192.168.blah.blah should either be commented out (preceded with a #) or not be there at all.



Finally, go to /etc/dhcp3/dhclient-script and comment out this:

# Modified for Debian. Matt Zimmerman and Eloy Paris, December 2003

# The alias handling in here probably still sucks. -mdz

#make_resolv_conf() {
# if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then
# local new_resolv_conf=/etc/resolv.conf.dhclient-new
# rm -f $new_resolv_conf
#
# if [ -n "$new_domain_name" ]; then
# echo search $new_domain_name >> $new_resolv_conf
# else # keep 'old' search/domain scope
# egrep -i '^ *[:space:]*(search|domain)' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
#
# if [ -n "$new_domain_name_servers" ]; then
# for nameserver in $new_domain_name_servers; do
# echo nameserver $nameserver >>$new_resolv_conf
# done
# else # keep 'old' nameservers
# egrep -i '^ *[:space:]*nameserver' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
#
# chown --reference=/etc/resolv.conf $new_resolv_conf
# chmod --reference=/etc/resolv.conf $new_resolv_conf
# mv $new_resolv_conf /etc/resolv.conf
# fi
#}

***************************************************************
After turning on all repositories & updating the system, adding & removing a few things along the way.  I installed Automatix, see here:

[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

I then installed most of the selections presented by Automatix, but not all.  I was impressed with how many more of the chosen selections actually installed this time on 32bit.  Mixed feelings there.  (The Firefox v1.5 upgrade did not install even though it was selected?  I am still wary of the effect following the wiki might have on my machine... Not again...)

I also included Wine for installation via Automatix, no prob's in 32bit, after Automatix had finished (a couple of hours on my 512kb connection) I downloaded & installed WineTools, using it to setup Wine.  Making sure NOT to install IE6 this time, even though other parts of the windoze sytem that were installed complained about IE6 not being there.

I then installed DVD shrink v3.2, without any dramas.  I then backed up one of my DVD's at the same speed as if it was done in the native XP OS. :KS :KS :KS  I was very happy about that.

Wanted to burn the backed up DVD, downloaded & installed NeroLINUX v2.0.0.4, it works like a dream.  Picks the speed of the DVD media automatically, tested on 4x & 8x disks, burns at those speeds, burns DVD backups stored on fat32 & ntfs partitions.  Burns multi-session disks too. I will pay $20- U.S. for this software.

I installed the nVidia (c) drivers through Automatix too, painless.

I don't really notice any decrease in speed at this point.  I haven't had the stop watch out, If I don't notice it that's good enough.

I haven't installed UT2K4, that will be a good test, seeing as it takes advantage of 64bit, will it bypass the 32bit OS anyway?

Glxgears is as fast in  32 as 64bit, I guess the GPU is in control here.

I had to work hard to get sound working in 64bit Breezy, in 32bit it just worked  :rolleyes: 

Overall I'm happier in 32bit, I can do everything that I want to do in Ubuntu now, I will only boot into xp, when I have to for work.

I look forward to Dapper 64bit, but the thing  that I have to be sure not to loose sight of here is that most problems with 64bit Ubuntu, are not Ubuntu's fault.  We are at    the beginning of the transition from 32 to 64bit, I've seen the 16 to 32bit transition, it takes a while for these things to happen.  Patience is so valuable, especially with computers.  We can think things are changing too slow, when in fact it is the opposite.  :confused: 

I will stay in 32bit untill I can run DVDshrink , & NeroLINUX on 64bit as well as they run on 32.  For all I know NeroLINUX allready does run on 64bit?

I might try & make Guild Wars work under Wine, while I'm watching the world change before my very eyes. :KS 

handy

---

### Post by handy on 2006-01-08
I installed UT2K4 last night & gave it a good workout, both with bots & on the net.

Fantastic, it probably seemed faster due to my installing the latest 3369.2 patch, the new patch makes it sound better too. :KS   Anyone running UT2K4 really should install the patch, it's roughly 22Mb in size.

There was not ANY kind of a problem, fast as can be, smooth as silk, even in very busy circumstances.

Running at 1600x1200 24bit res' with everything turned on to the max in system setup.

I expect the UT2K4 install was 64bit, anyway, so this isn't any kind of benchmark for 32 against 64bit.

Just sharing my enthusiasm.

handy

---

