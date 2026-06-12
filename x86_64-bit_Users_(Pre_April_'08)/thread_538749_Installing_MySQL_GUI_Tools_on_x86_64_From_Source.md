---
title: "Installing MySQL GUI Tools on x86_64 From Source"
date: 2007-08-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by MicahCarrick on 2007-08-30
I had the problem with MySQL Administrator crashing at startup and MySQL Query Browser crashing periodically when using the packages installed from apt-get.

I read the installing from source works better (I also tried the generic x86_64 binaries from MySQL).

I removed repository packages and installed dependencies using:
```
sudo aptitude remove mysql-admin mysql-admin-common mysql-query-browser mysql-query-browser-common
sudo aptitude install libx11-dev libc6-dev libstdc++6-4.0-dev libglib2.0-dev libgtk2.0-dev libglade2-dev libsigc++-2.0-dev libglibmm-2.4-dev libgtkmm-2.4-dev libpcre3-dev pkg-config libxml2-dev libmysqlclient15-dev

```

I then downloaded and extracted the MySQL GUI Tools tarball:
```
wget mysql-gui-tools-5.0r12.tar.gz
tar -xcf mysql-gui-tools-5.0r12.tar.gz
cd mysql-gui-tools-5.0r12/mysql-common
```

I applied the patch as described in bug 27519 ([http://bugs.mysql.com/bug.php?id=27519):](http://bugs.mysql.com/bug.php?id=27519):)
```
wget http://bugs.mysql.com/file.php?id=6068
patch < mysql-gui-common-build.patch
```

That patch fixes the error:
```
checking for unicode support in pcre... ./configure: line 23497: syntax error near
unexpected token `}'
./configure: line 23497: `echo "${ECHO_T}yes" >&6; }'
```

I then compile and build as described in the manual using autogen:
```
chmod a+x autogen.sh
./autogen.sh
make
sudo make install
```

Although everything goes okay, there's a warning during the configure that worries me:
```
config.status: WARNING:  po/Makefile.in.in seems to ignore the --datarootdir setting
```

I think this is significant because when I build and install mysql-administrator, the same warning is seen. Then when I try to run mysql-administrator, I get this:

```
(mysql-administrator-bin:26600): libglade-WARNING **: could not find glade file '/usr/local//usr/local/share/mysql-gui/common/preferences.glade'
terminate called after throwing an instance of 'MGGladeXML::Error'
Aborted (core dumped)

```

So it seems to be putting an extra prefix in front of the path when looking for the glade file. 

Any suggestions?

---

### Post by MicahCarrick on 2007-08-30
Just as an FYI...

I modified get_prefix() in main.cc in the /source/linux/ directory as follows:
[CODE]std::string get_prefix()
{
  return "";
  /*
  if (getenv(PATH_ENV))
    return std::string(getenv(PATH_ENV))+"/";
  else
    return PREFIX"/";
  */
}[CODE]

This gets it to run though it's a cheap trick. In any case, the application still seg faults so I'm not any better off than I was using the generic binaries from MySQL.

---

