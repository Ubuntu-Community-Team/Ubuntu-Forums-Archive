---
title: "kde-window-decorator crash"
date: 2008-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by malathion on 2008-03-03
kde-window-decorator is randomly crashing, which requires me to restart compiz. Here's the backtrace:

```
(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 47718743433376 (LWP 4733)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#5  0x00002b665ee3d3b6 in QObject::parent () from /usr/lib/libqt-mt.so.3
#6  0x00002b665ee3db1f in QWidget::parentWidget () from /usr/lib/libqt-mt.so.3
#7  0x00002b665ef4a217 in QWidget::~QWidget () from /usr/lib/libqt-mt.so.3
#8  0x00002b665efaa59d in QButton::~QButton () from /usr/lib/libqt-mt.so.3
#9  0x00002b66634801b0 in CrystalButton::~CrystalButton ()
   from /usr/lib/kde3/kwin3_crystal.so
#10 0x00002b66634786b2 in CrystalClient::~CrystalClient ()
   from /usr/lib/kde3/kwin3_crystal.so
#11 0x0000000000417bb1 in ?? ()
#12 0x000000000040fcb5 in ?? ()
#13 0x000000000040c8ba in ?? ()
#14 0x00002b665ef0fd76 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#15 0x00002b665ceaf093 in KWinModule::windowRemoved ()
   from /usr/lib/libkdecore.so.4
#16 0x00002b665ceb321a in KWinModulePrivate::removeClient ()
   from /usr/lib/libkdecore.so.4
#17 0x00002b665cea4aed in NETRootInfo::update () from /usr/lib/libkdecore.so.4
#18 0x00002b665cea4ef8 in NETRootInfo::event () from /usr/lib/libkdecore.so.4
#19 0x00002b665ceb4465 in KWinModulePrivate::x11Event ()
   from /usr/lib/libkdecore.so.4
#20 0x00002b665cf52a98 in KApplication::x11EventFilter ()
   from /usr/lib/libkdecore.so.4
#21 0x00000000004102e5 in ?? ()
#22 0x00002b665ee2ac6a in ?? () from /usr/lib/libqt-mt.so.3
#23 0x00002b665ee3a4c3 in QApplication::x11ProcessEvent ()
   from /usr/lib/libqt-mt.so.3
#24 0x00002b665ee5143e in QEventLoop::processEvents ()
   from /usr/lib/libqt-mt.so.3
#25 0x00002b665eec47e7 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#26 0x00002b665eec45ef in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#27 0x00002b665eeacd68 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#28 0x000000000040e929 in ?? ()
#29 0x00002b665de2cb44 in __libc_start_main () from /lib/libc.so.6
#30 0x000000000040c2e9 in ?? ()
#31 0x00007fff4e9913e8 in ?? ()
#32 0x0000000000000000 in ?? ()

```

Is this a known error?

---

### Post by luisromangz on 2008-03-03
Are you sure it is a random crash? It was known to happen with the Crystal decoration when you try to shade a window using the scroll wheel. The latest version of the window decoration solved this problem, you can look for them at [www.kde-look.org](www.kde-look.org).

---

### Post by malathion on 2008-03-08
> **luisromangz said:**
> Are you sure it is a random crash? It was known to happen with the Crystal decoration when you try to shade a window using the scroll wheel. The latest version of the window decoration solved this problem, you can look for them at [www.kde-look.org](www.kde-look.org).

I'm not sure that it's random, I should have said that I can't discern anything that causes it, and I can't relibly reproduce it. :) I'll try that and report back, thanks.

---

