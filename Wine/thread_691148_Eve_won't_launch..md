---
title: "Eve won't launch."
date: 2008-02-08
forum: Wine
---

### Post by Thaeos on 2008-02-08
Hi there.

After downloading the official .deb and installing eve, when I type 'eve' into a terminal this is what I get:

> eve
Single-user install...
This is the update checker...
Running /home/daniel/.cedega/.updater/cedega_updater.py
Running... /home/daniel/.cedega/.ui/runGUI
/home/daniel/.cedega/.winex_ver/winex-eve-000072/bin/winex3: 160: /home/daniel/.cedega/.winex_ver/winex-eve-000072/winex/bin/pthreads_stack_test: not found
[: 160: 0: unexpected operator
/lib/ld-linux.so.2: could not open

After looking into it a bit, i made a symbolic link called ld-linux-so.2 that points to ld-2.6.1.so ... then after trying again I get this:

> eve
Single-user install...
This is the update checker... 
Running /home/daniel/.cedega/.updater/cedega_updater.py
Running... /home/daniel/.cedega/.ui/runGUI
/home/daniel/.cedega/.winex_ver/winex-eve-000072/bin/winex3: 160: /home/daniel/.cedega/.winex_ver/winex-eve-000072/winex/bin/pthreads_stack_test: Accessing a corrupted shared library
[: 160: 0: unexpected operator
/lib/ld-linux.so.2: not an i386 ELF binary... don't know how to load it

I looked for a lib32 dir but there doesn't seem to be one. I'm supposing I have to install a 32bit version of this library.

Any suggestions?

---

### Post by Thaeos on 2008-02-08
OK,

I installed getlibs from [here, ]("http://ubuntuforums.org/showthread.php?t=474790")and after doing so just opened up a terminal and typed getlibs, which installed a bunch of 32bit stuff which worked fine.

Then i typed 'sudo ln -s /lib32/ld-2.6.1.so /lib/ld-linux.so.2' to create a symbolic link to the 32bit library that it's looking for.

Open up a terminal and type eve, I see the splash screen but after it disappears and the fullscreen logon screen is up, everything is blank/greyed out, and it quits after about 2 seconds.

This is what happens in the terminal while this is going on:

> eve
Single-user install...
This is the update checker... 
Running /home/daniel/.cedega/.updater/cedega_updater.py
Running... /home/daniel/.cedega/.ui/runGUI
daniel@daniel-desktop:/lib32$ 
0004:  Bad stuff: client ignore setting select events for 0x9005083c to 1
0004:  Bad stuff: client ignore setting select events for 0x9005083c to 0
0004:  Bad stuff: client ignore setting select events for 0x9005083c to 1
0004:  Bad stuff: client ignore setting select events for 0x9005083c to 0
0004:  Bad stuff: client ignore setting select events for 0x9005083c to 1
0004:  Bad stuff: client ignore setting select events for 0x9005083c to 0
0004:  Bad stuff: client ignore setting select events for 0x9005083c to 1
0004:  Bad stuff: client ignore setting select events for 0x9005083c to 0
0004:  Bad stuff: client ignore setting select events for 0x9005083c to 1
0004:  Bad stuff: client ignore setting select events for 0x9005083c to 0
0004:  Bad stuff: client ignore setting select events for 0x9005083c to 1
0004:  Bad stuff: client ignore setting select events for 0x9005083c to 0
0004:  Bad stuff: client ignore setting select events for 0x9005083c to 1
0004:  Bad stuff: client ignore setting select events for 0x9005083c to 0
0004:  Bad stuff: client ignore setting select events for 0x9005083c to 1
0004:  Bad stuff: client ignore setting select events for 0x9005083c to 0
0004:  Bad stuff: client ignore setting select events for 0x9005083c to 1
0004:  Bad stuff: client ignore setting select events for 0x9005083c to 0
And it just keeps repeating. Also I noticed that my system fails the OpenGL Direct Rendering test in the Eve Online Configuration, although I don't know why. I'm using an 8800gt with the latest linux drivers fine ...

---

### Post by Perfect Storm on 2008-02-08
Have you tried with;

```
sudo aptitude install ia32-libs
```

first? To get the most common 32 bit libs

---

### Post by Thaeos on 2008-02-08
Well I tried it and this is the output:

> sudo aptitude install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done    

So I already them ...

---

### Post by Perfect Storm on 2008-02-08
> /home/daniel/.cedega/.winex_ver/winex-eve-000072/bin/winex3: 160: /home/daniel/.cedega/.winex_ver/winex-eve-000072/winex/bin/pthreads_stack_test: Accessing a corrupted shared library

I was thinking it might be a corrupt download. Try download it again, so you can rule that out.

---

### Post by DestroyMicroshaft on 2008-02-15
This is the output after I installed the client.

> derek@derek-desktop:~$  eve
Single-user install...
This is the update checker... 
Running /home/derek/.cedega/.updater/cedega_updater.py
/home/derek/.cedega/.updater/gddb.py:26: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
Traceback (most recent call last):
  File "/home/derek/.cedega/.updater/cedega_updater.py", line 72, in <module>
    updater_obj = updater.Updater(game_name)
  File "/home/derek/.cedega/.updater/updater.py", line 68, in __init__
    self.support_contact = misc_updater_utils.get_support_contact(game_name, self.manifest_url)
  File "/usr/lib/eve/misc_updater_utils.py", line 352, in get_support_contact
    fp = urllib.urlopen(manifest_url)
  File "/usr/lib/python2.5/urllib.py", line 82, in urlopen
    return opener.open(url)
  File "/usr/lib/python2.5/urllib.py", line 190, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.5/urllib.py", line 325, in open_http
    h.endheaders()
  File "/usr/lib/python2.5/httplib.py", line 856, in endheaders
    self._send_output()
  File "/usr/lib/python2.5/httplib.py", line 728, in _send_output
    self.send(msg)
  File "/usr/lib/python2.5/httplib.py", line 695, in send
    self.connect()
  File "/usr/lib/python2.5/httplib.py", line 663, in connect
    socket.SOCK_STREAM):
IOError: [Errno socket error] (-2, 'Name or service not known')
Running... /home/derek/.cedega/.ui/runGUI
/home/derek/.cedega/.ui/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
/home/derek/.themes/Clearlooks_blackgreen/gtk-2.0/gtkrc:53: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
derek@derek-desktop:~$ ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM /dev/mixer
0005:  Bad stuff: client ignore setting select events for 0x900514ac to 1
0005:  Bad stuff: client ignore setting select events for 0x900514ac to 0
0005:  Bad stuff: client ignore setting select events for 0x900514ac to 1
0005:  Bad stuff: client ignore setting select events for 0x900514ac to 0
0005:  Bad stuff: client ignore setting select events for 0x900514ac to 1
0005:  Bad stuff: client ignore setting select events for 0x900514ac to 0


Not sure what the issue is here, cant get it to work any way I try.

---

### Post by Kivech on 2008-02-15
Right, I have the same issue with getting EvE going.

In my case however I'm running an ATI Radeon x1900 vid card. So for sure it's not our video cards otherwise one of us wouldn't have this problem.

I'm keeping an eye out here, because also I would like to be able to get EvE going. Especially since I have a paid account. :P

Kivech

---

### Post by DestroyMicroshaft on 2008-02-15
Ive tried this every way I can, win installer with wine and cedega, cedega wrapper, all sorts of arguments and nothing, same thing happens every time, starts up shows the splash screen, and goes black with no response.

It sux, guess Ill stick with Vendetta till something changes.

---

### Post by Ender Black on 2008-02-25
have you copied at copy of Arial.ttf to your ~/user/.wine/drive_c/Windows/fonts folder?


Usually splash and crash is caused by that...I can't get the cedega "official Linux Client" to work, but wine version .55 works just fine after you add the arial fonts.

---

