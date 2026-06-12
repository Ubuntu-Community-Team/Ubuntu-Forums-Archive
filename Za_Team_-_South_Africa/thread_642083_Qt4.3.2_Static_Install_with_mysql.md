---
title: "Qt4.3.2 Static Install with mysql"
date: 2007-12-16
forum: Za Team - South Africa
---

### Post by creatron on 2007-12-16
I tried to install qt4.3.2 using in a scrip file

./configure -prefix /usr/local/Trolltech/Qt-4.3.2.static -static -release -qt-sql-mysql  -I/usr/include/mysql -L/usr/lib/mysql -v

 (note 1. this script compile correctly in openSuse10.3.
          2. Source downloaded from Trolltech. 
          3. if I do the standard ./configure it works but I need to access mysql).

The output is as follows:

gerrie@ubuntu_3G:~/qt/qt-x11-opensource-src-4.3.2$ ./config_release_static  > static.log
yes
floatmath.cpp:3: warning: unused parameter ‘argc’
floatmath.cpp:3: warning: unused parameter ‘argv’
libjpeg.cpp: In function ‘int main(int, char**)’:
libjpeg.cpp:10: warning: ‘cinfo’ is used uninitialized in this function
libtiff.cpp:1:20: error: tiffio.h: No such file or directory         .....            (1)
libtiff.cpp:4:6: error: #error "Required libtiff not found"
libtiff.cpp: In function ‘int main(int, char**)’:
libtiff.cpp:11: error: ‘tdata_t’ was not declared in this scope
libtiff.cpp:11: error: expected `;' before ‘buffer’
libtiff.cpp:12: error: ‘buffer’ was not declared in this scope
libtiff.cpp:12: error: ‘_TIFFfree’ was not declared in this scope
make: *** [libtiff.o] Error 1
ibase.cpp:1:19: error: ibase.h: No such file or directory         ....           (2)
make: *** [ibase.o] Error 1
odbc.cpp:1:17: error: sql.h: No such file or directory
odbc.cpp:2:20: error: sqlext.h: No such file or directory
make: *** [odbc.o] Error 1
dbus.cpp:2:23: error: dbus/dbus.h: No such file or directory  ....           (3)
dbus.cpp:5:2: error: #error Needs at least dbus version 1
dbus.cpp: In function ‘int main(int, char**)’:
dbus.cpp:10: error: ‘dbus_shutdown’ was not declared in this scope
make: *** [dbus.o] Error 1
glib.cpp: In function ‘int main(int, char**)’:
glib.cpp:14: warning: ‘pollfd’ is used uninitialized in this function
ptrsizetest.cpp: In function ‘int main(int, char**)’:
ptrsizetest.cpp:18: error: ‘PointerSize’ is not a member of ‘QPointerSizeTest<4>’
make: *** [ptrsizetest.o] Error 1
cat: .qmake.vars: No such file or director

1. I cannot find the mysql-dev.deb to install that should have the header files
2. libTIFF supplied with Gutsy is installed.
3. All mysql packages as on the 10.7 image is installed.
6. The header files for mysql in /usr/lib and /usr/include seem to be intact.

Where can I get the development headers(with the correct name) to be installed
Thanks in advance.

---

