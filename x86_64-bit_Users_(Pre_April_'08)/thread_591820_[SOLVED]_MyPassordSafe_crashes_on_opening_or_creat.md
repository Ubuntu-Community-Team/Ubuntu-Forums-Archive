---
title: "[SOLVED] MyPassordSafe crashes on opening or creating new safe"
date: 2007-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by paulisdead on 2007-10-25
Just did a clean install of Gutsy on my desktop and I can't use MyPasswordSafe at all.  It runs fine on my i386 installs of Gutsy, though.  On my desktop it crashes whenever I try to open a safe or create a new one, here's the crash output.

```
paulisdead@deepthought:~$ MyPasswordSafe .pass/vigilos_admin.dat 
*** glibc detected *** MyPasswordSafe: free(): invalid next size (fast): 0x0000000000953080 ***
======= Backtrace: =========
/lib/libc.so.6[0x2acdee263b0a]
/lib/libc.so.6(cfree+0x8c)[0x2acdee2676fc]
MyPasswordSafe[0x419859]
MyPasswordSafe[0x4198cc]
MyPasswordSafe[0x419a52]
MyPasswordSafe[0x41269d]
MyPasswordSafe[0x41809d]
MyPasswordSafe[0x418e65]
MyPasswordSafe[0x414154]
MyPasswordSafe[0x4279b0]
MyPasswordSafe[0x426d0f]
MyPasswordSafe[0x43dbd2]
MyPasswordSafe[0x444593]
MyPasswordSafe[0x4423c9]
/usr/lib/libqt-mt.so.3(_ZN7QObject15activate_signalEP15QConnectionListP8QUObject+0x12a)[0x2acdecb02d76]
/usr/lib/libqt-mt.so.3(_ZN7QObject15activate_signalEi+0x174)[0x2acdecb03910]
/usr/lib/libqt-mt.so.3(_ZN7QButton7clickedEv+0x25)[0x2acdece7918f]
/usr/lib/libqt-mt.so.3(_ZN7QDialog13keyPressEventEP9QKeyEvent+0x12b)[0x2acdecca889f]
/usr/lib/libqt-mt.so.3(_ZN7QWidget5eventEP6QEvent+0x3a0)[0x2acdecb37728]
/usr/lib/libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0x25e)[0x2acdeca9e2a2]
/usr/lib/libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x432)[0x2acdecaa0208]
/usr/lib/libqt-mt.so.3(_ZN12QApplication20sendSpontaneousEventEP7QObjectP6QEvent+0x5e)[0x2acdeca30d84]
/usr/lib/libqt-mt.so.3(_ZN9QETWidget17translateKeyEventEPK7_XEventb+0xa41)[0x2acdeca223d7]
/usr/lib/libqt-mt.so.3(_ZN12QApplication15x11ProcessEventEP7_XEvent+0xc60)[0x2acdeca2dbd8]
/usr/lib/libqt-mt.so.3(_ZN10QEventLoop13processEventsEj+0x110)[0x2acdeca4443e]
/usr/lib/libqt-mt.so.3(_ZN10QEventLoop9enterLoopEv+0x73)[0x2acdecab77e7]
/usr/lib/libqt-mt.so.3(_ZN12QApplication10enter_loopEv+0x22)[0x2acdeca9fd06]
/usr/lib/libqt-mt.so.3(_ZN7QDialog4execEv+0xd7)[0x2acdecca8ef1]
MyPasswordSafe(_ZNK7QDialog8sizeHintEv+0x250)[0x411af0]
MyPasswordSafe(_ZN9QListView13keyPressEventEP9QKeyEvent+0x113f)[0x411e9f]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2acdee20fb44]
MyPasswordSafe(_ZNK7QDialog8sizeHintEv+0xc9)[0x411969]
======= Memory map: ========
00400000-004b4000 r-xp 00000000 08:04 1148403                            /usr/bin/MyPasswordSafe
006b4000-006b6000 rw-p 000b4000 08:04 1148403                            /usr/bin/MyPasswordSafe
006b6000-0099c000 rw-p 006b6000 00:00 0                                  [heap]
2acdec4a9000-2acdec4c6000 r-xp 00000000 08:03 2326547                    /lib/ld-2.6.1.so
2acdec4c6000-2acdec4c9000 rw-p 2acdec4c6000 00:00 0 
2acdec4c9000-2acdec4ca000 r--p 00000000 08:04 1393660                    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
2acdec4ca000-2acdec4d1000 r--s 00000000 08:04 1345102                    /usr/lib/gconv/gconv-modules.cache
2acdec4d1000-2acdec4d2000 r--p 00000000 08:04 1393661                    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
2acdec4d2000-2acdec4d3000 r--p 00000000 08:04 1393666                    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
2acdec4d3000-2acdec4d4000 r--p 00000000 08:04 1393657                    /usr/lib/locale/en_US.utf8/LC_ADDRESS
2acdec4d4000-2acdec4d5000 r--p 00000000 08:04 1393663                    /usr/lib/locale/en_US.utf8/LC_NAME
2acdec4d5000-2acdec4d6000 r--p 00000000 08:04 1393665                    /usr/lib/locale/en_US.utf8/LC_PAPER
2acdec4d6000-2acdec4d7000 r--p 00000000 08:04 1409040                    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
2acdec4d7000-2acdec4d8000 r--p 00000000 08:04 1393662                    /usr/lib/locale/en_US.utf8/LC_MONETARY
2acdec4d8000-2acdec5b8000 r--p 00000000 08:04 1393658                    /usr/lib/locale/en_US.utf8/LC_COLLATE
2acdec5b8000-2acdec5b9000 r--p 00000000 08:04 1393667                    /usr/lib/locale/en_US.utf8/LC_TIME
2acdec5b9000-2acdec5ba000 r--p 00000000 08:04 1393664                    /usr/lib/locale/en_US.utf8/LC_NUMERIC
2acdec5ba000-2acdec5f9000 r--p 00000000 08:04 1393659                    /usr/lib/locale/en_US.utf8/LC_CTYPE
2acdec5f9000-2acdec600000 r--s 00000000 08:03 361147                     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2acdec600000-2acdec605000 r--s 00000000 08:03 360509                     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2acdec605000-2acdec60b000 r--s 00000000 08:03 361069            Aborted (core dumped)
```

If anyone has any clue how to get it to work, I'd be grateful.  Or if anyone knows of another password manager that runs on x86_64 and is compatible with the .dat files created in MyPasswordSafe, I'd be willing to give that a go.  I really don't want to build a new safe just for this one computer, as I probably have a few hundred or so passwords in it.

I do recall having setup a 32bit MyPasswordSafe when I used to run Gentoo on this box, until Gutsy came out.  I'm still a little fresh to Ubuntu, so if that's the only way to get it going, I just need to be pointed to the right direction on how to setup 32bit compatibility libs and stuff.

Thanks.

---

### Post by tbfr on 2007-10-26
> if anyone knows of another password manager that runs on x86_64 and is compatible with the .dat files created in MyPasswordSafe

I am using Revelation. It has an option to import MyPasswordSafe files.

---

### Post by paulisdead on 2007-10-26
I gave revelation a shot, and it lets me import the safe, but as soon as I try to open a password or save the safe it crashes.  Here's the output of it crashing when I clicked on a password.

```
paulisdead@deepthought:~$ revelation 
Traceback (most recent call last):
  File "/usr/bin/revelation", line 415, in <lambda>
    self.tree.selection.connect("changed", lambda w: self.entryview.display_entry(self.entrystore.get_entry(self.tree.get_active())))
  File "/usr/lib/python2.5/site-packages/revelation/ui.py", line 1929, in display_entry
    widget = generate_field_display_widget(field, self.config, self.clipboard)
  File "/usr/lib/python2.5/site-packages/revelation/ui.py", line 200, in generate_field_display_widget
    widget = Label(util.escape_markup(field.value))
  File "/usr/lib/python2.5/site-packages/revelation/util.py", line 155, in escape_markup
    string = string.replace("&", "&amp;")
AttributeError: 'NoneType' object has no attribute 'replace'
```

---

### Post by tbfr on 2007-10-27
hmm, [https://bugs.launchpad.net/revelation/+bug/120371]("https://bugs.launchpad.net/revelation/+bug/120371")

---

### Post by paulisdead on 2007-10-27
> **tbfr said:**
> hmm, [https://bugs.launchpad.net/revelation/+bug/120371]("https://bugs.launchpad.net/revelation/+bug/120371")

I tried the patch listed there, but now revelation doesn't startup at all
```


paulisdead@deepthought:~$ revelation 
Traceback (most recent call last):
  File "/usr/bin/revelation", line 40, in <module>
    from revelation import config, data, datahandler, dialog, entry, io, ui, util
  File "/usr/lib/python2.5/site-packages/revelation/__init__.py", line 27, in <module>
    import util
  File "/usr/lib/python2.5/site-packages/revelation/util.py", line 161
    if string:
             ^
IndentationError: unindent does not match any outer indentation level
```

So looks like revelation is out for me.

I found an app called getlibs on the forums and used that to install a 32bit libqt-mt.so.3, and then force installed the deb package for the 32bit MyPasswordSafe, and got it working that way.

---

