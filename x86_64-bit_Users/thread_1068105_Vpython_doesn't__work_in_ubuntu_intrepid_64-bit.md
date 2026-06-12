---
title: "Vpython doesn't  work in ubuntu intrepid 64-bit"
date: 2009-02-12
forum: x86 64-bit Users
---

### Post by giannisfs on 2009-02-12
Firstly I  opened to synaptic  package manager
and i installed the python-numeric the python-numarray
and the Python-visual.

But when i tried in the python interpreter to import visual

i got the following error:
```
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/site-packages/visual/__init__.py", line 15, in <module>
    import array_backend
  File "/usr/lib/python2.5/site-packages/visual/array_backend.py", line 50, in <module>
    raise RuntimeError, "Neither Numeric nor numarray could be found."
RuntimeError: Neither Numeric nor numarray could be found.
```

so i opened the array_backend.py file
and  i saw that it in the top function at line 8 and 6 
it calls :
**cvisual._init_numeric_impl()**
and
**cvisual._init_numarray_impl()**

which those don't exist in the cvisual module
"**/usr/lib/python2.5/site-packages/cvisualmodule.so.1.0.0**"
and that's propably (or maybe obvious) why i get an 
**AttributeError: 'module' object has no attribute '_init_numeric_impl'**
when i imported from the python interpreter

Also when I typed :
**python -c 'import sys; print sys.path'**
i got the 
```
['', '/usr/lib/python2.5/site-packages/nose-0.10.4-py2.5.egg', '/usr/lib/python2.5', '/usr/lib/python2.5/plat-linux2', '/usr/lib/python2.5/lib-tk', '/usr/lib/python2.5/lib-dynload', '/usr/local/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages/Numeric', '/usr/lib/python2.5/site-packages/PIL', '/usr/lib/python2.5/site-packages/gst-0.10', '/var/lib/python-support/python2.5', '/usr/lib/python2.5/site-packages/gtk-2.0', '/var/lib/python-support/python2.5/gtk-2.0', '/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode']
```
and there was not **/usr/share/pyshared **in the list
so i thought 
"""it might be a problem with the links from **/usr/lib/python2.5/site-packages/visual** pointing to  **/usr/share/pyshared/visua**""" 
and i tried to "correct it" by adding in sys.path the absolute path
**sys.append('/usr/share/pyshared/visual')**
**[SIZE="4"]but again[/SIZE]**
i got :
```
...
RuntimeError: Neither Numeric nor numarray could be found.

```


i was very disappointed so i tried to install the newest Vpython but even if a got all dependencies satisfied it wouldn't work . i couldn't compiled without errors ... :(

Finally i tried to compile the "stable " release" of vpython "visual-3.2.9"
and again not working:confused::(

[SIZE="2"]**So any suggestions how to make it work ?**[/SIZE]

---

