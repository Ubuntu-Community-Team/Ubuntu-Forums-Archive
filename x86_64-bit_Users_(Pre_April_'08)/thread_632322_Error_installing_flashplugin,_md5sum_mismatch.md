---
title: "Error installing flashplugin, md5sum mismatch"
date: 2007-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by dandandan on 2007-12-05
Hello

I installed Ubuntu 64bit today, when installing flashplugin-nonfree i get the following error.
I tried --purge and reinstall already, as suggested in other threads, no effect.

Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
....
....
.....
 2800K .......... .......... .......... .......... .......... 96%  711.77 KB/s
 2850K .......... .......... .......... .......... .......... 97%  428.89 KB/s
 2900K .......... .......... .......... .......... .......... 99%  429.90 KB/s
 2950K .......... ....                                       100%    2.04 MB/s

18:04:32 (465.40 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

---

### Post by rsambuca on 2007-12-05
Are you using Automatix?

---

### Post by dandandan on 2007-12-05
no, should i? i dont really like that.

---

### Post by VON_CAPO on 2007-12-05
Same problem here but I am using a 32 bits architecture.

 2850K .......... .......... .......... .......... .......... 97%  701.98 KB/s
 2900K .......... .......... .......... .......... .......... 99%  702.81 KB/s
 2950K .......... ....                                       100%  658.92 KB/s

12:27:09 (557.25 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed. 

:(

---

### Post by rsambuca on 2007-12-05
I am not a fan of using Automatix.  I just asked because I have seen this error popping up lately and a lot of the time the users were using it.  I was wondering if it was related.

What method did you use to install it in the first place which resulted in the error.  You never specified.

---

### Post by VON_CAPO on 2007-12-05
OK, SOLVED!!! using instructions from this thread:

[http://ubuntuforums.org/showthread.php?t=632107](http://ubuntuforums.org/showthread.php?t=632107)

:)

---

### Post by dandandan on 2007-12-05
i installed via apt-get install flashplugin-nonfree


i tried the fix from the other threads, tried to copy the fileto plugin folder and did ndiswrapper -i   but it  did not work

---

### Post by dandandan on 2007-12-05
what i did now is copied the .so file to /usr/lib/firefox/plugins and did nspluginwrapper -i on it

now flash starts, but its really really slow and firefox freezed after 1 minute, so its not really working.
any suggestions?

---

### Post by hollowhead on 2007-12-05
I had this problem too the funny thing is I had to reinstall see

[http://ubuntuforums.org/showthread.php?t=629661](http://ubuntuforums.org/showthread.php?t=629661)

but when I downloaded flash on Saturday it installed fine

 thanks your method works!  but presumably I need to copy the lib file to all home/mozilla/plugin dirs for each user.....

---

### Post by Kilz on 2007-12-05
> **hollowhead said:**
> I had this problem too the funny thing is I had to reinstall see

[http://ubuntuforums.org/showthread.php?t=629661](http://ubuntuforums.org/showthread.php?t=629661)

but when I downloaded flash on Saturday it installed fine

 thanks your method works!  but presumably I need to copy the lib file to all home/mozilla/plugin dirs for each user.....

Did you report your problems installing flash from flashplugin-nonfree on launchpad?

Did any of the people with problems getting flashplugin-nonfree working report their bug on launchpad?

---

### Post by VON_CAPO on 2007-12-05
> **Kilz said:**
> 
Did any of the people with problems getting flashplugin-nonfree working report their bug on launchpad?
I googled it before I found this thread.

The problem with flash (the wrong checksum) is not new at all, this bug has been already reported in Feisty.

---

### Post by rsambuca on 2007-12-05
> **VON_CAPO said:**
> I google it before I found this thread.

The problem with flash (the wrong checksum) is not new at all, this bug has been already reported in Feisty.

That is impossible.  The flashplugin-nonfree package for 64bit is new to Gutsy.

---

### Post by VON_CAPO on 2007-12-05
> **rsambuca said:**
> That is impossible.  The flashplugin-nonfree package for 64bit is new to Gutsy.
The checksum problem is not related to the architecture, because I am using 32 bits system. 

In  Absolute Beginner Talk Forum there is another thread with the same problem

---

### Post by VON_CAPO on 2007-12-05
Launchpad links reporting this bug (from july 2007):

---> [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/125131](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/125131)

---> [https://answers.launchpad.net/ubuntu/+question/10061](https://answers.launchpad.net/ubuntu/+question/10061)

---

### Post by Txukie on 2007-12-05
Problem is that there is a new version of the flahplayer plugin but the file from the internet is called the same.

The .deb checks the sum of this file and obviously gets it wrong, since its looking for the md5sum of the old version and is getting the new version.

A quick workaround for this is to modify the post-install script for this package.

That is after apt-getting the flashplugin-nonfree and it failing you do

sudo vi /var/lib/dpkg/info/flashplugin-nonfree.postinst

You go here:

        # verify MD5 checksum of (copied or downloaded) tarball
        rm -rf install_flash_player_9_linux/
        echo "821cc72359a937caef85bb4cc74ef5cd  install_flash_player_9_linux.tar.gz"| md5sum -c > /dev/null 2>&1 \
                || fp_exit_with_error "md5sum mismatch install_flash_player_9_linux.tar.gz"

        # unpacking and checking the plugin
        tar xzf install_flash_player_9_linux.tar.gz || fp_exit_with_error "cannot unpack plugin"
        echo "be5a2f9032f8fc8bccbbf5d96c5028f9  install_flash_player_9_linux/libflashplayer.so"| md5sum -c > /dev/null 2>&1 \
                || fp_exit_with_error "plugin changed, not trusted"
        echo "a81fd3b03b8c6d6e5a14298110718d3f  install_flash_player_9_linux/flashplayer.xpt"| md5sum -c > /dev/null 2>&1 \
                || fp_exit_with_error "plugin changed, not trusted"


And you change it as such:

        # verify MD5 checksum of (copied or downloaded) tarball
        #rm -rf install_flash_player_9_linux/
        #echo "821cc72359a937caef85bb4cc74ef5cd  install_flash_player_9_linux.tar.gz"| md5sum -c > /dev/null 2>&1 \
         #       || fp_exit_with_error "md5sum mismatch install_flash_player_9_linux.tar.gz"

        # unpacking and checking the plugin
        tar xzf install_flash_player_9_linux.tar.gz || fp_exit_with_error "cannot unpack plugin"
        #echo "be5a2f9032f8fc8bccbbf5d96c5028f9  install_flash_player_9_linux/libflashplayer.so"| md5sum -c > /dev/null 2>&1 \
          #      || fp_exit_with_error "plugin changed, not trusted"
        #echo "a81fd3b03b8c6d6e5a14298110718d3f  install_flash_player_9_linux/flashplayer.xpt"| md5sum -c > /dev/null 2>&1 \
          #      || fp_exit_with_error "plugin changed, not trusted"



Of course you can actually change the md5sums so that they match this new version but this option is just quicker.

---

### Post by dandandan on 2007-12-05
@Txukie  thx that worked for the installation

Problem is, after a few second, either picture in firefox disappears or firefox freezes completely.
Check [www.burgerking.at](www.burgerking.at) or [www.burgerking.de](www.burgerking.de) for confirmation

console reports:
 dan@sued0r:/usr/lib/firefox/plugins$ firefox 
*** NSPlugin Wrapper *** ERROR: NPP_URLNotify() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::Invalidate() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NP_Shutdown() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_URLNotify() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::Invalidate() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NP_Shutdown() invoke: Connection closed

---

### Post by rsambuca on 2007-12-05
> **dandandan said:**
> @Txukie  thx that worked for the installation

Problem is, after a few second, either picture in firefox disappears or firefox freezes completely.
Check [www.burgerking.at](www.burgerking.at) or [www.burgerking.de](www.burgerking.de) for confirmation

console reports:
 dan@sued0r:/usr/lib/firefox/plugins$ firefox 
*** NSPlugin Wrapper *** ERROR: NPP_URLNotify() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::Invalidate() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NP_Shutdown() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_URLNotify() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::Invalidate() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NP_Shutdown() invoke: Connection closed

Works fine for me.

---

### Post by jespdj on 2007-12-05
**Txukie**: What am I supposed to do after editing the postinstall script? Just editing the script is not enough. Should I run it manually?

---

### Post by Kilz on 2007-12-05
> **VON_CAPO said:**
> Launchpad links reporting this bug (from july 2007):

---> [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/125131](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/125131)

---> [https://answers.launchpad.net/ubuntu/+question/10061](https://answers.launchpad.net/ubuntu/+question/10061)

That you found 2 ancient bugs is not an excuse to report this one. This bug has not been here since August, it is resent.

Googling bugs is not an excuse to not report bugs. 

As a rule report all bugs, even if you think its already done add comments to the report you find.

---

### Post by VON_CAPO on 2007-12-05
> **Kilz said:**
> That you found 2 ancient bugs is not an excuse to report this one. This bug has not been here since August, it is resent.

Googling bugs is not an excuse to not report bugs. 

As a rule report all bugs, even if you think its already done add comments to the report you find.
:lolflag: This is amazing!!!

I did not think I enrolled in the army.

If I understand the forum, this is about to help people, and pointing to personal faults... is out of place.

Regards. :popcorn:

---

### Post by Kilz on 2007-12-05
> **VON_CAPO said:**
> :lolflag: This is amazing!!!

I did not think I enrolled in the army.

If I understand the forum, this is about to help people, and pointing to personal faults... is out of place.

Regards. :popcorn:

Telling people to report bugs is not pointing out personal faults.  Suggesting that the excuse they had for not reporting them is not a good one is also not a personal attack.

What you should understand is that good community members report bugs and that excuses do no one any good.

---

### Post by VON_CAPO on 2007-12-05
Sir, if you think something has to be made, do it yourself.

On my side, I just did in this thread a few commentaries to help some members to find a fix.

I think your persistence in this hostile attitude deserves moderator's action.

---

### Post by Kilz on 2007-12-05
> **VON_CAPO said:**
> Sir, if you think something has to be made, do it yourself.

On my side, I just did in this thread a few commentaries to help some members to find a fix.

I think your persistence in this hostile attitude deserves moderator's action.

You are just to funny. but you still need to report bugs that happen to you.

---

### Post by dandandan on 2007-12-05
can we get back to the topic pls?
Anyone any ideas why i got those errors and ff/flash freezes on me?

I got a new error outout tho, when the ff screen goes all grey console says this:

*** glibc detected *** /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: free(): invalid next size (normal): 0x080edbd0 ***
======= Backtrace: =========
/lib32/libc.so.6[0xf77c28e5]
/lib32/libc.so.6[0xf77c4462]
/lib32/libc.so.6(realloc+0x106)[0xf77c65e6]
/usr/lib32/libglib-2.0.so.0(g_realloc+0x3b)[0xf7a3e9bb]
/usr/lib32/libglib-2.0.so.0[0xf7a57c7c]
/usr/lib32/libglib-2.0.so.0(g_string_insert_len+0x73)[0xf7a58773]
/usr/lib32/libglib-2.0.so.0(g_string_append+0x41)[0xf7a58b41]
/usr/lib32/libglib-2.0.so.0(g_log_default_handler+0x1ab)[0xf7a40a0b]
/usr/lib32/libglib-2.0.so.0(g_logv+0x2e5)[0xf7a3fd65]
/usr/lib32/libglib-2.0.so.0(g_log+0x29)[0xf7a3ff89]
/usr/lib32/libgobject-2.0.so.0(g_object_newv+0x97a)[0xf7ad928a]
/usr/lib32/libgobject-2.0.so.0(g_object_new_valist+0x2c9)[0xf7ad9839]
/usr/lib32/libgobject-2.0.so.0(g_object_new+0x40)[0xf7ad9940]
/usr/lib32/libgdk_pixbuf-2.0.so.0(gdk_pixbuf_new_from_data+0x104)[0xf7746314]
/usr/lib32/libgdk_pixbuf-2.0.so.0(gdk_pixbuf_new+0xea)[0xf774442a]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf6d23cf0]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf6d24187]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf6ced702]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf6cd5b0c]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf6d03540]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf6d041f0]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf6d0454e]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf7014550]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf7013d5b]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf701508d]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf70139aa]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf7013d27]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf701508d]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf7013d5b]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf701508d]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf7013d5b]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf701508d]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf7013d5b]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf701508d]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf7013d5b]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf701508d]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf7013d5b]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf701508d]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf6f80c5d]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf6f8488a]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf70a1162]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf70a5738]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf70a5915]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf6c4e55d]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf70b08df]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf6d2a63b]
/usr/lib/flashplugin-nonfree/libflashplayer.so[0xf6c4e01e]
/usr/lib32/libglib-2.0.so.0[0xf7a378d6]
/usr/lib32/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xf7a3711c]
/usr/lib32/libglib-2.0.so.0[0xf7a3a55f]
/usr/lib32/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xf7a3a909]
/usr/lib32/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xf7ce09e4]
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin[0x804f960]
/lib32/libc.so.6(__libc_start_main+0xe0)[0xf776e050]
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin[0x804a971]
======= Memory map: ========
08048000-08060000 r-xp 00000000 08:03 18613279                           /usr/lib/nspluginwrapper/i386/linux/npviewer.bin
08060000-08061000 rw-p 00018000 08:03 18613279                           /usr/lib/nspluginwrapper/i386/linux/npviewer.bin
08061000-0896e000 rw-p 08061000 00:00 0                                  [heap]
f32d7000-f37f1000 rw-p f32d7000 00:00 0 
f3829000-f3955000 rw-p f3829000 00:00 0 
f3955000-f3999000 r--p 00000000 08:03 1048673                            /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
f3999000-f399f000 r--s 00000000 08:03 16089697                           /home/dan/.fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
f399f000-f39a2000 r--s 00000000 08:03 16089696                           /home/dan/.fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
f39a2000-f39a6000 *** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::Invalidate() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NP_Shutdown() invoke: Connection closed

