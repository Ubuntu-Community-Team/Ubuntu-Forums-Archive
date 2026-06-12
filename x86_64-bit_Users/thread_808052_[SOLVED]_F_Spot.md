---
title: "[SOLVED] F Spot"
date: 2008-05-26
forum: x86 64-bit Users
---

### Post by gibsonsimswilson on 2008-05-26
Hi

Sorry if this is in the wrong place.

I click F Spot in the Applications >> Graphics menu and nothing happens

Am I doing something wrong ?

Thanks

Gibby

---

### Post by chrisccoulson on 2008-05-26
What happens if you run it from the terminal:
```
f-spot
```

---

### Post by FirstTimeMan on 2008-05-26
> **chrisccoulson said:**
> What happens if you run it from the terminal:
```
f-spot
```



where do you find the terminal?

---

### Post by gibsonsimswilson on 2008-05-26
I get this

```
f-spot
Stacktrace:

  at FSpot.Global..cctor () <0xffffffff>
  at FSpot.Global..cctor () <0x0000d>
  at (wrapper runtime-invoke) FSpot.Defines.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at FSpot.Driver.Main (string[]) <0xffffffff>
  at FSpot.Driver.Main (string[]) <0x00144>
  at (wrapper runtime-invoke) FSpot.Driver.runtime_invoke_int_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	f-spot [0x51bb67]
	f-spot [0x43dacd]
	/lib/libpthread.so.0 [0x7ff04c3fc7d0]
	/lib/libc.so.6(memcpy+0x60) [0x7ff04be87d50]
	f-spot(mono_breakpoint_clean_code+0x1b) [0x42725b]
	f-spot [0x43f78d]
	f-spot [0x44005e]
	[0x40fab15b]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x7ff04d0e17a0 (LWP 6825)]
[New Thread 0x42142950 (LWP 6827)]
[New Thread 0x418f3950 (LWP 6826)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0x00007ff04c3fb5cb in read () from /lib/libpthread.so.0
  3 Thread 0x418f3950 (LWP 6826)  0x00007ff04c3fbe81 in nanosleep ()
   from /lib/libpthread.so.0
  2 Thread 0x42142950 (LWP 6827)  0x00007ff04c3f8b99 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  1 Thread 0x7ff04d0e17a0 (LWP 6825)  0x00007ff04c3fb5cb in read ()
   from /lib/libpthread.so.0

Thread 3 (Thread 0x418f3950 (LWP 6826)):
#0  0x00007ff04c3fbe81 in nanosleep () from /lib/libpthread.so.0
#1  0x00000000004b8f4f in ?? ()
#2  0x00007ff04c3f43f7 in start_thread () from /lib/libpthread.so.0
#3  0x00007ff04bee2b2d in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x42142950 (LWP 6827)):
#0  0x00007ff04c3f8b99 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004bb585 in ?? ()
#2  0x00000000004bdb37 in ?? ()
#3  0x00000000004cbc03 in ?? ()
#4  0x000000000046b3c1 in ?? ()
#5  0x00000000004855c3 in ?? ()
#6  0x00000000004cb287 in ?? ()
#7  0x00000000004e07d2 in ?? ()
#8  0x00007ff04c3f43f7 in start_thread () from /lib/libpthread.so.0
#9  0x00007ff04bee2b2d in clone () from /lib/libc.so.6
#10 0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7ff04d0e17a0 (LWP 6825)):
#0  0x00007ff04c3fb5cb in read () from /lib/libpthread.so.0
#1  0x00007ff04c877a90 in ?? () from /usr/lib/libglib-2.0.so.0
#2  0x00007ff04c877f7e in ?? () from /usr/lib/libglib-2.0.so.0
#3  0x00007ff04c8788df in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#4  0x00007ff04c878d98 in g_spawn_command_line_sync ()
   from /usr/lib/libglib-2.0.so.0
#5  0x000000000051bbf9 in ?? ()
#6  0x000000000043dacd in ?? ()
#7  <signal handler called>
#8  0x00007ff04be87d50 in memcpy () from /lib/libc.so.6
#9  0x000000000042725b in mono_breakpoint_clean_code ()
#10 0x000000000043f78d in ?? ()
#11 0x000000000044005e in ?? ()
#12 0x0000000040fab15b in ?? ()
#13 0x0000000000000000 in ?? ()
#0  0x00007ff04c3fb5cb in read () from /lib/libpthread.so.0


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

```

