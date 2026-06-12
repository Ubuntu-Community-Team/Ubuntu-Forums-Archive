---
title: "wxPython"
date: 2007-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by orbit on 2007-01-20
Hello,

I need the latest version of wxPython (2.8.0.1).  Does anyone know where I can get a deb for 64-bit Edgy.  I've looked but can only find an apt repository for i386.


Thanks

---

### Post by marianix on 2007-02-04
This worked for me (ubuntu edgy eft amd64):

[LIST=1]
[*] Update system Software: System->Administration->Update Manager (I don't now if this is a necessary step, just it worked for me)
[*] Add wxWindows and wxPython repositories to /etc/apt/sources.list: System->Administration->Software Sources, Other Providers:
```

deb http://apt.tt-solutions.com/ubuntu/ edgy main
deb http://wxpython.wxcommunity.com/apt/ubuntu/dapper /

```
[*] Add trusted keys of wxWindows, in a terminal type:
```

sudo -i
wget http://www.tt-solutions.com/vz/key.asc -O- | apt-key add -

```
[*] Install the packages, using synaptic or command line: 
```

sudo aptitude update
sudo apt-get install python-wxgtk2.8 python-wxtools wx2.8-i18n

```
[/LIST]

I get this instructions from official sites:
[LIST]
[*][http://www.wxwidgets.org/downloads/](http://www.wxwidgets.org/downloads/) (Current Stable Release, Binaries, Ubuntu section)
[*][http://www.wxpython.org/download.php](http://www.wxpython.org/download.php) (Ubuntu section)
[/LIST]

I've get some warnings on wx-docs but everything is working ok (PyCrust appeared in Applications->Programming menu) and demo.py from wxPython-demo-2.8 worked great.

Please note that I'm new to ubuntu (just one day) and my desktop is in spanish language.

Regards
Mariano

---

