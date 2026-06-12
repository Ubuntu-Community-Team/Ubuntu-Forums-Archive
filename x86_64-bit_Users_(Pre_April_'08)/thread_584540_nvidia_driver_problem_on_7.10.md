---
title: "nvidia driver problem on 7.10"
date: 2007-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by sles on 2007-10-21
Hello!

I uprgaded 7.04 to 7.10 and
I can't use nvidia driver on 7.10 -
if I install nvidia-glx-new or nvidia-glx then X server doesn;t start because  of kernel module and driver version mismatch.

If I install nvidia-glx-legacy than X starts, but there is no glx:
 glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual


And I can' start restricted driver manager:
 sudo restricted-manager 
[sudo] password for dm:
Traceback (most recent call last):
  File "/usr/bin/restricted-manager", line 42, in <module>
    rm = RestrictedManager()
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 53, in __init__
    RestrictedManagerCommon.__init__(self,args,opts)
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerCommon.py", line 197, in __init__
    self.launch_manager()
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 151, in launch_manager
    self.ManagerWindow(self.xml, self.handlers, self)
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 209, in __init__
    self.reset_model()
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 262, in reset_model
    self.parent.set_title_label(self.xml.get_widget('label_heading'), any_enabled)
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 122, in set_title_label
    (bold, normal) = RestrictedManagerCommon.title_label(self, in_use)
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerCommon.py", line 242, in title_label
    'these drivers.') % {'os': get_os_name()}
KeyError: u's'

Any ideas?

btw, I think this is ams64 specific problem- my colleague did uprgade from 7.04 to 7.10 on x86 without such problem...

---

### Post by Cappy on 2007-10-21
Try ```

sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r`

```

And no, it isn't a 64-bit problem. A problem on a 64-bit machine doesn't mean it is a 64-bit problem.

---

### Post by sles on 2007-10-21
Thank you!

This helps :-)
=D>

---

### Post by sot3 on 2007-10-22
So what does this mean?

$ sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nvidia-glx-dev for regex 'nvidia-glx*'
Note, selecting nvidia-glx-ia32 for regex 'nvidia-glx*'
Note, selecting nvidia-glx-new for regex 'nvidia-glx*'
Note, selecting nvidia-glx-src for regex 'nvidia-glx*'
Note, selecting nvidia-glx-legacy-dev for regex 'nvidia-glx*'
Note, selecting nvidia-glx-legacy for regex 'nvidia-glx*'
Note, selecting nvidia-glx for regex 'nvidia-glx*'
Note, selecting nvidia-glx-new-dev for regex 'nvidia-glx*'
Package nvidia-settings is not installed, so not removed
The following packages were automatically installed and are no longer required:
  snort-rules-default libmail-spf-query-perl libnet-cidr-lite-perl libprelude2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-generic* linux-restricted-modules-2.6.20-15-generic*
  linux-restricted-modules-2.6.20-16-generic* linux-restricted-modules-2.6.22-14-generic*
  linux-restricted-modules-generic* nvidia-glx nvidia-kernel-2.6.20-15-generic*
  nvidia-kernel-2.6.20-16-generic* nvidia-kernel-common*
0 upgraded, 0 newly installed, 9 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 184MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 137668 files and directories currently installed.)
Removing nvidia-glx ...
rm: cannot remove `/usr/lib/libGL.so': No such file or directory
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1.2' with
  different file `/usr/lib/nvidia/libGL.so.1.2.xlibmesa', not allowed
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Cappy on 2007-10-22
Run the other lines and see what happens:
```

sudo apt-get --purge remove nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r`

```

or if that fails
```

sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r`

```

Somehow it never completed the installation of nvidia-glx.

---

### Post by sot3 on 2007-10-23
Well, everything I tried with apt-get, even if I attempted to install or remove something unrelated to nvidia, returned me to the same message:

rename involves overwriting `/usr/lib/libGL.so.1.2' with different file `/usr/lib/nvidia/libGL.so.1.2.xlibmesa', not allowed

In Synaptic I saw that nvidia-glx was marked for removal, and there was nothing I could do to change that, and it wouldn't let me make any other changes either.  I finally gave up and simply did

$ sudo mv /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1.2.BAD

and tried again.  Everything seemed to complete successfully after that.

---

### Post by piciu3175@yahoo.com on 2007-10-24
I used envy to install my nvidia driver. It worked fine for me and i think that for a beginner is the best choice.

---

### Post by sot3 on 2007-10-24
Funny you should mention that.  I'm pretty sure I used envy to install the nvidia driver many moons ago (maybe it was easyubuntu?), and I wondered if that was the reason that the nvidia install failed during the 7.10 upgrade process.  That seemed to cause some other things to fail as well, but I'm still sorting things out.

I haven't even figured out where the upgrade log file is located yet (no time!).

---

