---
title: "4Suite failure"
date: 2008-11-15
forum: x86 64-bit Users
---

### Post by netdog888 on 2008-11-15
Hello,

I'm having trouble running an existing app (built on Python 2.5 in 32bit world) and it looks like the python-4Suite-xml package is my problem.  When I try to import the XSLT parts of the app (See below):

>>> import from Ft.Xml.Xslt.Processor import Processor

 [I]  File "/usr/lib/python2.5/site-packages/Ft/Xml/__init__.py", line 160, in <module>
    from Ft.Xml.Lib.XmlString import SplitQName
ImportError: /usr/lib/python2.5/site-packages/Ft/Xml/Lib/XmlString.so: undefined symbol: PyUnicodeUCS4_FromObject  
[/I]

I have tried to remove and reinstall but that had no effect and I've tried installing from source and from easy_install but the setup.py programs hangs (a 4Suite problem I'm guessing) so I'm pretty well stuck.  Any clues would be greatly appreciated

Thanks Gang!
'

---