---

### Post by t_anjan on 2007-12-06
What are we supposed to do after editing the postinst file? How to install?

---

### Post by Leppiz on 2007-12-06
> **t_anjan said:**
> What are we supposed to do after editing the postinst file? How to install?

Doing
```
sudo dpkg-reconfigure flashplugin-nonfree
nspluginwrapper -v -a -i
```
was enough for me.

---

### Post by Txukie on 2007-12-06
Yeah sorry you are to reconfigure the program, reconfigure launches only the post install tasks

sudo dpkg-reconfigure flashplugin-nonfree

If you do an

sudo apt-get install --reinstall flashplugin-nonfree


You will overwrite your modifications on the file and it won't work.

Any bugs to do with freezes in particular websites and such are not related to this bug.

---

### Post by Kilz on 2007-12-06
Has anyone experiencing these problems reported the bug on launchpad, if so please provide the url.

---

### Post by frodon on 2007-12-06
Kilz, with all due respect, i think users in this thread understood the need to report bugs so there's no need to repeat over and over the same thing.

You still have the possibility to report the bug for them if they don't have time or will to do so ;)

Ok, lets go back on topic now.

---

### Post by tiger_xp on 2007-12-06
Probably the easiest way to install Flash plugin (at least, for me) is using the 'install_flash_player_9_linux.tar.gz' with md5 checksum that matches the package. Fortunately, one of my friends have successfully downloaded and installed plugin about a week ago, so I took this file from his cache. You may download it from here:
[http://rapidshare.com/files/74688266/install_flash_player_9_linux.tar.gz](http://rapidshare.com/files/74688266/install_flash_player_9_linux.tar.gz)
Download, save it somewhere and then run:
```

sudo dpkg-reconfigure flashplugin-nonfree
```
When prompted, enter the path where you saved the file. It should reconfigure the package and say:
```

Installing from local file <your path>
Flash Plugin installed.
```
After this make sure that FF is closed (maybe this is not critical) and run:
```

nspluginwrapper -v -a -i
```
That's it, hope it will help someone ;)

---

### Post by cbaby on 2007-12-06
it helped me... 
thanks.

---

### Post by Roland123 on 2007-12-06
> **Txukie said:**
> Problem is that there is a new version of the flahplayer plugin but the file from the internet is called the same.
[...]
Of course you can actually change the md5sums so that they match this new version but this option is just quicker.

Thanks, this worked like a charm.

---

### Post by utUtu on 2007-12-06
Whoever packaged the flashplugin-nonfree  has to fix it now that there is a new version of flash out there.  IMHO he/she should not have hard coded the MD5 chksum in the postinst script, or should have left out the chksum check out alltogether because I don't see any MD5 sums published by Adobe on their download site.

---

### Post by misfitpierce on 2007-12-06
[https://bugs.launchpad.net/ubuntu/+bug/174276](https://bugs.launchpad.net/ubuntu/+bug/174276)

there goes one of the bug reports for it.

---

### Post by Kilz on 2007-12-06
> **frodon said:**
> Kilz, with all due respect, i think users in this thread understood the need to report bugs so there's no need to repeat over and over the same thing.

You still have the possibility to report the bug for them if they don't have time or will to do so ;)

Ok, lets go back on topic now.

I think that it is not understood as some people think.

1. There is no sticky in this section that deals with how to report bugs.
2.  A lot of users believe that simply posting to the forums is all they have to do to report a problem. 
3. Others think that someone else will report the bug, they dont have to.
4. Yet others will think a work around is the fix.

In fact this bug was [only first reported 16 hours ago]("https://bugs.launchpad.net/ubuntu/+bug/174276") yet this thread is over 24 hours old. If someone had reported it , they could have added the bug report in this thread so others can add comments. 

Lastly as good community members it is right and correct that each person who experiences bugs to report them. People who do not experience the problem may not have all the details necessary to report the bug. In fact one of the requirements for r[eporting the bug]("http://www.ubuntu.com/community/reportproblem") are "You can repeat the problem"

> **misfitpierce said:**
> [https://bugs.launchpad.net/ubuntu/+bug/174276](https://bugs.launchpad.net/ubuntu/+bug/174276)

there goes one of the bug reports for it.

Thanks.  :D

---

### Post by collector on 2007-12-07
sudo vi /var/lib/dpkg/info/flashplugin-nonfree.postinst

when i run this in the terminal i can see the text and stuff but i cant change it how comes that or how can i change it.

sorry for the noob question :(

---

### Post by neighborlee on 2007-12-07
> **VON_CAPO said:**
> Sir, if you think something has to be made, do it yourself.

On my side, I just did in this thread a few commentaries to help some members to find a fix.

I think your persistence in this hostile attitude deserves moderator's action.

Your lack of willingness not to help the community is really disrtrubing and unjust.  You want to use free software yet seem unwilling to help in its bug reports which HELP  EVERYONE when they are done..on top of that the reports  automatically generates these things so not doing is in clear violation of the all for one and one for all philosophy :)

dont you like to help others make their OS better ? ;)

:popcorn:

cheers
nl

---

### Post by neighborlee on 2007-12-07
> **frodon said:**
> Kilz, with all due respect, i think users in this thread understood the need to report bugs so there's no need to repeat over and over the same thing.

You still have the possibility to report the bug for them if they don't have time or will to do so ;)

Ok, lets go back on topic now.

I disagree..its so  easy to report them ( I mean when they are caught by apport ) that its almost a crime if they dont..oss is only made better if people that USE oss help out.

I mean with apport its  so   amazingly   easy now I can't imagine anyone wouldnt love helping out  now ;))

 I dont think that could be said enough.. if you like it use it help it and pass it along...whats so terrible about that...

oh btw..not to TOOT My own horn as Id' not care if I was annoymous..but yes I did report this when the apport did its job..it did its job and I was  MORE than happy to comply and do my part,,I was honored to be able to help make OSS better ;)



cheers
nl

---

### Post by neighborlee on 2007-12-07
> **utUtu said:**
> Whoever packaged the flashplugin-nonfree  has to fix it now that there is a new version of flash out there.  IMHO he/she should not have hard coded the MD5 chksum in the postinst script, or should have left out the chksum check out alltogether because I don't see any MD5 sums published by Adobe on their download site.

That seems logical.something as important as flash to people I find very strange at best that this was allowed to happen..isn't there any oversight into these things ? ;))

I would be happy to help out on this project assuming thats desired ?

I have another quetion on this same topic: why is there no apt file at  adobe's download page just yum and rpm.I think we should be working with them to get a apt package up so this is never a issue again ?

cheers
:popcorn:
nl

---

### Post by jespdj on 2007-12-07
The problem has been fixed: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890)

However, the change doesn't seem to be in the 32-bit Gutsy (which is what I'm using) repository yet. Maybe I'll have to wait a day or so for the mirrors to be updated.

