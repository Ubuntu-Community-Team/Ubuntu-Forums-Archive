---
title: "Kontact crashes on start up"
date: 2008-09-09
forum: x86 64-bit Users
---

### Post by JG6_oddball on 2008-09-09
I added an OPML feed last night and now it wont start up here is the error trace, this happened one time before and i had to uninstall it 2 twice to get it to work again, thnx for any help
p.s kubuntu 8.04
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
[New Thread 0x7f63b0f7f6f0 (LWP 13102)]
[New Thread 0x419f1950 (LWP 13132)]
[New Thread 0x411f0950 (LWP 13131)]
[New Thread 0x409ef950 (LWP 13130)]
[New Thread 0x423f0950 (LWP 13129)]
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
[KCrash handler]
#5  0x00007f63ab555471 in QGListIterator::QGListIterator ()
   from /usr/lib/libqt-mt.so.3
#6  0x00007f63a192e582 in KMFolderMaildir::createIndexFromContents ()
   from /usr/lib/libkmailprivate.so
#7  0x00007f63a1929964 in KMFolderMaildir::open ()
   from /usr/lib/libkmailprivate.so
#8  0x00007f63a1a8faf5 in KMail::FolderTreeBase::hideLocalInbox ()
   from /usr/lib/libkmailprivate.so
#9  0x00007f63a181e14c in KMFolderTree::addDirectory ()
   from /usr/lib/libkmailprivate.so
#10 0x00007f63a181e3ca in KMFolderTree::reload ()
   from /usr/lib/libkmailprivate.so
#11 0x00007f63a19beb14 in KMMainWidget::slotShowStartupFolder ()
   from /usr/lib/libkmailprivate.so
#12 0x00007f63a19cfb4b in KMMainWidget::qt_invoke ()
   from /usr/lib/libkmailprivate.so
#13 0x00007f63ab26afd0 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#14 0x00007f63ab5e3181 in QSignal::signal () from /usr/lib/libqt-mt.so.3
#15 0x00007f63ab2891a3 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#16 0x00007f63ab2909e4 in QSingleShotTimer::event ()
   from /usr/lib/libqt-mt.so.3
#17 0x00007f63ab20333a in QApplication::internalNotify ()
   from /usr/lib/libqt-mt.so.3
#18 0x00007f63ab205093 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#19 0x00007f63ac93940d in KApplication::notify ()
   from /usr/lib/libkdecore.so.4
#20 0x00007f63ab19420e in QApplication::sendEvent ()
   from /usr/lib/libqt-mt.so.3
#21 0x00007f63ab1f6abc in QEventLoop::activateTimers ()
   from /usr/lib/libqt-mt.so.3
#22 0x00007f63ab1a9107 in QEventLoop::processEvents ()
   from /usr/lib/libqt-mt.so.3
#23 0x00007f63ab21d5bf in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#24 0x00007f63ab204d9e in QApplication::enter_loop ()
   from /usr/lib/libqt-mt.so.3
#25 0x00007f63ab414f31 in QDialog::exec () from /usr/lib/libqt-mt.so.3
#26 0x00007f63ad6ed2ef in KMessageBox::createKMessageBox ()
   from /usr/lib/libkdeui.so.4
#27 0x00007f63ad6ed9dd in KMessageBox::createKMessageBox ()
   from /usr/lib/libkdeui.so.4
#28 0x00007f63ad6ef53e in KMessageBox::sorryWId () from /usr/lib/libkdeui.so.4
#29 0x00007f63b0aced82 in ?? () from /usr/lib/libkdepim.so.1
#30 0x00007f63b0acf8d6 in KPIM::kFileToString () from /usr/lib/libkdepim.so.1
#31 0x000000000041b7ae in ?? ()
#32 0x000000000041dbe4 in ?? ()
#33 0x000000000041dea8 in ?? ()
#34 0x0000000000418d30 in ?? ()
#35 0x00007f63ac8f2066 in KUniqueApplication::processDelayed ()
   from /usr/lib/libkdecore.so.4
#36 0x00007f63ac91bff1 in KUniqueApplication::qt_invoke ()
   from /usr/lib/libkdecore.so.4
#37 0x00007f63ab26afd0 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#38 0x00007f63ab5e3181 in QSignal::signal () from /usr/lib/libqt-mt.so.3
#39 0x00007f63ab2891a3 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#40 0x00007f63ab2909e4 in QSingleShotTimer::event ()
   from /usr/lib/libqt-mt.so.3
#41 0x00007f63ab20333a in QApplication::internalNotify ()
   from /usr/lib/libqt-mt.so.3
#42 0x00007f63ab205093 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#43 0x00007f63ac93940d in KApplication::notify ()
   from /usr/lib/libkdecore.so.4
#44 0x00007f63ab19420e in QApplication::sendEvent ()
   from /usr/lib/libqt-mt.so.3
#45 0x00007f63ab1f6abc in QEventLoop::activateTimers ()
   from /usr/lib/libqt-mt.so.3
#46 0x00007f63ab1a9107 in QEventLoop::processEvents ()
   from /usr/lib/libqt-mt.so.3
#47 0x00007f63ab21d5bf in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#48 0x00007f63ab21d2ab in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#49 0x00007f63ab204e00 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#50 0x0000000000419299 in ?? ()
#51 0x00007f63a7a301c4 in __libc_start_main () from /lib/libc.so.6
#52 0x0000000000418a59 in ?? ()
#53 0x00007fffb8faea18 in ?? ()
#54 0x0000000000000000 in ?? ()


S!

---

