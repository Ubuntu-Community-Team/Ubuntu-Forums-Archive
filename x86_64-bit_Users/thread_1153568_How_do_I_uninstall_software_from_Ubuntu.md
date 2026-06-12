---
title: "How do I uninstall software from Ubuntu"
date: 2009-05-08
forum: x86 64-bit Users
---

### Post by teixidoj on 2009-05-08
My more specific question what be, how do I uninstall applications that I download myself in Ubuntu?

John...

---

### Post by Sef on 2009-05-08
How was it installed: deb package, source code or other?

---

### Post by sunhunter on 2009-05-09
If it was a tar related  file so you  extracted the tar , then compiled the program with ./configure ( or any ./install name) ,followed with  make and then make install (Root access needed)
Then you can uninstall it with make uninstall. so simple start terminal , CD to the path where-from the program is installed, once there do a make uninstall.

If it was a .deb file, then you can remove it with the Synaptic package manager.

The best way to install, uninstall is start with the synaptic package manager.
Second best way is with a .deb file and with the GDebi deb manager
(right click on .deb file)..remember that installed .deb's can be removed from within Synaptic also.

The last way is compile the program , terminal mode is needed in such case.

And remember, uninstall follows usual the same path , except .deb files.
That .deb installed program can be removed from synaptic is also cause Ubuntu is based on debian and .deb are debian packages.

---

### Post by pixel :-) on 2009-05-09
If you really need to compile, use checkinstall, instaid of make install, it will automatically generate a minimal deb package.

If it was an third party installer, you need to use the given uninstall script, other wise you have to do it by hand, by reading what the installer did.

A simple way to generate debs with checkinstall, is to put the filles in a recreated folder tree, only the folders that will actually have something in, open a normal deb in the archive manager you'll understand what i mean. then compress it in tar.gz and passe it as an argument to checkinstall

checkinstall yourarchive.tar.gz

---

### Post by teixidoj on 2009-05-09
Honestly all of the above.

---

### Post by pixel :-) on 2009-05-10
your question wasn't very precise.

---

