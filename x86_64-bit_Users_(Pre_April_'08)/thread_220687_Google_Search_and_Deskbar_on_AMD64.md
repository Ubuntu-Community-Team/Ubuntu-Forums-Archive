---
title: "Google Search and Deskbar on AMD64"
date: 2006-07-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by chessforce on 2006-07-21
If Google search within Deskbar was not working for you, you can try editing /usr/lib/python2.4/site-packages/SOAPpy/fpconst.py and change

```
tmp = struct.unpack('ll',struct.pack('d', dval))
```

to 

```
tmp = struct.unpack('ii',struct.pack('d', dval))
```

in the ```
_double_as_longs
``` function.

P.S. The reverse process was suggested at [http://ubuntuforums.org/showpost.php?p=929397&postcount=10](http://ubuntuforums.org/showpost.php?p=929397&postcount=10) to fix the problem.  However, the link that post contains suggests otherwise as stated above.

---

### Post by simbaB on 2006-12-11
You must also delete any Python bytecode for this file. I don't know if Ubuntu adopted the Debian python-central/python-support infrastructure, but in the case of python-soappy in Debian 'sid' you need to make the change noted above and delete /var/lib/python-support/python2.4/SOAPpy/fpconst.pyc too. Python seems not to notice the change, probably due to the symbolic link (mtime isn't updated), and uses the old bytecode.

---