About reporting bugs: If you find a bug in Ubuntu, **report it**! Otherwise the developers won't know there is a problem and it will not get fixed. Not reporting bugs means that you don't care about Ubuntu... Compare not reporting bugs to the following story:

Recently, here in the Netherlands a church burnt down where there was an exhibition of paintings of a well-known Dutch artist. Many of his unique paintings are now lost forever! :( The fire brigade arrived very late, because nobody who saw the burning church called the emergency number. Everybody thought that someone else had already called - but that wasn't the case.

---

### Post by daradib on 2007-12-08
This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by battles33 on 2007-12-08
from this page
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890)

i followed cyrus jones' method and it worked for me, with a couple small problems
had to download cdbs, [http://packages.debian.org/sarge/cdbs](http://packages.debian.org/sarge/cdbs)
also, changed his last command to something else

cryrus' procedure
wget [http://launchpadlibrarian.net/10756602/flashplugin-nonfree_9.0.115.0ubuntu2.tar.gz](http://launchpadlibrarian.net/10756602/flashplugin-nonfree_9.0.115.0ubuntu2.tar.gz)
tar -zxvf flashplugin-nonfree_9.0.115.0ubuntu2.tar.gz
cd flashplugin-nonfree-9.0.115.0ubuntu2
dpkg-buildpackage -b -rfakeroot

last line for me was modified to make it work in my situation
sudo dpkg-buildpackage -b -d

---

### Post by Jeroi on 2007-12-09
Ok, here is fix for Kubuntu Gutsy amd64 flashplugin-nonfree md5-checksum error:

1. sudo apt-get install flashplugin-nonfree
2. sudo nano /var/lib/dpkg/info/flashplugin-nonfree.postinst
3. Edit:
```
# verify MD5 checksum of (copied or downloaded) tarball
rm -rf install_flash_player_9_linux/
echo "821cc72359a937caef85bb4cc74ef5cd install_flash_player_9_linux.tar.gz"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "md5sum mismatch install_flash_player_9_linux.tar.gz"

# unpacking and checking the plugin
tar xzf install_flash_player_9_linux.tar.gz || fp_exit_with_error "cannot unpack plugin"
echo "be5a2f9032f8fc8bccbbf5d96c5028f9 install_flash_player_9_linux/libflashplayer.so"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "plugin changed, not trusted"
echo "a81fd3b03b8c6d6e5a14298110718d3f install_flash_player_9_linux/flashplayer.xpt"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "plugin changed, not trusted"
```

to:
```
        # verify MD5 checksum of (copied or downloaded) tarball
        rm -rf install_flash_player_9_linux/
        echo "93b7c48eaa492237b807a3ae1de65cf9  install_flash_player_9_linux.tar.gz"| md5sum -c > /dev/null 2>&1 \
                || fp_exit_with_error "md5sum mismatch install_flash_player_9_linux.tar.gz"

        # unpacking and checking the plugin
        tar xzf install_flash_player_9_linux.tar.gz || fp_exit_with_error "cannot unpack plugin"
        #echo "a81fd3b03b8c6d6e5a14298110718d3f  install_flash_player_9_linux/flashplayer.xpt"| md5sum -c > /dev/$
        #echo "13ce705df5d47422a9192b29827544e8  install_flash_player_9_linux/libflashplayer.so"| md5sum -c > /de$
        #       || fp_exit_with_error "plugin changed, not trusted"

```

4. sudo dpkg-reconfigure flashplugin-nonfree
5. nspluginwrapper -v -a -i

Atleast this helped me and after 3hour of trying, it gave me so nice warm wave to watch flash with firefox. I hope you rest can enjoy it too.

---

### Post by battles33 on 2007-12-09
the fix for Kubuntu also works for the regular Ubuntu Gutsy. i managed to screw up my libc6 by installing a newer one, which when installing removed a bunch of stuff including the flash plugin. then, following those instruction i had posted for some reason didn't work the second time around. but Jeroi's method worked, makes sense, too, as it's all in the md5checksum. so Jeroi, thanks a lot

---

### Post by bazzbc on 2007-12-09
Worked like a charm.  

Thanks a lot mate

---

### Post by daradib on 2007-12-09
Thanks battles33. I guess you did not have the dependencies for the flash plugin already installed. You could run:

```
sudo apt-get build-dep flashplugin-nonfree
```

That downloads and installs all of the dependencies for the flash plugin. BTW, I'm Cyrus Jones.

Jeroi's method essential does what exactly is done in the new Ubuntu package. You can build you own amd64 (32-bit users already have an "official" package compiled) package, or you can use [this binary package I compiled]("http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb").

As a rule of thumb, however, you should only install packages if you trust the maker.

---

### Post by daradib on 2007-12-10
For more information on this bug see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

### Post by Maybelline on 2007-12-12
> **Jeroi said:**
> Ok, here is fix for Kubuntu Gutsy amd64 flashplugin-nonfree md5-checksum error:

1. sudo apt-get install flashplugin-nonfree
2. sudo nano /var/lib/dpkg/info/flashplugin-nonfree.postinst
3. Edit:
```
# verify MD5 checksum of (copied or downloaded) tarball
rm -rf install_flash_player_9_linux/
echo "821cc72359a937caef85bb4cc74ef5cd install_flash_player_9_linux.tar.gz"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "md5sum mismatch install_flash_player_9_linux.tar.gz"

# unpacking and checking the plugin
tar xzf install_flash_player_9_linux.tar.gz || fp_exit_with_error "cannot unpack plugin"
echo "be5a2f9032f8fc8bccbbf5d96c5028f9 install_flash_player_9_linux/libflashplayer.so"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "plugin changed, not trusted"
echo "a81fd3b03b8c6d6e5a14298110718d3f install_flash_player_9_linux/flashplayer.xpt"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "plugin changed, not trusted"
```

to:
```
        # verify MD5 checksum of (copied or downloaded) tarball
        rm -rf install_flash_player_9_linux/
        echo "93b7c48eaa492237b807a3ae1de65cf9  install_flash_player_9_linux.tar.gz"| md5sum -c > /dev/null 2>&1 \
                || fp_exit_with_error "md5sum mismatch install_flash_player_9_linux.tar.gz"

        # unpacking and checking the plugin
        tar xzf install_flash_player_9_linux.tar.gz || fp_exit_with_error "cannot unpack plugin"
        #echo "a81fd3b03b8c6d6e5a14298110718d3f  install_flash_player_9_linux/flashplayer.xpt"| md5sum -c > /dev/$
        #echo "13ce705df5d47422a9192b29827544e8  install_flash_player_9_linux/libflashplayer.so"| md5sum -c > /de$
        #       || fp_exit_with_error "plugin changed, not trusted"

```

4. sudo dpkg-reconfigure flashplugin-nonfree
5. nspluginwrapper -v -a -i

Atleast this helped me and after 3hour of trying, it gave me so nice warm wave to watch flash with firefox. I hope you rest can enjoy it too.

In case anyone (like me) likes to pore over the code as you follow along, don't miss the extra space (2 of them) between the md5sum and the install_flash_player_9_linux.tar.gz on this line:
```
 echo "93b7c48eaa492237b807a3ae1de65cf9  install_flash_player_9_linux.tar.gz"
```

Thanks, Jeroi... worked like a champ.

---

### Post by DeLaNooch on 2007-12-12
Wow! After reading all of this I am still confused as ever...

I am currently running a fresh install of Feisty AMD64 and will have absolutely no problems or complaints if my system is inadvertantly broken while trying to get Flashplayer working.

Is my best bet at this point still to use Cyrus / Daradib's method of building my own package?

---

### Post by Kilz on 2007-12-12
> **DeLaNooch said:**
> Wow! After reading all of this I am still confused as ever...

I am currently running a fresh install of Feisty AMD64 and will have absolutely no problems or complaints if my system is inadvertantly broken while trying to get Flashplayer working.

Is my best bet at this point still to use Cyrus / Daradib's method of building my own package?

No, this problem does not effect Feisty (7.04). It only effects Gutsy (7.10) and Hardy (current development version) You cant install flashplugin-nonfree in Feisty amd64, the package does not exist. Even if it did the nspluginwrapper package doesnt exist in feisty.
[The best way to get Flash working in Feisty amd64 is right here]("http://ubuntuforums.org/showthread.php?t=476924").

---

### Post by daradib on 2007-12-12
Kilz is right. His method is better for your purpose, though it is possible to create your own package and then use nspluginwrapper.

---

### Post by Kilz on 2007-12-12
I have modified my [nspluginwrapper script]("http://ubuntuforums.org/showthread.php?t=476924") to work on Gutsy since its taking the Ubuntu developers so long to fix this. It uses the nspluginwrapper package in the Gutsy repositories and downloads the flash plugin directly from Adobe.

---

### Post by daradib on 2007-12-12
Good news.

The new flashplugin-nonfree package was uploaded to all supported Ubuntu proposed repositories (6.06-7.10) about 8 hours ago, though 32-bit and 64-bit binaries have not yet been built.

[https://www.launchpad.net/ubuntu/+source/flashplugin-nonfree](https://www.launchpad.net/ubuntu/+source/flashplugin-nonfree)

Just as we were beginning to lose hope. But there are some problems with this update (namely for Konqueror and Opera).

See more information on this bug and fix [here]("http://ubuntuforums.org/showthread.php?t=636397") (updated).

---

### Post by Jeroi on 2007-12-13
> **daradib said:**
> 
Jeroi's method essential does what exactly is done in the new Ubuntu package. You can build you own amd64 (32-bit users already have an "official" package compiled) package, or you can use [this binary package I compiled]("http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb").


I now tested this package on fresh install of Kubuntu amd64 Gutsy. Works like charm with default packet installer on kde. Firefox started right away to show flash content.

Hope this package will come to repositories soon.

---

### Post by TheShocker on 2007-12-13
32 bit package has been built

---

### Post by daradib on 2007-12-13
Yes, the 32-bit package has been built (I have updated the [thread]("http://ubuntuforums.org/showthread.php?t=636397")).

Jeroi: The package's problem with Kubuntu is the fact that it doesn't work with Konqueror (See the [thread]("http://ubuntuforums.org/showthread.php?t=636397"))

---

### Post by utUtu on 2007-12-13
> **daradib said:**
> Yes, the 32-bit package has been built (I have updated the [thread]("http://ubuntuforums.org/showthread.php?t=636397")).

Jeroi: The package's problem with Kubuntu is the fact that it doesn't work with Konqueror (See the [thread]("http://ubuntuforums.org/showthread.php?t=636397"))

After installing the flash plugin, you have to tell Konqueror.  Go to configure konqueror > plugins > 'scan for plugins', or you can check the box ' scan..startup'.  Make sure the '/usr/lib/firefox/plugins' is in the list of directories to scan.

:guitar:

---

### Post by Kilz on 2007-12-13
Those of you discussing that the 32bit package has been released, and that it has issues, should be aware that this thread is in the 64bit section.

---

### Post by daradib on 2007-12-15
> **utUtu said:**
> After installing the flash plugin, you have to tell Konqueror.  Go to configure konqueror > plugins > 'scan for plugins', or you can check the box ' scan..startup'.  Make sure the '/usr/lib/firefox/plugins' is in the list of directories to scan.

See [Launchpad Bug# 174343]("https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/174343")

---

### Post by buntu_hugenewbie11 on 2007-12-15
I am trying to do the 64 bit version correction but when I run tar-zvxf I get a bash command error that the command is not found. How can I fix this?

---

### Post by Kilz on 2007-12-15
> **buntu_hugenewbie11 said:**
> I am trying to do the 64 bit version correction but when I run tar-zvxf I get a bash command error that the command is not found. How can I fix this?
[Go here]("http://ubuntuforums.org/showthread.php?t=476924") , get script, run script.

---

### Post by buntu_hugenewbie11 on 2007-12-15
I never get the option to run in terminal. How do I run a script in the terminal?

---

### Post by buntu_hugenewbie11 on 2007-12-15
Actually I think I ran it (./GetFlash) but it doesn't install as when I run about:plugins in firefox and swiftweasel it says nothing about a flash plugin?? And where is the script with nspluginwrapper?
The link you sent me doesn't seem to have it?
Thanks for your help with this.
Much appreciated.

---

### Post by Kilz on 2007-12-15
> **buntu_hugenewbie11 said:**
> Actually I think I ran it (./GetFlash) but it doesn't install as when I run about:plugins in firefox and swiftweasel it says nothing about a flash plugin?? And where is the script with nspluginwrapper?
The link you sent me doesn't seem to have it?
Thanks for your help with this.
Much appreciated.

Yes that script has nspluginwrapper. It has been tested and works with both firefox and swiftweasel (I use swiftweasel myself).

---

### Post by buntu_hugenewbie11 on 2007-12-15
So there must be something I am doing wrong as this script does not work for me. I do get the following error:
chown: cannot access `/usr/lib/nspluginwrapper/plugins': No such file or directory
Is this a permissions problem?

---

### Post by Kilz on 2007-12-16
> **buntu_hugenewbie11 said:**
> So there must be something I am doing wrong as this script does not work for me. I do get the following error:
chown: cannot access `/usr/lib/nspluginwrapper/plugins': No such file or directory
Is this a permissions problem?

There could be a number of reasons. It may be because you do not have the multiverse repository enabled. That you have deleted the folder. 
But seeing how it has worked for others I think the script is ok.

---

### Post by buntu_hugenewbie11 on 2007-12-16
How would I delete the folder?
Doesn't it get created when you tar?
Also in the temp file I don't get a flashplayer.xpt?

---

### Post by thomaswp on 2007-12-16
Thank you.  That worked for me.

---

### Post by Kilz on 2007-12-16
> **buntu_hugenewbie11 said:**
> How would I delete the folder?
Doesn't it get created when you tar?
Also in the temp file I don't get a flashplayer.xpt?

There are a few ways to delete the folder, but if you have deleted it and did not uninstall the nspluginwrapper package. Your system will think the package is installed and the folder exists and so not install the package again.
/usr/lib/nspluginwrapper/plugins is created by the install of the nspluginwrapper package from the gutsy repository if you are running gutsy and have the multiverse repository enabled. If of corse it isnt already installed as per above.
What version of Ubuntu are you running?
Do you have the universe and multiverse enabled?

---

### Post by pekkal on 2007-12-26
Thanks Jeroi - your post #43 in this thread worked for me (Kubuntu Gutsy AMD64)!

---

### Post by gimfred on 2007-12-27
I've got the same problem on kubuntu 7.10.
flash doesn't work either.

---

### Post by ^rooker on 2007-12-30
It seems that the "md5sum mismatch" error is here to stay (in all releases: Dapper, Edgy, Feisty - even Gutsy and Hoary). Could anyone please explain to me why this is so?

I thought that each package has its checksum, and that it was caused by Adobe updating/changing their installer file. Ok, but isn't it possible to update the checksum in the repositories, or is Adobe changing its installer daily?

Secondly, I saw that the new .tar.gz from Adobe's site doesn't contain the "flashplugin.xpt" file anymore. Does that have any side-effects? (Since then, playing flash in Konqueror behaves "unstable")


Thanks for any hints.

---

### Post by Kilz on 2007-12-30
> **^rooker said:**
> It seems that the "md5sum mismatch" error is here to stay (in all releases: Dapper, Edgy, Feisty - even Gutsy and Hoary). Could anyone please explain to me why this is so?

I thought that each package has its checksum, and that it was caused by Adobe updating/changing their installer file. Ok, but isn't it possible to update the checksum in the repositories, or is Adobe changing its installer daily?

Secondly, I saw that the new .tar.gz from Adobe's site doesn't contain the "flashplugin.xpt" file anymore. Does that have any side-effects? (Since then, playing flash in Konqueror behaves "unstable")


Thanks for any hints.

Sadly it is taking way to long for the Developers to fix this issue for us. [Here is a good way to get flash working.]("http://ubuntuforums.org/showthread.php?t=476924")
The "md5sum mismatch" error is because the deb file downloads the plugin from Adobe. It checks that the file is the right size with md5sum. When Adobe released a new plugin (one that is broken for a lot of sites by the way)  the files no longer matched. It would seem a trivial thing to fix, but alas we are still waiting. But I did fix my install script to work for 64bit users, link above.

---

### Post by ^rooker on 2007-12-30
@Kilz:
You're confirming my understanding, but I ran into this problem already in September. Slow or not - I think that some repository maintainer could have taken care of that between Adobe's updates. 

So I'm suspecting that Adobe fiddles around with their .tar.gz file so often that the repository maintainers can't keep up? If that's the case, I'd really like to know *what* Adobe's changing all the time... (Last change on Dec. 3rd, 2007)
(And have they removed the ".xpt" file?)


Does anyone have any clue about this issue?

Furthermore: 
The current version of FlashPlugin (v9.0.115.0) always crashes in Konqueror (v3.5.6).


PS: Damn Adobe! Can't they just make Flash GPL - or at least let us have it directly in the repositories? arrrrgh!

---

### Post by Kilz on 2007-12-30
> **^rooker said:**
> @Kilz:
You're confirming my understanding, but I ran into this problem already in September. Slow or not - I think that some repository maintainer could have taken care of that between Adobe's updates. 

So I'm suspecting that Adobe fiddles around with their .tar.gz file so often that the repository maintainers can't keep up? If that's the case, I'd really like to know *what* Adobe's changing all the time... (Last change on Dec. 3rd, 2007)
(And have they removed the ".xpt" file?)


Does anyone have any clue about this issue?

Furthermore: 
The current version of FlashPlugin (v9.0.115.0) always crashes in Konqueror (v3.5.6).


PS: Damn Adobe! Can't they just make Flash GPL - or at least let us have it directly in the repositories? arrrrgh!

Version 115 was the version that started this whole problem. Before that it was version 48. As you see from your current flash, its the same thing. The file is not changing at all. The Ubuntu developers could remove the md5sum check.
But to be honest 115 is a bad plugin. It has lots of issues that 48 didnt. I went back to 48 because of mycokerewards.com. The site will not work with the new plugin.

---

### Post by daradib on 2008-01-02
The main reason it is taking so long is because the new flash plugin has important bugs with Konqueror and Opera, which cannot be abandoned.

See the [bug comments]("https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890")

[https://lists.ubuntu.com/archives/ubuntu-devel/2007-December/024877.html](https://lists.ubuntu.com/archives/ubuntu-devel/2007-December/024877.html)

[https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890/comments/85](https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890/comments/85)

---

### Post by utUtu on 2008-01-02
[QUOTE=daradib;4060261]The main reason it is taking so long is because the new flash plugin has important bugs with Konqueror and Opera, which cannot be abandoned.

[QUOTE]

You mean Konqueror and Opera has bugs handling flash - not the Adobe flash has bugs.

Why would FireFox users be 3rd fiddle  to Konqueror & Opera?

---

### Post by daradib on 2008-01-02
Well the new flash plugin removes some essential things for Opera and Konqueror and requires the use of XEmbed.

XEmbed in Konquerer: [Launchpad Bug# 174343]("https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/174343")

If you read the links provided in my previous post (for future audience), you will understand the issues.

Of course, it is perfectly correct to say that Konqueror and Opera have problems with flash and not the other way around. Nevertheless, this fix cannot be done until Konqueror gains XEmbed support (Novell patch) in Ubuntu as Kubuntu is an official derivative that uses Konqueror by default with Konqueror in the main repository.

---

### Post by Kilz on 2008-01-02
I find that 115 is buggy even under Firefox. It is not a good plugin. [I have made a version of my script available that installs the r48 plugin, as well as the new r115.]("http://ubuntuforums.org/showthread.php?t=476924") It is an easy way to install flash for amd64. Not only for Gutsy, but also for older versions of Ubuntu that did not have a nspluginwrapper package.

---

### Post by utUtu on 2008-01-03
> **Kilz said:**
> I find that 115 is buggy even under Firefox. It is not a good plugin. [I have made a version of my script available that installs the r48 plugin, as well as the new r115.]("http://ubuntuforums.org/showthread.php?t=476924") It is an easy way to install flash for amd64. Not only for Gutsy, but also for older versions of Ubuntu that did not have a nspluginwrapper package.

I could be wrong, but I'm more inclined to believe the nspluginwrapper/npviewer need to be updated to the r115, or web page developer not implementing the site properly.

---

### Post by utUtu on 2008-01-03
> **daradib said:**
> Well the new flash plugin removes some essential things for Opera and Konqueror and requires the use of XEmbed.

XEmbed in Konquerer: [Launchpad Bug# 174343]("https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/174343")

If you read the links provided in my previous post (for future audience), you will understand the issues.

Of course, it is perfectly correct to say that Konqueror and Opera have problems with flash and not the other way around. Nevertheless, this fix cannot be done until Konqueror gains XEmbed support (Novell patch) in Ubuntu as Kubuntu is an official derivative that uses Konqueror by default with Konqueror in the main repository.

I could be wrong but not all Kubuntu users use Konqueror for web browsing. So it's safe to say majority of 'buntu users are FireFox users.?:confused:

I didn't realize global warming is so pervasive now that it even affected the winds at Canonical - Firefox users are now captive to Konqueror.  :)

---

### Post by araz on 2008-01-04
Same problem here:
```

xxxxx@xxxxx:~$ sudo apt-get install flashplugin-nonfree
A Ler Listas de Pacotes... Pronto
Construindo Árvore de Dependências       
Reading state information... Pronto 
Pacotes sugeridos :
  konqueror-nsplugins
Os seguintes NOVOS pacotes serão instalados:
  flashplugin-nonfree
0 pacotes actualizados, 1 pacotes novos instalados, 0 a remover e 0 não actualizados.
É necessário fazer o download de 18,1kB de arquivos.
Depois de descompactar, 160kB adicionais de espaço em disco serão utilizados.
Obter:1 http://archive.ubuntu.com gutsy/multiverse flashplugin-nonfree 9.0.48.0.2+really0ubuntu12 [18,1kB]
Obtidos 18,1kB em 0s (39,7kB/s)          
A pré-configurar os pacotes...
A seleccionar pacote anteriormente não seleccionado flashplugin-nonfree
(Lendo a base de dados ... 90302 ficheiros e directórios actualmente instalados.)
A descompactar flashplugin-nonfree (desde .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
A instalar flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--13:27:29--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
A resolver fpdownload.macromedia.com... 84.53.150.70
A conectar fpdownload.macromedia.com|84.53.150.70|:80... conectado.
Pedido HTTP enviado, a aguardar resposta... 200 OK
Tamanho: 3,036,127 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  277.95 KB/s
(...)
 2950K .......... ....                                       100%  896.23 KB/s

13:27:34 (739.45 KB/s) - './install_flash_player_9_linux.tar.gz' gravado [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

```

this is the solution i found to solve the problem.
[https://bugs.launchpad.net/medibuntu/+bug/175420]("https://bugs.launchpad.net/medibuntu/+bug/175420")

---

### Post by daradib on 2008-01-04
> **utUtu said:**
> I could be wrong but not all Kubuntu users use Konqueror for web browsing. So it's safe to say majority of 'buntu users are FireFox users.?:confused:

I didn't realize global warming is so pervasive now that it even affected the winds at Canonical - Firefox users are now captive to Konqueror.  :)

Well, as Konqueror is in the main repository and the DEFAULT, it must be supported. I know, the majority of *buntu users use Firefox, but Canonical has to offer special support to applications in the main repository.

And by the way, here is the solution to the problem again: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

### Post by Kilz on 2008-01-04
> **daradib said:**
> Well, as Konqueror is in the main repository and the DEFAULT, it must be supported. I know, the majority of *buntu users use Firefox, but Canonical has to offer special support to applications in the main repository.

And by the way, here is the solution to the problem again: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)
[URL="http://ubuntuforums.org/showthread.php?t=476924"]
64bit users can also use my script for simple installation.[/URL] This will also install nspluginwrappper on older 64 bit Ubuntu versions (everything before Gutsy) that did not have the package available.

---

### Post by Ryo964 on 2008-01-10
To anyone still having this "mismatch" problem. 

I had it to. But I never checked out the nspluginwrapper files. 
To be clear, you need to download the nspluginwrapper in addition to the flashplugin-nonfree (synaptic automatically yokes them). While the flashplugin-nonfree gave me the error, nspluginwrapper installed fine. 

So JUST install nspluginwrapper, go to the directory where it installed, find the file that says "Get Flash," and run it in a terminal. Follow the very easy instructions. 

I watched youtube's opening page for an hour! 

Maybe this is a classic case for me, a beginner, not reading readme files in my downloads. Hope that helps.

Gutsy 64/Vista on Dell Inspiron 1501

---

### Post by tajunta on 2008-01-26
> **Jeroi said:**
> Ok, here is fix for Kubuntu Gutsy amd64 flashplugin-nonfree md5-checksum error:

1. sudo apt-get install flashplugin-nonfree
2. sudo nano /var/lib/dpkg/info/flashplugin-nonfree.postinst
3. Edit:
```
# verify MD5 checksum of (copied or downloaded) tarball
rm -rf install_flash_player_9_linux/
echo "821cc72359a937caef85bb4cc74ef5cd install_flash_player_9_linux.tar.gz"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "md5sum mismatch install_flash_player_9_linux.tar.gz"

# unpacking and checking the plugin
tar xzf install_flash_player_9_linux.tar.gz || fp_exit_with_error "cannot unpack plugin"
echo "be5a2f9032f8fc8bccbbf5d96c5028f9 install_flash_player_9_linux/libflashplayer.so"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "plugin changed, not trusted"
echo "a81fd3b03b8c6d6e5a14298110718d3f install_flash_player_9_linux/flashplayer.xpt"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "plugin changed, not trusted"
```

to:
```
        # verify MD5 checksum of (copied or downloaded) tarball
        rm -rf install_flash_player_9_linux/
        echo "93b7c48eaa492237b807a3ae1de65cf9  install_flash_player_9_linux.tar.gz"| md5sum -c > /dev/null 2>&1 \
                || fp_exit_with_error "md5sum mismatch install_flash_player_9_linux.tar.gz"

        # unpacking and checking the plugin
        tar xzf install_flash_player_9_linux.tar.gz || fp_exit_with_error "cannot unpack plugin"
        #echo "a81fd3b03b8c6d6e5a14298110718d3f  install_flash_player_9_linux/flashplayer.xpt"| md5sum -c > /dev/$
        #echo "13ce705df5d47422a9192b29827544e8  install_flash_player_9_linux/libflashplayer.so"| md5sum -c > /de$
        #       || fp_exit_with_error "plugin changed, not trusted"

```

4. sudo dpkg-reconfigure flashplugin-nonfree
5. nspluginwrapper -v -a -i


Thanks mate! This helped me and for the first time in months I can see flash, though I have Ubuntu (with a U) Gutsy and Opera. The last command (5th) was not found though, but it seems I don't need it since it works fine now anyways. Feels nice to get something working as a noob. =)

---

### Post by lodp on 2008-01-29
.. so it did for me (also leaving away step 5, kubuntu 7.10 x86).

How come there's no official fix for this yet? Looks like this problem has been around for quite a while, and flash support is not exactly a marginal issue, is it? </rant>

the nasty thing is if you install the plugin through adept-manager, you don't even notice that it's not properly installed -- the package shows up with status "installed" there, even though the command line output says "flash-plugin NOT installed";

---

