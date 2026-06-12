---
title: "playonlinux won´t start"
date: 2017-10-08
forum: Wine
---

### Post by rosika on 2017-10-08
Hello altogether,


I have problems starting playonlinux and wonder whether you could help.


I have playonlinux v. 4.2.12. Yet when trying to start the programme via the terminal I get the following message:


```
Looking for python... 2.7.12 - wxversion(s): 3.0-gtk2
/usr/share/playonlinux/bash/find_python: Zeile 58:  9558 Ungültiger Maschinenbefehl   "$POL_PYTHON" "$POLDIR/python/check_python.py"
failed tests
Looking for python2.7... 2.7.12 - wxversion(s): 3.0-gtk2
/usr/share/playonlinux/bash/find_python: Zeile 58:  9564 Ungültiger Maschinenbefehl   "$POL_PYTHON" "$POLDIR/python/check_python.py"
failed tests
Looking for python2.6...
Looking for python2... 2.7.12 - wxversion(s): 3.0-gtk2
/usr/share/playonlinux/bash/find_python: Zeile 58:  9571 Ungültiger Maschinenbefehl   "$POL_PYTHON" "$POLDIR/python/check_python.py"
failed tests
Please install python before trying to run this program



```According to the output of the terminal it seems that  python ist´t installed - which simply is not true.
Here are my python versions:


```
ii  python                                        2.7.11-1                                     amd64        interactive high-level object-oriented language (default version)
ii  python2.7                                   2.7.12-1ubuntu0~16.04.1      amd64        Interactive high-level object-oriented language (version 2.7)
ii  python3                                      3.5.1-3                                       amd64        interactive high-level object-oriented language (default python3 version)
ii  python3.5                                   3.5.2-2ubuntu0~16.04.3        amd64        Interactive high-level object-oriented language (version 3.5)



```

Is there any way to get playonlinux started?


Thanks a lot in advance for your help.
Greetings
Rosika  :confused:

P.S.:
my system: Linux/Lubuntu 16.04.3 LTS, 64bit

---

### Post by fredwntr1 on 2017-10-29
Did you install this from the terminal or download the .Deb from the website?

---