---

### Post by gibsonsimswilson on 2008-05-26
Look at your menu

Applications >>> Accessories

---

### Post by chrisccoulson on 2008-05-26
gibsonsimswilson: Does Apport catch the crash (could you have a look in /var/crash to see if a crash report for F-spot exists). If not, could you try enabling Apport (you can enable it by editing /etc/default/apport as root, and setting enabled=1), then do:
```
sudo /etc/init.d/apport restart
```
...and then get F-Spot to crash again. You should then get a crash report which you can report on Launchpad.

---

### Post by gibsonsimswilson on 2008-05-26
Sorry - I am a newbie and what you posted just fused my brain !!!

Anything else I can do.... Or some more details instructions so I don't blow up my desktop..

Thanks, Gibby

---

### Post by chrisccoulson on 2008-05-26
Sorry!

Could you open a file browser and navigate to /var/crash, to check if there are any F-Spot crash reports in there (will be called something like '_usr_bin_f-spot.1000.crash). If there is one, right click on it and select Properties, and check the modified date/time to make sure it coincides roughly with when you crashed F-Spot. If the date/time is similar to when you crashed F-Spot just now, then double click on the '.crash' file in Nautilus. It will then open your web browser so you can report the crash on Launchpad.

If there is no crash report, then enable Apport to catch crashes. Open up a terminal (Applications -> Accessories -> Terminal), and do the following:
```
sudo nano /etc/default/apport
```
Use the arrow keys to navigate around. Change the following line:
```
enabled=0
```
...to...
```
enabled=1
```
...then press CTRL+X to exit. Press 'Y' to save, and then press ENTER to confirm the filename to save (/etc/default/apport).

Then restart Apport from the same terminal by typing:
```
sudo /etc/init.d/apport restart
```

Now you can try running f-spot again. Hopefully it will generate a crash report (you should even get a crash report notification)

---

### Post by gibsonsimswilson on 2008-05-26
Hi

Thanks for your time - did as you said (twice) but no crash report - run F- spot in terminal again and get the same as I posted before - sorry not much help am i:-(

Gibby

---

### Post by gibsonsimswilson on 2008-05-26
I uninstalled and reinstalled and I get the same problem :-(

---

### Post by cubeist on 2008-05-26
You could try installing the latest version of F-spot.  For me, the version that shipped with Hardy Heron was buggy.

Installing the latest version should be fairly straight forward, just a couple steps. For reference, here is the link I got this info from ([http://f-spot.org/How_To_Build_from_Release](http://f-spot.org/How_To_Build_from_Release))


First, go into synaptic and uninstall f-spot

Second, follow this link and download the latest version (0.4.3.1): [http://f-spot.org/Download#Releases](http://f-spot.org/Download#Releases)

Third, open a terminal and get all the pre-requisites. Fortunately for ubuntu this is as easy as typing
```
sudo apt-get build-dep f-spot 
```

After those files are installed you will also need:
```
sudo apt-get install automake1.9 build-essential intltool libtoo
```

Finally, right-click on the file you downloaded and choose "extract here"

Then in your terminal, navigate to the file you just extracted (you can change directories with the cd command, so if you downloaded the file to your desktop you would type cd ~/Desktop/name of extracted folder)

once in the extracted f-spot directory type ```
./configure
``` then after the configuration has run type ```
make
``` and then after it has been built type ```
sudo make install
```

Thats it, you should have the latest version in your applications menu and hopefully it will work!

---

### Post by chrisccoulson on 2008-05-26
> **cubeist said:**
> You could try installing the latest version of F-spot.  For me, the version that shipped with Hardy Heron was buggy.

Installing the latest version should be fairly straight forward, just a couple steps. For reference, here is the link I got this info from ([http://f-spot.org/How_To_Build_from_Release](http://f-spot.org/How_To_Build_from_Release))


First, go into synaptic and uninstall f-spot

Second, follow this link and download the latest version (0.4.3.1): [http://f-spot.org/Download#Releases](http://f-spot.org/Download#Releases)

Third, open a terminal and get all the pre-requisites. Fortunately for ubuntu this is as easy as typing
```
sudo apt-get build-dep f-spot 
```

After those files are installed you will also need:
```
sudo apt-get install automake1.9 build-essential intltool libtoo
```

Finally, right-click on the file you downloaded and choose "extract here"

Then in your terminal, navigate to the file you just extracted (you can change directories with the cd command, so if you downloaded the file to your desktop you would type cd ~/Desktop/name of extracted folder)

once in the extracted f-spot directory type ```
./configure
``` then after the configuration has run type ```
make
``` and then after it has been built type ```
sudo make install
```

Thats it, you should have the latest version in your applications menu and hopefully it will work!

No need to build from source. The latest version is in hardy-proposed (0.4.3.1-0ubuntu1) - you just need to enable that repository.

I'm not sure it'll fix the crash though. The problem is more likely to be with the mono runtime

---

### Post by cubeist on 2008-05-26
> **chrisccoulson said:**
> No need to build from source. The latest version is in hardy-proposed (0.4.3.1-0ubuntu1) - you just need to enable that repository.

Really?  I have proposed active and the latest version I have access to in the repos is 0.4.2-1ubuntu3.

Maybe because I am on amd64 and 0.4.3-1ubuntu1 has not been added to the 64bit repository?

[QUOTE=chrisccoulson;5048231
I'm not sure it'll fix the crash though. The problem is more likely to be with the mono runtime[/QUOTE]

Very true, if the latest f-spot doesn't run, there are lots of alternatives: Digikam, google picassa, etc.

---

### Post by chrisccoulson on 2008-05-26
I'm on amd64 too. It's definately there. Maybe you should try another mirror (they might not all be up to date yet)
```
chr1s@chris-desktop:~$ apt-cache policy f-spot
f-spot:
  Installed: 0.4.3.1-0ubuntu1
  Candidate: 0.4.3.1-0ubuntu1
  Version table:
 *** 0.4.3.1-0ubuntu1 0
        500 http://archive.ubuntu.com hardy-proposed/main Packages
        100 /var/lib/dpkg/status
     0.4.2-1ubuntu3 0
        500 http://archive.ubuntu.com hardy/main Packages
```

---

### Post by cubeist on 2008-05-26
> **chrisccoulson said:**
> I'm on amd64 too. It's definately there. Maybe you should try another mirror (they might not all be up to date yet)
```
chr1s@chris-desktop:~$ apt-cache policy f-spot
f-spot:
  Installed: 0.4.3.1-0ubuntu1
  Candidate: 0.4.3.1-0ubuntu1
  Version table:
 *** 0.4.3.1-0ubuntu1 0
        500 http://archive.ubuntu.com hardy-proposed/main Packages
        100 /var/lib/dpkg/status
     0.4.2-1ubuntu3 0
        500 http://archive.ubuntu.com hardy/main Packages
```

Yup, your right! I was using a mirror and missing out on lots of beta packages... I compiled most by hand over the last month!

---

### Post by Sef on 2008-05-27
> Sorry if this is in the wrong place.

I click F Spot in the Applications >> Graphics menu and nothing happens

Am I doing something wrong ?


Gibby, I had a [similar problem]("http://ubuntuforums.org/showthread.php?p=5054285#post5054285").  I fixed it by using the proposed updates.  System > Administration > Synaptic Package Manager > Settings > Repositories > Updates > click on 'Pre-released updates (hardy proposed)' > Close Repository menu > Reload > Mark All Upgrades > Apply (I believe) > after finishing, click close.

---

### Post by gibsonsimswilson on 2008-05-27
Hi

I did as you said and I can't open my emails - I lost evolution !

I get the "crashed application" icon and when I click it I get this message

No command (Exec) to launch

I post the problem on Launchpad - so I guess I wait fingers crossed now for a reply :-(

Gibby

---

### Post by gibsonsimswilson on 2008-05-27
Hi

I just reloaded evolution and now all works fine

I am a newbie - but I have to say this really is a wonderful experience :-)

With "you know what" - when something went wrong you just felt lost - not anymore

Thank you for your help and support

Gibby

---

### Post by Sef on 2008-05-28
> I just reloaded evolution and now all works fine

I am a newbie - but I have to say this really is a wonderful experience

With "you know what" - when something went wrong you just felt lost - not anymore

Thank you for your help and support


Glad to hear all is fine.  

You're welcome.

---

