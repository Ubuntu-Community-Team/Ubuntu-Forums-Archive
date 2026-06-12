---
title: "need help 32bit python"
date: 2009-08-08
forum: x86 64-bit Users
---

### Post by dhysk on 2009-08-08
I'm trying to get FSEconomy to work with X-Plane 9.  The script uses python2.5 and I believe the error has to do with the fact its tring to use the 64bit not the 32bit dependencies.  I have all the 32bit libs installed, however the two files mentioned in the log 'select.so' and 'time.so' are not in the 32 bit libs contained under '/use/lib32/python2.5/'.  So I'm thinking I have to install a separate 32bit python or get X-plane to use the 32bit libs somehow.  I'm still a bit new with linux, I learn slow, but any help on this would be greatly appreciated.

here is the error log from the PythonInterface25 script.

```

+++ LOGGING STARTED +++
PythonInterface v2.42 - Sandy Barbour 2006
Before Py_Initialize()
After Py_Initialize()
Before Modules Init
Using path below for script path
/home/rick/X-Plane 9/Resources/plugins/PythonScripts
Traceback (most recent call last):
  File "/home/rick/X-Plane 9/Resources/plugins/PythonScripts/PI_xfse.py", line 10, in <module>
    from httplib import *
  File "/usr/lib/python2.5/httplib.py", line 70, in <module>
    import mimetools
  File "/usr/lib/python2.5/mimetools.py", line 5, in <module>
    import rfc822
  File "/usr/lib/python2.5/rfc822.py", line 74, in <module>
    import time
ImportError: /usr/lib/python2.5/lib-dynload/time.so: wrong ELF class: ELFCLASS64
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 38, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.5/site-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.5/site-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.5/subprocess.py", line 401, in <module>
    import select
ImportError: /usr/lib/python2.5/lib-dynload/select.so: wrong ELF class: ELFCLASS64

Original exception was:
Traceback (most recent call last):
  File "/home/rick/X-Plane 9/Resources/plugins/PythonScripts/PI_xfse.py", line 10, in <module>
    from httplib import *
  File "/usr/lib/python2.5/httplib.py", line 70, in <module>
    import mimetools
  File "/usr/lib/python2.5/mimetools.py", line 5, in <module>
    import rfc822
  File "/usr/lib/python2.5/rfc822.py", line 74, in <module>
    import time
ImportError: /usr/lib/python2.5/lib-dynload/time.so: wrong ELF class: ELFCLASS64
'PI_xfse' failed to load
--- LOGGING STOPPED ---
```

any help would be greatly appreciated.

---

### Post by dhysk on 2009-08-09
well I'm about out of ideas, anybody else?

---

### Post by dhysk on 2009-08-09
Well I got the client to load and was able to log into FSE. I haven't Flown yet though. Basically all I did was d/l and extract the i386 .debs for python2.5, python2.5-dev, and python2.5-minimal. I extracted them all into a separate directory `downloads/ I think. Then I renamed the libs in /usr/lib/python2.5 to /usr/lib/apython2.5 then I copied the lib folder from `downlads/usr/lib/python2.5 to /usr/lib/ and it worked. Unfortunately to avoid problems I will have to do this and undo this every time I want to play. So the question is how do I get it to redirect it's self?

---

