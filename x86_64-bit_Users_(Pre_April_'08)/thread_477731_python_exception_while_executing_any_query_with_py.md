---
title: "python exception while executing any query with python-mysqldb"
date: 2007-06-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by dervish on 2007-06-18
I have encountered a serious problem with the 64bit version of python-mysqldb coming with feisty.
I cannot execute even a simple SQL query (using pyformat placeholders).

import MySQLdb
>>> MySQLdb.__version__
'1.2.1_p2'
>>> c = MySQLdb.connect("localhost", "root", "", "mydatabase")
>>> c.cursor().execute("SELECT * FROM table_name WHERE table_name.id = %(id)s", {'id':1})

This results in a python execption:
Exceptions.KeyError: 'id'

The same code works on the 32bit version and on other 64bit linux distros with the same version of python-mysqldb. It seems also to be already fixed in the gutsy package, which provides version 1.2.2.
Is there a workaround for the current  feisty python-mysqldb environment?

Cheers
dervish

---

### Post by incubus on 2007-06-18
Hmm, it seems that installing the gutsy package is out of question, because of dependencies:
[http://packages.ubuntu.com/gutsy/python/python-mysqldb](http://packages.ubuntu.com/gutsy/python/python-mysqldb)

What if you install through setup tools (easy_install)?

The latest version is available on PyPI:
[http://www.python.org/pypi/MySQL-python/1.2.2](http://www.python.org/pypi/MySQL-python/1.2.2)

If you have to compile, you may have to have build-essential and python-dev.

incubus

---

### Post by dervish on 2007-06-19
thanks for the reply. I dist-upgraded the whole system to gutsy and now I see no problems there. However, I think this bug is quite serious so that it should be patched as soon as possible. What is the best way to report this bug (or to check if it hasn't been already reported)?

Dervish

---

### Post by incubus on 2007-06-19
dervish,

Launchpad, definitely.  Could this be related?
[https://bugs.launchpad.net/ubuntu/+source/python-mysqldb/+bug/109336](https://bugs.launchpad.net/ubuntu/+source/python-mysqldb/+bug/109336)

The key is to discuss the issue there and get the attention of developers.  I can try to reproduce the bug here.  The thing for me is that I don't use MySQL, I use PostgreSQL.  I would have to install it.

incubus

---

### Post by dervish on 2007-06-20
I also discovered the same behavior like described in the bug report.
I think this launchpad post is a good starting point to initiate a discussion.

dervish

---

### Post by dervish on 2007-06-20
I just opened a launchpad bug report:
[https://bugs.launchpad.net/ubuntu/+source/python-mysqldb/+bug/121300](https://bugs.launchpad.net/ubuntu/+source/python-mysqldb/+bug/121300)

---

