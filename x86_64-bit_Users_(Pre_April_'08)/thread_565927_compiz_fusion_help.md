---
title: "compiz fusion help?"
date: 2007-10-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by markp1989 on 2007-10-02
i installed compiz fusion from this guide:

[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

all i changed was the source, i added -amd64 to the end, the install goes fine, but when i try and run compiz fusion i get a bunch of errors and my windows borders disappear 
those are the errors i get
> 
mark@mark-desktop:~$ compiz --replace -c emerald &
[1] 9361
mark@mark-desktop:~$ /usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libccp.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ccp'

so i try to run compiz configuration manager from the terminal to see if i can disable the plugin. and i get another load of errors 

> mark@mark-desktop:~$ ccsm
GConf backend: There is an unsupported value at path /apps/compiz/general/allscreens/options/run_command_terminal_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/general/allscreens/options/run_command_terminal_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
mark@mark-desktop:~$ 

can some one tell me how i can get around this, and i will be extremely thankful

---

### Post by markp1989 on 2007-10-02
> mark@mark-desktop:~$ ccsm
GConf backend: There is an unsupported value at path /apps/compiz/general/allscreens/options/run_comman d_terminal_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/general/allscreens/options/run_comman d_terminal_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Traceback (most recent call last):
File "/usr/bin/ccsm", line 45, in <module>
idle = ccm.IdleSettingsParser(context)
File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
mark@mark-desktop:~$

i managed to sort this out by navigating to  "/apps/compiz/general/allscreens/options/run_comman d_terminal_key" in config_editor and typing "disabled" in the value field, and now i get a different error 

> mark@mark-desktop:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: /var/lib/python-support/python2.5/compizconfig.so: undefined symbol: ccsStringToEdges


i thank you in advanced for any help you can give me with this problem

---

### Post by jusmurph on 2007-10-03
I recommend you simply use the repo found here to install it:
[http://ubuntuforums.org/showthread.php?t=196093](http://ubuntuforums.org/showthread.php?t=196093)

It is found under the expiremental section.

It simply just works.

---

